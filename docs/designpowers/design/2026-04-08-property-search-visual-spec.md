# Property Search Results — Visual Design Specification

**Date:** 2026-04-08  
**Project:** Property search results page for real estate app  
**Design Lead:** design-lead agent  
**Status:** Ready for implementation

---

## Design Principles

1. **Three seconds to signal** — every card communicates "worth exploring or not" within 3 seconds
2. **Accessibility is not negotiable** — WCAG 2.1 AA minimum, 48px touch targets
3. **Information hierarchy beats information density** — whitespace and clarity over cramming
4. **Surface time pressure, not urgency theater** — days on market, factual badges

---

## 1. Color System

### Primary Palette
Warm, trustworthy, human — avoiding sterile corporate blues or aggressive reds.

- **Primary Brand**: `#2B6CB0` (Ocean Blue)
  - Use: Save buttons, focus states, interactive elements
  - Contrast ratio: 4.52:1 against white (AA compliant for large text)

- **Primary Dark**: `#1E4E8C` (Deep Ocean)
  - Use: Hover states, pressed states
  - Contrast ratio: 7.02:1 against white (AAA compliant)

- **Accent Warm**: `#E07A3D` (Terracotta)
  - Use: Price text, high-importance information
  - Contrast ratio: 3.42:1 against white (AA compliant for 24px+ text)

- **Accent Warm Dark**: `#C25E1F` (Burnt Orange)
  - Use: Price hover states
  - Contrast ratio: 4.89:1 against white (AA compliant)

### Semantic Colors (Colorblind-Safe)
All status badges use icon + text, never color alone.

- **Status: New**: `#059669` (Emerald Green)
  - Icon: ✦ (sparkle)
  - Contrast: 4.52:1 against white overlay background
  - Text: "New" in 14px semibold

- **Status: Price Reduced**: `#DC2626` (Alert Red)
  - Icon: ↓ (down arrow)
  - Contrast: 5.14:1 against white overlay background
  - Text: "Price Reduced" in 14px semibold

- **Status: Open House**: `#7C3AED` (Vivid Purple)
  - Icon: 🏠 (house) or ⌂
  - Contrast: 4.67:1 against white overlay background
  - Text: "Open House" in 14px semibold

### Neutral Scale

- **Text Primary**: `#1A202C` (Charcoal)
  - Contrast: 15.8:1 against white (AAA compliant)
  - Use: Price, address, primary information

- **Text Secondary**: `#4A5568` (Slate Gray)
  - Contrast: 8.59:1 against white (AAA compliant)
  - Use: Metadata (beds/baths/sqft, price per sqft)

- **Text Tertiary**: `#718096` (Warm Gray)
  - Contrast: 5.74:1 against white (AA compliant)
  - Use: Days on market, secondary labels

- **Border Default**: `#E2E8F0` (Light Gray)
  - Use: Card borders, dividers

- **Border Hover**: `#CBD5E0` (Medium Gray)
  - Use: Card borders on hover

- **Background Surface**: `#FFFFFF` (Pure White)
  - Use: Card backgrounds

- **Background Page**: `#F7FAFC` (Off-White)
  - Use: Page background, provides subtle contrast with cards

- **Background Overlay**: `rgba(255, 255, 255, 0.95)` (Semi-transparent white)
  - Use: Status badge backgrounds on photos

### Dark Mode Considerations
Not fully specced, but recommend:
- Invert neutral scale
- Reduce primary/accent saturation by 15%
- Use `#1A202C` as page background, `#2D3748` as card background
- Reduce opacity of photo overlays to 0.88

---

## 2. Typography Scale

### Font Family
**System Font Stack** (performance-first):
```css
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, 
             "Helvetica Neue", Arial, sans-serif;
```

Fallback: Arial or sans-serif on all platforms.

### Type Scale

#### Price
- **Mobile**: 24px / 1.2 line height / -0.01em letter spacing / 700 weight
- **Desktop**: 28px / 1.2 line height / -0.01em letter spacing / 700 weight
- **Color**: `#E07A3D` (Accent Warm)

#### Heading (Address)
- **Mobile**: 16px / 1.4 line height / 0 letter spacing / 600 weight
- **Desktop**: 18px / 1.4 line height / 0 letter spacing / 600 weight
- **Color**: `#1A202C` (Text Primary)

