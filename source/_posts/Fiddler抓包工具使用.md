---
title: Fiddler抓包工具使用
date: 2022-03-16 15:47:02
categories: 'TOOLS'
tags: 工具
cover: https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/Telerik_Fiddler_202208301550.png
---
# 一、Fiddler简介	
Fiddler是最强大最好用的Web调试工具之一， 它能记录所有客户端和服务器的http和https请求。允许你监视、设置断点、甚至修改输入输出数据。

## Fiddler Classic VS Fiddler Everywhere
|  | Fiddler Classic（经典版） | Fiddler Everywhere |
| --- | --- | --- |
| 支持平台 | Windows | macOS, Windows, and Linux |
| 功能 | Fiddler Classic | Fiddler Classic+postman |
| 费用 | **免费** | **收费** |


## 下载链接

以下介绍以Fiddler Classic为例。

# 二、Fiddler界面
主界面分为顶部工具栏，左侧会话列表，右侧请求信息和底部的命令行工具。界面左侧会话列表中的是HTTP数据包，右侧Inspectors用于查看会话的内容，上边是Request请求信息，下边是Response响应信息<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647416431436-9441f34d-04b3-4622-8211-7d56d58d8fed.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u2d25c61f&margin=%5Bobject%20Object%5D&name=image.png&originHeight=729&originWidth=1366&originalType=url&ratio=1&rotation=0&showTitle=false&size=182450&status=done&style=none&taskId=u6a821b65-2a87-4bc0-a948-a8f3147dee8&title=)

## 1、会话列表
![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647416921107-f68b2c44-b07f-4cf8-956b-c4a8f11b9ebd.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=192&id=u86882106&margin=%5Bobject%20Object%5D&name=image.png&originHeight=383&originWidth=1563&originalType=binary&ratio=1&rotation=0&showTitle=false&size=269387&status=done&style=none&taskId=u20d7a0b7-643f-4c56-9306-2eea24587c9&title=&width=781.5)

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



## 2、会话信息
右侧面板可以查看会话请求的详细信息，可以通过点击不同的页签查看请求的详细信息和分析结果。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647417341810-c2186958-d071-497d-8140-ba369ca6ec47.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=191&id=u06a33a31&margin=%5Bobject%20Object%5D&name=image.png&originHeight=381&originWidth=1350&originalType=binary&ratio=1&rotation=0&showTitle=false&size=191498&status=done&style=none&taskId=u7dd69faf-fb58-40b7-92d3-0918acfc6d5&title=&width=675)

### Statistics统计页签
通过该页签， 用户可以通过选择多个会话来得来这几个会话的总的信息统计，比如多个请求和传输的字节数。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647417561953-93875383-0ae2-4a7b-999f-6d56517f681c.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=456&id=ubf70349d&margin=%5Bobject%20Object%5D&name=image.png&originHeight=911&originWidth=1059&originalType=binary&ratio=1&rotation=0&showTitle=false&size=212330&status=done&style=none&taskId=u319d002d-df4b-40f2-9903-a7f0e4eefbb&title=&width=529.5)

1. 反映一个请求的性能指标，其中主要需要关注RTT（体现一个请求从发送到返回响应的时间）
1. 会展示全世界范围的请求平均数据
1. show chart按钮，从饼状图中分别出哪些资源的请求耗时最多，从而对页面的访问进行访问速度优化

### Inspectors检查页签
它提供headers、textview、hexview,Raw等多种方式查看单条http请求的请求报文的信息，它分为上下两部分：上部分为HTTP Request（请求）展示，下部分为HTTPResponse（响应）展示<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647418561646-2496daa6-f504-4cbf-85c7-59f8b9ae679a.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=439&id=u58c5b512&margin=%5Bobject%20Object%5D&name=image.png&originHeight=878&originWidth=1059&originalType=binary&ratio=1&rotation=0&showTitle=false&size=245650&status=done&style=none&taskId=u9145361d-de48-438f-888f-2a05c8fab20&title=&width=529.5)

### AutoResponse自动响应页签
Fiddler最实用的功能， 它可以抓取在线页面保存到本地进行调试， 大大减少了在线调试的困难， 可以让我们修改服务器端返回的数据， 例如让返回都是HTTP404或者读取本地文件作为返回内容。

![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647418661075-77eaea39-5011-44f4-9fa5-8d33aadc7de4.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=439&id=u25dfabef&margin=%5Bobject%20Object%5D&name=image.png&originHeight=878&originWidth=1059&originalType=binary&ratio=1&rotation=0&showTitle=false&size=166531&status=done&style=none&taskId=u8253f686-e766-4eb3-8bac-fa82fee4502&title=&width=529.5)

