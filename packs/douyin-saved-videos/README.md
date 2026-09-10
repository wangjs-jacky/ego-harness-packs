# 抖音收藏视频只读提取

包名 `douyin-saved-videos`，版本 `0.1.0`。入口：[站点索引](sites/index.md)。

```bash
ego-harness add 'github:wangjs-jacky/ego-harness-packs#douyin-saved-videos'
ego-harness resolve douyin-saved-videos --json
```

对 Agent 说：“用 ego-harness 的 douyin-saved-videos 经验包，在我的授权账号中只读列出收藏视频的前 10 条，不修改收藏。”

## 来源与验证边界

- 来自作者现有 ego-ops 本地知识：`references/sites/douyin/operations/read-saved-videos.md`，原项目 [jacky-skills](https://github.com/wangjs-jacky/jacky-skills)。沿用原项目 [MIT 许可证](LICENSE)。
- Operation 正文与原始文件一致；历史 `last_verified` 为 **2026-09-02**。旧站点索引日期落后于 operation，本包仅把索引同步到该历史日期。2026-09-10 没有重新执行抖音网页任务。
- 本包只包含步骤，不包含收藏清单、视频样本、个人主页标识或登录材料。`/user/self` 指向执行者自己的当前账号，不是作者账号。
- 安装不会打开浏览器、登录或读取收藏。实际提取必须获得账号使用者授权，且不得添加、取消收藏或修改账号数据。
- 提取结果可能包含个人偏好，不应自动上传回经验仓库。只在用户指定范围内返回标题和链接，不把结果当作新的公共经验内容。
