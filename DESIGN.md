# Study Shelf design notes

The look is called **study violet**. It aims for modern and sleek without being bubbly: 8 to 16px corners, 1px borders, soft layered shadows, and a frosted top bar and sidebar over a faint aurora background. It comes in light and dark. Each class gets its own accent color, so the shelf reads as colorful while the interface itself stays calm.

## Where the look comes from

The palette, fonts and style come from the ui-ux-pro-max design data:

- **Palette.** This is the "Flashcard & Study Tool" profile. Study purple `#7C3AED` is the primary color. "Correct" green marks things that are ready or answered right.
- **Type.** This is the "Friendly SaaS" pairing: Plus Jakarta Sans for everything, in weights 400 to 800.
- **Style.** The top bar and sidebar use glassmorphism: 72% surface with an 18px blur. Behind the page is an aurora background made of three soft radial glows (violet, pink and teal).
  - The tool's first suggestion was claymorphism. It was left out because it is too bubbly for this app.
- **Gradients.** These appear only on the primary button, the logo, the class tiles and the class-card stripes. Everything else is flat.

## What changed in round two

| Ask | What changed |
|---|---|
| Key terms were highlighted in yellow and hard to read | Key terms are now cards. The term is bold violet on a tinted surface with a violet left edge, and the definition is regular text below it. No text sits on a highlighter color anywhere. The term text is 8.0:1 in light mode and 9.2:1 in dark. |
| The sidebar should be able to go away | The panel button at the top left hides and shows the sidebar, and the browser remembers the choice. Below 900px wide, the sidebar becomes a slide-in menu over a dimmed page. Escape, the close button or tapping outside closes it. |
| A tab to see the classes | An **All classes** tab in the top bar, and the same link at the top of the sidebar, opens a page of class cards. Each card shows the class color and code, the number of materials, when it was last updated, which study tools are ready, and a progress bar. A "New class" card sits at the end. The second tab is the class you have open. Arrow keys move between the tabs. |
| Light and dark mode, modern and not bland | There is a new palette with a light and a dark theme. The sun/moon button in the top bar switches between them. The app follows the device's setting until the student picks one, then remembers it. The phone's browser bar changes color to match. |
| (found while testing) | Adding a class now opens a small dialog instead of an inline form. The "Upload" and "Compare with model answer" buttons use a softer violet tint, so the main action in each view stands out. On wide screens, the Materials panel stays in view while you scroll through a summary or quiz. On phones, the big class tile is hidden to give the title room, and the four study tabs fit on one line. |

## Kept from the first redesign

- Every button, field, tab and checkbox has a touch target of at least 44px.
- Tabs follow the ARIA tabs pattern, with arrow, Home and End keys. Screen readers announce the "ready" dots.
- Focus stays inside open dialogs and the phone menu, and Escape closes them.
- **AI on the public site.** "AI off · Turn on" lets a student paste their own Anthropic API key, which is saved only in that browser. Inside Claude, AI runs on the viewer's Claude account.
- Course codes appear only for numbered classes, for example "BIOL 101" or "CALC I".
- Below 760px there is a sticky Materials / Study switch.
- Errors say what happened and what to do. Empty states say how many materials will be used.

## Tokens

Each token is defined once on `:root` in `index.html`. Dark mode redefines them, both for `prefers-color-scheme: dark` and for `data-theme="dark"`. A student's own choice, `data-theme="light"` or `"dark"`, always wins over the device setting.

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg` | `#f7f5fc` | `#0c0a1a` | Page |
| `--surface` | `#ffffff` | `#15122b` | Panels, cards |
| `--surface-2` | `#f4f1fb` | `#1c1838` | Term cards, tab tracks, inputs |
| `--surface-3` | `#ece7f8` | `#241f45` | Hover |
| `--raised` | `#ffffff` | `#2b2552` | Selected tab or segment |
| `--ink` | `#0f172a` | `#f1eefc` | Main text |
| `--muted` | `#475569` | `#b7b0d4` | Secondary text |
| `--faint` | `#5b6478` | `#9a93bd` | Hints, counts |
| `--line` / `--line-strong` | `#ebe5f7` / `#d9d0ee` | `#2a2550` / `#3a3468` | Borders |
| `--control` | `#8b84a3` | `#7a72a6` | Checkbox and field borders (3:1 or more) |
| `--primary` | `#7c3aed` | `#a78bfa` | Brand violet |
| `--primary-ink` | `#5b21b6` | `#c4b5fd` | Violet text (key terms, links, counts) |
| `--primary-soft` | `#f1eafe` | violet at 14% | Tinted backgrounds |
| `--good` / `--bad` / `--warn` | `#047857` / `#b91c1c` / `#b45309` | `#34d399` / `#f87171` / `#fbbf24` | Ready or correct / wrong / still learning |
| `--grad` | `#7c3aed` → `#6d28d9` → `#4f46e5` | same | Primary button, logo |