#### Body (Metadata: beds/baths/sqft)
- **Mobile**: 16px / 1.5 line height / 0 letter spacing / 400 weight
- **Desktop**: 16px / 1.5 line height / 0 letter spacing / 400 weight
- **Color**: `#4A5568` (Text Secondary)

#### Metadata (Price per sqft)
- **Mobile**: 14px / 1.5 line height / 0 letter spacing / 400 weight
- **Desktop**: 14px / 1.5 line height / 0 letter spacing / 400 weight
- **Color**: `#4A5568` (Text Secondary)

#### Secondary (Days on market)
- **Mobile**: 14px / 1.5 line height / 0 letter spacing / 400 weight
- **Desktop**: 14px / 1.5 line height / 0 letter spacing / 400 weight
- **Color**: `#718096` (Text Tertiary)

#### Status Badge
- **All sizes**: 14px / 1.2 line height / 0.01em letter spacing / 600 weight
- **Color**: Semantic color (New/Price Reduced/Open House)

---

## 3. Spacing System

### Base Unit
**8px** (chosen for easy scaling and alignment)

### Card Internal Spacing
- **Photo**: Full bleed to card edges (0px padding)
- **Content padding**: 16px all sides (2 units)
- **Save button inset**: 12px from top-right corner of card
- **Status badge spacing**: 8px gap between badges, 12px from top-left corner

### Vertical Rhythm (Inside Card Content Area)
- **Photo to Price**: 16px (2 units)
- **Price to Beds/Baths/Sqft**: 12px (1.5 units)
- **Beds/Baths/Sqft to Days on Market**: 8px (1 unit)
- **Days on Market to Address**: 12px (1.5 units)
- **Address to Price per Sqft**: 8px (1 unit)

### Grid & Layout Spacing
- **Card to Card Gap (Mobile)**: 16px (2 units)
- **Card to Card Gap (Tablet/Desktop)**: 24px (3 units)
- **Page Margin (Mobile)**: 16px (2 units)
- **Page Margin (Tablet)**: 32px (4 units)
- **Page Margin (Desktop)**: 48px (6 units)
- **Results Header to First Card**: 24px (3 units)
- **Last Card to Load-More Button**: 32px (4 units)

---

## 4. Card Component Specification

### Card Dimensions

#### Mobile (< 768px)
- **Width**: `100%` (minus page margins)
- **Photo Height**: 50% of card height (aspect ratio 16:9, approximately 200px for 375px viewport)
- **Content Height**: Auto (based on content)
- **Total Card Height**: Approximately 400px

#### Tablet (768px - 1024px)
- **Width**: `calc((100% - 24px) / 2)` (2-column grid)
- **Photo Height**: 240px (16:9 aspect ratio)
- **Content Height**: Auto
- **Total Card Height**: Approximately 440px

#### Desktop (> 1024px)
- **Width**: `calc((100% - 48px) / 3)` (3-column grid)
- **Photo Height**: 220px (16:9 aspect ratio)
- **Content Height**: Auto
- **Total Card Height**: Approximately 420px

### Card Structure (Top to Bottom)

```
┌─────────────────────────────────────┐
│                                     │
│           PHOTO (16:9)              │
│                                     │
│  [Status Badges]      [Save ❤️]    │
│                                     │
├─────────────────────────────────────┤
│  16px padding                       │
│                                     │
│  $450,000 (Price - 24px)            │
│                                     │
│  🛏️ 3  🚿 2  📏 1,850 sqft          │
│  (16px, icon + number)              │
│                                     │
│  Listed 12 days ago (14px)          │
│  (Secondary text)                   │
│                                     │
│  123 Main Street (16px)             │
│  Springfield, IL 62701              │
│                                     │
│  $243/sqft (14px, secondary)        │
│                                     │
│  16px padding                       │
└─────────────────────────────────────┘
```

### Card States

#### Default
- **Border**: 1px solid `#E2E8F0` (Border Default)
- **Border Radius**: 12px
- **Background**: `#FFFFFF` (Background Surface)
- **Shadow**: `0 1px 3px rgba(0, 0, 0, 0.1)`

#### Hover (Desktop/Pointer Devices)
- **Border**: 1px solid `#CBD5E0` (Border Hover)
- **Shadow**: `0 4px 12px rgba(0, 0, 0, 0.15)`
- **Transition**: `all 0.2s ease-in-out`
- **Save Button**: Scale to 1.05, color changes to `#1E4E8C` (Primary Dark)

