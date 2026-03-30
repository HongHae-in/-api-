# 贡献指南 / Contributing Guide

感谢你对本项目的兴趣！欢迎提交新的视频源接口或解析器。

Thank you for your interest in this project! We welcome contributions of new video sources and parsers.

---

## 📝 如何添加新的视频源 / How to Add a New Video Source

### 步骤 1: Fork 本项目 / Step 1: Fork the Repository
点击 GitHub 页面右上角的 **Fork** 按钮，创建你的个人副本。

Click the **Fork** button in the upper right corner of the GitHub page to create your own copy.

### 步骤 2: 克隆到本地 / Step 2: Clone to Local
```bash
git clone https://github.com/你的用户名/-api-.git
cd -api-
```

### 步骤 3: 创建新分支 / Step 3: Create a New Branch
```bash
git checkout -b add-new-source
```

### 步骤 4: 修改文件 / Step 4: Edit Files

#### 4.1 编辑 `sources/vod-sources.json` / Edit `sources/vod-sources.json`

在 `sources` 数组中添加新的视频源对象。
Add a new video source object to the `sources` array:

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

**字段说明 / Field Description:**
- `name` ⭐ 必填 / Required - 源的中文名称 / Chinese name
- `url` ⭐ 必填 / Required - 源的根API地址 / Root API address
- `category` - 分类 / Category (通常为 / usually "点播")
- `nameEn` - 英文名称 / English name (可选 / Optional)
- `searchInterface` - 搜索接口地址 / Search interface (可选 / Optional)
- `detailInterface` - 详情接口地址 / Detail interface (可选 / Optional)
- `status` - 状态 / Status ("active" 或/or "inactive")
- `notes` - 使用说明或备注 / Notes (可选 / Optional)

#### 4.2 编辑 `sources/vod-sources.txt` / Edit `sources/vod-sources.txt`

按照以下格式添加纯文本版本。
Add a plain text version in the following format:

```
源的名称|点播
https://example.com/api.php/provide/vod/
```

#### 4.3 编辑 `sources/vod-sources-v2.json`（可选）/ Edit `sources/vod-sources-v2.json` (Optional)

优化版本也需要更新。
The optimized version also needs to be updated.

---

## 🔍 添加视频源前的检查清单 / Checklist Before Adding

在提交前，请确保 / Before submitting, please ensure:

- [ ] ✅ API 地址能够正常访问 / API accessible
- [ ] ✅ API 返回有效的 JSON 数据 / API returns valid JSON
- [ ] ✅ 搜索接口能够正常返回搜索结果 / Search interface works
- [ ] ✅ 详情接口能够正常返回视频详情 / Detail interface works
- [ ] ✅ 源名称准确且唯一（避免重复）/ Unique source name
- [ ] ✅ JSON 格式正确（可用在线验证工具检查）/ JSON format valid
- [ ] ✅ 已按字母顺序排序（可选但推荐）/ Sorted alphabetically (recommended)

---

## 📍 API 接口标准格式 / API Interface Standard Format

所有视频源应遵循以下标准格式。
All video sources should follow the standard format below:

### 搜索接口 / Search Interface
```
https://example.com/api.php/provide/vod/?ac=videolist&wd=关键词
```

### 详情接口 / Detail Interface
```
https://example.com/api.php/provide/vod/?ac=detail&ids=视频ID
```

详见项目的 [API-STANDARD.md](API-STANDARD.md) / See [API-STANDARD.md](API-STANDARD.md) for details

---

## 📊 如何添加新的解析器 / How to Add a New Parser

### 编辑 `sources/parsers.json` / Edit `sources/parsers.json`

```json
{
  "name": "解析器名称",
  "url": "https://example.com/player/?url="
}
```

### 编辑 `sources/parsers.txt` / Edit `sources/parsers.txt`

```
解析器名称
https://example.com/player/?url=
```

---

## 🚀 提交你的更改 / Submit Your Changes

