# Design State: Property Search Results Page

_Last updated: 2026-04-08 by design-strategist_

## Brief
- **Problem:** Information overload — users can't quickly identify which properties are worth exploring
- **Primary persona:** Home buyers and renters (first-time and experienced)
- **Success metric:** Users identify a "worth exploring" property within 3 seconds of scanning
- **Brief document:** docs/designpowers/briefs/2026-04-08-property-search-results.md

## Personas
[Full personas](docs/designpowers/personas/2026-04-08-property-search-personas.md)
- Maya Chen — First-time buyer, mobile in sunlight, ESL, 3-second scan window
- Robert Williams — Experienced renter, colorblind (deuteranopia), keyboard-only navigation
- Aisha Mohammed — Single mother, low literacy, data-constrained phone, financial stress
- David Park — Blind, expert screen reader user, relocating under time pressure

## Design Principles
1. **Three seconds to signal** — every card communicates "worth exploring or not" within 3 seconds
2. **Accessibility is not negotiable** — WCAG 2.1 AA minimum, 48px touch targets, load-more not infinite scroll
3. **Information hierarchy beats information density** — whitespace and clarity over cramming
4. **Surface time pressure, not urgency theater** — days on market, price history, factual badges; no dark patterns

## Taste Profile
- **Emotional target:** Trustworthy, fast, respectful of time
- **Quality level:** Production
- **Key references:** Zillow (data-heavy), Redfin (clean but impersonal)
- **Aesthetic principles:** _Pending full taste calibration_
- **Taste document:** _Not yet created_

## Decisions Log

| Date | Agent | Decision | Rationale |
|------|-------|----------|-----------|
| 2026-04-08 | design-discovery | Card-based results with progressive disclosure | Enables 3-second scan; reduces cognitive load |
| 2026-04-08 | design-discovery | Mobile-first responsive web | Primary use case is mobile browsing during commutes |
| 2026-04-08 | design-discovery | WCAG 2.1 AA minimum | User-mandated accessibility priority |
| 2026-04-08 | design-scout | Load-more button on mobile, pagination on desktop | Infinite scroll fails screen reader testing; load-more is accessible alternative |
| 2026-04-08 | design-scout | Touch targets 48x48px minimum | Industry average 40-44px fails WCAG; this is a differentiation opportunity |
| 2026-04-08 | design-scout | Days on market on cards | High-value info underutilized by competitors; aids urgency assessment |
| 2026-04-08 | design-scout | No broker branding on cards | Competes with property info; move to detail page |
| 2026-04-08 | design-scout | Price per sqft on cards | Helps comparison shopping; newer platforms include this |
| 2026-04-08 | design-strategist | Card hierarchy: photo → price → beds/baths/sqft → days on market | User-specified; serves 3-second scan principle |
| 2026-04-08 | design-strategist | Status badges on photo as high-contrast overlays (max 3) | User direction: surface "price reduced" and "new listing" prominently |
| 2026-04-08 | design-strategist | 4 inclusive personas: Maya, Robert, Aisha, David | Cover speed, accessibility, stress, and compliance testing |
| 2026-04-08 | design-strategist | 4 design principles | Three seconds to signal, accessibility non-negotiable, hierarchy > density, time pressure not urgency theater |

## Open Questions

- [x] Pagination vs infinite scroll vs virtual scroll? → Load-more mobile, pagination desktop
- [x] How to differentiate from Zillow/Redfin? → Accessibility-first, time-respecting, honest status info
- [x] Final information hierarchy on card → photo → price → beds/baths/sqft → days on market → address → price/sqft → CTA
- [ ] Typography scale and color system with WCAG 2.1 AA baked in
- [ ] Save/favorite interaction pattern
- [ ] Color palette that feels trustworthy and warm (not sterile like Redfin)

## Artefact Index

| Artefact | Path | Status |
|----------|------|--------|
| Brief | docs/designpowers/briefs/2026-04-08-property-search-results.md | Approved |
| Competitive Analysis | docs/designpowers/research/2026-04-08-property-search-competitive-analysis.md | Complete |
| Personas | docs/designpowers/personas/2026-04-08-property-search-personas.md | Complete |
| Strategy | docs/designpowers/strategy/2026-04-08-property-search-strategy.md | Complete |

## Design Debt Register
_Items: 0 | Critical: 0 | Oldest: —_

| ID | Date | Source | Severity | What | Who is affected | Suggested fix | Status | Notes |
|----|------|--------|----------|------|----------------|---------------|--------|-------|

## Handoff Chain

_Pipeline started in DIRECT mode._

### 2026-04-08 design-discovery → design-scout
> "We're designing a property search results page — the core problem is information overload. Users need to scan and decide 'worth a tap' in under 3 seconds. Zillow and Redfin are the benchmarks — Zillow is too data-heavy, Redfin is clean but impersonal. Look at what's working in this space, what's broken, and especially where the accessibility gaps are."

### 2026-04-08 design-scout → design-strategist
> "The industry is failing at accessibility across the board — touch targets too small, contrast failures on badges, screen reader experiences barely functional, infinite scroll breaking keyboard nav. This is our differentiation. Information hierarchy beats density every time — Redfin proves whitespace wins. Load-more on mobile, pagination on desktop, virtual scroll for performance. Days on market is high-value data everyone buries. No broker branding on cards. Your move: nail the information architecture priority stack and the interaction model."

**User direction:** Card hierarchy: photo → price → beds/baths/sqft → days on market. Surface "price reduced" and "new listing" prominently.

### 2026-04-08 design-strategist → design-lead
> "Four personas, four principles, card hierarchy locked. Maya is your speed test (3 seconds in sunlight), Robert is your accessibility test (colorblind + keyboard), Aisha is your stress test (low literacy, financial pressure), David is your compliance canary (blind, screen reader). Status badges must be colorblind-safe — text + icons, not color-only. Touch targets 48px minimum. Days on market is non-negotiable. Typography scale: price 24px mobile/28px desktop, metadata 16px, secondary 14px. Whitespace is strategic. Go make it beautiful — and make it work for everyone."
