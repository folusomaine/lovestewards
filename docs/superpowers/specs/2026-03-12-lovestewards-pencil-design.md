# Love Stewards — Pencil MCP Single-Page Design Spec
**Date:** 2026-03-12
**Status:** Approved

## Overview
A full single-page redesign of the Love Stewards website built in Pencil MCP. Adopts the dark editorial aesthetic from `design-style.html` across all 8 content sections. No emojis — icons/images only. Unsplash images used for all image slots.

---

## Design Tokens

| Token | Value |
|---|---|
| Background | `#1B1D22` |
| Text primary | `#E8E9EA` |
| Text secondary | `#8E929A` |
| Accent gold | `#CBA57A` |
| Card surface | `#252830` |
| Border subtle | `rgba(255,255,255,0.08)` |
| Ghost color | `rgba(255,255,255,0.02)` |
| Sidebar width | `65px` |
| Nav height | `100px` |
| Font | Plus Jakarta Sans (300/400/500/600/800) |

---

## Global Shell

### Persistent Left Sidebar (65px, fixed)
- Top: Instagram + TikTok SVG icons, `14px`, `#8E929A`, gold on hover
- Bottom: Vertical rotated contact info (phone numbers), `0.65rem`, uppercase, letter-spacing `0.1em`
- Right border: `1px solid rgba(255,255,255,0.08)`

### Top Navigation (100px, sticky)
- Left: "Love Stewards" logotype, `font-weight: 800`, `1.2rem`
- Center: Nav links — Home · About Us · Collections · Corporate · Journal · Contact (dot separators, `#8E929A`, active/hover `#E8E9EA`)
- Right: Search icon + Account icon (SVG, stroke style)

---

## Section 1 — Hero

**Layout:** 2-column grid (50/50). Full viewport height.

**Left — Content:**
- Ghost watermark: "GIFTING" at `13vw`, `rgba(255,255,255,0.02)`, absolute positioned
- Headline: *"Elevating the Art of Thoughtful Gifting."* — "Thoughtful Gifting." in gold (`#CBA57A`), `clamp(3rem, 4.5vw, 5rem)`, `font-weight: 400`
- Subtext: "Curated gift boxes designed to articulate your deepest sentiments...", `#8E929A`, `0.9rem`
- CTA 1: Arrow-circle button "Explore Gift Boxes" (primary)
- CTA 2: Ghost outline "Create a Custom Box"
- CTA 3: Text link "Get in Touch" — smooth scrolls to Contact section (Section 8)
- Bottom bar: Pagination `01 — Signature Boxes` + scroll navigation arrows

**Right — Visuals:**
- 4 vertical image slices, staggered heights (55vh, 80vh, 65vh, 50vh), `border-radius: 2px`
- Unsplash images: luxury gift boxes, ribbon details, perfume/fragrance, wrapped presents
- `filter: brightness(0.85) contrast(1.1)`, hover brightens
- Animate in with `clip-path: inset(100% 0 0 0)` reveal

**Effects:** fadeUpIn on text, sliceReveal on images, ghost watermark animation

---

## Section 2 — Occasions

**Layout:** 2-row × 3-column card grid. `min-height: 100vh`.

**Header:**
- Ghost watermark "OCCASIONS"
- Section label: "02 · Occasions", small uppercase gold
- Heading: "Gifts for Every Chapter of Life"

**Cards (6 total):**
- Birthdays · Weddings · Anniversaries · Corporate Gifting · Thank You Gifts · Just Because
- Card surface: `#252830`, `border-radius: 4px`
- Left border `2px solid transparent`, gold on hover
- Top: Unsplash image (relevant to occasion), `200px` height, `object-fit: cover`, slight dark overlay
- Body: Occasion name in serif italic (Playfair Display or similar), short descriptor in `#8E929A`
- Hover: image brightens, gold left border appears, subtle lift (`transform: translateY(-4px)`)

**Effects:** Staggered fade-in on scroll

---

## Section 3 — Signature Collections

**Layout:** 4-column row of tall portrait cards. `min-height: 100vh`.

**Header:**
- Ghost watermark "COLLECTIONS"
- Section label: "03 · Collections"
- Heading: "Our Signature Collections"

**Cards (4 total):** Celebration · Self-Care · Luxury Essentials · Corporate Appreciation
- Tall portrait format: `aspect-ratio: 3/4`
- Top 65%: Unsplash image (curated luxury items, self-care products, corporate gifts, celebration setup)
- Bottom 35%: Collection name, 1-line description, gold arrow link
- Gold badge top-right: collection tier label
- Hover: image scale `1.05`, card lifts

**Effects:** Image parallax on hover, staggered entrance

---

## Section 4 — Corporate & Bulk Orders

**Layout:** Asymmetric 2-column. Left 55% text, right 45% stacked image slices.

**Left:**
- Ghost watermark "CORPORATE"
- Section label: "04 · Corporate"
- Headline: "Elevated Corporate Gifting"
- 3 bullet points with gold dash prefix: volume orders, custom branding, white-glove delivery
- CTA button: "Enquire About Corporate Orders" with gold arrow

