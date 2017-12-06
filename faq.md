# 疑难解答

### 安装成功，页面报500错误

请编辑.env文件，修改APP_DEBUG=true，执行`php artisan config:cache`，查看日志输出。

### 页面总是提示websocket连接异常

请检查socket服务运行是否正常，必要时可通过输入`supervisorctl`查看相关信息。以下是一个成功运行的例子：

```
$ supervisorctl
piplin:queue_0                   RUNNING   pid 16607, uptime 23:14:00
piplin:queue_1                   RUNNING   pid 16606, uptime 23:14:00
piplin:queue_2                   RUNNING   pid 16605, uptime 23:14:00
piplin-broadcast                 RUNNING   pid 16608, uptime 23:14:00
piplin-socketio                  RUNNING   pid 16604, uptime 23:14:00
supervisor> 

```

### 测试服务器连通状态，返回`Permission denied (publickey,password)`

请将项目的公钥追加到服务器执行任务用户目录的$HOME/.ssh/authorized_keys文件中。注意：.ssh/ 目录的权限应该被设置为700, authorized_keys 文件的权限应该被设置为600。公钥内容格式如下：
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDbeU5/HCoF52Kun+99w0AhHmMjglHqQHUS2y8XSL/lJxtx+cyiIkysdD/
f2FFk6TqeWJAUHtoFQRgjFRiNciPM50qwD/bgZvzVvsAkbQgpNnGofAx89M592BHaaaWBVZOREg/F/scT9z4Xq7VF+JtrM/l0yPNrY/
A0WzWf63nL1xmhpQU3XxEcIP74hNTAutONQJtyhxxxxxxedyrvA4e1XObnq8rHTBPIYQWC1azPEgJb/
DhNxXsjEiTkasBKvPiBItnnOc/jQBBaur8KvB7R7kLeYn3QOgGUE5jGq3OkDgHRTgnY2C4dKCtqFajGelwSYJcF3QjwhT11 
worker@piplin
```
