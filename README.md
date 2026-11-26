# 微博数据接口（Weibo API）：微博搜索、详情、评论、热搜榜、用户

**微博数据 API · 微博搜索 · 微博评论采集 · 微博热搜榜 · 微博用户主页**

这个仓库是 [DataXAPI](https://dataxapi.com/zh/?ref=gh-weibo-api) 的微博接口说明和能直接跑的脚本：13 个接口，一把 Key，按次付费，$0.002 起，**出错不收费**。不用登录平台账号，不用 Cookie，不开浏览器。

[免费拿 Key：试用最多 333 次，不用绑卡](https://dataxapi.com/zh/signin/?button=gh-weibo-api) · [全部接口文档](https://dataxapi.com/zh/apis/?ref=gh-weibo-api) · [接进 AI（MCP）](#接进-aimcp) · [English](#english)

最低充 $10，余额不过期；支持支付宝、微信支付和银行卡。

## 全部 13 个接口

### 内容

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [微博实时搜索](https://dataxapi.com/zh/apis/weibo/posts/search/?ref=gh-weibo-api) | 按搜索词取一页微博，新发的在前：正文（长微博在这里是截短的）、作者和粉丝数、点赞、评论、转发数、视频播放数、图片、话题。 | $0.002 一次 | `weibo.posts.search` |
| [微博评论](https://dataxapi.com/zh/apis/weibo/posts/comments/list/?ref=gh-weibo-api) | 按微博编号取一页评论：正文、评论者、点赞数、回复数、发布时间、IP 属地。 | $0.002 一次 | `weibo.posts.comments.list` |
| [微博详情](https://dataxapi.com/zh/apis/weibo/posts/get/?ref=gh-weibo-api) | 按微博编号取一条微博：全文（长微博也是全文）、作者、点赞、评论、转发、阅读数（视频微博是播放数）、图片、话题、IP 属地。 | $0.002 一次 | `weibo.posts.get` |
| [微博视频转文字（文案提取、逐字稿）](https://dataxapi.com/zh/apis/weibo/posts/transcript/get/?ref=gh-weibo-api) | 给一条带视频的微博的链接、分享文字或编号，返回视频里说的话：全文、每一句的起止时间和现成的 SRT 字幕，连同正文、作者和时长；可以区分说话人。每次收费，识别语音的另按视频分钟数收，没人说话不收。5 分钟以内的视频直接返回文字；超过 5 分钟、2 小时以内的先回一个凭证（job），过一会儿带着它再调这个接口取文字，按实际分钟数收，只在取到文字时收。 | $0.002 一次 | `weibo.posts.transcript.get` |
| [微博点赞用户](https://dataxapi.com/zh/apis/weibo/posts/likers/list/?ref=gh-weibo-api) | 按微博编号取最近给这条微博点赞的账号，一次约 50 个：昵称、简介、头像、是否认证和认证类型、粉丝数、关注数、微博数，资料里填的性别和地区。 | $0.002 一次 | `weibo.posts.likers.list` |
| [微博视频和图片下载地址](https://dataxapi.com/zh/apis/weibo/posts/media/get/?ref=gh-weibo-api) | 给一条微博的编号、链接或分享文字，返回视频的各档清晰度（到 4K 的有几档给几档，带宽高、码率、大小、是否带水印和过期时间）、封面，或者每张图片的最大尺寸地址；只对视频微博和图片微博，纯文字的按没有文件返回。地址不用带请求头，过期了再调一次即可。 | $0.002 一次 | `weibo.posts.media.get` |

### 热榜和趋势

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [微博热搜榜](https://dataxapi.com/zh/apis/weibo/trends/list/?ref=gh-weibo-api) | 取微博当前的热搜榜，50 个词，带名次、热度和标签（新、热等）。 | $0.002 一次 | `weibo.trends.list` |

### 评论

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [微博评论回复](https://dataxapi.com/zh/apis/weibo/comments/replies/list/?ref=gh-weibo-api) | 按评论编号取一页回复：正文、回复者、点赞数、回复的是哪一条、发布时间、IP 属地。 | $0.002 一次 | `weibo.comments.replies.list` |

### 账号

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [微博用户粉丝列表](https://dataxapi.com/zh/apis/weibo/users/followers/list/?ref=gh-weibo-api) | 按用户编号取一页关注该微博用户的账号，每页 20 个：昵称、简介、头像、是否认证和认证类型、粉丝数、关注数、微博数、注册时间，资料里填的性别和地区。 | $0.002 一次 | `weibo.users.followers.list` |
| [微博用户资料](https://dataxapi.com/zh/apis/weibo/users/get/?ref=gh-weibo-api) | 按用户编号取微博用户资料：昵称、简介、头像、是否认证和认证说明、粉丝数、关注数、微博数，主页上的转评赞总数、获赞总数，性别和地区。 | $0.002 一次 | `weibo.users.get` |
| [微博用户微博](https://dataxapi.com/zh/apis/weibo/users/posts/list/?ref=gh-weibo-api) | 按用户编号取一页该用户主页上的微博（原创和转发），新的在前：正文（长微博在这里是截短的）、点赞、评论、转发数、视频播放数、图片、话题、IP 属地、是否置顶。 | $0.002 一次 | `weibo.users.posts.list` |
| [微博用户搜索](https://dataxapi.com/zh/apis/weibo/users/search/?ref=gh-weibo-api) | 按搜索词取一页微博用户：编号、昵称、头像、主页链接。 | $0.002 一次 | `weibo.users.search` |

### 备用版：原接口取不到时改调

| 接口 | 拿到什么 | 价格 | 编号 |
|---|---|---|---|
| [微博热搜榜（备用版）](https://dataxapi.com/zh/apis/weibo/backup/trends/list/?ref=gh-weibo-api) | 微博热搜榜的备用版，原接口取不到时改调：参数和返回相同，价格更高。 | $0.03 一次 | `weibo.backup.trends.list` |

## 真实返回长什么样

**微博实时搜索**（`weibo.posts.search`，参数 `{"query":"新能源汽车"}`），录下的真实返回，个人信息换成了 …：

```json
{
  "data": {
    "items": [
      {
        "id": "…",
        "url": "https://example.com/…",
        "type": "image",
        "text": "…",
        "published_at": "2026-10-12T18:01:10.000Z",
        "author": {
          "id": "…",
          "name": "…",
          "avatar_url": "https://example.com/…",
          "verified": false,
          "followers": 2568
        },
        "metrics": {
          "likes": 0,
          "comments": 3,
          "views": null,
          "reposts": 0
        },
        "images": [
          "https://example.com/…",
          "https://example.com/…"
        ],
        "hashtags": null
      }
    ]
  },
  "page": {
    "next_cursor": "example-cursor-1",
    "cursor_expires_at": "2026-10-12T20:03:07.000Z",
    "has_more": true,
    "returned": 9
  }
}
```

每个接口都是同一种结构：列表在 `data.items`，单个在 `data.item`，下一页用 `page.next_cursor`，这次扣了多少在 `meta.billing.amount`，平台不给的字段为 `null` 并在 `meta.unavailable` 里写明。

## 快速开始

1. [拿一把 Key](https://dataxapi.com/zh/signin/?button=gh-weibo-api)（`dx_` 开头），放进环境变量：`export DATAXAPI_API_KEY=dx_...`
2. 调一次接口：

```bash
curl -G "https://api.dataxapi.com/v1/weibo/posts/search" \
  -H "Authorization: Bearer $DATAXAPI_API_KEY" \
  --data-urlencode 'query=新能源汽车'
```

3. 或者跑 `examples/` 里的脚本。只用 Python 标准库（3.9 以上）；不加 `--yes` 只报价、不调用，加了才真跑，跑完告诉你实际花了多少：

| 脚本 | 做什么 | 先看要花多少 |
|---|---|---|
| [quickstart.py](examples/quickstart.py) | 取几页结果，存成 CSV | `cd examples && python3 quickstart.py 新能源汽车` |

## 接进 AI（MCP）

Claude Code：

```bash
claude mcp add --transport http --scope user dataxapi https://api.dataxapi.com/mcp --header "Authorization: Bearer $DATAXAPI_API_KEY"
```

Cursor、Cherry Studio、WorkBuddy 等支持远程 MCP 的客户端：

```json
{
  "mcpServers": {
    "dataxapi": {
      "url": "https://api.dataxapi.com/mcp",
      "headers": {
        "Authorization": "Bearer dx_..."
      }
    }
  }
}
```

接上以后直接用中文问，比如“帮我看看这个关键词最近一个月在抖音上的热度”。AI 花钱前可以先免费查接口和价格。也可以装成技能：`npx skills add data-x-api/skills`。

## 常见问题

**要不要平台账号、Cookie 或扫码？**

不要。只要一把 DataXAPI Key，不碰你的账号，也就不存在账号被风控的问题。

**调用出错扣钱吗？**

不扣。每次返回里的 `meta.billing.amount` 写明这次扣了多少（美元）。

**数据有多新？**

默认在你调用时从平台实时读取，返回里的 `meta.fetched_at` 写明读取时间。

**怎么翻页？**

列表接口一次返回一页，把返回里的 `page.next_cursor` 作为 `cursor` 传回去取下一页，每一页单独计费。

## English

Weibo API: post search, posts, comments, hot search list and users, through one key, paid per call.

No platform account, cookie or QR login. Paid per call from $0.002; errors are not charged. Free trial: up to 333 calls, no card. [Get a key](https://dataxapi.com/signin/?button=gh-weibo-api) · [All endpoints](https://dataxapi.com/apis/?ref=gh-weibo-api) · MCP: `https://api.dataxapi.com/mcp`.

## License

MIT

<sub>接口和价格取自 DataXAPI 的目录 0051cce45e9530b9、价格版本 22；以 [dataxapi.com/zh/apis](https://dataxapi.com/zh/apis/?ref=gh-weibo-api) 为准。</sub>