- **Type.** `--font` is Plus Jakarta Sans. `--mono` is the system monospace, used for codes and counts. Sizes run from `--t-xs` (12px) to `--t-lg` (18px). Titles use weight 800 with tight letter spacing.
- **Space.** A 4px grid, from `--s1` (4px) to `--s10` (40px).
- **Shape.** `--r-sm` 8px, `--r` 10px, `--r-md` 12px, `--r-lg` 16px, and `--r-pill` for small badges only.
- **Depth.** `--shadow-sm`, `--shadow`, `--shadow-lg`, plus `--glow` under the primary button.
- **Motion.** `--fast` is 0.15s and `--med` is 0.25s. Motion is removed under `prefers-reduced-motion`. The glass becomes solid under `prefers-reduced-transparency`.

## Class colors

| Key | Color | Example |
|---|---|---|
| `c1` | `#4f46e5` indigo | Calculus I |
| `c2` | `#0f766e` teal | Biology 101 |
| `c3` | `#be185d` raspberry | US History |
| `c4` | `#b45309` amber | Islamic Art |
| `c5` | `#7c3aed` violet | |
| `c6` | `#0369a1` blue | |

White initials on each color are 5.0:1 or better. The class color only decorates: the tile, the card stripe, the progress bar and the dot in the sidebar. It never colors text.

## Contrast checks (WCAG AA)

| Pair | Light | Dark |
|---|---|---|
| Key term name on its card | 8.0:1 | 9.2:1 |
| Main text on tinted surfaces | 16.0:1 | 14.9:1 |
| Definition text on a term card | 6.8:1 | 8.2:1 |
| Hint text, worst case | 5.3:1 | 4.9:1 |
| White on the primary button | 5.7:1 | 5.7:1 |
| Soft button text | 7.7:1 | 8.0:1 |
| Correct / wrong / still learning text | 5.5 / 6.0 / 5.0:1 | 9.5 / 6.6 / 10.9:1 |
| Field and checkbox borders | 3.5:1 | 4.2:1 |

## Buttons

| Variant | Use for |
|---|---|
| `.btn.primary` | The one main action in a view: Generate, Add class, Save, Got it. Gradient with a soft glow. |
| `.btn.soft` | A strong but secondary action: Upload, Compare with model answer. Violet tint. |
| `.btn` | Other actions: Photo, Notes, Still learning. Outlined. |
| `.btn.quiet` | Low-emphasis actions: Cancel, Rename, icon buttons. |
| `.btn.danger` | Destructive confirmation only: Delete class. |
| `.btn.sm` / `.icon-btn` | A smaller size, and a square 44px icon button. |

## Layout

- **Desktop.** A 272px frosted sidebar, then the main column. The top bar holds the sidebar toggle, the page tabs and the theme button. It stays at the top while scrolling.
- **Above 1120px.** Materials and Study sit side by side. The Materials panel stays in view while the study column scrolls, and a long list scrolls inside the panel.
- **Below 1120px.** Materials and Study stack into one column.
- **Below 900px.** The sidebar becomes a slide-in menu, and the logo moves into the top bar.
- **Below 760px.** The top bar wraps into two rows (logo, then tabs), and the sticky Materials / Study switch appears.
- **Below 380px.** Tab labels get slightly smaller, and the BETA badge hides.
