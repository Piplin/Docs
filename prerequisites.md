# 系统要求

### 基础软件

和很多开源的Web项目相比，Piplin是一款比较复杂的系统，我们依赖了一些的软件来支撑这些复杂的功能。

- Web服务器: Nginx, Apache (with mod_rewrite)，或 Lighttpd都可以，但我们强烈推荐使用Nginx
- [PHP](http://www.php.net) 7.0.0+
- 数据库 [MySQL](https://www.mysql.com) 或 [PostgreSQL](http://www.postgresql.org) ([SQLite](https://www.sqlite.org) 也可以运行，但不推荐使用).
- [Composer](https://getcomposer.org)
- [Redis](http://redis.io)，Piplin广播驱动用的是Redis，所以Redis是必须的。
- [Node.js](https://nodejs.org/)，Websocket Server需要它。
- [Beanstalkd](http://kr.github.io/beanstalkd/) 我们用Beanstalkd作为默认的队列系统，当然你也可以用Redis等

**增强服务**

- [Supervisord](http://supervisord.org) Piplin使用Supervisord来管理websocket和队列等后台进程，虽然这并不是必须的，但我们强烈建议你使用它。
- [缓存驱动](http://laravel.com/docs/5.5/cache), 建议使用Memcached或Redis

### 系统要求

Piplin只支持 **类Unix** 操作系统(如: Linux, Freebsd, Mac OS等)。和其他的web项目不同，我们有很多工作是仰赖于终端命令来实现的。有很多朋友问我什么时候支持windows，我目前唯一想到的是：在windows下用类似于Git bash的方案是不是可以，我没有亲自试验过，你可以尝试一下。

Piplin不会支持虚拟主机。我理解的虚拟主机应该是只有通过ftp来上传文件的权限，而Piplin需要有执行ssh的能力。所以只能对使用虚拟主机的用户说抱歉了。

### Web服务器

#### Nginx要求

Nginx是被我们推荐的web服务器，它同时还非常完美的支持做我们的Websocket代理。Nginx和PHP最好的合作模式是使用`php-fpm`

#### Apache要求

如果你用的是Apache，那么以下模块可能Apache的默认模式没有开启，记得要安装并开启他们:

* `mod_rewrite`
* `mod_ssl` (如果需要以SSL模式运行Piplin的话)

> 为了能支持rewrite，你需要在apache配置文件的`<Directory>`区块内设置`AllowOveride All`，或者在`.htaccess`的`<VirtualHost>` 区块里去设置。

### PHP要求

PHP自身的版本我们在前面已经交代了，必须是PHP7.0+，同时我们你还需要确保安装了以下PHP扩展:

* `gd` (处理头像)
* `fileinfo` (处理头像和和版本发布都需要它)
* `curl` (涉及到和外部的请求都需要它)
* `openssl` (加密封装库)
* `mbstring` (各种语言都有自己的编码，需要用它来转换)

以下模块通常都是默认打开的:

* `tokenizer`
* `json`
* `pdo`
* `phar`

我们原生支持3种数据库 `mysql`, `pgsql` 和 `sqlite`， 所以你还需要安装它们的`pdo` 驱动，请根据你的实际情况进行选择安装。

很多朋友用的是一键安装套件安装的LNMP环境，这些套件可能会出于安全原因关闭一些函数，如[proc_open](http://php.net/manual/en/function.proc-open.php)。如果你安装过程中遇到报错，请记得在`php.ini`的`disable_functions`里打开它们，或者干脆在安装的时候把`disable_functions`注释掉，安装完成之后再取消注释。

### 系统命令

#### Piplin宿主机
Piplin用到了很多的系统命令，你需要确保以下命令是可执行的。举例：假设你不能确定rsync是否安装，可以用`which rsync`来检查，以此类推。

* `ssh` (连接你的远程服务器和构建代理都需要它)
* `ssh-keygen` (生成秘钥用的)
* `rsync` (跨服务期间传输文件用的)
* `git` (代码检出)

#### 构建服务器和远程服务器需要

* `ssh`
* `bash`

继续阅读有关 [安装与升级](installation.md) 的内容。
