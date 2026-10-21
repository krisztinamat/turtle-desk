# Turtle Desk

A browser-based Python editor for beginners with turtle graphics, syntax highlighting,
smart indentation, and paste blocking with a typing record for teachers.

Features:
- Learn panel with six step-by-step lessons (printing, turtle movement, loops,
  color and pens, functions, if/else and random). Each step checks the student's
  code when they press Run.
- Searchable reference for turtle and Python basics, with examples.
- The lessons panel can be hidden with the arrow button next to the tabs, giving the
  editor and output more room. A slim "Lessons" strip brings it back. While the panel is
  hidden, runs are free coding: lesson and practice checks pause until it's shown again.
- In-editor tips that explain the function under the cursor, and
  "Did you mean …?" suggestions for misspelled names in error messages.
- Clear error messages: when a program fails, the Output panel shows one short,
  plain-language message pointing at the line that actually needs fixing (missing
  colons, indentation, misaligned else/elif, unclosed brackets and quotes), even
  when Python reports a different line. Common runtime errors (missing values in a
  command, mixing text and numbers, typos in names) get specific explanations; anything
  else shows Python's own message with a one-line explanation of the error type.
- Lesson checks focus on what each step teaches. For turtle lessons they also look at
  what the turtle actually drew (lines, turns, closed shapes, fills, jumps). Steps pass
  when the concept is right; if values differ from the example (for example a smaller
  loop), the student still passes and gets a short note about the difference.
- Downloadable typing report: students add their name in Typing record and click
  "Download report". They get a single .html file with their final code, a replay
  of the code being typed, a summary, completed lesson steps and a full event log.
  Students email it or upload it to the class page, and teachers open it in any browser.

## Practice problems
The Practice tab makes turtle drawing problems from 17 templates with random numbers.
Students see a goal picture and write code that draws it. The check compares the two
drawings, so any correct approach passes.

- Levels: Basic (single shapes), Intermediate (loops, pen jumps, spirals, stars) and
  Advanced (functions with parameters, nested loops, rotating patterns).
- Challenges that can be added to any level when they apply: Use a loop, Use a function,
  Short code (line limit), One forward() and Color fill.
- Every problem has a code such as `I4821-L` (level, number, challenges). The same code
  always gives the same problem, so a teacher can give a whole class one code. On GitHub
  Pages, a link ending in `#I4821-L` opens that problem directly.
- Hints are revealed one at a time, from general to specific. The last hint unlocks
  after 2 runs: an outline of a solution with every number blanked out.
- Solutions are never shown before a problem is solved. After solving, students can
  compare their code with one example solution.
- After 3 unsuccessful runs, students can switch to an easier version (challenges
  removed, or one level down).
- After each run, challenge buttons show a ✓ for every challenge the code already meets,
  even ones that weren't selected. Turning a challenge on re-checks the last run straight
  away, so there's no need to run again.
- Runs, hints used, solved problems and challenges met appear in the typing record and
  the report.

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
- Skulpt (MIT license) — https://skulpt.org
- Atkinson Hyperlegible fonts (SIL Open Font License) via Google Fonts

## Notes
- Turtle tracking works by adding a few hidden lines before the student's code when it
  uses turtle. Error line numbers are corrected automatically. To switch tracking off,
  set `const TRACK_TURTLE = false;` in index.html. Lessons then check the code text only.
- Each student's code and typing record are saved in their own browser (localStorage),
  separately for each site address.
- Checks run on the student's device, so they deter and record cheating
  rather than make it impossible.

## Privacy and security
- There is no server and no account. Code, names, lesson progress and the typing record
  stay in the browser's localStorage until a student downloads a report.
- The page loads Skulpt from cdn.jsdelivr.net and fonts from Google Fonts. Those services
  can see visitors' IP addresses. To avoid any third-party requests, host the two Skulpt
  files in a `vendor/` folder (see above) and remove the Google Fonts link (the page falls
  back to system fonts).
- localStorage is shared by every page on the same address. All of a user's GitHub Pages
  projects share `username.github.io`, so code from your other projects there can read
  Turtle Desk data. For full separation, use a separate GitHub account or a custom domain.
- On shared computers, the next student sees the previous student's work unless they click
  "Start a new session" in the Typing record.
- Student code runs inside Skulpt in the student's own browser tab, so it can't reach
  other students' computers or any server.
- Reports are HTML files made on the student's computer, so a student could edit one. Treat
  reports as evidence, not proof, and open them like any file from a student.
- The page source is public, so a determined student could read how the practice
  problems are built and work out solutions from it.

