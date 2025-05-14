# Astrbot RSS订阅插件

![AstrbotPlugin-RSS](https://socialify.git.ci/QingFeng-awa/AstrbotPlugin-RSS/image?custom_description=%E6%94%AF%E6%8C%81%E9%80%9A%E8%BF%87RSSHub%E8%B7%AF%E7%94%B1%E5%92%8C%E7%9B%B4%E6%8E%A5URL%E8%AE%A2%E9%98%85RSS%E6%BA%90%EF%BC%8C%E5%B9%B6%E5%AE%9A%E6%97%B6%E8%8E%B7%E5%8F%96%E6%9C%80%E6%96%B0%E7%9A%84RSS%E5%86%85%E5%AE%B9%E3%80%82&description=1&font=KoHo&language=1&name=1&pattern=Circuit+Board&theme=Auto)

> [!note]
> 由于QQ官方对主动消息限制较为严重，因此主动推送不支持`qqofficial`消息平台。

## 功能

- 添加、列出和删除 RSSHub endpoint
- 通过 RSSHub 路由订阅 RSS 源
- 直接通过 URL 订阅 RSS 源
- 列出所有订阅
- 删除订阅
- 获取最新一条订阅内容

## 安装

在应用市场点击右下角+号,复制粘贴本仓库URL并点击安装。

## 使用

### RSSHub 相关指令

- `/rss rsshub add <url>`: 添加一个 RSSHub endpoint
- `/rss rsshub list`: 列出所有 RSSHub endpoint
- `/rss rsshub remove <idx>`: 删除一个 RSSHub endpoint

### 订阅相关指令
#### 通过 RSSHub 路由订阅

```
/rss add <idx> <route> <cron_expr>
```
`idx`为订阅的RSSHub ID,`route`为RSSHub路由,`cron_expr`为Cron表达式。

#### 直接通过URL订阅
```
/rss add-url <url> <cron_expr>
```
`url`为直接URL地址,`cron_expr`为Cron表达式。

#### 其他

- `/rss list`: 列出所有订阅
- `/rss remove <idx>`: 删除订阅
- `/rss get <idx>`: 获取最新一条订阅内容

### Cron 表达式

Cron 表达式格式：`* * * * *`，分别表示分钟、小时、日、月、星期，`*` 表示任意值，支持范围和逗号分隔。例：

1. `0 0 * * *` 表示每天 0 点触发。
2. `0/5 * * * *` 表示每 5 分钟触发。
3. `0 9-18 * * *` 表示每天 9 点到 18 点触发。
4. `0 0 1,15 * *` 表示每月 1 号和 15 号 0 点触发。

星期的取值范围是 0-6，0 表示星期天。

## 示例

### 从RSSHub订阅内容

首先使用指令 `/rss rsshub add https://rsshub.app` 添加官方 RSSHub 订阅站。\
然后使用指令 `/rss rsshub list` 查看刚刚添加的订阅站。


官方维护了很多可用的路由，涵盖了TelegramChannel、Bilibili、金融信息、高校官网信息等等。\
有关RSSHub所有可用的路由,请参阅[此处](https://docs.rsshub.app/zh/routes/popular)。


### 从自定义链接订阅内容

你可以使用指令 `/rss add-get <url> <cron_expr>` 订阅。\
如 `/rss add-get https://blog.lwl.lol/index.xml 0 * * * *`。\

> 目前仅支持 RSS 2.0 格式。
