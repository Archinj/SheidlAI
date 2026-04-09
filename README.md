# ShieldAI

**An agentic WordPress security plugin that monitors your site, uses AI to draft specific fixes, and asks for your approval before doing anything.**

> "Wordfence tells you there's a problem. ShieldAI drafts the fix."

---

## What Is ShieldAI?

ShieldAI sits inside your WordPress admin. It runs four AI agents in the background — checking for attacks, scanning plugins for vulnerabilities, auditing your security settings, and generating incident reports. When something is found, instead of sending a confusing alert, it uses Claude AI to write the exact fix in plain English and puts it in an **approval queue**.

You read the explanation. You see a before/after diff of exactly what will change. You click **Approve** or **Dismiss**. Nothing touches your live site until you say so. Every approved action can be rolled back in one click.

```
Monitor → Detect → AI Drafts Fix → Approval Queue → You Approve → Executes → Rollback Available
```

---

## The Four Agents

| Agent | Runs | What It Does |
|-------|------|--------------|
| **ThreatResponseAgent** | Every 15 min | Detects brute force attacks and core file changes. Drafts firewall rules. |
| **VulnScanAgent** | Weekly (Sunday 2am) | Scans all installed plugins against the WPScan CVE database. Flags vulnerable ones. |
| **HardeningAgent** | Monthly (1st of month) | Audits 40 security settings — debug mode, file permissions, XML-RPC, security headers. |
| **IncidentReportAgent** | After any critical fix | Generates a structured incident report: attack timeline, likely vector, recommended follow-up. |

---

## Who Is It For?

**Solo bloggers and content creators** who get scary security alert emails and don't know what to do with them. ShieldAI explains what the threat is and what the fix is — in plain English, not code.

**WooCommerce store owners** who can't afford a security incident destroying customer trust. ShieldAI scans every installed plugin weekly for known vulnerabilities and has a specific update queued before attackers exploit it.

**WordPress freelancers and agencies** managing 10-20 client sites. The Agency plan covers 20 sites for $399/year. One approval queue across all sites. Audit logs you can put in a client report.

---

## Pricing

| Plan | Price | Who It's For |
|------|-------|--------------|
| Free | $0 | See recommendations — but can't execute them |
| Shield | $79/year | All 4 agents, full approval queue, executors, rollback |
| Shield Pro | $199/year | + Incident reports, extended audit log |
| Agency | $399/year | Up to 20 sites, 1-year audit log |

---

## Key Design Decisions

**Approval before action.** Nothing executes automatically. Ever. The AI drafts the fix. You approve it.

**Rollback everything.** Before any fix runs, ShieldAI saves a snapshot of the current state. You can undo any approved action in one click.

**No PII leaves the site.** Only plugin slugs, file hashes, CVE IDs, and anonymized patterns are sent externally. No customer emails, names, or order data.

**LLM output is schema-validated.** The AI response is checked against a strict schema before it reaches any executor. Raw AI text never becomes a system action.

**Nginx-safe.** On Nginx hosts, `.htaccess` executor actions are skipped and you see a notice to apply the rule manually.

---

## Tech Stack

| Layer | Choice |
|-------|--------|
| Language | PHP 8.1+, OOP, PSR-4, WPCS |
| WordPress minimum | 6.0 |
| Scheduling | WP-Cron (with notice to set up real cron on low-traffic sites) |
| LLM | Claude API (primary), OpenAI GPT-4o (fallback) |
| CVE data | WPScan API + NVD JSON feed as fallback |
| Admin UI | PHP-rendered WP admin pages + vanilla JS |

---

## Market Position

The WordPress security plugin market has a clear gap: every major tool (Wordfence, Sucuri, Solid Security, MalCare) is good at **detecting** threats. None of them **generate a specific fix and ask for approval**. ShieldAI occupies this position exclusively.

Wordfence has 5M+ active installs. That is the addressable market. When a Wordfence user gets an alert they don't understand and can't act on, ShieldAI is the answer.

---

## Conservative Year 1 Targets

- 4,000 free installs (WordPress.org organic)
- 120 paying customers
- ~$13,500 ARR
- Primary channel: WordPress.org directory + content SEO

---

## Important Limitation (WP-Cron)

All four agents use WP-Cron for scheduling. WP-Cron only fires when someone visits the site — so on low-traffic sites, the 15-minute threat check might run hours late. ShieldAI ships with a notice in the admin panel instructing paid users to set up a real server cron. Managed hosts (Kinsta, WP Engine, Cloudways) handle this automatically.

The long-term fix is a hybrid SaaS platform (Phase 2) that pings each site on a guaranteed schedule regardless of traffic.

---

## Research Documents

Full research is in the `/research` folder. Each document links to the detailed analysis behind the decisions above.

| Document | What's Inside |
|----------|---------------|
| [Market Analysis](research/MARKET_ANALYSIS.md) | TAM/SAM/SOM, market size, trends, timing ("why now?") |
| [User Personas](research/USER_PERSONAS.md) | Maya (blogger), David (WooCommerce), Sarah (agency) — full profiles, pain points, WTP |
| [Interview Guide](research/CUSTOMER_INTERVIEWS/INTERVIEW_GUIDE.md) | Behavioral research questions for customer discovery interviews |
| [Interview Synthesis](research/CUSTOMER_INTERVIEWS/INTERVIEW_SYNTHESIS.md) | Hypothetical synthesis of 5 user profiles ⚠️ UNVALIDATED — replace with real interviews |
| [Competitive Analysis](research/COMPETITIVE_ANALYSIS.md) | Wordfence, Sucuri, Solid Security, AIOS, MalCare — feature matrix and gaps |
| [Customer Discovery Journey](research/CUSTOMER_DISCOVERY_JOURNEY.md) | How site owners find, evaluate, and decide on security plugins |
| [Value Proposition](research/VALUE_PROPOSITION.md) | Positioning statement, elevator pitches, objection handlers |
| [Product Vision](research/PRODUCT_VISION.md) | Vision, principles, 3-phase roadmap (Plugin → SaaS → Platform) |
| [Business Model](research/BUSINESS_MODEL.md) | Pricing strategy, unit economics, financial projections, risks |
| [User Journeys](research/USER_JOURNEYS.md) | 5 journeys mapped: first install, queue approval, rollback, vuln scan, agency dashboard |
| [MVP Definition](research/MVP_DEFINITION.md) | MVP scope, what's out of scope, kill criteria, launch gates |
| [Marketing Plan](research/MARKETING_PLAN.md) | 90-day launch plan, channel strategy, budget (~$5.5K Year 1) |

---

## Before Building

Two things to validate before committing to the full MVP build:

1. **Run 5-10 real customer interviews** using the [Interview Guide](research/CUSTOMER_INTERVIEWS/INTERVIEW_GUIDE.md). The current synthesis is hypothetical.
2. **Prototype-test the approval queue UI** with non-technical users. The concept works on paper — confirm it works in a clickable prototype before writing code.

---

## Related Documents

- [Plugin Specification](../ShieldAI%20Plugin%20Spec.md) — the technical spec an AI can code from
- [Technical Documentation](../ShieldAI%20Technical%20Documentation.md) — plugin vs. SaaS architecture decision
- [Landing Page](index.html) — the public-facing product page (deployed on GitHub Pages)
