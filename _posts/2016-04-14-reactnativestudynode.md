---
layout: post
title: React Native 学习笔记（一）
description: ""
category:
tags: [react-native]
---
{% include JB/setup %}

最近一直在研究Android App的架构，但是考察了MVP，MVVM等框架以后，对于已经非常喜欢
Ruby，RoR的简洁风格我来说，Java世界的繁琐、累赘还是让人爱不起来。

这时发现了React和React Native。（为什么去年对这些新技术那么迟钝呢？先自责一下。）

通过对React Native的初步考察和学习，准备在实际项目中使用React Native，主要考虑以下几个好处：

+ 代码量大大减少。（我是个懒人）
+ Android和iOS的代码复用程度可以大大增加，而性能上比起嵌入H5的那些方案来要好很多。
+ 调试方便，只要晃晃手机，点下“Reload JS”就可以了，省略了build的过程，编程-运行-调试的节奏大大加快。

除了React Native外，目前准备在项目中使用的js库包括：

##### [redux](http://redux.js.org) 和 [react-redux](https://github.com/reactjs/react-redux)

管理App的所有状态（state）

##### [redux-thunk](https://github.com/gaearon/redux-thunk) redux-thunk 使得
redux 可以 ```dispatch``` 一个function，在这个function中完成需要的操作（访问后台
服务什么的。）

[这个Demo](https://wiredcraft.com/blog/native-soundcloud-android-app/)演示了
redux和redux-thunk在RN应用中的使用。

但是在这个Demo```action```函数中返回一个包含```type```字段的Object，然后在
reducer中再用 ```switch``` 根据 ```type``` 去做散列，这是redux的本来用法。总感觉
这不太对。使用了 redux-thunk以后能不能简化 ```reducer``` 的写法呢？

##### [redux-form](https://github.com/erikras/redux-form)
redux-form 可以用 App state 存放 form中的数据，还可以在表单提交时完成数据验证。

##### [iz](https://www.npmjs.com/package/iz)

数据验证功能。主要用来对表单数据进行校验。

iz和redux-form集成的示例：

``` javascript
const login_rules = {
    'login_name': [{ 'rule': 'required',
                     'error': '请输入登录名。'} 
    ]
};

function createValidator(rules) {
    return (data) => {
        const r = are(rules);
        return r.validFor(data) ? {} :
        r.getInvalidFields();
    };
}

let LoginFormContainer = reduxForm({form: 'login',
                                    fields: ['login_name', 'password'],
                                    validate: createValidator(login_rules)} )(LoginForm);


```

##### [react-native-extended-stylesheet](https://github.com/vitalets/react-native-extended-stylesheet)
在样式中使用变量、百分比、算数表达式等等。

#### 几个待研究的问题

##### *TODO* 如何配置不同环境（开发和发布）中的服务器地址

之前在原生的Android App中是在build阶段根据build type 将服务器地址写入 string resource:

```
  buildTypes {
    debug {
      resValue "string", "server_host", "测试服务器地址"
    }

    release {
      resValue "string", "server_host", "正式服务器地址"
    }
  }

```

然后在应用初始化时从资源表中读取即可。

目前尚未找到在RN中读取android 资源的方法，而且在iOS App中显然不能这么做。目前另
一种考虑是写一个NativeModule提供给RN部分，负责提供App运行所需要的许多环境信息，
不限于build模式、服务器地址这些。

比如，我们的App运行中需要用到一些设备品牌、型号等信息，
[react-native-device-info](https://github.com/rebeccahughes/react-native-device-info)
可以提供这些，但是提供不了IMEI号（iOS不需要），这也需要自己写 Native Module来提供。

##### *TODO* 考察[reactive-native-camera](https://github.com/lwansbrough/react-native-camera)

##### *TODO* 研究在RN中调用支付宝、微信支付等支付应用的方法。