### 步骤 5: 提交更改 / Step 5: Commit Changes
```bash
git add sources/
git commit -m "添加新的视频源：源名称"
```

提交信息格式示例 / Commit message examples:
- ✅ `添加新的视频源：海外看` / Add new VOD source: HaiWaiKan
- ✅ `添加新的解析器：jx.xmflv` / Add new parser: jx.xmflv
- ✅ `更新视频源状态：源名称` / Update source status: source name

### 步骤 6: 推送到你的 Fork / Step 6: Push to Your Fork
```bash
git push origin add-new-source
```

### 步骤 7: 创建 Pull Request / Step 7: Create Pull Request

1. 访问你 Fork 的项目页面 / Visit your forked repository page
2. 点击 **New Pull Request** / Click **New Pull Request**
3. 选择 Base Repository：`HongHae-in/-api-` / Select Base: `HongHae-in/-api-`
4. 选择 Base Branch：`main` / Select Base Branch: `main`
5. 填写 PR 标题和描述 / Fill in PR title and description
6. 点击 **Create Pull Request** / Click **Create Pull Request**

---

## 📋 Pull Request 描述模板 / Pull Request Description Template

```markdown
## 描述 / Description
添加了新的视频源... / Added a new video source...

## 类型 / Type
- [ ] 新增视频源 / New VOD source
- [ ] 新增解析器 / New parser
- [ ] 更新现有信息 / Update existing info
- [ ] 修复问题 / Bug fix

## 检查列表 / Checklist
- [ ] API 已验证可用 / API verified working
- [ ] JSON 格式正确 / JSON format valid
- [ ] 已按规范添加所有必要字段 / Added all required fields
- [ ] 没有重复的源名称 / No duplicate sources

## 相关链接 / Related Links
没有 / None

## 备注 / Notes
（可选）添加任何额外信息 / (Optional) Add any additional information
```

---

## ⚠️ 贡献规范 / Contribution Guidelines

### 必须遵守 / Must Follow
1. **遵循标准格式** / Follow standard format - 使用规定的 JSON 结构 / Use specified JSON structure
2. **验证数据有效性** / Verify data validity - 确保 API 地址可访问 / Ensure API is accessible
3. **保持信息准确** / Keep info accurate - 不添加失效或错误的源 / Don't add inactive sources
4. **尊重他人工作** / Respect others - 不删除或修改他人贡献 / Don't modify others' work

### 应该做 / Should Do
- 📝 清晰描述你的更改 / Describe changes clearly
- 🔗 提供源的相关信息 / Provide source information
- 🧪 测试 API 的有效性 / Test API functionality
- 💬 如有问题，先开 Issue 讨论 / Discuss in Issues first

### 不应该做 / Don't Do
- ❌ 添加已知失效的源 / Don't add inactive sources
- ❌ 修改他人的贡献而不说明原因 / Don't modify others' work without reason
- ❌ 添加重复的源 / Don't add duplicates
- ❌ 上传包含个人敏感信息的内容 / Don't upload sensitive info

---

## ⚖️ 许可证 / License

所有贡献必须遵守 MIT License。提交 PR 即表示你同意按 MIT License 发布你的贡献。

All contributions must comply with the MIT License. Submitting a PR means you agree to release your contribution under the MIT License.

---

## 🤔 有问题？/ Questions?

- 📖 查看 [README.md](README.md) 了解更多信息 / See [README.md](README.md) for more info
- 📄 查看 [API-STANDARD.md](API-STANDARD.md) 了解 API 标准 / See [API-STANDARD.md](API-STANDARD.md) for API spec
- 🐛 提交 Issue 报告问题或建议 / Submit an Issue to report or suggest
- 💬 在 Issue 中提出讨论 / Start discussions in Issues

---

## 🙏 感谢 / Thanks

感谢所有为本项目做出贡献的开发者！

Thank you to all developers who contribute to this project!

Together, we build a better open source community! 🌟
