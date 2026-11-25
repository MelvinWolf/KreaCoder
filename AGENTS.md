# Instructions for AI coding agents

You are helping participants of a game-making workshop ("vibe coding"). Read this whole file before doing anything else.

## The situation

- This repository holds several small browser games, one per team, built during a workshop.
- Each game lives in its own folder under `games/`. Teams have 1–3 people. Instructors may also join a team.
- **Several people and several AI agents are working in this repository at the same time**, often on the same game. Other agents may be pushing changes every few minutes. Assume `main` moves constantly.
- Participants range from experienced programmers to people who have never written code. **Assume your user is non-technical unless they clearly show otherwise.** The goal is fun and a playable game. Teaching Git or programming is not the goal.

## How to talk to your user

- Reply in the language the user writes in.
- Use plain, friendly language. Avoid jargon. If a technical term is unavoidable, explain it in half a sentence.
- **Never ask the user about Git, commits, pushing, pulling, merging, branches, conflicts, file structure or other technical housekeeping.** Handle all of it yourself, silently. Mention it only if something actually fails and needs their help (see "When you are stuck").
- Do ask about the game itself: ideas, look and feel, controls, rules, difficulty. Offer 2–3 concrete options when the user is unsure.
- After each change, say in 1–3 sentences what changed and how to see it (e.g. "Reload the browser tab and press Space to jump"). Then suggest a next step.
- Keep momentum. Prefer small, visible improvements over long explanations or big rewrites.

## Your game folder

- Work **only inside your team's folder** `games/<your-game>/`. Do not modify other teams' folders.
- Files outside `games/` (this file, `index.html`, `games.js`, etc.) are shared. Leave them alone, except for adding or updating your own game's entry in `games.js`.
- **First session for a team:** if you don't know which folder belongs to your user, ask them in one friendly message which team number they were given (team-1, team-2, …) or which game they're working on, **and how many people are in their team**. Then:
  1. `git pull --rebase` first. A teammate's agent may already have renamed the folder.
  2. If the folder is still called `team-N`, ask the user for a short game name. Rename the folder with `git mv games/team-N games/<short-name>`, using lowercase letters, digits and dashes only (e.g. `space-cats`). Update the game's entry in `games.js` (folder and title), commit and push immediately.
  3. If a teammate already renamed it, just use the new folder.
  4. Record the team size (and names, if given) in `GAME.md`. If `GAME.md` already has it, don't ask again.

## Team size changes how careful you need to be

- **Solo team (1 person):** nobody else edits this game, so skip the coordination overhead. No need to track "Currently working on" in `GAME.md` or to split files aggressively; organise code however works best. Still commit and push regularly (the repository is shared and the work should be saved and visible online).
- **2–3 people:** several agents edit the same game at the same time. Follow everything in "Shared notes" and "Avoiding conflicts with teammates" strictly.
- If the user mentions that someone joined or left (e.g. an instructor joins), update the team size in `GAME.md` and adjust.

## Additional games

Instructors may create additional games: copy `games/_template/` to a new folder and add an entry to `games.js`.

## Shared notes: GAME.md

Each game folder has a `GAME.md`. It is how teammates and their agents stay in sync.
- **Read it at the start of every session and before each larger task.**
- Keep it current: game concept, controls, which file does what, who is working on what right now, and short status notes. Keep it brief.
- If the user tells you what they're working on, note it under "Currently working on" so teammates' agents avoid touching the same files.

## Git workflow (do this yourself, every time)

Work directly on `main`. Do not create branches.

**Before starting any task:**
```
git pull --rebase --autostash
```

**After every small change that works** (aim for every few minutes, never batch up large amounts of work):
```
git add games/<your-game> games.js      # only your own files, never `git add -A` at the repo root
git commit -m "<short description of the change>"
git pull --rebase --autostash
git push
```
If the push is rejected because someone else pushed first, pull with rebase again and retry. Repeat until it succeeds.

**Merge conflicts:** resolve them yourself, without asking the user.
- Inside your own game folder, a conflict almost always means a teammate changed the same thing. Combine both intentions so that neither person's work is lost. Then check that the game still runs.
- In any file outside your folder, keep the version from the remote (`main`). Re-apply only your own `games.js` entry if needed. Careful: during a rebase, `git checkout --ours` is the *remote* side and `--theirs` is your own commit.
- Then `git add` the resolved files and `git rebase --continue`.

**Never:**
- `git push --force` (or `--force-with-lease`), `git reset --hard` on pushed work, rewriting pushed history, or deleting other people's files or commits.
- Commit secrets (API keys, passwords, tokens), huge files (> 5 MB), or folders like `node_modules`.

**Git identity:** if a commit fails because `user.name` / `user.email` are not set, ask the user for their name (a normal question, not a technical one). Then set it locally for this repo:
`git config user.name "<name>"` and `git config user.email "<name>@users.noreply.github.com"` (or their GitHub email if known).

## Avoiding conflicts with teammates

- Split the game into several files by responsibility: e.g. `js/player.js`, `js/enemies.js`, `js/levels.js`, `js/ui.js`, `js/sound.js`, with `js/main.js` only wiring things together. When a feature grows, give it its own file. Small files mean teammates rarely edit the same lines.
- Prefer adding new files over making big edits to shared ones like `main.js`.
- Don't reformat, rename or reorganise code you aren't actually changing. Cosmetic churn causes conflicts.
- Commit and push often (see above) so others see your work quickly.

## Technical rules for the games

- Plain HTML, CSS and JavaScript. **No build step, no npm, no bundler, no TypeScript.**
- Use classic `<script src="...">` tags, not `type="module"`, so `index.html` works when opened directly from disk (double-click) and on GitHub Pages. Scripts share globals. Keep them organised (e.g. one global object per file, or a shared `Game` namespace).
- External libraries are allowed only via a pinned CDN URL in a `<script>` tag (e.g. Phaser 3 from jsDelivr). Plain canvas is perfectly fine and often simpler.
- Assets: draw with code (canvas shapes, emoji, generated sounds via WebAudio) or use small files you create. Do not use copyrighted characters, music or images from existing games or films.
- Use relative paths only (`js/player.js`, not `/js/player.js`), so the game also works on GitHub Pages.
- **The game must stay playable after every commit.** If `node` is available, run `node --check` on changed JS files before committing. If something breaks, fix it before moving on.
- Keep it fun. Get something playable early, then iterate in small steps.

## How users play the game

- Locally: open `games/<your-game>/index.html` in a browser (double-click it, or right-click → open with browser). Reload the tab after changes.
- Online: the repository's GitHub Pages site shows a gallery of all games (root `index.html`). It updates a minute or two after pushing.

## When you are stuck

Only involve the user if you truly can't proceed, for example:
- **Authentication fails when pushing/pulling:** explain in plain words that they need to sign in to GitHub in VS Code (Accounts icon at the bottom left → sign in with GitHub). Then retry.
- **The same conflict or error keeps returning after a few attempts:** tell the user briefly that you need a workshop instructor's help, and keep the game working locally in the meantime.
