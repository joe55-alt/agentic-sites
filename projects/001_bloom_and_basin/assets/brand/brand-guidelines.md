# Brand Guidelines - Bloom & Basin

**Business:** Bloom & Basin
**Tagline:** Desert-inspired greenery for your home and yard
**Industry:** Plant Shop + Landscaping Services
**Location:** Phoenix, Arizona
**Created:** December 21, 2025

---

## Logo

### Logo Concept

**Design Philosophy:**
The Bloom & Basin logo combines desert botanical elements with modern minimalism. The mark features a stylized agave or succulent plant emerging from a basin/pot, creating a clean icon that works at any size.

**Primary Logo:**
- Full logo with icon + wordmark "Bloom & Basin"
- Icon positioned to the left of wordmark
- Clean, balanced composition

**Logo Variations:**
1. **Full Color:** Primary sage green icon + warm charcoal text (for light backgrounds)
2. **Reversed:** White version for dark backgrounds
3. **Icon Only:** Standalone plant mark for small spaces, favicons, social profiles
4. **Wordmark Only:** Text-only version for limited space applications

### Logo Usage Guidelines

**Clear Space:**
Maintain padding equal to the height of the icon on all sides. Never crowd the logo with other elements.

**Minimum Size:**
- Digital: 120px width minimum
- Print: 1 inch width minimum

**Logo Don'ts:**
- ✗ Don't stretch, distort, or change proportions
- ✗ Don't change the colors (use approved versions only)
- ✗ Don't add effects (drop shadows, gradients, glows)
- ✗ Don't place on busy or low-contrast backgrounds
- ✗ Don't rotate or rearrange elements
- ✗ Don't outline or add borders

---

## Color Palette

Our color palette is inspired by the natural desert landscape of Arizona - warm, earthy, and sophisticated.

### Primary Colors

**Sage Green (Primary Brand Color)**
- **Hex:** #7A9B76
- **RGB:** rgb(122, 155, 118)
- **CMYK:** C:21 M:0 Y:24 K:39
- **Use:** Logo icon, primary CTAs, section headers, navigation active states
- **Description:** A muted desert green that evokes succulents and drought-tolerant plants

**Terracotta (Secondary)**
- **Hex:** #C07855
- **RGB:** rgb(192, 120, 85)
- **CMYK:** C:0 M:38 Y:56 K:25
- **Use:** Accent elements, hover states, secondary CTAs, special highlights
- **Description:** Warm clay color inspired by Southwest pottery and desert soil

### Accent & Neutral Colors

**Sand Cream (Accent)**
- **Hex:** #E8DCC4
- **RGB:** rgb(232, 220, 196)
- **CMYK:** C:0 M:5 Y:16 K:9
- **Use:** Background sections, cards, subtle highlights
- **Description:** Soft, warm neutral inspired by desert sand

**Warm Charcoal (Dark Neutral)**
- **Hex:** #3A3635
- **RGB:** rgb(58, 54, 53)
- **CMYK:** C:0 M:7 Y:9 K:77
- **Use:** Body text, dark headings, navigation text
- **Description:** Rich, warm near-black that's softer than pure black

**Warm Gray (Light Neutral)**
- **Hex:** #F5F3F0
- **RGB:** rgb(245, 243, 240)
- **CMYK:** C:0 M:1 Y:2 K:4
- **Use:** Page backgrounds, light sections, subtle borders
- **Description:** Warm off-white for softer contrast

**White**
- **Hex:** #FFFFFF
- **RGB:** rgb(255, 255, 255)
- **CMYK:** C:0 M:0 Y:0 K:0
- **Use:** Text on dark backgrounds, card backgrounds, clean sections

### Color Combinations

