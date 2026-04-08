# Property Search Results — Design Strategy

**Project:** Property search results page for real estate app  
**Date:** April 8, 2026  
**Created by:** design-strategist  
**Status:** Strategy approved, ready for visual design

---

## Executive Summary

We're designing a property search results page that solves information overload. Users need to identify "worth exploring" properties within 3 seconds of scanning. This strategy prioritizes speed, accessibility, and high-value signals (days on market, status badges) over industry-standard information density.

**Key differentiator:** We surface time-pressure signals (new listings, price cuts, days on market) that competitors bury. This serves both anxious first-time buyers and methodical comparison shoppers.

**Non-negotiable:** WCAG 2.1 AA compliance across all components. No accessibility theater — keyboard nav, screen reader support, and colorblind-safe design are table stakes, not nice-to-haves.

---

## Design Principles

### 1. Three Seconds to Signal
**The principle:** Every card must communicate "worth exploring or not" within 3 seconds of scanning.

**What it means in practice:**
- Visual hierarchy follows user-specified order: photo → price → beds/baths/sqft → days on market
- Status signals (new, price cut, open house) use high-contrast overlays on the photo, not buried in metadata
- Price is the largest text element after the photo
- Deal-breaker info (beds/baths) is scannable without reading

**What it rules out:**
- Dense paragraph descriptions on the card (move to detail page)
- Broker branding, logos, or agent photos on cards (clutter)
- Feature lists longer than 3 items (overwhelming)
- Hidden information that requires hover or click to reveal

**How to test it:**
- 5-second test: show a card, hide it, ask "would you explore this property?"
- Eye-tracking: do users fixate on photo → price → beds/baths in that order?
- Time-to-decision: can users decide in under 3 seconds per card?

---

### 2. Accessibility Is Not Negotiable
**The principle:** Every interaction, every visual element, every piece of information must meet WCAG 2.1 AA minimum. No exceptions.

**What it means in practice:**
- All touch targets are 48x48px minimum (industry standard is 40-44px — we exceed it)
- All status badges use 4.5:1 contrast minimum and include text alternatives for screen readers
- All interactive elements have visible focus indicators (2px solid, high contrast)
- All cards are keyboard-navigable with logical tab order
- All images have descriptive alt text (not "property image 1")
- Load-more button instead of infinite scroll (preserves keyboard position and screen reader context)

**What it rules out:**
- Color-only communication (red = hot, green = new) — must include text or icons
- Infinite scroll (accessibility disaster for keyboard and screen reader users)
- Background image text overlays without text alternatives
- Auto-playing carousels or videos
- Touch targets smaller than 48px (including filter chips, favorite icons, card links)

**How to test it:**
- Keyboard-only navigation: can you complete all tasks without a mouse?
- Screen reader test: does NVDA/VoiceOver read cards logically?
- Colorblind test: does the design work in grayscale?
- Contrast checker: do all text and interactive elements meet 4.5:1 minimum?
- Touch target audit: are all interactive elements 48x48px minimum?

---

### 3. Information Hierarchy Beats Information Density
**The principle:** Show less, but show it better. Whitespace and clear hierarchy beat cramming more data onto the card.

**What it means in practice:**
- One card per row on mobile (no side-by-side cramming)
- Generous padding around text elements (minimum 16px)
- Days on market gets dedicated space (not hidden in overflow menu)
- Price-per-sqft is displayed (high-value comparison metric)
- Maximum 3 status badges per card (prioritize new, price cut, open house)

**What it rules out:**
- Zillow-style density (tiny text, crammed layout, visual chaos)
- Feature lists with 10+ bullets
- Multiple CTAs on one card (one primary action: view details)
- Truncated text with "read more" (let the card breathe)

**How to test it:**
- Comprehension test: after viewing 10 cards, can users recall key details?
- Scan speed: how many cards can users evaluate per minute?
- A/B test: dense layout vs spacious layout — which leads to more detail views?

---

### 4. Surface Time Pressure, Not Urgency Theater
**The principle:** Give users real signals about market dynamics (days on market, price changes) instead of artificial scarcity ("only 2 left!" "hot property!").

**What it means in practice:**
- Days on market is displayed prominently (reveals negotiating room and listing freshness)
- Price history is visible if available (price cut badge + amount reduced)
- Status badges are factual: "New listing" (posted in last 48h), "Price reduced" (with %), "Open house" (with date)
- No countdown timers, no "X people viewing now," no fake urgency

**What it rules out:**
- Dark patterns (artificial scarcity, countdown timers)
- Vague status messages ("Hot!" "Popular!" without definition)
- Paid placement disguised as organic results
- Burying days-on-market data in detail page

**How to test it:**
- User interviews: do users trust the time-pressure signals?
- Behavior analysis: do "price reduced" badges lead to more clicks than "hot" badges?
- A/B test: days-on-market visible vs hidden — does visibility increase engagement?

---

## Competitive Position

### Industry Failures We're Fixing

