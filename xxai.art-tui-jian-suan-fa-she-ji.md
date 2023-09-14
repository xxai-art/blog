# xxai.art · 推荐算法设计

### 开发环境搭建

确认有 https://github.com/aier-dev/conf 的访问权限

```
curl -s https://ghproxy.com/https://raw.githubusercontent.com/xxai-art/docker/main/dev/curl.sh | bash
```

### 表结构

启动之后访问 [http://localhost:8082](http://localhost:8082)

![](https://i-01.eu.org/2023/09/SxvhYuQ.webp)

用户名 `gt` 密码 `DPUBU6Ytyx47dh`

表结构见 [init.sql](https://github.com/xxai-art/rsrv/blob/main/init/init.sql)

其中 aid 代表 action id，含义见 [rsrv/xc/src/action.rs](https://github.com/xxai-art/rsrv/blob/main/xc/src/action.rs)

[aier-art/rec](https://github.com/aier-art/rec/blob/main/src/main.rs) 会读取数据库，更新每个图的质量分

[rsrv/xws/src/db/rec.rs](https://github.com/xxai-art/rsrv/blob/main/xws/src/db/rec.rs) 会根据用户每次点击和收藏，创建新的推荐序列

[web/src/db/recPool.coffee](https://github.com/xxai-art/web/blob/main/src/db/recPool.coffee) 会用下面的算法，抽取 41 个推荐序列+1 个全局推荐序列，给用户展示图片，被点击的推荐流会被再次置顶

[web/src/lib/sampling.coffee](https://github.com/xxai-art/web/blob/main/src/lib/sampling.coffee) 这是随机抽取的算法，魔改版的斐波那契数列
