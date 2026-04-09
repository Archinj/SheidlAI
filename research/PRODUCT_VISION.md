# ShieldAI — Product Vision

---

## 1. Vision Statement

A world where any WordPress site owner — regardless of technical skill — can run a secure site, because an AI handles the complexity of security response and a human handles the decisions.

---

## 2. Mission Statement

ShieldAI monitors WordPress sites for security threats, uses AI to generate specific, actionable fixes, and presents those fixes in a human approval queue. We make enterprise-grade security response accessible to the 800 million sites that can't afford a security team.

---

## 3. Product Principles

**Approval before action.** Nothing changes on a live site without a human click. Autonomy is a feature we earn over time through trust — it is not the starting point.

**Explain, don't just detect.** Every alert comes with a plain-English explanation. We never leave site owners with a notification they don't understand. "Critical threat detected" is not a complete sentence.

**Undo everything.** Every action that ShieldAI executes must be reversible. Before executing any fix, we save a snapshot. The presence of a rollback option makes people willing to approve changes they'd otherwise be afraid of.

**No PII leaves the site.** We send CVE hashes, plugin slugs, file checksums, and anonymized patterns to external APIs — never customer names, emails, order data, or any personally identifiable information.

**LLM output is never trusted directly.** AI-generated fixes are schema-validated before they reach an executor. If the response doesn't match the expected structure, it is discarded. Raw LLM text never becomes a system action.

**Grow with the user's confidence.** A new user approves their first fix cautiously. A year in, they trust the system and approve quickly. The product should reward that growing trust with increasing capability — not a static tool.

**The approval queue is a dataset.** Every approve/dismiss decision is a signal. Over time, this becomes a proprietary training dataset that improves fix recommendations for every user. First movers accumulate this advantage — late entrants cannot recreate it.

---

## 4. North Star Metric

**Fixes approved and successfully executed per active paid site per month.**

This metric captures what matters most: that the product is detecting real threats, generating fixes users trust enough to approve, and executing those fixes without breaking anything. A site with ShieldAI installed but no fixes executed isn't being protected — it's just being monitored. The North Star tracks actual remediation, not just presence.

Secondary metrics:
- Time from threat detection to fix approval (speed of the loop)
- Rollback rate (a high rollback rate signals fix quality problems)
- Free-to-paid upgrade rate

---

## 5. Strategic Phases

### Phase 1 — Plugin (0 to 18 months)

**What we build:** A pure WordPress plugin. All four agents (ThreatResponseAgent, VulnScanAgent, HardeningAgent, IncidentReportAgent), the approval queue UI, all three executors (htaccess, plugin update, header), rollback system, and audit log. Scheduled via WP-Cron.

**Why:** Get to market fast, validate the approval-first concept with real users, and generate the first batch of approve/dismiss data. No infrastructure complexity — just a plugin and a licensing endpoint.

**Key milestones:**
- WordPress.org listing live with free tier
- First 1,000 active installs
- First 100 paying customers
- First approve/dismiss dataset (50+ decisions per agent type)

**What unlocks Phase 2:** Paying customers asking for guaranteed scheduling (WP-Cron limitation hits them), request for multi-site management, and validation that the approval queue concept resonates.

---

### Phase 2 — Hybrid SaaS (18 to 36 months)

**What we build:** An external SaaS platform that pings each connected site on a guaranteed schedule, regardless of site traffic. A central dashboard where site owners (and agencies) manage multiple sites. The platform tracks exactly when each agent last ran and fires the next one on time.

**Why:** Phase 1's WP-Cron dependency is a real limitation — a brute force attack at 3am on a quiet site goes undetected until morning. The SaaS platform removes this. It also enables the Agency plan to work properly with a single management interface.

**Key milestones:**
- External pinging infrastructure live for all paid subscribers
- Multi-site dashboard with cross-site approval queue
- Approve/dismiss dataset large enough to begin model fine-tuning experiments
- MRR crosses threshold where SaaS infrastructure cost is justified

**What unlocks Phase 3:** A critical mass of approve/dismiss data (50K+ decisions), demand from developers to build integrations, and an opportunity to sell threat intelligence to other security vendors.

---

### Phase 3 — Platform (36+ months)

**What we build:** A multi-tenant platform with an API, a developer ecosystem, and potentially a threat intelligence product built on the accumulated approve/dismiss dataset. ShieldAI becomes the security layer that other WordPress products integrate with.

**Why:** At scale, the approve/dismiss data is a unique asset. A recommendation engine trained on how real site owners respond to real security threats is something no competitor can replicate without years of data collection. The platform layer monetizes this as a B2B product.

**Key milestones:** [DATA GAP — Phase 3 strategy depends heavily on Phase 1/2 learnings]

---

## 6. 12-Month Roadmap

**Q1 (Months 1-3): Foundation**
- Core plugin architecture (PSR-4, WPCS, PHP 8.1)
- ThreatResponseAgent + HardeningAgent (highest-value for early users)
- Approval queue UI with approve/dismiss/rollback
- Free tier + Shield plan ($79/year) at launch
- WordPress.org submission

**Q2 (Months 4-6): Complete the Agents**
- VulnScanAgent (WPScan API + NVD fallback)
- IncidentReportAgent
- Shield Pro tier ($199/year) launch
- First 500 active installs target

**Q3 (Months 7-9): Agency and Retention**
- Agency plan ($399/year, 20 sites) — multi-site architecture
- Audit log page with extended retention
- Email notifications for critical severity actions
- First community feedback loop (customer interviews with real users)

**Q4 (Months 10-12): Quality and Growth**
- Fix quality improvements based on real approve/dismiss data
- WPBeginner / Kinsta review outreach
- YouTube tutorial production
- First annual renewal cohort analysis

---

## 7. Strategic Assumptions and Bets

**We're betting that:** Non-technical users want control, not automation. The "approve before execute" model will resonate more than auto-fix tools because people are afraid of things changing on their sites without their knowledge.

**We're betting that:** The market will pay a premium for comprehensibility. Explaining what's wrong in plain English is more valuable than a longer feature list.

**We're betting that:** The approval queue data compounds into a real moat. At 10K+ sites, the pattern of what gets approved vs. dismissed becomes a training signal that improves ShieldAI faster than any competitor can manually replicate.

**We're betting that:** WP-Cron is acceptable in Phase 1 if we're transparent about it. Site owners on managed hosts (Kinsta, WP Engine, Cloudways) already have external cron handled. The limitation hits low-traffic sites on cheap shared hosting — and we document it clearly.

**We must be wrong about:** The assumption that users will read fix explanations before approving. If approval fatigue sets in and people start clicking Approve without reading, the safety model breaks down. We need to track this and design against it.

**Key risk:** Wordfence or Sucuri adds AI-generated fix suggestions in the next 12-18 months. Our moat is the approval queue UX and the accumulating dataset — but this is a real competitive threat that would neutralize our primary differentiator.