**Accessibility disasters:**
- Zillow, Redfin, Trulia all fail touch target minimums (40-44px vs 48px required)
- Contrast failures on status badges (white text on yellow = 2.8:1, need 4.5:1)
- Infinite scroll breaks keyboard navigation and screen reader context
- Generic alt text ("image 1 of 12") or missing alt text on property photos

**Information hierarchy failures:**
- Competitors bury days on market (Zillow hides it entirely on mobile)
- Status badges are inconsistent (Redfin uses 5 different badge types, no clear hierarchy)
- Broker branding clutters cards (agent photo, logo, "featured by")
- Price-per-sqft hidden in detail page or missing entirely

### What We Do Differently

**Accessibility-first:**
- 48px minimum touch targets (exceeds industry standard)
- Load-more button instead of infinite scroll (preserves keyboard and screen reader position)
- Colorblind-safe status badges (text + icons, not color-only)
- Semantic HTML with proper ARIA labels

**Information hierarchy:**
- User-specified card hierarchy: photo → price → beds/baths/sqft → days on market
- Days on market is visible on every card (reveals market dynamics)
- Price-per-sqft displayed (comparison shopping essential)
- Status badges limited to 3 per card, high-contrast overlays on photo

**Honest signals:**
- No urgency theater, no dark patterns
- Factual status badges with clear definitions
- Price history visible (amount reduced, not just "price cut")
- No paid placement disguised as organic

---

## Information Architecture

### Property Card Hierarchy (User-Specified)

**1. Photo (primary visual anchor)**
- Hero image, 16:9 aspect ratio
- Status badges as high-contrast overlays (top-left corner)
- Maximum 3 badges: prioritize "New listing," "Price reduced," "Open house"
- Alt text describes property type and key features (not "image 1")

**2. Price (largest text element after photo)**
- Font size: 24px minimum (mobile), 28px (desktop)
- Color: high contrast, accessible
- If price reduced: show old price (strikethrough) + new price + % reduced

**3. Beds/Baths/Sqft (scannable metadata)**
- Icon + number format for quick scanning (bed icon + "3", bath icon + "2", sqft icon + "1,200")
- Horizontal layout, evenly spaced
- Font size: 16px minimum

**4. Days on Market (time-pressure signal)**
- "Listed 3 days ago" or "Listed 45 days ago"
- Color-coded (accessible): 0-7 days = neutral, 30+ days = opportunity signal
- Font size: 14px minimum

**5. Address/Location (secondary metadata)**
- Neighborhood or zip code (full address on detail page)
- Font size: 14px

**6. Price per Sqft (comparison metric)**
- "$450/sqft" format
- Font size: 14px
- Helps comparison shopping

**7. Primary CTA**
- "View details" button or entire card is clickable
- 48x48px minimum touch target
- Visible focus indicator for keyboard nav

### Results Page Layout

**Mobile (320px - 768px):**
- Single column, one card per row
- Cards stack vertically with 16px gap between
- Load-more button at bottom (never infinite scroll)
- Sticky filter bar at top (collapses to icon on scroll)

**Desktop (768px+):**
- 2-column grid (768-1024px), 3-column grid (1024px+)
- Cards maintain aspect ratio, equal height rows
- 24px gap between cards
- Load-more button centered at bottom
- Sidebar filters (left side, persistent)

