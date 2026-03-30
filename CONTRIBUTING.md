# 贡献指南 / Contributing Guide

感谢你对本项目的兴趣！欢迎提交新的视频源接口或解析器。

Thank you for your interest in this project! We welcome contributions of new video sources and parsers.

---

## 📝 如何添加新的视频源 / How to Add a New Video Source

### 步骤 1: Fork 本项目
点击 GitHub 页面右上角的 **Fork** 按钮，创建你的个人副本。

### 步骤 2: 克隆到本地
```bash
git clone https://github.com/你的用户名/-api-.git
cd -api-
```

### 步骤 3: 创建新分支
```bash
git checkout -b add-new-source
```

### 步骤 4: 修改文件

#### 4.1 编辑 `sources/vod-sources.json`

在 `sources` 数组中添加新的视频源对象：

```json
{
  "name": "源的名称",
  "nameEn": "Source Name",
  "category": "点播",
  "url": "https://example.com/api.php/provide/vod/",
  "searchInterface": "https://example.com/api.php/provide/vod/?ac=videolist&wd=",
  "detailInterface": "https://example.com/api.php/provide/vod/?ac=detail&ids=",
  "status": "active",
  "notes": "备注信息（可选）"
}
```

**字段说明：**
- `name` ⭐ 必填 - 源的中文名称
- `url` ⭐ 必填 - 源的根API地址
- `category` - 分类，通常为"点播"
- `nameEn` - 英文名称（可选）
- `searchInterface` - 搜索接口地址（可选）
- `detailInterface` - 详情接口地址（可选）
- `status` - 状态，"active" 或 "inactive"（默认active）
- `notes` - 使用说明或备注（可选）

#### 4.2 编辑 `sources/vod-sources.txt`

按照以下格式添加纯文本版本：

```
源的名称|点播
https://example.com/api.php/provide/vod/
```

#### 4.3 编辑 `sources/vod-sources-v2.json`（可选）

优化版本也需要更新。

---

## 🔍 添加视频源前的检查清单

在提交前，请确保：

- [ ] ✅ API 地址能够正常访问
- [ ] ✅ API 返回有效的 JSON 数据
- [ ] ✅ 搜索接口能够正常返回搜索结果
- [ ] ✅ 详情接口能够正常返回视频详情
- [ ] ✅ 源名称准确且唯一（避免重复）
- [ ] ✅ JSON 格式正确（可用在线验证工具检查）
- [ ] ✅ 已按字母顺序排序（可选但推荐）

---

## 📍 API 接口标准格式

所有视频源应遵循以下标准格式：

### 搜索接口 (Search)
```
https://example.com/api.php/provide/vod/?ac=videolist&wd=关键词
```

### 详情接口 (Detail)
```
https://example.com/api.php/provide/vod/?ac=detail&ids=视频ID
```

详见项目的 [API-STANDARD.md](API-STANDARD.md)

---

## 📊 如何添加新的解析器 / How to Add a New Parser

### 编辑 `sources/parsers.json`

```json
{
  "name": "解析器名称",
  "url": "https://example.com/player/?url="
}
```

### 编辑 `sources/parsers.txt`

```
解析器名称
https://example.com/player/?url=
```

---

## 🚀 提交你的更改

### 步骤 5: 提交更改
```bash
git add sources/
git commit -m "添加新的视频源：源名称"
```

提交信息格式示例：
- ✅ `添加新的视频源：海外看`
- ✅ `添加新的解析器：jx.xmflv`
- ✅ `更新视频源状态：源名称`

### 步骤 6: 推送到你的 Fork
```bash
git push origin add-new-source
```

### 步骤 7: 创建 Pull Request

1. 访问你 Fork 的项目页面
2. 点击 **New Pull Request**
3. 选择 Base Repository：`HongHae-in/-api-`
4. 选择 Base Branch：`main`
5. 填写 PR 标题和描述
6. 点击 **Create Pull Request**

---

## 📋 Pull Request 描述模板

```markdown
## 描述
添加了新的视频源...

## 类型
- [ ] 新增视频源
- [ ] 新增解析器
- [ ] 更新现有信息
- [ ] 修复问题

## 检查列表
- [ ] API 已验证可用
- [ ] JSON 格式正确
- [ ] 已按规范添加所有必要字段
- [ ] 没有重复的源名称

## 相关链接
没有

## 备注
（可选）添加任何额外信息
```

---

## ⚠️ 贡献规范 / Contribution Guidelines

### 必须遵守
1. **遵循标准格式** - 使用规定的 JSON 结构
2. **验证数据有效性** - 确保 API 地址可访问
3. **保持信息准确** - 不添加失效或错误的源
4. **尊重他人工作** - 不删除或修改他人贡献

### 应该做
- 📝 清晰描述你的更改
- 🔗 提供源的相关信息
- 🧪 测试 API 的有效性
- 💬 如有问题，先开 Issue 讨论

### 不应该做
- ❌ 添加已知失效的源
- ❌ 修改他人的贡献而不说明原因
- ❌ 添加重复的源
- ❌ 上传包含个人敏感信息的内容

---

## ⚖️ 许可证

所有贡献必须遵守 MIT License。提交 PR 即表示你同意按 MIT License 发布你的贡献。

---

## 🤔 有问题？

- 📖 查看 [README.md](README.md) 了解更多信息
- 📄 查看 [API-STANDARD.md](API-STANDARD.md) 了解 API 标准
- 🐛 提交 Issue 报告问题或建议
- 💬 在 Issue 中提出讨论

---

## 🙏 感谢

感谢所有为本项目做出贡献的开发者！

Together, we build a better open source community! 🌟
