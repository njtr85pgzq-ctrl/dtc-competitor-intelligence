# DTC Competitor Intelligence — Claude Code Skill Plugin

> 一个能被 AI 直接执行的 DTC 独立站竞对深度拆解技能插件。
> 提供竞对网址 → 自动执行 10 阶段全链路分析 → 输出可直接分发执行团队的落地报告。

## 这是什么？

这是一个 **Claude Code 技能插件（AI Skill Plugin）**。它不是纯文档——它是一个能被 Claude Code 加载和执行的 AI 指令集。

在 Claude Code 中安装后，只需输入：

```
分析一下 https://competitor.com
```

Claude Code 会自动按 10 阶段框架执行：
流量摸底 → 受众画像 → 渠道审计 → SEO深拆 → 广告逆向 → GMV测算 → 技术栈扫描 → 口碑挖掘 → SWOT收敛 → 90天行动计划

## 安装

```bash
# 克隆到 Claude Code 技能目录
git clone https://github.com/njtr85pgzq-ctrl/dtc-competitor-intelligence.git \
  ~/.claude/skills/dtc-competitor-intelligence
```

重启 Claude Code 后，技能会自动加载。输入 `竞对调研` 或 `分析一下 <网址>` 即可触发。

## 技能架构

```
~/.claude/skills/dtc-competitor-intelligence/
├── SKILL.md              # 主指令文件（YAML frontmatter + AI orchestration）
└── references/            # 15个参考文件，skill激活时自动加载
    ├── phase-1-traffic.md       # 流量底盘摸底
    ├── phase-2-audience.md      # 受众画像与决策链路
    ├── phase-3-channels.md      # 渠道构成与质量审计
    ├── phase-4-seo.md           # SEO与内容策略深拆
    ├── phase-5-ads.md           # 广告打法逆向工程
    ├── phase-6-gmv.md           # 转化漏斗与GMV三角验证
    ├── phase-7-techstack.md     # 技术栈扫描
    ├── phase-8-reputation.md    # 品牌口碑与用户洞察
    ├── phase-9-swot.md          # SWOT收敛
    ├── phase-10-action-plan.md  # 90天行动计划
    ├── sop-product-launch.md    # 产品上线全流程SOP（附录A）
    ├── sop-offsite-seo.md       # 站外SEO与外链建设SOP（附录B）
    ├── sop-fullstack.md         # 独立站全栈架构速查（附录C）
    ├── tools-matrix.md          # 工具矩阵速查
    └── report-template.md       # 报告输出模板
```

### 关键设计

- **`SKILL.md`** 是 AI 的指挥中枢：定义触发词、执行流程编排、搜索策略、核心原则
- **`references/`** 是 AI 的知识库：每个 Phase 的详细分析框架、公式、检查清单
- **10 Phase 渐进式搜索**：前期 Phase 可并行，后期 Phase 依赖前期发现，SWOT/Action Plan 不搜索
- **功利性原则内嵌**：每个 Phase 要求 AI 回答"所以呢？对我有什么用？"

## SKILL.md 设计亮点

| 特性 | 说明 |
|------|------|
| YAML frontmatter | `triggers`（10个触发词）、`allowed-tools`（工具权限）、`argument-hint` |
| 工具权限控制 | 声明所需权限：Bash/Read/Write/WebFetch/WebSearch/Agent 等 |
| 10 Phase 工作流 | 每个 Phase 有：目标 → 搜索策略 → 并行搜索关键词 → 分析维度 → 必须输出 |
| 数据可信度体系 | 每个数据点标注：确认 / 估算 / 推断 |
| 报告输出路径 | 自动写入 `d:/projects/dtc-competitor-intelligence/examples/` |

## 实战案例

| 案例 | 品类 | 核心发现 |
|------|------|---------|
| [DME Superstore](./examples/dmesuperstore.md) | 医疗器械 DTC | 年GMV ~$1M，运营基本功不稳，做同价+好服务就能赢 |
| [ULIP Store](./examples/ulipstore.md) | 电自配件 DTC | 中国工厂出海，年收$3-10M，但做了10年品牌还是零 |

## 市场分析

[电动出行配件赛道机会分析](./market-analysis/电自配件赛道.md) — 三个方向的市场规模、竞争格局、进入路径。

## 适用人群

- **出海 DTC 创业者**：一键生成竞对深度拆解报告
- **跨境电商运营**：系统化竞调方法论 + 可直接抄的 SOP
- **AI Agent 开发者**：参考 YAML frontmatter + references/ 的 skill 封装模式，了解如何将领域知识打包为可被 AI 执行的插件
- **独立站操盘手**：竞调 → 决策 → 执行的全链路工作流

## 使用其他 AI 平台？

`SKILL.md` 的 YAML frontmatter 是 Claude Code 特有格式，但主体内容（10 Phase 指令 + references/ 知识库）是平台无关的。你可以：

- 将 `SKILL.md` + `references/` 整体作为 Claude 的自定义指令（Custom Instructions / Project Knowledge）
- 将 references/ 作为 GPTs 或 Cursor Rules 的素材
- 将方法论作为手动竞调的 checklist 使用

## 更新与维护

```bash
cd ~/.claude/skills/dtc-competitor-intelligence
git pull origin master
```

Claude Code 在每次会话启动时重新加载技能，无需重启。
