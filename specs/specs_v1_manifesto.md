# REI Manifesto Page Specification v1.0

## Purpose

Add a dedicated manifesto page to the REI landing site with minimal navigation. The manifesto presents the full text
from `MANIFESTO.md` in a visually attractive long-form reading experience that maintains the site's dark retro-machine
aesthetic.

---

## Navigation Implementation (Option A - Minimal)

### Landing Page Changes

**Location**: "Explore Further" section (Section 8)

**Add CTA Button**:

- Text: "Read the Manifesto →"
- Position: Add to existing CTA button group
- Link: `/manifesto`
- Style: Same frosted glass button treatment as other CTAs
- Icon: 📜 or similar (optional)

### Manifesto Page Navigation

**Back Link**:

- Position: Top-left of page (before content begins)
- Text: "← Back to Overview" or "← REI Project"
- Link: `/` (homepage)
- Style: Simple text link with electric blue color on hover
- Placement: Outside main content container, subtle

---

## Manifesto Page Design

### Overall Layout

**Container**:

- Max width: 800px (optimized for reading)
- Centered on page
- Padding: 4rem 2rem (desktop), 2rem 1rem (mobile)
- Background: Same dark base as landing page

**Reading Experience**:

- Long-form vertical scroll
- No sections/cards - continuous text flow
- Generous line-height for readability (1.7-1.8)
- Optimal line length (60-75 characters)

---

## Typography & Formatting

### Body Text

