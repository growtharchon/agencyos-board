# AgencyOS — Ownership Audit: Gaps & Overlaps

**Scope:** all 60 functions on the AgencyOS Functions & Ownership map.
**Method:** every function checked for (a) a single accountable DRI and (b) clean boundaries with adjacent functions.
**Source caveat:** built from Fathom meeting *summaries* (Jun 24 – Jul 7 2026), not verbatim transcripts — treat owner/support assignments as a working draft to confirm.
**Date:** 2026-07-08

---

## Headline

| Check | Result |
|---|---|
| Functions with exactly one DRI | 56 / 60 |
| **Gaps** — no accountable owner | **3** (+1 unseated) |
| **Overlaps** — shared / unclear ownership | **8** flagged |
| DRI concentration risk | **Kas = 22 of 60 (37%)** — single point of failure |
| People with no assigned function | **0** (Paulene Cortez = Daniel Ops — resolved) |

**Bottom line:** the single-DRI model is *mostly* clean — the real exposure is (1) a handful of unowned high-risk functions, (2) an over-concentrated founder, and (3) a set of adjacent functions whose boundaries aren't drawn, especially around **dashboards/data**, **the website-delivery chain**, and **client communication**.

---

## A. Gaps — functions with no DRI

These are live functions nobody is accountable for. Assigning one owner each is the fastest risk reduction on the map.

| # | Function | Domain | Why it matters | Recommended DRI | Support |
|---|---|---|---|---|---|
| G1 | **Go-live / redirect process** | Delivery | *Highest-stated delivery risk.* 301/302 mapping, URL preservation, tracking, hosting, reindex — a botched launch tanks a client's SEO overnight. Currently done ad-hoc per project. | **Leo** (it's the tail of his zero-to-live workflow) | Rehan (deploy/hosting), Darko (redirects/reindex) |
| G2 | **Billing ops / payouts / revenue-share** | Finance | Vendor/VA payouts, client billing, revenue-share accounting — money moving with no operational owner. Kas holds finance *strategy* but not the day-to-day. | **Daniel (Ops)** (operational) | Kas (consulted on revenue-share economics) |
| G3 | **Approval-capture SOP / change log** | Client Success | The control that prevents "you never approved that" disputes with clients. Introduced in meetings, never assigned. Adjacent to change-request intake you already own. | **Daniel (Ops)** (owns intake/PRDs) | Rehan (system) |
| G4 | **Legal / compliance / contracts / NDAs** | Finance | Sits with Jack but flagged **not firmly seated**. NDAs and third-party liability (e.g. hosting outages) protect high-value client data — can't be half-owned. | **Confirm Jack** as DRI, or route to external counsel | Kas |

---

## B. Overlaps — shared or unclear ownership

Places where two+ people touch the same territory, a function is co-owned (violating single-DRI), or a boundary isn't drawn.

### O1 — Dashboards & reporting: three owners, unclear boundary  ⚠️ *highest overlap risk*
Three separate "dashboard" functions across two people, plus the data layer under a third:
- **Client Dashboard** (client-facing filtered view) — **Kas**, support Rehan
- **Client dashboards & data pipelines** (build + Scraper-API→BigQuery) — **Rehan**
- **Reporting reconciliation / dashboards** (fix client-vs-agency metric mismatches) — **Rehan**
- **Data module (BigQuery + reports)** — **Leo**

**Risk:** unclear who owns the client-facing dashboard end to end vs. the pipeline feeding it; the recent client conversion-count discrepancy is exactly this seam failing.
**Recommendation:** Rehan = DRI for the **data + reporting engine**; Kas (or Daniel Ops) = DRI for the **client-facing dashboard/experience**; Leo = DRI for **data architecture** only. Write the handoff line between them.

### O2 — Website-delivery chain: split across 3, with a hole
- **Astro website build** — **Mostafa**
- **Zero-to-live website workflow** (the repeatable process) — **Leo**
- **Go-live / redirect** — **nobody** (see G1)
- QA/skeptic — **Rehan**

**Risk:** no single DRI for "this client's site, start to finish." The Astro-build duplicated-work incident in the transcripts came from exactly this.
**Recommendation:** name a **per-project delivery DRI** (default Mostafa or Leo) accountable for the whole chain including go-live; keep the others as support.

