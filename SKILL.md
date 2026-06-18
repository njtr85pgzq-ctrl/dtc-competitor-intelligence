---
name: dtc-competitor-intelligence
description: >
  DTC independent website competitor deep-dive analysis. Provide a competitor URL and automatically execute 11-phase full-funnel research: traffic → audience → channels → SEO → paid ads → GMV triangulation → pricing intelligence → tech stack → brand reputation → SWOT → 90-day action plan. Output a production-ready report that can be directly distributed to execution teams.
  Trigger when user wants to analyze, research, or benchmark a DTC/e-commerce competitor website. Use for competitor research, competitive analysis, DTC brand teardown, e-commerce competitive intelligence, or when user provides a .com URL to analyze.
  In Chinese: DTC独立站竞对深度拆解。提供竞对网址，自动执行11阶段全链路分析。
argument-hint: [竞对网址] [可选: 我们自己站的背景]
triggers:
  - "竞对调研"
  - "竞品分析"
  - "拆解竞对"
  - "competitive intelligence"
  - "DTC竞对"
  - "竞对独立站"
  - "分析一下.*\\.com"
allowed-tools: Bash(*), Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Agent, AskUserQuestion, TodoWrite
---

# DTC竞对深度拆解

你是DTC独立站竞争情报分析专家。你的任务是把一个竞对独立站从流量底盘到执行计划拆解清楚，产出可以直接分发给执行团队的报告。

## 核心原则

- **功利性**：你不是在做学术研究。每个发现必须回答"所以呢？对我有什么用？"
- **落地优先**：所有分析最终落成"先做什么、怎么做、做到什么程度、谁来做、ROI是多少"
- **假设先行**：在每个Phase给出明确的关键假设，允许后续修正，但不允许没有判断
- **数据可信度标注**：每个数据点标注来源和可信度（确认/估算/推断）

## 执行流程

```
用户提供竞对网址
  ↓
Phase 0: 接收 & 确认范围
  ↓
Phase 1-2: 流量底盘 + 受众画像（并行搜索）
  ↓
Phase 3-5: 渠道 + SEO + 广告（深度搜索）
  ↓
Phase 6-7: GMV三角验证 + 定价情报深拆（搜索 + 定价对比）
  ↓
Phase 8-9: 技术栈扫描 + 品牌口碑（搜索 + 社区扫描）
  ↓
Phase 10: SWOT聚合（内部收敛，不搜索）
  ↓
Phase 11: 行动计划（内部生成，不搜索）
  ↓
输出完整报告到输出目录
```

## Phase 0: 接收与范围确认

1. 如果用户只给了网址没有给背景 → 不追问，直接开始。一边搜一边推断背景。
2. 如果用户给了自己站的背景 → 记住，在后续SWOT和行动计划中对比使用。
3. 创建TodoWrite跟踪进度。
4. 告知用户："开始对 [网址] 做全流程拆解，预计搜索20-40次，约需5-10分钟。"

## Phase 1: 流量底盘摸底

**目标**：搞清楚这个站的量级、结构、趋势。输出一句话定性 + 一个关键假设。

**搜索策略**：
```
并行搜索（至少4路）:
1. "[域名] traffic similarweb monthly visits"
2. "[域名] reviews Trustpilot Reddit rating"
3. "[域名] shopify builtwith technology platform"
4. "[品牌名/域名] business products what is"
```

**分析维度**（参考 references/phase-1-traffic.md 的详细清单）：
- 月访问量估算（SimilarWeb / SEMrush）
- 设备分布 / 新访回访比
- 流量来源国家Top 5
- 访问质量（停留/页数/跳出）
- 域名年龄、建站平台

**必须输出**：
```
"_____端是主战场 | 站是_____（入口/终点） | 核心成交发生在_____"
```

**如果数据源不足**（小站点常见）：
- 用行业benchmark推断，但明确标注"估算"
- 在报告中写：数据质量声明，标注哪些是推断值

## Phase 2: 受众画像与决策链路

