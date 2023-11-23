# 通过API获取字幕

## 概述

使用的API有：

- ‘https://api.bilibili.com/x/web-interface/view’ ，带参数`bvid`
- 'https://api.bilibili.com/x/player/pagelist?bvid=' +bvid，用于请求`cid`
- f'https://api.bilibili.com/x/player/v2?bvid={bvid}&cid={cid}' ，用于请求`subtitle_url`
- 返回的`subtitle_url`，用于获取字幕

详细抓取过程请见jupyter notebook
## workflow

```mermaid
graph TD

get{requests}

info(bili_info)
tags(bili_tags)
cid(cid)
bvid(bvid)
json_api(json_api)
subtitle_url(subtitle_url)
information((information))
subtitle_json((subtitle_json))

bvid --> get
get -.-> info
get -.-> tags

info --> information
tags --> information

get -.-> cid
bid(bvid) -.-> json_api
cid --> json_api
json_api --> subtitle_url
subtitle_url --> subtitle_json
```

## 关联数据库

在`Notion`中创建数据库，保存密钥

`secret_w4bNzNzvVF9N6FEQ5eVSyo1frjyCpB8PWcaXtMTi5hb`

<img src="https://mdstore.oss-cn-beijing.aliyuncs.com/background.jpg" alt="background" style="zoom:33%;" />

本地创建database

格式如下：

| NAME     | TYPE            |
| -------- | --------------- |
| title    | `title`         |
| cover    | `files & media` |
| URL      | `URL`           |
| UP主     | `text`          |
| 分区     | `select`        |
| tags     | `multi select`  |
| 发布时间 | `date`          |
| 加入时间 | `date`          |



复制链接`https://www.notion.so/kiharari/8a4650422a3c4bfc98d58c8ce863a5a5?v=b58e0bfbe42c475fb3b5e4b9a8da5022&pvs=4`

其中中间的一段`8a4650422a3c4bfc98d58c8ce863a5a5`为`database_id`

## ChatGPT API



| NAME | KEY |
|-----------|-----|
| bili_info |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|

## References
- https://developers.notion.com/reference/intro
