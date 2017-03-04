# vue 全家桶（持续更新）

* vue-cli
* vue-resource
* vue
* vue-router

___

## vue-cli

vue的官方脚手架 , 非常好用 , 目录为

    -- build   webpack的配置文件夹
    ---- build.js    最终编译的配置文件
    ---- check-versions.js
    ---- dev-client.js
    ---- dev-server.js
    ---- utils.js    检测vue文件需要的loader
    ---- vue-loader.conf.js    vue文件的loader配置
    ---- webpack.base.config.js    webpack的基础配置
    ---- webpack.dev.conf.js    webpack的开发环境配置
    ---- webpack.prod.conf.js    webpack的生产环境配置
    -- config   webpack的配置文件夹
    ---- dev.env.js
    ---- index.js    开发环境和生产环境的生成配置，开发环境和设置端口号和跨域调试（proxyTable）
    ---- prod.env.js
    -- node_modules    webpack依赖的模块
    -- dist    项目的生产目录（编译之后生成的项目的目录）
    -- src    项目的开发目录
    ---- assets
    ---- components    组件文件夹
    ---- App.vue
    ---- main.js    项目的webpack入口文件
    -- static    项目的静态资源
    -- .gitignore    git备份的忽略文件配置
    -- package.json   该项目的发布信息和开发依赖的工具包
    -- README.md

开发环境中遇到的问题及解决方案

### 跨域调试

当出现跨域问题的时候 ， 最简单的办法就是让后台设置 Access-Control-Allow-Origin:* 即可 ， 不过这也就意味着所有地址都能访问服务器的接口 ， 当然 可以把 * 替换成 开发机的IP地址 ， 如果不想麻烦后台 ， 前端可以采用jsonp的方法 ，不过个人并不推荐 ，vue-cli的脚手架提供了一个很不错的方法 proxyTable

在config文件夹下的index.js中 ，可以找到 ，进行如下设置

首先把 port: 8080 端口号改成和服务器的一样 ，然后设置

    proxyTable: {
        '/test': {
            target: 'http://text.mall.cn',  //服务器的域名或者IP地址
            changeOrigin: true,  //允许跨域
            pathRewrite:{  
                '^/test':'test'
            }
        }
    }
    
然后在ajax中，原本请求 'http://text.mall.cn/goods' 的写成 '/goods' 即可

## vue-resource

上面的调试说完，立马要提一下 vue-resource 的一个坑 , vue-resource 的 post 方法 发出的请求头不符合服务器的设置的时候会报错

    import VueResource from 'vue-resource'
    Vue.use(VueResource);
    Vue.http.options.emulateJSON = true;