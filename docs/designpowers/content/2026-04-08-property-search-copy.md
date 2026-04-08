# Property Search Results Page — UX Copy
**Project:** Real estate app search results  
**Date:** 2026-04-08  
**Writer:** content-writer agent  
**Emotional target:** Trustworthy, fast, respectful of time  
**Reading level target:** Grade 4-6 (Aisha-first)

---

## 1. Card Copy Strings

### Price Format
**Primary display:** `$425,000`  
**Rationale:** Full numbers build trust. No abbreviations. Aisha needs to see the real number.

**Alternative for $1M+:** `$1,250,000` (still full number, not "1.25M")

### Beds/Baths/Sqft Format
**Display:** `3 bd / 2 ba / 1,450 sqft`  
**Screen reader:** "3 bedrooms, 2 bathrooms, 1,450 square feet"  
**Rationale:** Abbreviations save space but spell out for assistive tech. Forward slashes parse clearly for screen readers.

### Days on Market Label
**Display:** `Listed 5 days ago`  
**Screen reader:** Same  
**Rationale:** "Days ago" is more conversational and less jargon-y than "days on market." Fits Aisha's literacy level. Active voice.

**Edge cases:**
- Today: `Listed today`
- Yesterday: `Listed yesterday`
- 1 day: `Listed 1 day ago`
- 30+ days: `Listed 4 weeks ago` (convert to weeks after 30 days)

### Price Per Sqft Format
**Display:** `$294/sqft`  
**Screen reader:** "294 dollars per square foot"  
**Rationale:** Compact for card space. Common real estate metric but may confuse Aisha — recommend making this secondary/optional info.

### Address Format
**Display:**  
```
123 Oak Street
Riverside District
```
**Screen reader:** "123 Oak Street, Riverside District"  
**Rationale:** Two lines for scanability (Maya on mobile). No city/state per design-lead constraint. Neighborhood helps orient users.

---

## 2. Status Badge Strings

### New Listing Badge
**Display:** `New`  
**Screen reader:** "New listing"  
**Icon:** Sparkle or star (visual indicator)  
**Character count:** 3 chars + icon = ~8 chars total  
**Rationale:** Simple, fast to scan. Universal concept.

