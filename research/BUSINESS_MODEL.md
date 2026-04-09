# ShieldAI — Business Model

---

## 1. Revenue Model

ShieldAI sells annual subscriptions, not monthly plans and not one-time purchases.

**Why annual:**
Security is not a one-time purchase — it's an ongoing service. Threats emerge continuously, and agents need to run on a regular schedule to be useful. An annual commitment matches the cadence of the product.

Operationally, annual upfront payments reduce churn risk, improve cash flow, and make LLM API costs predictable. Monthly plans at this price point tend to generate higher churn from users who deactivate after a scare resolves — exactly the cohort that benefits most from year-round protection.

A one-time plugin purchase was ruled out because LLM API calls have a real, ongoing cost per site per month. A one-time sale cannot sustain per-site API costs at any reasonable price point.

---

## 2. Pricing Strategy

| Tier | Price | Target User | Key Unlock |
|------|-------|-------------|------------|
| Free | $0 | Any WordPress user | See recommendations, can't execute |
| Shield | $79/year | Solo site owners, bloggers | Full agents, approval queue, executors, rollback |
| Shield Pro | $199/year | WooCommerce stores, serious sites | + Incident reports, extended audit log |
| Agency | $399/year | Freelancers, agencies | Up to 20 sites, 1-year audit log |

**Why $79 for Shield:**
Wordfence Premium is $119/year; Solid Security Pro is $99/year. At $79, ShieldAI enters the market below established premium players while still being positioned as premium (not competing with free-tier-only tools). The value proposition — AI-generated fixes, not just detection — justifies pricing at or near Wordfence's level even at lower market awareness.

**Why $199 for Shield Pro:**
The jump from $79 to $199 is justified by incident reports (a deliverable WooCommerce owners can show payment processors or partners) and extended audit log retention (compliance value). Sucuri's basic platform starts at $199/year, validating this price point for the WooCommerce/business segment.

**Why $399 for Agency:**
Covers up to 20 sites. At $399/20 = $19.95/site/year, agencies can resell site-level security management to clients at $30-50/month and keep a comfortable margin. Competitive with ManageWP's security add-ons and MainWP extended plans.

**The free tier:**
Free users can see what ShieldAI detects but cannot act on recommendations. This is deliberately frustrating — it shows the value of the queue without delivering it. The free tier serves as the acquisition funnel: WordPress.org installs come first, paid upgrades follow when users encounter a real detection they want to act on.

---

## 3. Unit Economics

All figures are estimates [ESTIMATE]. Methodology is stated for each.

### LLM API Cost per Site

| Agent | Frequency | Estimated tokens/run | Cost/run (Claude Haiku) | Monthly cost |
|-------|-----------|---------------------|------------------------|-------------|
| ThreatResponseAgent | Every 15 min (max 4 active runs/day) | ~2,000 | ~$0.001 | ~$0.03 |
| VulnScanAgent | Weekly | ~5,000 | ~$0.003 | ~$0.01 |
| HardeningAgent | Monthly | ~8,000 | ~$0.005 | ~$0.005 |
| IncidentReportAgent | ~2 per year average | ~10,000 | ~$0.006 | ~$0.001 |
| **Total** | | | | **~$0.05/month** |

[ESTIMATE: Based on Claude Haiku pricing of ~$0.25/million input tokens + $1.25/million output tokens as of early 2024. Actual usage depends on detection frequency. Higher-activity sites cost more; most sites have low daily threat activity. The $0.70/month figure cited earlier assumed more frequent triggering — actual average is likely lower. Use $0.10-0.25/site/month as conservative planning figure to account for variable activity.]

### Gross Margin by Tier (Annual)

| Tier | Price | LLM cost/year (conservative @ $0.25/mo) | Gross Margin | Margin % |
|------|-------|-----------------------------------------|-------------|----------|
| Shield | $79 | $3.00 | $76 | 96% [ESTIMATE] |
| Shield Pro | $199 | $3.00 | $196 | 98% [ESTIMATE] |
| Agency (20 sites) | $399 | $60.00 | $339 | 85% [ESTIMATE] |

[ASSUMPTION: Margin figures exclude payment processing (~3%), hosting/infrastructure, support, and customer acquisition costs. These are contribution margins before operating expenses.]

### Lifetime Value (LTV) by Tier

Assuming 70% annual retention rate [ASSUMPTION based on SaaS security plugin benchmarks]:

| Tier | Annual Price | Avg Lifetime (yrs at 70% retention) | LTV |
|------|-------------|-------------------------------------|-----|
| Shield | $79 | 2.85 years | $225 [ESTIMATE] |
| Shield Pro | $199 | 2.85 years | $567 [ESTIMATE] |
| Agency | $399 | 3.5 years [ASSUMPTION: agencies churn less] | $1,397 [ESTIMATE] |

### Customer Acquisition Cost (CAC) Targets

[ASSUMPTION: Early-stage CAC via organic WordPress.org + content marketing]

| Channel | Expected CAC | LTV:CAC at Shield tier |
|---------|-------------|----------------------|
| WordPress.org organic | $10-20 | 11-22x [ESTIMATE] |
| SEO/content marketing | $20-50 | 4.5-11x [ESTIMATE] |
| Review site partnerships | $30-80 | 2.8-7.5x [ESTIMATE] |
| Paid search | $50-150 | 1.5-4.5x [ESTIMATE] |

