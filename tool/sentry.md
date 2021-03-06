# Sentry

Sentry 是一个开源的实时错误报告工具，支持 web 前后端、移动应用以及游戏，支持
Python、OC、Java、Go、Node、Django、RoR 等[主流编程语言和框架](https://getsentry.com/platforms/)
，还提供了 GitHub、Slack、Trello 等常见开发工具的[集成](https://getsentry.com/integrations/)。

## 基本概念

### Sentry 是什么

通常我们所说的 Sentry 是指 Sentry 的后端服务，由 Django 编写。8.0 版本使用了 React.js
构建前端 UI。使用 Sentry 前还需要在自己的应用中配置 Sentry 的 SDK ——
通常在各语言的包管理工具中叫做 Raven。

当然，Sentry 还可以是其公司所提供的 Sentry SaaS 服务。

### DSN（Data Source Name）

Sentry 服务支持多用户、多团队、多应用管理，每个应用都对应一个 PROJECT_ID，以及用于身份认证的
PUBLIC_KEY 和 SECRET_KEY。由此组成一个这样的 DSN：

    '{PROTOCOL}://{PUBLIC_KEY}:{SECRET_KEY}@{HOST}/{PATH}{PROJECT_ID}'

PROTOCOL 通常会是 ``http`` 或者 ``https``，HOST 为 Sentry 服务的主机名和端口，PATH
通常为空。


## 部署 Sentry 服务

### 安装

由于 Sentry 依赖众多，建议在独立的 Virtualenv 中安装。Sentry 依赖 Unix 兼容系统、Python 2.7、
PostgreSQL 以及 Redis，确保你已经安装好了这些依赖。考虑到 Python WSGI 应用的部署，
你可能还需要 Nginx 或者 Apache 2 作为前端服务器，以及 supervisor 管理应用。

有了这些以后，Sentry 的安装就非常简单：``pip install sentry``。

### 配置

### 启动

我自己写了个[简单的 Supervisor配置文件](https://gist.github.com/kxxoling/e26827955a191cb6ab8f)，可供参考。


## 使用 Sentry SDK

Sentry 的 SDK 通常在各语言的包管理器中成为 Raven，使用起来也非常简单。以 Python 为例：

```python
from raven import Client
client = Client('https://<key>:<secret>@app.getsentry.com/<project>')

try:
    1 / 0
except ZeroDivisionError:
    client.captureException()
```

这样就可以使用 ``client`` 对象向 Sentry 服务器中提交日志信息了。

当然 Sentry 还为知名 web 框架提供了便捷的封装，以 Python Flask 框架为例：

```python
sentry = Sentry(dsn='http://public_key:secret_key@example.com/1')

def create_app():
    app = Flask(__name__)
	sentry.init_app(app, logging=True, level=logging.ERROR)
    return app
```

### 添加上下文信息

为了解决问题，通常还会需要上下文信息重现当时的问题，以及快速了解影响的范围。

```python
client.user_context({
	'email': request.user.email
})
```


## 使用 Sentry web 服务

### 搜索

Sentry 的搜索支持 ``token:value`` 语法，例如：

	is:resolved user.username:"Jane Doe" server:web-8 example error

支持的 token 包括：

- is：问题状态（resolved, unresolved, muted）
- assigned：问题的分配状态（用户 ID、用户 Email 或者 ``me``）
- release：指定发布版本中出现的问题
- user.id
- user.email
- user.username
- user.ip

### 通知
### 合并&样本
### 数据过滤

## 和其它服务集成
### 和 GitLab 集成
### 和 Trello 集成

## Docker 部署

Sentry 官方还提供了 Docker 镜像以及[部署方案](https://github.com/docker-library/docs/blob/master/sentry/variant-onbuild.md)，用起来非常方便。

0. 首先安装并启动 Docker 服务，然后拉取最新的 Sentry 镜像：``docker pull sentry``。
1. 启动一个 redis 服务作为消息 broker：``docker run -d --name sentry-redis redis``
2. 设置数据库密码作为环境变量，之后的命令都会用到：``export DBPW='<your-postgres-db-password>'``
3. 启动一个 Postgres 数据库服务作为存储数据库：``docker run -d --name sentry-postgres -e POSTGRES_PASSWORD='$(DBPW)' -e POSTGRES_USER=sentry postgres``
4. migrate 数据库解构至最新：``docker run -it --rm -e SENTRY_SECRET_KEY='$(DBPW)' --link sentry-postgres:postgres --link sentry-redis:redis sentry upgrade``
5. 启动 Sentry  并链接以上服务: ``docker run -d --name sentry-app -e SENTRY_SECRET_KEY='$(DBPW)' --link sentry-redis:redis --link sentry-postgres:postgres -p 8080:9000 sentry``
6. 运行一个 cron container 用于定时任务：``docker run -d --name sentry-cron -e SENTRY_SECRET_KEY='$(DBPW)' --link sentry-postgres:postgres --link sentry-redis:redis sentry run cron``
7. 运行一个 worker container 用户后台任务：``docker run -d --name sentry-worker-1 -e SENTRY_SECRET_KEY='$(DBPW)' --link sentry-postgres:postgres --link sentry-redis:redis sentry run worker``

如果没有什么错误发生，使用 ``docker ps`` 命令将会得到 sentry-app、sentry-posgres、sentry-redis、sentry-cron、sentry-worker-1 5 个正在运行的容器。

参考：

- [Sentry Python 文档](https://docs.getsentry.com/on-premise/clients/python)

[Sentry]: https://getsentry.com/

