## android 插件化学习梳理

###android类加载器DexClassLoader介绍

    在java中有个概念叫做“类加载器”(ClassLoader)，作用为动态加载class文件。
    ClassLoader装载机制暂时不做深究，可以[参考](http://www.iteye.com/topic/83978)
    android程序最后会产生dex文件，dex文件是一种经过android打包工具优化后的class文件，因为加载这样的特殊文件就需要特殊的装载器dexClassLoader

    这个类只有一个构造函数：
    ```
    public DexClassLoader (String dexPath, String optimizedDirectory, String libraryPath, ClassLoader parent)
    ```
    
