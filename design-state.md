# Design State: Property Search Results Page

_Last updated: 2026-04-08 by content-writer_

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
- **Aesthetic principles:** Clean enough to scan, warm enough to feel human; ocean blue + terracotta palette
- **Taste document:** docs/designpowers/design/2026-04-08-property-search-visual-spec.md

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
| 2026-04-08 | design-lead | Ocean blue (#2B6CB0) + terracotta (#E07A3D) palette | Warm and trustworthy; terracotta for price gives warmth without sterility |
| 2026-04-08 | design-lead | System font stack (no web fonts) | Performance priority; faster LCP on mobile |
| 2026-04-08 | design-lead | 8px base spacing unit, 16px card padding | Consistent rhythm, generous whitespace for scannability |
| 2026-04-08 | design-lead | Status badges: icon + text on white overlay | Colorblind-safe; Robert can read without color distinction |
| 2026-04-08 | design-lead | 48px circular save button on photo top-right | Meets touch target minimum; expected position from competitor research |
| 2026-04-08 | design-lead | 16:9 photo aspect ratio at 50% card height | Balances engagement and info density per scout findings |
| 2026-04-08 | content-writer | "home" not "property" or "listing" | "Property" feels clinical; "home" is warm, Grade 2 reading level |
| 2026-04-08 | content-writer | Full prices ($425,000) not abbreviated ($425K) | Builds trust; Aisha needs unambiguous numbers |
| 2026-04-08 | content-writer | "Listed X days ago" for days on market | Conversational, Grade 3, warmer than "X days on market" |
| 2026-04-08 | content-writer | Grade 4-6 reading level target | Serves Aisha (low literacy) and Maya (ESL) |

## Open Questions

- [x] Pagination vs infinite scroll vs virtual scroll? → Load-more mobile, pagination desktop
- [x] How to differentiate from Zillow/Redfin? → Accessibility-first, time-respecting, honest status info
- [x] Final information hierarchy on card → photo → price → beds/baths/sqft → days on market → address → price/sqft → CTA
- [x] Typography scale and color system → system fonts, ocean blue + terracotta, full scale defined
- [x] Save/favorite interaction pattern → 48px circular button, heart icon, top-right of photo
- [x] Color palette → warm ocean blue + terracotta, all contrast ratios documented
- [x] Content-writer copy → all strings final, Grade 4-6, "home" vocabulary
- [ ] Motion specs for card interactions (hover, save, load-more) — skipping for this pipeline
- [ ] Build the page (design-builder)

## Artefact Index

| Artefact | Path | Status |
|----------|------|--------|
| Brief | docs/designpowers/briefs/2026-04-08-property-search-results.md | Approved |
| Competitive Analysis | docs/designpowers/research/2026-04-08-property-search-competitive-analysis.md | Complete |
| Personas | docs/designpowers/personas/2026-04-08-property-search-personas.md | Complete |
| Strategy | docs/designpowers/strategy/2026-04-08-property-search-strategy.md | Complete |
| Visual Spec | docs/designpowers/design/2026-04-08-property-search-visual-spec.md | Complete |
| Copy Doc | docs/designpowers/content/2026-04-08-property-search-copy.md | Complete |

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

### 2026-04-08 design-lead → content-writer
> "Cards have tight space constraints. Price label: none needed, it's obvious. Beds/baths format: '3 bd / 2 ba / 1,450 sqft'. Status badges: 'New', 'Price Reduced', 'Open House' — keep it short, no articles. Load-more button text needed. Empty state copy needed. Address format: street + neighborhood, no city/state (that's in the search context). Write for Aisha — Grade 4 reading level, no jargon."

### 2026-04-08 design-lead → design-builder
> "Full visual spec at docs/designpowers/design/2026-04-08-property-search-visual-spec.md. Ocean blue + terracotta palette, system fonts, 8px grid. Cards are 16:9 photo at 50%, price in terracotta at 24px, beds/baths with icons, days on market gets its own line. Status badges overlay photo top-left with white semi-transparent background. Save button is 48px circle top-right. One tab stop per card. Load-more button, not infinite scroll. Build mobile-first. Wait for content-writer's copy before implementing labels."

### 2026-04-08 content-writer → design-builder
> "All strings are final in the copy doc. Full prices ($425,000 not $425K). 'Show more homes' for load-more. 'Save this home' for screen reader on heart button. Days on market: 'Listed today' / 'Listed 5 days ago' / 'Listed 2 months ago'. Use 'home' not 'property' everywhere. Dynamic templates need singular/plural handling. Reading level: Grade 4-6."
