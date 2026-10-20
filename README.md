# Turtle Desk

A browser-based Python editor for beginners with turtle graphics, syntax highlighting,
smart indentation, and paste blocking with a typing record for teachers.

Features:
- Learn panel with six step-by-step lessons (printing, turtle movement, loops,
  colour and pens, functions, if/else and random). Each step checks the student's
  code when they press Run.
- Searchable reference for turtle and Python basics, with examples.
- In-editor tips that explain the function under the cursor, and
  "Did you mean …?" suggestions for misspelled names in error messages.
- Clear error messages: when a program fails, the Output panel shows one short,
  plain-language message pointing at the line that actually needs fixing (missing
  colons, indentation, misaligned else/elif, unclosed brackets and quotes), even
  when Python reports a different line. Python's original message is one click away.
- Lesson checks focus on what each step teaches. For turtle lessons they also look at
  what the turtle actually drew (lines, turns, closed shapes, fills, jumps). Steps pass
  when the concept is right; if values differ from the example (for example a smaller
  loop), the student still passes and gets a short note about the difference.
- Downloadable typing report: students add their name in Typing record and click
  "Download report". They get a single .html file with their final code, a replay
  of the code being typed, a summary, completed lesson steps and a full event log.
  Students email it or upload it to the class page, and teachers open it in any browser.

## Run locally
Open `index.html` in a browser. An internet connection is needed to load Skulpt
(the in-browser Python) and the fonts from their CDNs.

## Deploy on GitHub Pages
1. Create a public repository, e.g. `turtle-desk`.
2. Upload `index.html` (and this README) to the root of the `main` branch.
3. Go to Settings → Pages → Build and deployment → Source: "Deploy from a branch",
   Branch: `main`, folder: `/ (root)` → Save.
4. After a minute, the site is live at `https://<your-username>.github.io/turtle-desk/`.

## Optional: host Skulpt yourself
To avoid depending on the jsDelivr CDN, download these two files into a `vendor/` folder:
- https://cdn.jsdelivr.net/npm/skulpt@1.2.0/dist/skulpt.min.js
- https://cdn.jsdelivr.net/npm/skulpt@1.2.0/dist/skulpt-stdlib.js

Then change the two `<script src="...">` tags in `index.html` to
`vendor/skulpt.min.js` and `vendor/skulpt-stdlib.js`.

## Credits
- Skulpt (MIT licence) — https://skulpt.org
- Atkinson Hyperlegible fonts (SIL Open Font License) via Google Fonts

## Notes
- Turtle tracking works by adding a few hidden lines before the student's code when it
  uses turtle. Error line numbers are corrected automatically. To switch tracking off,
  set `const TRACK_TURTLE = false;` in index.html. Lessons then check the code text only.
- Each student's code and typing record are saved in their own browser (localStorage),
  separately for each site address.
- Checks run on the student's device, so they deter and record cheating
  rather than make it impossible.
