---
title: SourceMap定位线上JS报错代码
date: 2022-09-06 11:05:44
tags: 项目开发
categories: 'DEBUG'
cover: https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/20220906110353_202209061104.png
---

#### 一、背景
大部分SPA网页应用在发布时，都会进行压缩，导致监控系统收集到的报错信息都是乱码。如以下情况：
![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/dad77d6cfecc_202209061249.png)

![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/3fb0290fa515_202209061249.png)

报错信息都是以下类型：
[https://h5.xiaowhale.com/wx/static/js/89009.5f7c3b3896500ef6f7cc.js:1:54624](https://h5.xiaowhale.com/wx/static/js/89009.5f7c3b3896500ef6f7cc.js:1:54624)
这种情况下，我们不好定位错位代码。

#### 二、构建包含SourceMap的生产包
官方推荐方法为：使用SourceMap关联JS文件。但是我们打包时，一般不会生成SourceMap。这时我们便可以调整webpack配置（`webpack.config.js `或者 `vue.config.js`)，构建一个生产包。

1. 修改webpack配置

`config.devtool = 'source-map'`
![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/20_202209061251.png)

2. 在本地构建一个生产包：npm run build: prod

3. 构建完成后，在dist目录下，找到相关的文件，此时我们可以看到已经生成了map文件。

![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/21_202209061251.png)

#### 三、解析关联sourcemap和js
如需要定位: 
https://h5.xiaowhale.com/wx/static/js/89009.5f7c3b3896500ef6f7cc.js:1:54624 的代码错误.

1. 访问[SourceMap在线解析|在线工具](https://www.hai-fe.com/decodeSourceMap)

2. 选择js文件、map文件、输入报错的行/列号，点击解码，真实代码就会被标记成红底，从而定位报错的代码

![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/22_202209061252.png)
