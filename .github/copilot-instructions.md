## Repository overview

This is a small frontend workshop repository for practicing JavaScript array methods.
Files of interest:

- `lab3.html` — single-page UI that loads `lab3.js` and exposes buttons to run the exercises.
- `lab3.js` — contains the dataset (`analyticsData`) and five TODO functions students must implement: `getEngagementLevel`, `findLongestSessionUser`, `formatSessions`, `getActiveUsers`, `getTotalSessions`.
- `lab3.css` — styles following a simple BEM-like naming convention (e.g. `analytics`, `analytics__header`, `analytics__button`).
- `README.md` — classroom integration badge, no build steps.

Keep guidance focused and actionable for code-completion agents working on student-facing exercises.

## Big picture / intent

- Single-page static site. No build tools, server, or package manager required. Editing `lab3.js` and opening `lab3.html` in the browser is the main developer workflow.
- The goal is educational: implement the TODO functions using specific JS language features (conditionals, loops, map/filter/reduce). Avoid over-engineering — prefer plain, readable JavaScript that demonstrates the intended method.

## Project-specific conventions

- Minimal, vanilla JS. Prefer ES6 syntax already used in the file (const, arrow functions, template literals).
- Keep function signatures and names unchanged. Buttons in `lab3.html` call global functions like `runEngagementLevel()` and expect the TODO functions to be present in the global scope.
- UI responsibilities are handled in `lab3.js` (output via `output.textContent`); agents should not change the DOM API surface or remove existing IDs/classes.
- Follow the existing BEM-like CSS naming when adding classes: block `analytics`, element `analytics__button`, modifier `analytics__button--danger`.

## Files and patterns to reference

- `lab3.js` — locate the dataset at the top and the TODO functions in the middle. Each TODO includes a short inline hint; use those to craft implementations.
- `lab3.html` — shows how UI wires to functions by name (e.g., `onclick="runTotalSessions()"`). Avoid renaming these handlers unless updating both HTML and JS.
- `lab3.css` — provides layout and visual conventions; small, self-contained stylesheet with a responsive media query.

## Typical edits an agent should make

- Implement the five TODO functions in `lab3.js`. Keep implementations minimal, idiomatic, and limited to the requested language feature:

  - `getEngagementLevel(user)` — return "Good" for avgSessionDuration >= 200, else "Low".
  - `findLongestSessionUser(data)` — use a for-loop to return the user name with the highest avgSessionDuration.
  - `formatSessions(data)` — return an array of strings using `map` and template literals: "Name: X sessions".
  - `getActiveUsers(data)` — use `filter` then `map` to return names with totalSessions >= 5.
  - `getTotalSessions(data)` — use `reduce` to sum `totalSessions`.

- Avoid modifying the UI wiring (handlers in `lab3.html`) unless coordinating changes across files.
- When editing CSS, prefer adding modifier classes instead of changing existing class names referenced from HTML or JS.

## Example snippets (for guidance only)

Use these styles when implementing functions (do not add extra libraries):

getTotalSessions example approach:

const getTotalSessions = (data) => data.reduce((sum, u) => sum + u.totalSessions, 0);

formatSessions example approach:

const formatSessions = (data) => data.map(u => `${u.name}: ${u.totalSessions} sessions`);

findLongestSessionUser approach (for-loop required by exercise intent):

let max = -Infinity; let name = '';
for (let i = 0; i < data.length; i++) {
if (data[i].avgSessionDuration > max) { max = data[i].avgSessionDuration; name = data[i].name; }
}
return name;

## Developer workflow / quick checks

- No build step: open `lab3.html` in a browser to run interactively.
- Quick smoke test: edit `lab3.js` to implement a function, save, then reload `lab3.html`. The output section shows results when clicking the buttons.
- Keep changes small and isolated to the TODO functions for student code submissions.

## Edge cases and grading expectations

- Implementations should handle the provided dataset shape (objects with `name`, `totalSessions`, `avgSessionDuration`). It's acceptable to assume these fields exist for this exercise.
- For ties in `findLongestSessionUser`, returning the first encountered highest value is fine.

## What not to do

- Do not introduce bundlers, transpilers, or npm dependencies.
- Avoid changing global names that `lab3.html` depends on unless updating both files and verifying behavior.

## Where to ask for clarification

- If unsure about altering HTML handlers or changing the dataset shape, ask the repository owner before large refactors.

---

If you want I can refine this further (shorten, add precise examples inline, or merge with an existing instructions file). What would you like changed?
