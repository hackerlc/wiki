## android 插件化学习梳理

###android类加载器DexClassLoader介绍

    在java中有个概念叫做“类加载器”(ClassLoader)，作用为动态加载class文件。
    ClassLoader装载机制暂时不做深究，可以[参考](http://www.iteye.com/topic/83978)
    android程序最后会产生dex文件，dex文件是一种经过android打包工具优化后的class文件，因为加载这样的特殊文件就需要特殊的装载器dexClassLoader

    这个类只有一个构造函数：
    ```
    public DexClassLoader (String dexPath, String optimizedDirectory, String libraryPath, ClassLoader parent)
    Parameters
    dexPath	需要装载的APK或者Jar文件的路径。包含多个路径用File.pathSeparator间隔开,在Android上默认是 ":" 
    optimizedDirectory	优化后的dex文件存放目录，不能为null
    libraryPath	目标类中使用的C/C++库的列表,每个目录用File.pathSeparator间隔开; 可以为 null
    parent	该类装载器的父装载器，一般用当前执行类的装载器
    ```
###插件相关介绍
    首先插件只是一个逻辑概念，而不是什么技术标准，主要包含如下几个意思：
    *插件不能独立运行，必须运行一个宿主程序中，宿主程序去调用插件?
    *插件一般情况下可以独立安装，android中就可以设计一个apk
    *宿主程序中可以管理插件，比如添加，删除，禁用等。
    *宿主程序应该保证插件向下兼容，新的宿主程序应该兼容老的插件
    
###主程序与插件的结构(实验)
BAndroid(主程序)
DemoPlu(插件)
testPlugin(SDK)
###使用
1.首先创建testPlugin并且定义接口
```
package IPlugin;

/**
 * BAndroid
 * Created by YichenZ on 2016/2/15 14:09.
 */
public interface IPlugin {
    String getName();
    String getVersion();
    void show();
}
```
2.上面程序生成jar包
3.创建DemoPlu
4.把生成好的jar包放到DemoPlu的lib下面并引入
5.实现jar包的接口类
```
package plugin.yc.org.demoplu;

import IPlugin.IPlugin;

/**
 * DemoPlu
 * Created by YichenZ on 2016/2/15 14:35.
 */
public class PluginImpl implements IPlugin{
    @Override
    public String getName() {
        return "name";
    }

    @Override
    public String getVersion() {
        return "1.0";
    }

    @Override
    public void show() {
        android.util.Log.d(getName(), "ha ha I'm "+getVersion());
    }
}

```
6.生成apk并放置到手机sdcard目录下
7.把jar包放到BAndroid的lib下并引用
8.在主程序中调用
```
        try{
            //获取dex文件路径
            String dexOutputDir = getApplicationInfo().dataDir;
            ClassLoader classLoader =getClassLoader();
            //加载插件 app-debug.apk为插件生成的apk文件
            DexClassLoader localDexClassLoader =new DexClassLoader("/sdcard/app-debug.apk",dexOutputDir,null,classLoader);
            //加载相关类
            Class localClass =localDexClassLoader.loadClass("plugin.yc.org.demoplu.PluginImpl");
            Constructor localConstructor = localClass.getConstructor(new Class[]{});
            Object instance =localConstructor.newInstance(new Object[]{});
            
            IPlugin iPlugin =(IPlugin)instance;
            System.out.println(iPlugin.getName());
            iPlugin.show();
        }catch (Exception e){

        }
        
        输出：
        02-15 18:13:19.657 4970-4970/com.bandroid.demo I/System.out: name
        02-15 18:13:19.658 4970-4970/com.bandroid.demo D/PluginImp: ha ha I'm 1.0
```
结束

###问题
dexClassLoader除了加载了plugin.yc.org.demoplu.PluginImpl 是否也加载了plugin.yc.org.demoplu.PluginImpl中调用的其他类
修改上面的代码，在插件中增加Content类
···
package plugin.yc.org.demoplu;

/**
 * DemoPlu
 * Created by YichenZ on 2016/2/15 17:56.
 */
public class Content {
    public static String name = "PluginImp";
    public  static String version ="1.0";
}

···
实现类中修改为
···
    @Override
    public String getName() {
        return Content.name;
    }

    @Override
    public String getVersion() {
        return Content.version;
    }
···
重新打包插件类并放置到cdcard下，重新run主程序
```
输出
02-15 18:13:19.657 4970-4970/com.bandroid.demo I/System.out: PluginImp
02-15 18:13:19.658 4970-4970/com.bandroid.demo D/PluginImp: ha ha I'm 1.0
```
###问题2(待验证)
是否可以通过主程序下载插件并实现更新加载

###参考
http://www.alloyteam.com/2014/04/android-cha-jian-yuan-li-pou-xi/
http://blog.csdn.net/com360/article/details/14125683
http://blog.csdn.net/com360/article/details/14127395
