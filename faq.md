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
