# -api-

一些视频源接口合集 | A Collection of Video Source APIs

## 项目说明 / Description

本项目收集整理了各类视频点播源和视频解析器接口，方便用户集成到自己的应用中使用。

This project collects and organizes various video on-demand (VOD) sources and video parser APIs for easy integration into user applications.

## 📂 文件结构 / Project Structure

```
-api-/
├── README.md                 # 项目说明文档 / Documentation
├── CONTRIBUTING.md           # 贡献指南 / Contributing guide
├── API-STANDARD.md           # API规范标准 / API standards
├── sources/                  # 资源目录 / Resources
│   ├── vod-sources.json      # 点播视频源集合 / VOD sources
│   └── parsers.json          # 视频解析器集合 / Video parsers
└── LICENSE                   # MIT 许可证 / License
```

## 📋 资源说明 / Resources

### 1. 点播视频源 (VOD Sources)
文件 / File: `sources/vod-sources.json`

包含39个精选视频点播源，分为以下两类 / Contains 39 curated VOD sources in two categories:

**资源源 (Resource Sources - 13个)**
- 紅牛資源、量子資源、卧龙资源、森林资源、閃電資源、金鹰资源、光速资源、奥斯卡资源网、U酷资源、樱花资源网、闪电资源、百度资源、艾旦影视

**点播源 (VOD Sources - 26个)**
- 360|点播、牛牛|点播、丫丫|点播、U酷|点播、豪华|点播、极速|点播、索尼|点播、ikun|点播、非凡|点播、量子|点播、暴风|点播、红牛|点播、闪电|点播、樱花|点播、卧龙|点播、虎牙|点播、百度|点播、飘零|点播、无尽|点播、速博|点播、魔都|点播、最大|点播、火狐|点播、新浪|点播

每个源包含以下信息 / Each source contains:
- `name`: 源名称 / Source name
- `url`: API接口地址 / API address

**API 使用格式 / API Usage Format:**

每个视频源遵循以下标准接口格式：

#### 搜索接口 / Search Interface
```
https://example.com/api.php/provide/vod/?ac=videolist&wd=关键词
```
参数说明 / Parameters:
- `ac=videolist` : 获取视频列表 / Get video list
- `wd=关键词` : 搜索关键词（需URL编码）/ Search keyword (URL encoded)

示例 / Example:
```
https://360zy.com/api.php/provide/vod/?ac=videolist&wd=教父
```

#### 详情接口 / Detail Interface
```
https://example.com/api.php/provide/vod/?ac=detail&ids=视频ID
```
参数说明 / Parameters:
- `ac=detail` : 获取视频详情 / Get video detail
- `ids=视频ID` : 视频ID（多个ID用逗号分隔）/ Video IDs (comma-separated)

示例 / Example:
```
https://360zy.com/api.php/provide/vod/?ac=detail&ids=12345
https://360zy.com/api.php/provide/vod/?ac=detail&ids=12345,12346,12347
```

**使用示例** / Usage Example:
```json
{
  "name": "360|点播",
  "url": "https://360zy.com/api.php/provide/vod/",
  "searchInterface": "https://360zy.com/api.php/provide/vod/?ac=videolist&wd=",
  "detailInterface": "https://360zy.com/api.php/provide/vod/?ac=detail&ids="
}
```

### 2. 视频解析器 (Video Parsers)
文件 / File: `sources/parsers.json`

包含精选的视频解析器，用于解析各类视频链接。每个解析器包含 / Contains curated video parsers for parsing video links. Each parser contains:
- `name`: 解析器名称 / Parser name
- `url`: 解析器地址（参数：?url=VIDEO_URL）/ Parser URL (parameter: ?url=VIDEO_URL)

**使用示例** / Usage Example:
```
https://yparse.ik9.cc/index.php?url=https://example.com/video.m3u8
```

## 🚀 快速开始 / Getting Started

### 使用JSON文件 / Using JSON Files
直接导入 `vod-sources.json` 或 `parsers.json` 到你的应用中。
Import `vod-sources.json` or `parsers.json` directly into your application:

```javascript
// Node.js 示例 / Example
const vodSources = require('./sources/vod-sources.json');
const parsers = require('./sources/parsers.json');

console.log(vodSources.sources[0]); // 第一个视频源 / First video source
console.log(parsers.parsers[0]);    // 第一个解析器 / First parser
```

```python
# Python 示例 / Example
import json

with open('sources/vod-sources.json', 'r', encoding='utf-8') as f:
    vod_sources = json.load(f)

with open('sources/parsers.json', 'r', encoding='utf-8') as f:
    parsers = json.load(f)

print(vod_sources['sources'][0])  # 第一个视频源 / First video source
```

## ⚠️ 免责声明 / Disclaimer

- 本项目仅供学习交流使用，不对任何源站的内容合法性负责
- This project is for educational purposes only and is not responsible for the legality of any content from third-party sources

- 使用这些资源时，请确保遵守当地法律法规
- When using these resources, please ensure compliance with local laws and regulations

- 作者不对因使用本项目资源造成的任何后果负责
- The author is not responsible for any consequences caused by using this project's resources

## 📝 许可证 / License

本项目采用 MIT 许可证 / Licensed under MIT License

## 🤝 贡献 / Contributing

欢迎提交 Issue 和 Pull Request 来改进本项目！

详见 [CONTRIBUTING.md](CONTRIBUTING.md) 了解如何贡献新的视频源或解析器。

Feel free to submit issues and pull requests to improve this project!

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute new video sources or parsers.
