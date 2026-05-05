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

---

### Plan Mode — Review Before Claude Acts
Activate with **`Shift + Tab`** — cycles through Claude Code permission modes.

| Mode | What it does |
|---|---|
| `default` | Asks permission before making changes |
| `acceptEdits` | Auto-accepts file edits without asking |
| `plan` | Shows proposed changes only — nothing runs until you approve |

**When to use:** when you want to see Claude's full plan before it touches any files.

---

## Slash Command Skills

| Skill | What it does |
|---|---|
| `/keybindings-help` | Customize keyboard shortcuts in Claude Code |
| `/init` | Analyze project and create/update `CLAUDE.md` |
| `/clear` | Clear conversation history, keep Claude running |
| `/exit` | Quit Claude Code session |
| `/compact` | Compress conversation to free up context space |
| `/update-config` | Configure settings (hooks, permissions, env vars) |
| `/review` | Review a pull request |
| `/security-review` | Security review of pending branch changes |
| `/loop` | Run a prompt on a recurring interval |
| `/schedule` | Schedule recurring or one-time remote agents |

---

---

### "Think" / "Think Hard" — Extended Reasoning Mode
Telling Claude to **"think"** or **"think hard"** before answering activates deeper reasoning.
Claude works through the problem step-by-step internally before responding — like asking someone
to pause and really consider before speaking.

| Phrase | Effect |
|---|---|
| `think` | Claude reasons more carefully before answering |
| `think hard` | Deeper, more thorough reasoning — good for complex tasks |
| `think step by step` | Claude walks through logic one step at a time |

**When to use:** architecture decisions, debugging tricky bugs, planning complex features.

---

### Subagents — Specialized AI Helpers Claude Can Spawn

Claude can launch specialized subagents to handle parts of a task in parallel.

| Subagent | What it does |
|---|---|
| **Explore** | Read-only — searches and reads files without making any changes |
| **Plan** | Designs an implementation approach and considers trade-offs |
| **General-purpose** | Researches complex questions, searches code, multi-step tasks |

**How it works:** Claude spawns an agent for a specific job, gets the result back, then continues.
Like a manager delegating research to a team member before making a decision.

---

### Plan Mode — Deep Dive

**Two ways plan mode activates:**
1. **You press `Shift + Tab`** — cycles Claude into plan mode manually
2. **Claude calls `EnterPlanMode`** — Claude decides proactively for complex tasks

**Plan mode workflow:**
1. Claude explores your code with Explore subagents (read-only)
2. Claude writes a plan file with full architecture + steps
3. You review and approve (or reject) before Claude touches any file
4. Claude calls `ExitPlanMode` → you approve → implementation begins

**Key tools inside plan mode:**
| Tool | What it does |
|---|---|
| `EnterPlanMode` | Claude enters plan mode proactively |
| `ExitPlanMode` | Claude presents finished plan for your approval |
| `AskUserQuestion` | Claude asks you to choose between approaches |

---

### Security Concepts (from comment system)

| Term | Meaning |
|---|---|
| **XSS prevention** | Sanitizing user input before rendering — stops malicious code injection |
| **Soft delete** | Mark a record as deleted (`isDeleted: true`) instead of removing it permanently |
| **Security rules** | Database rules controlling who can read or write data |
| **Moderation** | System for flagging, hiding, and reviewing inappropriate content |
| **Auto-hide** | Automatically hiding content when it reaches a flag threshold (e.g. 5 flags) |

---

### Firebase Concepts

| Term | Meaning |
|---|---|
| **Firestore** | Firebase's real-time NoSQL cloud database |
| **onSnapshot** | Firestore listener — updates your UI live when data changes, no refresh needed |
| **Firebase Auth** | Built-in authentication — handles sign up, sign in, Google login |
| **CDN SDK** | Load Firebase via `<script>` tag — no bundler or npm needed |
| **Composite index** | Firestore index for queries that filter + sort on multiple fields |

---

---

### Custom Slash Commands — Create Your Own `/commands`

Create custom commands by adding `.md` files inside `.claude/commands/` in your project.

**Folder structure:**
```
your-project/
└── .claude/
    └── commands/
        └── summarize.md   →  type /summarize to run it
        └── review.md      →  type /review to run it
```

**How it works:**
- File name = command name (`summarize.md` → `/summarize`)
- File content = the instruction Claude follows when you run the command
- Great for tasks you repeat often — write it once, reuse forever

**Example `summarize.md` content:**
```
Read all files in this project and summarize what each one does.
```

---

### Hidden Files & the `.claude` Folder

| Concept | What it is |
|---|---|
| **Hidden files** | Files/folders starting with `.` are invisible by default on Mac |
| **`Cmd + Shift + .`** | Toggle hidden files on/off in Finder |
| **`.claude` folder** | Hidden folder Claude Code uses to store settings, commands, memory |
| **`.claude/commands/`** | Where custom slash commands live |
| **`.claude/settings.json`** | Claude Code configuration file (hooks, permissions, etc.) |
| **`.claude/CLAUDE.md`** | Instructions Claude reads about your project |

---

### All 4 Thinking Levels

| Phrase | Thinking budget | Best for |
|---|---|---|
| `think` | ~1,000 tokens | Small decisions, naming things |
| `think hard` | ~10,000 tokens | Architecture, planning features |
| `think harder` | ~20,000 tokens | Tricky bugs, security analysis |
| `ultrathink` | ~32,000 tokens | Full system design, critical decisions |

**How it works:** Claude reasons internally (like scratch paper) before writing its response.
More budget = more reasoning steps = better answers for hard problems.
**System reminder:** When you type `ultrathink`, Claude Code automatically tells Claude to use maximum reasoning depth.

---

---

### UI Component Development — Key Terms

