---
inclusion: fileMatch
fileMatchPattern: "**/*.{tsx,jsx,css}"
---

# Design System

## Writing in the product
- Short, plain sentences.
- Use animation terms as defined in the glossary in `product.md`.
- No marketing words such as "revolutionary" or "magic". No emoji in the UI.
- Button labels are verbs: "Start animating", "Generate keyframes", "Keep", "Undo", "Export".

## Logo
- The mark is three circles on a diagonal. The front circle is solid. The two circles behind it are cut by the circle in front of each, so they appear as crescents in darker shades of the accent color.
- **Construction (100 × 100 grid)**: three circles with radius 24, centers at (34, 66), (50, 50) and (66, 34), on a 45° line. Each back circle is cut by the circle in front of it enlarged to radius 28.5, which leaves a 4.5 unit gap.
- **Colors are solid fills, not transparency.**
  - On `#14111C` background: front `#FF7A1A`, middle `#A1501B`, back `#5F331B`.
  - On light background: front `#14111C`, middle `#7A7480`, back `#C9C2B9`.
  - On `#FF7A1A` background: front `#14111C`, middle and back are `#14111C` mixed with `#FF7A1A` at 60% and 30%.
- **Wordmark**: "tweenaro" in lowercase, Funnel Display weight 800, letter spacing −0.035em.
- **Lockups**: horizontal (mark to the left of the wordmark), stacked (mark above the wordmark), mark only (app icon, favicon).
- **App icon**: mark at about 74% of the tile size, tile color `#14111C`, corner radius about 23% of the tile size.
- **Minimum size**: 16 px, mark only.
- **Do not**: rotate the mark, add outlines or gradients, add more circles, use transparency for the back circles, or use colors outside this palette.

## Colors
### Backgrounds and borders (dark UI is the default)
| Token | Hex | Use |
|---|---|---|
| `bg` | `#14111C` | App background |
| `bg-stage-area` | `#100E16` | Area around the stage |
| `panel` | `#17141F` | Sidebars, top bar, timeline background |
| `surface` | `#1D1928` | Cards, inputs on panels, timeline cells |
| `surface-raised` | `#26212F` | Hover and selected nav items, chips |
| `border` | `#2C2638` | Default 1 px borders and dividers |
| `border-strong` | `#3A3446` | Input borders, outline buttons |

### Text
| Token | Hex | Use |
|---|---|---|
| `text-primary` | `#F6F1E9` | Main text on dark backgrounds |
| `text-secondary` | `#C9C3D2` | Secondary text, nav links |
| `text-muted` | `#A49FB0` | Labels, metadata, placeholders |
| `text-on-accent` | `#14111C` | Text on accent color and on light backgrounds |

### Accent
| Token | Hex | Use |
|---|---|---|
| `accent` | `#FF7A1A` | Primary buttons, active tool, keyframes on the selected layer, AI icon |
| `accent-hover` | `#FF9A4D` | Hover state for accent elements |
| `accent-tween` | `#3A2618` | Tween span on the selected layer |
| `logo-middle` | `#A1501B` | Logo middle circle on dark background |
| `logo-back` | `#5F331B` | Logo back circle on dark background |

Text on `accent` is always `#14111C`, never white.

### Stage and timeline
| Token | Hex | Use |
|---|---|---|
| `stage` | `#F6F1E9` | Default stage color |
| `stage-guide` | `#D9D1C4` | Guide lines on the stage |
| `onion-previous` | `#D14B4B` | Onion skin for previous frames |
| `onion-next` | `#3E9B6E` | Onion skin for next frames |
| `keyframe-inactive` | `#B9A8FF` | Keyframes on layers that are not selected |
| `tween-inactive` | `#2A2337` | Tween span on layers that are not selected |
| `selection` | `#FF7A1A` | Selection box, 1.5 px dashed |

### Other colors
For project thumbnails and illustrations only, not for UI controls: `#5EE6B8`, `#FFB27A`, `#B9A8FF`. Thumbnail backgrounds: `#201A2C`, `#1F2A26`, `#231D33`, `#2A1F1A`.

