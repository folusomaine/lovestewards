# Love Stewards Pencil MCP Design Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a complete single-page Love Stewards website design in Pencil MCP using the dark editorial aesthetic from design-style.html, with all 8 content sections, Unsplash images, and scroll effects.

**Architecture:** Create a new .pen document, establish design variables (tokens), then build each section top-to-bottom as self-contained frames stacked vertically. Each section is a full-width frame with the persistent sidebar overlaid.

**Tech Stack:** Pencil MCP (batch_design, batch_get, get_guidelines, get_style_guide, get_variables, set_variables, get_screenshot), Unsplash CDN for images.

**Spec:** `docs/superpowers/specs/2026-03-12-lovestewards-pencil-design.md`

---

## Chunk 1: Setup — Document, Variables & Style Guide

### Task 1: Get Pencil guidelines and open document

- [ ] **Step 1: Get Pencil web-app guidelines**

Call: `get_guidelines(topic="web-app")`

- [ ] **Step 2: Get style guide tags**

Call: `get_style_guide_tags()`

- [ ] **Step 3: Get a dark luxury style guide**

Call: `get_style_guide(tags=["dark", "luxury", "editorial", "minimal"], name=null)`

- [ ] **Step 4: Open a new Pencil document**

Call: `open_document(filePathOrNew="new")`

- [ ] **Step 5: Set design variables (tokens)**

Call: `set_variables` with:
```json
{
  "bgColor": "#1B1D22",
  "textPrimary": "#E8E9EA",
  "textSecondary": "#8E929A",
  "accentGold": "#CBA57A",
  "cardSurface": "#252830",
  "borderSubtle": "rgba(255,255,255,0.08)",
  "sidebarWidth": "65",
  "navHeight": "100"
}
```

---

## Chunk 2: Global Shell — Sidebar & Navigation

### Task 2: Build persistent left sidebar

**Target:** Fixed 65px sidebar with social icons and vertical contact info

- [ ] **Step 1: Insert sidebar container**

```
sidebar=I("root", {
  type: "frame",
  name: "Sidebar",
  x: 0, y: 0,
  width: 65, height: 6680,
  fill: "#1B1D22",
  borderRight: "1px solid rgba(255,255,255,0.08)"
})
```

- [ ] **Step 2: Insert Instagram icon (top)**

```
ig=I("sidebar", {
  type: "icon",
  name: "Instagram",
  icon: "instagram",
  x: 25, y: 40,
  width: 14, height: 14,
  color: "#8E929A"
})
```

- [ ] **Step 3: Insert TikTok icon**

```
tt=I("sidebar", {
  type: "icon",
  name: "TikTok",
  icon: "tiktok",
  x: 25, y: 70,
  width: 14, height: 14,
  color: "#8E929A"
})
```

- [ ] **Step 4: Insert vertical phone numbers**

```
phone1=I("sidebar", {
  type: "text",
  name: "Phone1",
  text: "07947908615",
  x: 32, y: 6400,
  fontSize: 9,
  color: "#8E929A",
  rotation: -90,
  letterSpacing: 1.5,
  textTransform: "uppercase"
})
phone2=I("sidebar", {
  type: "text",
  name: "Phone2",
  text: "07442910982",
  x: 32, y: 6520,
  fontSize: 9,
  color: "#8E929A",
  rotation: -90,
  letterSpacing: 1.5,
  textTransform: "uppercase"
})
```

- [ ] **Step 5: Take screenshot to verify sidebar**

Call: `get_screenshot` on sidebar node

### Task 3: Build top navigation bar

**Target:** 100px sticky nav — logo left, links center, icons right

- [ ] **Step 1: Insert nav container**

```
nav=I("root", {
  type: "frame",
  name: "Navigation",
  x: 65, y: 0,
  width: 1375, height: 100,
  fill: "#1B1D22",
  borderBottom: "1px solid rgba(255,255,255,0.08)"
})
```

- [ ] **Step 2: Insert logo**

```
logo=I("nav", {
  type: "text",
  name: "Logo",
  text: "Love Stewards",
  x: 64, y: 35,
  fontSize: 19,
  fontWeight: 800,
  color: "#E8E9EA",
  letterSpacing: -0.3
})
```

- [ ] **Step 3: Insert nav links**

```
navlinks=I("nav", {
  type: "text",
  name: "NavLinks",
  text: "Home  ·  About Us  ·  Collections  ·  Corporate  ·  Journal  ·  Contact",
  x: 400, y: 38,
  fontSize: 12,
  fontWeight: 500,
  color: "#8E929A",
  letterSpacing: 0
})
```

- [ ] **Step 4: Insert search + account icons**

```
search=I("nav", {
  type: "icon",
  name: "Search",
  icon: "search",
  x: 1290, y: 38,
  width: 16, height: 16,
  color: "#E8E9EA"
})
account=I("nav", {
  type: "icon",
  name: "Account",
  icon: "user",
  x: 1320, y: 38,
  width: 16, height: 16,
  color: "#E8E9EA"
})
```

- [ ] **Step 5: Screenshot nav**

Call: `get_screenshot` on nav node

---

## Chunk 3: Section 1 — Hero

### Task 4: Build hero section frame and ghost watermark

- [ ] **Step 1: Insert hero section frame**

```
hero=I("root", {
  type: "frame",
  name: "Hero",
  x: 65, y: 100,
  width: 1375, height: 900,
  fill: "#1B1D22"
})
```

- [ ] **Step 2: Insert ghost watermark "GIFTING"**

```
watermark=I("hero", {
  type: "text",
  name: "Watermark",
  text: "GIFTING",
  x: 30, y: 120,
  fontSize: 180,
  fontWeight: 800,
  color: "rgba(255,255,255,0.025)",
  letterSpacing: -3,
  textTransform: "uppercase"
})
```

### Task 5: Build hero left content

- [ ] **Step 1: Insert headline**

