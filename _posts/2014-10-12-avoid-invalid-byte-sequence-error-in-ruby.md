---
layout: post
title: "在Ruby程序中如何避免“invalid byte sequence for UTF-8”错误"
description: ""
category: 技术
tags: [ruby]
---
{% include JB/setup %}

在Ruby程序中抛出“invalid byte sequence for UTF-8 "，表示在处理的UTF-8字符串中包含不合法的编码字节。一般情况下，比如在正常接收用户从网页上输入内容的Rails程序中，是不应该出现这种错误的。这种错误往往出现在由程序从外部系统输入数据的情况。比如网页抓取爬虫从其它网站上抓取的内容如果含有不合标准的UTF-8内容（在被抓取的网页上可能显示为乱码），那么在对抓取内容做处理时就可能抛出“invalid byte sequence for UTF-8”这个错误。另外的可能性还包括：读取第三方提供的数据文件、对外接口程序读取到的数据。

问题的复杂在于，并不是所有用到这样的不合规的字符串的时候都会抛出这个错误。根据经验，读取到数据后如果只是简单地写入数据库，不做其它操作的话是不会报错的。从数据库读取后简单显示也是不会报错的。只有当对这个字符串做一些操作，比如截取子串、与其它字符串拼接时才会报错。

我碰到过一种复杂情况是搜索引擎的爬虫在抓取我的网页的时候，带的参数中含有invalid byte sequence。我的程序在对这个参数处理时抛出异常被错误捕捉程序捕捉到，然后将错误信息连同原始HTTP请求写入错误日志。写入错误日志的过程是正确的，但是在查询错误日志的页面上，应该要对原始HTTP请求进行处理以便显示，这时再次抛出了“invalid byte sequence for UTF-8”的错误（实际是ArgumentError，exception message 是这个）。

所以最好是在有风险的外部数据进入系统的边界处进行处理。简单的处理程序如下：

{% highlight ruby linenos %}
def correct_encoding(value)
  return value if value.valid_encoding?
  v = value.encode(Encoding::ISO8859_1, Encoding::UTF_8,
                   invalid: :replace, undef: :replace)
  v.encode(Encoding::UTF_8, Encoding::ISO8859_1,
           invalid: :replace, undef: :replace)
end
{% endhighlight %}

encode函数的两个option invalid 和 undef 分别指示当碰到非法的字节序列或不能转换的编码是应该如何处理。缺省都是抛出异常。指定为 :replace，表示用指定的替换字符替换非法的或不能处理的编码。缺省的替换字符是uFFFD（对Unicode）或“?”（对其它编码），替换字符可以用:replace 选项另外指定。

程序员应该永远记住：

> 外面的世界很精彩, 外面的世界很无奈