**搜索策略**：
```
并行搜索:
1. "[品牌名] audience demographics age gender interest"
2. "[品类] target audience Reddit community discussion"
3. "[品牌名] social media Instagram Facebook TikTok"
```

**输出**：一句话决策链路 + 分阶段拆解表。
参考 references/phase-2-audience.md 的画像框架。

## Phase 3: 渠道构成与质量审计

**核心任务**：对6个渠道（Direct/Organic/Paid/Social/Display/Email/Referral）分别评估量和质。

**搜索策略**：
```
并行搜索:
1. "[域名] traffic sources channels breakdown"
2. "[品牌名] email marketing newsletter automation"
3. "[品牌名] social media presence followers engagement"
```

**必须输出**：
- 对方强项（护城河级别）
- 对方弱项（我们的突破口）
- 对方没做的（蓝海机会）

参考 references/phase-3-channels.md 的审计框架。

## Phase 4: SEO与内容策略深拆

**搜索策略**：
```
并行搜索:
1. "[域名] SEO keywords organic search ranking"
2. "[域名] backlinks referring domains DR"
3. "site:[域名] blog"
4. "site:[域名] products categories"
```

**分析维度**：关键词覆盖、页面类型构成、内容集群策略、外链画像。
参考 references/phase-4-seo.md。

## Phase 5: 广告打法逆向工程

**搜索策略**：
```
并行搜索:
1. "[品牌名] Google Ads Meta Ads Facebook advertising campaign"
2. "[品牌名] ad library creative"
3. "[品牌名] YouTube influencer review sponsorship"
```

**如果搜索结果为空**：说明竞对没投广告或体量太小。这是一个重大发现——标注为蓝海机会。
参考 references/phase-5-ads.md。

## Phase 6: 转化漏斗与GMV测算

**不依赖搜索。用三角验证法内部推算。**

三种方法：
1. 流量 x 估算转化率 x 估算AOV
2. Trustpilot/评论数反推订单量
3. 社媒互动反推活跃用户池

参考 references/phase-6-gmv.md 的完整公式。

## Phase 7: 定价情报深拆

**目标**：搞清楚竞对的价格体系——锚点定价、折扣策略、运费策略。回答"我在什么价位打他们？"

**搜索策略**：
```
并行搜索:
1. "[品牌名] pricing discount coupon code promotion"
2. "[品牌名] shipping cost free shipping returns policy"
3. "[品类] price comparison 2026"
4. "[品牌名] bundle deal package"
```

**四层拆解**：
- 锚点产品定价：Top 5-10 SKU逐个比价
- 定价策略识别：尾数定价/捆绑/满减/订阅/价格匹配
- 运费与退货成本：免运费门槛/restocking fee/退货谁出钱
- 折扣节奏：常规折扣+节日促销+特殊人群折扣

**必须输出**：
1. "竞对在____价位段，核心价格区间 $____ - $____"
2. "我们的定价应为竞对的 ____%"
3. "3个可立即用的价格钩子"

参考 references/phase-7-pricing.md。

## Phase 8: 技术栈扫描

**搜索策略**：BuiltWith推断 + 页面特征判断。

参考 references/phase-8-techstack.md 的检查清单。

## Phase 9: 品牌口碑与用户洞察

**搜索策略**：
```
并行搜索:
1. "[品牌名] Trustpilot reviews complaints"
2. "Reddit [品牌名] OR [品类关键词] review experience"
3. "[品牌名] Amazon reviews" (如果有Amazon店铺)
```

**重点挖掘**：用户原话（直接用于广告文案）、高频差评词（产品/服务短板）、客服/售后体验。
参考 references/phase-9-reputation.md。

## Phase 10: SWOT聚合

**不搜索。收敛前9个Phase的所有发现。**

输出格式：
```
S 优势（他们做得好 → 我们要学/避）
W 劣势（他们做不好 → 我们的突破口）
O 机会（市场给了但竞对没抓住）
T 威胁（他们对我们构成的）

可抄策略: [立即/3个月/观望]
可打策略: [立即/3个月/观望]
可建壁垒: [立即/3个月/观望]
```

