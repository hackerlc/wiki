### android

#### IOC 控制反转框架
注解+反射机制来绑定控件和点击事件

```
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface BaseContentView {
    int value();
}
```