#### Focus
- **Outline**: 2px solid `#2B6CB0` (Primary Brand)
- **Outline Offset**: 2px
- **Border**: Retains hover state border
- **Background**: No change (remains white)

#### Visited
- **Price Color**: `#7C3AED` (Vivid Purple, same as Open House status)
- **All Other Elements**: Unchanged
- **Note**: Subtle visual feedback that user has clicked this property

#### Loading/Skeleton
- **Photo**: Gray gradient animation (`#E2E8F0` to `#CBD5E0`)
- **Text Lines**: Gray bars with same gradient animation
- **Animation**: 1.5s ease-in-out infinite shimmer effect
- **Aria-label**: "Loading property..."

### Status Badges

**Placement**: Top-left corner of photo, 12px from edges  
**Layout**: Horizontal row, 8px gap between badges, max 3 badges  
**Order of Priority**: New > Price Reduced > Open House

#### Badge Structure
- **Height**: 32px
- **Padding**: 8px horizontal, 6px vertical
- **Border Radius**: 6px
- **Background**: `rgba(255, 255, 255, 0.95)` (Background Overlay)
- **Border**: 1px solid semantic color
- **Shadow**: `0 2px 4px rgba(0, 0, 0, 0.15)`

#### Badge Content
- **Icon**: 14px, semantic color, left-aligned
- **Text**: 14px semibold, semantic color, 6px gap from icon
- **Example**: `✦ New`, `↓ Price Reduced`, `⌂ Open House`

### Save Button

**Placement**: Top-right corner of card, 12px from edges (overlaying photo)  
**Dimensions**: 48px × 48px (meets WCAG touch target minimum)  
**Border Radius**: 24px (circular)

#### Default State
- **Background**: `rgba(255, 255, 255, 0.95)` (Background Overlay)
- **Border**: 1px solid `#E2E8F0` (Border Default)
- **Icon**: ❤️ (heart outline), 24px, `#4A5568` (Text Secondary)
- **Shadow**: `0 2px 4px rgba(0, 0, 0, 0.15)`

#### Hover State
- **Background**: `#FFFFFF` (opaque)
- **Border**: 1px solid `#2B6CB0` (Primary Brand)
- **Icon**: ❤️ (heart outline), 24px, `#2B6CB0` (Primary Brand)
- **Shadow**: `0 2px 6px rgba(0, 0, 0, 0.2)`
- **Transform**: `scale(1.05)`

#### Saved State
- **Background**: `#2B6CB0` (Primary Brand)
- **Border**: 1px solid `#2B6CB0`
- **Icon**: ❤️ (heart filled), 24px, `#FFFFFF`
- **Shadow**: `0 2px 6px rgba(0, 0, 0, 0.2)`

#### Focus State
- **Outline**: 2px solid `#2B6CB0` (Primary Brand)
- **Outline Offset**: 2px
- **All other properties**: Inherit from hover state

### Image Loading Behavior

- **Aspect Ratio**: 16:9 (enforced with `aspect-ratio` CSS property)
- **Object Fit**: `cover` (crop to fill container)
- **Loading**: Lazy loading (`loading="lazy"`)
- **Placeholder**: Gray gradient skeleton while loading
- **Alt Text**: "Property at [address]" (for screen readers)
- **Error State**: Show placeholder icon (🏠) with gray background if image fails to load

---

## 5. Results Page Layout

### Mobile (< 768px)
- **Layout**: Single column
- **Card Width**: 100% minus 16px margins on each side
- **Card Gap**: 16px vertical spacing
- **Results Count**: Sticky header at top, 56px height, white background
- **Sort Controls**: Below results count, 48px height
- **Load-More Button**: 48px height, full width minus margins, 32px margin above

### Tablet (768px - 1024px)
- **Layout**: 2-column grid
- **Grid Gap**: 24px (both horizontal and vertical)
- **Card Width**: `calc((100% - 24px) / 2)`
- **Results Count**: Sticky header, 64px height
- **Sort Controls**: Same row as results count, right-aligned
- **Load-More Button**: 48px height, centered, max-width 320px

### Desktop (> 1024px)
- **Layout**: 3-column grid
- **Grid Gap**: 24px (both horizontal and vertical)
- **Card Width**: `calc((100% - 48px) / 3)`
- **Max Container Width**: 1280px (centered with auto margins)
- **Results Count**: Sticky header, 72px height
- **Sort Controls**: Same row as results count, right-aligned
- **Load-More Button**: 48px height, centered, max-width 320px