### Price Reduced Badge
**Display (with amount):** `$10K off`  
**Display (percentage):** `5% off`  
**Screen reader:** "Price reduced by 10 thousand dollars" or "Price reduced by 5 percent"  
**Character count:** ~7-9 chars  
**Rationale:** "Off" is simpler than "reduced." Shows value immediately (important for Aisha's financial stress).

**Fallback (no amount):** `Price drop` (10 chars)

### Open House Badge
**Display:** `Open Sat 1-3`  
**Screen reader:** "Open house Saturday 1 PM to 3 PM"  
**Character count:** 12 chars  
**Rationale:** Day + time window. Critical info for time-pressed users like Aisha.

**Alternative (no time):** `Open house` (10 chars)

### Pending/Under Contract Badge
**Display:** `Pending`  
**Screen reader:** "Pending sale"  
**Character count:** 7 chars  
**Rationale:** Standard term. Low literacy concern but common enough in context.

### Back on Market Badge
**Display:** `Available again`  
**Screen reader:** "Back on market"  
**Character count:** 15 chars (at limit)  
**Rationale:** "Available" is grade 3-4 reading level vs "market" which is grade 6. Positive framing.

---

## 3. Interactive Element Labels

### Save/Favorite Button
**Visible label:** (icon only, per design-lead)  
**Icon:** Heart outline (unsaved) / Heart filled (saved)  
**Screen reader label (unsaved):** "Save this home"  
**Screen reader label (saved):** "Remove from saved homes"  
**Button accessible name:** Includes property address, e.g., "Save 123 Oak Street, Riverside District"  
**Rationale:** "Save" is grade 1 reading level. "Home" is warmer than "listing" or "property."

### Card Link (Full Card Clickable)
**Screen reader announcement:**  
```
"View details for 123 Oak Street, Riverside District. 
3 bedrooms, 2 bathrooms, 1,450 square feet. 
$425,000. 
Listed 5 days ago."
```
**Rationale:** David (blind user) needs full context before clicking. Address first for orientation, then key facts.

### Load-More Button
**Display:** `Show more homes`  
**Screen reader:** Same (optional: "Show more homes, currently showing 20 of 143 results")  
**Character count:** 15 chars  
**Rationale:** Clear action. "Homes" not "results" — human-centered language. Grade 2-3 reading level.

### Sort Dropdown Labels
**Trigger button:** `Sort: Price (low to high)` or just `Price (low to high)` if space tight  
**Screen reader:** "Sort by price, low to high. Change sort order."

**Dropdown options:**
- `Price (low to high)`
- `Price (high to low)`
- `Newest first`
- `Most relevant` (if applicable)
- `Beds (most to least)`

**Screen reader for options:** "Sort by price, low to high" (announced as radio button or selected menu item)

**Rationale:** Explicit sort direction. No abbreviations. "Newest" not "most recent" (shorter, grade 3).

### Results Count Format
**Singular:** `1 home found`  
**Plural:** `143 homes found`  
**Zero:** `No homes found` (see Empty States section)

**Screen reader:** Same (announced as live region when updated)

**Rationale:** Simple, direct. "Found" confirms action completion (respectful of time).

---

## 4. Screen Reader Announcements

### Full Card Announcement (Complete Listing Summary)
**What David hears when tabbing to a card link:**
```
"Link. 
123 Oak Street, Riverside District. 
$425,000. 
3 bedrooms, 2 bathrooms, 1,450 square feet. 
Listed 5 days ago. 
New listing. 
View details."
```

**Structure:**
1. Address (orientation)
2. Price (key decision factor)
3. Specs (beds/baths/sqft)
4. Days on market
5. Status badges (if any)
6. Call to action

**Rationale:** Most important info first (address + price). Status badges at end so they don't interrupt flow.

### Dynamic Announcements (Live Regions)

**New results loaded:**  
`"Loaded 20 more homes. Now showing 40 of 143."`

**Sort changed:**  
`"Results sorted by price, low to high."`

**Save toggled (on):**  
`"123 Oak Street saved."`

**Save toggled (off):**  
`"123 Oak Street removed from saved homes."`

**Rationale:** Polite live region (not assertive) so it doesn't interrupt. Confirms action with address for context.

### Skip Link Text
**Display:** `Skip to results`  
**Rationale:** First focusable element. Let's David skip filters/nav and jump to listings.

### Landmark Labels
**Main landmark:** `<main aria-label="Search results">`  
**Navigation landmark (filters):** `<nav aria-label="Search filters">`  
**Complementary (sidebar/map):** `<aside aria-label="Map view">`

**Rationale:** Clear landmark navigation for screen reader users. "Search results" is self-explanatory.

---

## 5. Empty and Edge States

### No Results Found
**Heading:** `No homes found`  
**Body:**  
```
Try adjusting your filters or search area.
```
**Call to action button:** `Clear all filters`

**Screen reader:** Same

**Reading level:** Grade 2-3  
**Rationale:** Short, actionable. No blame language ("Sorry"). Grade 1 vocabulary.

### Search Too Narrow (Zero Results with Heavy Filtering)
**Heading:** `No homes match your filters`  
**Body:**  
```
Try removing some filters to see more homes.
```
**Suggested actions:**
- `Remove price limit`
- `Show all bedroom options`
- `Expand search area`

**Reading level:** Grade 3-4  
**Rationale:** Specific problem + solution. Aisha can fix it herself.

### Loading State (Skeleton Cards Visible)
**Screen reader (live region announcement):** `"Loading search results."`  
**Visually hidden text on skeleton cards:** "Loading"

**Rationale:** Minimal announcement. Don't spam David with "loading" for every skeleton card. One polite announcement is enough.

### Error Loading Results
**Heading:** `We can't load results right now`  
**Body:**  
```
Please try again in a moment.
```
**Call to action button:** `Try again`

**Screen reader:** Same (announced as alert role)

**Reading level:** Grade 2  
**Rationale:** Plain language error. No technical jargon. Grade 1-2 vocabulary. Respectful of user's time — clear action.

---

## 6. Vocabulary List (Consistency Decisions)

| Concept | Use This | Not This | Rationale |
|---------|----------|----------|-----------|
| The thing being viewed | **home** | property, listing, unit, house | Warmer, grade 1 word, emotionally appropriate |
| User's collection | **saved homes** | favorites, liked, bookmarked | Clear action verb, consistent with button label |
| Bathrooms (abbreviated) | **ba** | bth, bath | Shortest standard abbreviation |
| Bedrooms (abbreviated) | **bd** | br, bed, bdrm | Shortest standard abbreviation |
| Square feet (abbreviated) | **sqft** | sf, sq ft | Most common real estate convention |
| Status of home | **available** | active, on market | Grade 3 word vs grade 6 |
| User action on card | **view details** | see more, learn more, open | Specific to David (screen reader), clear action |
| Sorting | **sort** | filter, order by | "Sort" is distinct from "filter" (separate UI) |
| Adjusting search | **filter** | refine, narrow | Grade 4 word, standard web pattern |

**Tone consistency:**
- Use contractions sparingly (only in casual UI like empty states: "can't" is fine)
- Active voice always
- Grade 4-6 reading level priority (Aisha-first)
- No real estate jargon unless unavoidable (and if used, keep it simple: "pending" is okay, "contingent offer" is not)

---

## 7. Reading Level Assessment

| Content Area | Grade Level | Notes |
|--------------|-------------|-------|
| **Card strings** (price, address, specs) | Grade 2-3 | Numbers and addresses are low complexity. "Listed X days ago" is grade 3. |
| **Status badges** | Grade 3-5 | "New" and "Pending" are simple. "Available again" is grade 4. "Price reduced" is grade 5. |
| **Interactive labels** (save, sort, load more) | Grade 1-3 | "Save," "show," "sort" are all grade 1-3 words. |
| **Screen reader announcements** | Grade 4-5 | Longer sentences but still plain language. "Bedrooms" is grade 4. |
| **Empty states** | Grade 2-3 | "No homes found" is grade 2. "Try adjusting" is grade 3. |
| **Error messages** | Grade 2 | "We can't load results" is grade 2. Very plain. |

**Overall assessment:** Meets grade 4-6 target. Prioritizes Aisha's low literacy needs while remaining professional and trustworthy for all users.

**Tested with:** Hemingway Editor and Flesch-Kincaid Grade Level formulas.

---

## Handoff to design-builder

Hey design-builder, here's what you need to wire up:

### Final Strings (Use As-Is)
- All status badges (section 2) — these are locked and tested
- Interactive element labels (section 3) — save button, load more, sort options
- Empty/error states (section 5) — exact copy, don't improvise

### Dynamic Templates (Requires Logic)
- **Days on market:** You need conditional logic for "today" vs "yesterday" vs "X days ago" vs "X weeks ago" (after 30 days)
- **Results count:** Singular/plural handling ("1 home" vs "143 homes")
- **Save button state:** Toggle between "Save this home" and "Remove from saved homes" for screen readers
- **Live region announcements:** Wire up ARIA live regions for sort changes, new results loaded, and save toggles

### Watch Out For
1. **Full card announcement for screen readers** (section 4) — make sure the entire card link has one accessible name with address, price, specs, and badges. Don't let individual elements inside the link announce separately (use aria-hidden on decorative text that's already in the link label).

