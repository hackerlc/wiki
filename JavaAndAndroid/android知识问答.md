### android知识问答
在android（以下简称a）开发中现在使用的主流开发语言是java.（以下简称j）
### 1
####1.1
Q.j是面相对象的编程语言是否能简单按照自己的理解简述一下面向对象的含义.

A.在编程过程中我们把每个需求分析后，除了整个需求作为一个对象，每个需求的细节也都分解成一个个相互依赖的对象，在技术实现过程中每个类、方法也都可以看作一个一个的对象，这些对象有继承的父子关系，有开放接口的相互调用关系，每个对象都专注于处理自己的业务逻辑，就如同一个个齿轮一样可以独立运转也可以相互关联，从而形成我们程序
####1.2
Q.普通类、抽象类、接口 有什么异同.

A.普通类class 与 abstract class ac可以声明抽象方法，ac与interface 接口只做声明，而ac可只做声明也可以实现
### 2
####2.1
Q.进程与线程的区别

A.在一个系统中一般的情况下我们每个程序都是一个进程，一个进程中可以开启多个线程
####2.2
Q.在a中的进程与线程又是什么样的

A.在a中我们每开启一个app系统都会启动一个进程，当进程被开启后会默认开启一个主线程这个线程也被称为ui线程，程序中所有的ui更新都会在这个线程中运行，这个线程中无法做耗时的操作，如果有耗时操作，需要另外开启线程.
####2.3
Q.如何开启线程，是否能简单描述有哪几种现在接触过的线程开启方式

A.可以在activity中使用new rannble实现run方法，在new thread 中开启rannble，也可以继承thread实现run方法并且调用start方法
或者利用new一个线程池的方式开启
####2.4
Q.a中进程的生命周期是什么样的

A.TODO：
### 3
####3.1
Q.j中list和hasmap分别在什么情况下使用

A.当我们需要在列表中添加数据的时候我们可以始终arraylist.当需要对列表的数据做查询的时候可以使用hasmap
####3.2
Q.j中什么时候我们可以使用范型有什么好处？

A.当我们需要规范数据格式是可以使用范型，并且在对base class做抽象的时候可以使用T，R两张模式做抽象
####3.3
Q.j中注解的使用，有哪几种注解

A.TODO：
####3.4
Q.简述j中反射的机制

A.TODO：
### 4
####4.1
Q.a中四大组件分别是什么

A.activity、broadcast receiver、service、content provider
####4.2
Q.activity的入栈方式有哪几种

A.默认的栈内多任务、栈顶唯一，栈内唯一，多栈唯一
####4.3
Q.activity生命周期

A.onCereate,onRestart,onStart,onResume,onPause,onStop,onDestory
####4.4
Q.Fragment 的生命周期与activity生命周期的关联

A.onAttach,onCreate,onCreateView,onActivityCreated,onStart,onResume,onPause,onStop,onDestoryView,onDestory,onDetach

####4.5
Q.怎样开启一个BroadcastReceiver

A.继承BroadCastReceiver 重写onReceive()方法，静态注册：在ManiFest文件中声明一个receive，动态注册：activity中IntentFilter注册，通过unregisterReceiver解绑

####4.6
Q.Intent 在android 中有什么作用

A.activity 通过Intent通信，通过在maniFest文件中声明activity的时候，当activity需要跳转时会通过intentFilter查找，新的activity通过intent的通知后开始运行

####4.7
Q.如何开始一个service

A.继承service，在manifest文件中声明service，然后需要通过Context.startService()或者Context.bindService()

####4.8 
Q.startService与bindService有什么不同

A.使用startService与调用着没有关系，首次调用会经过onCreate、onStart方法，如果再次调用会执行onStart方式，如果想停止则需要调用onStopService则会执行onDestory。使用bindService则会与调用者绑定，调用者关闭之后也随之关闭。

####4.9
Q.怎样进行网络请求的优化

A.设置超时时间、设置http缓存、开启gizp压缩以及使用https

####4.9.1
Q.http与https有什么不同

A.https会生成一个证书，通过https传输的信息是加密信息

####4.10
Q.对称加密与非对称加密有什么区别

A.对称加密可以使用相同的秘钥加解密，非对称加密有自己的私钥和公钥，加密放使用公钥加密，解密则需要使用私钥解密。

####4.11
Q.activity中有哪几种方式可以进行数据交互

A.Intent、static 变量、数据库、sheardPreferences、interface

###5
####5.1
Q.layout中有那几大布局

A.FragmentLayout、LinearLayout、RelativeLayout、TableLayout、百分比布局
####5.1
Q.为什么在布局的时候建议使用RelativeLayout

A.减少界面层级，减少内存使用
####5.2
Q.layout中有那几个常用标签

A.Include,viewStub,merge

#####5.2.1
Q.include与viewStub有什么不同

A.include和viewStub都可以引入一段layout，但是用viewStub之后引入的layout会默认不加载减少界面内存的使用
#####5.2.2
Q.viewStub和merge在什么情况下使用

A.在界面加载时不需要首先显示的layout可以使用viewstub，当使用include和viewstub的时候可能会增加界面的层级，这时就可以使用merge标签来减少层级

###6

Q.现在常用的开源框架有哪些
Q.fresco
Q.Rxjava是否了解
Q.dexClassLoader，热部署热修复
Q.databinding
