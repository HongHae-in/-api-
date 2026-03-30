# API 规范说明 / API Standards Guide

## 概述 / Overview

本文档规范了向本项目添加自定义API时应遵循的格式标准。

This document specifies the format standards for adding custom APIs to this project.

---

## 📌 标准API接口规范 / Standard API Interface Specification

### 1. 搜索接口 / Search Interface

用于搜索视频内容。

**URL 格式 / URL Format:**
```
https://example.com/api.php/provide/vod/?ac=videolist&wd=关键词
```

**参数说明 / Parameters:**
- `ac=videolist` : 固定参数，表示获取视频列表
- `wd=关键词` : 搜索关键词（URL编码）

**请求方法 / Request Method:** GET

**响应格式 / Response Format:** JSON

**示例 / Example:**
```
https://example.com/api.php/provide/vod/?ac=videolist&wd=教父
```

---

### 2. 详情接口 / Detail Interface

用于获取单个视频的详细信息。

**URL 格式 / URL Format:**
```
https://example.com/api.php/provide/vod/?ac=detail&ids=视频ID
```

**参数说明 / Parameters:**
- `ac=detail` : 固定参数，表示获取详情
- `ids=视频ID` : 视频ID（多个ID用逗号分隔）

**请求方法 / Request Method:** GET

**响应格式 / Response Format:** JSON

**示例 / Example:**
```
https://example.com/api.php/provide/vod/?ac=detail&ids=12345
https://example.com/api.php/provide/vod/?ac=detail&ids=12345,12346,12347
```

---

## 📋 JSON 响应格式 / JSON Response Format

### 2.1 搜索响应示例 / Search Response Example

```json
{
  "code": 1,
  "msg": "success",
  "page": 1,
  "pagecount": 10,
  "limit": 10,
  "total": 100,
  "list": [
    {
      "vod_id": "12345",
      "vod_name": "电影名称",
      "vod_pic": "https://example.com/poster.jpg",
      "vod_hits": 1000,
      "vod_score": "8.5"
    }
  ]
}
```

### 2.2 详情响应示例 / Detail Response Example

```json
{
  "code": 1,
  "msg": "success",
  "list": [
    {
      "vod_id": "12345",
      "vod_name": "电影名称",
      "vod_pic": "https://example.com/poster.jpg",
      "vod_year": "2020",
      "vod_area": "中国",
      "vod_director": "导演名字",
      "vod_actor": "演员1,演员2",
      "vod_content": "剧情介绍...",
      "vod_play_from": "播放源",
      "vod_play_url": "播放开始#http://example.com/video.mp4$第二集#http://example.com/video2.mp4"
    }
  ]
}
```

---

## 🎯 常见参数 / Common Parameters

| 参数名 | 说明 | 备注 |
|--------|------|------|
| `ac` | 行为参数 | videolist(列表) / detail(详情) |
| `wd` | 搜索关键词 | 搜索接口必填 |
| `ids` | 视频ID | 详情接口必填 |
| `page` | 分页页码 | 默认为1 |
| `limit` | 每页数量 | 默认10-20 |
| `order` | 排序方式 | time(时间) / hits(热度) / score(评分) |

---

## ✅ 贡献指南 / Contribution Guidelines

### 添加新API时请注意：

1. **测试可用性** - 确保API端点能正常访问和返回数据
2. **格式规范** - 遵循上述标准接口格式
3. **文档完整** - 在JSON文件中填写准确的信息
4. **错误处理** - 标注已知问题或限制

### 提交步骤 / Submission Steps:

1. Fork 本项目
2. 修改 `sources/vod-sources.json` 添加新API
3. 在提交信息中说明API来源和特点
4. 提交 Pull Request

---

## 🔗 JSON 格式示例 / JSON Format Example

在 `sources/vod-sources.json` 中添加新API：

```json
{
  "name": "示例源",
  "nameEn": "Example Source",
  "category": "点播",
  "url": "https://example.com/api.php/provide/vod/",
  "searchInterface": "https://example.com/api.php/provide/vod/?ac=videolist&wd=",
  "detailInterface": "https://example.com/api.php/provide/vod/?ac=detail&ids=",
  "status": "active",
  "notes": "备注信息（可选）"
}
```

**字段说明 / Field Description:**
- `name` : 源名称（中文）
- `nameEn` : 源名称（英文，可选）
- `category` : 分类，如"点播"
- `url` : API根地址
- `searchInterface` : 搜索接口模板
- `detailInterface` : 详情接口模板
- `status` : 状态，如"active"(有效) / "inactive"(失效)
- `notes` : 备注或使用说明（可选）

---

## ⚠️ 注意事项 / Important Notes

1. **URL 编码** - 搜索关键词需要进行URL编码
2. **响应码** - 通常 code=1 表示成功，code=0 表示失败
3. **时间限制** - 某些API可能有请求频率限制
4. **稳定性** - 某些API可能不稳定或间歇性宕机
5. **法律合规** - 请确保API内容合法合规

## 📞 技术支持 / Technical Support

如有问题或建议，请提交 Issue 或 Pull Request。

For technical issues or suggestions, please submit an Issue or Pull Request.

---

## 📝 许可证 / License

本项目采用 MIT 许可证 / Licensed under MIT License
