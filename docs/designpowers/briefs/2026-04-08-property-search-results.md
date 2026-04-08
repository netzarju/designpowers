# Design Brief: Property Search Results Page

## Problem Statement
Users face information overload when browsing property listings. Hundreds of results with dense data make it hard to quickly identify which properties are worth exploring. The result: decision fatigue, missed opportunities, and wasted time.

## Users
Home buyers and renters — both first-time (need more guidance, less familiar with terminology) and experienced (want efficiency, scan fast). All browsing on mobile during commutes, breaks, or couch sessions, with occasional desktop deep-dives.

## Design Direction
A scannable, card-based results page that surfaces the most decision-relevant information first — not everything about a property, but enough to decide "worth a tap or not" in under 3 seconds. Progressive disclosure: summary on the card, detail on tap.

## Constraints
- Responsive web, mobile-first
- Must handle 100+ results without performance degradation
- Image-heavy content (property photos are the primary hook)
- No existing design system (building from scratch)
- Accessibility is a priority — WCAG 2.1 AA minimum across all components

## Taste Direction (Early Signal)
- Trustworthy and fast — "a tool that respects your time"
- Zillow: good data, but too dense
- Redfin: cleaner, but loses personality
- The sweet spot: clean enough to scan, warm enough to feel human

## Success Criteria
- Users can identify a "worth exploring" property within 3 seconds of scanning
- Page feels fast on mobile (perceived and actual performance)
- First-time buyers don't feel overwhelmed; experienced searchers don't feel slowed down

## Out of Scope
- Search filters / filter UI (separate project)
- Individual property detail page
- Map view (results list only for now)
- User accounts / saved listings
