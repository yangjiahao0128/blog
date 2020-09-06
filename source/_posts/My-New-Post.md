---
title: Vue-cli@2.0脚手架搭建与打包
date: 2018-01-01 12:00:00
updated: 2018-08-09 18:09:21
tags:
---
![vuejs](https://upload-images.jianshu.io/upload_images/7255677-087930a3da74c424.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
# 一、vue-cli脚手架
`vue.js` 核心构成：vuex，vue-cli，vue-router，vue-resource
&nbsp;&nbsp;&nbsp;&nbsp;_1.1vue-cli_ ：脚手架，为了保证各施工过程 顺利进行而搭建的工作平台，
&nbsp;&nbsp;&nbsp;&nbsp;_1.2实际开发_ ：开发过程中，从零开始构建项目非常的麻烦，所以各种脚手架就应运而生。常见的脚手架：yoeman，express-generator，vue-cli
&nbsp;&nbsp;&nbsp;&nbsp;_特点_ ：功能丰富，使用他们能够快速的搭建一个完整的项目，开发者只需要在生成的项目结构的基础上进行开发即可非常高效。
&nbsp;&nbsp;&nbsp;&nbsp;极大地降低了webpack的使用难度，并支持热更新，有webpack-dev-server支持，相当于启动了一个请求服务器，帮你搭建了一个测试环境，最为开发者只需要关注开发就ok
# 二、安装vue-cli
 &nbsp;&nbsp;_2.1_ 需要使用`npm`，全局安装`webpack`，由于从`webpack@4.0`开始需要安装`webpack-cli`
&nbsp;&nbsp;_2.2_ 先执行CMD
&nbsp;&nbsp;webpack -v  确认是否全局安装过webpack,没有的话执行 
```
$ npm install -g webpack
```
&nbsp;&nbsp;再全局安装  
```
$ npm install webpack-cli -g
```
&nbsp;&nbsp;全局安装`vue-cli`
```
npm i -g vue-cli  或者  npm install --globel vue-cli
```
&nbsp;&nbsp;安装完成后确认是否安装过：
```
vue -V
```
&nbsp;&nbsp;CMD:
```
vue list        //列出可用的模板
```
# 三、利用vue-cli构建项目
   _3.1_ 首先建一个文件夹
   然后：
```
cd demo
```
   将构建的项目放进demo文件夹
   执行： 
```
vue init webpack + 项目名称
```
   执行后显示：
```
   Project name 确认项目名称
   Project description 项目描述
   Author  作者
   Vue build
    Runtime-only: about 6KB lighter min+gzip, but templates (or any Vue-specific HTML) are ONLY
    allowed in .vue files - render functions are required elsewhere 推荐的运行加编译
   Install vue-router  是否安装vue-router
   Use ESLint to lint your code 是否使用ESLint管理代码(这块一直又爱又恨)
   Set up unit tests 是否建立单元测试
   Setup e2e tests with Nightwatch 是否安装端对端的测试
```
> vue init webpack项目名称：适用于中大型项目
> vue init webpack-simple：小型项目
                        
然后 cd 进入项目
运行项目 
```
npm run dev
```
# 四、打包上线
自己的项目放在 *src* 文件夹下
编辑开发完成后打包
在`cmd`中执行
```
npm run build
```
打包成功后：默认会生成 *dist* 文件夹项目上线，只需要将 *dist* 文件夹交给后台人员放在服务器就可以了
# 小结
&nbsp;&nbsp;&nbsp;&nbsp;以上，Vue-cli@2.0脚手架基本搭建在日常的使用中基本就没有什么大问题了，只要多加练习，配合好用的官网，写起东西来肯定会行云流水。💗