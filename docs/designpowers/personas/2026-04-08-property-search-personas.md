# Property Search Results — Inclusive Personas

**Project:** Property search results page for real estate app  
**Date:** April 8, 2026  
**Created by:** design-strategist

---

## Primary User 1: Maya Chen — First-Time Buyer in a Rush

**Context**  
Maya is 28, a software engineer in Seattle, and she's trying to buy her first home before interest rates climb again. She has 3 weeks to find a place before her pre-approval expires. She's searching during work breaks and commutes — never more than 5 minutes at a time.

**Abilities and Conditions**  
- Uses iPhone 14 in direct sunlight (commuting, walking between meetings)
- Mild myopia, wears glasses but often forgets them at home
- ESL (English as second language) — prefers simple, concrete language over real estate jargon

**Technology**  
- iPhone 14, iOS 18
- Usually on 5G but drops to LTE in her neighborhood
- Uses Voice Control when walking
- Browser: Safari mobile

**Goals**  
- Identify "worth exploring" properties in under 3 seconds per card
- Understand what's changed since yesterday (new listings, price cuts)
- Filter out overpriced properties quickly (uses price-per-sqft as heuristic)
- Save promising listings to share with her partner later

**Frustrations**  
- "Everything looks the same after scrolling 20 listings"
- Can't read tiny text in bright sunlight
- Loses her place when the page reloads
- Doesn't understand why a property is "featured" (is it paid placement?)
- Wastes time on listings that sold 3 days ago but still show up

**Environment**  
High-pressure, fragmented attention, mobile-first, outdoor lighting conditions, voice control intermittent use

---

## Primary User 2: Robert Williams — Experienced Renter, Methodical Searcher

**Context**  
Robert is 42, a high school teacher in Austin, and he's rented 6 different apartments in 15 years. He knows exactly what he wants: ground floor, washer/dryer in unit, allows large dogs, parking included. He searches on his laptop every Sunday morning with coffee, spending 45-60 minutes per session.

**Abilities and Conditions**  
- Colorblind (deuteranopia — red-green colorblindness)
- Uses trackpad, prefers keyboard navigation
- Runs browser at 125% zoom
- Screen reader user for long text (reads lease details with VoiceOver to catch fine print)

**Technology**  
- MacBook Air M2, macOS 15
- Home WiFi, reliable connection
- Browser: Safari desktop with VoiceOver enabled
- Uses "Reader Mode" frequently to strip out clutter

**Goals**  
- Compare 5-10 properties side-by-side on detailed criteria
- Spot deal-breakers instantly (no dogs = skip, no parking = skip)
- Track which listings he's already reviewed (hates seeing the same thing twice)
- Contact landlord directly without broker intermediary
- Understand time pressure (days on market = negotiating room)

**Frustrations**  
- Color-coded badges are meaningless to him (red "Hot!" vs green "New" look identical)
- Infinite scroll breaks keyboard navigation and his mental map
- Can't tell which properties he's already clicked
- Photos with text overlays are invisible to VoiceOver
- Broker contact info clutters the card when he wants landlord info

**Environment**  
Methodical, desktop, high-scrutiny, keyboard and screen reader user, reliable connectivity, extended sessions

---

## Edge Case User: Aisha Osman — Low-Literacy User Under Financial Stress

**Context**  
Aisha is 35, works two jobs (retail + gig delivery), and she's searching for a rental after an eviction. She has a 6-year-old daughter and needs to find a place within 10 days. She has limited English literacy (reads at 4th-grade level) and no rental history that qualifies her for most listings.

**Abilities and Conditions**  
- Low English literacy (4th-grade reading level)
- Uses Android phone with large text (accessibility settings maxed)
- Cognitive load from financial stress and time pressure
- Intermittent vision blur from stress-related migraines

**Technology**  
- Samsung Galaxy A14 (budget Android), Android 13
- Prepaid data plan (500MB/month) — avoids images when possible
- Browser: Chrome mobile with "Lite mode" enabled (data saver)
- Uses Google Translate for complex words

**Goals**  
- Understand price and basic requirements (beds/baths) instantly
- Avoid wasting data on listings she can't afford
- Identify "flexible landlord" signals (properties on market 30+ days)
- Skip listings with income requirements she can't meet

**Frustrations**  
- Can't understand real estate jargon ("HOA," "sqft," "pre-approval")
- Auto-playing videos and hero images blow through her data cap
- Doesn't know what "days on market" means or why it matters
- Form fields require information she doesn't have (credit score, references)
- Price doesn't include fees/deposits, so "affordable" listings aren't

**Environment**  
High stress, data-constrained, low literacy, mobile-only, fragmented attention, financial pressure, time pressure

**Design Implications**  
Aisha reveals where our assumptions break: jargon, data weight, cognitive load under stress, income-based exclusion patterns. If the design works for Aisha, it works for Maya on a bad day.

---

## Stress Case User: David Kim — Screen Reader User in Crisis Mode

**Context**  
David is 52, blind since birth, and he's searching for an accessible apartment after his current building announced elevator repairs that will take 4 months (he lives on the 8th floor). He needs ground floor, wheelchair-accessible (he uses a cane but has mobility limitations), near public transit. He's searching on a tight timeline with high stakes.

**Abilities and Conditions**  
- Blind, screen reader user (NVDA on Windows)
- Expert keyboard navigator (never touches a mouse)
- High proficiency with assistive tech but intolerant of broken implementations
- Audio processing in noisy environments (searches at work during lunch breaks)

**Technology**  
- Windows 11 desktop, office computer
- NVDA screen reader (latest version)
- Browser: Firefox with high contrast mode
- Braille display (RefreshaBraille 18) for skimming

**Goals**  
- Navigate 50+ listings efficiently using keyboard and semantic markup
- Understand property accessibility features (ground floor, ramps, wide doors)
- Skip inaccessible listings without wasting time
- Identify landlord responsiveness signals (days on market, "pet-friendly" = flexible)

**Frustrations**  
- Image carousels with no alt text or generic "property image 1 of 12"
- Clickable cards with no focus indicators (can't tell where he is)
- Status badges as background images (CSS) invisible to screen reader
- "Load more" buttons that reload the page and reset his position
- Filter controls that don't announce state changes (checked/unchecked)

**Environment**  
High-stakes, time-pressure, expert assistive tech user, noisy environment (office), requires perfect semantic HTML and ARIA, intolerant of accessibility failures

**Design Implications**  
David is the canary in the coal mine. If the design fails for David, it's not WCAG 2.1 AA compliant. His frustrations are non-negotiable requirements: semantic markup, focus management, alt text, keyboard nav, state announcements.

---

## How to Use These Personas

**Maya** is your speed test. Can she scan a card in 3 seconds? Can she see it in sunlight? Can she voice-navigate?

**Robert** is your keyboard and colorblind test. Does the design work without color? Can he tab through 50 cards? Does VoiceOver read the card logically?

**Aisha** is your stress test. Is the language simple? Is the data weight low? Does the hierarchy surface her top needs (price, beds, baths) first?

**David** is your compliance test. Is the semantic HTML correct? Are focus states visible? Do status badges have text alternatives? Does "load more" preserve his position?

Design for all four, ship for everyone.
