### Linux 命令

ls  |查看目录中文件

ls -l  |查看目录中文件权限

dir  |查看目录中文件

---

cd |进入当前用户主目录

cd .. |返回上级目录

cd ../.. |返回两级目录

cd /dir/dir/.../dir  |进入指定目录

pwd |显示当前目录路径

---

mkdir [dirname] |创建目录

mkdir [dirname] [dirname2] |创建两个目录

---

chmod -R 777 [dir/file] |设置文件或者文件夹权限

---

echo $JAVA_HOME  |显示环境变量路径

source /etc/profile |设置环境变量起作用

---

mv /dir/file /dir2/ |移动文件到指定目录

rm /dir/file |删除指定文件

cp /dir/file /dir2 |复制文件到指定目录

---

cat /dir/dir/.../file |显示文件信息

---

ssh-keygen -t rsa -C "xx@xx.com"  |创建ssh公秘钥

ssh -T xx@xx.com |ssh登录指定服务器

---
