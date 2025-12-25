# Bloom & Basin - Logo Specifications

## Logo Concept

**Design Description:**
The Bloom & Basin logo features a stylized desert plant (agave/succulent) emerging from a basin or pot. The design is minimalist, modern, and instantly recognizable.

**Key Elements:**
1. **Icon:** Geometric succulent/agave plant with layered leaves
2. **Wordmark:** "Bloom & Basin" in Crimson Pro (serif)
3. **Tagline (optional):** "Desert-inspired greenery for your home and yard"

---

## Logo Variations

### 1. Primary Logo (Full)
**File:** `primary-logo.svg`, `primary-logo.png`
**Description:** Icon on the left + wordmark on the right
**Colors:**
- Icon: Sage Green (#7A9B76)
- Wordmark: Warm Charcoal (#3A3635)
**Usage:** Website header, business cards, letterhead, primary marketing
**Minimum Width:** 120px (digital), 1 inch (print)

### 2. Icon Only
**File:** `icon-only.svg`, `icon-only.png`
**Description:** Plant mark without text
**Colors:** Sage Green (#7A9B76)
**Usage:** Favicon, app icons, social media profile pictures, watermarks
**Minimum Size:** 32px × 32px

### 3. Wordmark Only
**File:** `wordmark.svg`, `wordmark.png`
**Description:** "Bloom & Basin" text without icon
**Colors:** Warm Charcoal (#3A3635) or Sage Green (#7A9B76)
**Usage:** Limited horizontal space applications
**Minimum Width:** 100px

### 4. Reversed (White)
**File:** `primary-logo-white.svg`, `icon-only-white.svg`
**Description:** White versions for dark backgrounds
**Colors:** White (#FFFFFF) - all elements
**Usage:** Dark background sections, photography overlays, video

### 5. Favicon
**File:** `favicon.ico`
**Description:** 32×32 icon-only version for browser tabs
**Format:** ICO format with multiple sizes embedded

---

## Technical Specifications

### SVG Files (Preferred)
- **Format:** SVG (Scalable Vector Graphics)
- **Viewbox:** 0 0 200 60 (primary), 0 0 100 100 (icon)
- **Advantages:** Infinite scalability, small file size, perfect for web

### PNG Files (Fallback)
- **Formats Available:**
  - `primary-logo.png` - 1000px width, transparent background
  - `primary-logo@2x.png` - 2000px width (retina displays)
  - `icon-only.png` - 500×500px, transparent background
  - `icon-only-sm.png` - 200×200px, transparent background

### File Naming Convention
```
primary-logo.svg         // Main logo, color
primary-logo-white.svg   // Reversed for dark backgrounds
icon-only.svg            // Icon mark, color
icon-only-white.svg      // Icon reversed
wordmark.svg             // Text only
favicon.ico              // Browser icon
```

---

## Logo Construction

### Icon Design
The plant icon is built from geometric shapes:
```
- 5-7 layered leaves arranged radially
- Leaves taper from thick base to pointed tip
- Subtle organic curves (not perfectly geometric)
- Base "pot" element (optional, can be simplified basin line)
- Overall proportion: 1:1 (square)
```

### Wordmark Design
```
Font: Crimson Pro Semi-Bold (600)
Text: Bloom & Basin
Letter Spacing: -0.02em (slightly tighter)
Case: Title Case
Ampersand: Use stylized & or spell out "and"
```

### Layout Proportions
```
[ICON] [SPACING] [WORDMARK]
  20%      10%       70%

Icon height = Wordmark height
Spacing = 1/2 icon width
```

---

## Clear Space

**Rule:** Maintain clear space equal to the height of the icon on all sides of the logo.

```
     [X]
  [X][LOGO][X]
     [X]

Where X = height of icon
```

**Minimum Clearance:**
- Digital: 20px on all sides
- Print: 0.25 inches on all sides

---

## Usage Guidelines

### ✓ DO:
- Use approved logo files only
- Maintain clear space around logo
- Place on high-contrast backgrounds
- Use reversed (white) version on dark backgrounds
- Scale proportionally (lock aspect ratio)
- Use icon-only for small applications (< 100px)

### ✗ DON'T:
- Stretch, compress, or distort the logo
- Change colors (except approved white version)
- Rotate the logo
- Add effects (shadows, glows, outlines, gradients)
- Place on busy or low-contrast backgrounds
- Separate icon from wordmark and rearrange
- Recreate or redraw the logo
- Use outdated versions

---

## Background Usage

### Approved Backgrounds:
✓ White (#FFFFFF)
✓ Warm Gray (#F5F3F0)
✓ Sand Cream (#E8DCC4)
✓ Photography (with sufficient contrast or overlay)

### Use White Logo On:
✓ Sage Green (#7A9B76)
✓ Terracotta (#C07855)
✓ Warm Charcoal (#3A3635)
✓ Dark photography
✓ Video overlays

### Avoid:
✗ Busy patterns
✗ Low-contrast colors
✗ Gradients (unless tested for visibility)
✗ Centered over detailed imagery without backdrop

---

## Accessibility

**Color Contrast:**
- Sage Green logo on white background: Passes WCAG AA
- White logo on sage green background: Passes WCAG AA
- Ensure logo is visible to colorblind users (test with tools)

**Alt Text for Web:**
```html
<img src="logo.svg" alt="Bloom & Basin - Desert-inspired greenery">
```

---

## Logo Asset Checklist

For frontend implementation, ensure you have:

- [ ] `primary-logo.svg` - Main color logo (vector)
- [ ] `primary-logo.png` - Main color logo (raster, 1000px)
- [ ] `primary-logo-white.svg` - Reversed logo for dark backgrounds
- [ ] `icon-only.svg` - Icon mark (vector)
- [ ] `icon-only.png` - Icon mark (raster, 500px)
- [ ] `icon-only-white.svg` - Icon reversed
- [ ] `wordmark.svg` - Text-only logo
- [ ] `favicon.ico` - Browser favicon (32×32, multi-size ICO)
- [ ] `favicon.png` - PNG favicon fallback (32×32)

---

## Social Media Specifications

### Profile Pictures (Icon Only)
- **Instagram:** 320×320px minimum (icon-only.png centered)
- **Facebook:** 180×180px minimum
- **LinkedIn:** 400×400px recommended
- **Background:** Sage green or white

### Cover Photos
- **Facebook:** 820×312px (1640×624px for retina)
- **LinkedIn:** 1584×396px
- **Content:** Full logo + tagline, centered or left-aligned

### Open Graph Images (og:image)
- **Size:** 1200×630px
- **Content:** Logo + tagline + subtle plant imagery
- **File:** `social/og-image.png`

---

## Implementation Code Snippets

### HTML (SVG inline for best performance)
```html
<svg class="logo" viewBox="0 0 200 60">
  <!-- SVG content here -->
</svg>
```

### HTML (Image tag)
```html
<img src="/assets/brand/logos/primary-logo.svg"
     alt="Bloom & Basin"
     class="logo"
     width="200"
     height="60">
```

### CSS (Styling)
```css
.logo {
  width: auto;
  height: 60px; /* Adjust as needed */
  max-width: 200px;
}

@media (max-width: 768px) {
  .logo {
    height: 40px;
  }
}
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Dec 21, 2025 | Initial brand identity created |

---

*Logo specifications prepared by Logo Agent for Bloom & Basin*
*Project 001 - Proof of Concept*
