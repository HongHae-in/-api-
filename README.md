# -api-

一些视频源接口合集 | A Collection of Video Source APIs

## 项目说明 / Description

本项目收集整理了各类视频点播源和视频解析器接口，方便用户集成到自己的应用中使用。

This project collects and organizes various video on-demand (VOD) sources and video parser APIs for easy integration into user applications.

## 📂 文件结构 / Project Structure

```
-api-/
├── README.md                 # 项目说明文档
├── sources/                  # 资源目录
│   ├── vod-sources.json      # 点播视频源集合 (VOD sources)
│   └── parsers.json          # 视频解析器集合 (Video parsers)
└── LICENSE                   # GPLv3 许可证
```

## 📋 资源说明 / Resources

### 1. 点播视频源 (VOD Sources)
文件: `sources/vod-sources.json`

包含40+个视频点播源，每个源包含以下信息：
- `name`: 源名称 (中文)
- `nameEn`: 英文名称 (部分源)
- `category`: 分类
- `url`: API接口地址

**使用示例** / Usage Example:
```json
{
  "name": "海外看",
  "url": "https://haiwaikan.com/api.php/provide/vod/"
}
```

### 2. 视频解析器 (Video Parsers)
文件: `sources/parsers.json`

包含14+个视频解析器，用于解析各类视频链接。每个解析器包含：
- `name`: 解析器名称
- `url`: 解析器地址（参数：?url=VIDEO_URL）

**使用示例** / Usage Example:
```
https://jx.xmflv.com/?url=https://example.com/video.m3u8
```

## 🚀 快速开始 / Getting Started

### 使用JSON文件
直接导入 `vod-sources.json` 或 `parsers.json` 到你的应用中：

```javascript
// Node.js 示例
const vodSources = require('./sources/vod-sources.json');
const parsers = require('./sources/parsers.json');

console.log(vodSources.sources[0]); // 第一个视频源
console.log(parsers.parsers[0]);     // 第一个解析器
```

```python
# Python 示例
import json

with open('sources/vod-sources.json', 'r', encoding='utf-8') as f:
    vod_sources = json.load(f)

with open('sources/parsers.json', 'r', encoding='utf-8') as f:
    parsers = json.load(f)

print(vod_sources['sources'][0])  # 第一个视频源
```

## ⚠️ 免责声明 / Disclaimer

- 本项目仅供学习交流使用，不对任何源站的内容合法性负责
- 使用这些资源时，请确保遵守当地法律法规
- 作者不对因使用本项目资源造成的任何后果负责

This project is for educational and learning purposes only. Users are responsible for their own compliance with local laws and regulations when using these resources.

## 📝 许可证 / License

本项目采用 GPLv3 许可证 / Licensed under GPLv3

## 🤝 贡献 / Contributing

欢迎提交 Issue 和 Pull Request 来改进本项目！

Feel free to submit issues and pull requests to improve this project!
