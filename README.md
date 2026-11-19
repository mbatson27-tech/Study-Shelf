# Study Shelf

A study organizer for students. Make a shelf for each class, add anything (PDFs, Word docs, slides, spreadsheets, photos of notes, pasted notes), and turn it into summaries, flashcards, quizzes and practice questions.

**Live site:** https://mbatson27-tech.github.io/Study-Shelf/ (once GitHub Pages is turned on, see below)

## How it works

- The whole app is one file, `index.html`. No build step.
- Everything a student adds is saved in their own browser (IndexedDB). Nothing is uploaded to a server, and nothing syncs between devices.
- Comes with example classes and a ready-made Islamic Art (AP Art History, Ch. 9) set: summary, 46 flashcards, a 20-question quiz and practice questions.
- **All classes** shows every class as a card with its progress. The sidebar can be hidden (it becomes a slide-in menu on phones), and there is a light and a dark mode.

## AI

- Opened inside Claude (claude.ai or the Claude app), AI runs on the viewer's own Claude account.
- On the public website, each student turns AI on by pasting their own Anthropic API key (from console.anthropic.com). The key is stored only in that browser and sent only to `api.anthropic.com`. Without a key, everything else works and the example sets still show.

## Publishing with GitHub Pages

Settings → Pages → Build and deployment → Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)** → Save. The site appears at the address above within a few minutes.

Design notes: see [DESIGN.md](DESIGN.md).
