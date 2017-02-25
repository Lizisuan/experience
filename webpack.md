# webpack 的入门和踩坑(持续完善)

## 什么是webpack？

> Webpack 是当下最热门的前端资源模块化管理和打包工具。(摘自webpack中文指南)

## 前提

* Node.js

> npm 是 Node自带的包管理工具

## 安装

1. 将webpack安装到全局环境下，可以使用webpack命令

    `npm install -g webpack`

2. 为了使不同的项目拥有不同的webpack配置文件，一般再将webpack安装到项目中

    `npm install --save-dev webpack`

## 配置


### 创建package.json文件,可以新建也可以使用命令

`npm init`

使用命令的情况下会让你输入信息，然后生成文件

package.json 基本内容 如下

```
{
    "name": "project name",
    "version": "1.0.0",
    "description": "project description",
    "scripts": {
        
    },
    "author": "author",
    "license": "MIT",
    "dependencies": {

    },
    "devDependencies": {
        "webpack": "^2.2.1"
    }
    
}
```

scripts 内容的含义用如下的例子来说明

```
"scripts": {
    "dev": "node build/dev-server.js",
},
```

在终端中输入` npm run dev ` 等同于 `node build/dev-server.js `

dependencies 是模块列表，以 -save 安装

devDependencies 是模块列表，以 -save-dev 安装

> 使用npm run的方便之处在于，npm会自动把node_modules/.bin加入$PATH，这样你可以直接运行依赖程序和开发依赖程序，不用全局安装了

> 小技巧 : 可以在package.json文件中输入需要的模块，使用`npm install` 一次安装所有模块

### 创建 webpack.config.js

> webpack可以写commonjs语法

当然，可以直接在使用webpack命令将入口文件总所有依赖打包成一个出口文件

`webpack entry.js bundle.js`

基本的文件内容
```
var webpack = require('webpack')

module.exports = {
  devtool:false,
  entry: './entry.js',
  output: {
    path: __dirname,
    filename: 'bundle.js'
  },
  module: {
    loaders: [
      {
        test: /\.css$/,
        exclude: /node_modules/,
        loader: 'style-loader!css-loader',
        query: {
          
        }
      }
    ]
  },
  plugins: [
    new webpack.BannerPlugin('')
  ]
}
```
> "__dirname"是 node 中的一个全局变量，它指向当前执行脚本所在的目录。

参数说明

* devtool -- 生成Source Maps，方便调试，但是出口文件体积会变大
* entry   -- 入口文件路径
* output  -- 出口文件路径，文件名
* module > loaders > test  -- 匹配loaders所处理的文件类型的正则表达式（必须）
* module > loaders > exclude  -- 屏蔽不需要处理的路径 , 也可以写成 include 必须处理的文件路径（可选）
* module > loaders > loader -- 进行作用的加载器(从右到左作用)（必须）
* module > loaders > loader  -- 为loaders提供额外的设置选项（可选）
* plugins --插件

其中 loader 和 插件 都需要额外安装，例如

`npm install css-loader style-loader`

## 打包


`webpack ` 打包

`webpack -p ` 打包并压缩输出文件

`webpack --watch` 启用观察者模式，文件改变自动打包

`webpack -d` 生成map映射文件,告知哪些模块被最终打包到哪里了

`webpack --colors` 显示静态资源的颜色

···

## loader

1. sass-loader

sass-loader 安装会遇到各种各样的问题，建议采用淘宝的镜像安装

    npm install -g cnpm --registry=https://registry.npm.taobao.org
    cnpm install --save-dev node-sass



