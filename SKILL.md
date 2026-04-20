---
name: wiom-design-system
description: >
  Wiom Design System — the single source of truth for all Wiom org tools.
  Desktop-first, light mode only. 64 color tokens (bg/text/stroke/icon/CTA/overlay), 16 typography, 14 spacing, 7 radius, 2 stroke, 5 shadow,
  12-column grid, 3 container variants, 3 layout patterns, Material Icons Filled, Noto Sans,
  Nielsen's 10 heuristics, WCAG AA accessibility.
  Use EVERY TIME you build, review, or edit any UI for Wiom.
  Trigger on: colors, fonts, spacing, padding, margin, icons, breakpoints, responsive, accessibility,
  border-radius, box-shadow, border, layout, grid, heuristics, UX review, design system, wiom ui.
---

# Wiom Design System

**Desktop-first · Light mode only · Web (CSS variables) · Font: Noto Sans · Icons: Material Icons Filled**

**Context:** Wiom builds tools for org-level use across teams. Design for desktop first (1360px default container), then make responsive for tablet and mobile. Support Hindi + English. Prioritize clarity, consistency, and accessibility.

---

## 0. Rules

### Do

1. **Use CSS variables for everything.** `var(--wiom-bg-brand)`, `var(--wiom-text-default)`, `var(--wiom-space-16)`, etc. Never raw hex or px in component styles.
2. **Desktop-first, then responsive.** Design for desktop (1360px container) first, then adapt down to tablet and mobile. Start wide — multi-column grids, side-by-side panels, proper desktop patterns — then collapse for smaller screens.
3. **Use the 12-column grid.** `.wiom-grid` with `.wiom-col-*` spans, or preset grids (`.wiom-grid-2`, `.wiom-grid-3`, `.wiom-grid-4`).
4. **Use display tokens for hero/section headers.** `display.2xl` (72px), `display.xl` (60px), `display.md` (40px) — these scale down automatically via responsive CSS.
5. **Use generous spacing on desktop.** Hero sections: `space-120` to `space-160`. Standard sections: `space-96`. These scale down on smaller screens.
6. **Use the text color hierarchy.** `text.default` → `text.subtle` → `text.disabled`. Use `text.brand`, `text.positive`, `text.critical` for semantic inline text.
7. **Use layout patterns for page structure.** Sidebar layout for dashboards/admin. Top nav for marketing/public. Content + aside for detail pages.
8. **WCAG AA minimum.** All text must pass 4.5:1 contrast ratio. Touch/click targets minimum 48px for actions, 32px for navigation, 24px for info.
9. **Use gap-only spacing.** Parents own the gap between children. Children own their internal padding. No margins — ever.
10. **Full-bleed sections on desktop.** Section backgrounds stretch edge-to-edge (100vw, zero horizontal padding). Only the inner container constrains content width. Horizontal padding only applies on mobile/tablet (24px tablet, 16px mobile).

### Don't

1. **No dark mode.** Never generate dark mode variants, dark backgrounds, or dark themes unless explicitly requested.
2. **No gradients.** Use solid fills from the token system only. No linear-gradient, radial-gradient, or gradient overlays.
3. **No custom colors.** Every color must map to a semantic token. If no token fits, flag it — do not invent.
4. **No hardcoded values.** No raw hex, px, or font sizes outside the token scale. If it's not a token, don't use it.
5. **No mobile-first layout thinking.** Don't design narrow single-column layouts and stretch them for desktop. Start wide, then collapse for mobile.
6. **No decorative pseudo-elements without purpose.** Don't add timeline dots, ornamental shapes, or decorative `::before`/`::after` elements unless they serve a clear functional role.
7. **No centered-everything layouts.** Centered text and narrow stacked layouts feel like stretched mobile pages. Use left-aligned content, multi-column grids, and side panels on desktop.
8. **No icon libraries other than Material Icons Filled.** No outlined, rounded, sharp, or two-tone variants. No Lucide, Phosphor, or custom SVGs unless explicitly approved.
9. **No font other than Noto Sans.** Load via Google Fonts or local files.
10. **No border AND shadow on the same element.** Pick one. Flat = border. Elevated = shadow.

### Footer

