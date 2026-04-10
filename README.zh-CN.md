# Marketing Skills —— AI 营销技能库（简体中文说明）

> 本文件是对 [README.md](README.md) 的简体中文翻译与说明，帮助不熟悉英文的用户快速理解本仓库的结构和用途。

---

## 这个仓库是什么？

这是一个专为 AI 编程助手（如 Claude Code、OpenAI Codex、Cursor、Windsurf 等）设计的**营销技能集合**。

- 每个"技能（Skill）"都是一个 Markdown 文件，告诉 AI 代理如何处理特定的营销任务。
- 你把这些技能文件放进你的项目后，AI 就能识别营销相关请求，并按照专业框架和最佳实践来执行。
- 由 [Corey Haines](https://corey.co) 创建，遵循 [MIT 开源协议](LICENSE)。

---

## 仓库目录结构

```
marketingskills/
├── .claude-plugin/
│   └── marketplace.json     # Claude Code 插件市场配置文件
├── skills/                  # 所有技能文件夹（核心内容）
│   └── 技能名称/
│       └── SKILL.md         # 必须有的技能说明文件
├── tools/
│   ├── clis/                # 51 个零依赖的 Node.js 命令行工具
│   ├── integrations/        # 各第三方平台的 API 集成说明
│   └── REGISTRY.md          # 工具总索引
├── CONTRIBUTING.md          # 贡献指南
├── LICENSE                  # 开源协议（MIT）
├── README.md                # 英文说明文档
└── VERSIONS.md              # 各技能的版本历史
```

---

## 什么是"技能（Skill）"？

技能是一种特殊的 Markdown 文件，文件头部包含 YAML 格式的元数据，告诉 AI 代理：

1. 这个技能叫什么（`name`）
2. 什么情况下使用它（`description`，含触发词）
3. 具体的操作步骤和专业建议（文件正文）

### 技能文件示例（SKILL.md）

```yaml
---
name: page-cro
description: 当用户想优化营销页面转化率时使用。例如用户说"CRO"、"提升转化"、"落地页效果差"……
metadata:
  version: 1.1.0
---

# 页面转化率优化（CRO）

你是一名转化率优化专家。你的目标是分析营销页面，提供可执行的优化建议……
```

### 技能文件字段规则

| 字段          | 是否必须 | 规则说明                                           |
|---------------|----------|----------------------------------------------------|
| `name`        | ✅ 必须  | 1-64 个字符，只能用小写字母、数字、连字符，必须与文件夹名称完全一致 |
| `description` | ✅ 必须  | 1-1024 个字符，说明用途和触发词                    |
| `license`     | 可选     | 授权协议，默认 MIT                                 |
| `metadata`    | 可选     | 作者、版本等键值对信息                             |

---

## 技能如何协作工作？

所有技能都建立在 `product-marketing-context`（产品营销上下文）这个基础技能之上。每个技能在执行前都会先读取它，了解你的产品、受众和定位。

```
                        ┌─────────────────────────────┐
                        │    product-marketing-context │
                        │  （所有技能运行前都先读取它） │
                        └──────────────┬──────────────┘
                                       │
     ┌──────────┬──────────┬───────────┼───────────┬──────────┬──────────┐
     ▼          ▼          ▼           ▼           ▼          ▼          ▼
  SEO与      转化率      内容与      付费与      增长与     销售与     营销策略
  内容优化   优化(CRO)   文案        数据        留存       GTM
```

技能之间也会互相引用，例如：
- `copywriting` ↔ `page-cro` ↔ `ab-test-setup`
- `revops` ↔ `sales-enablement` ↔ `cold-email`
- `seo-audit` ↔ `schema-markup` ↔ `ai-seo`

---

## 可用技能总览

### 🎯 转化率优化（CRO）

| 技能 | 用途说明 |
|------|----------|
| `page-cro` | 优化任意营销页面（首页、落地页、定价页等） |
| `signup-flow-cro` | 优化注册/账户创建流程 |
| `onboarding-cro` | 优化注册后的用户激活和引导流程 |
| `form-cro` | 优化非注册类表单（线索捕获、联系表单等） |
| `popup-cro` | 优化弹窗、模态框、横幅等 |
| `paywall-upgrade-cro` | 优化应用内付费升级弹窗和功能门控页 |

### ✍️ 内容与文案

| 技能 | 用途说明 |
|------|----------|
| `copywriting` | 撰写或改写营销页面文案 |
| `copy-editing` | 编辑和润色已有文案 |
| `cold-email` | 撰写 B2B 冷邮件和跟进序列 |
| `email-sequence` | 创建自动化邮件流程 |
| `social-content` | 创作社交媒体内容 |

### 🔍 SEO 与搜索发现

| 技能 | 用途说明 |
|------|----------|
| `seo-audit` | 技术与页面 SEO 审查 |
| `ai-seo` | AI 搜索优化（AEO、GEO、LLMO） |
| `programmatic-seo` | 程序化批量生成 SEO 页面 |
| `site-architecture` | 网站页面层级、导航与 URL 结构规划 |
| `competitor-alternatives` | 竞品对比和替代产品页面 |
| `schema-markup` | 结构化数据标记（JSON-LD 等） |

### 💰 付费广告与分发

| 技能 | 用途说明 |
|------|----------|
| `paid-ads` | Google、Meta、LinkedIn 等平台广告投放 |
| `ad-creative` | 批量生成和迭代广告素材 |
| `content-strategy` | 内容策略规划 |

### 📊 数据与测试

| 技能 | 用途说明 |
|------|----------|
| `analytics-tracking` | 事件追踪与数据埋点设置 |
| `ab-test-setup` | A/B 测试实验设计 |

### 🔄 增长与留存

| 技能 | 用途说明 |
|------|----------|
| `churn-prevention` | 减少流失、取消挽留流程、欠款催收 |
| `free-tool-strategy` | 免费工具营销策略 |
| `referral-program` | 推荐计划和联盟营销 |

### 🧠 策略与变现

| 技能 | 用途说明 |
|------|----------|
| `marketing-ideas` | 140 个 SaaS 营销创意 |
| `marketing-psychology` | 营销心理学和行为科学 |
| `launch-strategy` | 产品发布和新功能上线策略 |
| `pricing-strategy` | 定价、套餐设计和变现策略 |

### 🤝 销售与业务运营

| 技能 | 用途说明 |
|------|----------|
| `revops` | 收入运营、线索生命周期管理 |
| `sales-enablement` | 销售材料、演示文档、异议处理 |

---

## 如何安装？

### 方式一：命令行安装（推荐）

```bash
# 安装所有技能
npx skills add coreyhaines31/marketingskills

# 只安装特定技能
npx skills add coreyhaines31/marketingskills --skill page-cro copywriting

# 查看可用技能列表
npx skills add coreyhaines31/marketingskills --list
```

安装后，技能文件会自动放入 `.agents/skills/` 目录（同时为 Claude Code 建立软链接至 `.claude/skills/`）。

### 方式二：Claude Code 插件

```bash
# 添加插件市场
/plugin marketplace add coreyhaines31/marketingskills

# 安装所有营销技能
/plugin install marketing-skills
```

### 方式三：克隆并复制

```bash
git clone https://github.com/coreyhaines31/marketingskills.git
cp -r marketingskills/skills/* .agents/skills/
```

### 方式四：Git 子模块

```bash
git submodule add https://github.com/coreyhaines31/marketingskills.git .agents/marketingskills
```

### 方式五：Fork 并自定义

1. Fork 本仓库
2. 根据自己需求修改技能
3. 将你的 Fork 克隆到项目中

---

## 如何使用？

安装后，直接用自然语言告诉 AI 代理你想做什么：

```
"帮我优化这个落地页的转化率"
→ 使用 page-cro 技能

"帮我写 SaaS 首页文案"
→ 使用 copywriting 技能

"帮我设置 GA4 追踪注册事件"
→ 使用 analytics-tracking 技能

"帮我写一个 5 封邮件的欢迎序列"
→ 使用 email-sequence 技能
```

也可以直接调用技能：

```
/page-cro
/email-sequence
/seo-audit
```

---

## 如何贡献？

1. Fork 仓库，创建分支（例如 `feature/my-new-skill`）
2. 在 `skills/` 下新建文件夹，命名规则：小写字母 + 连字符（如 `my-skill`）
3. 在文件夹内创建 `SKILL.md`，包含 YAML 头部（`name` 和 `description` 字段必填）
4. 确认 `name` 字段与文件夹名称完全一致
5. 提交 PR，并选择对应的 PR 模板

详情请参考 [CONTRIBUTING.md](CONTRIBUTING.md)。

---

## 版本说明

当前所有技能均为 **v1.1.0**（2026-02-27 更新）。

主要变更历史请查看 [VERSIONS.md](VERSIONS.md)。

---

## 工具集成

`tools/` 目录下包含：

- **51 个命令行工具**（`tools/clis/`）：零依赖的 Node.js 脚本，支持 GA4、Stripe、Mailchimp、Google Ads 等平台
- **31+ 个集成指南**（`tools/integrations/`）：各平台的 API 端点、认证方式和常用操作说明
- **工具索引**（`tools/REGISTRY.md`）：所有工具的功能概览

---

## 许可证

[MIT](LICENSE) —— 随意使用。