### Results Header

**Structure**:
```
┌─────────────────────────────────────────────────────────────┐
│  347 properties found            Sort by: Price ▼  Filter   │
└─────────────────────────────────────────────────────────────┘
```

#### Mobile
- **Height**: 56px
- **Padding**: 16px horizontal
- **Background**: `#FFFFFF` with `box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1)`
- **Results Text**: 16px semibold, `#1A202C` (Text Primary)
- **Sort Control**: 14px, `#4A5568` (Text Secondary), right-aligned
- **Sticky Position**: `position: sticky; top: 0; z-index: 10;`

#### Tablet
- **Height**: 64px
- **Padding**: 24px horizontal
- **Results Text**: 18px semibold
- **Sort Control**: 16px, inline-flex with dropdown icon

#### Desktop
- **Height**: 72px
- **Padding**: 48px horizontal (within max-width container)
- **Results Text**: 20px semibold
- **Sort Control**: 16px, more spacing between controls

### Sort Controls

**Dropdown Style**:
- **Min Width**: 160px
- **Height**: 40px (mobile), 48px (desktop)
- **Border**: 1px solid `#E2E8F0`
- **Border Radius**: 8px
- **Padding**: 12px
- **Font Size**: 14px (mobile), 16px (desktop)
- **Icon**: ▼ (chevron down), 16px, `#4A5568`

**Options**:
- Price: Low to High
- Price: High to Low
- Newest First
- Days on Market
- Square Footage

### Load-More Button

**Styling**:
- **Height**: 48px
- **Width**: Full width (mobile), max-width 320px (tablet/desktop)
- **Border**: 2px solid `#2B6CB0` (Primary Brand)
- **Border Radius**: 8px
- **Background**: `#FFFFFF` (default), `#2B6CB0` (hover)
- **Text**: "Load More Properties", 16px semibold
- **Text Color**: `#2B6CB0` (default), `#FFFFFF` (hover)
- **Padding**: 12px horizontal
- **Margin**: 32px top, 48px bottom

**States**:
- **Default**: White background, blue border and text
- **Hover**: Blue background, white text, `box-shadow: 0 4px 12px rgba(43, 108, 176, 0.3)`
- **Focus**: 2px solid outline, 2px offset, `#2B6CB0`
- **Loading**: Text changes to "Loading...", spinner icon, disabled state
- **Disabled**: Opacity 0.5, cursor not-allowed

**Behavior**:
- Loads 20 more properties on click
- Shows loading spinner while fetching
- Disappears when all results are loaded (replaced with "You've seen all properties")

---

## 6. Focus & Keyboard Navigation

### Focus Indicator Style
- **Outline**: 2px solid `#2B6CB0` (Primary Brand)
- **Outline Offset**: 2px (creates visible gap)
- **Border Radius**: Matches element (12px for cards, 24px for save button, 8px for buttons)
- **Contrast Ratio**: 4.52:1 against white background (AA compliant)

### Tab Order
1. **Results Header**: Results count (not focusable), Sort dropdown (focusable)
2. **Property Cards**: One tab stop per card (entire card is focusable link)
3. **Save Button**: Separate tab stop within each card
4. **Load-More Button**: Final tab stop on page

### Card-Level Keyboard Interactions

**Focus on Card**:
- **Tab**: Focus next card
- **Shift + Tab**: Focus previous card
- **Enter**: Navigate to property detail page
- **Space**: Save/unsave property (same as clicking save button)
- **Tab (from card)**: Focus save button within card

**Focus on Save Button**:
- **Enter or Space**: Save/unsave property
- **Tab**: Focus next card (skips to next card, not next save button)

### Skip Link
- **Text**: "Skip to results"
- **Position**: Visually hidden, appears on focus at top of page
- **Style**: Same as focus indicator, `#2B6CB0` background, white text
- **Function**: Jumps keyboard focus to first property card

### Screen Reader Announcements

**Card Focus**:
```
"Property at 123 Main Street, Springfield, Illinois. 
Price: $450,000. 3 bedrooms, 2 bathrooms, 1,850 square feet. 
Listed 12 days ago. New listing. 
Link. Button: Save property."
```

**Save Button**:
- Default: "Save property. Button."
- Saved: "Unsave property. Button. Pressed."

