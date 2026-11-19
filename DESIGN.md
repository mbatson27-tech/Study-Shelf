# Study Shelf design notes

The look is called **deep teal**. It aims for modern and sleek without being bubbly. Corners are 8 to 16px, borders are 1px, and shadows are soft and layered. The top bar and sidebar are frosted over a faint aurora background. It comes in light and dark, and there is no purple anywhere. Each class gets its own accent color, so the shelf reads as colorful while the interface itself stays calm.

## Where the look comes from

The palette, fonts and style come from the ui-ux-pro-max design data.

- **Palette.** The colors come from the "Online Course / E-learning" profile, built on progress teal `#0D9488`.
  - To pass WCAG AA, buttons use a teal-700 to cyan-700 gradient with white text.
  - Teal text uses a deeper `#0e6f68` in light mode.
  - Green still marks things that are ready or correct. It is a yellower green, so it doesn't blend into the teal.
- **Type.** The fonts follow the "Friendly SaaS" pairing: Plus Jakarta Sans for everything, in weights 400 to 800.
- **Style.** The top bar and sidebar use glassmorphism: a 74% surface with an 18px blur.
  - Behind the page is an aurora background made of three soft radial glows: teal, sky and a hint of amber.
  - The tool's first suggestion was claymorphism. It was left out because it is too bubbly for this app.
- **Gradients.** Gradients appear only on the primary button, the logo, the class tiles and the class-card stripes. Everything else is flat.

## History

| Round | What was asked | What changed |
|---|---|---|
| 1 | Publish the app and rework the design | The notebook look was refined (contrast, touch targets, phone layout, accessibility), and AI was made to work on the public site. |
| 2 | Key terms were yellow and hard to read. The sidebar should be able to go away. Add a tab to see the classes. Make it modern and sleek, with light and dark mode, and not bland. | Key terms became cards. The sidebar can be hidden. There is an **All classes** tab and page. A new palette came in with light and dark modes. |
| 3 | "I don't like the purple" | The violet palette was replaced by deep teal everywhere: tokens, logo, favicon, class colors and the browser bar. |

### Key terms
Each term is a card. The term is bold teal on a tinted surface with a teal left edge, and the definition is regular text below it. No text sits on a highlighter color anywhere. The term text is 5.5:1 in light mode and 11.0:1 in dark mode.

### Sidebar
The panel button at the top left hides and shows the sidebar, and the browser remembers the choice. Below 900px wide, the sidebar becomes a slide-in menu over a dimmed page. Escape, the close button, or tapping outside closes it.

### All classes
An **All classes** tab in the top bar, and the same link at the top of the sidebar, opens a page of class cards. A "New class" card sits at the end. Each card shows:
- The class color and code.
- The number of materials and when the class was last updated.
- Which study tools are ready, with a progress bar.

The second tab is the class you have open. Arrow keys move between the tabs.

### Light and dark
The sun/moon button in the top bar switches modes. The app follows the device until the student picks a mode, then remembers it. The phone's browser bar changes color to match.

### Smaller changes
- Adding a class opens a small dialog.
- "Upload" and "Compare with model answer" use a softer tint, so the main action in each view stands out.
- On wide screens, the Materials panel stays in view while you scroll.
- On phones, the big class tile is hidden to give the title room, and the four study tabs fit on one line.

### Kept from round 1
- Every button, field, tab and checkbox has a touch target of at least 44px.
- Tabs follow the ARIA tabs pattern, with arrow, Home and End keys. Screen readers announce the "ready" dots.
- Focus stays inside open dialogs and the phone menu, and Escape closes them.
- **AI on the public site.** "AI off · Turn on" lets a student paste their own Anthropic API key, saved only in that browser. Inside Claude, AI runs on the viewer's Claude account.
- Course codes appear only for numbered classes ("BIOL 101", "CALC I").
- Below 760px there is a sticky Materials / Study switch.
- Errors say what happened and what to do. Empty states say how many materials will be used.

## Tokens