```
h1=I("hero", {
  type: "text",
  name: "Headline",
  text: "Elevating the Art of",
  x: 64, y: 280,
  fontSize: 58,
  fontWeight: 400,
  color: "#E8E9EA",
  lineHeight: 1.1,
  letterSpacing: -0.5
})
h1gold=I("hero", {
  type: "text",
  name: "HeadlineGold",
  text: "Thoughtful Gifting.",
  x: 64, y: 348,
  fontSize: 58,
  fontWeight: 600,
  color: "#CBA57A",
  lineHeight: 1.1,
  letterSpacing: -0.5
})
```

- [ ] **Step 2: Insert subtext**

```
sub=I("hero", {
  type: "text",
  name: "HeroSubtext",
  text: "Curated gift boxes designed to articulate your deepest sentiments. From intimate weddings to corporate milestones, every detail is hand-selected to create an unforgettable unboxing experience.",
  x: 64, y: 450,
  width: 420,
  fontSize: 14,
  fontWeight: 400,
  color: "#8E929A",
  lineHeight: 1.7
})
```

- [ ] **Step 3: Insert CTA 1 — Explore Gift Boxes**

```
cta1bg=I("hero", {
  type: "frame",
  name: "CTA1",
  x: 64, y: 570,
  width: 200, height: 44,
  fill: "rgba(255,255,255,0.03)",
  borderRadius: 22,
  border: "1px solid rgba(255,255,255,0.08)"
})
cta1icon=I("cta1bg", {
  type: "icon",
  name: "CTA1Arrow",
  icon: "arrow-right",
  x: 12, y: 14,
  width: 16, height: 16,
  color: "#CBA57A"
})
cta1text=I("cta1bg", {
  type: "text",
  name: "CTA1Text",
  text: "Explore Gift Boxes",
  x: 38, y: 13,
  fontSize: 12,
  fontWeight: 600,
  color: "#E8E9EA",
  letterSpacing: 1.5,
  textTransform: "uppercase"
})
```

- [ ] **Step 4: Insert CTA 2 — Create a Custom Box**

```
cta2=I("hero", {
  type: "text",
  name: "CTA2",
  text: "Create a Custom Box",
  x: 64, y: 632,
  fontSize: 12,
  fontWeight: 500,
  color: "#8E929A",
  letterSpacing: 1,
  textTransform: "uppercase",
  textDecoration: "underline"
})
```

- [ ] **Step 5: Insert CTA 3 — Get in Touch**

```
cta3=I("hero", {
  type: "text",
  name: "CTA3",
  text: "Get in Touch →",
  x: 64, y: 665,
  fontSize: 12,
  fontWeight: 500,
  color: "#CBA57A",
  letterSpacing: 1,
  textTransform: "uppercase"
})
```

### Task 6: Build hero right — image slices

- [ ] **Step 1: Fetch hero Unsplash images and insert slices**

```
slice1=I("hero", {
  type: "image",
  name: "HeroSlice1",
  src: "https://images.unsplash.com/photo-1549465220-1a8b9238cd48?auto=format&fit=crop&w=300&h=500&q=80",
  x: 720, y: 200,
  width: 140, height: 495,
  borderRadius: 2,
  objectFit: "cover"
})
slice2=I("hero", {
  type: "image",
  name: "HeroSlice2",
  src: "https://images.unsplash.com/photo-1599305090598-fe179d501227?auto=format&fit=crop&w=300&h=720&q=80",
  x: 875, y: 45,
  width: 140, height: 720,
  borderRadius: 2,
  objectFit: "cover"
})
slice3=I("hero", {
  type: "image",
  name: "HeroSlice3",
  src: "https://images.unsplash.com/photo-1605282717367-5d5d852cc5eb?auto=format&fit=crop&w=300&h=585&q=80",
  x: 1030, y: 140,
  width: 140, height: 585,
  borderRadius: 2,
  objectFit: "cover"
})
slice4=I("hero", {
  type: "image",
  name: "HeroSlice4",
  src: "https://images.unsplash.com/photo-1614030424754-24d0eebd46b2?auto=format&fit=crop&w=300&h=450&q=80",
  x: 1185, y: 260,
  width: 140, height: 450,
  borderRadius: 2,
  objectFit: "cover"
})
```

- [ ] **Step 2: Insert bottom pagination bar**

```
pagenum=I("hero", {
  type: "text",
  name: "PageNum",
  text: "01",
  x: 64, y: 840,
  fontSize: 11,
  color: "#E8E9EA",
  letterSpacing: 1
})
pageline=I("hero", {
  type: "rectangle",
  name: "PageLine",
  x: 96, y: 851,
  width: 60, height: 1,
  fill: "rgba(255,255,255,0.15)"
})
pagelabel=I("hero", {
  type: "text",
  name: "PageLabel",
  text: "Signature Boxes",
  x: 166, y: 840,
  fontSize: 11,
  color: "#8E929A",
  letterSpacing: 1
})
scrolllabel=I("hero", {
  type: "text",
  name: "ScrollLabel",
  text: "Scroll",
  x: 1200, y: 840,
  fontSize: 10,
  color: "#8E929A",
  letterSpacing: 2,
  textTransform: "uppercase"
})
```

- [ ] **Step 3: Screenshot hero section**

Call: `get_screenshot` on hero node

---

## Chunk 4: Section 2 — Occasions

### Task 7: Build occasions section

- [ ] **Step 1: Insert occasions frame**

```
occasions=I("root", {
  type: "frame",
  name: "Occasions",
  x: 65, y: 1000,
  width: 1375, height: 900,
  fill: "#1B1D22"
})
```

- [ ] **Step 2: Ghost watermark + header**

```
wm2=I("occasions", {
  type: "text",
  name: "Watermark2",
  text: "OCCASIONS",
  x: -20, y: 60,
  fontSize: 140,
  fontWeight: 800,
  color: "rgba(255,255,255,0.02)",
  letterSpacing: -2,
  textTransform: "uppercase"
})
seclabel2=I("occasions", {
  type: "text",
  name: "SectionLabel2",
  text: "02 · OCCASIONS",
  x: 64, y: 80,
  fontSize: 11,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 3,
  textTransform: "uppercase"
})
h2=I("occasions", {
  type: "text",
  name: "OccasionsHeading",
  text: "Gifts for Every Chapter of Life",
  x: 64, y: 110,
  fontSize: 40,
  fontWeight: 400,
  color: "#E8E9EA",
  letterSpacing: -0.5
})
```

