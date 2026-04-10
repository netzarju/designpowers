# Renter Profile — Design Strategy
**Agent:** design-strategist
**Date:** 2026-04-10
**Status:** Post-discovery, ready for design-lead

---

## Brief

Design a renter profile page for Zillow's mobile app that serves two simultaneous jobs: (1) a portable, landlord-facing credential that eliminates per-application document uploads, and (2) a personal document vault the renter manages over time. The core problem is effort and repetition — renters upload the same documents to every landlord, every platform, every application.

The strategic opportunity is larger than the UI: Zillow can own the portable renter identity standard. The profile becomes the renter's credential that travels with them across listings. That is the platform bet, and it should be named explicitly in any stakeholder framing.

---

## Personas

### Primary: The Qualified Renter Who Hates the Process

**Who they are:** A renter who knows they're financially qualified — stable income, reasonable credit, rental history — but finds the application process degrading and repetitive. They're not anxious about their qualifications; they're exhausted by having to prove them over and over.

**Their job:** Get through applications faster with less friction, without feeling like they're starting from zero every time.

**What breaks for them today:** Every new listing, every new platform, every new landlord asks for the same pay stub. They've uploaded it five times this month. They've stopped applying to some listings just because the process felt like too much work.

**Ability spectrum notes:** Includes renters who are neurodivergent and find repetitive administrative tasks especially draining. Includes renters with motor impairments for whom each upload is a meaningful effort.

---

### Secondary: The Non-Standard Renter

Three sub-segments Zillow knows exist but doesn't serve well yet:

**Self-employed renter** — No pay stub. Has bank statements, tax returns, or client contracts as income proof. The current document model doesn't accommodate them cleanly, so their profile looks incomplete even when they're financially strong.

**New-to-US renter** — No US credit history. May have strong financial history in another country, savings, or a co-signer. The profile has no way to surface this context, so they look like a blank slate.

**Renter with a co-signer** — Partially supported in the application flow but not in the profile. The co-signer relationship and their documents have no clear home.

**Design implication for all three:** The profile must accommodate income verification that isn't a pay stub, and it must have a way to add context — a short renter statement or an explanation field — so non-standard profiles can tell their own story rather than just showing gaps.

**Note on eviction history:** This is the hardest case — Zillow must balance landlord information needs with fair housing obligations. This persona is not fully in scope for this design but must not be made worse. Any disclosure mechanism must be reviewed by legal before it ships.

---

## Design Principles

### 1. Upload once, share selectively
The profile is a vault, not a form. Every document a renter uploads lives permanently in their profile and can be shared with any landlord without re-uploading. Sharing is an action, not a re-submission.

**In practice:** Sending your profile to a new landlord takes one tap. You never upload the same document twice.
**Rules out:** Any flow where the renter is asked to provide information Zillow already has.
**How to test:** A renter who has completed their profile can share it with a new landlord in under 30 seconds, with zero uploads.

---

### 2. Progressive trust, not all-or-nothing
Renters share lightweight profile information upfront (name, income tier, credit tier, rental history summary) and unlock full document access only when they're seriously interested in a specific listing. Landlords get enough signal to shortlist; renters retain control over sensitive documents until trust is established.

**In practice:** A renter browsing a listing sees a "Share profile" option. Tapping it shares a summary. Full documents (pay stubs, ID, credit report) are unlocked by the renter as a second step, with a clear explanation of what they're sharing and with whom.
**Rules out:** All-or-nothing profile sharing. Automatic document release on profile share.
**How to test:** A renter can share their summary with 10 landlords and their full documents with only 2, with full visibility into who has access to what.

---

### 3. Gaps are guidance, not judgment
An incomplete profile should feel like a helpful prompt, not a warning. Non-standard renters (self-employed, new to US) must never feel like their profile is broken — it should surface what's there, explain what would strengthen it, and offer alternatives where standard documents don't apply.

**In practice:** Instead of "Income verification: missing," show "Add proof of income — pay stub, bank statement, or tax return accepted." A self-employed renter sees the same prompt as a salaried renter; only the document options differ.
**Rules out:** Red states, warning icons, or language that implies the renter is unqualified. Percentage-complete meters that punish non-standard renters.
**How to test:** A self-employed renter and a salaried renter both feel their profile is complete when they've added what they have.

---

### 4. Visibility and control are the same action
Renters need to see exactly who has access to their profile and documents at all times, and revoking access must be as easy as granting it. Transparency about sharing is not a settings screen — it's part of the core profile experience.

**In practice:** The profile shows a persistent "Shared with" section — a list of landlords who have access, what they can see, and when access was granted. Revoking is one tap.
**Rules out:** Sharing flows with no confirmation. Access that can't be revoked. Documents shared without the renter knowing what was included.
**How to test:** A renter can identify every landlord with access to their documents within 10 seconds, without navigating to a settings screen.

---

## Information Architecture

### Screen Map

```
Renter Profile
├── Profile Header (identity layer)
│   ├── Name, photo
│   ├── Renter summary (income tier, credit tier, rental history — text, no raw numbers)
│   └── "Share profile" CTA
│
├── Document Vault (utility layer)
│   ├── Income verification
│   │   ├── Pay stub (primary)
│   │   ├── Bank statement (alternative)
│   │   ├── Tax return (alternative)
│   │   └── [Add document]
│   ├── Identity
│   │   └── Government ID
│   ├── Credit
│   │   └── Credit report (Zillow-generated)
│   └── Supporting documents
│       ├── Employment letter
│       ├── References
│       └── Renter statement (free-form context field)
│
├── Sharing & Access (trust layer)
│   ├── Active shares — landlords with current access + what they see
│   ├── Share history
│   └── Revoke access
│
└── Application History
    ├── Active applications
    └── Past applications
```