- Always use `var(--wiom-bg-brand-bold)` (#443152) as footer background.
- Footer text: `var(--wiom-text-on-brand)` (#FFFFFF) for primary, `rgba(255,255,255,0.6)` for secondary/links.
- Footer links: `rgba(255,255,255,0.6)` default → `#FFFFFF` on hover.
- This applies to all pages. The footer is the one standard dark surface.

---

## 1. Color System — Light Mode Only

Use ONLY semantic tokens. CSS variable format: `var(--wiom-bg-default)`, `var(--wiom-text-default)`, etc.

### bg.* — Backgrounds & Fills (15 tokens)

#### Neutrals
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `bg.default` | `--wiom-bg-default` | #FAF9FC | Page bg, card, modal, input fill |
| `bg.subtle` | `--wiom-bg-subtle` | #F1EDF7 | Hover rows, section cards, shimmer |
| `bg.muted` | `--wiom-bg-muted` | #E8E4F0 | Grouped sections, skeleton fills |
| `bg.disabled` | `--wiom-bg-disabled` | #D7D3E0 | Disabled control backgrounds |
| `bg.inverse` | `--wiom-bg-inverse` | #161021 | Dark hero, footer, dark sections |
| `bg.selected` | `--wiom-bg-selected` | #FFCCED | Selected tab bg, active chip, current row |

#### Brand (non-action surfaces)
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `bg.brand.subtle` | `--wiom-bg-brand-subtle` | #FFE5F6 | Soft brand surface |
| `bg.brand.bold` | `--wiom-bg-brand-bold` | #443152 | Premium surfaces, partner headers, **footer** |

#### Status
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `bg.positive.subtle` | `--wiom-bg-positive-subtle` | #E1FAED | Success banner bg |
| `bg.positive` | `--wiom-bg-positive` | #008043 | Solid success fill (badge) |
| `bg.critical.subtle` | `--wiom-bg-critical-subtle` | #FFE5E7 | Error banner bg |
| `bg.warning.subtle` | `--wiom-bg-warning-subtle` | #FFE9A1 | Warning banner bg |
| `bg.warning` | `--wiom-bg-warning` | #E2B203 | Solid warning fill (badge) |
| `bg.info.subtle` | `--wiom-bg-info-subtle` | #F1E5FF | Info banner bg |
| `bg.info` | `--wiom-bg-info` | #6D17CE | Solid info fill (badge) |

### text.* — Foreground Text (11 tokens)

| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `text.default` | `--wiom-text-default` | #161021 | Headings, body, labels, warning banner text |
| `text.subtle` | `--wiom-text-subtle` | #5C5570 | Descriptions, placeholders, metadata |
| `text.disabled` | `--wiom-text-disabled` | #A7A1B2 | Disabled text (sub-AA intentional) |
| `text.inverse` | `--wiom-text-inverse` | #FAF9FC | Text on dark neutral surfaces |
| `text.selected` | `--wiom-text-selected` | #D9008D | Selected tab label, active chip |
| `text.positive` | `--wiom-text-positive` | #008043 | Success text |
| `text.onPositive` | `--wiom-text-on-positive` | #FFFFFF | Text on `bg.positive` |
| `text.critical` | `--wiom-text-critical` | #D92130 | Error text, required asterisk |
| `text.onCritical` | `--wiom-text-on-critical` | #FFFFFF | Text on `bg.critical` |
| `text.onWarning` | `--wiom-text-on-warning` | #372902 | Text on `bg.warning` (dark olive on gold) |
| `text.info` | `--wiom-text-info` | #6D17CE | Info text |
| `text.onInfo` | `--wiom-text-on-info` | #FFFFFF | Text on `bg.info` |

**No `text.warning` token.** Warning text is always `text.default`.

### stroke.* — Borders & Focus Rings (11 tokens)

#### Neutrals
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `stroke.default` | `--wiom-stroke-default` | #E8E4F0 | Inner-card dividers, light separators |
| `stroke.subtle` | `--wiom-stroke-subtle` | #D7D3E0 | Card outlines, input borders (rest) |
| `stroke.strong` | `--wiom-stroke-strong` | #473F55 | Checkbox/radio borders (small controls) |
| `stroke.selected` | `--wiom-stroke-selected` | #D9008D | Selected tab, active chip border |

#### Brand
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `stroke.brand` | `--wiom-stroke-brand` | #FFB2E4 | Soft decorative brand borders |
| `stroke.brand.focus` | `--wiom-stroke-brand-focus` | #D9008D | Secondary CTA border + keyboard focus ring |

#### Status
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `stroke.positive` | `--wiom-stroke-positive` | #A5E5C6 | Success card outline |
| `stroke.critical` | `--wiom-stroke-critical` | #FFB3B9 | Error outline |
| `stroke.critical.focus` | `--wiom-stroke-critical-focus` | #D92130 | Invalid input, destructive focus |
| `stroke.warning` | `--wiom-stroke-warning` | #E2B203 | Warning card border |
| `stroke.info` | `--wiom-stroke-info` | #D6B2FF | Info card outline |

### icon.* — Icon Tints (9 tokens)

| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `icon.nonAction` | `--wiom-icon-non-action` | #A7A1B2 | Decorative / non-actionable icons |
| `icon.action` | `--wiom-icon-action` | #352D42 | Actionable icons (back, close, menu, tappable) |
| `icon.inverse` | `--wiom-icon-inverse` | #FAF9FC | Icons on dark surfaces, inside Primary/Destructive CTAs |
| `icon.brand` | `--wiom-icon-brand` | #D9008D | Brand accent (selected check) |
| `icon.positive` | `--wiom-icon-positive` | #008043 | Success |
| `icon.critical` | `--wiom-icon-critical` | #D92130 | Error |
| `icon.warning` | `--wiom-icon-warning` | #E2B203 | Warning (only inside `bg.warning.subtle`) |
| `icon.info` | `--wiom-icon-info` | #6D17CE | Info |
| `icon.disabled` | `--wiom-icon-disabled` | #D7D3E0 | Disabled icons |

### CTA Tokens — 5 Types (17 action tokens)

#### Primary CTA (max 1 per screen)
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `bg.brand` | `--wiom-bg-brand` | #D9008D | Primary fill (rest) |
| `bg.brand.hover` | `--wiom-bg-brand-hover` | #C00080 | Primary hover |
| `bg.brand.pressed` | `--wiom-bg-brand-pressed` | #A30070 | Primary pressed |
| `text.onBrand` | `--wiom-text-on-brand` | #FFFFFF | Primary label |

#### Secondary CTA (outlined, no rest fill)
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `text.brand` | `--wiom-text-brand` | #D9008D | Label (rest + pressed) |
| `text.brand.hover` | `--wiom-text-brand-hover` | #C00080 | Label on hover |
| `stroke.brand.focus` | `--wiom-stroke-brand-focus` | #D9008D | Border (rest) + focus ring |

#### Tertiary CTA (text-only, no fill or border)
Uses same tokens as Secondary: `text.brand`, `text.brand.hover`, `bg.brand.subtle` (pressed fill)

#### Destructive CTA (irreversible actions only, max 1 per screen)
| Token | CSS Variable | Hex | Use |
|---|---|---|---|
| `bg.critical` | `--wiom-bg-critical` | #D92130 | Destructive fill (rest) |
| `bg.critical.hover` | `--wiom-bg-critical-hover` | #BF1D2A | Destructive hover |
| `bg.critical.pressed` | `--wiom-bg-critical-pressed` | #A31824 | Destructive pressed |
| `text.onCritical` | `--wiom-text-on-critical` | #FFFFFF | Destructive label |

**Red button rule:** Destructive is ONLY for irreversible actions (delete data, cancel plan). Never for "Skip", "Cancel", "No thanks" — those use Secondary/Tertiary.

### overlay.* — Scrims (1 token)
| Token | CSS Variable | Value | Use |
|---|---|---|---|
| `overlay.scrim` | `--wiom-overlay-scrim` | rgba(22,16,33,0.50) | Modal backdrop, bottom sheet scrim |

### Color Decision Tree

```
Text on a filled CTA (brand primary, destructive)?
  → var(--wiom-text-on-brand) or var(--wiom-text-on-critical)    #FFFFFF

Text on a dark neutral surface (inverse, footer)?
  → var(--wiom-text-inverse)                                      #FAF9FC

Text on a warning badge/fill?
  → var(--wiom-text-on-warning)                                   #372902

Heading, label, input value, primary content?
  → var(--wiom-text-default)                                      #161021

Description, helper, placeholder, metadata?
  → var(--wiom-text-subtle)                                       #5C5570

Selected tab/chip label?
  → var(--wiom-text-selected)                                     #D9008D

Inline link or CTA label?
  → var(--wiom-text-brand)                                        #D9008D

Inline success text ("Active", "Verified")?
  → var(--wiom-text-positive)                                     #008043

Inline error text, validation?
  → var(--wiom-text-critical)                                     #D92130

Disabled?
  → var(--wiom-text-disabled)                                     #A7A1B2

Default icon (decorative, non-tappable)?
  → var(--wiom-icon-non-action)                                   #A7A1B2

Actionable icon (back, close, menu)?
  → var(--wiom-icon-action)                                       #352D42

Status icon?
  → Use matching: icon.positive / icon.critical / icon.warning / icon.info
  → Warning icon ONLY valid inside bg.warning.subtle surface
```

### Quick Hex Lookup

```
BG:        #FAF9FC  #F1EDF7  #E8E4F0  #D7D3E0  #161021  #FFCCED  #FFE5F6  #443152
BG STATUS: #E1FAED  #008043  #FFE5E7  #FFE9A1  #E2B203  #F1E5FF  #6D17CE
TEXT:      #161021  #5C5570  #A7A1B2  #FAF9FC  #D9008D  #008043  #D92130  #6D17CE  #372902  #FFFFFF
STROKE:    #E8E4F0  #D7D3E0  #473F55  #D9008D  #FFB2E4  #A5E5C6  #FFB3B9  #E2B203  #D6B2FF
ICON:      #A7A1B2  #352D42  #FAF9FC  #D9008D  #008043  #D92130  #E2B203  #6D17CE  #D7D3E0
CTA:       #D9008D  #C00080  #A30070  #D92130  #BF1D2A  #A31824  #FFFFFF
OVERLAY:   rgba(22,16,33,0.50)
```

---

## 2. Typography — 16 Semantic Tokens

**Font: Noto Sans** (load via Google Fonts or local files). All sizes in rem (base 16px). Never use sizes outside this scale.

### Token Table

| Token | CSS Variable | Size | Weight | Line Height | Letter Spacing | Use for |
|-------|-------------|------|--------|-------------|----------------|---------|
| `type.display.2xl` | `--wiom-type-display-2xl` | 4.5rem (72px) | 700 | 5rem (80px) | -0.03em | Landing page hero, campaign splash, marketing headline |
| `type.display.xl` | `--wiom-type-display-xl` | 3.75rem (60px) | 700 | 4.25rem (68px) | -0.025em | Campaign headers, feature showcase, product hero |
| `type.display.lg` | `--wiom-type-display-lg` | 3rem (48px) | 700 | 4rem (64px) | -0.02em | Desktop hero, splash, section marketing |
| `type.display.md` | `--wiom-type-display-md` | 2.5rem (40px) | 700 | 3rem (48px) | -0.02em | Sub-hero, large callouts, desktop section headers |
| `type.heading.xl` | `--wiom-type-heading-xl` | 2rem (32px) | 700 | 2.75rem (44px) | -0.01em | Section hero |
| `type.heading.lg` | `--wiom-type-heading-lg` | 1.5rem (24px) | 700 | 2rem (32px) | -0.01em | Page title, dialog header |
| `type.heading.md` | `--wiom-type-heading-md` | 1.25rem (20px) | 700 | 1.75rem (28px) | -0.01em | Card group title, sub-section |
| `type.title.lg` | `--wiom-type-title-lg` | 1.25rem (20px) | 500 | 1.75rem (28px) | -0.01em | Nav/toolbar title |
| `type.title.sm` | `--wiom-type-title-sm` | 1rem (16px) | 700 | 1.5rem (24px) | 0 | Card title, list header |
| `type.body.lg` | `--wiom-type-body-lg` | 1rem (16px) | 400 | 1.5rem (24px) | 0 | Long-form, descriptions |
| `type.body.md` | `--wiom-type-body-md` | 0.875rem (14px) | 400 | 1.25rem (20px) | 0 | Default paragraph, inputs |
| `type.body.sm` | `--wiom-type-body-sm` | 0.75rem (12px) | 400 | 1rem (16px) | 0 | Caption, helper, footnote |
| `type.label.lg` | `--wiom-type-label-lg` | 1rem (16px) | 600 | 1.5rem (24px) | 0.01em | Button text, CTA |
| `type.label.md` | `--wiom-type-label-md` | 0.875rem (14px) | 600 | 1.25rem (20px) | 0.01em | Input label, nav item, small button |
| `type.label.sm` | `--wiom-type-label-sm` | 0.75rem (12px) | 600 | 1rem (16px) | 0.01em | Chip, badge, tag |
| `type.meta.xs` | `--wiom-type-meta-xs` | 0.625rem (10px) | 400 | 1rem (16px) | 0.02em | Timestamps and badges ONLY |

### Token Selector — "What is this text's job?"

```
Landing page hero / campaign splash?         → display.2xl  (72px Bold)
Campaign header / product hero?              → display.xl   (60px Bold)
Desktop hero / splash / marketing?           → display.lg   (48px Bold)
Sub-hero / large callout / desktop section?  → display.md   (40px Bold)
Section hero / feature highlight?            → heading.xl   (32px Bold)
Page title / dialog header?                  → heading.lg   (24px Bold)
Card group title / sub-section?              → heading.md   (20px Bold)
Nav / toolbar / prominent card title?        → title.lg     (20px Medium)
Card title / list group header?              → title.sm     (16px Bold)
Long-form reading / description?             → body.lg      (16px Regular)
Default paragraph / input value?             → body.md      (14px Regular)
Caption / helper text / footnote?            → body.sm      (12px Regular)
Default button / primary CTA?               → label.lg     (16px SemiBold)
Input label / nav item / compact button?     → label.md     (14px SemiBold)
Chip / badge / tag?                          → label.sm     (12px SemiBold)
Timestamp / badge number?                    → meta.xs      (10px Regular) ⚠ RESTRICTED
```

**If unsure:** `body.md` for reading text, `label.md` for interactive text.

### Google Fonts Setup

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

## 3. Spacing — 4px Grid, 14 Semantic Tokens

Every spacing, sizing, padding, and margin value must be a **multiple of 4px**.

### Token Table

| Token | CSS Variable | Value | Use for |
|-------|-------------|-------|---------|
| `space-4` | `--wiom-space-4` | 4px | Chip icon → label, tight inline elements |
| `space-8` | `--wiom-space-8` | 8px | Inline pairs, related items in a group |
| `space-12` | `--wiom-space-12` | 12px | Between list items, component internals |
| `space-16` | `--wiom-space-16` | 16px | Card padding, screen margins, heading → body |
| `space-24` | `--wiom-space-24` | 24px | Between sections within a card, dialog padding |
| `space-32` | `--wiom-space-32` | 32px | Between major content blocks, content → CTA |
| `space-40` | `--wiom-space-40` | 40px | Section breaks on a page |
| `space-48` | `--wiom-space-48` | 48px | Touch target height, page-level margins |
| `space-64` | `--wiom-space-64` | 64px | Large layout gaps, section padding (mobile) |
| `space-72` | `--wiom-space-72` | 72px | Hero content areas |
| `space-84` | `--wiom-space-84` | 84px | Full-width section padding (tablet) |
| `space-96` | `--wiom-space-96` | 96px | Large section padding (desktop) |
| `space-120` | `--wiom-space-120` | 120px | Hero section vertical padding (desktop) |
| `space-160` | `--wiom-space-160` | 160px | Full-bleed section breathing room (desktop) |

### Spacing Hierarchy

| Level | Range | What it groups | Examples |
|-------|-------|----------------|----------|
| **Tight** | 4–12px | One unit | Icon + label, title + subtitle |
| **Medium** | 16–24px | Same section | List items, card internals |
| **Loose** | 32–48px | Separate sections | Section breaks, content → CTA |
| **Layout** | 64–160px | Page-level sections | Hero padding, section gaps, full-bleed breathing room |

### Gap-Only Rule

**Parents own the gap between children. Children own their internal padding. No margins — ever.**

```css
/* ✅ Correct */
.card-list { display: flex; flex-direction: column; gap: var(--wiom-space-16); }
.card { padding: var(--wiom-space-16); }

/* ❌ Wrong — margin on child */
.card { margin-bottom: 16px; }
```

### Common Spacing Recipes

| Context | Value |
|---------|-------|
| Card padding | 16px all sides |
| Between cards | 16px gap |
| Title → subtitle | 8px |
| Title → body text | 12px |
| Icon → text (inline) | 12px |
| Content → CTA | 32px |
| Between stacked inputs | 16px |
| Page horizontal padding | 16px |
| Section → section | 32px |

---

## 4. Iconography — Material Icons Filled

**Library:** Google Material Icons (Filled variant only). No outlined, rounded, sharp, or two-tone variants. No custom SVGs unless explicitly approved.

### Setup

```html
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
```

### Usage

```html
<span class="material-icons">home</span>
<span class="material-icons">search</span>
<span class="material-icons">settings</span>
```

### Size Tokens

| Token | Icon Size | Container | Touch Target | Use for |
|-------|-----------|-----------|-------------|---------|
| `icon.xs` | 16px | 24px | 40px | Inline indicators, input trailing icons only |
| `icon.sm` | 20px | 32px | 40px | Button icons, compact controls |
| `icon.md` | 24px | 40px | 48px | **Default.** Toolbar, nav, list, cards |
| `icon.lg` | 48px | 56px | 56px | Empty states, onboarding, hero |

### CSS for icon sizes

```css
.icon-xs { font-size: 16px; }
.icon-sm { font-size: 20px; }
.icon-md { font-size: 24px; }  /* default */
.icon-lg { font-size: 48px; }
```

### Icon Color Rules

| Context | CSS Variable | Hex |
|---------|-------------|-----|
| Default (decorative, non-tappable) | `--wiom-icon-non-action` | `#A7A1B2` |
| Actionable (back, close, menu) | `--wiom-icon-action` | `#352D42` |
| Disabled | `--wiom-icon-disabled` | `#D7D3E0` |
| On colored fill / dark surface | `--wiom-icon-inverse` | `#FAF9FC` |
| Success | `--wiom-icon-positive` | `#008043` |
| Error | `--wiom-icon-critical` | `#D92130` |
| Warning (only inside `bg.warning.subtle`) | `--wiom-icon-warning` | `#E2B203` |
| Info | `--wiom-icon-info` | `#6D17CE` |
| Brand emphasis (selected) | `--wiom-icon-brand` | `#D9008D` |

**Never** use `icon.warning` (#E2B203) on white backgrounds — only valid inside `bg.warning.subtle` surfaces.

---

## 5. Radius — 7 Tokens

| Token | CSS Variable | Value | Use for |
|-------|-------------|-------|---------|
| `radius-none` | `--wiom-radius-none` | 0px | Table cells, app bar, square thumbnails |
| `radius-tiny` | `--wiom-radius-tiny` | 4px | Badges, tags, tooltips |
| `radius-small` | `--wiom-radius-small` | 8px | Chips, snackbars, small containers |
| `radius-medium` | `--wiom-radius-medium` | 12px | Input fields, nested containers |
| `radius-large` | `--wiom-radius-large` | 16px | Buttons, cards, main containers |
| `radius-xlarge` | `--wiom-radius-xlarge` | 24px | Dialogs, modals, bottom sheets |
| `radius-full` | `--wiom-radius-full` | 9999px | Avatars, pills, FABs, toggles |

**Nested rule:** inner-radius = outer-radius - padding. Example: 16px outer + 4px padding → 12px inner.

---

## 6. Stroke — 2 Tokens

| Token | CSS Variable | Value | Use for |
|-------|-------------|-------|---------|
| `stroke-small` | `--wiom-stroke-small` | 1px | Dividers, card outlines, input borders (rest) |
| `stroke-medium` | `--wiom-stroke-medium` | 2px | Active inputs, selected states, error states, focus rings |

**Rules:**
- A component uses EITHER a border OR a shadow, never both.
- Filled/checked/toggled states = no border (the fill IS the boundary).
- Borders are always `solid`. Dashed only for upload zones / empty states.

---

## 7. Shadow — 5 Tokens

| Token | CSS Variable | Value | Use for |
|-------|-------------|-------|---------|
| `shadow.none` | `--wiom-shadow-none` | `none` | Buttons, inputs, flat surfaces |
| `shadow.sm` | `--wiom-shadow-sm` | `0 1px 3px 0 rgba(0,0,0,0.15)` | Sticky nav (scrolled), tooltips |
| `shadow.md` | `--wiom-shadow-md` | `0 2px 6px 0 rgba(0,0,0,0.15)` | Cards, bottom sheets, dropdowns, FAB |
| `shadow.lg` | `--wiom-shadow-lg` | `0 4px 12px 0 rgba(0,0,0,0.15)` | Floating toasts, dropdowns over busy bg |
| `shadow.xl` | `--wiom-shadow-xl` | `0 8px 24px 0 rgba(0,0,0,0.15)` | Modal dialogs (always with overlay backdrop) |

**Rules:**
- Default to `shadow.md` for elevated components.
- Max 1–2 `shadow.lg` per screen.
- `shadow.xl` always paired with `--wiom-overlay-scrim`.
- Shadow OR border — never both (exception: payment cards on budget devices).

---

## 8. Layout — 12-Column Grid & Responsive Breakpoints

Benchmarked against Carbon (IBM), Primer (GitHub), and Polaris (Shopify). 12-column grid with 5 breakpoints, 3 container variants, and canonical layout patterns.

### 12-Column Grid System

| Breakpoint | Name | Min Width | Columns | Gutter | Page Margin | Container Behavior |
|-----------|------|-----------|---------|--------|-------------|-------------------|
| `xs` | Mobile | 0px | 4 | 16px | 16px | Fluid (full-width) |
| `sm` | Mobile Large | 576px | 4 | 16px | 16px | Fluid (full-width) |
| `md` | Tablet | 768px | 8 | 24px | 24px | Fluid (full-width) |
| `lg` | Desktop | 1024px | 12 | 24px | 40px | Fluid up to max-width |
| `xl` | Desktop Large | 1440px | 12 | 32px | auto | Centered, max-width |

**Column math:** Content width = container - (2 x margin). Column width = (content - (11 x gutter)) / 12.

### Container Variants

Three container types for different content needs:

| Variant | CSS Class | Max Width | Use for |
|---------|----------|-----------|---------|
| **Narrow** | `.wiom-container-narrow` | 680px | Forms, articles, reading-heavy pages, single-column flows |
| **Default** | `.wiom-container` | 1360px | Standard pages, dashboards, list views |
| **Wide** | `.wiom-container-wide` | 1600px | Data-dense dashboards, admin tools, full-width layouts |

```css
/* Narrow — forms, articles, single-column content */
.wiom-container-narrow {
  max-width: 680px;
  margin-inline: auto;
}

/* Default — standard pages */
.wiom-container {
  max-width: 1360px;
  margin-inline: auto;
}

/* Wide — data-dense dashboards */
.wiom-container-wide {
  max-width: 1600px;
  margin-inline: auto;
}

/* Desktop (1024px+): zero padding — max-width + auto margins handle centering.
   Below desktop: progressive padding so content never sticks to screen edges. */
@media (max-width: 1023px) {
  .wiom-container-narrow,
  .wiom-container,
  .wiom-container-wide { padding-inline: var(--wiom-space-24); }  /* Tablet: 24px */
}

@media (max-width: 767px) {
  .wiom-container-narrow,
  .wiom-container,
  .wiom-container-wide { padding-inline: var(--wiom-space-16); }  /* Mobile: 16px */
}
```

**Responsive padding scale:** Desktop = 0 (container handles it) → Tablet = 24px → Mobile = 16px. Content never touches the screen edges.

### 12-Column Grid Utilities

```css
/* Base grid — use spans to size columns */
.wiom-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--wiom-space-16);
}

@media (min-width: 768px) {
  .wiom-grid { gap: var(--wiom-space-24); }
}

@media (min-width: 1440px) {
  .wiom-grid { gap: var(--wiom-space-32); }
}

/* Column spans */
.wiom-col-1  { grid-column: span 1; }
.wiom-col-2  { grid-column: span 2; }
.wiom-col-3  { grid-column: span 3; }   /* 25% — quarter */
.wiom-col-4  { grid-column: span 4; }   /* 33% — third */
.wiom-col-5  { grid-column: span 5; }
.wiom-col-6  { grid-column: span 6; }   /* 50% — half */
.wiom-col-7  { grid-column: span 7; }
.wiom-col-8  { grid-column: span 8; }   /* 67% — two-thirds */
.wiom-col-9  { grid-column: span 9; }   /* 75% — three-quarters */
.wiom-col-10 { grid-column: span 10; }
.wiom-col-11 { grid-column: span 11; }
.wiom-col-12 { grid-column: span 12; }  /* 100% — full width */

/* Responsive overrides */
@media (max-width: 767px) {
  [class*="wiom-col-"] { grid-column: span 4; }  /* All full-width on mobile (4-col grid) */
}

@media (min-width: 768px) and (max-width: 1023px) {
  .wiom-col-md-4 { grid-column: span 4; }  /* Half on tablet (8-col grid) */
  .wiom-col-md-8 { grid-column: span 8; }  /* Full on tablet */
}
```

### Canonical Layout Patterns

#### Pattern 1: Sidebar + Content (Dashboard, Admin)

```css
.wiom-layout-sidebar {
  display: grid;
  grid-template-columns: 280px 1fr;
  gap: 0;
  min-height: 100vh;
}

.wiom-layout-sidebar__nav {
  position: sticky;
  top: 0;
  height: 100vh;
  overflow-y: auto;
  border-right: var(--wiom-stroke-small) solid var(--wiom-stroke-subtle);
  padding: var(--wiom-space-16);
  background: var(--wiom-bg-default);
}

.wiom-layout-sidebar__content {
  padding: var(--wiom-space-32) var(--wiom-space-40);
  overflow-y: auto;
}

@media (max-width: 1023px) {
  .wiom-layout-sidebar {
    grid-template-columns: 1fr;  /* Sidebar becomes top nav or hamburger */
  }
}
```

#### Pattern 2: Top Nav + Content (Marketing, Public Pages)

```css
.wiom-layout-topnav {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.wiom-layout-topnav__header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--wiom-bg-default);
  border-bottom: var(--wiom-stroke-small) solid var(--wiom-stroke-subtle);
  padding: var(--wiom-space-16) 0;  /* zero horizontal — inner container handles width */
}

.wiom-layout-topnav__content {
  flex: 1;
}

.wiom-layout-topnav__footer {
  background: var(--wiom-bg-brand-bold);  /* #443152 — always dark footer */
  color: var(--wiom-text-inverse);
  padding: var(--wiom-space-48) 0;  /* zero horizontal padding — full-bleed */
}
```

#### Pattern 3: Content + Aside (Detail Page, Settings)

```css
.wiom-layout-aside {
  display: grid;
  grid-template-columns: 1fr 320px;
  gap: var(--wiom-space-32);
  align-items: start;
}

.wiom-layout-aside__main {
  min-width: 0;  /* Prevent grid blowout */
}

.wiom-layout-aside__sidebar {
  position: sticky;
  top: var(--wiom-space-24);
}

@media (max-width: 1023px) {
  .wiom-layout-aside {
    grid-template-columns: 1fr;  /* Stack on tablet and below */
  }

  .wiom-layout-aside__sidebar {
    position: static;
  }
}
```

### Content Grid Presets

Common content grids built on the 12-column system:

```css
/* 2-column content (6+6) */
.wiom-grid-2 {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--wiom-space-16);
}

@media (min-width: 768px) {
  .wiom-grid-2 {
    grid-template-columns: repeat(2, 1fr);
    gap: var(--wiom-space-24);
  }
}

/* 3-column content (4+4+4) */
.wiom-grid-3 {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--wiom-space-16);
}

@media (min-width: 768px) {
  .wiom-grid-3 { grid-template-columns: repeat(2, 1fr); gap: var(--wiom-space-24); }
}

@media (min-width: 1024px) {
  .wiom-grid-3 { grid-template-columns: repeat(3, 1fr); }
}

/* 4-column content (3+3+3+3) */
.wiom-grid-4 {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--wiom-space-16);
}

@media (min-width: 768px) {
  .wiom-grid-4 { grid-template-columns: repeat(2, 1fr); gap: var(--wiom-space-24); }
}

@media (min-width: 1024px) {
  .wiom-grid-4 { grid-template-columns: repeat(4, 1fr); gap: var(--wiom-space-32); }
}
```

### Responsive Typography Scaling

Display sizes scale down on smaller screens. Body, label, and meta stay fixed.

| Token | Mobile (< 768px) | Tablet (768px+) | Desktop (1024px+) | Large Desktop (1440px+) |
|-------|-------------------|-----------------|-------------------|------------------------|
| `display.2xl` | 40px | 48px | 60px | 72px |
| `display.xl` | 32px | 40px | 48px | 60px |
| `display.lg` | 28px | 36px | 40px | 48px |
| `display.md` | 24px | 32px | 36px | 40px |
| `heading.xl` | 24px | 28px | 32px | 32px |
| `heading.lg` | 20px | 22px | 24px | 24px |
| All others | No change | No change | No change | No change |

### Section Spacing Scaling

Vertical section padding also scales with viewport:

| Context | Mobile | Tablet | Desktop | Large Desktop |
|---------|--------|--------|---------|---------------|
| Hero section | `space-64` | `space-84` | `space-120` | `space-160` |
| Standard section | `space-48` | `space-64` | `space-84` | `space-96` |
| Compact section | `space-32` | `space-40` | `space-48` | `space-64` |
| Between cards | `space-16` | `space-16` | `space-24` | `space-24` |

### Desktop-First Layout Rules

1. **Full-bleed on desktop.** Sections have zero horizontal padding on desktop. Backgrounds stretch edge-to-edge. Only the inner container constrains content via `max-width` + `margin-inline: auto`. Horizontal padding only applies below 1024px (24px tablet, 16px mobile).
2. **Container max-widths:** Narrow 680px, Default 1360px, Wide 1600px. Content never stretches to full viewport — the container handles it.
3. **Reading line length:** 60–80 characters max (~600–680px). Use `.wiom-container-narrow` or `max-width` on text blocks.
4. **Sidebar layouts:** At `lg`+ breakpoints, sidebars are 280px fixed. Content fills remaining space. Collapses to hamburger on mobile/tablet.
5. **Cards:** Minimum 280px wide. On mobile, always full-width. On desktop, constrain with the grid (3-col or 4-col).
6. **Tables:** Horizontal scroll on mobile via `overflow-x: auto`. Never shrink columns below readable width.
7. **Modals:** Mobile = full-screen bottom sheet. Tablet+ = centered dialog, max-width 560px, `border-radius: var(--wiom-radius-xlarge)`.
8. **Navigation:** Mobile = bottom nav or hamburger. Desktop = sidebar (admin) or top nav (marketing).
9. **Footer:** Always `var(--wiom-bg-brand-bold)` (#443152) background. White text. The one standard dark surface on every page.
10. **Minimum touch/click targets:** 48px for actions, 32px for navigation, 24px for info — at ALL breakpoints.

### Section Pattern (Desktop)

```css
/* Section: zero horizontal padding, background full-bleed */
.section {
  padding: var(--wiom-space-96) 0;
}

/* Inner container constrains content */
.section-inner {
  max-width: var(--wiom-container-default); /* 1360px */
  margin-inline: auto;
}

/* Tablet: breathing room from edges */
@media (max-width: 1023px) {
  .section { padding-inline: var(--wiom-space-24); }
}

/* Mobile: tight but comfortable */
@media (max-width: 767px) {
  .section { padding-inline: var(--wiom-space-16); }
}
```

---

## 9. Nielsen's 10 Usability Heuristics — Wiom Application

Every UI built for Wiom must satisfy these 10 principles. Use this as a review checklist.

### 1. Visibility of System Status

The system should always keep users informed about what is going on, through appropriate feedback within reasonable time.

**Wiom application:**
- Show loading states for every async operation (API calls, data fetches, form submissions)
- Display progress indicators for multi-step flows (recharge, onboarding, booking)
- Use status colors (positive/negative/warning/info) to communicate outcomes immediately
- Show real-time connection status where relevant (online/offline indicator)
- Breadcrumbs or step indicators on multi-page flows

**Checklist:**
- [ ] Every button click shows immediate feedback (loading spinner, disabled state, or navigation)
- [ ] Form submission shows clear success or error state
- [ ] Long operations (>1s) show a progress indicator
- [ ] Current location in navigation is visually indicated (`bg.selected` + `stroke.selected`)

### 2. Match Between System and Real World

The system should speak the users' language, with words, phrases, and concepts familiar to the user, rather than system-oriented terms.

**Wiom application:**
- Use plain Hindi and English — avoid technical jargon ("session expired" → "Please log in again")
- Currency always in ₹ format, Indian number system (1,00,000 not 100,000)
- Date format: DD MMM YYYY (15 Apr 2026), time in 12-hour format with AM/PM
- Use familiar metaphors for Indian users (wallet, recharge, plan, balance)
- Error messages should explain what happened AND what to do next

**Checklist:**
- [ ] No technical error codes shown to users (no "Error 500", "null", "undefined")
- [ ] All labels use plain language the target audience understands
- [ ] Numbers, dates, and currency follow Indian conventions
- [ ] Hindi content uses conversational tone, not formal/literary Hindi

### 3. User Control and Freedom

Users often perform actions by mistake. They need a clearly marked "emergency exit" to leave the unwanted action without having to go through an extended process.

**Wiom application:**
- Every screen must have a clear back/close action
- Destructive actions require confirmation dialogs (but NOT for "Cancel" or "Skip" — those ARE the exit)
- Forms preserve entered data on accidental back navigation (use `sessionStorage` or state management)
- Multi-step flows allow going back to previous steps
- "Undo" for reversible actions (archive, remove from list) instead of confirmation dialogs

**Checklist:**
- [ ] Every modal/dialog has a close button AND backdrop click to dismiss
- [ ] Back button works predictably on every screen
- [ ] Destructive actions (delete, cancel plan) have a confirmation step
- [ ] Accidental navigation away from a form warns about unsaved changes

### 4. Consistency and Standards

Users should not have to wonder whether different words, situations, or actions mean the same thing.

**Wiom application:**
- Use the same token for the same purpose everywhere — `label.lg` for ALL primary buttons, `body.md` for ALL paragraph text
- Same interaction pattern for same action type (all filters use the same filter component, all lists scroll the same way)
- Navigation structure is consistent across all tools
- Action labels are consistent: "Save" not sometimes "Submit" or "Done" or "Apply"
- Status indication follows the same color pattern everywhere (green=success, red=error, yellow=warning, purple=info)

**Checklist:**
- [ ] Primary CTA is always `--wiom-bg-brand` fill + `--wiom-text-on-brand` text
- [ ] All form validation uses the same error pattern (red border + error text below)
- [ ] Navigation patterns match across all pages
- [ ] Terminology is consistent (pick one term and use it everywhere)

### 5. Error Prevention

Even better than good error messages is a careful design that prevents a problem from occurring in the first place.

**Wiom application:**
- Disable submit buttons until form is valid (but show why it's disabled)
- Use input masks and validation on type (phone: 10 digits, email: @ required, amount: numbers only)
- Constrain choices where possible (dropdowns over free text, date pickers over text input)
- Show character counts on limited fields before the user hits the limit
- Confirm before irreversible actions with clear consequences stated

**Checklist:**
- [ ] Required fields are marked with asterisk (using `--wiom-text-critical`)
- [ ] Input validation happens on blur, not just on submit
- [ ] Dropdown/select used instead of free text where options are finite
- [ ] Destructive buttons clearly state the consequence ("Delete this account permanently")

### 6. Recognition Rather Than Recall

Minimize the user's memory load by making objects, actions, and options visible. The user should not have to remember information from one part of the interface to another.

**Wiom application:**
- Show selected plan details on the payment screen (don't make users remember what they chose)
- Recent/frequent items at the top of lists
- Search with suggestions, not just a blank input
- Form fields with placeholder examples ("e.g., 9876543210")
- Contextual help inline, not buried in a separate help section

**Checklist:**
- [ ] Summary/review screens show all relevant details before final action
- [ ] Frequently used items are surfaced prominently (recent, favorites, suggested)
- [ ] Labels and placeholders provide enough context to act without external reference
- [ ] Navigation items have icons + labels (not just icons)

### 7. Flexibility and Efficiency of Use

Accelerators — unseen by the novice user — may speed up the interaction for the expert user, so that the design caters to both.

**Wiom application:**
- Keyboard shortcuts for power users in admin/internal tools (documented in a help panel)
- Quick actions on list items (hover actions on desktop, swipe on mobile)
- Bulk operations for admin tasks (select all, bulk update, batch export)
- Saved filters / presets for repeated queries
- Recently used / frequently used items pinned for quick access

**Checklist:**
- [ ] Common tasks are reachable in 3 clicks or fewer
- [ ] Desktop tools support keyboard navigation (Tab, Enter, Escape, arrow keys)
- [ ] Bulk actions are available where users manage multiple items
- [ ] Search/filter state is preserved across navigation

### 8. Aesthetic and Minimalist Design

Interfaces should not contain information that is irrelevant or rarely needed. Every extra unit of information competes with relevant information and diminishes their relative visibility.

**Wiom application:**
- Use progressive disclosure — show essential info first, details on demand
- Card designs show 3–5 key data points, not every field
- Empty states are helpful, not just "No data" (explain what to do next)
- Remove decorative elements that don't aid comprehension
- White space is a feature, not wasted space — use the spacing hierarchy

**Checklist:**
- [ ] Each screen has one clear primary action
- [ ] Secondary actions are visually de-emphasized (secondary/tertiary buttons)
- [ ] No more than 5–7 items in a navigation menu
- [ ] Tables show only essential columns by default (others available via column settings)

### 9. Help Users Recognize, Diagnose, and Recover from Errors

Error messages should be expressed in plain language (no codes), precisely indicate the problem, and constructively suggest a solution.

**Wiom application:**
- Error messages follow the pattern: **What happened** + **What to do** ("Payment failed. Please check your card details and try again.")
- Inline validation shows the specific field that has an error (red border + helper text)
- Network errors suggest checking connection and provide a retry button
- Form errors scroll to and focus the first errored field
- Never show stack traces, error codes, or technical details to end users

**Checklist:**
- [ ] Every error state has a user-facing message (no blank screens, no raw errors)
- [ ] Error messages suggest a concrete next action
- [ ] Form errors highlight the specific field(s) with `--wiom-stroke-critical-focus` border
- [ ] Network failures offer a "Retry" button
- [ ] 404/empty pages provide navigation back to a useful screen

### 10. Help and Documentation

Even though it is better if the system can be used without documentation, it may be necessary to provide help. Help should be easy to search, focused on the user's task, list concrete steps, and not be too large.

**Wiom application:**
- Contextual help tooltips on complex fields (info icon → tooltip, not a separate page)
- Onboarding tooltips for first-time users (dismissible, not blocking)
- Search in help/FAQ sections
- Contact support as a last resort, always accessible (not hidden behind 5 clicks)
- Help content written as task-oriented steps, not feature descriptions

**Checklist:**
- [ ] Complex inputs have an info icon with tooltip explanation
- [ ] Help/support is accessible from every screen (footer link or menu item)
- [ ] FAQ answers are task-oriented ("How to recharge" not "Recharge feature overview")
- [ ] First-time users get contextual guidance without blocking their workflow

---

## 10. Accessibility — WCAG AA Compliance

### Text Contrast (WCAG AA: 4.5:1 minimum)

All approved contrast pairings:

| Text | Background | Ratio | Status |
|------|------------|-------|--------|
| `text.default` #161021 | `bg.default` #FAF9FC | 17.71:1 | PASS |
| `text.default` #161021 | `bg.subtle` #F1EDF7 | 16.10:1 | PASS |
| `text.default` #161021 | `bg.muted` #E8E4F0 | 14.85:1 | PASS |
| `text.subtle` #5C5570 | `bg.default` #FAF9FC | 6.70:1 | PASS |
| `text.positive` #008043 | `bg.default` #FAF9FC | 5.04:1 | PASS |
| `text.critical` #D92130 | `bg.default` #FAF9FC | 4.99:1 | PASS |
| `text.brand` #D9008D | `bg.default` #FAF9FC | 4.62:1 | PASS (large text + non-text) |
| `text.inverse` #FAF9FC | `bg.inverse` #161021 | 17.71:1 | PASS |
| `text.onBrand` #FFFFFF | `bg.brand` #D9008D | 4.84:1 | PASS |
| `text.onCritical` #FFFFFF | `bg.critical` #D92130 | 4.99:1 | PASS |
| `text.onPositive` #FFFFFF | `bg.positive` #008043 | 5.04:1 | PASS |
| `text.onInfo` #FFFFFF | `bg.info` #6D17CE | 7.88:1 | PASS |
| `text.onWarning` #372902 | `bg.warning` #E2B203 | 7.16:1 | PASS |
| `text.default` #161021 | `bg.warning.subtle` #FFE9A1 | 15.62:1 | PASS |

**Pairings to AVOID:**

| Pairing | Ratio | Problem |
|---------|-------|---------|
| `text.disabled` on `bg.muted` | 2.00:1 | Unreadable |
| `icon.warning` (#E2B203) on white | 1.55:1 | Invisible — only use inside `bg.warning.subtle` |
| `text.brand` on `bg.brand.subtle` (#FFE5F6) | 4.10:1 | Fails AA for body text |

### Touch Targets

| Tier | Size | Use |
|------|------|-----|
| **Action** | 48 x 48px minimum | Delete, edit, share, close, menu, back |
| **Navigation** | 32 x 32px minimum | Expand/collapse, sort, pagination, filters |
| **Info** | 24 x 24px minimum | Help, tooltip triggers, status indicators |

A small icon (e.g., 16px) must have transparent padding extending to the target size. Use `padding` or `min-width`/`min-height`, not visible padding.

### Focus Indicators

- All interactive elements must have a visible focus indicator
- Default focus ring: `2px solid var(--wiom-stroke-brand-focus)` (#D9008D)
- Destructive focus ring: `2px solid var(--wiom-stroke-critical-focus)` (#D92130)
- Focus ring radius = element radius + 2px offset
- Never remove `outline` without adding an equivalent visible indicator

```css
/* ✅ Correct */
button:focus-visible {
  outline: 2px solid var(--wiom-stroke-brand-focus);
  outline-offset: 2px;
}

/* ❌ Wrong — removes focus indicator entirely */
button:focus { outline: none; }
```

### Keyboard Navigation

- All interactive elements reachable via Tab key
- Logical tab order (left-to-right, top-to-bottom, matching visual order)
- Enter/Space activates buttons and controls
- Escape closes modals, dropdowns, and overlays
- Arrow keys navigate within component groups (tabs, radio groups, menus)

### Screen Reader Support

- Every `<img>` needs `alt` text (decorative images: `alt=""`)
- Icon buttons need `aria-label` (e.g., `<button aria-label="Close"><span class="material-icons">close</span></button>`)
- Form inputs linked to labels via `for`/`id` or wrapping `<label>`
- Dynamic content updates use `aria-live="polite"` (errors, status changes)
- Modals trap focus and have `role="dialog"` + `aria-modal="true"`
- Hide decorative elements from screen readers with `aria-hidden="true"`

### Minimum Text Sizes

| Minimum | When |
|---------|------|
| 12px (`body.sm`) | Smallest allowed for body/reading text |
| 10px (`meta.xs`) | ONLY timestamps and badge counts — never for Hindi body text |
| 14px (`body.md`) | Recommended minimum for primary content |

---

## 11. Anti-Pattern Checklist

Before shipping any Wiom UI, verify NONE of these are present:

**Color:**
- [ ] Hardcoded hex values (use CSS variables)
- [ ] Colors not from the semantic token system (bg.*, text.*, stroke.*, icon.*, CTA)
- [ ] `icon.warning` (#E2B203) used on white bg — only valid inside `bg.warning.subtle`
- [ ] `text.onBrand` / `text.onCritical` on neutral surfaces (only for filled CTAs)
- [ ] `text.inverse` on light backgrounds
- [ ] Red button (`bg.critical`) for non-destructive actions
- [ ] Mixed status families (warning icon on error card)
- [ ] Dark mode / dark theme (not supported)
- [ ] Gradients (not supported)

**Typography:**
- [ ] Font sizes outside the 16-token scale (no 11px, 13px, 15px, 18px, 22px, 36px, 44px, 52px, 56px, 64px, 68px)
- [ ] Font other than Noto Sans
- [ ] Heading tokens for buttons (use label.lg)
- [ ] `meta.xs` used for anything other than timestamps/badges
- [ ] Body tokens for buttons or headings

**Spacing:**
- [ ] Values not on the 4px grid (no 13px, 17px, 23px)
- [ ] Margins on child components (use parent gap)
- [ ] Inconsistent padding at the same hierarchy level
- [ ] Same spacing everywhere (no hierarchy)

**Layout:**
- [ ] Content stretching beyond container max-width (680/1360/1600px)
- [ ] Text lines exceeding 80 characters
- [ ] Fixed layouts that break on mobile or large screens
- [ ] Missing responsive breakpoint adjustments
- [ ] Horizontal padding on sections at desktop (should be zero — full-bleed backgrounds)
- [ ] Centered-everything single-column layout on desktop (use multi-column grids, side panels)
- [ ] Mobile-first narrow layout stretched for desktop
- [ ] Decorative pseudo-elements (::before/::after) without functional purpose
- [ ] Footer using light surface instead of `bg.brand.bold` (#443152)

**Accessibility:**
- [ ] Text below 4.5:1 contrast ratio
- [ ] Touch/click targets below 24px
- [ ] Missing focus indicators on interactive elements
- [ ] Icon buttons without `aria-label`
- [ ] Images without `alt` text
- [ ] `outline: none` without alternative focus indicator

**Components:**
- [ ] Border AND shadow on the same element
- [ ] Border on a filled/checked/toggled element
- [ ] Same radius on nested containers (use inner = outer - padding)
- [ ] Icon sizes not in {16, 20, 24, 48}px

---

## Quick Hex Lookup

```
BG:        #FAF9FC  #F1EDF7  #E8E4F0  #D7D3E0  #161021  #FFCCED  #FFE5F6  #443152
BG STATUS: #E1FAED  #008043  #FFE5E7  #FFE9A1  #E2B203  #F1E5FF  #6D17CE
TEXT:      #161021  #5C5570  #A7A1B2  #FAF9FC  #D9008D  #008043  #D92130  #6D17CE  #372902  #FFFFFF
STROKE:    #E8E4F0  #D7D3E0  #473F55  #D9008D  #FFB2E4  #A5E5C6  #FFB3B9  #E2B203  #D6B2FF
ICON:      #A7A1B2  #352D42  #FAF9FC  #D9008D  #008043  #D92130  #E2B203  #6D17CE  #D7D3E0
CTA:       #D9008D  #C00080  #A30070  #D92130  #BF1D2A  #A31824  #FFFFFF
OVERLAY:   rgba(22,16,33,0.50)
```

---

*Wiom Design System — Org Foundations. April 2026.*
*Light mode only. Web (CSS). Noto Sans. Material Icons Filled.*
