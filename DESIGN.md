# Study Shelf design notes

The redesign keeps the "working notebook" direction (square corners, hairlines, black ink, one highlighter yellow) and fixes what a design critique, an accessibility audit and a design-system audit found in the first prototype.

## What changed and why

| Area | Before | After |
|---|---|---|
| Contrast | Small grey labels were 3.0:1 on the page background (fails WCAG AA). Checkbox and input borders were 1.7:1. | Every text color is at least 4.5:1 on its background in light and dark mode. Controls use a `--control` border at 3.5:1. |
| Touch targets | Buttons and fields were 40px tall. | 44px minimum everywhere (buttons, fields, tabs, checkboxes, quiz review). |
| Phone layout | Study tools sat below the whole materials list, a long scroll away. Tab labels were hidden except the selected one. | A sticky Materials / Study switch. All four study tabs show their names. |
| Tabs | Tabs looked like tabs but arrow keys did nothing; "ready" dots weren't announced. | ARIA tabs pattern with arrow, Home and End keys; "ready" is read out by screen readers. |
| Dialogs | Tab could leave an open dialog. | Focus stays inside open dialogs; Escape closes them. |
| AI on the web | Outside Claude, AI only showed example output and said "Preview mode". | "AI off · Turn on" opens a sheet to add an Anthropic API key (saved only in that browser). Inside Claude it still uses Claude directly. |
| Course codes | Every class got a code, e.g. "ISLA ART". | Codes only for numbered classes ("BIOL 101", "CALC I"); others just show their name. |
| Identity | Text-only wordmark. | Small bookshelf mark (also the favicon), yellow active-class marker, red margin rule down the study page, colored edge on file icons by type. |
| Dark mode | Followed the system only. | Also a Dark mode / Light mode switch in the sidebar, remembered per browser. |
| Copy | "Preview mode", generic empty states. | Errors say what happened and what to do; empty states say how many materials will be used. |

## Tokens

Defined once on `:root` in `index.html` and redefined for dark mode:

- Color: `--bg`, `--surface`, `--surface-2`, `--ink`, `--muted`, `--faint`, `--line`, `--line-strong`, `--control`, `--hl` (highlighter), `--hl-soft`, `--rule` (margin red), `--good`, `--bad` and their `-soft` tints.
- Type: `--serif` (Newsreader) for content a student reads, `--font` (IBM Plex Sans) for UI, `--mono` (IBM Plex Mono) for codes and counts. Sizes `--t-xs` to `--t-lg`.
- Space: 4px grid, `--s1` (4px) to `--s10` (40px).
- Shape and motion: `--r`, `--r-lg`, `--tap` (44px), `--ease`, `--fast`, `--med`. Motion is removed under `prefers-reduced-motion`.

## Button variants

| Variant | Use for |
|---|---|
| `.btn.primary` | The one main action in a view (Generate, Save, Got it). |
| `.btn` | Secondary actions (Photo, Notes, Still learning). |
| `.btn.quiet` | Low-emphasis actions (Cancel, Rename, sidebar links). |
| `.btn.danger` | Destructive confirmation only (Delete class). |
