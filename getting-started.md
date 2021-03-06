# 快速开始

### Piplin是做什么的？

Piplin是一款免费、开源的持续集成系统，适用于软件的自动化构建、测试和部署相关的各种应用场景。

![Screenshot](http://piplin.com/img/screenshot.png?v1)

### 为什么用Piplin这个名字？

Piplin(建议读作/ˈpɪpˌlɪn/)灵感来自于英文单词"Pipeline"，Pipeline中文的字面意思是：流水线、管道，很多持续集成系统里都有这个概念。Pipeline相当于一次持续集成任务，里面可以包含多个流程，如安装依赖、运行测试、编译、部署测试服务器、部署生产服务器等流程，这些都是Piplin所做的工作。所以我们把Pipeline这个词去掉2个不发音的e，得到piplin。

### 主要功能列表

* 支持PHP、Python、JAVA、Ruby等项目的构建、测试与发布
* 可与Gitlab、Github、Gogs、Gitee(Oschina)等代码托管平台进行集成
* 可灵活配置自定义构建和部署步骤
* 支持自定义构建物规则，对构建物创建发布版本并部署
* 支持项目的多环境部署(可自行建立开发、测试、预发布和生产等多个环境)
* 支持联动部署，比如：开发环境部署成功后可自动触发测试环境启动部署
* 服务管理支持机柜功能，机柜可与多个部署环境绑定
* 支持项目克隆与模板功能
* 项目支持多成员
* 通过Websocket实现项目部署状态的实时跟踪
* 支持钉钉机器人、Slack、邮件和自定义Webhook的服务集成

继续阅读有关 [系统要求](prerequisites.md) 的内容。