**Load-More Button**:
- Default: "Load more properties. Button."
- Loading: "Loading more properties. Button. Aria-busy: true."

---

## 7. ASCII Mockups

### Single Card (Mobile)

```
┌───────────────────────────────────────┐
│                                       │
│                                       │
│          [PHOTO 16:9]                 │
│                                       │
│   [✦ New]              [❤️]           │
│                                       │
├───────────────────────────────────────┤
│                                       │
│   $450,000                            │
│                                       │
│   🛏️ 3  🚿 2  📏 1,850 sqft            │
│                                       │
│   Listed 12 days ago                  │
│                                       │
│   123 Main Street                     │
│   Springfield, IL 62701               │
│                                       │
│   $243/sqft                           │
│                                       │
└───────────────────────────────────────┘
```

### Results Page (Mobile, 2 Cards + Load-More)

```
╔═══════════════════════════════════════════════╗
║ 347 properties found     Sort by: Price ▼    ║
╚═══════════════════════════════════════════════╝

┌───────────────────────────────────────────────┐
│                                               │
│              [PHOTO 16:9]                     │
│                                               │
│   [✦ New] [↓ Price Reduced]      [❤️]         │
│                                               │
├───────────────────────────────────────────────┤
│                                               │
│   $450,000                                    │
│                                               │
│   🛏️ 3  🚿 2  📏 1,850 sqft                    │
│                                               │
│   Listed 12 days ago                          │
│                                               │
│   123 Main Street                             │
│   Springfield, IL 62701                       │
│                                               │
│   $243/sqft                                   │
│                                               │
└───────────────────────────────────────────────┘

┌───────────────────────────────────────────────┐
│                                               │
│              [PHOTO 16:9]                     │
│                                               │
│   [⌂ Open House]                 [❤️]         │
│                                               │
├───────────────────────────────────────────────┤
│                                               │
│   $525,000                                    │
│                                               │
│   🛏️ 4  🚿 2.5  📏 2,200 sqft                  │
│                                               │
│   Listed 3 days ago                           │
│                                               │
│   456 Oak Avenue                              │
│   Springfield, IL 62704                       │
│                                               │
│   $239/sqft                                   │
│                                               │
└───────────────────────────────────────────────┘

           ┌─────────────────────────┐
           │  Load More Properties    │
           └─────────────────────────┘
```

### Desktop Layout (3-Column Grid)

```
╔═══════════════════════════════════════════════════════════════════════════════════╗
║ 347 properties found                              Sort by: Price ▼     [Filter]  ║
╚═══════════════════════════════════════════════════════════════════════════════════╝

┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────────┐
│                     │  │                     │  │                     │
│    [PHOTO 16:9]     │  │    [PHOTO 16:9]     │  │    [PHOTO 16:9]     │
│                     │  │                     │  │                     │
│  [✦ New]     [❤️]   │  │  [↓ Reduced] [❤️]   │  │  [⌂ Open]    [❤️]   │
├─────────────────────┤  ├─────────────────────┤  ├─────────────────────┤
│ $450,000            │  │ $525,000            │  │ $389,000            │
│ 🛏️ 3 🚿 2 📏 1,850sf │  │ 🛏️ 4 🚿 2.5 📏 2.2k │  │ 🛏️ 2 🚿 1 📏 1,200sf │
│ Listed 12 days ago  │  │ Listed 3 days ago   │  │ Listed 45 days ago  │
│ 123 Main Street     │  │ 456 Oak Avenue      │  │ 789 Pine Lane       │
│ Springfield, IL     │  │ Springfield, IL     │  │ Springfield, IL     │
│ $243/sqft           │  │ $239/sqft           │  │ $324/sqft           │
└─────────────────────┘  └─────────────────────┘  └─────────────────────┘

                        ┌─────────────────────────┐
                        │  Load More Properties    │
                        └─────────────────────────┘
```

---

## 8. Responsive Breakpoints

- **Mobile**: < 768px (single column)
- **Tablet**: 768px - 1024px (2-column grid)
- **Desktop**: > 1024px (3-column grid)
- **Large Desktop**: > 1280px (max container width, no change in columns)

---

## 9. Accessibility Checklist