- [ ] **Step 3: Insert 6 occasion cards (row 1: Birthdays, Weddings, Anniversaries)**

```
card1=I("occasions", {
  type: "frame",
  name: "CardBirthdays",
  x: 64, y: 200,
  width: 400, height: 280,
  fill: "#252830",
  borderRadius: 4,
  borderLeft: "2px solid transparent"
})
img1=I("card1", {
  type: "image",
  name: "CardImg1",
  src: "https://images.unsplash.com/photo-1558618666-fcd25c85cd64?auto=format&fit=crop&w=800&h=400&q=80",
  x: 0, y: 0,
  width: 400, height: 160,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
title1=I("card1", {
  type: "text",
  name: "CardTitle1",
  text: "Birthdays",
  x: 20, y: 175,
  fontSize: 20,
  fontWeight: 400,
  color: "#E8E9EA",
  fontStyle: "italic"
})
desc1=I("card1", {
  type: "text",
  name: "CardDesc1",
  text: "Make their day unforgettable",
  x: 20, y: 204,
  fontSize: 13,
  color: "#8E929A"
})

card2=I("occasions", {
  type: "frame",
  name: "CardWeddings",
  x: 489, y: 200,
  width: 400, height: 280,
  fill: "#252830",
  borderRadius: 4
})
img2=I("card2", {
  type: "image",
  name: "CardImg2",
  src: "https://images.unsplash.com/photo-1519741497674-611481863552?auto=format&fit=crop&w=800&h=400&q=80",
  x: 0, y: 0,
  width: 400, height: 160,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
title2=I("card2", {
  type: "text",
  name: "CardTitle2",
  text: "Weddings",
  x: 20, y: 175,
  fontSize: 20,
  fontWeight: 400,
  color: "#E8E9EA",
  fontStyle: "italic"
})
desc2=I("card2", {
  type: "text",
  name: "CardDesc2",
  text: "Celebrate the union in style",
  x: 20, y: 204,
  fontSize: 13,
  color: "#8E929A"
})

card3=I("occasions", {
  type: "frame",
  name: "CardAnniversaries",
  x: 914, y: 200,
  width: 400, height: 280,
  fill: "#252830",
  borderRadius: 4
})
img3=I("card3", {
  type: "image",
  name: "CardImg3",
  src: "https://images.unsplash.com/photo-1518199266791-5375a83190b7?auto=format&fit=crop&w=800&h=400&q=80",
  x: 0, y: 0,
  width: 400, height: 160,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
title3=I("card3", {
  type: "text",
  name: "CardTitle3",
  text: "Anniversaries",
  x: 20, y: 175,
  fontSize: 20,
  fontWeight: 400,
  color: "#E8E9EA",
  fontStyle: "italic"
})
desc3=I("card3", {
  type: "text",
  name: "CardDesc3",
  text: "Honour milestones with meaning",
  x: 20, y: 204,
  fontSize: 13,
  color: "#8E929A"
})
```

- [ ] **Step 4: Insert 6 occasion cards (row 2: Corporate, Thank You, Just Because)**

```
card4=I("occasions", {
  type: "frame",
  name: "CardCorporate",
  x: 64, y: 510,
  width: 400, height: 280,
  fill: "#252830",
  borderRadius: 4
})
img4=I("card4", {
  type: "image",
  name: "CardImg4",
  src: "https://images.unsplash.com/photo-1600880292203-757bb62b4baf?auto=format&fit=crop&w=800&h=400&q=80",
  x: 0, y: 0,
  width: 400, height: 160,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
title4=I("card4", {
  type: "text",
  name: "CardTitle4",
  text: "Corporate Gifting",
  x: 20, y: 175,
  fontSize: 20,
  fontWeight: 400,
  color: "#E8E9EA",
  fontStyle: "italic"
})
desc4=I("card4", {
  type: "text",
  name: "CardDesc4",
  text: "Impress clients and reward teams",
  x: 20, y: 204,
  fontSize: 13,
  color: "#8E929A"
})

card5=I("occasions", {
  type: "frame",
  name: "CardThankYou",
  x: 489, y: 510,
  width: 400, height: 280,
  fill: "#252830",
  borderRadius: 4
})
img5=I("card5", {
  type: "image",
  name: "CardImg5",
  src: "https://images.unsplash.com/photo-1607344645866-009c320b63e0?auto=format&fit=crop&w=800&h=400&q=80",
  x: 0, y: 0,
  width: 400, height: 160,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
title5=I("card5", {
  type: "text",
  name: "CardTitle5",
  text: "Thank You Gifts",
  x: 20, y: 175,
  fontSize: 20,
  fontWeight: 400,
  color: "#E8E9EA",
  fontStyle: "italic"
})
desc5=I("card5", {
  type: "text",
  name: "CardDesc5",
  text: "Express gratitude beautifully",
  x: 20, y: 204,
  fontSize: 13,
  color: "#8E929A"
})

card6=I("occasions", {
  type: "frame",
  name: "CardJustBecause",
  x: 914, y: 510,
  width: 400, height: 280,
  fill: "#252830",
  borderRadius: 4
})
img6=I("card6", {
  type: "image",
  name: "CardImg6",
  src: "https://images.unsplash.com/photo-1487530811015-780b67a41978?auto=format&fit=crop&w=800&h=400&q=80",
  x: 0, y: 0,
  width: 400, height: 160,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
title6=I("card6", {
  type: "text",
  name: "CardTitle6",
  text: "Just Because",
  x: 20, y: 175,
  fontSize: 20,
  fontWeight: 400,
  color: "#E8E9EA",
  fontStyle: "italic"
})
desc6=I("card6", {
  type: "text",
  name: "CardDesc6",
  text: "No reason needed to show love",
  x: 20, y: 204,
  fontSize: 13,
  color: "#8E929A"
})
```

