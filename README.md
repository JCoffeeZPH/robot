#### 1、部署上传springboot war包文件

tomcat所在文件路径：`/usr/local/apache-tomcat-9.0.54/`

打包项目为war包，用mac为例，上传命令为：

```java
scp /Users/penghui.zhang/Downloads/chat_robot.war root@8.218.14.137:/usr/local/apache-tomcat-9.0.54/webapps
// scp 本地文件路径 服务器登录username@ip:上传的文件保存到服务器路径
```

上传war包之后重启tomcat会自动解析，如上传的为chat.war，重启tomcat之后会在webapps目录下生成一个chat文件夹，访问路径也需要加上/chat，如果不想要文件夹名称前缀访问，则把chat 文件夹名称直接改为ROOT（只适用于单个Java服务），如果存在多个Java服务都不想有前缀访问，[tomcat部署war包时，访问路径如何取消包名前缀](https://blog.csdn.net/a624193873/article/details/103575732)

注意：上传的war包解压之后必须要有一份在/webapps下

#### 2、启动关闭tomcat

```java
// 进到/usr/local/apache-tomcat-9.0.54/bin目录下
// 启动
./start.sh
// 关闭
./shutdown.sh
// 后台启动
// nohup ./startup.sh &
```

#### 3、配置文件相关

进入到`/usr/local/apache-tomcat-9.0.54/conf`下，修改server.xml

* 修改端口(默认为8080)

![image](https://user-images.githubusercontent.com/43327981/142799679-84d81c98-feda-4ac7-8824-52935cb1efaa.png)

* 修改服务器访问(默认为localhost)

  ![image](https://user-images.githubusercontent.com/43327981/142799731-b13e3f9b-2ca1-4359-840e-c6a420803e3f.png)


说明：Java部署的时war包，是编译之后的.classs文件，无法看到源码，想要看编译之后的源码，可进入classes文件夹下com下查看.class文件

#### 3、robot_id相关

在/usr/local/apache-tomcat-9.0.54/webapps/ROOT/WEB-INF/classes目录下，修改application.yml文件对应robot_id配置，如下图

![image](https://user-images.githubusercontent.com/43327981/142799758-5d9cc544-07a0-4178-858a-322aace5289a.png)

重启服务即可

