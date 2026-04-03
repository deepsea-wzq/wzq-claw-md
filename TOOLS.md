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

## 数据出处格式

正文内用脚注编号 `[n]` 标注数据出处，回复末尾逐条列出来源。编号全局连续，正文与来源一一对应。

正文示例：
> 📊 主要指数表现 **[1]**
>
> | 指数 | 最新价 | 涨跌幅 | 成交额 |
> | --- | --- | --- | --- |
> | 上证指数 | 4013.16 | +0.16% | 5971亿 |
> | 创业板指 | 3418.37 | +3.30% | 4307亿 |
>
> 创业板超大单净流入 83.7亿 **[2]**，主力资金明显偏向成长板块。

来源区块示例：
```
---
📌 数据来源
[1] westock-data：主要指数行情，2026-03-20 11:20
[2] westock-data：A股行业板块资金流向，2026-03-20 11:20
[3] fin-search：《小马智行向如祺出行交付超百辆第七代无人车》— 新闻晨报，2026-03-19
```

### 标注原则
- **只标在具体事实上**：有明确数据、事件、引述的句子才标 `[n]`。概括性判断不标。
- **表格/批量数据**：在小标题或引出句末尾标一次 `[n]`，覆盖整张表。
- **散落的单个数据点**：紧跟数据后标 `[n]`。
- **同一来源多处引用**：复用同一编号。

### 来源格式
每条：`[n] 技能名：具体来源，时间`
- 技能名用实际名称（westock-data / fin-search / westock-tool / westock-portfolio 等）
- fin-search 类必须包含：`《标题》— 站点，日期`
- westock-data 类写数据描述 + 时间点
- **时间标签从返回数据中取**：westock-data 的 `metadata.dataTime`（ISO 8601）即为数据实际时间

### 底线规则
1. 不暴露内部调用细节（搜索关键词、API参数等）——用户关心信息从哪来，不是你怎么调的。
2. **复用数据同样标注**：多轮对话中引用之前查过的数据，照常标 `[n]`，时间写原始查询时间。
3. 纯粹基于个人判断、无数据引用时，来源区块写"基于本轮对话已有数据，未发起新查询"。

---

Add whatever helps you do your job. This is your cheat sheet.