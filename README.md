# 📈 E-Commerce Ad Campaign Performance Analysis

> **End-to-end paid advertising analytics project** measuring campaign efficiency across platforms, identifying ROAS leaders and uncovering where ad spend is  and isn't  working.  
> Tools: `Python` · `pandas` · `Excel` · `Power BI` &nbsp;|&nbsp; Dataset: 2,000 records · Full Year 2024

---

## 📁 Table of Contents

- [Background & Overview](#-background--overview)
- [Data Structure Overview](#-data-structure-overview)
- [Executive Summary](#-executive-summary)
- [Insights Deep Dive](#-insights-deep-dive)
- [Recommendations](#-recommendations)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)

---

## 🔍 Background & Overview

### Business Problem

An e-commerce business running paid advertising across five platforms needed to understand which campaigns and channels were delivering profitable returns  and which were burning budget without proportional revenue. The core question:

> *"Where should we increase ad spend, where should we cut and what is actually driving conversions?"*

### Objectives

- Calculate and compare ROAS, CTR, CVR and CPA across all platforms and campaigns
- Identify which platform × campaign combinations deliver the strongest and weakest returns
- Uncover temporal patterns (monthly, quarterly) in ad performance
- Distinguish between volume-driven and efficiency-driven revenue performance
- Deliver ranked, data-backed budget reallocation recommendations

### Methodology

| Step | Description | Tool |
|------|-------------|------|
| 1. Problem definition | Defined key advertising KPIs before analysis | — |
| 2. Data cleaning & audit | Validated 2,000 rows, checked nulls, computed derived metrics | `excel` |
| 3. Metric engineering | Derived CTR, CVR, CPA, ROAS from raw impressions/clicks/spend/revenue | `excel calculated fields` |
| 4. Platform segmentation | Aggregated performance by platform, campaign, and platform × campaign | `excel` |
| 5. Temporal analysis | Monthly and quarterly revenue and ROAS trends | `excel` · `datetime` |
| 6. Correlation analysis | Identified which raw inputs most predict revenue 
| 7. Dashboard | Built interactive Excel + Power BI dashboard with slicers | `Excel` · `Power BI` |

---

## 🗂 Data Structure Overview

### Dataset at a Glance

**2,000 records · Jan 2024 – Feb 2025 · 5 platforms · 8 campaigns**

| Column | Type | Description |
|--------|------|-------------|
| `Campaign_ID` | String | Unique identifier per record (CAMP1000–CAMP2999) |
| `Campaign_Name` | Categorical | 8 campaign types (Holiday Deals, Flash Sale, Winter Promo, etc.) |
| `Platform` | Categorical | 5 channels: Google Ads, Meta Ads, TikTok Ads, Email Marketing, Affiliate |
| `Date` | Date | Daily record date |
| `Impressions` | Integer | Total ad impressions served |
| `Clicks` | Integer | Total clicks received |
| `Conversions` | Integer | Completed purchases or goal actions |
| `Ad_Spend` | Float ($) | Total spend for the record |
| `Revenue` | Float ($) | Revenue attributed to the record |
| `CTR` *(derived)* | Float (%) | `Clicks / Impressions` |
| `Conversion_Rate` *(derived)* | Float (%) | `Conversions / Clicks` |
| `CPA` *(derived)* | Float ($) | `Ad_Spend / Conversions` — cost per acquisition |
| `ROAS` *(derived)* | Float (x) | `Revenue / Ad_Spend` — return on ad spend |
| `Year` / `Month` / `Month_Number` | Temporal | Derived date parts for time-series analysis |

### Data Quality

- ✅ Zero null values across all columns
- ✅ All 2,000 Campaign IDs unique — no duplicate records
- ✅ Derived metrics (CTR, CVR, CPA, ROAS) validated against source columns
- ✅ Consistent categorical values across Platform and Campaign_Name
- ℹ️ Date range spans into early 2025 (Jan–Feb) — treated as a separate comparative period where relevant

---

## 📋 Executive Summary

### The Central Finding

> **Ad Spend has a near-zero correlation with Revenue (r = 0.019). Conversions, however, correlate with Revenue at r = 0.87.**

Spending more does not reliably produce more revenue. Converting more does. This shifts the optimisation focus from *"increase budget"* to *"improve conversion efficiency per dollar spent."*

### Key Metrics at a Glance

| Metric | Value |
|--------|-------|
| Total Revenue | **$42,617,275** |
| Total Ad Spend | **$5,204,110** |
| Overall ROAS | **8.19x** |
| Total Impressions | **157,617,854** |
| Total Clicks | **7,008,736** |
| Total Conversions | **598,748** |
| Overall CTR | **4.45%** |
| Overall CVR | **8.54%** |
| Ad Spend ↔ Revenue correlation | **r = 0.019** |
| Conversions ↔ Revenue correlation | **r = 0.87** |

### Performance Summary by Platform

| Platform | Revenue | Ad Spend | ROAS | CTR | CVR | CPA |
|----------|---------|----------|------|-----|-----|-----|
| Google Ads | $9,148,694 | $1,088,177 | **8.41x** | 4.42% | 8.23% | $8.99 |
| Email Marketing | $8,919,627 | $1,062,118 | 8.40x | **4.59%** | 8.56% | **$8.31** |
| Meta Ads | $8,726,840 | $1,098,464 | 7.94x | 4.47% | 8.45% | $8.78 |
| TikTok Ads | $8,054,448 | $956,149 | 8.42x | 4.45% | **8.95%** | $8.33 |
| Affiliate | $7,767,665 | $999,201 | 7.77x | 4.29% | 8.59% | $9.09 |

> 💡 **TikTok Ads** achieves the highest CVR (8.95%) and second-lowest CPA ($8.33) despite the lowest spend — the most capital-efficient platform in the mix.

---

## 🔬 Insights Deep Dive

### 1. Platform Performance

| Platform | ROAS | CVR | CPA | Rev/Spend Rank |
|----------|------|-----|-----|----------------|
| TikTok Ads | 8.42x | 8.95% | $8.33 | 🥇 1st (efficiency) |
| Google Ads | 8.41x | 8.23% | $8.99 | 🥈 2nd |
| Email Marketing | 8.40x | 8.56% | $8.31 | 🥉 3rd |
| Meta Ads | 7.94x | 8.45% | $8.78 | 4th |
| Affiliate | 7.77x | 8.59% | $9.09 | 5th |

**Key findings:**
- **TikTok Ads** converts at the highest rate (8.95%) with the second-lowest CPA — strong signals for budget increase
- **Google Ads** leads on raw revenue ($9.1M) but has the highest CPA ($8.99) and the lowest CVR — volume is doing the work, not efficiency
- **Email Marketing** delivers the lowest CPA ($8.31) tied with TikTok, making it a high-efficiency, low-waste channel
- **Affiliate** consistently underperforms across all efficiency metrics (ROAS 7.77x, highest CPA $9.09) — the clearest candidate for spend reduction
- **Meta Ads** sits below the portfolio average ROAS (8.19x) with no standout efficiency metric

---

### 2. Campaign Performance

| Campaign | Revenue | Ad Spend | ROAS | CTR | CVR |
|----------|---------|----------|------|-----|-----|
| Brand Awareness | $5,876,152 | $680,584 | **8.63x** | 4.56% | 8.49% |
| Holiday Deals | $5,658,538 | $654,541 | **8.65x** | 4.09% | 8.99% |
| Winter Promo | $5,471,284 | $673,074 | 8.13x | 4.49% | **9.13%** |
| New Product Launch | $5,427,155 | $646,174 | 8.40x | 4.36% | 8.69% |
| Flash Sale | $5,296,928 | $607,557 | **8.72x** | **4.66%** | 8.58% |
| Retargeting Campaign | $5,059,369 | $651,364 | 7.77x | 4.60% | 8.39% |
| Clearance Event | $5,001,329 | $592,818 | 8.44x | 4.40% | 8.17% |
| Summer Sale | $4,826,520 | $697,998 | 6.91x | 4.44% | 7.90% |

**Key findings:**
- **Flash Sale** delivers the highest ROAS (8.72x) and the highest CTR (4.66%) — the most well-rounded performer
- **Holiday Deals** pairs a strong ROAS (8.65x) with the highest CVR (8.99%) — when users click, they buy
- **Summer Sale** is the weakest campaign overall: lowest ROAS (6.91x), lowest CVR (7.90%), and highest spend ($698K) — negative combination
- **Retargeting Campaign** underperforms its purpose: a retargeting campaign should convert at above-average rates, but 8.39% CVR sits below the 8.54% portfolio average
- **Winter Promo** leads all campaigns on CVR (9.13%) despite a mid-table ROAS — conversion quality is high but scale or spend efficiency is holding it back

---

### 3. Platform × Campaign Matrix (Top & Bottom Performers)

**Top 5 ROAS combinations:**

| Platform | Campaign | Revenue | Ad Spend | ROAS |
|----------|----------|---------|----------|------|
| Meta Ads | Brand Awareness | $1,499,649 | $128,983 | **11.63x** |
| Email Marketing | Clearance Event | $1,245,624 | $116,085 | **10.73x** |
| TikTok Ads | Flash Sale | $1,078,149 | $101,519 | **10.62x** |
| TikTok Ads | Winter Promo | $1,347,944 | $129,794 | **10.39x** |
| Google Ads | Flash Sale | $1,165,669 | $113,737 | **10.25x** |

**Bottom 5 ROAS combinations (budget risk):**

| Platform | Campaign | Revenue | Ad Spend | ROAS |
|----------|----------|---------|----------|------|
| Email Marketing | Summer Sale | $1,171,379 | $192,885 | ⚠️ **6.07x** |
| Meta Ads | Winter Promo | $765,972 | $119,858 | ⚠️ **6.39x** |
| TikTok Ads | Retargeting Campaign | $884,614 | $137,209 | ⚠️ **6.45x** |
| Affiliate | Brand Awareness | $720,396 | $109,627 | ⚠️ **6.57x** |
| Affiliate | Retargeting Campaign | $858,433 | $128,175 | ⚠️ **6.70x** |

> The spread between the best (11.63x) and worst (6.07x) platform × campaign ROAS is nearly 2x — significant optimisation headroom exists within the current campaign mix without launching anything new.

---

### 4. Temporal Patterns

**Monthly Revenue & ROAS:**

| Month | Revenue | Ad Spend | ROAS | vs. Annual Avg |
|-------|---------|----------|------|----------------|
| January | $5,429,032 | $677,817 | 8.01x | +28.1% ↑ |
| February | $5,432,642 | $688,756 | 7.89x | +27.6% ↑ |
| March | $3,333,589 | $351,179 | **9.49x** | -21.7% ↓ |
| April | $3,339,954 | $404,961 | 8.25x | -21.5% ↓ |
| May | $2,885,579 | $393,456 | 7.33x | -32.1% ↓ |
| June | $2,937,007 | $354,002 | 8.30x | -31.0% ↓ |
| July | $3,407,799 | $389,697 | 8.74x | -19.9% ↓ |
| August | $2,886,554 | $378,129 | 7.63x | -32.1% ↓ |
| September | $2,959,273 | $344,543 | 8.59x | -30.4% ↓ |
| October | $3,044,116 | $365,893 | 8.32x | -28.4% ↓ |
| November | $3,130,588 | $380,345 | 8.23x | -26.4% ↓ |
| December | $3,831,141 | $475,331 | 8.06x | -10.0% ↓ |

**Quarterly Summary:**

| Quarter | Revenue | Ad Spend | ROAS |
|---------|---------|----------|------|
| Q1 | $14,195,264 | $1,717,753 | 8.26x |
| Q2 | $9,162,540 | $1,152,419 | 7.95x |
| Q3 | $9,253,627 | $1,112,369 | 8.32x |
| Q4 | $10,005,844 | $1,221,569 | 8.19x |

**Key findings:**
- **Q1 dominates** — January and February alone account for 33% of full-year revenue, likely driven by post-holiday demand, Winter Promo and New Year campaigns
- **March achieves the highest ROAS (9.49x)** despite lower absolute revenue, suggesting lean, high-efficiency spend in that month
- **May and August** are the weakest months on both revenue and ROAS — potential candidates for spend reduction or creative refreshes
- **Q2 is the weakest quarter (ROAS 7.95x)** — the Summer Sale campaign drags performance here (6.91x ROAS, lowest CVR)
- **December recovers** to $3.8M heading into Q1 — Holiday Deals and seasonal campaigns doing their job

---

### 5. Correlation Analysis

| Metric | Correlation with Revenue (r) | Interpretation |
|--------|------------------------------|----------------|
| Conversions | **+0.87** | Very strong — the primary revenue driver |
| Clicks | **+0.70** | Strong — volume of engaged users matters |
| ROAS | **+0.58** | Moderate — efficiency and revenue aligned |
| Impressions | **+0.50** | Moderate — reach contributes but isn't sufficient |
| CTR | **+0.43** | Moderate — click quality matters |
| CVR | **+0.42** | Moderate — conversion rate quality matters |
| Ad Spend | **+0.02** | ⚠️ Near zero — spend alone does not drive revenue |

> 💡 **Ad Spend has essentially no correlation with Revenue (r = 0.019).** Doubling the budget will not double revenue. Increasing the *conversion efficiency* of existing traffic is the higher-leverage lever.

---

## 💡 Recommendations

### 1. Increase TikTok Ads budget — highest efficiency platform
TikTok Ads has the highest CVR (8.95%), second-lowest CPA ($8.33), and strong ROAS (8.42x) while receiving the lowest ad spend ($956K) of any platform. It is systematically underfunded relative to its efficiency.  
**Action:** Reallocate 15–20% of Meta Ads or Affiliate budget to TikTok, prioritising Flash Sale and Winter Promo combinations (ROAS 10.39–10.62x).  
**Estimated impact:** +8–15% improvement in portfolio ROAS with budget-neutral reallocation

### 2. Scale Flash Sale and Holiday Deals — top ROAS campaigns
Flash Sale (8.72x ROAS, 4.66% CTR) and Holiday Deals (8.65x ROAS, 8.99% CVR) are the two most well-rounded campaigns. Both have above-average performance across every metric.  
**Action:** Increase investment in Flash Sale and Holiday Deals in Q3 and Q4 when overall revenue dips. Run Flash Sale events in May and August — currently the two weakest months.  
**Estimated impact:** 15–20% revenue uplift in historically underperforming months

### 3. Audit or restructure Summer Sale — lowest performer
Summer Sale has the worst ROAS (6.91x), lowest CVR (7.90%), and the second-highest spend ($698K). It is the only campaign combining high investment with low efficiency.  
**Action:** Conduct creative and audience review. If performance cannot be improved to above 8.0x ROAS in testing, reallocate Summer Sale budget to Flash Sale or Brand Awareness which use similar seasonal timing.  
**Estimated impact:** Recovering Summer Sale spend to portfolio average ROAS would generate ~$840K in additional revenue at current spend

### 4. Fix Retargeting Campaign — it should convert above average, not below
Retargeting campaigns target warm audiences who have already engaged with the brand. A CVR of 8.39% (below the 8.54% portfolio average) indicates the audiences, creatives, or offers are not differentiated enough to convert better than cold traffic.  
**Action:** Refresh retargeting creatives with personalised offers (abandoned cart discount, dynamic product ads). Tighten audience windows from 30-day to 7-day lookback for higher-intent targeting.  
**Estimated impact:** Even a 0.5 pp CVR improvement would generate ~3,000 additional conversions at current traffic volumes

### 5. Reduce Affiliate spend — worst efficiency metrics across the board
Affiliate consistently delivers the lowest ROAS (7.77x), lowest CTR (4.29%), and highest CPA ($9.09) of any platform. It is the only platform underperforming on every measurable dimension.  
**Action:** Audit affiliate partners for quality. Remove or renegotiate terms with partners generating below 7.0x ROAS. Redirect freed budget to TikTok or Email Marketing.  
**Estimated impact:** Reallocating 30% of Affiliate budget to Email Marketing (CPA $8.31) saves ~$299K in CPA inefficiency per year

### 6. Protect and replicate Q1 and March playbook
Q1 drives 33% of full-year revenue. March achieves the highest ROAS of any month (9.49x) with lower absolute spend. The combination of Winter Promo + New Product Launch campaigns in Q1 appears highly effective.  
**Action:** Document the creative mix, audience segments, and spend distribution that produced March's efficiency. Apply the same structure to Q2 and Q3 campaigns to raise underperforming months.  
**Estimated impact:** Lifting Q2 ROAS from 7.95x to Q1 levels (8.26x) on the same spend would generate ~$357K additional Q2 revenue

---

## 📁 Project Structure

```
ecommerce-ad-campaign-analysis/
│
├── data/
│   ├── raw/
│   │   └── ecommerce_ad_campaign_dataset.csv   # Original 2,000-record dataset
│   └── processed/
│       └── campaign_with_metrics.csv           # Dataset with derived KPIs added
│
├── excel/
│   ├── 01_data_cleaning.                  # Null checks, type casting, derived metrics
│   ├── 02_platform_analysis.              # ROAS, CVR, CPA by platform
│   ├── 03_campaign_analysis.              # Performance by campaign type
│   ├── 04_temporal_analysis.              # Monthly and quarterly trends
│   └── 05_correlation_analysis.           # What actually drives revenue
│
├── dashboard/
│   ├── ecommerce_ad_campaign_dashboard.xlsx    # Excel dashboard with pivot tables
│   └── campaign_powerbi.pbix                  # Power BI interactive dashboard
│
├── visuals/
│   └── *.png                                  # Exported charts for README/portfolio
│
└── README.md
```

---

## ⚙️ How to Run

**1. Clone the repo**
```bash
git clone https://github.com/PatienceAnono/ecommerce-ad-campaign-analysis.git
cd ecommerce-ad-campaign-analysis
```

**2. excel open**
```

**3. Open dashboards**
- Excel: open `dashboard/ecommerce_ad_campaign_dashboard.xlsx` directly
- Power BI: open `dashboard/campaign_powerbi.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/)

---

## 🔖 Key Formulas Used

```Excel and python
| Click-Through Rate (CTR) | `=F2/E2` | `df['CTR'] = df['Clicks'] / df['Impressions']` |
| Conversion Rate (CVR) | `=G2/F2` | `df['CVR'] = df['Conversions'] / df['Clicks']` |
| Cost Per Acquisition (CPA) | `=H2/G2` | `df['CPA'] = df['Ad_Spend'] / df['Conversions']` |
| Return on Ad Spend (ROAS) | `=I2/H2` | `df['ROAS'] = df['Revenue'] / df['Ad_Spend']` |
| Cost Per Click (CPC) | `=H2/F2` | `df['CPC'] = df['Ad_Spend'] / df['Clicks']` |
| Profit / Loss | `=I2-H2` | `df['Profit'] = df['Revenue'] - df['Ad_Spend']` |

> **Column mapping (CampaignData sheet):** E = Impressions · F = Clicks · G = Conversions · H = Ad_Spend · I = Revenue · formulas start row 2
```

---

## 🔖 Analytical Limitations

- Revenue is attributed at the campaign-record level — multi-touch attribution across platforms is not modelled
- Campaign costs are included but media planning context (target CPM, bid strategies) is not available
- The dataset extends into early 2025 (Jan–Feb) — these months are included in overall totals but excluded from annual trend comparisons
- Creative-level data (ad format, copy, visual) is not available; performance differences within platforms may be creative-driven

---

*Patience Anono · Data Analytics Portfolio · [github.com/PatienceAnono](https://github.com/PatienceAnono)*










