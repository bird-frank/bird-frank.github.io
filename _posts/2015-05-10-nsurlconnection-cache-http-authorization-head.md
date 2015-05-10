---
layout: post
title: NSURLConnection缓存HTTP Authorization 头字段带来的问题
description: ""
category: tech
tags: [ios]
---

为一个项目开发iOS客户端App，服务端采用HTTP Digest Authentication 进行身份认证。在客户使用```NSURLCredentialStorage```将
用户名、登录密码存入KeyChain是最直接了当的方法。这样一来密码将加密存放在系统的KeyChain中，非常安全；二来，可以相信iOS
```NSURLConnection``` 与WebServer进行身份认证的过程足够可靠。但是，就是这个直接了当的方法隐含着一个巨大的坑。

问题发生在当前用户退出，使用另一个帐号（登录名）登录的时候。测试发现用户用新的帐号登录以后，每次调用服务端需要身份认证的
接口时，发送的仍然是前一个用户的身份认证信息！

首先，Logout时使用下面的代码段从 ```NSURlCredentialStorage``` 中清除用户登录信息：

```objc
NSURLCredentialStorage * store = [NSURLCredentialStorage sharedCredentialStorage];
NSDictionary * creds = [store credentialsForProtectionSpace: protectionSpace];

for (NSURLCredential * cred in creds.allValues) {
    [store removeCredential:cred forProtectionSpace:protectionSpace];
}
```

通过加入调试代码，验证确认在切换帐号后KeyChain中保存的用户帐号信息是正确的。

而且正常使用HTTP Digest Authentication认证方式时，客户端和服务端应该有两次交互。第一次客户端发送的HTTP请求中不包含身份认
证信息，因此服务器端返回Status code 401，客户端在发送同样的请求，但是包含Authorization头字段，这一次如果认证成功，服务端
返回Status code 200。但是观察服务器（nginx）的日志，发现对第一次HTTP请求就返回了200。

再观察服务器端（Rails）的日志，发现切换帐号登录成功后，客服端发到服务器端的HTTP Authorization头字段的信息没有改变。因此
便怀疑是iOS的 ```NSURLConnection``` 在第一次身份认证成功后缓存了 HTTP Authorization 头字段的信息，并且在对同一个服务器的
后续请求中会自动填入缓存的身份认证信息（只会缓存一段时间，而且据观察，这个时间可能是几分钟）。

显示尝试实现 ```NSURLConnectionDelegate``` 中的这两个方法：

```objc
- (BOOL)connectionShouldUseCredentialStorage:(NSURLConnection *)connection
{
    return NO;
}


- (void)connection:(NSURLConnection *)connection
    willSendRequestForAuthenticationChallenge:(NSURLAuthenticationChallenge *)challenge
{
    if (challenge.previousFailureCount > 1) {
        NSLog(@"can't authentication.");
        [challenge.sender cancelAuthenticationChallenge:challenge];
        return;
    }

    NSURLCredential * cred = [[NSURLCredentialStorage sharedCredentialStorage]
        defaultCredentialForProtectionSpace: challenge.protectionSpace];

    [[challenge sender] useCredential: cred
           forAuthenticationChallenge:challenge];
 
}
```

但是这两个方法根本没有被调用！

在这个过程中也化了很多时间在Google上搜索答案，但不知道是不是关键词用的不对，一直没有找到有用的信息。知道找到这篇Blog：

[HTTP Basic Authentication "Logout" with NSURLConnection](http://www.springenwerk.com/2008/11/i-am-currently-building-iphone.html)

文章作者遇到了和我一模一样的问题。他认为是iOS的Bug，并且发现了一个看上去似乎不太靠谱的方法：在所有请求服务端的URL后加上
“#”。

我试了，这个方法果然不靠谱。这篇文章写于2008年，这个方法也许真的恰好利用了iOS的某个Bug，但是在2015年的今天这个Bug已经修
复了。

就在“山重水复疑无路”的时候，这篇文章的某条评论带来了“柳暗花明又一村”：

> It looks like your bug report did the trick! In iPhone 3.0 you can now use:

> [NSURLCredential credentialWithUser:[usernameTextField text] password:[passwordTextField text] persistence:NSURLCredentialPersistenceNone] forAuthenticationChallenge:challenge]

显然，问题的关键是，用于这次 ```NSURLAuthenticationChallenge``` 的 ```NSURLCredential``` 的```persistence```必须是
```NSURLCredentialPersistenceNone```，否则，这个认证信息将被缓存用于后续的请求！

所以，修改一下上面的程序：

```objc
- (void)connection:(NSURLConnection *)connection
    willSendRequestForAuthenticationChallenge:(NSURLAuthenticationChallenge *)challenge
{
    if (challenge.previousFailureCount > 1) {
        NSLog(@"can't authentication.");
        [challenge.sender cancelAuthenticationChallenge:challenge];
        return;
    }

    NSURLCredential * pCred = challenge.proposedCredential;

    NSURLCredential * cred = [[NSURLCredentialStorage sharedCredentialStorage] defaultCredentialForProtectionSpace: challenge.protectionSpace];

    NSURLCredential * newCred = [NSURLCredential credentialWithUser: cred.user
                                                        password: cred.password
                                                     persistence: NSURLCredentialPersistenceNone];

    [[challenge sender] useCredential: newCred
           forAuthenticationChallenge:challenge];
 
}
```

根据从 KeyChain中保存的用户名和密码创建一个新的 ```NSURLCredential``` ，并设置 persistence 为“不保存”，问题解决啦！

{% include JB/setup %}