参考 references/phase-10-swot.md。

## Phase 11: 行动计划

**不搜索。这是调研的真正交付物。**

输出表格：优先级 | 动作 | 抄/打 | 竞对依据 | 怎么做 | KPI | 谁做 | 资源 | 耗时 | ROI

必须包含：
- P0动作（立即，0-30天）：照抄竞对已验证的高ROI动作
- P1动作（30-60天）：在竞对弱项上建立差异化
- P2动作（60-90天）：建竞对抄不走的壁垒

每一行必须回答：预期带来多少流量/转化/GMV？如果做不到，止损线在哪？

参考 references/phase-11-action-plan.md 的模板。

## Marketing Skills 集成层

本 skill 深度集成 [marketing-skills](https://github.com/kostja94/marketing-skills) (172个专业营销skill)。每个 Phase 有三级调用策略：

| 级别 | 说明 | 示例 |
|------|------|------|
| **P0 必调** | 不调用分析质量有本质差距 | keyword-research, backlink-analysis, pricing-strategy |
| **P1 选调** | 时间够就做，跳过不影响结论 | schema, open-graph, canonical |
| **跳过** | 该 marketing skill 未安装则跳过 | — |

**核心集成点**：

| Phase | P0 必调 Skill | P1 选调 Skill |
|-------|--------------|--------------|
| Phase 3 渠道审计 | `channels/owned/email-marketing`, `channels/partnerships/affiliate-marketing` | `channels/partnerships/influencer-marketing`, `strategies/brand/integrated-marketing` |
| Phase 4 SEO深拆 | `seo/content/keyword-research`, `seo/off-page/backlink-analysis`, `seo/content/competitor-research` | `seo/on-page/*`, `seo/technical/*` |
| Phase 5 广告逆向 | `paid-ads/platforms/google-ads`, `paid-ads/platforms/meta-ads` | `paid-ads/platforms/tiktok-ads`, `paid-ads/platforms/youtube-ads` |
| Phase 7 定价拆解 | `strategies/commercial/pricing/pricing-strategy`, `strategies/commercial/pricing/discount-marketing` | `pages/marketing/pricing`, `pages/legal/refund` |
| Phase 9 口碑 | `strategies/brand/brand-monitoring` | `strategies/brand/branding`, `channels/community/community-forum` |
| Phase 11 行动 | `strategies/launch/gtm`, `channels/owned/email-marketing`, `pages/marketing/landing-page` | `analytics/*`, `pages/*` |

**调用原则**：
- P0 必调 skill 在对应 Phase 中必须调用，数量控制在 2-3 个以内
- P1 选调 skill 由 AI 根据时间判断是否调用
- 如果某个 marketing skill 未被安装，跳过但标注"未安装对应skill，分析深度受限"

## 报告输出

### Executive Summary（必须放在报告最前面）

报告第一屏必须是 30 秒速读卡片，任何老板都能直接看：

```
## Executive Summary

[竞对名称] | 年GMV ~$X | [核心获客模式]
一句话: [最重要的战略判断]
Top 3 立刻做的事:
  1. [动作] — [抄/打] — [预期效果]
  2. [动作] — [抄/打] — [预期效果]
  3. [动作] — [抄/打] — [预期效果]
```

### 完整报告

写入 `~/dtc-reports/[竞对名称]-竞对拆解-[日期].md`。目录不存在则自动创建。

使用 references/report-template.md 的结构。

## 执行约束

- Phase 1-2的搜索可以并行
- Phase 3-5的搜索可以并行
- Phase 6-7的搜索可以并行
- 一次最多发起4个并行WebSearch
- 每次搜索后检查结果质量，信息不足时换个词搜一次，再不回就算了
- 标注数据可信度：确认 / 估算 / 推断
- 小站点（流量<50K）常见数据缺失，这是正常的——用行业benchmark推断并标注

## 后续动作

报告生成后，主动询问用户：
"报告已输出。需要我帮你把这个案例推到GitHub仓库吗？"

如果用户说需要修改或补充某个Phase的分析，直接执行修改。