**Right:**
- 3 stacked image slices (smaller than hero), slightly offset
- Unsplash: branded packaging, corporate gift sets, elegant unboxing

**Effects:** Parallax offset on scroll for right image column

---

## Section 5 — Why Choose Love Stewards

**Layout:** 4-column icon+text grid.

**Header:**
- Ghost watermark "CRAFTED"
- Section label: "05 · Why Us"
- Heading: "Why Choose Love Stewards"

**Value Points (4):**
1. Hand-Curated Selection — SVG box/gift icon
2. Premium Packaging — SVG ribbon/package icon
3. Personal Touch — SVG heart/pen icon
4. Fast & Reliable Delivery — SVG delivery icon

Each: gold SVG icon `32px`, bold title, 2-line description in `#8E929A`. Thin horizontal rule separator below icons.

**Effects:** Icon gold glow on hover (`filter: drop-shadow`)

---

## Section 6 — How It Works

**Layout:** 3-step horizontal flow.

**Header:**
- Ghost watermark "PROCESS"
- Section label: "06 · Process"
- Heading: "Gifting Made Effortless"

**Steps (3):**
1. Choose Your Box
2. Personalise It
3. We Deliver the Joy

Each: Ghost step number (`10vw`, `opacity: 0.04`), SVG icon above, bold title, short description. Connected by thin gold dashed horizontal line.

**Effects:** Step numbers animate in large, line draws left-to-right on scroll

---

## Section 7 — Testimonials

**Layout:** Full-width dark strip, 3 testimonial cards side by side.

**Header:**
- Ghost watermark "LOVE"
- Section label: "07 · Testimonials"
- Heading: "What Our Clients Say"

**Cards (3):**
- Card 1 (Isreal): *"Love Stewards truly exceeded my expectations. Every item was carefully chosen and beautifully presented — it felt like they understood exactly what I wanted to say."* — Isreal, Wedding Gift
- Card 2 (placeholder): *"The most thoughtful corporate gifts we've ever sent. Our clients were genuinely moved. We'll be ordering again."* — Sarah M., Corporate Client
- Card 3 (placeholder): *"I ordered a birthday box last-minute and it arrived perfectly wrapped and on time. Absolutely stunning."* — Amara K., Birthday Gift
- Each: Oversized `"` in gold, star rating (5 gold dots/SVG stars), quote text, attribution name + occasion type
- Background: `#252830`, subtle gold top border

**Effects:** Horizontal scroll snap on mobile, fade-in on desktop

---

## Section 8 — Contact

**Layout:** 2-column. Left contact details, right contact form.

**Left:**
- Ghost watermark "HELLO"
- Section label: "08 · Contact"
- Heading: "Let's Create Something Special"
- Phone 1: 07947908615 (with phone SVG icon)
- Phone 2: 07442910982 (with phone SVG icon)
- WhatsApp QR placeholder (dark bordered box `150×150`, label "Scan to WhatsApp")
- Email: concierge@lovestewards.com (placeholder, with email SVG icon)

**Right — Form:**
- Dark inputs (`#252830`, `1px solid rgba(255,255,255,0.08)`, focus border gold)
- Fields: Name, Occasion Type (select), Message (textarea)
- Submit: Gold background button "Send Enquiry"

**Effects:** Input focus gold glow, form slide-in from right

---

## Footer

**Layout:** Single row, border-top `1px solid rgba(255,255,255,0.08)`, `80px` tall.

- Left: "Love Stewards" bold logotype
- Center: "Stewarding Meaningful Moments Through Thoughtful Gifting." in `#8E929A`, small
- Right: Instagram + TikTok SVG icons, gold on hover

---

## Unsplash Image Plan

| Section | Slot | Query |
|---|---|---|
| Hero | Slice 1 | luxury gift ribbon dark |
| Hero | Slice 2 | elegant perfume bottle dark |
| Hero | Slice 3 | premium gift box packaging |
| Hero | Slice 4 | moody floral texture dark |
| Occasions | Birthdays | birthday celebration luxury |
| Occasions | Weddings | wedding details elegant |
| Occasions | Anniversaries | romantic luxury setup |
| Occasions | Corporate | corporate gift premium |
| Occasions | Thank You | thank you gift elegant |
| Occasions | Just Because | flowers luxury minimal |
| Collections | Celebration | celebration gift set dark |
| Collections | Self-Care | skincare luxury flat lay |
| Collections | Luxury Essentials | luxury products minimal |
| Collections | Corporate | corporate branding premium |
| Corporate | Slice 1 | branded corporate packaging |
| Corporate | Slice 2 | corporate gift unboxing |
| Corporate | Slice 3 | luxury gift wrapping |

---

## Effects Summary

- **fadeUpIn:** All headings, descriptions, CTAs on scroll enter
- **sliceReveal:** `clip-path` reveal on all image slices
- **Ghost watermarks:** Large background text per section, `opacity: 0.02`
- **Card hover:** `translateY(-4px)` lift + gold border
- **Image hover:** `scale(1.05)` + brightness increase
- **Icon hover:** Gold `drop-shadow` glow
- **Form focus:** Gold border glow on inputs
- **Step line:** Draws left-to-right on scroll
- **Staggered entrance:** Cards animate in with delay offsets
