### android

#### IOC 控制反转框架
注解+反射机制来绑定控件和点击事件

```
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface BaseContentView {
    int value();
}

    /**
     * 注入布局
     * @param activity
     */
    private static void injectContentView(Activity activity){
        Class<? extends Activity> clazz =activity.getClass();
        //查询是否存在BaseContentView注解
        BaseContentView baseContentView=clazz.getAnnotation(BaseContentView.class);
        if(baseContentView!=null){
            //获得layoutId值
            int contentViewLayoutId = baseContentView.value();

            try {
                //获得加载layout方法以及参数类型
                Method method = clazz.getMethod(METHOD_SET_CONTENT_VIEW,int.class);
                //开启语言访问检查
                method.setAccessible(true);
                //调用方法
                method.invoke(activity, contentViewLayoutId);
            } catch (Exception  e) {
                e.printStackTrace();
            }
        }
    }
```

##### 注解
###### @target
@Target(ElementType.TYPE) //接口、类、枚举、注解

@Target(ElementType.FIELD) //字段、枚举的常量 

@Target(ElementType.METHOD) //方法 

@Target(ElementType.PARAMETER) //方法参数 

@Target(ElementType.CONSTRUCTOR) //构造函数 

@Target(ElementType.LOCAL_VARIABLE)//局部变量 

@Target(ElementType.ANNOTATION_TYPE)//注解 

@Target(ElementType.package) ///包 

这里可以使用多个，比如:@Target({ElementType.TYPE,ElementType.METHOD})