- **Font**: Monospace (JetBrains Mono or same as site)
- **Size**: 16px (1rem) base, 18px (1.125rem) on desktop
- **Color**: `var(--color-text-primary)` (#e8e8e8)
- **Line height**: 1.75
- **Letter spacing**: 0.02em (subtle - enhances monospace readability)

### Headings

**H1 (Page Title - "MANIFESTO")**:

- **Font**: Monospace
- **Size**: 3rem (mobile: 2rem)
- **Color**: Electric blue (`var(--color-electric-blue)`)
- **Treatment**: Uppercase, centered
- **Spacing**: Large margin-bottom (3rem)
- **Optional**: Subtle glow effect

**H2 (Major Sections)**:

- **Font**: Monospace
- **Size**: 2rem (mobile: 1.5rem)
- **Color**: Electric blue (`var(--color-electric-blue)`)
- **Treatment**: Uppercase or title case
- **Spacing**: 3rem top margin, 1.5rem bottom margin
- **Optional**: Thin electric blue underline or border-left accent

**H3 (Subsections)**:

- **Font**: Monospace
- **Size**: 1.5rem (mobile: 1.25rem)
- **Color**: Neon green (`var(--color-neon-green)`)
- **Treatment**: Title case
- **Spacing**: 2rem top margin, 1rem bottom margin

**H4+ (if needed)**:

- **Font**: Monospace
- **Size**: 1.25rem
- **Color**: Amber (`var(--color-amber)`)
- **Spacing**: 1.5rem top margin, 0.75rem bottom margin

### Other Elements

**Paragraphs**:

- Margin-bottom: 1.5rem
- No first-line indent
- Block paragraphs with spacing

**Lists** (ul/ol):

- Margin-left: 2rem
- Margin-bottom: 1.5rem
- Line-height: 1.7
- Bullet color: Electric blue for `<ul>`, numbers in neon green for `<ol>`

**Emphasis**:

- `<em>` / italic: Color shift to electric blue (keep monospace)
- `<strong>` / bold: Bolder weight + neon green color
- Code-like emphasis: Keep monospace, amber color

**Blockquotes** (if any):

- Border-left: 2px solid electric blue
- Padding-left: 1.5rem
- Margin: 2rem 0
- Italic + slightly muted color
- Optional: Frosted glass background

**Links** (if any in content):

- Color: Electric blue
- Underline on hover
- Glow effect on hover

---

## Visual Treatments

### Background

- Same as landing page: `var(--color-bg-primary)` (#0a0a0a)
- Optional: Very subtle noise texture or scanline effect for retro feel

### Scrollbar Styling (optional enhancement)

```css
::-webkit-scrollbar {
    width: 8px;
}

::-webkit-scrollbar-track {
    background: rgba(20, 20, 20, 0.5);
}

::-webkit-scrollbar-thumb {
    background: var(--color-electric-blue);
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: var(--color-neon-green);
}
```

### Reading Progress Indicator (optional)

- Thin line at top of viewport showing scroll progress
- Color: Electric blue
- Height: 2-3px
- Animates as user scrolls

---

## Content Processing

### Source

- Pull content from: `https://github.com/rei-project/REI/blob/main/MANIFESTO.md`
- Convert Markdown to HTML with proper heading hierarchy

### Markdown Conversion

- H1 (`#`) → Page title
- H2 (`##`) → Major sections (electric blue)
- H3 (`###`) → Subsections (neon green)
- H4+ (`####`) → Minor sections (amber)
- Preserve all text content
- Maintain paragraph breaks
- Process emphasis, lists, etc.

### Special Handling

- If manifesto contains code blocks: Use darker background panel with syntax highlighting
- If manifesto contains horizontal rules (`---`): Style as electric blue divider line

---

## Responsive Behavior

### Mobile (< 640px)

- Reduce font size slightly (14px base for monospace)
- Reduce heading sizes
- Tighter padding (1rem)
- Back link remains visible

### Tablet (640px - 1024px)

- Medium font size (15px base)
- Medium padding (2rem)

### Desktop (> 1024px)

- Full font size (16-18px)
- Maximum padding and line length
- Optional: Subtle parallax or fade-in effects on scroll

---

## Technical Implementation

### File Structure

```
src/
├── pages/
│   ├── index.astro           # Landing page
│   └── manifesto.astro       # New manifesto page
├── components/
│   └── BackLink.astro        # Reusable back navigation
├── layouts/
│   ├── MainLayout.astro      # Used by landing page
│   └── ManifestoLayout.astro # Reading-optimized layout
└── styles/
    ├── global.css            # Shared variables
    └── manifesto.css         # Manifesto-specific styles
```

### ManifestoLayout.astro

```astro
---
import '../styles/global.css'
import '../styles/manifesto.css'
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>REI Manifesto - Redesigning Execution for Intelligence</title>
  <meta name="description" content="The REI Manifesto - A vision for AI-first programming">
  <!-- OpenGraph / Social meta tags -->
</head>
<body>
  <div class="reading-container">
    <slot />
  </div>
</body>
</html>
```

### manifesto.astro

```astro
---
import ManifestoLayout from '../layouts/ManifestoLayout.astro'
import BackLink from '../components/BackLink.astro'

// Fetch and parse MANIFESTO.md content
// Convert Markdown to HTML
---

<ManifestoLayout>
  <BackLink href="/" text="← REI Project" />
  
  <article class="manifesto-content">
    <h1>MANIFESTO</h1>
    
    <!-- Rendered manifesto content here -->
    <div set:html={manifestoHtml} />
  </article>
</ManifestoLayout>
```

### manifesto.css (Key Styles)

```css
.reading-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 4rem 2rem;
    background: var(--color-bg-primary);
    min-height: 100vh;
}

.manifesto-content {
    font-family: var(--font-mono);
    font-size: 1rem;
    line-height: 1.75;
    letter-spacing: 0.02em;
    color: var(--color-text-primary);
}

.manifesto-content h1 {
    font-size: 3rem;
    color: var(--color-electric-blue);
    text-align: center;
    text-transform: uppercase;
    margin-bottom: 3rem;
    text-shadow: var(--glow-sm) var(--color-electric-blue);
}

.manifesto-content h2 {
    font-size: 2rem;
    color: var(--color-electric-blue);
    margin-top: 3rem;
    margin-bottom: 1.5rem;
    text-transform: uppercase;
}

.manifesto-content h3 {
    font-size: 1.5rem;
    color: var(--color-neon-green);
    margin-top: 2rem;
    margin-bottom: 1rem;
}

.manifesto-content h4 {
    font-size: 1.25rem;
    color: var(--color-amber);
    margin-top: 1.5rem;
    margin-bottom: 0.75rem;
}

.manifesto-content p {
    margin-bottom: 1.5rem;
}

.manifesto-content ul,
.manifesto-content ol {
    margin-left: 2rem;
    margin-bottom: 1.5rem;
}

.manifesto-content li {
    margin-bottom: 0.5rem;
}

.manifesto-content strong {
    color: var(--color-neon-green);
    font-weight: 700;
}

.manifesto-content em {
    color: var(--color-electric-blue);
    font-style: italic;
}

@media (max-width: 640px) {
    .reading-container {
        padding: 2rem 1rem;
    }

    .manifesto-content {
        font-size: 0.875rem;
    }

    .manifesto-content h1 {
        font-size: 2rem;
    }

    .manifesto-content h2 {
        font-size: 1.5rem;
    }
}
```

---

## Content Integration

### Option 1: Static Copy

- Copy `MANIFESTO.md` content into Astro component
- Manually convert to HTML with proper heading classes
- Full control over formatting

### Option 2: Dynamic Fetch + Parse

- Fetch from GitHub raw URL at build time
- Use Markdown parser (remark/marked)
- Automatically convert to HTML
- Apply CSS classes to generated elements

**Recommendation**: Option 2 for easier updates if manifesto changes

---

## Meta Tags & SEO

```html

<meta property="og:title" content="REI Manifesto">
<meta property="og:description" content="A vision for programming in the age of AI collaboration">
<meta property="og:type" content="article">
<meta name="twitter:card" content="summary">
```

---

## Accessibility

- Semantic HTML5 (`<article>`, `<nav>`)
- Proper heading hierarchy (H1 → H2 → H3)
- Sufficient contrast (WCAG AA minimum)
- Focus indicators for back link
- Skip-to-content link (optional)

---

## Success Criteria

- [ ] Manifesto content is fully readable and formatted
- [ ] Monospace font applies to all body text
- [ ] Headings use electric colors as specified
- [ ] "Read the Manifesto" CTA appears on landing page
- [ ] Back link works and is visible
- [ ] Page maintains dark retro aesthetic
- [ ] Text is readable on mobile devices
- [ ] Line length optimized for reading (60-75 chars)
- [ ] Deploys successfully to GitHub Pages at `/manifesto`

---

## Future Enhancements (Post-v1)

- Reading progress indicator
- Table of contents (sticky sidebar on desktop)
- Print-friendly stylesheet
- Section anchor links
- Dark/light mode toggle (if desired)
- Animated text reveal on scroll

---

**Version**: 1.0  
**Last Updated**: 2025-01-18  
**Status**: Ready for Implementation