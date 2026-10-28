# OER App Planner

A single-page tool that helps instructors plan a small interactive learning app, generate a ready-to-paste prompt for any AI assistant, and check the result before students see it.

No accounts, no API keys, no build step, no network requests. One HTML file.

## What it does

1. **Plan your app** — twelve questions about the learning problem, the students, and the activity. Each one has an expandable panel with coaching questions and example answers.
2. **Check your plan** — plain in-browser checks for common snags: unobservable learning goals, scope that is too broad, thin wrong-answer feedback, content sources that cannot be openly licensed. Plus expandable guidance on what makes a first app succeed.
3. **Get your prompt** — the plan becomes a complete build prompt with privacy, accessibility, and LMS requirements built in. Copy it into Claude, ChatGPT, Gemini, Copilot, or anything else that writes code. Includes follow-up prompts for improving the teaching, fixing what broke, and checking accessibility.
4. **Check the result** — paste back the HTML the AI produced. An in-browser scan looks for network requests, outside files, embedded keys, missing alt text, and LMS compatibility problems. Finishes with a human checklist and a downloadable summary.

## Use it

Open `index.html` in a browser. That is the whole installation.

To host it with GitHub Pages: push this repository, then under **Settings → Pages**, set the source to your default branch and the root folder. The tool will be live at `https://<your-username>.github.io/<repository-name>/`.

## Privacy

Everything runs in the browser. Work in progress is saved to `localStorage` on the user's own device and is never transmitted. There are no analytics, no external scripts, no fonts loaded from a CDN, and no network calls of any kind.

The **Preview the app** button opens pasted code in a new tab so the author can try it. That code runs with the same permissions as any page the user opens themselves, so only preview code you generated or trust.

## Browser support

Written in ES5 JavaScript with no dependencies. Works in any current browser, and in the older browsers some campuses still run.

## Customizing it for your campus

Everything configurable sits at the top of the `<script>` block:

- `FIELDS` — the planning questions, their hints, and the contents of each help panel.
- `CHECKS` — the final human checklist, grouped by heading.
- `RULES` — the code-scan patterns, each with a severity (`flag` or `check`) and the plain-language explanation shown to the user.
- `buildPrompt()` — the generated prompt. Edit this to match your institution's requirements.

Colors are CSS custom properties on `:root`, with a dark-mode block below. The defaults use SUNY Cortland red (`#d71e25`) and maroon (`#85181c`).

If your LMS has different constraints, the two places to change are the LMS lines inside `buildPrompt()` and the rules named `LMS: modern JavaScript` and `LMS: timer chains` in `RULES`.

## Accessibility

Built to WCAG 2.1 AA: keyboard operable throughout with visible focus, semantic headings and labels, live regions on results, no color-only signaling, and support for reduced-motion and dark-mode preferences. A print stylesheet is included so faculty can print their plan. If you find a barrier, please open an issue.

## License

CC BY 4.0 — reuse and adapt with attribution.
