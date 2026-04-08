# Design State: Property Search Results Page

_Last updated: 2026-04-08 by design-scout_

## Brief
- **Problem:** Information overload — users can't quickly identify which properties are worth exploring
- **Primary persona:** Home buyers and renters (first-time and experienced)
- **Success metric:** Users identify a "worth exploring" property within 3 seconds of scanning
- **Brief document:** docs/designpowers/briefs/2026-04-08-property-search-results.md

## Personas
_Pending — inclusive-personas not yet run_

## Design Principles
_Pending — design-strategist not yet run_

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

## Open Questions

- [x] Pagination vs infinite scroll vs virtual scroll? → Load-more mobile, pagination desktop
- [x] How to differentiate from Zillow/Redfin? → Accessibility-first, time-respecting, honest status info
- [ ] Final information hierarchy on card — strategist to confirm Priority 1/2/3 items
- [ ] Typography scale and color system with WCAG 2.1 AA baked in
- [ ] Save/favorite interaction pattern

## Artefact Index

| Artefact | Path | Status |
|----------|------|--------|
| Brief | docs/designpowers/briefs/2026-04-08-property-search-results.md | Approved |
| Competitive Analysis | docs/designpowers/research/2026-04-08-property-search-competitive-analysis.md | Complete |

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