Each token is defined once on `:root` in `index.html`. Dark mode redefines them, both for `prefers-color-scheme: dark` and for `data-theme="dark"`. A student's own choice (`data-theme="light"` or `"dark"`) always wins over the device setting.

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg` | `#f5f8f8` | `#0a1114` | Page |
| `--surface` | `#ffffff` | `#10191d` | Panels, cards |
| `--surface-2` | `#f0f5f5` | `#152227` | Term cards, tab tracks, inputs |
| `--surface-3` | `#e5eeee` | `#1b2c32` | Hover |
| `--raised` | `#ffffff` | `#22363d` | Selected tab or segment |
| `--ink` | `#0f172a` | `#e9f2f2` | Main text |
| `--muted` | `#475569` | `#a8bcbf` | Secondary text |
| `--faint` | `#5b6478` | `#8ba1a5` | Hints, counts |
| `--line` / `--line-strong` | `#e2eaea` / `#cddada` | `#1f3036` / `#2b4148` | Borders |
| `--control` | `#7d8f92` | `#5d777d` | Checkbox and field borders (3:1 or better) |
| `--primary` | `#0d9488` | `#2dd4bf` | Icons, focus rings, dots (3:1 or better) |
| `--primary-ink` | `#0e6f68` | `#5eead4` | Teal text (key terms, counts, soft buttons) |
| `--primary-soft` | `#e2f4f1` | teal at 12% | Tinted backgrounds |
| `--good` / `--bad` / `--warn` | `#157a3a` / `#b91c1c` / `#b45309` | `#4ade80` / `#f87171` / `#fbbf24` | Ready or correct / wrong / still learning |
| `--grad` | `#0f766e` → `#0e7490` | same | Primary button, logo |

- **Type.** `--font` is Plus Jakarta Sans. `--mono` is the system monospace, used for codes and counts. Sizes run from `--t-xs` (12px) to `--t-lg` (18px). Titles use weight 800 with tight letter spacing.
- **Space.** A 4px grid, from `--s1` (4px) to `--s10` (40px).
- **Shape.** `--r-sm` is 8px, `--r` is 10px, `--r-md` is 12px and `--r-lg` is 16px. `--r-pill` is for small badges only.
- **Depth.** `--shadow-sm`, `--shadow` and `--shadow-lg` use neutral slate shadows. `--glow` sits under the primary button.
- **Motion.** `--fast` is 0.15s and `--med` is 0.25s. Motion is removed under `prefers-reduced-motion`. The glass becomes solid under `prefers-reduced-transparency`.

## Class colors

| Key | Color | Example |
|---|---|---|
| `c1` | `#2563eb` blue | Calculus I |
| `c2` | `#15803d` green | Biology 101 |
| `c3` | `#be185d` raspberry | US History |
| `c4` | `#b45309` amber | Islamic Art |
| `c5` | `#0e7490` cyan | |
| `c6` | `#475569` slate | |

White initials on each color are 5.0:1 or better. The class color only decorates the tile, the card stripe, the progress bar and the dot in the sidebar. It never colors text.

## Contrast checks (WCAG AA)

| Pair | Light | Dark |
|---|---|---|
| Key term name on its card | 5.5:1 | 11.0:1 |
| Main text on tinted surfaces | 16.2:1 | 14.3:1 |
| Definition text on a term card | 6.9:1 | 8.2:1 |
| Hint text, worst case | 5.0:1 | 4.7:1 |
| White on the primary button | 5.4:1 | 5.4:1 |
| Soft button text (and on hover) | 5.3:1 (5.1:1) | 9.6:1 |
| Correct / wrong / still learning text | 5.4 / 6.5 / 5.0:1 | 10.2 / 6.4 / 10.7:1 |
| Field and checkbox borders | 3.4:1 | 3.7:1 |
| Teal icons and focus rings | 3.7:1 | 9.6:1 |

## Buttons

| Variant | Use for |
|---|---|
| `.btn.primary` | The one main action in a view: Generate, Add class, Save, Got it. Gradient with a soft glow. |
| `.btn.soft` | A strong but secondary action: Upload, Compare with model answer. Teal tint. |
| `.btn` | Other actions: Photo, Notes, Still learning. Outlined. |
| `.btn.quiet` | Low-emphasis actions: Cancel, Rename, icon buttons. |
| `.btn.danger` | Destructive confirmation only: Delete class. |
| `.btn.sm` / `.icon-btn` | Smaller size, and a square 44px icon button. |

## Layout

- **Desktop.** A 272px frosted sidebar, then the main column. The top bar holds the sidebar toggle, the page tabs and the theme button. It stays at the top while scrolling.
- **Above 1120px.** Materials and Study sit side by side. The Materials panel stays in view while the study column scrolls, and a long list scrolls inside the panel.
- **Below 1120px.** Materials and Study stack into one column.
- **Below 900px.** The sidebar becomes a slide-in menu, and the logo moves into the top bar.
- **Below 760px.** The top bar wraps into two rows (the logo, then the tabs), and the sticky Materials / Study switch appears.
- **Below 380px.** Tab labels get slightly smaller, and the BETA badge hides.