**High Impact (CTAs, Headers):**
- Sage Green (#7A9B76) on White (#FFFFFF)
- White (#FFFFFF) on Sage Green (#7A9B76)
- Terracotta (#C07855) on White (#FFFFFF)

**Soft & Warm (Backgrounds):**
- Warm Charcoal (#3A3635) text on Sand Cream (#E8DCC4)
- Sage Green (#7A9B76) text on Warm Gray (#F5F3F0)

---

## Typography

Our typography pairing balances sophistication with approachability - a modern serif for elegance paired with a clean sans-serif for readability.

### Heading Font: Crimson Pro

**Font Family:** Crimson Pro (Google Fonts)
**Type:** Modern Serif
**Weights Used:** 600 (Semi-Bold), 700 (Bold)
**Use Cases:** H1, H2, H3, H4, section headers, hero text
**Source:** https://fonts.google.com/specimen/Crimson+Pro

**Why Crimson Pro:**
- Elegant serif with organic, slightly rounded shapes
- Excellent readability at all sizes
- Sophisticated but warm (not cold or corporate)
- Pairs beautifully with sans-serif body text

**Styling:**
```css
h1, h2, h3, h4 {
  font-family: 'Crimson Pro', serif;
  font-weight: 600;
  color: #3A3635; /* Warm Charcoal */
}

h1 { font-size: 3.5rem; line-height: 1.2; }
h2 { font-size: 2.5rem; line-height: 1.3; }
h3 { font-size: 1.75rem; line-height: 1.4; }
```

### Body Font: Inter

**Font Family:** Inter (Google Fonts)
**Type:** Sans-Serif
**Weights Used:** 400 (Regular), 500 (Medium), 600 (Semi-Bold)
**Use Cases:** Body text, captions, navigation, buttons, labels
**Source:** https://fonts.google.com/specimen/Inter

**Why Inter:**
- Exceptional readability on screens
- Modern, clean, professional
- Excellent letter spacing and proportions
- Wide range of weights for hierarchy

**Styling:**
```css
body, p, a, button, nav {
  font-family: 'Inter', sans-serif;
  font-weight: 400;
  color: #3A3635; /* Warm Charcoal */
}

p { font-size: 1rem; line-height: 1.7; }
.lead { font-size: 1.25rem; font-weight: 500; }
```

### CSS Import

```css
/* Import both fonts */
@import url('https://fonts.googleapis.com/css2?family=Crimson+Pro:wght@600;700&family=Inter:wght@400;500;600&display=swap');

/* Apply to elements */
h1, h2, h3, h4, h5, h6 {
  font-family: 'Crimson Pro', serif;
}

body, p, a, span, button, input, textarea {
  font-family: 'Inter', sans-serif;
}
```

### Type Scale

| Element | Font | Size | Weight | Line Height |
|---------|------|------|--------|-------------|
| H1 | Crimson Pro | 3.5rem (56px) | 600 | 1.2 |
| H2 | Crimson Pro | 2.5rem (40px) | 600 | 1.3 |
| H3 | Crimson Pro | 1.75rem (28px) | 600 | 1.4 |
| H4 | Crimson Pro | 1.25rem (20px) | 600 | 1.5 |
| Body Large | Inter | 1.25rem (20px) | 400 | 1.7 |
| Body | Inter | 1rem (16px) | 400 | 1.7 |
| Small | Inter | 0.875rem (14px) | 400 | 1.6 |
| Button | Inter | 1rem (16px) | 500 | 1 |

---

## Logo Files Reference

### Available Formats

**Primary Logo:**
- `logos/primary-logo.svg` - Vector (preferred for web)
- `logos/primary-logo.png` - Transparent PNG (1000px width)
- `logos/primary-logo-white.svg` - Reversed for dark backgrounds

**Icon Only:**
- `logos/icon-only.svg` - Vector icon
- `logos/icon-only.png` - Transparent PNG (500px)
- `logos/favicon.ico` - 32x32 favicon for browsers

**Wordmark Only:**
- `logos/wordmark.svg` - Text-only logo
- `logos/wordmark.png` - Transparent PNG

### Color Palette File

- `colors/color-palette.png` - Visual reference of all brand colors

---

## Social Media Assets

**Profile Picture (400x400px):**
- `social/profile-pic.png`
- Uses: Instagram, Facebook, LinkedIn profile images
- Content: Icon only (plant mark) centered on sage green background

**Cover Photo (1500x500px):**
- `social/cover-photo.png`
- Uses: Facebook cover, LinkedIn banner
- Content: Full logo + tagline on warm gradient background

**OG Image (1200x630px):**
- `social/og-image.png`
- Uses: Link previews on social media, Slack, Discord
- Content: Logo + tagline + subtle desert plant imagery

---

## Brand Personality

**Voice & Tone:**
- Knowledgeable but not pretentious
- Warm and welcoming (Southwest hospitality)
- Passionate about plants and sustainability
- Helpful and educational
- Professional yet approachable

**Brand Attributes:**
- Modern yet natural
- Sophisticated yet accessible
- Expert yet friendly
- Sustainable yet beautiful

**Visual Style:**
- Clean lines and white space
- Organic shapes and natural textures
- High-quality photography (plants, landscapes)
- Warm, inviting color palette
- Modern desert aesthetic

---

## Implementation Notes for Frontend Agent

### CSS Variables Setup

```css
:root {
  /* Colors */
  --color-primary: #7A9B76;
  --color-secondary: #C07855;
  --color-accent: #E8DCC4;
  --color-dark: #3A3635;
  --color-gray-light: #F5F3F0;
  --color-white: #FFFFFF;

  /* Typography */
  --font-heading: 'Crimson Pro', serif;
  --font-body: 'Inter', sans-serif;

  /* Spacing (based on 8px grid) */
  --space-xs: 0.5rem;
  --space-sm: 1rem;
  --space-md: 1.5rem;
  --space-lg: 2rem;
  --space-xl: 3rem;
  --space-2xl: 4rem;
}
```

### Button Styles

```css
.btn-primary {
  background-color: var(--color-primary);
  color: var(--color-white);
  font-family: var(--font-body);
  font-weight: 500;
  padding: 0.75rem 2rem;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

.btn-primary:hover {
  background-color: #6A8A66; /* Darker sage */
}

.btn-secondary {
  background-color: var(--color-secondary);
  color: var(--color-white);
}
```

---

## Competitor Differentiation

**vs. Traditional Phoenix Landscapers:**
- Our brand feels modern and premium (they feel dated)
- We emphasize lifestyle and sustainability (they focus on services only)
- Our visual identity is clean and cohesive (theirs are generic)

**vs. National Plant Retailers:**
- We have deep desert expertise (they're generic)
- We offer both retail + professional services (they're one or the other)
- We're locally rooted in Phoenix (they're corporate)

---

## Brand Applications

### Website
- Hero sections: Sage green overlays on plant photography
- CTA buttons: Primary (sage) and secondary (terracotta)
- Backgrounds: Alternating white and warm gray sections
- Accent elements: Terracotta for special highlights

### Print Materials
- Business cards: Sage green logo on sand cream cardstock
- Brochures: Clean layouts with warm photography
- Signage: Wordmark + icon in various sizes

### Retail Environment
- Wall color: Warm gray or sand cream
- Signage: Warm charcoal letters
- Accent colors: Terracotta pottery, sage plant displays

---

*Generated by Logo Agent for Bloom & Basin*
*Project 001 - Proof of Concept*
*December 21, 2025*
