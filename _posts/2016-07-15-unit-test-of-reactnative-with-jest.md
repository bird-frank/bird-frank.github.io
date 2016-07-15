---
layout: post
title: Unit Test of React-Native with Jest
description: ""
category:
tags: [react-native]
---

{% include JB/setup %}

```React-Native``` 当前版本（0.29）官方网站上对于使用jest进行单元测试的说明
多有错误，依言行之，肯定是做不出来的。在网上搜索良久，关于使用jest对
React-Native进行单元测试的文章也有不少，但是都是针对比较旧的版本，已经过时
了。幸好后来找到StackOverflow上
[这个问题](http://stackoverflow.com/questions/37287702/testing-react-native-apps-with-jest)
下Abdullah Bakhsh的回答，才算解决了问题。在此将其答案翻译、整理如下：

首先是```package.json```文件其中的```jest```配置，这部分```React-Native```官网上的说明是错误的。

```javascript
  "jest": {
    "scriptPreprocessor": "<rootDir>/node_modules/babel-jest",
    "unmockedModulePathPatterns": [
      "node_modules"
    ],
    "verbose": true,
    "collectCoverage": true
  },
```

第二步是安装必要的npm module:

```sh
npm install --save-dev babel-jest
npm install --save-dev babel-plugin-tranform-regenerator 
npm install --save-dev babel-preset-react-native
npm install --save-dev jest-cli
npm install --save-dev react-addons-test-utils
npm install --save-dev react-native-mock
```

第三步创建 ```.babelrc``` 文件

```javascript
{
    "presets": ["react-native"],
    "plugins": [
        "transform-regenerator"
    ]
}
```

第四步创建```__mocks__/react-native.js```文件：

```javascript
module.exports = require('react-native-mock');
```

最后，```jest```的```unmock```方法似乎不起作用，Abdullah Bakhsh给的例子中使用这样的写法：

```javascript
const ModuleName = require.requireActual('../module-name).default;
```

以此来获得未经过mock的模块，一般用于获得待测试模块。

Abdullah Bakhsh在git上有一个[演示项目](https://github.com/ethemes/react-native-jest/)包含了以上所有代码。

但是，我对于以下这句还有疑问，有待进一步实验：

```javascript
    "unmockedModulePathPatterns": [
      "node_modules"
    ],
```