### O3 — Internal-ops governance is genuinely co-owned  ⚠️ *single-DRI violation*
"Internal-ops whip governance" is currently DRI **Leo**, support **Daniel (Ops)** — but the transcripts describe it as **jointly owned by Leo and Daniel**. Co-ownership is the exact thing the DRI rule forbids.
**Recommendation:** pick one DRI (recommend **Daniel (Ops)** since you run PM cadence and IDS), Leo as support — or split it into two functions with clean edges.

### O4 — Client communication: operational vs. strategic boundary
- **Client communication & updates** + **change-request intake** — **Daniel (Ops)**
- **Retention / expansion** (strategic account leadership) — **Kas**
- Jack runs comms for **his own client book**

**Risk:** who "owns the client relationship" is ambiguous — operational updates (you) vs. strategic relationship (Kas/Jack per account). Clients can get mixed signals.
**Recommendation:** define it as **Daniel (Ops) owns the communication *system & cadence*; the account DRI (Kas or Jack) owns the *relationship & strategic messaging*.** State it explicitly.

### O5 — Data / BigQuery: architecture vs. pipelines
**Leo** owns data *architecture* + the agent stack; **Rehan** owns the *pipelines* (Scraper-API→BigQuery). Overlapping surface on the same stack.
**Recommendation:** likely fine as arch-vs-build, but write the boundary so a new data task has an obvious home.

### O6 — Onboarding & client access: three touchpoints
- **Client onboarding + access spec** — **Leo**
- **Centralized client access** (ops@ backend) — **Rehan**
- **Client Dashboard → onboarding module** — **Kas**

**Risk:** onboarding a client touches all three; no single owner of "the onboarding experience."
**Recommendation:** Leo = DRI for the onboarding *process*; Rehan = DRI for *access provisioning* as a support step within it.

### O7 — Cold email: overlap resolved, keep it enforced
Transcripts explicitly flagged **Kas's team and Jack's team duplicating cold-email effort**; resolved by consolidating under **Vovik / Kas's team**. Also appears in two domains (Sales + Delivery) under Vovik.
**Recommendation:** no action beyond making sure Jack's side stays out — this is a resolved overlap worth keeping an eye on.

### O8 — "Email" means three different things
- **Klaviyo / email & retention flows** (client lifecycle) — Jack
- **Cold email** (outbound) — Vovik
- **Meeting & Email templates** (internal) — Daniel (Ops)

**Risk:** low — distinct functions, but the shared word "email" invites confusion in tasking.
**Recommendation:** keep the qualifiers ("client lifecycle", "outbound", "internal templates") in every reference.

---

## C. Structural findings

### S1 — Founder concentration (Kas = 22/60, 37%)  ⚠️
Kas is DRI on the entire Platform product, all of Finance, most of Sales, and key Client-Success functions. This is a **single point of failure** and the stated reason the internal-ops "whip" governance exists.
**Recommendation:** targeted offload — move **Finance ops (G2)** and **1–2 Platform modules** to Leo/Rehan/Daniel (Ops); keep Kas on commercial strategy + product vision. A redistribution draft is a good next deliverable.

### S2 — Two people named Daniel + alias sprawl (data-integrity risk)
**Daniel (Ads)** = Google Ads only. **Daniel (Ops)** = internal ops/PM/client comms — and the *same person* appears across the sources under several names: **Seselovsky, Sese / Cese ("Sassy Cese"), and Paulene Cortez**. The Fathom summaries treated these as different people.
**Recommendation:** collapse all of those aliases to one identity (Daniel Ops) in Plane/task tooling, and keep Daniel (Ads) strictly separate, so new work is attributed correctly.

### S3 — ~~Person with no function~~ (resolved)
Earlier flagged **Paulene Cortez** as an unassigned attendee — this was wrong: **Paulene Cortez is Daniel Ops** (see S2). No unassigned people remain.

---

## Priority actions

1. **Assign DRIs to G1–G3** and confirm G4 (legal) — closes the only true single-DRI violations.
2. **Draw the boundary lines for O1 (dashboards) and O2 (website delivery)** — the two overlaps most likely to cause dropped work.
3. **Resolve O3** — pick one DRI for internal-ops governance.
4. **Draft a Kas redistribution (S1)** — reduce the 37% concentration.
5. **Enforce the identity mapping in tooling (S2)** — collapse Seselovsky / Sese / Cese / Paulene Cortez to Daniel Ops; keep Daniel Ads separate.
