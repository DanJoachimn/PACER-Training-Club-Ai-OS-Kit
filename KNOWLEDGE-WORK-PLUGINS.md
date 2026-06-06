# Knowledge Work Plugins — the upstream backbone

> PACER installs and references a public Anthropic-maintained plugin marketplace. This file documents what's installed for HTC operators, what's optional, and how updates flow.

---

## What this is

`anthropics/knowledge-work-plugins` is a public marketplace of role-specific plugins (sales, customer support, finance, marketing, productivity, brand voice, and more) built and maintained by Anthropic. Each plugin is plain markdown + a small manifest — no code, no infrastructure, no build steps. They install via Claude Code's standard plugin system and update from upstream.

PACER stands on top of this marketplace. A curated subset of plugins installs during kick-off, then PACER's HTC-specific wrappers layer HYROX context on top — gym brand voice, member CRM, qualifying questions, race calendar, coach roster.

| | |
|---|---|
| **Upstream repo** | https://github.com/anthropics/knowledge-work-plugins |
| **Marketplace name** | `knowledge-work-plugins` |
| **License** | Per upstream — see the LICENSE in the marketplace repo |
| **Maintainer** | Anthropic |

---

## What PACER installs by default

Seven plugins cover the universal small-business operations that PACER layers HTC context on top of. They install during Stage 0.5 of `INSTALL-PART-2.md`.

| Plugin | What it does | HTC use case |
|---|---|---|
| **sales** | Prospect, call-prep, pipeline, outreach drafting | **Speed-to-Lead #1.** Lead intake, trial booking, qualifying questions, PFT follow-up. |
| **customer-support** | Triage tickets, draft responses, escalation, KB articles | **Knowledge Base #7** + day-to-day member support. FAQ handling, complaint triage, member churn-risk responses. |
| **marketing** | Content drafting, campaign planning, brand voice consistency, performance reporting | **Social Content #6** + **Post-Race Re-Engagement #5**. Race promo, member spotlights, weekly content batch. |
| **finance** | Reconciliation, statements, variance, month-end close | **Dunning #4.** Failed payment chase, member billing, monthly close, COGS tracking. |
| **productivity** | Tasks, calendars, daily workflows | Owner's daily ops. Class schedule, coach roster, vendor follow-ups. |
| **enterprise-search** | One query across email, chat, docs, wikis | Find anything across Wodify, email, Slack, the vault. |
| **brand-voice** *(Tribe AI, partner-built)* | Extracts gym voice from existing writing, generates guidelines, validates output | **Powers PACER's brand-voice extraction phase** during kick-off. Production-grade. |

---

## Optional add-ons

These are NOT auto-installed. PACER knows they exist and can install on request — say *"add the legal plugin"* or *"install data"* and PACER runs the install.

| Plugin | When you'd want it |
|---|---|
| **legal** | Coach contracts, GDPR compliance, member agreements, NDA triage. Useful as the gym scales past 100 members. |
| **data** | Wodify data exports + SQL/dashboard analysis. For operators who want to slice retention/attendance/revenue beyond what Wodify's built-in reports show. |
| **cowork-plugin-management** | Power-user only. Lets you build custom plugins specific to your gym (e.g., your own race-prep flow, your own membership tier rules). |

The full marketplace includes plugins for product-management, engineering, design, HR, bio-research — none of those fit HTC, so PACER doesn't surface them. You can install them manually if your situation calls for it.

---

## How updates work

When the gym owner runs `/update`, PACER's update flow:

1. Pulls the latest version of the PACER kit from GitHub (the usual)
2. Pulls the latest version of the underlying personal kit (`Partner-Ai-Kit-Personal`)
3. **Also runs** `claude plugin marketplace update knowledge-work-plugins`
4. Reports any installed plugins that have new versions
5. Surfaces any NEW plugins added to upstream since the last update
6. Asks if the owner wants to install any of them — never silent

You stay on the plugin versions you have until you say "update." No silent upstream rolls.

---

## Install / remove individual plugins (manual)

```bash
# One-time: add the marketplace (PACER does this during Stage 0.5)
claude plugin marketplace add anthropics/knowledge-work-plugins

# Install a specific plugin
claude plugin install [plugin-name]@knowledge-work-plugins

# Remove
claude plugin remove [plugin-name]@knowledge-work-plugins

# List everything installed
claude plugin list

# Pull upstream updates manually
claude plugin marketplace update knowledge-work-plugins
```

---

## Why "wrap, don't fork"

PACER deliberately does NOT copy Anthropic's plugin source into the repo. Instead:

- The plugins install fresh from upstream on first run
- They update automatically through Claude Code's standard plugin system
- Anthropic maintains the heavy lifting. PACER adds the HTC sauce on top.

If Anthropic ships a better `sales` plugin tomorrow, every PACER install gets it for free. If PACER forked, the maintainer (Dani) would carry the burden forever.

This is the kepano pattern — stand on the shoulders, add the vertical.

---

## What PACER adds ON TOP of the upstream plugins

The plugins above handle the UNIVERSAL versions of these workflows. PACER's `training-club-overlay/skills/` adds HTC-specific wrappers that pre-load the gym's context before delegating to the underlying plugin skill.

Examples of how the layering works:

| Upstream plugin skill | PACER wrapper | What the wrapper adds |
|---|---|---|
| `/sales:call-prep` (generic) | `pacer-lead-triage` | HYROX qualifying questions, member-fit scoring, Wodify trial-booking deeplink |
| `/customer-support:triage` (generic) | `pacer-member-support` | Gym's KB, race-calendar context, escalation rules for at-risk members |
| `/marketing:draft` (generic) | `pacer-content` | Brand voice doc, race-prep angles, social cadence rules |
| `/finance:dunning` (generic) | `pacer-dunning` | Wodify failed-payment context, member tenure, save-the-relationship script |

PACER's own skills are the **vertical layer.** The plugins are the **horizontal layer.** Together they cover both.

---

## If something goes wrong

- **A plugin install fails during Stage 0.5** → PACER logs it, marks Stage 0.5 incomplete, continues with the rest of Part 2. Re-run anytime with "redo Stage 0.5" or "install the missing plugins."
- **An upstream plugin has a regression** → roll back with `claude plugin install [name]@knowledge-work-plugins@<previous-version>` (if version-pinning is available in your Claude Code version) OR remove + reinstall.
- **A PACER wrapper references a plugin the owner removed** → wrapper errors gracefully and surfaces "this plugin is needed — want to reinstall?" rather than crashing.

---

*Plugin awareness layer — read by PACER on session start so it knows which upstream skills it can delegate to. Updated 2026-06-06.*