- [ ] **Step 5: Screenshot occasions section**

Call: `get_screenshot` on occasions node

---

## Chunk 5: Section 3 — Signature Collections

### Task 8: Build collections section

- [ ] **Step 1: Insert collections frame + header**

```
collections=I("root", {
  type: "frame",
  name: "Collections",
  x: 65, y: 1900,
  width: 1375, height: 900,
  fill: "#1B1D22"
})
wm3=I("collections", {
  type: "text",
  name: "Watermark3",
  text: "COLLECTIONS",
  x: -30, y: 60,
  fontSize: 120,
  fontWeight: 800,
  color: "rgba(255,255,255,0.02)",
  letterSpacing: -2
})
seclabel3=I("collections", {
  type: "text",
  name: "SectionLabel3",
  text: "03 · COLLECTIONS",
  x: 64, y: 80,
  fontSize: 11,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 3
})
h3=I("collections", {
  type: "text",
  name: "CollectionsHeading",
  text: "Our Signature Collections",
  x: 64, y: 110,
  fontSize: 40,
  fontWeight: 400,
  color: "#E8E9EA",
  letterSpacing: -0.5
})
```

- [ ] **Step 2: Insert 4 portrait collection cards**

```
col1=I("collections", {
  type: "frame",
  name: "CollCelebration",
  x: 64, y: 200,
  width: 295, height: 600,
  fill: "#252830",
  borderRadius: 4
})
colimg1=I("col1", {
  type: "image",
  name: "ColImg1",
  src: "https://images.unsplash.com/photo-1549465220-1a8b9238cd48?auto=format&fit=crop&w=600&h=800&q=80",
  x: 0, y: 0,
  width: 295, height: 390,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
colbadge1=I("col1", {
  type: "text",
  name: "Badge1",
  text: "SIGNATURE",
  x: 200, y: 14,
  fontSize: 8,
  fontWeight: 700,
  color: "#CBA57A",
  letterSpacing: 2
})
coltitle1=I("col1", {
  type: "text",
  name: "ColTitle1",
  text: "Celebration",
  x: 20, y: 415,
  fontSize: 22,
  fontWeight: 600,
  color: "#E8E9EA"
})
coldesc1=I("col1", {
  type: "text",
  name: "ColDesc1",
  text: "For every milestone worth marking",
  x: 20, y: 446,
  fontSize: 13,
  color: "#8E929A"
})
colarrow1=I("col1", {
  type: "text",
  name: "ColArrow1",
  text: "Explore →",
  x: 20, y: 490,
  fontSize: 12,
  color: "#CBA57A",
  letterSpacing: 1
})

col2=I("collections", {
  type: "frame",
  name: "CollSelfCare",
  x: 383, y: 200,
  width: 295, height: 600,
  fill: "#252830",
  borderRadius: 4
})
colimg2=I("col2", {
  type: "image",
  name: "ColImg2",
  src: "https://images.unsplash.com/photo-1571781926291-c477ebfd024b?auto=format&fit=crop&w=600&h=800&q=80",
  x: 0, y: 0,
  width: 295, height: 390,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
coltitle2=I("col2", {
  type: "text",
  name: "ColTitle2",
  text: "Self-Care",
  x: 20, y: 415,
  fontSize: 22,
  fontWeight: 600,
  color: "#E8E9EA"
})
coldesc2=I("col2", {
  type: "text",
  name: "ColDesc2",
  text: "Indulge in everyday luxury",
  x: 20, y: 446,
  fontSize: 13,
  color: "#8E929A"
})
colarrow2=I("col2", {
  type: "text",
  name: "ColArrow2",
  text: "Explore →",
  x: 20, y: 490,
  fontSize: 12,
  color: "#CBA57A",
  letterSpacing: 1
})

col3=I("collections", {
  type: "frame",
  name: "CollLuxury",
  x: 702, y: 200,
  width: 295, height: 600,
  fill: "#252830",
  borderRadius: 4
})
colimg3=I("col3", {
  type: "image",
  name: "ColImg3",
  src: "https://images.unsplash.com/photo-1523275335684-37898b6baf30?auto=format&fit=crop&w=600&h=800&q=80",
  x: 0, y: 0,
  width: 295, height: 390,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
coltitle3=I("col3", {
  type: "text",
  name: "ColTitle3",
  text: "Luxury Essentials",
  x: 20, y: 415,
  fontSize: 22,
  fontWeight: 600,
  color: "#E8E9EA"
})
coldesc3=I("col3", {
  type: "text",
  name: "ColDesc3",
  text: "Premium quality, curated with care",
  x: 20, y: 446,
  fontSize: 13,
  color: "#8E929A"
})
colarrow3=I("col3", {
  type: "text",
  name: "ColArrow3",
  text: "Explore →",
  x: 20, y: 490,
  fontSize: 12,
  color: "#CBA57A",
  letterSpacing: 1
})

col4=I("collections", {
  type: "frame",
  name: "CollCorporateApp",
  x: 1021, y: 200,
  width: 295, height: 600,
  fill: "#252830",
  borderRadius: 4
})
colimg4=I("col4", {
  type: "image",
  name: "ColImg4",
  src: "https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?auto=format&fit=crop&w=600&h=800&q=80",
  x: 0, y: 0,
  width: 295, height: 390,
  objectFit: "cover",
  borderRadius: "4px 4px 0 0"
})
coltitle4=I("col4", {
  type: "text",
  name: "ColTitle4",
  text: "Corporate Appreciation",
  x: 20, y: 415,
  fontSize: 20,
  fontWeight: 600,
  color: "#E8E9EA"
})
coldesc4=I("col4", {
  type: "text",
  name: "ColDesc4",
  text: "Elevate professional relationships",
  x: 20, y: 452,
  fontSize: 13,
  color: "#8E929A"
})
colarrow4=I("col4", {
  type: "text",
  name: "ColArrow4",
  text: "Explore →",
  x: 20, y: 490,
  fontSize: 12,
  color: "#CBA57A",
  letterSpacing: 1
})
```

