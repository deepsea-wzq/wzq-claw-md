# TOOLS.md - 工具备忘

Skills 定义工具的行为，这个文件记录你的**环境特定配置和使用经验**——从实际使用中积累的笔记。


---

## 搜索工具顺序（固定流程）

遇到需要搜索新闻/资讯的需求时，默认调用**fin-search**技能
---

## SkillHub 安装流程（skillhub.tencent.com）

**优先使用 SkillHub 安装技能**，替代 clawhub（clawhub 频繁 rate limit）。

### CLI 安装（推荐）
```bash
# 安装 CLI（已装好，路径 /root/.local/bin/skillhub）
curl -fsSL https://skillhub-1388575217.cos.ap-guangzhou.myqcloud.com/install/install.sh | bash -s -- --cli-only

# 搜索
skillhub search <关键词>

# 安装到当前 workspace/skills/
skillhub install <slug> --dir ~/.openclaw/workspace/skills

# 列出已安装
skillhub list

# 升级
skillhub upgrade
```

### 手动安装（备选，CLI 不可用时）
- **后端 base URL**：`https://lightmake.site`
- **Top 榜单**：`GET https://lightmake.site/api/skills/top`
- **下载 ZIP**：`GET https://lightmake.site/api/v1/download?slug=<slug>`
- 下载后解压到 `~/.openclaw/workspace/skills/<slug>/` 即可

### 注意
- 中国用户访问快（腾讯 CDN），无 rate limit 问题
- 安装后建议重启 openclaw 以感知新技能
- clawhub 作为备选，不优先使用

---

## 自研技能路径

以下技能均位于 **`~/.openclaw/skills/`** 下，**不要**在 workspace 目录或其他路径下查找：

- `fin-copilot`
- `fin-search`
- `market-pulse`
- `westock-data`
- `westock-portfolio`
- `westock-tool`
- `wzq-implicit-daily-review`

读取 SKILL.md 时使用正确路径，例如 `~/.openclaw/skills/westock-data/SKILL.md`。

---

## 数据冲突处理原则

当不同数据源的结果产生冲突时，**优先相信 westock-data 专业工具返回的结果**。westock-data 作为专业金融数据源，其数据准确性和权威性高于其他渠道（如网页搜索、通用 API 等）。

---

Add whatever helps you do your job. This is your cheat sheet.