| Term | What it means |
|---|---|
| `npx create-next-app` | Sets up a brand new Next.js project with all files ready to go |
| **Next.js** | A React framework — adds routing, pages, and folder structure on top of React |
| **TypeScript (`.tsx`)** | JavaScript with types — catches mistakes before they run |
| **PascalCase** | Naming style for React components — every word capitalized, no spaces (e.g. `MyCard`) |
| **Props / Interface** | How you pass data into a component — like settings you hand to it |
| **Variants** | Different visual styles of the same component (primary, danger, success, etc.) |
| **CSS custom properties** | `var(--color-primary)` — reusable color values defined once in `globals.css`, used everywhere |
| **Tailwind CSS** | Utility classes for styling directly in the component (like `p-5`, `rounded-xl`) |
| **`src/components/ui/`** | Conventional folder structure — one folder per component, reused across the app |
| **Preview page** | A dedicated page (`/preview`) just for viewing components in the browser — not shown to real users |
| **`disabled` state** | Common UI pattern — visually dims a component and blocks interaction |
| **`aria-disabled`** | Accessibility attribute that tells screen readers the element is disabled |

---

### Testing — Key Terms

| Term | What it means |
|---|---|
| **Jest** | JavaScript testing framework — runs your test files and reports pass/fail |
| `npm test` | Command to run all tests in the project |
| `jest.config.ts` | Config file that tells Jest how to behave (environment, setup files, etc.) |
| `setupFilesAfterEnv` | Jest config option — runs setup code before every test (e.g. loading jest-dom matchers) |
| **`@testing-library/react`** | Renders React components in tests so you can query and check them |
| **`@testing-library/jest-dom`** | Adds custom matchers like `toBeInTheDocument()` and `toHaveClass()` |
| `describe` | Groups related tests together under one label |
| `it` | A single test case — "it should do X" |
| `render` | Puts a component into memory so you can test it |
| `screen` | Lets you find elements in the rendered component (like `screen.getByText("Hello")`) |
| `toBeInTheDocument()` | Checks that an element exists on the page |
| `toHaveClass()` | Checks that an element has a specific CSS class applied |
| `toHaveAttribute()` | Checks that an element has a specific HTML attribute (e.g. `aria-disabled`) |
| `screen.getByAltText()` | Finds an image element by its `alt` text |
| `.parentElement` | In tests — gets the wrapper/parent element when the text is inside a child span |

---

### Avatar-Specific Patterns

| Term | What it means |
|---|---|
| **`initials` prop** | Passing text (e.g. `"MH"`) to show inside the avatar when there's no photo |
| **`src` prop** | Passing an image URL to display a real photo inside the avatar |
| **Fallback pattern** | Showing a default value (`?`) when no `src` or `initials` is provided — always have a backup |
| **`alt` attribute** | Text description of an image — used by screen readers for accessibility |
| **`object-cover`** | Tailwind class — makes an image fill its container without stretching |
| **`overflow-hidden`** | Tailwind class — clips content that goes outside the element's boundaries (keeps image inside circle) |
| **`rounded-full`** | Tailwind class — makes an element a perfect circle |

---

---

### Button-Specific Patterns

| Term | What it means |
|---|---|
| **`<button>` element** | A native clickable HTML element — built for interaction, unlike `<div>` which is just a container |
| **`onClick`** | A prop you pass to a button to run a function when clicked |
| **`extends React.ButtonHTMLAttributes`** | Lets the Button accept all standard HTML button props without listing them one by one |
| **`...props` (spread operator)** | Passes all remaining props down to the underlying element — so `<Button onClick={...}>` just works |
| **`transition-opacity`** | Tailwind class — smoothly animates the opacity change on hover |
| **`hover:opacity-90`** | Tailwind class — slightly dims the button when hovered |

---

### Testing — Button Extras

| Term | What it means |
|---|---|
| **`screen.getByRole("button")`** | Finds a button in tests by its HTML role — more reliable than finding by text |
| **`toBeDisabled()`** | Checks a button is actually disabled at the HTML level |
| **`jest.fn()`** | Creates a fake/mock function so you can check if it was called |
| **`userEvent.click()`** | Simulates a real user clicking an element in tests |
| **`toHaveBeenCalledTimes(1)`** | Checks the fake function was called exactly once |
| **`not.toHaveBeenCalled()`** | Checks the fake function was never called — used to verify disabled buttons block clicks |

---

### Custom Command Arguments (`$ARGUMENTS`)

| Term | What it means |
|---|---|
| **`$ARGUMENTS`** | Special variable in custom slash commands — captures everything typed after the command name |
| **`[name]`** | Placeholder in the command file — gets replaced with the parsed component name from `$ARGUMENTS` |
| **`[summary]`** | Placeholder in the command file — gets replaced with the component description from `$ARGUMENTS` |
| **`argument-hint`** | Field in command frontmatter — tells Claude what format the arguments should be in |
| **Pipe separator `\|`** | Splits arguments — e.g. `Button \| a clickable button` separates name from summary |
| **Frontmatter (`---`)** | Block at the top of a `.md` command file between `---` lines — holds metadata like `description` and `argument-hint` |
| **Dynamic commands** | Commands that behave differently based on arguments passed — more powerful than fixed commands |

**How it flows:**
```
/ui-component Button | a clickable button
        ↓
$ARGUMENTS = "Button | a clickable button"
        ↓
[name] = "Button"    [summary] = "a clickable button"
        ↓
Claude builds the component using those values
```

---

## Notes

- Ask Claude to **summarize keywords** anytime by just asking "summarize my keywords".
- Use **"think hard"** before complex requests to get deeper, more thorough answers.
- Use **`ultrathink`** for the most complex tasks — full system design, critical decisions.
