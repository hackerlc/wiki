#Android 知识体系分享

##分享者

```
@hackerlcg


当前分享者所自我掌握和了解的知识分享，如有不对的地方欢迎指正
```

###android 

android主要使用java语言开发，java一般包含三个部分

java语言、java虚拟机、库

```
java语言：语法、其他代码程式
java虚拟机：编译连接后采用Java bytecode，需要虚拟机来执行指令
库：常用的库与C语言一样
```

###android 基本架构
![android架构](http://images.cnitblog.com/blog/473657/201301/18203746-970e2cbe223e4c1c9ca129e7a2feb6c6.jpg)


android 底层为linux系统，在系统上增加了java虚拟机Dalvik，并在Dalvik虚拟机上搭建了一个java的application framework，所有的应用程序都基于java的application framework上

android分四层

```
       应用程序层
     应用程序框架层
	   系统运行库
       linux核心层

```

应用程序
由activity所组成的常见的应用
应用程序框架

```
1.Views 可扩展视图  用来构建应用程序，包含list、buttons 等
2.Content Providers 内容提供器  应用程序间数据交互
3.Resource Manager  资源管理器 提供非代码资源访问，getResource R.xx.xx
4.Notification Manager  通知管理器  状态栏消息
5.Activity Manager 活动管理器  管理应用程序生命周期等功能
```
系统运行库
TODO
linux核心层
TODO

###android mvc


**model**
实体类，数据交互接口、数据处理类



**view**
UI、自定义UI、资源文字、图片



**control**
数据交互、绑定UI


###android 网络相关

一般android与服务器交互有两种方式
1.http GET/POST  
2.Socket TCP/UDP

常见传输格式
1.json
2.xml
3.pd?

######优化

http优化超时时间，请求头先访问、异常处理

Socket优化心跳包、断点重连

json优化结构、尽量缩减请求体、gzip压缩

###android 内存相关

1.接口数据
2.图片
3.活动页面
4.线程

######优化

接口数据可以根据需求保存到内存或本地中
本地保存方式
```
1.SharedPreferences
2.file
3.sql
```

###插件化？
利用DexClassLoader原理把原有app分解成主程序以及插件程序，主程序通过调用插件程序实现热加载。

通过HOOK实现线上bug修复？

###其他

优化上会单独分开写
也借鉴了Trinea博主的文章，非常感谢分享

http://www.trinea.cn/android/layout-performance/
