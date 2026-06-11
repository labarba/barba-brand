# Lorena A. Barba group brand

Brand and design system for the computational research group of Prof. Lorena A. Barba (mechanical and aerospace engineering, the George Washington University). Editorial and restrained: serif-forward and strictly two-color, red and warm black on white.

The system has two tonal registers on one spine: a disciplined, serious default, and a playful, artsy mode that uses red as a full field and a hand-drawn, black-and-white-on-red portrait motif. Default to the serious register unless a project asks otherwise.

The brand extends into two layers, then translate that down into each tool.
> Keeps one brand with a tonal dial.

**Layer 1, the core (already in DESIGN.md).** The spine that never moves: Merriweather plus Source Sans 3; Barba Red and warm Ink on Paper; square corners, hairline rules, flat surfaces; the portrait-on-red sketch motif as the personal mark.

**Layer 2, the register dial.** The serious/playful split you described is not two brands; it is the same spine with about five levers turned up or down:

1. *Red quantity.* Serious uses red as punctuation only (the mark, a rule, one accent), so pages read mostly ink-on-paper; playful lets red become a field, the way the avatar does.
2. *The sketch motif.* Serious omits it or keeps it to the mark; playful promotes the ink linework and slate accent into an active language: annotations, frames, doodled arrows, the B&W-on-red treatment applied beyond the avatar.
3. *Type contrast.* Serious keeps moderate size jumps and restrained Merriweather; playful goes big and dramatic with pull quotes.
4. *Layout density.* Serious is a structured grid with generous margins; playful is looser, asymmetric, more masonry energy.
5. *Imagery.* Serious uses straight, undecorated photography; playful uses the treated, collaged, sketched style.

Then each surface is a thin translation layer that picks a default position on the dial and adapts to its tool's limits:

| Surface | Register default | Tooling reality | Kit contains |
|---|---|---|---|
| Site rebuild | Serious chrome, playful in blog/content | Full CSS | The `tokens.css` already drafted; component specs |
| Course sites (GitHub Pages sites) | Serious, clean | Full CSS, static | One shared brand stylesheet plus component specs |
| Slides | Dial per audience | Google Slides or HTML | Master template with a few layouts |
| Consulting proposals | Serious end | Google Docs / PDF | Cover, type styles, section system |
| Social / content | Playful end | Canva | Hex list, fonts, the motif, post templates |

Keep all of it in one versioned repo (DESIGN.md at the root, one folder per kit) for a single source of truth.

- `tokens.css` is a single, authoritative list of the brand's colors, type, and spacing, expressed as CSS so any site can reference `var(--color-red)` instead of hardcoding `#CE2406` everywhere. Change the value once, and everything that uses it updates.
- `base.css` contains the base styles that use the design tokens (load after `tokens.css`)
