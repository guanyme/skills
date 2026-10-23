---
name: profile
description: 'Use when starting or working on frontend or backend projects, choosing libraries, setting up JavaScript/TypeScript or Python tooling, installing dependencies, running scripts, formatting, linting, testing, managing runtime versions, writing commit messages or code comments, running long-running tasks, or installing agent skills. Covers the preferred stack (React with Next.js, TanStack Start or Vite SPA; uni-app for mini programs; Hono, NestJS), scenario libraries (TanStack Query, Table, Router, Form, Virtual, Zustand, Zod, next-intl, Paraglide, dnd-kit, React Flow, Recharts, GSAP), commit and comment language by Git remote (GitHub English, Codeup Chinese), Herdr for long-running tasks locally or on VPS, and default commands for mise, ni, nr, npx, na, uv, uvx, oxlint, oxfmt, npx skills, editor, shell, aliases, and code style. Avoid global pip installs.'
---

# Profile

Default conventions for project setup, dependency management, and toolchain decisions.

## Tech Stack

| Category           | Preference                                                           |
| ------------------ | -------------------------------------------------------------------- |
| Language           | TypeScript                                                           |
| Frontend Framework | React (Next.js, TanStack Start, Vite SPA); uni-app for mini programs |
| UI Library         | shadcn/ui                                                            |
| Styling            | Tailwind CSS (including uni-app)                                     |
| Desktop            | Electron, Tauri                                                      |
| Backend            | Hono, NestJS, Better Auth, Drizzle, Bun                              |
| Deploy             | Docker (compose), Vercel                                             |

## Libraries

Prefer these libraries when the scenario comes up. If the project already uses another library for the same job, follow the project.

| Scenario                                 | Preference                      |
| ---------------------------------------- | ------------------------------- |
| Full-stack, SSR, content and SEO sites   | Next.js                         |
| Full-stack apps built on TanStack Router | TanStack Start                  |
| SPA (admin panels, desktop shells)       | Vite + TanStack Router          |
| UI components                            | shadcn/ui on Base UI            |
| i18n in Next.js                          | next-intl                       |
| i18n in TanStack Start and Vite SPA      | Paraglide JS                    |
| Client state                             | Zustand                         |
| Async data fetching and caching          | TanStack Query                  |
| Headless tables and data grids           | TanStack Table                  |
| Type-safe routing                        | TanStack Router                 |
| Headless forms                           | TanStack Form                   |
| Long-list virtual scrolling              | TanStack Virtual                |
| Schema validation                        | Zod                             |
| Dates                                    | date-fns                        |
| Drag and drop                            | dnd-kit                         |
| Flow charts and node editors             | React Flow (`@xyflow/react`)    |
| Charts                                   | Recharts (via shadcn/ui charts) |
| Animation                                | GSAP (`@gsap/react`)            |
| LLM calls and streaming                  | Vercel AI SDK                   |
| Markdown and AI streaming output         | Streamdown                      |
| Performance                              | React Compiler                  |
| Unit testing                             | Vitest                          |
| E2E testing                              | Playwright                      |

## Toolchain

| Category           | Preference                                                                                           |
| ------------------ | ---------------------------------------------------------------------------------------------------- |
| Dependency Install | `ni`; use `ni --prefer-offline` for offline-friendly installs                                        |
| Package Scripts    | `nr <script>`; aliases are for personal interactive use                                              |
| One-off Node Tool  | `npx <tool>`                                                                                         |
| Create Scaffolding | tlyboy starters (`starter` skill); otherwise manual: `na create <name>`, agent: `pnpm create <name>` |
| Lint / Format      | oxlint, oxfmt                                                                                        |
| Python Tool        | uv, uvx (avoid global pip installs)                                                                  |
| Runtime Versions   | mise (node, pnpm, yarn, java)                                                                        |
| Editor             | VS Code + Vitesse Dark theme                                                                         |
| Shell              | Oh My Zsh + Starship                                                                                 |
| Font               | FiraCode Nerd Font                                                                                   |
| Git                | Disable CRLF auto-conversion, Ed25519 SSH                                                            |

## Command Habits

Personal interactive shells on macOS, Linux, and Windows may define short aliases or functions for common `nr` scripts and project navigation. Do not hard-code a shell-specific alias syntax in project docs or automation. Agents should prefer explicit non-interactive commands unless the user asks to use aliases.