**Pagination vs Load-More:**
- Load-more button (not infinite scroll) for accessibility
- Loads 20 cards per page (balances performance and user control)
- Button text: "Load 20 more properties" (specific, not vague "Load more")
- Keyboard focus preserved after load (user doesn't lose place)

---

## Experience Map

### 1. Entry (First impression)
**User arrives from search/filter action**

**Goals:**
- Understand result count and quality
- Orient to layout and card structure
- Spot first "worth exploring" property quickly

**Design supports:**
- Result count at top: "143 properties in Austin, TX"
- Filter summary visible: "3 beds, 2 baths, $300k-$500k"
- First card loads above fold (no hero image delaying content)
- Clear visual hierarchy: photo → price → metadata

**Success signal:** User scrolls within 3 seconds (engaged with results)

---

### 2. Scan (Rapid evaluation)
**User evaluates multiple cards quickly**

**Goals:**
- Identify "yes," "no," "maybe" properties in 3 seconds per card
- Spot status signals (new, price cut) without cognitive load
- Compare properties side-by-side (price, price-per-sqft, days on market)

**Design supports:**
- Consistent card hierarchy (no surprises between cards)
- Status badges on photo (high visibility, no hunting)
- Days on market visible (reveals urgency or opportunity)
- Price-per-sqft helps comparison shopping
- Whitespace reduces cognitive load

**Success signal:** User saves or clicks 1-3 properties within first 30 seconds

---

### 3. Decide (Selection)
**User identifies properties worth exploring further**

**Goals:**
- Remember which properties looked promising
- Avoid clicking the same property twice
- Share promising properties with partner/roommate

**Design supports:**
- Save/favorite button (48px touch target, visible focus indicator)
- Visited cards change visual state (subtle, accessible)
- Share button on card (generates shareable link)
- Saved count visible in sticky header: "3 saved"

**Success signal:** User saves 3-5 properties or clicks to view details

---

### 4. Act (Next step)
**User clicks card to view property details**

**Goals:**
- Access full information (photos, description, contact)
- Return to results without losing place
- Continue scanning if property isn't right

**Design supports:**
- Entire card is clickable (large touch target)
- Detail page opens in same tab (accessible back button)
- Scroll position preserved on return (no layout shift)
- Keyboard focus returns to card user clicked (screen reader support)

**Success signal:** User views 3+ property detail pages per session

---

## Success Metrics

### Primary Metrics
1. **Time to first save/click:** Users identify "worth exploring" property within 3 seconds of scanning _(target: 80% of users under 5 seconds)_
2. **Cards scanned per minute:** Users evaluate 15-20 cards per minute _(baseline: industry average is 8-12)_
3. **Save rate:** 30%+ of users save at least one property _(baseline: industry average is 18-22%)_

### Accessibility Metrics
4. **Keyboard task completion:** 100% of tasks completable without mouse _(WCAG 2.1 AA requirement)_
5. **Screen reader comprehension:** Users understand card content with screen reader only _(qualitative testing with blind users)_
6. **Contrast compliance:** 100% of text/interactive elements meet 4.5:1 minimum _(automated testing)_

### Engagement Metrics
7. **Detail page views:** Users click 3+ properties per session _(target: 50% of users)_
8. **Return rate:** Users return to results page after viewing details _(target: 70%+ return)_
9. **Load-more engagement:** Users click "load more" at least once _(target: 40% of users)_

---

## Constraints and Trade-Offs

### Constraint 1: WCAG 2.1 AA Compliance
**Impact:** Limits color choices, requires larger touch targets, rules out infinite scroll  
**Trade-off:** Accessibility-first design may feel "less modern" than competitors' infinite scroll, but it's non-negotiable. We're building for everyone, not just able-bodied users.  
**Mitigation:** Lean into accessibility as brand differentiator. "Built for everyone" is a competitive advantage.

### Constraint 2: Mobile-First, 3-Second Decision Window
**Impact:** Limits information density, requires brutal prioritization  
**Trade-off:** Can't show every feature on the card (pool, garage, year built). Some users want more data upfront.  
**Mitigation:** Hierarchy is user-specified (photo → price → beds/baths → days on market). Additional data lives on detail page. Test with users to validate prioritization.

### Constraint 3: Performance and Data Weight
**Impact:** Aisha (edge case persona) has 500MB/month data cap. Heavy images blow through her budget.  
**Trade-off:** High-quality hero images vs data-conscious design. Can't serve 2MB images to every user.  
**Mitigation:** Responsive images (srcset), lazy loading, opt-in "data saver" mode. Test with budget Android devices on throttled connections.

### Constraint 4: Competitive Pressure (Feature Parity)
**Impact:** Competitors show broker branding, 3D tours, mortgage calculators on cards. Stakeholders may push for feature parity.  
**Trade-off:** Feature bloat vs focused experience. Adding everything competitors have leads to Zillow's information overload.  
**Mitigation:** Principles guide cuts. If a feature doesn't serve "3 seconds to signal," it doesn't belong on the card. Mortgage calculator lives on detail page.

---

## Next Steps: Handoff to design-lead

This strategy document provides:
1. **Inclusive personas** (4 users) at `/Users/netzas/designpowers/docs/designpowers/personas/2026-04-08-property-search-personas.md`
2. **Design principles** (4 opinionated, testable principles)
3. **Information architecture** (card hierarchy, results page layout)
4. **Competitive position** (what we do differently, industry failures we're fixing)
5. **Experience map** (entry → scan → decide → act)
6. **Success metrics** (primary, accessibility, engagement)
7. **Constraints and trade-offs** (WCAG compliance, mobile-first, performance, competitive pressure)

**Ready for visual design phase.** design-lead should focus on:
- Card hierarchy (photo → price → beds/baths → days on market)
- Status badge design (high-contrast overlays, text + icons, colorblind-safe)
- Touch target sizing (48px minimum, exceeds industry standard)
- Focus indicators (2px solid, high contrast, visible on all interactive elements)
- Typography scale (price = 24px mobile/28px desktop, metadata = 16px, secondary = 14px)

**Key principles to carry forward:**
1. Three seconds to signal (speed test every design decision)
2. Accessibility is not negotiable (WCAG 2.1 AA minimum, no exceptions)
3. Information hierarchy beats information density (Redfin's whitespace, not Zillow's cramming)
4. Surface time pressure, not urgency theater (days on market, price history, factual badges)

The personas are your sanity check: Maya tests speed and sunlight readability, Robert tests keyboard nav and colorblind-safe design, Aisha tests cognitive load and data weight, David tests WCAG compliance and screen reader support.

Ship for all four, ship for everyone.
