# AnyModelAudioToText 使用手册

## 这个工具是做什么的

把你电脑上的录音/音频文件自动转成文字。支持中文、法语、英语混合音频。

---

## 使用方法 — 图形界面（推荐）

### Windows

1. 下载 `AnyModelAudioToText-v*-windows.zip`，解压
2. 双击 `doubao-transcriber.exe`

### macOS

1. 下载 `AnyModelAudioToText-v*-macos-arm64.zip`，解压
2. 终端运行 `./doubao-transcriber`

### 操作步骤

1. 粘贴 API Key（以 `ark-` 开头）
2. 勾选「记住 API Key」，下次免输入
3. 选择语言（可选，默认自动识别）
4. 拖拽音频文件到灰色虚线区域
5. 点击「🚀 开始转写」
6. 日志区实时显示进度，完成后可「打开」结果目录

> ffmpeg 首次运行时会自动下载。国内用户自动走清华镜像源。

---

## 使用方法 — 命令行

```bash
# 双击运行 volc_auc_batch_client.exe（Windows）按提示输入
# 或直接传参
volc_auc_batch_client \
  --api-key "ark-..." \
  --inputs "音频.m4a"

# 仅检查/转换，不提交
volc_auc_batch_client --inputs "音频.m4a" --prepare-only
```

### 主要参数

| 参数 | 默认 | 说明 |
|------|------|------|
| `--provider` | ark | ark / las / volcengine / azure |
| `--api-key` | — | API Key（必填） |
| `--inputs` | — | 音频文件或 URL |
| `--language` | 自动 | zh-CN / fr-FR 等 |
| `--prepare-only` | false | 仅检查转换，不提交 |
| `--output-dir` | 桌面 | 输出目录 |

---

## 支持的格式

MP3 / WAV / M4A / AAC / OGG / FLAC / MP4 / WebM / Opus

---

## 输出

- `result_{文件名}.txt` — 转写文本
- `result.srt` — 字幕文件（LAS 后端）
- `manifest.json` — 处理汇总
