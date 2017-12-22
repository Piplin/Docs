# 项目

### 项目设置

假设我们的服务器情况如下:

* Piplin宿主机：127.0.0.1
* 构建服务器：192.168.75.40
* 远程服务器：192.168.10.10

#### 一、创建项目
![project1](http://piplin.com/screenshots/project1.jpg)

创建成功后系统会自动进入项目详情页

![project2](http://piplin.com/screenshots/project2.jpg)

#### 二、设置构建计划

1、添加构建服务器
![project3](http://piplin.com/screenshots/project3.png)

2、将项目公钥添加到构建服务器
![project4](http://piplin.com/screenshots/project4.png)

```shell
ssh root@192.168.75.40
```

把以下内容追加到 ~/.ssh/authorized_keys

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC7E0tQBis2bl18L5bl0HsY+HYK4aYnF8bOOY+TnK5+QyWY/kfnza2P7mtU+B2bnEeihOUnty3oj+D2Uc8EtpHfe1BzjxB9iLgg0Fd5UZZ16ggBWnWmYk8u/Bq6AwSDlb/wWtBrmzWDwE8seFj7PMDEXeKj2fu0kVayqMKkhzhJc/WXVJ99wDnmrDYCBd4R8w6x2W5p/rkf+bWE8TIY7DpO4KRLspz+8MoXSUo6XEyF+gOy035oVwu3lSTXZ3luCSXVvHidGwtexAMRZPY4abi+X3DkYNjly0m6+Ku5GGdwfIAbbGdYfPwaERmjPKeCQTgOnO+EQppswE2ADCp+tpfj worker@piplin
```

3、开始测试构建服务器的连通状态
![project5](http://piplin.com/screenshots/project5.png)

一旦失败了，会有提示出错信息，这里提示项目路径没有创建

![project6](http://piplin.com/screenshots/project6.png)

我们登录这台服务器，创建一下项目路径

```shell
$ mkdir -p /var/www/piplin
```

再次开始测试，测试成功
![project6](http://piplin.com/screenshots/project6-1.png)

4、设置出品定义
![project10](http://piplin.com/screenshots/project10.png)

5、设置构建步骤，我们在开始构建的后置步骤做composer install，安装依赖包。

![project7](http://piplin.com/screenshots/project7.png)

6、添加后置命令：
![project8](http://piplin.com/screenshots/project8.png)

7、单元测试：这里我们简单做一下语法和注释的检查
![project9](http://piplin.com/screenshots/project9.png?rnd=1)

8、生成tar包
![project11](http://piplin.com/screenshots/project11.png?rnd=1)

9、导出tar包
![project13](http://piplin.com/screenshots/project13.png?rnd=1)

10、开始第一次构建
![project12](http://piplin.com/screenshots/project12.png?rnd=1)

构建成功，会有构建物产生(这里我们先不创建构建版本)
![project14](http://piplin.com/screenshots/project14.png?rnd=1)

#### 三、进行部署设置：

1、添加部署环境：

![project15](http://piplin.com/screenshots/project15.png)

2、往该环境里添加一台服务器

![project16](http://piplin.com/screenshots/project16.png)

填写服务器信息
![project17](http://piplin.com/screenshots/project17.png)

3、同样，这里也需要往这台服务器添加项目公钥，并创建项目路径

```shell
ssh root@192.168.10.10
```

```shell
$ mkdir -p /var/www/piplin
```
把以下内容追加到 ~/.ssh/authorized_keys

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC7E0tQBis2bl18L5bl0HsY+HYK4aYnF8bOOY+TnK5+QyWY/kfnza2P7mtU+B2bnEeihOUnty3oj+D2Uc8EtpHfe1BzjxB9iLgg0Fd5UZZ16ggBWnWmYk8u/Bq6AwSDlb/wWtBrmzWDwE8seFj7PMDEXeKj2fu0kVayqMKkhzhJc/WXVJ99wDnmrDYCBd4R8w6x2W5p/rkf+bWE8TIY7DpO4KRLspz+8MoXSUo6XEyF+gOy035oVwu3lSTXZ3luCSXVvHidGwtexAMRZPY4abi+X3DkYNjly0m6+Ku5GGdwfIAbbGdYfPwaERmjPKeCQTgOnO+EQppswE2ADCp+tpfj worker@piplin
```

4、测试服务器连通状态

![project18](http://piplin.com/screenshots/project18.png)

5、开始设置部署步骤

5.1、在安装新版本的后置命令中设置
![project19](http://piplin.com/screenshots/project19.png)

5.2、解压缩安装包，并将它删除
![project20](http://piplin.com/screenshots/project20.png)

5.3、更新缓存
![project21](http://piplin.com/screenshots/project21.png)

6、部署步骤全貌
![project22](http://piplin.com/screenshots/project22.png)

7、生成构建版本
![project23](http://piplin.com/screenshots/project23.png)

8、构建版本生成成功，从这里可以直接进入部署
![project24](http://piplin.com/screenshots/project24.png)

9、系统会自动选中构建版本
![project25](http://piplin.com/screenshots/project25.png)

10、部署成功
![project26](http://piplin.com/screenshots/project26.png)

11、让我们进入192.168.10.10看看项目的部署情况

![project27](http://piplin.com/screenshots/project27.png)

![project28](http://piplin.com/screenshots/project28.png)