2. **Price format:** Always use full numbers, no abbreviations. Trust is the emotional target — don't hide zeros.

3. **Status badge character limits:** "Available again" is exactly at your 15-char limit. If the icon eats more space, fall back to "Available" (9 chars).

4. **Screen reader labels on icons:** The save button (heart icon) is icon-only visually, but it MUST have an accessible name that includes the property address. Use aria-label or visually-hidden text.

5. **Reading level:** If you add any new copy (tooltips, microcopy, etc.), run it through Hemingway and keep it grade 4-6. Don't use jargon. Aisha is the priority user.

6. **Address format:** Two lines (street, then neighborhood). No city/state per design-lead constraints. If neighborhood data is missing, just show street address on one line.

7. **Live regions:** Use `aria-live="polite"` not `assertive` — we don't want to interrupt David mid-flow. Announcements should be brief (see section 4).

### Testing Checklist for You
- [ ] Tab through cards with a screen reader — does the full card announcement make sense?
- [ ] Toggle save button — does it announce the state change?
- [ ] Change sort order — does the live region announce it?
- [ ] Load more results — does the live region announce the count?
- [ ] Check badge character counts on smallest viewport (Maya's mobile)
- [ ] Verify singular/plural handling for results count
- [ ] Test empty states (no results, error) — do they show the right copy?

Let me know if any strings feel off in context or if you need variants for edge cases I didn't cover (like, what if sqft data is missing? What if there's no neighborhood name?). I can write fallbacks.

— content-writer
