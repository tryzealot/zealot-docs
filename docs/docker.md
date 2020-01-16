# Docker 安装部署

这是一篇手把手来指导使用 Docker 部署文档，同时也是解释[一键部署脚本]deployment.md)的分解

## 安装 Docker

按照[官方教程](https://get.docker.com/)安装

## 安装 Docker-Compose

按照[官方教程](https://docs.docker.com/compose/install/)安装

## 生成 .env 配置文件

从预先 `config.env` 配置文件复制一份部署使用的配置文件

## 配置域名

二次校验如果没有配置会再提醒

## 配置证书

部署脚本提供三种方式，就算使用最后一种生成的也是 https 的协议头

## 生成 docker-compose.yml

配置文件会生成至少四个服务（service），使用上面前两个证书方式会额外增加一个服务：

- `zealot-zealot`: 核心 Web 和 API 服务
- `zealot-worker`: 核心异步任务服务
- `zealot-postgres`: 数据库服务
- `zealot-redis`: 缓存服务
- `zealot-web`: 提供（服务和证书）反代的网关服务，非必需

## 创建持久化存储的 docker volumes

保存 zealot 和依赖服务的数据安全

- `zealot-app`: `zealot-zealot` 和 `zealot-worker` 强依赖
- `zealot-data`: 保存上传的应用、应用图标和调试文件
- `zealot-postgres`: 数据库数据
- `zealot-redis`: 缓存数据

`zealot-app` 和 `zealot-data` 还会被 `zealot-web` 使用用于静态文件托管，比如 js、css、图片和应用文件

> `zealot-app` 的数据仅作多服务之间共享使用实际上没有任何用户生产的数据，在每次 zealot 更新操作都需要删除并重新生成来保证新的变更不会被旧数据替换带来的问题。

## 拉取（更新）镜像

第一次使用会自动从 Docker hub 下载镜像，后续是更新操作，通常只会更新 zealot 镜像。其他几个依赖服务镜像都是固定版本号

## 设置数据库数据

第一次使用会初始化数据库、加载范例应用数据和设置管理员账号，后续这是因 zealot 更新需要的操作

## 运行 docker-compose

为了安全期间和用户的自定义操作需要手动执行 `docker-compose up -d` 来运行服务