# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Structure

This repo has two parts:

1. **Root HTML project** — plain HTML/CSS/JS files (`index.html`, `about.html`) for practicing basic Claude Code skills. No build step needed; open files directly in a browser.

2. **`my-app/`** — a Next.js 16 + React 19 + TypeScript + Tailwind CSS app for building and testing UI components.

## my-app Commands

Run all commands from inside `my-app/`:

```
npm run dev     # start dev server at localhost:3000
npm test        # run all Jest tests
npm run build   # production build
npm run lint    # ESLint
```

Run a single test file:
```
npx jest src/components/ui/button/Button.test.tsx
```

## my-app Architecture

- **`src/components/ui/`** — reusable UI components (avatar, badge, button, card). Each component lives in its own folder.
- **`src/app/preview/page.tsx`** — browser-only preview page at `/preview` for viewing components visually. Not shown to real users.
- **`src/app/globals.css`** — CSS custom properties (design tokens) used across all components via `var(--...)`.
- Tests live alongside components using Jest + React Testing Library.