可设置打开某网页显示自己想要的内容，点击add rule，设置如下所示。RuleEditor可以通过正则进行匹配，具体规则可以参考【[官方文档](https://docs.telerik.com/fiddler/knowledge-base/autoresponder)】<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647418770985-0272a225-4b05-4fde-8f9a-9ee5044ef465.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=219&id=u70d62926&margin=%5Bobject%20Object%5D&name=image.png&originHeight=438&originWidth=1059&originalType=binary&ratio=1&rotation=0&showTitle=false&size=147116&status=done&style=none&taskId=u0e985d38-d21d-4f93-9028-40fd45c1b1a&title=&width=529.5)

### Composer构建页签
支持手动构建和发送HTTP， HTTPS和FTP请求， 我们还可以从web session列表中拖曳session， 把它放到composer选项卡中， 当我们点击Execute按钮， 把请求发送到服务器端。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647419556897-f3216b4c-dc97-4246-be22-239941ca1dc6.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=0.6538&from=paste&height=439&id=u606a5fb0&margin=%5Bobject%20Object%5D&name=image.png&originHeight=878&originWidth=1059&originalType=binary&ratio=1&rotation=0&showTitle=false&size=115759&status=done&style=none&taskId=ue33e5ff1-078b-421f-a663-c922378d3b0&title=&width=530)


### Filters过滤页签
过滤器可以对左侧的数据流列表进行过滤， 我们可以标记、 修改或隐藏某些特征的数据流。<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647419755185-f746e24e-9c38-41c5-96a6-4e2da8d28943.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=286&id=u8e7ca4ca&margin=%5Bobject%20Object%5D&name=image.png&originHeight=571&originWidth=1060&originalType=binary&ratio=1&rotation=0&showTitle=false&size=125088&status=done&style=none&taskId=ub48f764b-25d4-4b04-a706-f767a2da707&title=&width=530)


### Timeline时间轴页签
时间轴，也称为Fiddler的瀑布图，展示网络请求时间的功能。 每个网络请求都会经历域名解析、建立连接、发送请求、接受数据等阶段。把多个请求以时间作为 X 轴， 用图表的形式展现出来， 就形成了瀑布图。 在左侧会话窗口点击一个或多个（同时按下 Ctrl 键），Timeline 便会显示指定内容从服务端传输到客户端的时间<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647419819800-f1ab5f4f-1912-42f4-9863-184e2310ee9e.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=425&id=ucca3db3c&margin=%5Bobject%20Object%5D&name=image.png&originHeight=850&originWidth=1932&originalType=binary&ratio=1&rotation=0&showTitle=false&size=624414&status=done&style=none&taskId=u0f617408-ee13-4362-b6fb-d56631f7188&title=&width=966)

## 3、命令行工具
Fiddler的左下角有一个命令行工具叫做QuickExec,允许你直接输入命令。
### 常见命令
| **help ** | 打开官方的使用页面介绍， 所有的命令都会列出来 |
| --- | --- |
| **cls ** | 清屏，也可以使用 【Ctrl+x 】 |
| **select ** | 选择会话的命令， 选择所有相应类型select image、select css、select html |
| **?sometext ** | 查找字符串并高亮显示查找到的会话列表的条目，例如：?qq.com |
| **>size** | 选择请求响应大小小于size字节的会话 |
| **=status/=method/@host** | 查找状态、方法、主机相对应的session会话，=504，=get，@www.qq.com |
| **quit** | 退出fiddler |



# 三、Fiddler使用
## 1、抓取HTTPS
打开Fiddler  Tool->Fiddler Options->HTTPS，选中"Decrpt HTTPS traffic",    Fiddler就可以截获HTTPS请求，第一次会弹出证书安装提示，若没有弹出提示，勾选Actions-> Trust Root Certificate。<br />配置完后记得要重启Fiddler！<br />![image.png](https://cdn.nlark.com/yuque/0/2022/png/547393/1647415986501-808340fb-7de6-4889-b574-16e94e84db17.png#clientId=uf8c9eaf0-1363-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=520&id=Jp2GQ&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1039&originWidth=1930&originalType=binary&ratio=1&rotation=0&showTitle=false&size=561477&status=done&style=none&taskId=ua982d8d5-6417-479f-9b1b-bf182aa73d7&title=&width=965)

## 2、移动端抓包
ios教程: [https://blog.csdn.net/zhengdonglingling/article/details/100857808](https://blog.csdn.net/zhengdonglingling/article/details/100857808)<br />android教程：[https://www.jianshu.com/p/b90901c1f19d](https://www.jianshu.com/p/b90901c1f19d)<br />ps：若ios浏览器打开任意网站都出现 “此站点的安全证书不受信任”的问题，解决方案：[链接](https://blog.csdn.net/cz__csdn/article/details/115057193)

## 3、微信公众号调试技巧（直连本地代码）
教程：[https://cfpamf.yuque.com/superqianduan/zx4n3h/bzsxgi](https://cfpamf.yuque.com/superqianduan/zx4n3h/bzsxgi)




# 四、参考资料

- Fiddler官方文档【[https://docs.telerik.com/fiddler](https://docs.telerik.com/fiddler)】
- Fiddler配置及使用教程【[https://www.cnblogs.com/woaixuexi9999/p/9247705.html](https://www.cnblogs.com/woaixuexi9999/p/9247705.html)】
- Fiddler抓包工具使用详解 【[https://www.cnblogs.com/hong-fithing/p/7582947.html](https://www.cnblogs.com/hong-fithing/p/7582947.html)】
- Fiddler抓包【[https://www.jianshu.com/p/44a64d485fed](https://www.jianshu.com/p/44a64d485fed)】