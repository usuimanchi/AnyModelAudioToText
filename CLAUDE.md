# CLAUDE.md

## 版本发布流程

每次更新代码后发布新版本时：

1. **更新 `dist/更新说明.txt`** — 面向用户，说明新增/变更/修复的功能，不提技术细节
2. **更新 `Cargo.toml`** 版本号
3. **打 git tag**（如 `v0.2.3`），否则 `build.rs` 中的 `git describe` 显示偏移量而非版本号
4. **`cargo build --release`** — 打 tag 后需重新编译
5. **复制到 dist**：`cp target/release/volc_auc_batch_client.exe dist/`
6. **更新 `dist/使用手册.txt`** — 如果 CLI 参数或默认值变化

## 提供商命名

| Provider | 显示名称 |
|----------|---------|
| Ark | 火山方舟豆包（volcengine ark doubao） |
| LAS | 火山引擎 AI数据湖服务（volcengine） |
| Volcengine | 火山方舟录音文件识别服务 |
| Azure | Azure Speech-to-Text |

## 项目结构

- `src/ark.rs` — Ark (doubao-seed-2-0-lite) 后端，Files API + file_id，temperature=0，thinking=disabled
- `src/main.rs` — CLI 编排、banner、合并逻辑、管道
- `src/audio.rs` — ffmpeg/ffprobe 音频处理、切分
- `dist/` — 发布文件（volc_auc_batch_client.exe、ffmpeg.exe、ffprobe.exe、使用手册.txt、更新说明.txt）
