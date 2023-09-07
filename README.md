---
description: 人工智能时代 · 我们计算艺术
---

# xxAI.Art 内测 v0.1 2023-09-7

{% embed url="https://xxai.art/" %}
分享 Stable Diffustion 提示词 · 发现新的模型和Lora
{% endembed %}

**点上面链接访问网站。CDN用的是 Cloudflare ，中国用户用境外代理访问速度会更好。**

![xxai.art 网站截图](https://i-01.eu.org/2023/09/xw0hXTH.webp)

可以搜索 AI 生成的图片，浏览提示词，并根据做个性化的图片推荐。

![搜索『老虎』](https://i-01.eu.org/2023/09/ALINMve.webp)

![浏览提示词](https://i-01.eu.org/2023/09/p8GS2IL.webp)

欢迎大家试玩，有问题告诉我，目前还请不要转发。

等我实现以下功能点后，可以正式上线：

1. 实现虚拟滚动条，优化windows下的体验 (参考我以前写的 [scrollbar.vue](https://gist.github.com/zew13/a48b41505cbd52afa880435f9c115a25) )
2. 以图搜图
3. 对图片的不喜欢（包含分级错误、内容与搜索关键词无关等等）
4. 用户可以上传图片，自动提取图片中的元信息
5. 搭建一个自动翻译多国语言的技术博客
6. 各种社交媒体账号和功能更新日志文件通过 API 做数据打通
7. 对图片的留言评论交流聊天
8. 上线宣传的文案

上线后，将会开发的一系列功能

1. 小图片的自动超分
2. 收藏的时候可以自定义标签，并在个人页按标签筛选
3. 在线扩图，剪裁，下载壁纸
4. 可以售卖提示词或者图片生成教程
5. 图片转视频
6. 网站 & 爬虫运维监控

等等 ...

## 开发历程

2023 年 3 月 27 日，就想写这个网站，当天就去注册了域名。

2023 年 9 月 03 日，一个人写了半年，终于写出来第一版了。

### 代码开源

代码基本都开源，不过有点杂，没文档。

因为我目前还是专注于功能开发，不过一个人搞的确进度很慢。

但是欢迎大家参与研发，有协作需求我就会补文档。

如果擅长AI模型，欢迎联系我，我有很多想法但是不懂机器学习。

比如: 能不能用[ort](https://github.com/pykeio/ort)配合TVM加速模型推理，怎么训练鉴黄模型，怎么做图片扩增和高效率超分。

如果擅长编程，有兴趣的可以先帮忙研究下面几个我搞不定的问题，多谢（[点此通过谷歌论坛](https://groups.google.com/g/xxai-art) 联系） :

问题1 数据库插件编译: [postgresql 16beta1-alpine3.18 : build plugin , VARSIZE\_ANY\_EXHDR: symbol not found](https://www.spinics.net/lists/pgsql/msg217017.html)

问题2 rust redis客户端的 bug : [fred - 6.3.0 resp2: when use hmget with vec len = 1, will cause error T::from\_owned\_bytes(bytes.to\_vec()).ok\_or(RedisError::new\_parse("Cannot convert from bytes"](https://github.com/aembke/fred.rs/issues/158)

问题3 nodejs 多进程如何实现类似nginx -s reload [https://github.com/wacpkg/\_/blob/main/api/Http/boot.coffee](https://github.com/wacpkg/\_/blob/main/api/Http/boot.coffee) ( 这是我自己的写的类似nodejs多进程http server，进程没请求会自动退出释放资源，有点类似serverless，但是目前不能被kill只能kill -9，我想要类似 nginx -s reload的效果，也就是开一个新进程处理新请求，老进程处理完当前请求或者超时之后退出 )

另外我还魔改了[coffeescript语法](https://github.com/wactax/node/tree/main/coffee\_plus) 来方便在 svelte 中使用 ，但是魔改得非常 hack ，如果有喜欢玩编译器的，欢迎帮忙正规一点。

如果擅长区块链，可以一起研究下怎么在[Celestia](https://learnblockchain.cn/article/6141)上创建一个可以和[USDC](https://twitter.com/CelestiaOrg/status/1663584183460179968)打通的虚拟积分，我想将来让大家都可以把闲置的GPU拿来推理图片，把算力换成链上的积分。模型作者也可以托管模型赚钱。

懂外语的欢迎帮忙优化下多语言包，目前都是机器翻译的。

#### 多语言文件

* [网站整体的语言包](https://github.com/xxai-art/web/tree/main/i18n)
* [登录模块的语言包](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [网站多语言文档](https://github.com/xxai-doc)

#### 网站前端

* xxai.art [https://github.com/xxai-art/web](https://github.com/xxai-art/web)
* 用户系统
  * 交互 [https://github.com/wactax/ui](https://github.com/wactax/ui)
  * 样式 [https://github.com/wactax/styl](https://github.com/wactax/styl)

#### 网站后端 · rust 部分  ( xxai.art )

&#x20;[https://github.com/xxai-art/rsrv](https://github.com/xxai-art/rsrv)

#### 网站后端 · nodejs 部分 （ 用户系统 ）

* [https://github.com/wactax/api](https://github.com/wactax/api)
* [https://github.com/wactax/pkg](https://github.com/wactax/pkg)
  * [https://github.com/wacpkg](https://github.com/wacpkg)
  * svg转webp(用于图片验证码) [https://github.com/wactax/svg2webp](https://github.com/wactax/svg2webp)
* 杂七杂八的库 [https://github.com/wactax/node](https://github.com/wactax/node)&#x20;
* 对[fred](https://crates.io/crates/fred)的封装 [https://github.com/wactax/xedis](https://github.com/wactax/xedis)

#### 图片向量索引&搜索&#x20;

[https://github.com/xxai-art/clip-runtime](https://github.com/xxai-art/clip-runtime)

#### 根据用户行为日志对图片打分&#x20;

[https://github.com/aier-art/rec](./#https-github.com-xxai-art-docker)

#### 数据库的 docker compose

[https://github.com/xxai-art/docker](https://github.com/xxai-art/docker)

#### 图片美学打分

[https://github.com/xxai-art/iaa](https://github.com/xxai-art/iaa)

## 技术栈

网站目前用到了以下技术栈

### 数据库

* [时序数据库 greptime](https://greptime.com) 用来记录用户行为日志
* [向量数据库 qdrant](https://qdrant.tech) 用来做图片搜索和推荐
* [KvRocks](https://kvrocks.apache.org)
* [redis](https://redis.io)
* [postgresql](https://www.postgresql.org)

### 模型

鉴于本人不懂机器学习，以下模型都是直接用的官方训练的模型，没有微调。

* [ETA 图片美学打分](https://github.com/woshidandan/Image-Aesthetics-Assessment/blob/main/README\_CN.md)
* [AltCLIP-m18 图片-多语言对齐向量化](https://github.com/FlagAI-Open/FlagAI/blob/master/examples/AltCLIP-m18/README.md)

### 图片鉴黄

* [Private Detector](https://github.com/bumble-tech/private-detector)
* [nudenet](https://github.com/vladmandic/nudenet)
* [nsfwjs](https://github.com/infinitered/nsfwjs)

### 前端

* [svelte](https://svelte.dev)
* [vite](https://vitejs.dev)
* [stylus](https://stylus-lang.com)
* [pug](https://pugjs.org)

### 设计

* [字节图标库](https://iconpark.oceanengine.com/official)

### 开发语言

* [rust](https://www.rust-lang.org)
  * [napi-rs](https://napi.rs/)
  * [axum](https://github.com/tokio-rs/axum)
  * [fred](https://crates.io/crates/fred)
* [coffeescript](https://coffeescript.org)

