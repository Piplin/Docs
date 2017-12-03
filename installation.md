# 安装与升级

### 全新安装

#### 一. 克隆代码

```shell
$ git clone https://github.com/Piplin/Piplin.git piplin
```

#### 二. 安装依赖包

```shell
$ cd piplin
$ make
```

> 安装过程如出现卡顿，请尝试更换npm镜像: `npm config set registry http://registry.npm.taobao.org/`

#### 三. 安装Piplin

```shell
$ make install
```

> Piplin安装器会进入一个交互式控制台，请根据提示进行相关参数设置。

#### 四. 请将Web服务器的根目录指向 `public/`, 请参考 [examples/](/examples) 下的相关配置文件，里面包含 Apache和Nginx的配置范例.

> 注意: `examples/` 提供的仅仅是范例，并不能保证直接拷贝就能使用，需要根据实际情况进行相关配置调整。

#### 五. 配置supervisord

Piplin使用`supervisord`进行后台进程管理。该配置范例请查看[examples/supervisor.conf](examples/supervisor.conf)。 一般supervisord的主配置文件在 `/etc/supervisor/supervisord.conf` ，其大致内容：

```
[unix_http_server]
file=/var/run/supervisor.sock   ; (the path to the socket file)
chmod=0700                       ; sockef file mode (default 0700)

......

[include]
files = /etc/supervisor/conf.d/*.conf
```

##### 配置步骤如下：

1). 拷贝 examples/supervisor.conf

```shell
$ cp examples/supervisor.conf /etc/supervisor/conf.d/piplin.conf
$ vi /etc/supervisor/conf.d/piplin.conf
```

> 请根据实际情况修改相关参数设置，尤其注意路径相关的参数。

2). 重启supervisord

```shell
$ /etc/init.d/supervisord restart 或 service supervisord restart
```

3). 检查supervisord服务是否正常

```shell
$ supervisorctl
```

如果返回如下信息，代表服务正常:

```
piplin:queue_0                   RUNNING   pid 26981, uptime 2 days, 15:30:59
piplin:queue_1                   RUNNING   pid 26980, uptime 2 days, 15:30:59
piplin:queue_2                   RUNNING   pid 26979, uptime 2 days, 15:30:59
piplin-broadcast                 RUNNING   pid 26987, uptime 2 days, 15:30:59
piplin-socketio                  RUNNING   pid 26978, uptime 2 days, 15:30:59
supervisor>
```

六. 访问Piplin

恭喜！您已完成Piplin的安装。请通过浏览器访问安装过程中设置的应用网址。

> 计划任务相关的设置请看 [examples/crontab](examples/crontab).


### 升级

一. 获取最新代码

```shell
$ git fetch --all
$ git checkout 0.4.5
 ```

二. 升级

```shell
$ make update
```
