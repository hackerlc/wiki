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

android 底层为linux系统，在系统上增加了java虚拟机Dalvik，并在Dalvik虚拟机上搭建了一个java的application framework，所有的应用程序都基于java的application framework上

android分四层

```
       应用程序层
     应用程序框架层
	   系统运行库
       linux核心层

```

应用程序：
由activity所组成的常见的应用。
应用程序框架：

```
Views 可扩展视图  用来构建应用程序，包含list、buttons 等
Content Providers 内容提供器  应用程序间数据交互
Resource Manager  资源管理器 提供非代码资源访问，getResource R.xx.xx
Notification Manager  通知管理器  状态栏消息
Activity Manager 活动管理器  管理应用程序生命周期等功能
```
系统运行库
@TODO
linux核心层
@TODO