- [ ] **Step 3: Screenshot collections section**

Call: `get_screenshot` on collections node

---

## Chunk 6: Sections 4 & 5 — Corporate and Why Us

### Task 9: Build corporate section

- [ ] **Step 1: Insert corporate frame + left content**

```
corp=I("root", {
  type: "frame",
  name: "Corporate",
  x: 65, y: 2800,
  width: 1375, height: 900,
  fill: "#1B1D22"
})
wm4=I("corp", {
  type: "text",
  name: "Watermark4",
  text: "CORPORATE",
  x: -10, y: 60,
  fontSize: 150,
  fontWeight: 800,
  color: "rgba(255,255,255,0.02)",
  letterSpacing: -2
})
seclabel4=I("corp", {
  type: "text",
  name: "SectionLabel4",
  text: "04 · CORPORATE",
  x: 64, y: 200,
  fontSize: 11,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 3
})
corpheading=I("corp", {
  type: "text",
  name: "CorpHeading",
  text: "Elevated\nCorporate\nGifting",
  x: 64, y: 240,
  fontSize: 52,
  fontWeight: 400,
  color: "#E8E9EA",
  lineHeight: 1.1,
  letterSpacing: -0.5
})
bullet1=I("corp", {
  type: "text",
  name: "Bullet1",
  text: "— Volume orders with premium pricing",
  x: 64, y: 450,
  fontSize: 15,
  color: "#8E929A"
})
bullet2=I("corp", {
  type: "text",
  name: "Bullet2",
  text: "— Custom branding & personalisation",
  x: 64, y: 478,
  fontSize: 15,
  color: "#8E929A"
})
bullet3=I("corp", {
  type: "text",
  name: "Bullet3",
  text: "— White-glove delivery to any address",
  x: 64, y: 506,
  fontSize: 15,
  color: "#8E929A"
})
corpcta=I("corp", {
  type: "frame",
  name: "CorpCTA",
  x: 64, y: 580,
  width: 300, height: 52,
  fill: "#CBA57A",
  borderRadius: 2
})
corpctatext=I("corpcta", {
  type: "text",
  name: "CorpCTAText",
  text: "Enquire About Corporate Orders →",
  x: 20, y: 16,
  fontSize: 12,
  fontWeight: 700,
  color: "#1B1D22",
  letterSpacing: 0.5
})
```

- [ ] **Step 2: Insert right image slices for corporate**

```
cslice1=I("corp", {
  type: "image",
  name: "CorpSlice1",
  src: "https://images.unsplash.com/photo-1553531384-397c80973a0b?auto=format&fit=crop&w=300&h=400&q=80",
  x: 800, y: 150,
  width: 160, height: 400,
  borderRadius: 2,
  objectFit: "cover"
})
cslice2=I("corp", {
  type: "image",
  name: "CorpSlice2",
  src: "https://images.unsplash.com/photo-1578985545062-69928b1d9587?auto=format&fit=crop&w=300&h=500&q=80",
  x: 980, y: 100,
  width: 160, height: 500,
  borderRadius: 2,
  objectFit: "cover"
})
cslice3=I("corp", {
  type: "image",
  name: "CorpSlice3",
  src: "https://images.unsplash.com/photo-1607082349566-187342175e2f?auto=format&fit=crop&w=300&h=350&q=80",
  x: 1160, y: 200,
  width: 160, height: 350,
  borderRadius: 2,
  objectFit: "cover"
})
```

- [ ] **Step 3: Screenshot corporate section**

Call: `get_screenshot` on corp node

### Task 10: Build Why Choose Us section

- [ ] **Step 1: Insert Why Us frame + header**

```
whyus=I("root", {
  type: "frame",
  name: "WhyUs",
  x: 65, y: 3700,
  width: 1375, height: 700,
  fill: "#1B1D22"
})
wm5=I("whyus", {
  type: "text",
  name: "Watermark5",
  text: "CRAFTED",
  x: 0, y: 40,
  fontSize: 160,
  fontWeight: 800,
  color: "rgba(255,255,255,0.02)",
  letterSpacing: -2
})
seclabel5=I("whyus", {
  type: "text",
  name: "SectionLabel5",
  text: "05 · WHY US",
  x: 64, y: 120,
  fontSize: 11,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 3
})
whyheading=I("whyus", {
  type: "text",
  name: "WhyHeading",
  text: "Why Choose Love Stewards",
  x: 64, y: 152,
  fontSize: 40,
  fontWeight: 400,
  color: "#E8E9EA",
  letterSpacing: -0.5
})
divider=I("whyus", {
  type: "rectangle",
  name: "Divider",
  x: 64, y: 220,
  width: 1245, height: 1,
  fill: "rgba(255,255,255,0.08)"
})
```

- [ ] **Step 2: Insert 4 value point columns**