Target: LTV:CAC > 3x across all channels. Paid search is viable only at Shield Pro / Agency tier.

---

## 4. Financial Projections (Years 1-3)

[ESTIMATE — All figures are modeled. Methodology: install count based on comparable WordPress plugin growth curves; conversion rates based on freemium security plugin benchmarks; tier distribution based on persona sizing.]

### Base Case (Conservative — validated by user review)

**Assumptions:**
- WordPress.org free tier grows at 250 new installs/month (Month 1) scaling to 800/month by Month 12
- Free-to-paid conversion rate: 2% in Year 1, 3% in Year 2 [ASSUMPTION — early plugins typically convert below 3%; 2% is realistic for an unproven brand]
- Tier distribution: 70% Shield, 20% Shield Pro, 10% Agency [ASSUMPTION]
- Annual retention: 70%

| Metric | Year 1 | Year 2 | Year 3 |
|--------|--------|--------|--------|
| Free installs (active) | 4,000 | 12,000 | 25,000 |
| Paid customers | 120 | 550 | 1,125 |
| — Shield ($79) | 84 | 385 | 788 |
| — Shield Pro ($199) | 24 | 110 | 225 |
| — Agency ($399) | 12 | 55 | 112 |
| ARR | ~$13.5K | ~$63.5K | ~$130K |
| LLM API costs | ~$1.8K | ~$8K | ~$16.5K |
| Net Revenue (after API) | ~$11.7K | ~$55.5K | ~$113.5K |

### Upside Case (if WPBeginner feature or community traction)

| Metric | Year 1 | Year 2 | Year 3 |
|--------|--------|--------|--------|
| Free installs (active) | 8,000 | 22,000 | 45,000 |
| Paid customers | 240 | 1,100 | 2,250 |
| ARR | ~$27K | ~$127K | ~$260K |

[DATA GAP: Actual conversion rate from WordPress.org free installs to paid is highly variable (1-10% range). The base case 3% is based on freemium plugin benchmarks but needs validation from real install data.]

---

## 5. Free Tier Economics

The free tier is funded by the value it generates as an acquisition funnel — not as a standalone product. 

A free user who sees ShieldAI detect a real vulnerability and display the fix in a blurred/locked UI is a warm upgrade lead. The emotional hook is seeing a specific, actionable recommendation they can't act on without upgrading. This is more effective than abstract "upgrade for more features" messaging.

Free tier LLM cost: [ASSUMPTION: Free users do NOT trigger LLM analysis. The free tier detects threats using local heuristics and CVE lookups only. LLM analysis is called only when the user upgrades. This keeps free tier marginal cost near zero.]

Expected free-to-paid conversion timeline: 30-90 days from install, triggered by first detection event.

---

## 6. Distribution and Go-to-Market

**Primary channel:** WordPress.org plugin directory. This is the highest-leverage distribution channel for any WordPress plugin. Wordfence's 5M+ installs started here. A well-crafted plugin page, 5-star ratings from early adopters, and a compelling free tier drive organic installs at near-zero CAC.

**Content marketing:** Security-focused content targeting "wordpress site hacked," "wordpress plugin vulnerability," "how to secure woocommerce" queries. Each agent's output maps to a content piece (e.g., "What to do when Wordfence says you have a critical vulnerability").

**Review site outreach:** WPBeginner, Kinsta, Elegant Themes Blog. A single featured review on WPBeginner has driven thousands of plugin installs for comparable tools. Investment in hands-on review relationships is high-leverage.

**YouTube:** The approval queue UI sells itself visually. A 5-minute tutorial showing a real vulnerability being detected, explained in plain English, approved, and executed is compelling content.

**Agency partnerships:** White-label or reseller discussions with WordPress maintenance agencies. Agencies already selling security monitoring can add ShieldAI to their stack.

---

## 7. Key Business Risks

**Risk 1 — Wordfence or Sucuri adds AI-generated fix recommendations**
Mitigation: Accelerate the approval queue data flywheel. Our moat is the proprietary dataset of approve/dismiss decisions, not the AI feature itself. Features can be copied; training data cannot.

**Risk 2 — Free-to-paid conversion rate is lower than 3%**
Mitigation: Invest in the free tier detection experience. The more valuable the free tier detections are (real CVEs, specific threats), the higher the conversion pressure. Also: email nurture sequences for free users.

**Risk 3 — LLM API costs increase significantly**
Mitigation: Multi-provider support (Claude primary, OpenAI fallback). Pricing tiers structured with 85%+ gross margin buffer. Annual subscription model provides cost predictability.

**Risk 4 — WordPress.org review velocity is slow / negative reviews early**
Mitigation: Managed rollout to a small beta cohort first. Recruit 20-30 trusted testers for private beta before public launch. Early 5-star reviews are critical for plugin directory ranking.

**Risk 5 — WP-Cron limitation damages trust on low-traffic sites**
Mitigation: Phase 1 ships with an explicit notice in the admin panel explaining the WP-Cron dependency and providing setup instructions for server cron. Managed host detection shows "You're covered" on Kinsta/WP Engine. This is documented prominently in marketing copy — not hidden.
