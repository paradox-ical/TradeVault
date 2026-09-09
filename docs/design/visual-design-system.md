# Trade Vault — Visual Design System

**Approved default theme:** Obsidian Mint  
**Direction:** Dark, premium, glass-forward collector interface

## 1. Design philosophy

Trade Vault should feel like a premium digital vault rather than a generic ecommerce dashboard.

Communicate:
- security;
- precision;
- collectability;
- modern technology;
- calm;
- trust;
- depth.

> **The cards provide the colour. Trade Vault provides the atmosphere.**

## 2. Core palette

| Token | Hex | Usage |
|---|---:|---|
| `--background` | `#0B0F14` | App/page background |
| `--surface` | `#141B22` | Panels, sidebars, inputs |
| `--surface-glass` | `#1C2733` | Elevated/translucent surfaces |
| `--accent-primary` | `#2EE6C5` | Vault Mint |
| `--accent-secondary` | `#66A8FF` | Signal Blue |
| `--highlight` | `#A7F3E8` | Frosted Mint |
| `--text-primary` | `#F4F7FA` | Primary text |
| `--text-secondary` | `#9BA8B5` | Secondary text |
| `--text-muted` | `#64717E` | Muted metadata |
| `--positive` | `#46E6A5` | Gains/success |
| `--negative` | `#FF6B7A` | Loss/destructive/fail |
| `--warning` | `#F5B942` | Review/warning |

Avoid pure black as the dominant surface; tonal separation matters.

## 3. Accent use

Vault Mint is the primary brand colour.

Use for:
- primary CTA;
- active navigation;
- selected tabs;
- focus rings;
- primary charts;
- verified/trust treatment;
- progress.

Do not flood every surface with mint.

Signal Blue supports informational states, secondary charts, AI assistance and comparison states.

## 4. Liquid Glass direction

Use **restrained Liquid Glass-inspired layering**.

Conceptual surface:

```css
background: rgba(28, 39, 51, 0.68);
backdrop-filter: blur(18px) saturate(130%);
border: 1px solid rgba(167, 243, 232, 0.10);
```

Glass levels:

### Subtle Glass
Normal cards, search, standard panels.

### Floating Glass
Popovers, dropdowns, Quick Add, mobile navigation, filter panels.

### Premium Glass
Verification, Vault-held assets, grading results, hero portfolio widgets.

Premium glass may use restrained mint edge glow/light sweep.

## 5. Borders

Typical:

```text
subtle:   rgba(255,255,255,0.07)
elevated: rgba(167,243,232,0.12)
active:   Vault Mint at controlled opacity
```

Use 1px borders by default.

## 6. Shadows

Broad, low-opacity shadows.

```css
box-shadow: 0 18px 50px rgba(0,0,0,0.35);
```

Optional accent glow:

```css
0 0 30px rgba(46,230,197,0.08);
```

## 7. Gradients

Primary gradient:

`#2EE6C5 → #66A8FF`

Use sparingly for logo, progress, premium CTA, selected accents and chart strokes.

Avoid giant neon backgrounds.

## 8. Typography

Use a clean modern variable sans-serif such as Geist/Inter or equivalent.

Priorities:
- strong numeric rendering;
- high information density;
- readability;
- tabular numerals where useful.

## 9. Radius scale

- Small: 8px
- Controls: 10–12px
- Cards: 14–16px
- Major panels: 18–24px
- Floating glass: 20–28px

Avoid making everything a pill.

## 10. Motion

Motion should be quick, smooth, physical, premium and restrained.

Typical:
- microinteraction: 150–300ms;
- larger transition: 300–500ms.

Recommended:
- button press/compression;
- subtle hover elevation;
- animated tab indicator;
- modal fade/scale;
- card add-to-Vault transition;
- chart interpolation;
- subtle card image zoom/tilt.

Avoid constant motion.

## 11. Trading-card hero effects

Optional:
- shallow perspective tilt;
- soft reflection;
- holographic shimmer;
- parallax on featured items;
- premium edge lighting.

Use primarily in Showcases, verification, grading results and high-value Vault views. Bulk grids remain calm.

## 12. Navigation

Desktop: dark sidebar with mint active state and subtle tinted glass background.

Mobile: frosted bottom navigation with high contrast and restrained blur.

## 13. Buttons

### Primary
Vault Mint fill with dark text.

### Secondary
Dark glass with subtle border.

### Tertiary
Transparent/text.

### Destructive
Coral/red.

### Premium
Mint→blue gradient only when meaningfully special.

## 14. Inputs

Default dark surface + neutral border.

Focus: mint border/glow.

Error: coral/red.

AI-assisted: optional Signal Blue label such as `Detected by AI ✦`.

## 15. Trust states

- Verified: Mint
- Review: Amber
- Failed/Revoked: Red/coral
- Vault Held / Continuous Custody: stronger premium trust treatment

Never use subscription/paid status as a trust signal.

## 16. Charts

Dark minimal background, mint primary series, blue secondary series, subtle grids, clear labels.

Avoid finance-terminal clutter.

## 17. Accessibility

Required:
- strong contrast;
- visible keyboard focus;
- minimum touch targets;
- text/icons in addition to colour;
- reduced-motion support;
- readable chart labels;
- accessible glass fallbacks.

## 18. Reduced motion

When `prefers-reduced-motion` is enabled, disable/simplify card tilt, shimmer, parallax and large transitions.

## 19. Performance

Avoid dozens of simultaneous blur/animation layers.

Optimise images, large collection rendering and scroll effects. My Vault must remain smooth with thousands of assets.

## 20. Theme architecture

Use semantic design tokens. Do not scatter literal hex values through feature components.

Potential future cosmetic themes:
- Obsidian Mint — default
- Midnight Violet
- Graphite Ember
- OLED Black

## 21. Design maxim

> **Secure enough to be a Vault. Premium enough for a Black Label. Clean enough to manage 10,000 cards.**
