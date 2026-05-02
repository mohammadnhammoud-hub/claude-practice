# Claude Code - Practice Keywords

## Commands

- **`npm run dev`** — starts the development server so the project runs live in the browser. "Turn on the engine" command.
- **`/init`** — Claude Code slash command that analyzes the project and creates/updates `CLAUDE.md`.
- **`/clear`** — clears the current conversation history and starts fresh, keeps Claude Code running.
- **`Esc Esc`** — keyboard shortcut to immediately cancel/interrupt Claude mid-task.
- **`/exit`** — closes/quits the Claude Code session completely.
- **`claude --continue`** — (terminal only) reopens your most recent conversation where you left off.
- **`claude --resume`** — (terminal only) lets you pick from a list of past conversations to resume.

## Concepts

- **git branch** — a separate copy of the project to experiment in safely. `main` = stable version, feature branches = sandbox. Changes on one branch don't affect the other.
- **`CLAUDE.md`** — file that tells Claude Code how the project works (build commands, architecture, etc.). Gets updated as the project grows.
- **Bash** — typing text commands to talk to your computer directly instead of clicking. Faster and more powerful than menus.
- **`/terminal-setup`** — Claude Code slash command that only works in the terminal version, not VSCode extension.

- **Hooks** — automated actions that trigger automatically when something happens in Claude Code (e.g. before/after a command runs). "If this happens, do that" — set once, runs every time.
- **Reusable hooks** — hooks defined globally so they apply across all projects, not just one. Set once, works everywhere.
- **Context** — Claude's short-term memory in a conversation. Includes all messages, replies, and files read so far.
- **Context window** — the size limit of Claude's memory. When it fills up, older content gets pushed out. Use `/compact` to free up space.
- **Local storage** — the browser's built-in way to save small pieces of data (like a theme preference) that persists even after closing the tab.
- **Theme toggle** — a button that switches between dark/light mode on a website.
- **Theme preference** — the user's saved choice of dark or light mode.
- **`#` (memory instruction)** — starting a message with `#` in Claude Code means you're giving Claude a rule to remember and follow going forward.
- **Project memory** — rules in `CLAUDE.md` committed to git. Shared with the whole team.
- **Project memory (local)** — rules in a `CLAUDE.md` NOT committed to git. Only on your machine, private.
- **User memory** — rules stored globally, apply across all your projects everywhere.
- **Page components** — individual pages or sections of a website.
- **Header** — the top navigation bar of a site.
- **Link** — a clickable element that navigates to another page.

## Skills

### Referencing files and folders with `@`
Point Claude to a specific file or folder so it knows exactly where to look or make changes.

| What you type | What it does |
|---|---|
| `@index.html fix the nav` | Claude reads index.html and fixes only the nav |
| `@about.html change h2 to Welcome` | Claude edits only about.html |
| `@src/components/ refactor all` | Claude looks at the whole folder |

**Why use it:** Without `@`, Claude guesses which file you mean. With `@`, you point directly — faster and more accurate.

---

### `Esc Esc` — Cancel a Running Task
Press **Escape twice** to immediately stop/interrupt whatever Claude is currently doing mid-task.

**When to use:** Claude is doing something wrong or you changed your mind mid-task.

---

### `/compact` — Compress Conversation History
Frees up context space when a conversation gets very long. Claude summarizes earlier parts of the chat to make room for more.

**When to use:** when your session is very long and Claude starts to slow down or lose track of earlier context.

---

### Sharing Images with Claude
Paste or drag and drop an image directly into the chat — Claude can read and analyze it.

**Examples:** screenshot a tutorial, share a UI design to build, show an error to debug.

---

### Understanding Components
A component is a reusable piece of a webpage — think of a website like LEGO bricks.

| Component | What it is |
|---|---|
| Header | Nav bar at the top |
| Footer | Bottom section |
| Card | A product or info block |
| About page | A full page as a component |

**Why:** Build it once, reuse it everywhere — no copy-pasting the same code on every page.

**In plain HTML:** each `.html` file is basically a page component (like `index.html`, `about.html`).

**In React:** components are `.jsx` files inside a `src/components/` folder.

---

- **Permission mode** — before Claude edits a file, it asks for your approval first. You can set it to always ask or auto-approve.

---

### Git Commit — Save a Snapshot of Your Project

| Command | What it does |
|---|---|
| `git add <files>` | Stages files — puts them in the "box" ready to save |
| `git commit -m "message"` | Seals the box and labels it — saves the snapshot |

**Think of it like:** `git add` = packing a box, `git commit` = sealing and labeling it.

---

## Notes

- Ask Claude to **summarize keywords** anytime by just asking "summarize my keywords".