### Navigation Model

The profile is a self-contained destination, not a tab within the application flow. It is accessible from:
- The renter's main nav (persistent)
- A listing page ("Share your profile with this landlord")
- An application in progress ("Your documents are ready — share your profile")

The profile does not live inside an active application. It precedes and outlives applications.

---

## User Flows

### Flow 1: First-Time Profile Setup

```
Entry: Renter lands on empty profile (post-onboarding or from listing CTA)
↓
Step 1: Identity — name, photo (optional), basic rental preferences
↓
Step 2: Income — upload pay stub OR select alternative (self-employed, other)
  → If self-employed: prompted to upload bank statement or tax return
  → If new to US: prompted to add renter statement + co-signer option
↓
Step 3: Credit — authorize Zillow credit check (soft pull)
↓
Step 4: Identity verification — upload government ID
↓
Profile complete — shown summary of what landlords will see
↓
CTA: "Share with a landlord" or "Save and exit"
```

**Error path — income verification fails or is ambiguous:**
Renter is not blocked. Profile is saved with what exists. A contextual prompt surfaces the gap inline: "Add a second proof of income to strengthen your profile."

**Ability spectrum notes:**
- Every upload step must support camera capture and file picker equally
- No time limits on document review steps
- Screen reader: form fields labeled with purpose, not just type ("Government ID" not "Upload document")

---

### Flow 2: Sharing a Profile with a Landlord

```
Entry: Renter taps "Share profile" from listing or profile screen
↓
Confirmation screen — shows exactly what will be shared (summary vs. full documents)
  → Default: summary only (name, income tier, credit tier, rental history)
  → Optional: "Also share full documents" toggle
↓
Renter confirms
↓
Landlord receives notification with access link
↓
Renter sees landlord added to "Shared with" list in profile
↓
Renter can revoke at any time from that list
```

**Edge case — renter shares full documents, then changes mind:**
Revoke access from "Shared with" list. Landlord loses access immediately. Renter sees confirmation.

**Open question (unresolved):** Does the landlord get notified when access is revoked? Legal and product need to weigh in — this has implications for landlord trust and fair housing.

---

### Flow 3: Returning Renter Updates a Document

```
Entry: Renter opens profile → Document Vault
↓
Taps document to replace (e.g., pay stub expired)
↓
Upload new version
↓
System asks: "Update everywhere this is shared?"
  → Yes: all active shares updated automatically
  → No: new version saved but not pushed to existing shares
↓
Done — no re-submission to individual landlords required
```

---

## Trade-offs Documented

| Decision | What was chosen | What was given up |
|----------|----------------|-------------------|
| Progressive sharing (summary first, documents on demand) | Renter control and trust-building | Landlord gets less signal upfront — some landlords may prefer all-or-nothing |
| Accommodating non-standard income documents | Inclusive profile for self-employed/new-to-US renters | More complex document validation and review logic |
| Profile lives outside the application flow | Profile is reusable and portable | Harder to drive profile completion if renters don't have a standalone reason to build it |
| Renter statement (free-form field) | Non-standard renters can add context | Some landlords will ignore it; some renters may write things that create legal exposure |
| Revocable access | Renter trust and control | Landlords can't rely on documents being permanently accessible |

---

## Proposed Success Metrics

*These are not finalized — product and finance need to align. Surfacing them here to force the conversation.*

**Primary (platform bet):**
- % of renters who complete a profile (defined as: identity + income + credit check)
- Application rate among renters with complete profiles vs. incomplete profiles
- 90-day return rate to Zillow for renters with complete profiles

**Secondary (landlord-side):**
- Time-to-first-contact after profile share (proxy for landlord engagement)
- Landlord-reported satisfaction with renter info quality

**What to watch for:** If complete-profile renters apply more but don't convert to leases at a higher rate, the platform bet may be generating activity without business value. Track downstream, not just top-of-funnel.

---

## Open Questions

1. **Metric alignment:** Product and finance have not aligned on whether success is renter-side (activation, return rate) or landlord-side (conversion, time-to-lease). This needs resolution before design can be fully validated.
2. **Landlord notification on revoke:** Does a landlord get notified when a renter revokes document access? Legal input required.
3. **Eviction history disclosure:** How does Zillow handle eviction history in the profile without violating fair housing obligations? Legal input required before this appears in any design.
4. **Co-signer profile integration:** Co-signer documents and identity are partially supported in the application flow. Does the co-signer get their own profile, or are their documents attached to the primary renter's profile?
5. **Profile portability beyond Zillow:** The strategic bet implies the profile should eventually work across platforms. Is that on the roadmap? It changes how the data model and sharing infrastructure should be built.

---

## Handoff to design-lead

> **design-strategist → design-lead:** "The core problem is effort and repetition — the renter who has uploaded the same pay stub five times this month. The platform opportunity is portable renter identity: upload once, share selectively. Four principles guide the work: upload once / share selectively, progressive trust, gaps as guidance not judgment, and visibility = control. The IA splits into three layers — identity (profile header), utility (document vault), and trust (sharing & access). Non-standard renters (self-employed, new to US) must be first-class, not edge cases. The progressive sharing model is the most important UX decision — design it so summary sharing feels natural and full document sharing feels deliberate. Mobile, 375px wide. Over to you."
