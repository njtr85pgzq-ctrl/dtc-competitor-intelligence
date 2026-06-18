# Phase 5: 广告打法逆向工程

## 搜索策略

```
并行搜索:
1. "[品牌名] Google Ads paid search advertising campaign"
2. "[品牌名] Facebook Meta Ads Instagram advertising"
3. "[品牌名] TikTok Ads advertising"
4. "[品牌名] YouTube influencer review sponsorship"
```

直接查看广告库（无需搜索）：
- Meta Ad Library: https://www.facebook.com/ads/library/
- TikTok Ad Library: https://library.tiktok.com/ads/
- Google Ad Transparency: https://adstransparency.google.com/

## 广告分析清单

```
□ 当前同时在跑的广告数量（估算）
□ 素材类型分布: 视频___% / 图片___% / UGC___%
□ 核心卖点/文案角度（至少提取3个）
□ 主要投哪类人群（受众定向推断）
□ 落地页类型：产品页 vs 专题页 vs 合集页 vs 弹窗
□ 是否有重定向广告（说明在做转化漏斗）
□ 季节性投放模式（节日季 vs 全年稳定）
```

## 广告成熟度评级

- **成熟**: 多渠道投放，素材多样，有明显漏斗策略，重定向活跃
- **中等**: 1-2个渠道投放，素材有一定优化，但漏斗不完整
- **新手**: 极小量投放，素材单一，无重定向
- **未投**: 所有渠道搜不到广告 → 重大发现

## 广告策略结论

```
对方广告成熟度: [新手/中等/成熟]
判断依据:

对方广告弱点:
1.

我们可以直接抄/优化的:
1.
```

## 特别注意

如果竞对完全没有投广告 + 社媒存在感也极低 → 这意味着：
1. 他们的流量来源非常单一（大概率只有SEO+直接访问）
2. 付费广告渠道是蓝海
3. 我们可以用广告快速起量，形成先发优势
4. 但同时也要验证：为什么他们不投？是品类ROI天然低，还是他们不会？

## 可调用的 Marketing Skills

广告逆向工程时——不只是搜"有没有投"，而是调用专业 ad skill 做平台级拆解：

| 平台 | 调用的 Skill | 逆向什么 |
|------|-------------|---------|
| Google Ads | `paid-ads/platforms/google-ads` | Search/Display/Shopping/PMax 投放结构、关键词覆盖、出价策略推断 |
| Meta Ads | `paid-ads/platforms/meta-ads` | FB/IG 在投广告、受众定向、素材类型、落地页 |
| TikTok Ads | `paid-ads/platforms/tiktok-ads` | TT在投素材、创意角度、投放规模 |
| YouTube Ads | `paid-ads/platforms/youtube-ads` | YT在投视频广告、In-stream/Discovery |
| LinkedIn Ads | `paid-ads/platforms/linkedin-ads` | B2B品类是否投LinkedIn |
| Reddit Ads | `paid-ads/platforms/reddit-ads` | Reddit社区广告投放 |
| Display | `paid-ads/formats/display-ads` | GDN/程序化Display投放 |
| Native | `paid-ads/formats/native-ads` | 原生广告/内容推荐广告 |
| CTV | `paid-ads/formats/ctv-ads` | 联网电视广告（品牌向） |
| 广告策略 | `strategies/commercial/paid-ads` | 整体广告策略判断：漏斗完整度、预算分配、渠道组合 |
| 落地页 | `pages/marketing/landing-page` | 广告→落地页匹配度、转化设计 |
| 定价 | `strategies/commercial/pricing/pricing-strategy` | 广告中的定价策略和折扣模式 |