```
vp1icon=I("whyus", {
  type: "icon",
  name: "VP1Icon",
  icon: "gift",
  x: 64, y: 260,
  width: 32, height: 32,
  color: "#CBA57A"
})
vp1title=I("whyus", {
  type: "text",
  name: "VP1Title",
  text: "Hand-Curated\nSelection",
  x: 64, y: 310,
  fontSize: 18,
  fontWeight: 700,
  color: "#E8E9EA",
  lineHeight: 1.3
})
vp1desc=I("whyus", {
  type: "text",
  name: "VP1Desc",
  text: "Every item is thoughtfully chosen by our expert team",
  x: 64, y: 368,
  width: 260,
  fontSize: 13,
  color: "#8E929A",
  lineHeight: 1.6
})

vp2icon=I("whyus", {
  type: "icon",
  name: "VP2Icon",
  icon: "package",
  x: 380, y: 260,
  width: 32, height: 32,
  color: "#CBA57A"
})
vp2title=I("whyus", {
  type: "text",
  name: "VP2Title",
  text: "Premium\nPackaging",
  x: 380, y: 310,
  fontSize: 18,
  fontWeight: 700,
  color: "#E8E9EA",
  lineHeight: 1.3
})
vp2desc=I("whyus", {
  type: "text",
  name: "VP2Desc",
  text: "Luxurious presentation that elevates every unboxing",
  x: 380, y: 368,
  width: 260,
  fontSize: 13,
  color: "#8E929A",
  lineHeight: 1.6
})

vp3icon=I("whyus", {
  type: "icon",
  name: "VP3Icon",
  icon: "heart",
  x: 700, y: 260,
  width: 32, height: 32,
  color: "#CBA57A"
})
vp3title=I("whyus", {
  type: "text",
  name: "VP3Title",
  text: "Personal\nTouch",
  x: 700, y: 310,
  fontSize: 18,
  fontWeight: 700,
  color: "#E8E9EA",
  lineHeight: 1.3
})
vp3desc=I("whyus", {
  type: "text",
  name: "VP3Desc",
  text: "Custom messages and personalisation for every order",
  x: 700, y: 368,
  width: 260,
  fontSize: 13,
  color: "#8E929A",
  lineHeight: 1.6
})

vp4icon=I("whyus", {
  type: "icon",
  name: "VP4Icon",
  icon: "truck",
  x: 1020, y: 260,
  width: 32, height: 32,
  color: "#CBA57A"
})
vp4title=I("whyus", {
  type: "text",
  name: "VP4Title",
  text: "Fast & Reliable\nDelivery",
  x: 1020, y: 310,
  fontSize: 18,
  fontWeight: 700,
  color: "#E8E9EA",
  lineHeight: 1.3
})
vp4desc=I("whyus", {
  type: "text",
  name: "VP4Desc",
  text: "Prompt, careful delivery anywhere in the UK",
  x: 1020, y: 368,
  width: 260,
  fontSize: 13,
  color: "#8E929A",
  lineHeight: 1.6
})
```

- [ ] **Step 3: Screenshot Why Us section**

Call: `get_screenshot` on whyus node

---

## Chunk 7: Sections 6 & 7 — How It Works & Testimonials

### Task 11: Build How It Works section

- [ ] **Step 1: Insert frame + header**

```
hiw=I("root", {
  type: "frame",
  name: "HowItWorks",
  x: 65, y: 4400,
  width: 1375, height: 700,
  fill: "#1B1D22"
})
wm6=I("hiw", {
  type: "text",
  name: "Watermark6",
  text: "PROCESS",
  x: 0, y: 50,
  fontSize: 160,
  fontWeight: 800,
  color: "rgba(255,255,255,0.02)",
  letterSpacing: -2
})
seclabel6=I("hiw", {
  type: "text",
  name: "SectionLabel6",
  text: "06 · PROCESS",
  x: 64, y: 120,
  fontSize: 11,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 3
})
hiwheading=I("hiw", {
  type: "text",
  name: "HIWHeading",
  text: "Gifting Made Effortless",
  x: 64, y: 152,
  fontSize: 40,
  fontWeight: 400,
  color: "#E8E9EA",
  letterSpacing: -0.5
})
stepline=I("hiw", {
  type: "rectangle",
  name: "StepLine",
  x: 64, y: 380,
  width: 1245, height: 1,
  fill: "#CBA57A",
  opacity: 0.3
})
```

- [ ] **Step 2: Insert 3 steps**

```
step1num=I("hiw", {
  type: "text",
  name: "Step1Num",
  text: "01",
  x: 64, y: 250,
  fontSize: 120,
  fontWeight: 800,
  color: "rgba(255,255,255,0.04)",
  letterSpacing: -2
})
step1icon=I("hiw", {
  type: "icon",
  name: "Step1Icon",
  icon: "shopping-bag",
  x: 64, y: 340,
  width: 28, height: 28,
  color: "#CBA57A"
})
step1title=I("hiw", {
  type: "text",
  name: "Step1Title",
  text: "Choose Your Box",
  x: 64, y: 400,
  fontSize: 20,
  fontWeight: 700,
  color: "#E8E9EA"
})
step1desc=I("hiw", {
  type: "text",
  name: "Step1Desc",
  text: "Browse our curated collections\nor build your own custom box",
  x: 64, y: 432,
  fontSize: 13,
  color: "#8E929A",
  lineHeight: 1.6
})

step2num=I("hiw", {
  type: "text",
  name: "Step2Num",
  text: "02",
  x: 490, y: 250,
  fontSize: 120,
  fontWeight: 800,
  color: "rgba(255,255,255,0.04)",
  letterSpacing: -2
})
step2icon=I("hiw", {
  type: "icon",
  name: "Step2Icon",
  icon: "edit-3",
  x: 490, y: 340,
  width: 28, height: 28,
  color: "#CBA57A"
})
step2title=I("hiw", {
  type: "text",
  name: "Step2Title",
  text: "Personalise It",
  x: 490, y: 400,
  fontSize: 20,
  fontWeight: 700,
  color: "#E8E9EA"
})
step2desc=I("hiw", {
  type: "text",
  name: "Step2Desc",
  text: "Add a personal message, choose\nwrapping, and any add-ons",
  x: 490, y: 432,
  fontSize: 13,
  color: "#8E929A",
  lineHeight: 1.6
})

step3num=I("hiw", {
  type: "text",
  name: "Step3Num",
  text: "03",
  x: 920, y: 250,
  fontSize: 120,
  fontWeight: 800,
  color: "rgba(255,255,255,0.04)",
  letterSpacing: -2
})
step3icon=I("hiw", {
  type: "icon",
  name: "Step3Icon",
  icon: "truck",
  x: 920, y: 340,
  width: 28, height: 28,
  color: "#CBA57A"
})
step3title=I("hiw", {
  type: "text",
  name: "Step3Title",
  text: "We Deliver the Joy",
  x: 920, y: 400,
  fontSize: 20,
  fontWeight: 700,
  color: "#E8E9EA"
})
step3desc=I("hiw", {
  type: "text",
  name: "Step3Desc",
  text: "We handle the rest — packed with\ncare and delivered with love",
  x: 920, y: 432,
  fontSize: 13,
  color: "#8E929A",
  lineHeight: 1.6
})
```

