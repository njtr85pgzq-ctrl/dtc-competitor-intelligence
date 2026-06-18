# DTC Competitor Intelligence — Cross-Platform AI Skill

> 一个跨平台的 DTC 独立站竞对深度拆解 AI 技能插件。遵循 [AgentSkills](https://agentskills.io) 开放标准。
> 提供竞对网址 → 自动执行 11 阶段全链路分析 → 输出可直接分发执行团队的落地报告。
>
> Claude Code / Codex CLI / OpenClaw / Cursor / Gemini CLI 均可使用。

## 快速开始

安装后只需输入：

```
分析一下 https://competitor.com
```

AI 自动执行 11 阶段全链路分析：流量摸底 → 受众画像 → 渠道审计 → SEO深拆 → 广告逆向 → GMV三角验证 → 定价情报 → 技术栈扫描 → 口碑挖掘 → SWOT收敛 → 90天行动计划。

## 安装

### Claude Code

```bash
git clone https://github.com/njtr85pgzq-ctrl/dtc-competitor-intelligence.git \
  ~/.claude/skills/dtc-competitor-intelligence
```

重启 Claude Code，输入 `竞对调研` 或 `分析一下 <网址>` 触发。

### Codex CLI (OpenAI)

```bash
git clone https://github.com/njtr85pgzq-ctrl/dtc-competitor-intelligence.git \
  ~/.agents/skills/dtc-competitor-intelligence
```

Codex 自动匹配 `description` 字段。输入 `analyze competitor website` 或 `/dtc-competitor-intelligence` 触发。

### OpenClaw

```bash
git clone https://github.com/njtr85pgzq-ctrl/dtc-competitor-intelligence.git \
  ~/.agents/skills/dtc-competitor-intelligence
```

或放到 workspace 级别：`<workspace>/.agents/skills/dtc-competitor-intelligence/`

### Cursor / Gemini CLI / 其他 35+ 平台

均支持 [AgentSkills](https://agentskills.io) 标准，安装方式同上，放到对应平台的 skills 目录即可。

### 一键安装（如果装了 skills.sh）

```bash
npx skills add njtr85pgzq-ctrl/dtc-competitor-intelligence
```

## 技能架构

```
dtc-competitor-intelligence/
├── SKILL.md                  # 主指令文件（AgentSkills 标准 YAML + 11 Phase 编排）
├── agents/
│   └── openai.yaml           # Codex 平台元数据
├── references/               # 16 个知识文件，skill 激活时自动加载
│   ├── phase-1-traffic.md         # 流量底盘摸底
│   ├── phase-2-audience.md        # 受众画像与决策链路
│   ├── phase-3-channels.md        # 渠道构成与质量审计（含 8 个 marketing skill 交叉引用）
│   ├── phase-4-seo.md             # SEO与内容策略深拆（含 20 个 SEO skill 交叉引用）
│   ├── phase-5-ads.md             # 广告打法逆向工程（含 12 个 paid-ads skill 交叉引用）
│   ├── phase-6-gmv.md             # 转化漏斗与GMV三角验证
│   ├── phase-7-pricing.md         # 定价情报深拆（v3 新增）
│   ├── phase-8-techstack.md       # 技术栈扫描
│   ├── phase-9-reputation.md      # 品牌口碑与用户洞察
│   ├── phase-10-swot.md           # SWOT收敛
│   ├── phase-11-action-plan.md    # 90天行动计划（含 40+ 执行 skill 交叉引用）
│   ├── sop-product-launch.md      # 产品上线全流程SOP（附录A）
│   ├── sop-offsite-seo.md         # 站外SEO与外链建设SOP（附录B）
│   ├── sop-fullstack.md           # 独立站全栈架构速查（附录C）
│   ├── tools-matrix.md            # 工具矩阵速查
│   └── report-template.md         # 报告输出模板（含 Executive Summary）
├── examples/
│   ├── dmesuperstore.md           # DME Superstore 竞调报告（v3 增强版）
│   └── ulipstore.md               # ULIP Store 竞调报告
└── market-analysis/
    └── 电自配件赛道.md            # 电自配件赛道市场分析
```

## 版本演进

| 版本 | 变化 |
|------|------|
| **v1** | 原始方法论文档，10 Phase，纯人读 |
| **v2** | 转为 AI skill 插件，集成 172 个 marketing-skills，P0/P1 分级调用 |
| **v3** | 新增 Phase 7 定价情报、Executive Summary、跨平台 AgentSkills 标准兼容 |

## 关键设计

- **跨平台**：遵循 [AgentSkills](https://agentskills.io) 开放标准，Claude Code / Codex / OpenClaw / Cursor 均可加载
- **P0/P1 skill 分级**：P0 必调（2-3 个关键 skill），P1 选调（时间够就调），解决"列 20 个 skill 但 AI 不全调"的问题
- **Executive Summary**：报告首页 30 秒速读卡，创始人/老板不用翻 500 行
- **功利性原则**：每个 Phase 要求 AI 回答"所以呢？对我有什么用？"
- **数据可信度体系**：每个数据点标注确认/估算/推断
- **定价情报深拆**：SKU 级比价、定价策略识别、运费退货成本、折扣节奏

## 依赖的 Marketing Skills（可选增强）

本 skill 深度集成 [marketing-skills](https://github.com/kostja94/marketing-skills)（172 个专业营销 skill）。未安装时核心功能仍可用，但分析深度会受影响。

```bash
git clone https://github.com/kostja94/marketing-skills.git ~/.agents/skills/marketing-skills
```

## 实战案例

| 案例 | 品类 | 核心发现 |
|------|------|---------|
| [DME Superstore](./examples/dmesuperstore.md) | 医疗器械 DTC | 年GMV ~$2M，Klaviyo邮件流成熟但物流不稳定，同价+好服务就能赢 |
| [ULIP Store](./examples/ulipstore.md) | 电自配件 DTC | 中国工厂出海，年收$3-10M，但做了10年品牌还是零 |

## 市场分析

[电动出行配件赛道机会分析](./market-analysis/电自配件赛道.md) — 三个方向的市场规模、竞争格局、进入路径。

## 适用人群

- **出海 DTC 创业者**：一键生成竞对深度拆解报告
- **跨境电商运营**：系统化竞调方法论 + 可直接抄的 SOP
- **AI Agent 开发者**：参考 AgentSkills 标准的 skill 封装模式
- **独立站操盘手**：竞调 → 决策 → 执行的全链路工作流

## 更新

```bash
cd ~/.agents/skills/dtc-competitor-intelligence  # 或 ~/.claude/skills/
git pull origin master
```

各平台在每次会话启动时重新加载 skill，无需重启。
