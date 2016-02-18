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