### Contrast
- Body text needs at least 4.5:1 contrast. Large text needs at least 3:1.
- `text-muted` passes on `bg`. Do not use `text-muted` for small text on `surface-raised`.
- Colors that must be told apart also need to differ in lightness, not only in hue.

## Typography
| Use | Font | Weights | Notes |
|---|---|---|---|
| Headings and wordmark | Funnel Display | 700, 800 | Letter spacing −0.02em to −0.035em |
| UI and body text | Onest | 400, 500, 600 | |
| Timeline numbers, timecodes, code, small uppercase labels | Martian Mono | 400, 500 | Uppercase labels use 0.08em to 0.12em letter spacing |

Do not use Inter, JetBrains Mono or Bricolage Grotesque.

### Sizes
| Token | Size / line height | Use |
|---|---|---|
| `display` | clamp(40px, 6vw, 80px) / 1.02 | Landing page headline |
| `h1` | 36 to 44 px / 1.1 | Page titles |
| `h2` | 32 to 48 px on the landing page, 18 px in the app | Section titles |
| `h3` | 19 to 22 px / 1.3, Onest 600 | Card titles |
| `body` | 15 to 16 px / 1.55 | Body text |
| `small` | 13 to 14 px | Metadata, buttons in dense areas |
| `micro` | 11 to 12 px, Martian Mono | Timeline numbers |

## Icons
- Use Phosphor Icons. Regular weight for tools that are not selected, Fill weight for the selected tool.
- Sizes: 16 px inline, 18 to 20 px in toolbars and navigation, 22 px in the mobile tab bar.
- Custom icons, drawn to match Phosphor (same stroke width, round caps and joins): keyframe (filled diamond), blank keyframe (outlined diamond), onion skin (three offset circles), motion tween, shape tween, symbol.
- The sparkle icon marks AI actions and is always `accent`.

## Radius, spacing, borders
- **Radius**: 8 px for small controls and timeline cells; 10 to 12 px for buttons, inputs and nav items; 14 px for prompt inputs; 20 to 24 px for cards; fully rounded for pills and landing page buttons.
- **Spacing**: 4 px base unit. Common values: 8, 12, 16, 20, 24, 28, 32, 40, 56, 64, 72.
- **Borders**: 1 px `border`. No drop shadows in the app UI. The stage has a 1 px `border` outline.
- **Touch targets**: at least 44 px on mobile and for toolbar buttons.

## Components
- **Primary button**: `accent` background, `text-on-accent` text, Onest 600, radius 10 to 14 px (fully rounded on the landing page).
- **Secondary button**: transparent background, 1 px `border-strong`, `text-primary` text.
- **Export button**: `text-primary` (#F6F1E9) background, `text-on-accent` text.
- **Chip**: transparent background, 1 px `border-strong`, `text-secondary` text, fully rounded.
- **Input**: `bg` or `surface` background, 1 px `border-strong`, radius 12 to 14 px, height 44 to 52 px. AI prompt inputs start with the sparkle icon.
- **Card**: `surface` background, 1 px `border`, radius 20 to 24 px.
- **AI assistant messages**: AI replies are `surface` cards with a summary and Keep (primary) and Undo (secondary) buttons. User messages are `surface-raised` bubbles aligned right.
- **Timeline**: layer name column 120 px wide; frame cells 15 × 26 px with a 1 px gap; every fifth cell is slightly lighter; keyframes are dots (`accent` on the selected layer, `keyframe-inactive` on other layers); the current frame has a 2 px `text-primary` inside outline; frame numbers every 5 frames in Martian Mono 11 px.

## Editor layout
Top bar (`panel`). Below it, from left to right: tool bar (60 px), stage area (`bg-stage-area` with a centered 16:9 stage), right panel (300 px, properties above the AI assistant). Timeline (`panel`) across the full width at the bottom.

## UI animation
- 150 to 200 ms ease-out for hover states and panels. No bouncing UI animations.
- Respect `prefers-reduced-motion`.

## Accessibility
- Use real `<button>`, `<a>`, `<input>` and `<label>` elements. Buttons with only an icon need `aria-label`.
- The timeline works with the keyboard: arrow keys step frames, F6 inserts a keyframe, F7 inserts a blank keyframe, Enter plays.
