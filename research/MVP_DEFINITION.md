# ShieldAI — MVP Definition

---

## 1. MVP Scope (Must Have)

The MVP must prove one thing: that a non-technical WordPress site owner can receive an AI-generated security fix recommendation, understand it, approve it, and see it execute without breaking their site.

Everything in the MVP exists to validate this core loop.

### Core Loop (Non-Negotiable)

- **ThreatResponseAgent** — brute force detection via login failure tracking. This is the fastest to demonstrate value (results within 15 minutes of a real attack). Core file integrity check is a bonus but secondary.
- **Approval queue UI** — the full queue page with severity badges, plain-English descriptions, before/after diffs, confidence score, and Approve/Dismiss controls.
- **HtaccessExecutor** — the only executor needed for MVP. Firewall rules via .htaccess cover the ThreatResponse output. Simple, low-risk to users.
- **RollbackManager** — snapshot before execution, one-click restore. Non-negotiable. Without rollback, no one will approve anything.
- **Audit log** — basic event logging (agent run, approved, executed, dismissed, rolled_back). Required for trust.
- **LLMClient** — Claude API integration with schema validation. No raw LLM output ever reaches an executor.
- **Free tier + Shield tier** — Free: show the recommendation, lock the Approve button. Shield ($79/year): full execution.
- **License key validation** — simple remote check on activation and weekly.
- **Email notification on critical severity** — one email to admin when a critical action is queued.

### Secondary (v1.0 Launch — Before WordPress.org)

- **VulnScanAgent** — CVE scanning is a strong second agent. Add before launch; don't wait for v1.1.
- **PluginUpdateExecutor** — required for VulnScanAgent to be useful beyond just detection.
- **Settings page** — API key entry, notification email, tier display.
- **Nginx detection** — detect Apache vs. Nginx. Show manual notice on Nginx instead of running HtaccessExecutor blindly.

---

## 2. Explicitly Out of Scope for MVP

The following are explicitly NOT in the MVP. They are planned for future versions. Saying no now is how the MVP stays shippable.

**Not in MVP:**
- HardeningAgent (monthly audit) — valuable but not the proof-of-concept hook
- IncidentReportAgent — requires Shield Pro tier; out of scope for v1.0
- HeaderExecutor — adds complexity, not required for ThreatResponse or VulnScan
- Multi-site / Agency dashboard — Phase 1.5 or Phase 2
- OpenAI GPT-4o fallback — Claude-only for MVP; add fallback in v1.1
- Custom action editing before approval (the "Edit" button in the spec) — Approve or Dismiss is sufficient for MVP
- WP-Cron to real-cron migration helper — document it, don't automate it for MVP
- Managed host auto-detection for cron coverage — add in v1.1
- API key encryption upgrade (beyond basic openssl_encrypt) — current spec is acceptable for launch
- WordPress multisite network support — out of scope entirely for Phase 1

---

## 3. Launch Criteria

The following must be true before submitting to WordPress.org:

**Functional:**
- [ ] ThreatResponseAgent detects real brute force attacks (tested against WP installations with simulated attacks)
- [ ] VulnScanAgent returns accurate CVE data for at least 5 test plugins with known vulnerabilities
- [ ] Approval queue renders correctly in Chrome, Firefox, Safari on desktop and mobile
- [ ] HtaccessExecutor applies and rolls back rules correctly on Apache hosts
- [ ] PluginUpdateExecutor updates a plugin and rolls back the version correctly
- [ ] LLM response schema validation rejects malformed responses (tested with intentionally bad prompts)
- [ ] Free tier correctly blocks execution — Approve button is locked, not just hidden
- [ ] License validation works on activation and fails gracefully when offline

**Security:**
- [ ] All AJAX endpoints verify nonce and check `manage_options` capability
- [ ] API key is encrypted at rest, never logged or exposed in the admin UI
- [ ] No PII (IPs only after anonymization, no customer emails/names) sent to LLM

**Code quality:**
- [ ] PHP 8.1+ compatible, no deprecation warnings
- [ ] WPCS standards pass (WordPress Coding Standards)
- [ ] PSR-4 autoloading in place
- [ ] No direct database queries outside `$wpdb` — no raw SQL string concatenation

**Documentation:**
- [ ] README.txt for WordPress.org written (description, installation, FAQ, screenshots)
- [ ] WP-Cron limitation documented in admin notice and FAQ

---

## 4. Success / Validation Criteria (First 90 Days)

These metrics determine whether the MVP is working. Measure from first WordPress.org listing.

**Install and activation:**
- Target: 500 active installs by Day 90 [ESTIMATE — conservative for unproven brand]
- Activation rate from install: >60% (people who install and activate within 7 days)

**Core loop validation:**
- At least 50 queue items generated across all installs (proves agents are detecting real threats)
- Approve rate on generated queue items: >30% (proves users trust the recommendations enough to act)
- Rollback rate: <5% of approved actions (proves executed fixes don't break sites)
- Zero critical failures (no instance of an execution that couldn't be rolled back)

**Conversion:**
- Free-to-paid upgrade rate: >2% within 90 days
- Target: 10 paying Shield customers by Day 90

**User feedback:**
- At least 5 WordPress.org reviews with 4+ stars
- No 1-star reviews citing "broke my site" or "false positives destroyed my trust"

---

## 5. Kill Criteria

These signals indicate the MVP assumption is wrong and a pivot is needed.

**Kill signal 1 — Approve rate below 10%**
If fewer than 10% of generated queue items are approved within 7 days of appearing, users don't trust the AI recommendations. This means the explanation quality is failing, the confidence scores aren't credible, or the approval queue model itself is wrong.

**Kill signal 2 — Rollback rate above 15%**
If more than 15% of approved fixes require rollback, the executor quality is too low for users to trust. This would invalidate the core "approve and it's safe" promise.

**Kill signal 3 — Zero paid conversions after 500 free installs**
If no one upgrades after 500 installs, the free-to-paid funnel is broken. Either the free tier shows too little value, the price point is wrong, or the problem we're solving isn't painful enough to pay for.

**Kill signal 4 — Consistent site breakage reports**
More than 3 reports of site breakage caused by ShieldAI in the first 90 days, without successful rollback, would be reputation-fatal on WordPress.org.

---

## 6. MVP Timeline Estimate

This is a rough milestone plan. Not a sprint schedule — just the major gates.

**Gate 1 — Core plugin architecture complete**
PSR-4 autoloading, database tables created on activation, LLMClient integrated and returning validated responses, basic admin menu registered.

**Gate 2 — ThreatResponseAgent + HtaccessExecutor + RollbackManager working**
End-to-end: simulate brute force → agent fires → LLM returns recommendation → queue item created → admin approves → .htaccess rule applied → snapshot saved → rollback tested.

**Gate 3 — VulnScanAgent + PluginUpdateExecutor working**
CVE lookup returns real data for installed plugins → queue item created with CVSS score → admin approves → plugin update executes via WordPress update API → snapshot saved.

**Gate 4 — Free vs. Paid feature gating working**
License validation endpoint live → free tier shows recommendations but blocks Approve → Shield plan unlocks execution → test upgrade flow end-to-end.

**Gate 5 — QA and Hardening**
WPCS review, security review (nonce/capability checks on every endpoint), PHP 8.1 compatibility check, test on Apache and confirm Nginx notice appears correctly.

**Gate 6 — WordPress.org submission**
README.txt, screenshots, plugin header complete. Submit. Wait for review (typically 1-4 weeks).
