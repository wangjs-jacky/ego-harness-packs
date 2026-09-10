# 淘宝商品只读搜索与比较

包名 `taobao-shopping`，版本 `0.1.0`。入口：[站点索引](sites/index.md)。

```bash
ego-harness add 'github:wangjs-jacky/ego-harness-packs#taobao-shopping'
ego-harness resolve taobao-shopping --json
```

对 Agent 说：“用 ego-harness 的 taobao-shopping 经验包，只读搜索并比较我指定的商品，不加入购物车、不下单。”

## 来源与验证边界

- 来自作者现有 ego-ops 本地知识：`references/sites/taobao/operations/search-compare-products.md`，原项目 [jacky-skills](https://github.com/wangjs-jacky/jacky-skills)。沿用原项目 [MIT 许可证](LICENSE)。
- Operation 正文与原始文件一致；历史 `last_verified` 为 **2026-09-01**。2026-09-10 只进行经验包整理与分发测试，没有重新执行淘宝网页任务。
- 本包不包含商品样本、订单、账号资料或登录材料。浏览器与登录态由使用者自行提供；安装经验包不代表已登录或当前页面仍适用。
- 只读范围不包含加入购物车、收藏、聊天、下单或付款；遇到登录、验证码、规格与价格不明确时停止。
- 价格、库存、运费和优惠应在实际执行时重新确认，不能把历史经验当作实时商品信息。
