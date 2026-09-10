# Ego Harness 站点经验包

[English](README.md)

这里存放可独立安装的站点经验，不把个人经验重新塞进 CLI 或 Skill。遵循 `sites + operations` 结构：首次下载、本地复用、显式更新。

## 首批经验

| 包名 | 能做什么 | 原始网页验证日期 |
| --- | --- | --- |
| [taobao-shopping](packs/taobao-shopping/README.md) | 淘宝商品只读搜索与比较，不加入购物车、不下单 | 2026-09-01 |
| [douyin-saved-videos](packs/douyin-saved-videos/README.md) | 在使用者授权下读取其收藏中的前 N 个视频，不修改收藏 | 2026-09-02 |

两包版本均为 `0.1.0`。只分发操作步骤，不包含商品样本、收藏清单、账号资料或登录材料。2026-09-10 进行了迁移整理，保留原 operation 正文与历史验证日期；本次没有重新执行网页任务。原始经验未被覆盖。

## 直接复用

需要 Node.js 22+ 和 Git。还未安装 CLI 和配套 Skill 时先执行：

```bash
npm install -g @wangjs-jacky/ego-harness
ego-harness skills install --env codex,claude-code --global
```

按需安装其中一个或两个包：

```bash
ego-harness add 'github:wangjs-jacky/ego-harness-packs#taobao-shopping'
ego-harness add 'github:wangjs-jacky/ego-harness-packs#douyin-saved-videos'
```

然后对 Agent 说：

> 用 ego-harness 的 taobao-shopping 经验包，只读搜索并比较我指定的商品，不加入购物车、不下单。

或：

> 用 ego-harness 的 douyin-saved-videos 经验包，在我的授权账号中只读列出收藏视频的前 10 条，不修改收藏。

执行网页任务还需要 Ego Browser/Ego Lite 及使用者自己的登录态。安装包不等于登录、执行或证明页面仍适用；执行前必须重新确认入口、权限与对象。收藏结果可能包含个人偏好，不应自动上传到本仓库。

## 本地读取与更新

```bash
ego-harness resolve taobao-shopping --json
ego-harness list --json
ego-harness update taobao-shopping
```

前两条只读本地；只有明确 `update` 才主动获取新版。重复 `add` 同一个来源和 ref 也复用本地。需要固定版本时，安装加 `--ref <commit>`；同名包需要共存时用 `--as <别名>`。

## 作者上传流程

```bash
ego-harness link /path/to/your-pack
ego-harness validate /path/to/your-pack
ego-harness push your-pack --to 'github:owner/experience-repo#your-pack' --dry-run
ego-harness push your-pack --to 'github:owner/experience-repo#your-pack'
```

替换示例路径、包名和仓库；仓库须预先存在且当前 Git 身份有写权限。只上传选定 `packs/<包名>`，不会上传整个工作目录。首次成功后，`push your-pack` 会记住目标。用户下载的快照与作者工作目录分开管理。

原始经验来自 [jacky-skills](https://github.com/wangjs-jacky/jacky-skills) 中作者本地维护的 ego-ops 知识；每包 README 记录来源与使用边界，并保留原 [MIT 许可证](LICENSE)。