- [ ] **Step 2: Screenshot How It Works section**

Call: `get_screenshot` on hiw node

### Task 12: Build Testimonials section

- [ ] **Step 1: Insert testimonials frame + header**

```
testi=I("root", {
  type: "frame",
  name: "Testimonials",
  x: 65, y: 5100,
  width: 1375, height: 700,
  fill: "#1B1D22"
})
wm7=I("testi", {
  type: "text",
  name: "Watermark7",
  text: "LOVE",
  x: 200, y: 40,
  fontSize: 200,
  fontWeight: 800,
  color: "rgba(255,255,255,0.02)",
  letterSpacing: -3
})
seclabel7=I("testi", {
  type: "text",
  name: "SectionLabel7",
  text: "07 · TESTIMONIALS",
  x: 64, y: 100,
  fontSize: 11,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 3
})
testiheading=I("testi", {
  type: "text",
  name: "TestiHeading",
  text: "What Our Clients Say",
  x: 64, y: 132,
  fontSize: 40,
  fontWeight: 400,
  color: "#E8E9EA",
  letterSpacing: -0.5
})
```

- [ ] **Step 2: Insert 3 testimonial cards**

```
tc1=I("testi", {
  type: "frame",
  name: "TestiCard1",
  x: 64, y: 220,
  width: 400, height: 340,
  fill: "#252830",
  borderRadius: 4,
  borderTop: "2px solid #CBA57A"
})
tquote1=I("tc1", {
  type: "text",
  name: "TQuote1Mark",
  text: "\"",
  x: 20, y: 10,
  fontSize: 60,
  fontWeight: 800,
  color: "#CBA57A",
  lineHeight: 1
})
ttext1=I("tc1", {
  type: "text",
  name: "TText1",
  text: "Love Stewards truly exceeded my expectations. Every item was carefully chosen and beautifully presented — it felt like they understood exactly what I wanted to say.",
  x: 20, y: 70,
  width: 360,
  fontSize: 14,
  color: "#E8E9EA",
  lineHeight: 1.7,
  fontStyle: "italic"
})
tname1=I("tc1", {
  type: "text",
  name: "TName1",
  text: "Isreal · Wedding Gift",
  x: 20, y: 290,
  fontSize: 12,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 1
})

tc2=I("testi", {
  type: "frame",
  name: "TestiCard2",
  x: 489, y: 220,
  width: 400, height: 340,
  fill: "#252830",
  borderRadius: 4,
  borderTop: "2px solid rgba(203,165,122,0.3)"
})
tquote2=I("tc2", {
  type: "text",
  name: "TQuote2Mark",
  text: "\"",
  x: 20, y: 10,
  fontSize: 60,
  fontWeight: 800,
  color: "#CBA57A",
  lineHeight: 1
})
ttext2=I("tc2", {
  type: "text",
  name: "TText2",
  text: "The most thoughtful corporate gifts we've ever sent. Our clients were genuinely moved. We'll be ordering again without question.",
  x: 20, y: 70,
  width: 360,
  fontSize: 14,
  color: "#E8E9EA",
  lineHeight: 1.7,
  fontStyle: "italic"
})
tname2=I("tc2", {
  type: "text",
  name: "TName2",
  text: "Sarah M. · Corporate Client",
  x: 20, y: 290,
  fontSize: 12,
  fontWeight: 600,
  color: "#8E929A",
  letterSpacing: 1
})

tc3=I("testi", {
  type: "frame",
  name: "TestiCard3",
  x: 914, y: 220,
  width: 400, height: 340,
  fill: "#252830",
  borderRadius: 4,
  borderTop: "2px solid rgba(203,165,122,0.3)"
})
tquote3=I("tc3", {
  type: "text",
  name: "TQuote3Mark",
  text: "\"",
  x: 20, y: 10,
  fontSize: 60,
  fontWeight: 800,
  color: "#CBA57A",
  lineHeight: 1
})
ttext3=I("tc3", {
  type: "text",
  name: "TText3",
  text: "I ordered a birthday box last-minute and it arrived perfectly wrapped and on time. Absolutely stunning — everyone asked where it was from.",
  x: 20, y: 70,
  width: 360,
  fontSize: 14,
  color: "#E8E9EA",
  lineHeight: 1.7,
  fontStyle: "italic"
})
tname3=I("tc3", {
  type: "text",
  name: "TName3",
  text: "Amara K. · Birthday Gift",
  x: 20, y: 290,
  fontSize: 12,
  fontWeight: 600,
  color: "#8E929A",
  letterSpacing: 1
})
```

- [ ] **Step 3: Screenshot testimonials section**

Call: `get_screenshot` on testi node

---

## Chunk 8: Sections 8 & Footer — Contact & Footer

### Task 13: Build Contact section

- [ ] **Step 1: Insert contact frame + left side**