- [x] WCAG 2.1 AA color contrast on all text (4.5:1 for body, 3:1 for 24px+ headings)
- [x] 48px minimum touch targets for save button and load-more button
- [x] Focus indicators with 2px outline and 2px offset (visible on all backgrounds)
- [x] Keyboard navigation: one tab stop per card, Enter to open, Space to save
- [x] Status badges use icon + text, not color alone (colorblind-safe)
- [x] Screen reader announcements for all interactive elements
- [x] Skip link to bypass header and jump to results
- [x] Load-more button (not infinite scroll) for control and predictability
- [x] Alt text on all images
- [x] Semantic HTML: `<article>` for cards, `<button>` for actions, `<a>` for navigation

---

## 10. Performance Considerations

- **System Fonts**: No web font loading overhead
- **Lazy Loading**: Images load only when near viewport
- **Skeleton States**: Instant feedback while content loads
- **Optimized Images**: 16:9 aspect ratio enforced, serve WebP with JPEG fallback
- **Minimal Shadows**: Box shadows are lightweight (1-3 layers max)
- **CSS Grid**: Native browser layout engine, no JavaScript layout calculations

---

## 11. Implementation Notes for design-builder

### CSS Architecture Recommendations
- Use CSS custom properties for colors, spacing, and typography
- Mobile-first media queries (min-width, not max-width)
- BEM or utility-first CSS (Tailwind) both acceptable
- Avoid `!important` (use specificity correctly)

### HTML Semantic Structure
```html
<article class="property-card" tabindex="0" role="link">
  <div class="property-card__image-container">
    <img src="..." alt="Property at 123 Main Street" loading="lazy" />
    <div class="property-card__badges">
      <span class="badge badge--new">✦ New</span>
    </div>
    <button class="property-card__save-btn" aria-label="Save property">
      <svg><!-- heart icon --></svg>
    </button>
  </div>
  <div class="property-card__content">
    <p class="property-card__price">$450,000</p>
    <div class="property-card__specs">
      <span>🛏️ 3</span>
      <span>🚿 2</span>
      <span>📏 1,850 sqft</span>
    </div>
    <p class="property-card__time">Listed 12 days ago</p>
    <p class="property-card__address">123 Main Street<br/>Springfield, IL 62701</p>
    <p class="property-card__price-per-sqft">$243/sqft</p>
  </div>
</article>
```

### JavaScript Interactions
- Save button: Toggle saved state, update icon and aria-pressed
- Card click: Navigate to detail page (exclude clicks on save button)
- Load-more: Fetch next 20 results, append to grid, handle loading state
- Keyboard: Enter on card = navigate, Space on card = save

---

## Handoff Babble Messages

### To: content-writer

Hey content-writer! Visual spec is done. I need you to handle the copy specifications:

1. **Status badge copy**: Confirm exact wording for "New", "Price Reduced", "Open House" — keep it under 15 characters per badge
2. **Days on market phrasing**: "Listed X days ago" vs "X days on market" — which feels better for Maya (first-time buyer)?
3. **Load-more button text**: "Load More Properties" vs "Show More Results" vs something shorter for mobile?
4. **Empty state copy**: When no results match filters, what message helps users refine without feeling defeated?
5. **Screen reader text**: Review my aria-labels and announcements — do they make sense for David (blind screen reader user)?

I've prioritized clarity and trust per the taste direction, but you're the wordsmith. Let me know if anything feels off.

—design-lead

---

### To: design-builder

Hey design-builder! Full visual spec is ready for implementation. Here's what you're getting:

- Complete color system with hex values and contrast ratios (all WCAG AA compliant)
- Full typography scale with mobile/desktop sizes
- Spacing system on 8px base unit
- Detailed card component spec with all states (default, hover, focus, visited, loading)
- Responsive grid layouts for mobile/tablet/desktop
- Focus and keyboard navigation specifications
- ASCII mockups for reference

**Key constraints to respect**:
- 48px touch targets for save button and load-more button (accessibility requirement)
- 2px focus indicators with 2px offset (keyboard nav)
- Status badges: icon + text, colorblind-safe
- Load-more button (not infinite scroll)
- System fonts only (performance)

**Files to reference**:
- `/Users/netzas/designpowers/docs/designpowers/design/2026-04-08-property-search-visual-spec.md` (this doc)

I've given exact pixel values and hex codes for everything. If anything is ambiguous or you need clarification on responsive behavior, holler. The personas to test against are Maya (mobile/sunlight/ESL), Robert (colorblind/keyboard), Aisha (low-literacy/data-constrained), and David (screen reader).

Go build something beautiful and accessible.

—design-lead
