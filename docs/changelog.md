# 变更日志

## 未发布

> 如下罗列的变更是还未发布的列表，代码变更历史：[未发布]

## 4.0.0 (2020-12-31)

### 修复

- [Web] 修正文件解析 iOS 证书对失效时间判断异常造成的页面错误显示
- [Web] 忽略默认开发版本号检查新版本

> 代码变更历史：[4.0.0]

## 4.0.0.rc2 (2020-12-25)
### 新功能

- [Web] 新的文件解析会保存到列表，上传的应用也会同步一份文件解析（异步任务） [#346](https://github.com/tryzealot/zealot/pull/346)
- [Web] 控制面板新增文件解析数据统计
- [Web] 控制面板针对管理员新增网络钩子、后台任务和磁盘使用的数据统计
- [Web] 版本详情提示文件缺失增加有权限者快速删除功能
### 变更

- [API] 调试文件版本检查接口改名并新增按照文件指纹和 dSYM uuid 检查是否存在 [#349](https://github.com/tryzealot/zealot/pull/346)

### 修复

- [Web] 修复禁用 LDAP 登录认证报错（ IP 白名单设置错误）
- [Web] 修正 Android 微信打开版本详情提示的文案


> 代码变更历史：[4.0.0.rc2]

## 4.0.0.rc1 (2020-10-29)

### 变更

- [Docker] **重大变更** 合并 rails 和 worker 到同一镜像部署需要同步更新 zealot-docker 库 [#235](https://github.com/tryzealot/zealot/pull/235)
- [Docker] Ruby 升级 2.7 部署
- [Web] font-awesome 从 4.7.0 升级至 5.13.0，可能会有遗漏的 Icon 显示不正常
- [Web] 调整邀请邮件的文案
- [Web] 应用和调试文件下载路径统一到 `/download` 路径
- [Web] 在线解析应用需要登录权限
- [Web] 优化已经删除的或不存在的版本详情地址会自动跳转最新版本
- [Web] 应用安装和下载逻辑做了调整（主要 iPadOS UserAgent 和 Desktop 一样无法判断）

### 新功能

- [Web] 涉及下载文件不存在会提示无法下载
- [Web] 在线解析支持 .mobileprovision 格式文件以及解析 .ipa 新增开启功能等
- [Web] 部分系统设置可以使用管理员面板在线修改 [#245](https://github.com/tryzealot/zealot/pull/245)
- [Web] 新增游客模式 [#243](https://github.com/tryzealot/zealot/pull/243)
- [Web] 支持显示 iOS AdHoc 版本测试设备的名称 [#211](https://github.com/tryzealot/zealot/pull/211)
- [Web] 支持解析已上传版本安装包的内容 [#210](https://github.com/tryzealot/zealot/pull/210)
- [Web] 支持获取 iOS 设备 UDID 功能 [#203](https://github.com/tryzealot/zealot/pull/203)
- [Web] 支持定期数据初始化且有功能限制的演示模式 [#198](https://github.com/tryzealot/zealot/pull/198)
- [Web] 上传 App 后在版本详情显示原本应用的名称
- [Web] 可通过版本、Git 分支、打包类型筛选过滤应用列表
- [Web] 版本详情最近上传关联 git commit 链接（如果在渠道设置了 git url）
- [Web] LDAP 登录融合到现有登录界面，不再使用第三方依赖提供的简陋界面
- [Task] 支持通过 rails 命令管理生成恢复数据备份功能（数据库、上传文件数据）[#207](https://github.com/tryzealot/zealot/pull/207)
- [API] 新增检查调试文件是否存在接口 `/api/debug_files/version_exist`

### 修复

- [Web] 修复上传 App 填写变更日志解析报错
- [Web] 解决版本详情中二维码在中等分辨率会超出父视图
- [Web] 解决应用渠道一些值为空确没有不显示默认值
- [Web] 优化在线解析 iOS 包的内容展示（和永远展示假数据的问题）
- [Web] 解决版本详情在使用 [fastlane-plugin-ci_changelog](https://github.com/icyleaf/fastlane-plugin-ci_changelog) 生成的变更日志没有展示提交者信息
- [Web] 修复并优化检查新版本逻辑
- [Web] 修复删除调试文件确认弹窗信息获取为空
- [Web] 优化版本详情设备列表在一些手机的显示方式
- [Web] 修复解析应用在不传参数提交的报错
- [Web] 优化版本列表在手机查看
- [Web] 渠道版本的最近上传动态仅显示底部分页，上部改为版本总数
- [Web] 修复管理员编辑用户留空密码提示不能为空
- [Web/API] 修复在线下载和安装版本不存在时会采用最新版本
- [Web] 修复游客模式登录界面会显示边栏菜单
- [Web] 修复上传同一应用同一平台调试文件总是会被覆盖的问题
- [Web] 系统设置页面优化对布尔类型、字典类型的显示
- [Task] 修复定时任务来清理老版本时因版本判断错误发生的误删版本
- [Docker] 修复因为 volume 存储 public 文件夹造成内部静态资源不会更新
- [Docker] 容器内的版本和外部不一致

> 代码变更历史：[4.0.0.rc1]

## 4.0.0.beta4 (2020-05-07)

### 新功能

- [Docker] 支持 Heroku 部署
- [Web] 游客模式允许查看 App 详情、列表和上传 App 详情
- [API] 上传 App 支持自定义字段 [#178](https://github.com/tryzealot/zealot/issues/178)
- [Web/API] 上传 App 传递了 `branch` 值开头包含 `origin/` 开头会自动清理掉
- [Web] 登录、注册、找回密码、重设密码等用户认证界面增加项目简介

### 修复

- [Web] 修正用户密码描述文案
- [Web] 修复网络钩子（WebHook）包含 url 字段的地址错误
- [Web/API] 修复上传 iOS dSYM 文件上传报错
- [API] 修复获取 App 接口 has_password 参数异常
- [API] 修复上传 App 记录的 source 来源都是 Web
- [API] 修复并支持上传 App 传递字符串类型的 json 格式的 changelog
- [Web] 修复系统信息没有正常获取 CPU 和内存信息
- [Web] 修复在线解析 Android 应用偶尔报错
- [Web] 修复使用微信扫描二维码页面报错

### 变更

- [API] 应用最新版本接口(`apps/latest`)增加 bundle_id 纬度的验证
- [Web] 游客模式可以访问应用版本详情和下载操作
- [Web] 应用版本详情对于 iOS AdHoc 右侧的设备列表左移并默认收起状态
- [Web] 开发环境移除 GraphQL 控制台功能，推荐使用 [graphql-playground](https://github.com/prisma-labs/graphql-playground)
- [Web] 页面底部移除 footbar，版本信息可以在系统信息查看

> 代码变更历史：[4.0.0.beta4]

## 4.0.0.beta3 (2020-01-16)

### 新功能

- [Web] 管理员添加的用户在邮箱未激活会提示并显示确认邮箱的链接
- [Web] 默认开启 Sentry 匿名上报机制（可关闭）

### 修复

- [API] 修复上传应用总会创建新渠道
- [Web/API] 修复上传 Android 应用无法显示图标

### 变更

- [Docker] 初始化数据从镜像移出到 [zealot-docker](https://github.com/tryzealot/zealot-docker) 操作 [#120](https://github.com/tryzealot/zealot/pull/120)
- [Docker] 精简镜像的体积大小从 1.18G 降到 308M [#114](https://github.com/tryzealot/zealot/issues/114)
- [Worker] 使用异步任务代替传统 cron job 来实现定时清理老版本历史包文件（可关闭）
- [Worker] 对异步任务进行分组和设置优先级
- [API] 所有报错信息改成中文显示，因数据库写操作会返回具体错误信息
- [Web] 使用 Rubocop Lint 规范化代码

> 代码变更历史：[4.0.0.beta3]

## 4.0.0.beta2 (2020-01-10)

### 新功能

- [Web] 新增上传到具体应用渠道的全部版本列表同时支持删除操作

### 修复

- [Web] 对于上传应用不是有效 ipa 或 apk 的会给予错误提示而不是报错
- [API] 修复获取应用最新版本列表因查询版本号不存在数据库无法返回最新版本列表
- [API] 只针对写操作的接口才会要求 token 验证（之前是绝大部分都需要）

> 代码变更历史：[4.0.0.beta2]

## 4.0.0.beta1

🌈 第一个公测版本发布啦

[未发布]: https://github.com/tryzealot/zealot/compare/4.0.0...HEAD
[4.0.0]: https://github.com/tryzealot/zealot/compare/4.0.0.rc2...4.0.0
[4.0.0.rc2]: https://github.com/tryzealot/zealot/compare/4.0.0.rc1...4.0.0.rc2
[4.0.0.rc1]: https://github.com/tryzealot/zealot/compare/4.0.0.beta4...4.0.0.rc1
[4.0.0.beta4]: https://github.com/tryzealot/zealot/compare/4.0.0.beta3...4.0.0.beta4
[4.0.0.beta3]: https://github.com/tryzealot/zealot/compare/4.0.0.beta2...4.0.0.beta3
[4.0.0.beta2]: https://github.com/tryzealot/zealot/compare/4.0.0.beta1...4.0.0.beta2