```
contact=I("root", {
  type: "frame",
  name: "Contact",
  x: 65, y: 5800,
  width: 1375, height: 800,
  fill: "#1B1D22"
})
wm8=I("contact", {
  type: "text",
  name: "Watermark8",
  text: "HELLO",
  x: 100, y: 60,
  fontSize: 180,
  fontWeight: 800,
  color: "rgba(255,255,255,0.02)",
  letterSpacing: -2
})
seclabel8=I("contact", {
  type: "text",
  name: "SectionLabel8",
  text: "08 · CONTACT",
  x: 64, y: 140,
  fontSize: 11,
  fontWeight: 600,
  color: "#CBA57A",
  letterSpacing: 3
})
contactheading=I("contact", {
  type: "text",
  name: "ContactHeading",
  text: "Let's Create\nSomething Special",
  x: 64, y: 172,
  fontSize: 48,
  fontWeight: 400,
  color: "#E8E9EA",
  lineHeight: 1.15,
  letterSpacing: -0.5
})
phone1icon=I("contact", {
  type: "icon",
  name: "Phone1Icon",
  icon: "phone",
  x: 64, y: 340,
  width: 16, height: 16,
  color: "#CBA57A"
})
phone1text=I("contact", {
  type: "text",
  name: "Phone1Text",
  text: "07947908615",
  x: 92, y: 338,
  fontSize: 16,
  color: "#E8E9EA"
})
phone2icon=I("contact", {
  type: "icon",
  name: "Phone2Icon",
  icon: "phone",
  x: 64, y: 376,
  width: 16, height: 16,
  color: "#CBA57A"
})
phone2text=I("contact", {
  type: "text",
  name: "Phone2Text",
  text: "07442910982",
  x: 92, y: 374,
  fontSize: 16,
  color: "#E8E9EA"
})
emailicon=I("contact", {
  type: "icon",
  name: "EmailIcon",
  icon: "mail",
  x: 64, y: 412,
  width: 16, height: 16,
  color: "#CBA57A"
})
emailtext=I("contact", {
  type: "text",
  name: "EmailText",
  text: "concierge@lovestewards.com",
  x: 92, y: 410,
  fontSize: 16,
  color: "#E8E9EA"
})
qrbox=I("contact", {
  type: "rectangle",
  name: "QRPlaceholder",
  x: 64, y: 460,
  width: 150, height: 150,
  fill: "#252830",
  borderRadius: 4,
  border: "1px solid rgba(255,255,255,0.1)"
})
qrlabel=I("contact", {
  type: "text",
  name: "QRLabel",
  text: "Scan to WhatsApp",
  x: 64, y: 622,
  fontSize: 11,
  color: "#8E929A",
  letterSpacing: 1
})
```

- [ ] **Step 2: Insert contact form (right side)**

```
formframe=I("contact", {
  type: "frame",
  name: "ContactForm",
  x: 700, y: 140,
  width: 600, height: 560,
  fill: "transparent"
})
nameField=I("formframe", {
  type: "frame",
  name: "NameField",
  x: 0, y: 0,
  width: 600, height: 56,
  fill: "#252830",
  borderRadius: 2,
  border: "1px solid rgba(255,255,255,0.08)"
})
nameLabel=I("nameField", {
  type: "text",
  name: "NameLabel",
  text: "Your Name",
  x: 20, y: 18,
  fontSize: 14,
  color: "#8E929A"
})
occasionField=I("formframe", {
  type: "frame",
  name: "OccasionField",
  x: 0, y: 76,
  width: 600, height: 56,
  fill: "#252830",
  borderRadius: 2,
  border: "1px solid rgba(255,255,255,0.08)"
})
occasionLabel=I("occasionField", {
  type: "text",
  name: "OccasionLabel",
  text: "Occasion Type  ↓",
  x: 20, y: 18,
  fontSize: 14,
  color: "#8E929A"
})
messageField=I("formframe", {
  type: "frame",
  name: "MessageField",
  x: 0, y: 152,
  width: 600, height: 220,
  fill: "#252830",
  borderRadius: 2,
  border: "1px solid rgba(255,255,255,0.08)"
})
messageLabel=I("messageField", {
  type: "text",
  name: "MessageLabel",
  text: "Your message...",
  x: 20, y: 20,
  fontSize: 14,
  color: "#8E929A"
})
submitbtn=I("formframe", {
  type: "frame",
  name: "SubmitBtn",
  x: 0, y: 396,
  width: 200, height: 52,
  fill: "#CBA57A",
  borderRadius: 2
})
submittext=I("submitbtn", {
  type: "text",
  name: "SubmitText",
  text: "Send Enquiry →",
  x: 30, y: 16,
  fontSize: 14,
  fontWeight: 700,
  color: "#1B1D22"
})
```

- [ ] **Step 3: Screenshot contact section**

Call: `get_screenshot` on contact node

### Task 14: Build Footer

- [ ] **Step 1: Insert footer frame**

```
footer=I("root", {
  type: "frame",
  name: "Footer",
  x: 65, y: 6600,
  width: 1375, height: 80,
  fill: "#1B1D22",
  borderTop: "1px solid rgba(255,255,255,0.08)"
})
footerlogo=I("footer", {
  type: "text",
  name: "FooterLogo",
  text: "Love Stewards",
  x: 64, y: 26,
  fontSize: 16,
  fontWeight: 800,
  color: "#E8E9EA"
})
footertagline=I("footer", {
  type: "text",
  name: "FooterTagline",
  text: "Stewarding Meaningful Moments Through Thoughtful Gifting.",
  x: 400, y: 30,
  fontSize: 12,
  color: "#8E929A",
  letterSpacing: 0.3
})
footerig=I("footer", {
  type: "icon",
  name: "FooterIG",
  icon: "instagram",
  x: 1280, y: 28,
  width: 18, height: 18,
  color: "#8E929A"
})
footertt=I("footer", {
  type: "icon",
  name: "FooterTT",
  icon: "tiktok",
  x: 1316, y: 28,
  width: 18, height: 18,
  color: "#8E929A"
})
```

- [ ] **Step 2: Take final full-page screenshot**

Call: `get_screenshot` on root node

- [ ] **Step 3: Take screenshot of footer**

Call: `get_screenshot` on footer node

---

## Chunk 9: Polish — Effects & Final Review

### Task 15: Add visual effects and polish

- [ ] **Step 1: Take snapshot of full layout to check alignment**

Call: `snapshot_layout` on root node

- [ ] **Step 2: Review and fix any alignment issues found in snapshot**

Use `batch_design` with U() operations to correct any misaligned nodes.

- [ ] **Step 3: Take section-by-section screenshots for final review**

Call `get_screenshot` on each major section: Hero, Occasions, Collections, Corporate, WhyUs, HowItWorks, Testimonials, Contact, Footer.

- [ ] **Step 4: Apply gold accent overlay effect to hero image slices**

Use U() operations to ensure all hero image slices have consistent `opacity: 0.9` and dark filter treatment.

- [ ] **Step 5: Verify all text is readable against dark backgrounds**

Check text color contrast — all body text should be `#8E929A` or brighter, no text on dark `#1B1D22` background below `#8E929A`.

- [ ] **Step 6: Final full-canvas screenshot**

Call: `get_screenshot` on root node and present to user.
