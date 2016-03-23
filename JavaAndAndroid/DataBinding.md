### DataBinding

#### 1.android studio 
最好把as升级到2.0+版本，对DataBinding支持比较好
下面都是基于2.0+版本的操作
#### 2.build.gradle

classpath 'com.android.tools.build:gradle:1.5.0'

or

classpath 'com.android.tools.build:gradle:1.5.+'

保证下载库为jcenter()

#### 3.build.gradle (app)

添加：
```
    dataBinding{
        enabled true
    }
```
程序会自动下载相应的文件

#### 4.Create POJO Class
```
public class User {
    private String id;
    private String user;
    private String pwd;

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getUser() {
        return user;
    }

    public void setUser(String user) {
        this.user = user;
    }

    public String getPwd() {
        return pwd;
    }

    public void setPwd(String pwd) {
        this.pwd = pwd;
    }
}
```


#### 5.Create Layout
```
<?xml version="1.0" encoding="utf-8"?>
<layout xmlns:android="http://schemas.android.com/apk/res/android">

    <data>

        <import type="gear.yc.com.gearapplication.pojo.User" />

        <variable
            name="user"
            type="User" />
    </data>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="@{user.id}"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="@{user.user}"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="@{user.pwd}"/>
    </LinearLayout>
</layout>

```

#### 6.Create Activity
onCreate 加入下面代码
```
        ActivityDatabindingBinding binding = DataBindingUtil.setContentView(this,R.layout.activity_databinding);
        User user=new User();
        user.setId("2213");
        user.setUser("Joker");
        user.setPwd("123123");
        binding.setUser(user);
```
ActivityDatabindingBinding 是根据你的layout名字自动生成的
#### 7.Run app

#### 引用
http://www.jianshu.com/p/b1df61a4df77
