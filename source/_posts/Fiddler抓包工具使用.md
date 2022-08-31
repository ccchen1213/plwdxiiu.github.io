---
title: Fiddler抓包工具使用
date: 2022-03-16 15:47:02
categories: 'TOOLS'
tags: 工具
cover: https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/Telerik_Fiddler_202208301550.png
---
# 一、Fiddler简介	
Fiddler是最强大最好用的Web调试工具之一， 它能记录所有客户端和服务器的http和https请求。允许你监视、设置断点、甚至修改输入输出数据。
<br />

### Fiddler Classic VS Fiddler Everywhere
|  | Fiddler Classic（经典版） | Fiddler Everywhere |
| --- | --- | --- |
| 支持平台 | Windows | macOS, Windows, and Linux |
| 功能 | Fiddler Classic | Fiddler Classic+postman |
| 费用 | **免费** | **收费** |
<br />

### 下载链接
[官方下载链接](https://www.telerik.com/download/fiddler)


<br />
以下介绍以Fiddler Classic为例。
<br />

# 二、Fiddler界面
主界面分为顶部工具栏，左侧会话列表，右侧请求信息和底部的命令行工具。界面左侧会话列表中的是HTTP数据包，右侧Inspectors用于查看会话的内容，上边是Request请求信息，下边是Response响应信息<br />
![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/1647416431436-9441f34d-04b3-4622-8211-7d56d58d8fed_202208311433.png)
<br />

## 1、会话列表
![image1.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/2_202208311436.png)
<br />

### 相关字段介绍
| **#**  | HTTP Request的顺序，从1开始，按照页面加载请求的顺序递增 |
| --- | --- |
| **Result**  | HTTP响应的状态 |
| **Protocol** | 请求使用的协议（如HTTP/HTTPS） |
| **HOST** | 请求地址的域名 |
| **URL** | 请求的服务器路径和文件名，也包含GET参数 |
| **BODY** | 请求的大小，以byte为单位 |
| **Caching** | 请求的缓存过期时间或缓存控制header的值 |
| **Content-Type** | 请求响应的类型 |
| **Process** | 发出此请求的Windows进程及进程ID |
| **Comments**  | 用户通过脚本或者菜单给此session增加的备注 |
| **custom** | 用户可以通过脚本设置的自定义值 |
<br />


## 2、会话信息
右侧面板可以查看会话请求的详细信息，可以通过点击不同的页签查看请求的详细信息和分析结果。<br />
![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/3_202208311442.png)
<br />

### Statistics统计页签
通过该页签， 用户可以通过选择多个会话来得来这几个会话的总的信息统计，比如多个请求和传输的字节数。<br />
![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/4_202208311442.png)
<br />

1. 反映一个请求的性能指标，其中主要需要关注RTT（体现一个请求从发送到返回响应的时间）
2. 会展示全世界范围的请求平均数据
3. show chart按钮，从饼状图中分别出哪些资源的请求耗时最多，从而对页面的访问进行访问速度优化
<br />

### Inspectors检查页签
它提供headers、textview、hexview,Raw等多种方式查看单条http请求的请求报文的信息，它分为上下两部分：上部分为HTTP Request（请求）展示，下部分为HTTPResponse（响应）展示<br />![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/5_202208311443.png)
<br />

### AutoResponse自动响应页签
Fiddler最实用的功能， 它可以抓取在线页面保存到本地进行调试， 大大减少了在线调试的困难， 可以让我们修改服务器端返回的数据， 例如让返回都是HTTP404或者读取本地文件作为返回内容。
<br />

![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/6_202208311443.png)
<br />

可设置打开某网页显示自己想要的内容，点击add rule，设置如下所示。RuleEditor可以通过正则进行匹配，具体规则可以参考[官方文档](https://docs.telerik.com/fiddler/knowledge-base/autoresponder)<br />![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/7_202208311445.png)
<br />

### Composer构建页签
支持手动构建和发送HTTP， HTTPS和FTP请求， 我们还可以从web session列表中拖曳session， 把它放到composer选项卡中， 当我们点击Execute按钮， 把请求发送到服务器端。<br />![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/8_202208311446.png)
<br />

### Filters过滤页签
过滤器可以对左侧的数据流列表进行过滤， 我们可以标记、 修改或隐藏某些特征的数据流。<br />![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/9_202208311447.png)
<br />

### Timeline时间轴页签
时间轴，也称为Fiddler的瀑布图，展示网络请求时间的功能。 每个网络请求都会经历域名解析、建立连接、发送请求、接受数据等阶段。把多个请求以时间作为 X 轴， 用图表的形式展现出来， 就形成了瀑布图。 在左侧会话窗口点击一个或多个（同时按下 Ctrl 键），Timeline 便会显示指定内容从服务端传输到客户端的时间<br />![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/10_202208311448.png)
<br />

## 3、命令行工具
Fiddler的左下角有一个命令行工具叫做QuickExec,允许你直接输入命令。
<br />

### 常见命令
| **help** | 打开官方的使用页面介绍， 所有的命令都会列出来 |
| --- | --- |
| **cls** | 清屏，也可以使用 【Ctrl+x 】 |
| **select** | 选择会话的命令， 选择所有相应类型select image、select css、select html |
| **?sometext** | 查找字符串并高亮显示查找到的会话列表的条目，例如：?qq.com |
| **>size** | 选择请求响应大小小于size字节的会话 |
| **=status/=method/@host** | 查找状态、方法、主机相对应的session会话，=504，=get，@www.qq.com |
| **quit** | 退出fiddler |
<br />


# 三、Fiddler使用
## 1、抓取HTTPS
打开Fiddler  Tool->Fiddler Options->HTTPS，选中"Decrpt HTTPS traffic",    Fiddler就可以截获HTTPS请求，第一次会弹出证书安装提示，若没有弹出提示，勾选Actions-> Trust Root Certificate。<br />配置完后记得要重启Fiddler！<br />![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/11_202208311450.png)
<br />

## 2、移动端抓包
ios教程: [https://blog.csdn.net/zhengdonglingling/article/details/100857808](https://blog.csdn.net/zhengdonglingling/article/details/100857808)<br />

android教程：[https://www.jianshu.com/p/b90901c1f19d](https://www.jianshu.com/p/b90901c1f19d)<br />

ps：若ios浏览器打开任意网站都出现 “此站点的安全证书不受信任”的问题，解决方案：[链接](https://blog.csdn.net/cz__csdn/article/details/115057193)

## 3、微信公众号调试技巧（直连本地代码）
教程：[https://cfpamf.yuque.com/superqianduan/zx4n3h/bzsxgi](https://cfpamf.yuque.com/superqianduan/zx4n3h/bzsxgi)




# 四、参考资料

- Fiddler官方文档【[https://docs.telerik.com/fiddler](https://docs.telerik.com/fiddler)】
- Fiddler配置及使用教程【[https://www.cnblogs.com/woaixuexi9999/p/9247705.html](https://www.cnblogs.com/woaixuexi9999/p/9247705.html)】
- Fiddler抓包工具使用详解 【[https://www.cnblogs.com/hong-fithing/p/7582947.html](https://www.cnblogs.com/hong-fithing/p/7582947.html)】
- Fiddler抓包【[https://www.jianshu.com/p/44a64d485fed](https://www.jianshu.com/p/44a64d485fed)】