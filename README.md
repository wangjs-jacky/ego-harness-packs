# Ego Harness Experience Packs

[中文使用说明](README_CN.md)

Independently installable browser-operation knowledge for [Ego Harness](https://github.com/wangjs-jacky/ego-harness). Experience content lives here, outside the CLI and bundled Skill. Download once, reuse locally, update explicitly.

## Available packs

| Pack | Operation | Historical verification |
| --- | --- | --- |
| [taobao-shopping](packs/taobao-shopping/README.md) | Read-only product search and comparison on Taobao | 2026-09-01 |
| [douyin-saved-videos](packs/douyin-saved-videos/README.md) | Read the first N saved videos from the authorized user's Douyin account | 2026-09-02 |

Both packs are version `0.1.0`. They contain instructions, not product samples, saved-video lists, account data, or login material. The original operation bodies and historical verification dates are preserved. Packaging on 2026-09-10 did **not** reverify the live websites.

## Install and use

Requires Node.js 22+, Git, and Ego Harness CLI.

```bash
npm install -g @wangjs-jacky/ego-harness
ego-harness skills install --env codex,claude-code --global
ego-harness add 'github:wangjs-jacky/ego-harness-packs#taobao-shopping'
ego-harness add 'github:wangjs-jacky/ego-harness-packs#douyin-saved-videos'
ego-harness resolve taobao-shopping --json
```

Ask your agent to use the named pack and explicitly state the read-only task. Browser execution additionally requires Ego Browser/Ego Lite and the user's own authorized login. Installation does not open a browser or perform website actions. Historical knowledge is not a guarantee that today's UI still matches.

Repeated `add` and `resolve` reuse the local pack without fetching. Website access still requires networking. Updates are explicit:

```bash
ego-harness update taobao-shopping
```

To pin a snapshot, pass `--ref <commit>` when installing. One repository may host multiple independently selected `packs/<name>` subtrees.

## Author and upload

Maintain an authoring folder separately from downloaded snapshots:

```bash
ego-harness link /path/to/your-pack
ego-harness validate /path/to/your-pack
ego-harness push your-pack --to 'github:owner/experience-repo#your-pack' --dry-run
ego-harness push your-pack --to 'github:owner/experience-repo#your-pack'
```

Replace the example source and alias with your own; the destination repository must already exist and you must have write access. Later `push your-pack` remembers its target. Do not upload private execution results. Never refresh `last_verified` unless the webpage operation was actually revalidated.

## Source and license

Selected from the author's existing local `ego-ops` experience in [jacky-skills](https://github.com/wangjs-jacky/jacky-skills). See each pack's README for provenance and limits. Distributed under the original [MIT license](LICENSE), also included in each pack.