- Install dependencies with `ni`.
- Use `ni --prefer-offline` for prefer-offline manual installs.
- Run package scripts with `nr <script>` when no alias is being used; script names should follow the project.
- Common personal aliases may map to scripts such as `start`, `dev`, `build`, `build --watch`, `test`, `test -u`, `test --watch`, `watch`, `play`, `typecheck`, `lint`, `lint --fix`, and `release`.
- Project navigation may use personal helpers under `~/i/<namespace>/<project>`, for example personal projects under `~/i/guanyme/`.
- Run temporary Node commands with `npx <tool>`.
- For a new project, check the `starter` skill (tlyboy starters pulled with giget) first; for Docker Compose services, the `compose` skill.
- For supported `create-*` scaffolds, manual use prefers `na create <name>`.
- For agent non-interactive scaffolding, use `pnpm create <name>` unless the user explicitly asks for another command.
- Use `uv` and `uvx` for Python dependencies and one-off Python tools.
- Runtime versions come from mise. The global defaults live in `~/.config/mise/config.toml`; a project pins its own with `mise.toml`, `.node-version`, or the `packageManager` field in `package.json`.
- mise reads `packageManager` and `devEngines`, but **not** the traditional `engines.node` field. A project that relies on `engines.node` needs `mise.toml` or `.node-version` instead.
- In scripts, systemd units, CI and anything else non-interactive, call the shims by absolute path (`~/.local/share/mise/shims/<tool>`). `mise activate` only runs in interactive shells.
- **Never write a version number into an executable path.** `.../node-versions/v24.15.0/installation/bin/node` breaks the moment the runtime is upgraded; the shims resolve the version themselves.

## Git Commits & Comments

- Use Conventional Commits: `type(scope): subject`. The `type` is always English (`feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `style`, ...).
- The first commit of a repository is always `feat: initial`.
- Pick the language of the subject and of code comments from `git remote get-url origin`:

| Remote                     | Commit subject              | Code comments            |
| -------------------------- | --------------------------- | ------------------------ |
| `github.com` (open source) | English                     | English                  |
| `codeup.aliyun.com`        | Chinese                     | Chinese                  |
| Other or none              | Follow the existing history | Follow the existing code |

- Project-local agent documentation (`AGENTS.md`, `CLAUDE.md`) overrides these defaults.

## Long-running Tasks

- Run time-consuming or resident processes (dev servers, watchers, long builds, crawlers, batch jobs, services) in Herdr panes. Use Herdr like tmux: a pane can run any command, not only coding agents.
- The `herdr` CLI reaches the local server from any shell, inside a Herdr pane or not, so the inside-only check in the `herdr` skill does not apply to these tasks.
- Tasks for a VPS run on the VPS's own Herdr server, so they keep running after the SSH connection drops. Do not open a local pane that runs `ssh <host> <command>`.
- Drive the remote Herdr with `ssh <host> herdr <command>` (e.g. `ssh <host> herdr pane ...`). Herdr is installed manually on each VPS; non-interactive SSH may not load the login `PATH`, so use the absolute path (often `~/.local/bin/herdr`) if `herdr` is not found.
- Machines saved with `herdr machine add` can also be driven locally with `herdr --machine <label> <command>`; check `herdr machine list` first.
- Take command syntax from the `herdr` skill and `herdr --help`.

## Agent Skills

Manage skills with `npx skills`. A cloned project should come with the skills its stack needs, so stack-specific skills belong to the project, not the global scope.

| Scope         | Contents                                                                                                  |
| ------------- | --------------------------------------------------------------------------------------------------------- |
| Global (`-g`) | Personal conventions (this repository), skill discovery, and skills for tools installed on the machine    |
| Project       | Skills for the libraries and frameworks the project depends on; install only where the dependency is used |

- Install project skills for both Claude Code and Codex: `npx skills add <source> -s '*' -a claude-code -a codex -y`. Repeat `-s` and `-a` for multiple values; comma-separated values are not parsed.
- The canonical copy goes to `.agents/skills/` (read by Codex and other universal agents) and `.claude/skills/` symlinks to it. Commit `.agents/skills/`, `.claude/skills/`, and `skills-lock.json` together.
- When a source ships several skills for one product, install all of them. Skip skills written for the source repository's own maintainers (descriptions that mention "this repository" or internal tooling), migration skills for versions the project has already passed, and unused skills from mixed collections such as `vercel-labs/agent-skills` or `stripe/ai`.
- Remove with `npx skills remove -s <name> -y` **without** `-a`. With `-a`, only the agent links are removed; the copy and the lock entry stay.
- Update project skills when upgrading the dependency they document: `npx skills update -p -y`, committed separately from code changes.

## Code Style

| Category     | Preference |
| ------------ | ---------- |
| Indent       | 2 spaces   |
| Line Endings | LF         |
| Semicolons   | No         |
| Quotes       | Single     |
| Theme Color  | #3498db    |
