# Bloom & Basin - Color Palette Reference

## Quick Reference

### Primary Brand Colors

**Sage Green (Primary)**
```
HEX:  #7A9B76
RGB:  122, 155, 118
CMYK: 21, 0, 24, 39
HSL:  116°, 16%, 54%
```
**Usage:** Logo icon, primary CTAs, navigation highlights, section headers
**Accessibility:** WCAG AA compliant on white backgrounds

---

**Terracotta (Secondary)**
```
HEX:  #C07855
RGB:  192, 120, 85
CMYK: 0, 38, 56, 25
HSL:  20°, 46%, 54%
```
**Usage:** Accent elements, hover states, secondary CTAs
**Accessibility:** WCAG AA compliant on white backgrounds

---

### Neutral Colors

**Sand Cream (Light Accent)**
```
HEX:  #E8DCC4
RGB:  232, 220, 196
CMYK: 0, 5, 16, 9
HSL:  40°, 45%, 84%
```
**Usage:** Background sections, cards, subtle highlights

---

**Warm Charcoal (Dark Text)**
```
HEX:  #3A3635
RGB:  58, 54, 53
CMYK: 0, 7, 9, 77
HSL:  12°, 5%, 22%
```
**Usage:** Body text, headings, navigation
**Accessibility:** WCAG AAA compliant on white/light backgrounds

---

**Warm Gray (Light Background)**
```
HEX:  #F5F3F0
RGB:  245, 243, 240
CMYK: 0, 1, 2, 4
HSL:  36°, 17%, 95%
```
**Usage:** Page backgrounds, subtle sections

---

**White**
```
HEX:  #FFFFFF
RGB:  255, 255, 255
```
**Usage:** Text on dark, clean backgrounds

---

## Color Combinations

### High Contrast (Accessible)
- **Text on Background:**
  - Warm Charcoal (#3A3635) on White (#FFFFFF) ✓ AAA
  - Warm Charcoal (#3A3635) on Sand Cream (#E8DCC4) ✓ AAA
  - White (#FFFFFF) on Sage Green (#7A9B76) ✓ AA
  - White (#FFFFFF) on Terracotta (#C07855) ✓ AA

### Recommended Pairings
- **Hero Sections:** Sage Green overlay on photography, white text
- **CTAs:** Sage Green background, white text
- **Accents:** Terracotta highlights on warm gray backgrounds
- **Cards:** White or sand cream backgrounds, warm charcoal text

---

## CSS Variables

```css
:root {
  /* Primary */
  --sage-green: #7A9B76;
  --terracotta: #C07855;

  /* Neutrals */
  --sand-cream: #E8DCC4;
  --warm-charcoal: #3A3635;
  --warm-gray: #F5F3F0;
  --white: #FFFFFF;

  /* Semantic naming */
  --color-primary: var(--sage-green);
  --color-secondary: var(--terracotta);
  --color-accent: var(--sand-cream);
  --color-text-dark: var(--warm-charcoal);
  --color-bg-light: var(--warm-gray);
  --color-bg-white: var(--white);
}
```

---

## Tailwind Config (if applicable)

```javascript
colors: {
  sage: {
    DEFAULT: '#7A9B76',
    light: '#96B492',
    dark: '#6A8A66',
  },
  terracotta: {
    DEFAULT: '#C07855',
    light: '#D49A7E',
    dark: '#A86443',
  },
  sand: '#E8DCC4',
  charcoal: '#3A3635',
  'warm-gray': '#F5F3F0',
}
```

---

## Gradients (Optional Accents)

**Desert Sunset:**
```css
background: linear-gradient(135deg, #C07855 0%, #7A9B76 100%);
```
Use sparingly for hero overlays or special sections.

**Warm Neutral:**
```css
background: linear-gradient(180deg, #F5F3F0 0%, #E8DCC4 100%);
```
Subtle background for sections.

---

*Color Palette Created: December 21, 2025*
