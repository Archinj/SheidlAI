# ShieldAI — User Journeys

---

## Overview

Five key journeys mapped across ShieldAI's three primary personas. Each journey shows user steps, system behavior, emotional state, friction points, and delight moments.

**Personas:**
- Maya — solo blogger, non-technical
- David — WooCommerce store owner, medium-tech
- Sarah — WordPress freelancer, 12 client sites

**Emotional state legend:** 😨 Anxious | 😤 Frustrated | 😐 Neutral | 🤔 Curious | 😊 Satisfied | 🎉 Delighted

---

## Journey 1: First Install (Maya, Day 1)

**Trigger:** Maya got a Wordfence email about a "critical vulnerability" she didn't understand. She searches "wordpress security plugin that explains alerts."

### Steps

| # | User Action | System Response | Emotion | Notes |
|---|-------------|-----------------|---------|-------|
| 1 | Finds ShieldAI on WordPress.org. Reads description: "explains threats in plain English." | Plugin page loads with screenshots of the approval queue UI. | 🤔 | Copy "explains threats in plain English" is the hook. This must be on the plugin page. |
| 2 | Installs and activates the free tier. | Welcome screen: "ShieldAI is scanning your site now. This takes about 2 minutes." | 😐 | First impression matters. Don't dump her into a blank dashboard. |
| 3 | Sees the dashboard for the first time. | Dashboard shows: scan status, site health score, and 1 finding flagged (the plugin Wordfence mentioned). | 🤔 | If first scan shows nothing, she'll wonder if it's working. First scan must find something real. |
| 4 | Clicks on the flagged item. | Expanded view: "This plugin has a known security flaw (CVE-2024-XXXX). A hacker could use it to gain access to your site." Followed by: "**Recommended Fix:** Update to version 3.4.2. This update patches the flaw." | 😊 | **DELIGHT MOMENT**: This is the first time she's understood what a security alert actually means. |
| 5 | Sees "Approve" button is locked behind upgrade. | "Unlock fix execution with Shield plan ($79/year). Your recommendation is ready and waiting." | 😤 | Friction point: she understands the fix but can't apply it. This is intentional conversion pressure but must not feel like a bait-and-switch. |
| 6 | Either upgrades or notes what she needs to do. | If upgrade: payment flow → confirmation → "Approve" button unlocks. | 😊 or 😤 | Goal: upgrade within 7 days of first detection. |

**User Story:** As a non-technical blogger, I want to understand what a security alert means in plain English, so that I know whether I need to act and what action to take.

**Friction to eliminate:** The gap between "I understand the problem" and "I can fix it" must be as short as possible. The upgrade CTA must appear naturally within the detection detail view.

---

## Journey 2: First Queue Action — Approve and Execute

**Trigger:** David logs in Monday morning. ThreatResponseAgent detected 23 failed login attempts from a single IP over the weekend. There's a new item in the queue.

### Steps

| # | User Action | System Response | Emotion | Notes |
|---|-------------|-----------------|---------|-------|
| 1 | Sees "1 New Recommendation" badge on ShieldAI menu. | Dashboard shows a "critical" severity badge on the queue item. Red pulse dot indicating urgency. | 😨 | The red badge works — it creates appropriate urgency without being alarmist. |
| 2 | Clicks to open the queue. | Item expanded: **Title:** "Block IP engaging in brute force attack." **Description:** "IP 198.51.100.22 made 23 failed login attempts in 4 hours — a pattern consistent with automated credential stuffing. Blocking this IP via your firewall will stop the attack." | 😨→🤔 | Plain English matters. "Credential stuffing" may need a tooltip for non-technical users. |
| 3 | Scrolls to see the diff. | **Before:** `.htaccess` shown in its current state. **After:** New `deny from 198.51.100.22` rule highlighted in green. | 🤔 | Diff must be simple enough to skim. David doesn't read code — he reads intent. |
| 4 | Sees confidence score: 94% and LLM reasoning. | "Why did ShieldAI suggest this? 23 failed attempts in 4 hours from one IP is 115x the normal rate. No successful logins from this IP. Recommend blocking." | 😊 | **DELIGHT MOMENT**: The reasoning transparency builds trust. "The AI is showing its work." |
| 5 | Clicks "Approve." | Confirmation modal: "This will add a firewall rule to block IP 198.51.100.22. ShieldAI will save a snapshot first so you can undo this." **[Cancel] [Confirm Approval]** | 😊 | The rollback mention in the confirmation modal is a key trust signal. |
| 6 | Clicks "Confirm Approval." | Success notice: "Rule applied. IP blocked. Snapshot saved — you can roll back this change at any time from the action history." | 🎉 | **DELIGHT MOMENT**: "I did something. The threat is handled. I'm still in control." |
| 7 | Sees action logged in audit trail. | Audit log entry: "Approved by David (admin) on April 9, 2026 at 9:14am. Executed successfully." | 😊 | Documentation of the decision creates confidence and paper trail. |

**User Story:** As a WooCommerce store owner, I want to understand why a security fix is recommended before I approve it, so that I feel confident approving changes to my live store.

**Friction to eliminate:** The confirmation step before execution must be present but not annoying. One modal, clear language, rollback reminder.

---

## Journey 3: Rollback After a Problem

**Trigger:** Sarah approved a header change (X-Frame-Options: DENY) for a client site. The client calls — their embedded checkout widget is broken. Sarah needs to undo it.

### Steps

