# Turtle Desk

A browser-based Python editor for beginners with turtle graphics, syntax highlighting,
smart indentation, and paste blocking with a typing record for teachers.

Features:
- Learn panel with six step-by-step lessons (printing, turtle movement, loops,
  color and pens, functions, if/else and random). Each step checks the student's
  code when they press Run.
- Searchable reference for turtle and Python basics, with examples. Each entry links to
  the official Python documentation, and a collapsible "All turtle commands" list shows
  every turtle command on one line.
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
- There is no server, login or database. Code, names, lesson progress and the typing
  record stay in the browser's localStorage until a student downloads a report.
- Student code runs in Skulpt inside the student's own browser tab, so it can't reach
  other students' computers or any server. Skulpt modules that could change the page or
  use the network (`document`, `urllib`, `image`, `webgl`, `processing` and similar) are
  blocked, and the `jseval` built-in is removed. Students can import turtle, math, random
  and time.
- Everything the page displays from student code, saved data, error messages or links is
  escaped first, so text such as `<script>` shows as text and never runs. Problem codes
  from links are checked against a strict pattern, and malformed links are ignored.
- The only links are fixed python.org documentation links, opened in a new tab with
  `rel="noopener noreferrer"`.
- localStorage is shared by every page on the same address. All of a user's GitHub Pages
  projects share `username.github.io`. The app checks saved data before using it, but for
  full separation use a separate GitHub account or a custom domain for Turtle Desk.

### Recommended before using it with a class
1. **Host Skulpt yourself.** Download the two Skulpt files into a `vendor/` folder (see
   "Optional: host Skulpt yourself" above). This removes the dependency on jsDelivr, so a
   compromised or blocked CDN can't affect your students, and school web filters that block
   CDNs won't break the app. If you keep the CDN instead, add Subresource Integrity hashes:
   run `openssl dgst -sha384 -binary skulpt.min.js | openssl base64 -A` on each downloaded
   file, then add `integrity="sha384-<hash>" crossorigin="anonymous"` to its `<script>` tag.
2. **Optionally remove Google Fonts** (the `<link>` tags at the top of index.html). The
   page falls back to system fonts, and no third party sees students' IP addresses.
3. **Turn on "Enforce HTTPS"** in the repository's Settings → Pages.

### Chromebooks
- When students sign in with their own school accounts, each student's work is stored
  separately. In Guest mode, everything is erased when they sign out, so students should
  download their report first.
- On a shared sign-in, the next student sees the previous student's work unless they
  click "Start a new session" in the Typing record.
- Downloaded reports go to the Files app and can be uploaded to Google Classroom.

### Reports
- Reports are HTML files made on the student's computer, so a student could edit one. Treat
  reports as evidence, not proof. An edited report can't reach the teacher's other files,
  but it could show fake content. Open reports in the browser like any student file, and
  never type a password into one. "Copy as text" gives a plain-text version instead.
- The page source is public, so a determined student could read how the practice problems
  are built and work out solutions from it.
