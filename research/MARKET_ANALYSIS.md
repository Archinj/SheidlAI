# ShieldAI Market Analysis
### Agentic WordPress Security Plugin
**Date:** April 2026  
**Classification:** Internal Research  
**Status:** Working Draft

---

## Table of Contents
1. [Executive Summary](#1-executive-summary)
2. [Market Overview](#2-market-overview)
3. [TAM / SAM / SOM](#3-tam--sam--som)
4. [Market Trends](#4-market-trends)
5. [Why Now — Timing Analysis](#5-why-now--timing-analysis)
6. [Market Risks and Barriers](#6-market-risks-and-barriers)
7. [Opportunity Assessment](#7-opportunity-assessment)

---

## 1. Executive Summary

WordPress is the world's dominant CMS, powering approximately 43% of all websites globally. (Source: https://w3techs.com/technologies/details/cm-wordpress) This installed base — estimated at over 800 million sites as of early 2026 — represents an enormous and structurally underserved attack surface. Existing security solutions either require significant manual expertise (Sucuri, MalCare Pro) or deliver broad, reactive protection without intelligent triage or remediation (Wordfence, iThemes Security).

ShieldAI enters this market as a new category: an **agentic** WordPress security plugin — one that doesn't just detect threats but autonomously investigates, prioritises, and remediates them. The timing is compelling: AI-native tooling is now mature enough to be embedded in plugins, WordPress attacks are accelerating in volume and sophistication, and small-to-medium businesses (SMBs) increasingly acknowledge that manual security management is operationally unsustainable.

Key findings:
- **TAM:** ~$4.2B [ESTIMATE] — the addressable global market for WordPress-specific security tooling
- **SAM:** ~$920M [ESTIMATE] — English-speaking SMB and agency segments with willingness to pay for premium tools
- **SOM (Year 3):** ~$18–28M ARR [ESTIMATE] — realistic capture based on 1–2% of SAM at competitive price points
- The market leader (Wordfence) has 5M+ active installs but [ASSUMPTION] generates <$50M ARR, suggesting significant pricing upside and undermonetisation in the segment
- The average cost of a successful WordPress breach to an SMB ranges from $5,000 to $50,000+ [ESTIMATE] when accounting for remediation, downtime, and reputational loss, creating a clear ROI case for a $20–50/month SaaS plugin

The window for establishing a category-defining AI-native WordPress security product is open now — but is unlikely to remain open beyond 2027, as Wordfence and Automattic both have the resources to ship AI features if they prioritise them.

---

## 2. Market Overview

### 2.1 The WordPress Ecosystem

WordPress is the foundational layer of the modern web for independent publishers, SMBs, agencies, and enterprises alike.

| Metric | Value | Source / Note |
|---|---|---|
| Share of all websites | ~43% | (Source: https://w3techs.com/technologies/details/cm-wordpress) |
| Share of CMS market | ~63% | (Source: https://w3techs.com/technologies/history_overview/content_management) |
| Estimated total sites | 810M+ [ESTIMATE] | Based on ~1.9B total websites × 43% |
| Active/maintained sites | ~500M [ESTIMATE] | Industry consensus; many sites are dormant |
| Plugin repository size | 59,000+ plugins | (Source: https://wordpress.org/plugins/) |
| Monthly active developers | ~100,000+ [ESTIMATE] | [DATA GAP] — no public figure from Automattic |
| WooCommerce-powered stores | 6M+ | (Source: https://woocommerce.com/document/woocommerce-overview/) |

WordPress's dominance creates a monoculture effect: a single vulnerability in a widely-used plugin can simultaneously expose millions of sites. This is the root cause of WordPress's disproportionate share of CMS-related cyberattacks.

### 2.2 The WordPress Attack Landscape

WordPress sites face relentless automated and targeted attacks. The threat landscape has three layers:

**Core vulnerabilities:** WordPress core is maintained by a large, security-aware open-source team. Critical core vulnerabilities are relatively rare but high-impact when discovered.

**Plugin and theme vulnerabilities:** The primary attack vector. The WPScan vulnerability database (Source: https://wpscan.com/vulnerability-database/) tracks thousands of known CVEs across plugins and themes. As of 2024, WPScan listed over 54,000 WordPress-specific vulnerabilities — the overwhelming majority (>97%) in plugins and themes, not core. [DATA GAP — exact current count; verify against https://wpscan.com/]

**Credential and infrastructure attacks:** Brute force, credential stuffing, XML-RPC abuse, and misconfigured hosting environments account for a large share of successful compromises independent of CVE exploitation.

**Key attack statistics:**
- Wordfence blocks over 26 billion attacks per month across its network (Source: https://www.wordfence.com/blog/) [ASSUMPTION — this figure is from c.2023 reporting; current figure may be higher]
- Sucuri reported that 95%+ of CMS-based infected websites in their dataset were WordPress-powered (Source: https://sucuri.net/reports/) [DATA GAP — confirm latest Sucuri annual report year]
- [DATA GAP] — No industry-wide consensus figure for total annual WordPress compromises; estimates range from 30,000 to 90,000 per day across sources

### 2.3 The WordPress Security Plugin Market

The WordPress security plugin market is a mature but innovation-stagnant segment currently dominated by a small number of incumbents.

**Market leaders by active installs (WordPress.org):**

| Plugin | Active Installs | Business Model | Est. ARR |
|---|---|---|---|
| Wordfence Security | 5M+ | Freemium + Premium ($119/yr) | [DATA GAP] |
| Jetpack (security features) | 5M+ | Bundled SaaS ($9.95–$57.95/mo) | Part of Automattic revenue |
| All-In-One Security (AIOS) | 1M+ | Freemium + Premium | [DATA GAP] |
| Sucuri Security | 900,000+ | Freemium + SaaS ($199.99/yr) | [DATA GAP] |
| iThemes Security (now Solid Security) | 900,000+ | Freemium + Pro | [DATA GAP] |
| MalCare Security | 400,000+ | SaaS ($99–$299/yr) | [DATA GAP] |
| WP Cerber | 200,000+ | Freemium + Commercial | [DATA GAP] |

(Source for install counts: https://wordpress.org/plugins/ — individual plugin pages)

**Observations:**
- Wordfence and Jetpack dominate by volume but both are primarily **reactive** tools — they detect and alert, with limited autonomous remediation
- Sucuri and MalCare offer managed remediation but it is human-executed (service model), not autonomous
- No current market entrant offers a genuinely agentic, AI-driven autonomous investigation and remediation loop [ASSUMPTION — based on public feature documentation as of Q1 2026; verify against each competitor's latest release notes]
- The freemium model is universal in this segment, which depresses ARPU but creates enormous top-of-funnel opportunity

---

## 3. TAM / SAM / SOM

### Methodology

This sizing uses a bottom-up approach anchored in known install data, then validated top-down against market research estimates for the broader cybersecurity SaaS segment.

### 3.1 Total Addressable Market (TAM)

**Definition:** All WordPress site owners globally who could conceivably pay for a security plugin.

**Bottom-up calculation:**

| Input | Value | Basis |
|---|---|---|
| Total active WordPress sites | ~500M | [ESTIMATE] — see Section 2.1 |
| Sites with a security plugin installed (any) | ~10–15% [ESTIMATE] | [ASSUMPTION] — based on Wordfence's 5M installs representing ~1% of 500M, extrapolating total security plugin penetration |
| Addressable (willing to pay, has a reason to secure) | ~50M sites [ESTIMATE] | [ASSUMPTION] — WooCommerce stores (6M+), business sites, news/media, membership sites, agencies managing client sites |
| Conservative ARPU for a premium plugin | $84/yr [ESTIMATE] | Midpoint of current market pricing ($59–$299/yr range) |
| **TAM** | **~$4.2B/yr** [ESTIMATE] | 50M × $84 |

**Top-down validation:**
The global web security market was valued at ~$6.1B in 2023 and is projected to reach ~$14B by 2030 at a ~12% CAGR. (Source: https://www.grandviewresearch.com/industry-analysis/web-security-market) [DATA GAP — verify this specific report figure] WordPress-specific tooling conservatively represents 20–30% of the addressable web security market given WordPress's ~43% web share, suggesting a $1.2–$1.8B market at 2023 values — broadly consistent with the bottom-up figure when growth through 2026 is applied.

### 3.2 Serviceable Addressable Market (SAM)

**Definition:** The portion of TAM that ShieldAI can realistically reach given its English-language focus (initial go-to-market), plugin distribution model, and SMB/agency target customer.

| Segment | Sites [ESTIMATE] | ARPU [ESTIMATE] | Segment Value [ESTIMATE] |
|---|---|---|---|
| SMB businesses (English-speaking) | ~8M | $120/yr | $960M |
| WordPress agencies (managing 5–50 sites) | ~200,000 agencies × avg 15 sites | $240/yr per agency | $48M |
| WooCommerce store owners | ~2M addressable | $180/yr | $360M |
| Content/media publishers | ~1M | $84/yr | $84M |
| **SAM Total** | — | — | **~$920M/yr** [ESTIMATE] |

[ASSUMPTION] — English-speaking market approximated at 30–35% of total WordPress installed base based on W3Techs language data.

### 3.3 Serviceable Obtainable Market (SOM)

**Definition:** Realistic revenue capture for ShieldAI across a 3-year horizon.

| Year | Target Market Share of SAM | Implied Sites/Agencies | ARR Target |
|---|---|---|---|
| Year 1 | 0.05% [ESTIMATE] | ~4,600 paying customers | ~$1.5M [ESTIMATE] |
| Year 2 | 0.2% [ESTIMATE] | ~18,000 paying customers | ~$6M [ESTIMATE] |
| Year 3 | 0.5–0.8% [ESTIMATE] | ~46,000–74,000 paying customers | ~$18–28M [ESTIMATE] |

[ASSUMPTION] — These figures assume a freemium distribution model with a 3–5% free-to-paid conversion rate, consistent with WordPress plugin market benchmarks. [DATA GAP — no published free-to-paid conversion benchmarks specific to WordPress security plugins; general SaaS freemium conversion data from OpenView Partners suggests 2–5% is typical.]

**Sensitivity note:** SOM is highly sensitive to (a) whether Wordfence or another incumbent ships a credible AI feature before ShieldAI gains traction, and (b) the pricing model chosen. A $20/mo SaaS model versus a $99/yr perpetual model would compress the site count required to hit ARR targets but may face adoption friction versus current market pricing norms.

---

## 4. Market Trends

### 4.1 AI-Powered Security Tools — Emerging to Mainstream

The broader cybersecurity industry has rapidly adopted AI/ML tooling, with WordPress security lagging by 3–5 years. [ASSUMPTION]

**Industry signals:**
- CrowdStrike, SentinelOne, and Palo Alto Networks have all shipped generative AI features into their core products (2023–2025), establishing "AI-native security" as a category expectation for enterprise buyers
- GitHub Copilot for security (code scanning), Snyk AI, and Socket.dev represent AI-assisted security moving into developer workflows — a proxy for the SMB-facing plugin market
- Google's Security AI Workbench and Microsoft's Security Copilot (launched 2023) signal that major cloud providers are embedding AI reasoning directly into security products (Source: https://cloud.google.com/security/ai, https://www.microsoft.com/en-us/security/business/ai-machine-learning/microsoft-security-copilot)
- The WordPress plugin ecosystem has seen zero mature AI-native security products as of Q1 2026 [ASSUMPTION — based on survey of top 20 security plugins; verify]

**Why this matters for ShieldAI:** WordPress site owners are consumers and SMB operators, not security engineers. AI assistance lowers the expertise barrier more dramatically for this segment than for enterprise buyers who already have SOC teams. The value proposition of "AI does the security work for you" is uniquely powerful in the SMB context.

### 4.2 Accelerating WordPress Attack Volume

Attack volume and sophistication targeting WordPress are on a clear upward trend:

- Automated vulnerability scanners now probe new WordPress CVEs within hours of disclosure (Source: Wordfence Threat Intelligence reports, https://www.wordfence.com/threat-intel/) [DATA GAP — specific citation needed for "hours" claim; verify in Wordfence 2024 annual report]
- The number of new WordPress plugin CVEs added to the WPScan database grew year-over-year in 2022, 2023, and 2024 [ASSUMPTION — direction of trend is industry consensus; specific YoY growth percentages are a DATA GAP]
- AI-generated malware and automated exploit kit generation is reducing the barrier for low-sophistication attackers, increasing the volume of credential stuffing and plugin-exploit attacks targeting SMB sites (Source: Imperva 2024 Bad Bot Report, https://www.imperva.com/resources/resource-library/reports/bad-bot-report/)
- Supply chain attacks on WordPress plugins (malicious code injected into popular plugins via compromised developer accounts) emerged as a significant threat vector in 2024–2025 [ASSUMPTION — based on multiple public incident reports; DATA GAP for quantified frequency]

### 4.3 SMB Security Awareness Is Rising

The SMB segment is experiencing a structural shift in security awareness driven by three factors:

**Insurance requirements:** Cyber insurance providers now routinely require evidence of basic security controls for coverage. For SMBs without internal IT, a security plugin that generates an audit trail and demonstrates active monitoring serves a dual compliance purpose. [ASSUMPTION — based on general cyber insurance industry trends; DATA GAP for WordPress-specific insurance requirements]

**Regulatory pressure:** GDPR enforcement actions involving inadequately secured websites — including WordPress sites — have resulted in fines reaching into the tens of thousands of euros for SMBs. (Source: https://www.enforcementtracker.com/) The EU's NIS2 Directive (effective October 2024) extends cybersecurity obligations to a wider set of organisations. SMBs operating in regulated industries (healthcare, finance, education) are increasingly required to demonstrate security controls. [ASSUMPTION — NIS2 applicability to WordPress-specific tooling needs legal analysis]

**Post-breach awareness:** Small businesses that have experienced a hack are 3–5x more likely to invest in proactive security tooling [ASSUMPTION — no specific WordPress study identified; general SMB security survey data from Hiscox Cyber Readiness Report supports this direction]. This creates a natural re-purchase market among previously breached site owners.

**Cost of inaction:**
- Average cost to remediate a hacked WordPress site through a professional service: $150–$600 (Sucuri, Wordfence Care, Fixhackedwebsite pricing)
- Average cost of downtime for an SMB e-commerce site: $5,000–$50,000/day depending on revenue volume [ESTIMATE] — based on general SMB downtime cost benchmarks from IDC/Gartner; [DATA GAP — WordPress e-commerce specific figures]
- Reputational and SEO damage from blacklisting (Google Safe Browsing, Spamhaus) can cost months of organic traffic recovery [ASSUMPTION]

These figures create a compelling ROI argument: a $20–50/month security plugin pays for itself with a single avoided incident.

### 4.4 Agentic AI — The Infrastructure Is Now Ready

The "agentic" framing — AI that acts autonomously rather than just generating text — became productionally viable in 2024–2025 with the maturation of:

- Function calling and tool use in LLM APIs (OpenAI, Anthropic, Google)
- Smaller, faster, cheaper models suitable for plugin-embedded or serverless inference
- Structured output capabilities enabling reliable parsing of security scan data into actionable decision trees
- Retrieval-augmented generation (RAG) enabling real-time CVE and threat intelligence grounding

This infrastructure did not reliably exist at production quality before 2024. ShieldAI is building on a foundation that was not possible to build on three years ago. [ASSUMPTION — based on general AI capability trajectory; specific model capability milestones are well-documented in public model release notes]

---

## 5. Why Now — Timing Analysis

### 5.1 The Convergence Window

Three forces are converging simultaneously to create an unusually favourable market entry window in 2025–2027:

| Force | Status | ShieldAI Relevance |
|---|---|---|
| AI infrastructure maturity | Ready now | Enables the core product |
| WordPress attack volume | At record levels and growing | Maximises perceived urgency |
| SMB security budget allocation | Growing | Increases willingness to pay |
| Incumbent AI feature development | Not yet shipped | First-mover advantage available |
| Consumer AI literacy | Mainstream | Reduces sales friction |

### 5.2 Incumbent Inertia

The current market leaders face structural reasons to be slow in shipping AI features:

**Wordfence:** Built on a PHP-native, server-side scanning architecture optimised for performance on shared hosting. Retrofitting agentic AI reasoning into this architecture is non-trivial. Their 5M+ user base also creates risk aversion around shipping experimental features. [ASSUMPTION — based on public architecture documentation and plugin codebase analysis]

**Jetpack (Automattic):** Automattic is heavily invested in its own AI roadmap (WordPress.com, WP.com AI tools, Akismet) but Jetpack Security has not historically been a strategic priority relative to publishing and e-commerce features. [ASSUMPTION]

**Sucuri (GoDaddy):** Sucuri was acquired by GoDaddy in 2017. Large-company acquisition typically slows product velocity in this segment. [ASSUMPTION — based on acquisition dynamics; verify against Sucuri's recent feature release cadence]

**iThemes/Solid Security (Liquid Web):** Similarly, iThemes was acquired by Liquid Web. Product velocity has reportedly slowed post-acquisition. [ASSUMPTION — DATA GAP for specific evidence]

### 5.3 The Risk of Waiting

If ShieldAI does not establish a meaningful installed base and brand position by end of 2027:
- Wordfence will likely ship AI features, leveraging its 5M+ existing install base as a distribution moat
- Automattic could embed AI security natively into WordPress.com-hosted sites, reducing the market for third-party plugins in that segment
- Well-funded AI security startups from outside the WordPress ecosystem could enter the plugin market

The window is open but not permanent. A 2025–2026 launch is necessary to establish the category.

---

## 6. Market Risks and Barriers

### 6.1 Distribution Risk — The WordPress.org Plugin Repository

**Risk:** WordPress.org is the dominant plugin distribution channel (it powers the in-dashboard plugin search and installation flow). Plugin approval, continued listing, and search visibility within the repository are controlled by the WordPress.org plugin review team. A plugin that is rejected, suspended, or delisted loses access to its primary acquisition channel.

**Specific considerations:**
- AI features that phone home to external APIs must disclose this in the plugin description
- WordPress.org guidelines prohibit obfuscated code and certain data collection practices
- High-support-thread complaint volumes can affect search ranking within the repository
- A freemium model with upsells is accepted but the free version must be genuinely functional

**Mitigation:** Strict compliance with WordPress.org guidelines from day one. Secondary distribution channels (direct website, agency partnerships, WooCommerce marketplace) should be developed in parallel. [ASSUMPTION — that WordPress.org listing will be sought; confirm this is the go-to-market intent]

### 6.2 Competition Risk — Incumbent Response

**Risk:** Wordfence, with 5M+ installs, could ship an "AI Powered by Wordfence" feature and immediately dominate the AI-native positioning through sheer distribution advantage.

**Probability:** Medium [ESTIMATE] — Wordfence has the engineering resources, brand trust, and install base. The key unknown is whether their architectural choices and organisational priorities create a sufficient lag window.

**Mitigation:** Speed to market; establishing "agentic" as a distinct and demonstrably superior category versus "AI-assisted" scanning. Patent or trade secret protection of core agentic architecture where viable.

### 6.3 Technical Risk — False Positives and Autonomous Action

**Risk:** An agentic plugin that takes autonomous remediation actions (quarantining files, blocking IPs, modifying .htaccess, disabling plugins) creates a non-zero risk of false positives that break legitimate site functionality. A single high-profile incident of ShieldAI breaking a customer's site could generate significant negative press and support burden.

**Mitigation:** Conservative default postures with explicit user confirmation for destructive actions; graduated autonomy settings; robust rollback mechanisms; sandboxed testing before action execution. This is both a product design requirement and a risk management requirement.

### 6.4 Privacy and Data Risk — AI Processing of Site Content

**Risk:** For an agentic AI to investigate a security incident, it may need to process site content, log files, user data, or code. Depending on implementation, this could raise GDPR, CCPA, and other data privacy concerns — particularly if data is transmitted to a third-party AI inference API.

**Specific concerns:**
- Processing EU user data through a US-based AI API without appropriate data processing agreements
- Storing security logs containing IP addresses (personal data under GDPR)
- WooCommerce sites may have order data, customer PII, or payment metadata accessible to the plugin

**Mitigation:** Privacy-by-design architecture. On-device/on-server inference where feasible. Clear data processing agreements. Opt-in for any cloud AI processing. GDPR-compliant data handling documentation.

### 6.5 Pricing and Monetisation Risk

**Risk:** The WordPress plugin market has a strong "free" culture. Users expect free security scanning and may resist a paid agentic tier. Established free options (Wordfence Free, AIOS Free) create strong pricing anchors.

**Mitigation:** The freemium model is effectively mandatory for distribution. The paid tier must offer demonstrably superior outcomes — autonomous remediation, zero-effort management, specific SLAs — that justify premium pricing vs. free alternatives. The ROI narrative (one avoided hack pays for years of subscription) is the key conversion argument.

### 6.6 Shared Hosting Environment Constraints

**Risk:** A significant portion of WordPress sites run on shared hosting environments with:
- PHP memory limits (64–256MB typically)
- Execution time limits (30–60 seconds max)
- Restrictions on outbound HTTP connections
- No access to server-level configuration

An agentic AI plugin that requires substantial compute, long-running processes, or unrestricted network access will not function correctly on shared hosting — which represents a large portion of the TAM.

**Mitigation:** Architecture must be designed for shared hosting constraints from day one. Lightweight plugin footprint; async processing via WordPress cron or background jobs; cloud-offloaded AI inference that does not require long local execution times.

---

## 7. Opportunity Assessment

### 7.1 The Core Opportunity

ShieldAI has the opportunity to define a new product category — **agentic WordPress security** — before any incumbent or well-resourced entrant. The category can be defined as:

> A security product that not only detects and alerts on threats but autonomously investigates incidents, explains findings in plain language, recommends and executes remediation actions, and learns from site-specific patterns over time — requiring zero security expertise from the site owner.

This is distinct from:
- "AI-assisted" scanning (adding ML to existing signature-based scanning — incremental)
- Managed security services (human-executed remediation — expensive, not scalable)
- WAF/CDN-layer protection (infrastructure-level, not plugin-level — different buyer)

### 7.2 Target Customer Segments (Priority Order)

**Segment 1 — WordPress Agencies (Highest Value)**
- Manage 5–50+ client sites
- Security incidents have agency-level reputation consequences, not just client consequences
- Willing to pay per-site or per-agency for tools that reduce support burden
- [ASSUMPTION] ARPU of $200–500/yr per agency; volume potential of 50,000–200,000 agencies globally
- [DATA GAP — no reliable count of WordPress agencies globally; WPMU Dev estimates ~70,000 agencies use their platform]

**Segment 2 — WooCommerce Store Owners**
- Direct revenue at risk from security incidents
- PCI DSS adjacent concerns increase security motivation
- Clear ROI calculation (downtime cost >> plugin cost)
- [ASSUMPTION] ARPU of $150–300/yr; addressable base of 2–4M stores

**Segment 3 — SMB Business Websites**
- Largest by volume, lower ARPU
- Security awareness is growing but price sensitivity is high
- Freemium conversion is the primary path; viral coefficient from agency referrals helps

**Segment 4 — Membership and Content Sites**
- Subscriber data at risk creates motivation
- GDPR exposure drives compliance-motivated purchases
- [DATA GAP — size of this segment]

### 7.3 Competitive Positioning

ShieldAI should position against the current market as follows:

| Dimension | Wordfence | Sucuri | ShieldAI |
|---|---|---|---|
| Detection | Strong | Strong | Strong |
| Investigation | Manual | Manual | Autonomous (AI) |
| Remediation | Manual | Human-managed (paid) | Autonomous (AI) |
| Explanation | Technical logs | Technical reports | Plain-language AI briefings |
| Required expertise | Medium | Low–Medium | Near zero |
| Pricing model | Freemium + $119/yr | Freemium + $199/yr | Freemium + $[TBD]/yr |
| AI-native | No [ASSUMPTION] | No [ASSUMPTION] | Yes |

The differentiation is not in detection capability — multiple incumbents have strong detection. The differentiation is in the **autonomy and accessibility of response**.

### 7.4 Revenue Model Recommendation

Based on market pricing benchmarks and customer segment analysis:

| Tier | Price | Features | Target Segment |
|---|---|---|---|
| Free | $0 | Scanning, alerting, basic hardening | All (acquisition) |
| Solo | $9/mo (~$99/yr) | Agentic investigation + guided remediation | SMB single site |
| Pro | $19/mo (~$199/yr) | Full autonomous remediation + AI briefings | WooCommerce, content sites |
| Agency | $49/mo (~$499/yr) | Multi-site dashboard, white-label reports, priority support | Agencies (up to 15 sites) |
| Agency+  | $99/mo (~$999/yr) | Unlimited sites under management | Large agencies |

[ASSUMPTION] — These price points are benchmarked against Wordfence Premium ($119/yr), Sucuri ($199.99/yr), and MalCare ($99–$299/yr). They reflect a modest premium for AI-native capability.

### 7.5 Key Success Metrics to Track

| Metric | Why It Matters |
|---|---|
| Free-to-paid conversion rate | Core monetisation health; target 3–5% [ESTIMATE] |
| Time-to-first-detection (TTFD) | Product quality signal |
| False positive rate | Risk management; must be <0.5% for autonomous actions [ASSUMPTION] |
| NPS from paid customers | Category-definition relies on word-of-mouth |
| Churn rate | Security plugins should have low churn; target <8%/yr [ESTIMATE] |
| Agency site-under-management growth | Proxy for agency channel effectiveness |
| WordPress.org review rating | Search visibility and social proof |

### 7.6 Summary Scoring

| Dimension | Score (1–5) | Notes |
|---|---|---|
| Market size | 4 | $4B+ TAM; large but competitive |
| Timing | 5 | Convergence window is open now |
| Competitive intensity | 3 | Incumbents are large but slow; window is real but finite |
| Technical feasibility | 4 | Infrastructure ready; shared hosting constraints are real but manageable |
| Customer willingness to pay | 3 | Free culture is a headwind; ROI case is strong |
| Distribution accessibility | 4 | WordPress.org is open; plugin ecosystem is accessible |
| Team/execution risk | [DATA GAP] | Not assessed in this document |
| **Overall Opportunity** | **4 / 5** [ESTIMATE] | Strong market timing; strong differentiation potential; execution is the key variable |

---

## Data Gaps Summary

The following data points would materially improve this analysis. Research priority is indicated.

| Data Gap | Priority | Suggested Source |
|---|---|---|
| Wordfence, Sucuri, MalCare actual ARR | High | Crunchbase, LinkedIn revenue estimates, founder interviews |
| WordPress agency global count | High | WPMU Dev, Cloudways agency surveys, WooExperts directory |
| Free-to-paid conversion benchmarks for WordPress security plugins | High | Direct competitor interviews, OpenView SaaS benchmarks |
| Total annual count of WordPress site compromises | Medium | Sucuri annual report, Wordfence annual report, Cloudflare data |
| WPScan CVE count year-over-year growth rate | Medium | WPScan API / database exports |
| NIS2 / GDPR applicability to WordPress plugin data processing | Medium | Legal analysis required |
| Shared hosting market share among WordPress sites | Medium | Kinsta, WP Engine, SiteGround published stats |
| SMB cyber insurance requirements referencing CMS security tools | Low | Hiscox, Coalition, Cowbell cyber insurance policy documents |

---

*This document was prepared for internal strategic planning purposes. All estimates and assumptions should be validated prior to use in investor materials or public communications. Data marked [DATA GAP] represents areas where further primary research is recommended before finalising market sizing figures.*