| # | User Action | System Response | Emotion | Notes |
|---|-------------|-----------------|---------|-------|
| 1 | Client calls, reports broken widget. Sarah logs into ShieldAI. | — | 😨😤 | High stress. Every minute the client is affected is professional reputation damage. |
| 2 | Navigates to the action that was executed (header change from yesterday). | Action detail shows: executed status, timestamp, executor used, snapshot saved. **[Rollback]** button visible. | 😐→😊 | **RELIEF MOMENT**: The rollback button exists and is easy to find. This is the product delivering on its promise. |
| 3 | Clicks Rollback. | Confirmation: "This will restore the previous header configuration. The X-Frame-Options rule will be removed. This action will be logged." **[Cancel] [Confirm Rollback]** | 😐 | Simple, clear. No jargon. |
| 4 | Confirms rollback. | Success: "Header configuration restored to state from April 8, 2026 at 2:14pm. Action logged." | 😊 | Client widget works again. |
| 5 | Calls client back within 5 minutes of the original call. | Audit log now shows both the original action and the rollback, with timestamps. | 😊🎉 | Sarah can say "I fixed it in 4 minutes and I have the full audit trail." |
| 6 | Queue item re-appears as "pending" with a note: "Previously executed. Rolled back. Review before re-approving." | — | 🤔 | The item stays in the queue so Sarah can make a more informed decision the next time. |

**User Story:** As a freelancer managing client sites, I want to be able to undo any approved change quickly and completely, so that I can fix mistakes without client downtime.

**DELIGHT MOMENT:** The whole rollback flow takes under 3 minutes. Sarah's professional reputation is intact.

**Friction to eliminate:** Rollback must be reachable in under 3 clicks from the main dashboard. "Rollback" should be visible on executed actions — not buried in a settings menu.

---

## Journey 4: Weekly Vulnerability Scan (David)

**Trigger:** VulnScanAgent runs Sunday 2am. David logs in Monday morning.

### Steps

| # | User Action | System Response | Emotion | Notes |
|---|-------------|-----------------|---------|-------|
| 1 | Logs into WordPress admin. | ShieldAI badge: "2 new recommendations from weekly scan." | 😨 | Anticipation of bad news. But "recommendations" is less scary than "threats detected." |
| 2 | Opens queue. Sees two items: one "high" severity, one "medium." | High: "Plugin X v2.1.0 has a known RCE vulnerability (CVE-2024-XXXX, CVSS 9.8). Update to 2.2.0 immediately." Medium: "Plugin Y has no patch available yet. Consider deactivating." | 😨→🤔 | CVSS score shown gives David a sense of relative severity without requiring him to know what CVSS is. |
| 3 | Opens high severity item. Sees full description, CVE link, and diff showing version change. | Before: `plugin-x 2.1.0` → After: `plugin-x 2.2.0`. Note: "ShieldAI will run the update using WordPress's built-in update system." | 🤔 | Link to the CVE page is important for technical users who want to verify. |
| 4 | Clicks Approve on the high severity update. | Update runs. Success notice. Snapshot saved. | 😊 | |
| 5 | Opens medium severity item (no patch available). | Description: "No update available yet. Until the developer releases a fix, deactivating this plugin removes the attack surface." Three options: **[Deactivate Plugin]** **[Dismiss — I'll monitor]** **[Remind me in 7 days]** | 🤔 | Multiple options for the "no easy fix" case is important. Not everything has a one-click solution. |
| 6 | Clicks "Remind me in 7 days." | Item snoozed. Will reappear next scan with updated vulnerability status. | 😊 | Snooze is a power move — respects David's decision-making authority. |

**User Story:** As a WooCommerce owner, I want to review plugin vulnerabilities on my own schedule and choose how to respond to each one, so that I stay informed without being forced into actions I'm not ready for.

---

## Journey 5: Agency Multi-Site Management (Sarah)

**Trigger:** Sarah does her weekly security review of all 12 client sites. She opens ShieldAI's Agency dashboard.

### Steps

| # | User Action | System Response | Emotion | Notes |
|---|-------------|-----------------|---------|-------|
| 1 | Opens ShieldAI Agency dashboard (master view). | Sees 12 sites listed with their current status: 3 sites have pending queue items, 9 are clear. Sorted by severity. | 😐 | **DELIGHT MOMENT**: Seeing all sites in one view instead of logging into 12 separate WP admins. |
| 2 | Clicks on first site with pending items (2 items, 1 critical). | Queue expands showing both items for that site. | 😨 | High-visibility critical item demands attention first. |
| 3 | Reviews and approves the critical item (plugin update for a client's WooCommerce store). | Executes. Success. Audit log entry: "Approved by Sarah Okafor (agency admin) on behalf of [Client Site]." | 😊 | Agency audit log shows actions by Sarah on behalf of specific client sites. |
| 4 | Dismisses the second item (low priority hardening suggestion the client has previously declined). | Item dismissed. Note saved: "Dismissed — client has chosen to keep current configuration." | 😐 | Dismiss with note = documentation that the client was informed and chose not to act. |
| 5 | Moves to next site with pending items. Processes remaining queue items. Total time: ~15 minutes for all 12 sites. | — | 😊 | 15 minutes vs. 2+ hours logging into each site individually. |
| 6 | Exports monthly security report for Client A. | Report generated: "April 2026 Security Report for [Client Site]. 3 vulnerabilities detected, 3 fixed. 0 incidents. Current hardening score: 87/100." | 🎉 | **DELIGHT MOMENT**: This is a client-facing deliverable Sarah can include in her monthly retainer invoice. It demonstrates the value of her service. |

**User Story:** As a WordPress freelancer managing multiple client sites, I want to review and act on security recommendations across all sites from a single dashboard, so that I can provide consistent, documented security management without site-hopping.

**Friction to eliminate:** Agency dashboard must not require individual site logins. Cross-site action approval must work seamlessly. Audit logs must clearly distinguish which client site an action was taken on.
