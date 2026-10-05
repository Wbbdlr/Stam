# Stam — instructions for Claude

Free app (iOS/Android, later web) that checks STaM from phone photos. Owner: Computer Rabbis LLC (ComputerRabbis.com). Private and proprietary.

## Read first — only what the task needs
- `docs/PLAN.md` — scope, result format, architecture, phases.
- `docs/DECISIONS.md` — settled decisions. Don't reopen them; append new ones with the date.
- `docs/RESEARCH.md`, `docs/halacha/RULES.md` — only when the task touches them.

## Token efficiency (always)
- Be brief. No preamble, no recap of what you did, no restating the task.
- Read narrowly: Grep/Glob first, then read only the lines you need. Don't re-read a file you already have unless it changed.
- Never dump large output: pipe through `head`/`tail`/`grep`. Run the one relevant test while iterating; the full suite once at the end.
- Edit, don't rewrite. Rewrite a file only when most of it changes.
- Batch independent tool calls in a single turn.
- No unrequested refactors, features, comments or docs.
- Don't re-research anything in `docs/RESEARCH.md`. Add new findings there (one or two lines + source link) so nothing is paid for twice.
- Ask only when blocked on a decision that is Sven's to make. Ask everything at once, with lettered options.
- No subagents unless Sven asks.
- Images, datasets and model weights never go in git (see `.gitignore`).

## Project rules
- **Halacha:** never call an item "kosher" or imply a hechsher. Results are: pasul / shailah / no visible problems found, plus a hiddur score. Every check's classification comes from `docs/halacha/RULES.md`, which cites published sources. Never invent a halachic rule.
- **Ksav:** support Beis Yosef, Arizal, Chabad (Alter Rebbe) and Sephardi (Vellish); detect the style from the image.
- **Languages:** English, Hebrew and Yiddish from day one. No hardcoded UI strings; every screen must work right-to-left.
- **Privacy:** analysis runs on the device. Images never leave it unless the user explicitly shares them.
- **Licenses:** MIT, Apache-2.0 or BSD only. Flag any GPL/AGPL dependency before adding it (e.g. Ultralytics YOLO is AGPL).
- **Commits:** small, imperative subject line, mention the phase (e.g. `P1: add line segmentation`).
