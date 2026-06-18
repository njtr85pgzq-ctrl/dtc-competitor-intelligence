# Phase 9: 品牌口碑与用户洞察

## 搜索策略

```
并行搜索:
1. "[品牌名] Trustpilot reviews rating complaints"
2. "Reddit [品牌名] review experience discussion"
3. "[品牌名] Amazon product reviews customer feedback"
4. "[品牌名] YouTube review comment"
```

## 数据源优先级

| 优先 | 数据源 | 价值 |
|------|-------|------|
| 1 | Trustpilot | 结构化评分，可量化统计 |
| 2 | Reddit | 真实用户原话，情绪最真实 |
| 3 | Amazon评论 | 产品层面反馈最细 |
| 4 | YouTube评论 | 视频评测下的提问 = 购买前顾虑 |
| 5 | 社媒评论区 | @朋友的互动 = 购买意图信号 |

## 分析维度

### 评分与评论量
- Trustpilot评分 + 评论总数
- 站内评论插件评分 + 评论数
- Amazon评分 + 评论数
- 判断：评论量 = 销量 × 留评率

### 好评词云
提取高频好评关键词，判断竞对的"核心卖点"在用户心智中是什么。

### 差评词云
提取高频差评关键词，这是竞对的弱点，也是我们的突破口。

### 用户原话
收集3-5条有代表性的用户原话（好评+差评），直接用于：
- 广告文案
- 产品页卖点
- 竞对比图

### 客服/售后
- 差评回复率（Trustpilot数据）
- 回复速度
- 退货政策质量
- 是否有多语言客服

## 输出

```
用户爱他们: 因为____（核心卖点）
用户恨他们: 因为____（最大痛点）
用户不知道他们: 品牌认知度 ____

→ 如果我们做到"____ + ____"，就能直接吃掉____
```

## 可调用的 Marketing Skills

口碑分析不只是"看好评差评"，调用专项 skill 做系统化评估：

| 分析维度 | 调用的 Skill | 做什么 |
|---------|-------------|--------|
| 品牌监控 | `strategies/brand/brand-monitoring` | 竞对全网品牌提及、舆情Sentiment |
| 品牌保护 | `strategies/brand/brand-protection` | 竞对是否注册品牌/商标，仿品/黑帽情况 |
| 品牌定位 | `strategies/brand/branding` | 竞对品牌定位、差异化信息 |
| 社区运营 | `channels/community/community-forum` | 竞对在Reddit/FB Group/Discord的社区声量 |
| UGC | `channels/owned/employee-generated-content` | 竞对用户自发内容量（UGC/口碑传播） |
| 内容营销 | `strategies/brand/content-marketing` | 竞对品牌内容营销的整体评估 |
