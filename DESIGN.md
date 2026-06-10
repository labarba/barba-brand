# Lorena A. Barba Group — Design System

**Status:** v0.1, foundation
**Source of truth:** Measured from the current `lorenabarba.com` (spruce-theme) screenshots and live markup, June 2026.
**Scope:** A brand and UI foundation that captures what works about the current site (two-color discipline, card layout, editorial restraint) and prepares for an eventual rebuild off the fragile WordPress theme.

---

## 1. Principles

The current site has aged well because it commits to a few decisions and holds them. This system codifies that discipline rather than expanding it.

- **Two colors, used with conviction.** One red, one warm near-black, on white. Color carries meaning (it marks what is interactive or what is the group's mark); it is not decoration.
- **Editorial, not corporate.** A serif sets a scholarly, written tone. Flat surfaces, hairline rules, square corners, no shadows.
- **Restraint as a feature.** Whitespace, a single accent, and a clear type hierarchy do the work. When in doubt, remove.
- **Open by default.** Type and icon choices favor libre licensing, consistent with the group's open-source and reproducibility commitments.

---

## 2. Color

The palette is two-color by intent: **Barba Red** and **Ink** on **Paper**, with a small set of neutrals for structure and meta text. Values below are measured, not eyeballed.

### Core tokens

| Token | Hex | Role |
|---|---|---|
| `--color-red` | `#CE2406` | Primary. The group's mark, icons, links, active states, badges. |
| `--color-red-deep` | `#A51D04` | Hover/active/pressed for red interactive elements. |
| `--color-red-wash` | `#FBEAE6` | Optional pale background tint (callouts, selected rows). Use sparingly. |
| `--color-ink` | `#181712` | Headings and body text. A *warm* near-black, not pure black. |
| `--color-paper` | `#FFFFFF` | Page and card background. |
| `--color-hairline` | `#EAEBE6` | Card borders, rules, dividers. A warm light grey. |
| `--color-muted` | `#787876` | Meta text: copyright, dates, captions, secondary labels. |
| `--color-muted-soft` | `#B4B4B2` | Faint dividers, disabled states. |
| `--color-icon-hover` | `#9C9C9A` | Grey that icons transition to on hover. |

### Optional accent (illustration only)

| Token | Hex | Role |
|---|---|---|
| `--color-slate` | `#546E7D` | The desaturated blue from the avatar's sketch linework. Permitted only in illustration and diagram contexts; never in UI chrome, links, or text. Keeps the UI strictly two-color. |

### Off-spec value to reconcile

The avatar background currently uses `#E7181E`, a brighter and more saturated red than the website's `#CE2406`. These read as two different brands side by side. Recommendation: regenerate or recolor the avatar field to `--color-red` so the mark is consistent across the site, slides, and social. If you prefer the brighter red as the new canonical, that is a legitimate choice; it should then replace `#CE2406` everywhere, not coexist with it.

### Contrast (WCAG 2.1, against Paper)

- `--color-ink` on Paper: ≈17.6:1. Passes AAA at all sizes.
- `--color-red` on Paper: ≈5.4:1. Passes AA for normal text and AAA for large text; red links at body size are safe.
- White on `--color-red`: ≈5.4:1. Safe for button and badge labels.
- `--color-muted` on Paper: ≈4.7:1. Fine for body-size meta text; avoid for anything smaller than 14px.

Note: the brighter avatar red `#E7181E` drops to ≈4.6:1, a second reason to standardize on `#CE2406`.

---

## 3. Typography

Two families, two jobs: a serif for everything expressive (the mark, headings) and a humanist sans for everything functional (body, navigation, UI).

### Families

**Display & headings — Merriweather** (serif).
Confirmed against the live site and matching your recollection. Sturdy, large x-height, bracketed serifs; reads scholarly without feeling antique. Licensed SIL OFL, so it carries no licensing friction for the rebuild.

- The lockup "Lorena A." is Merriweather **Regular (400)** in `--color-red`.
- "Barba group" and headlines are Merriweather **Bold (700)** in `--color-ink`.

**Body, navigation & UI — Source Sans 3** (humanist sans-serif).
The legacy body face was **Source Sans Pro**, confirmed from the original 2017 design work. The system carries this forward as **Source Sans 3**, the direct successor (Adobe's renamed, updated release of the same family), so the body type continues with no visual break. It is a neutral humanist sans, pairs cleanly with Merriweather, and is SIL OFL, keeping the whole type system libre.

Set as `--font-sans`, with Source Sans Pro retained as the first fallback for continuity.

### Roles and weights

| Role | Family | Size (rem / px @16) | Weight | Tracking | Notes |
|---|---|---|---|---|---|
| Display / mark | Merriweather | 2.5 / 40 | 400 + 700 | normal | Logo lockup; mixed red/ink. |
| H1 page title | Merriweather | 2.5 / 40 | 700 | normal | e.g. "Code". |
| H2 section | Merriweather | 1.75 / 28 | 700 | normal | e.g. "Our philosophy about sharing code". |
| H3 card title | Merriweather | 1.375 / 22 | 700 | normal | Card headlines. |
| Eyebrow / nav | sans | 0.875 / 14 | 700 | 0.08em | ALL CAPS, letter-spaced. Used for the top nav and card category labels. |
| Body | sans | 1.125 / 18 | 400 | normal | Line-height 1.6. Generous measure suits the editorial tone. |
| Body strong | sans | 1.125 / 18 | 700 | normal | In-text emphasis (e.g. **reproducibility**). |
| Meta | sans | 0.875 / 14 | 400 | normal | Dates, copyright, captions; `--color-muted`. |

Type scale follows roughly a 1.25 (major-third) ratio on an 18px body base. Adjust the base, not the ratios, if you want a denser layout.

---

## 4. Iconography

The current icons are an icon font (glyph names include `genius` for research/atom, `compose` for blog, `calendar` for events, `people`, `grid`, `octocat` for GitHub, `twitter`, plus puzzle for code and document for publications).

**Visual style to preserve:**
- Solid, single-color, geometric glyphs of even visual weight, in a roughly square bounding box.
- Default fill `--color-red`; transition to `--color-icon-hover` on hover/focus.
- Flat; no outline-and-fill mixing, no gradients.

**For the rebuild:** migrate from the icon font to inline SVG. SVG is crisper, accessible (each icon can carry a label), and removes a brittle font dependency. Keep the single-color fill and the red-to-grey hover. Target a consistent 24px optical size with 1.5–2px effective stroke weight equivalent.

---

## 5. Layout

### Card system

The defining pattern: equal-width cards of variable height in a masonry grid.

- **Surface:** `--color-paper` fill, 1px `--color-hairline` border, **square corners (radius 0)**, **no shadow**.
- **Padding:** 24px internal (1.5× the 16px base). Card titles sit tight to the top edge of the content box.
- **Gutters:** consistent 24px between cards.
- **Imagery in cards:** rectangular, full-width within the padding box, no border treatment.

**For the rebuild:** the current Masonry.js plus infinite-scroll combination is the most fragile part of the experience. Replace it with CSS grid masonry (or CSS multi-column as a progressive-enhancement fallback) so the layout needs no JavaScript, and replace infinite scroll with pagination or a "load more" control for accessibility, SEO, and back-button behavior.

### Grid & spacing

- **Spacing scale:** 4px base unit — 4, 8, 12, 16, 24, 32, 48, 64.
- **Page gutters:** 32–48px on desktop, 16–24px on mobile.
- **Max content width:** cap long-form pages (e.g. Code, Research prose) around 70–75 characters per line for readability; the home grid may run wider.
- **Header:** the mark sits left, nav right, as ALL-CAPS letter-spaced sans links in `--color-ink`, hovering to `--color-red`.

### Footer

`--color-muted` copyright line, red links for Contact and social handles, small single-color social glyphs at right.

---

## 6. Imagery & the avatar motif

The avatar is a distinctive, ownable device worth formalizing as a brand motif rather than a one-off.

**The treatment:** a portrait, desaturated to black-and-white, with a hand-drawn ink sketch overlaying part of the figure (hair and collar linework), set on a flat full-bleed Barba Red field, in a square format.

**Rules:**
- Background: flat `--color-red` (reconcile the existing `#E7181E` to this value).
- Subject: desaturated B&W, no duotone.
- Linework: ink black for primary strokes; `--color-slate` permitted as a sparing secondary accent only.
- Format: 1:1 for avatars; the same treatment can extend to wider crops for headers and slides.

**Photographs in content** (people, events, news) stay as straightforward rectangular images, undecorated. The sketch-on-red treatment is reserved for the personal/brand mark, so it stays special.

---

## 7. Implementation: design tokens

Paste-ready CSS custom properties. These are the single source of color and type for the rebuild; reference the variables, never raw hex, in component CSS.

```css
:root {
  /* Color — core */
  --color-red:         #CE2406;
  --color-red-deep:    #A51D04;
  --color-red-wash:    #FBEAE6;
  --color-ink:         #181712;
  --color-paper:       #FFFFFF;
  --color-hairline:    #EAEBE6;
  --color-muted:       #787876;
  --color-muted-soft:  #B4B4B2;
  --color-icon-hover:  #9C9C9A;

  /* Color — illustration accent (non-UI) */
  --color-slate:       #546E7D;

  /* Type families */
  --font-serif: "Merriweather", Georgia, "Times New Roman", serif;
  --font-sans:  "Source Sans 3", "Source Sans Pro", system-ui,
                -apple-system, "Segoe UI", Roboto, sans-serif;

  /* Type scale (18px body base, ~1.25 ratio) */
  --text-meta:    0.875rem;  /* 14px */
  --text-body:    1.125rem;  /* 18px */
  --text-h3:      1.375rem;  /* 22px */
  --text-h2:      1.75rem;   /* 28px */
  --text-h1:      2.5rem;    /* 40px */
  --leading-body: 1.6;
  --tracking-caps: 0.08em;

  /* Spacing (4px base) */
  --space-1: 4px;   --space-2: 8px;   --space-3: 12px;
  --space-4: 16px;  --space-6: 24px;  --space-8: 32px;
  --space-12: 48px; --space-16: 64px;

  /* Surfaces */
  --card-border: 1px solid var(--color-hairline);
  --card-radius: 0;
  --card-padding: var(--space-6);
  --grid-gutter: var(--space-6);
}

/* Element defaults */
body {
  color: var(--color-ink);
  background: var(--color-paper);
  font-family: var(--font-sans);
  font-size: var(--text-body);
  line-height: var(--leading-body);
}
h1, h2, h3 { font-family: var(--font-serif); font-weight: 700; }
a { color: var(--color-red); }
a:hover, a:active { color: var(--color-red-deep); }
.eyebrow, nav a {
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: var(--tracking-caps);
}
.icon { fill: var(--color-red); transition: fill .15s ease; }
.icon:hover { fill: var(--color-icon-hover); }
.card {
  background: var(--color-paper);
  border: var(--card-border);
  border-radius: var(--card-radius);
  padding: var(--card-padding);
}
```

---

## 8. Open questions / decisions to lock

1. **Canonical red:** confirm `#CE2406` (recommended) versus the brighter avatar `#E7181E`. One value, everywhere.
2. **Body sans (resolved):** the legacy face is Source Sans Pro, adopted forward as its successor Source Sans 3. No decision pending.
3. **Rebuild stack:** the layout decisions here assume a move off Masonry.js + infinite scroll to CSS grid + pagination. Confirm before component work begins.
