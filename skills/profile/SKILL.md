---
name: profile
description: 'Use when working on frontend projects, JavaScript/TypeScript tooling, Python tooling, project setup, dependency installation, formatting, linting, testing, command execution, or runtime environment management, or installing and organizing agent skills. Covers the preferred stack and default commands for mise, ni, nr, npx, na, uv, uvx, npx skills, editor, shell, Git, aliases, and code style. Prefer project-local agent documentation for project-specific toolchains, mise for Node and other runtime versions, ni for dependency installs, nr for package scripts, npx for common one-off Node tools, na create for supported create-* scaffolds in manual use, pnpm create for non-interactive agent scaffolding unless told otherwise, and uv/uvx for Python dependencies and one-off Python tools; avoid global pip installs.'
---

# Profile

Default conventions for project setup, dependency management, and toolchain decisions.

## Tech Stack

| Category           | Preference                                 |
| ------------------ | ------------------------------------------ |
| Language           | TypeScript                                 |
| Frontend Framework | React, Next.js, Vue, Nuxt                  |
| UI Library         | shadcn/ui, Element Plus, Vant              |
| Desktop            | Electron, Tauri                            |
| Backend            | Better Auth, Drizzle, Supabase, Bun, Nitro |
| Deploy             | Vercel, Netlify, Docker                    |

## Toolchain

| Category           | Preference                                                    |
| ------------------ | ------------------------------------------------------------- |
| Dependency Install | `ni`; use `ni --prefer-offline` for offline-friendly installs |
| Package Scripts    | `nr <script>`; aliases are for personal interactive use       |
| One-off Node Tool  | `npx <tool>`                                                  |
| Create Scaffolding | Manual: `na create <name>`; agent: `pnpm create <name>`       |
| Python Tool        | uv, uvx (avoid global pip installs)                           |
| Runtime Versions   | mise (node, pnpm, yarn, java)                                 |
| Editor             | VS Code + Vitesse Dark theme                                  |
| Shell              | Oh My Zsh + Starship                                          |
| Font               | FiraCode Nerd Font                                            |
| Git                | Disable CRLF auto-conversion, Ed25519 SSH                     |

## Command Habits

Personal interactive shells on macOS, Linux, and Windows may define short aliases or functions for common `nr` scripts and project navigation. Do not hard-code a shell-specific alias syntax in project docs or automation. Agents should prefer explicit non-interactive commands unless the user asks to use aliases.

- Install dependencies with `ni`.
- Use `ni --prefer-offline` for prefer-offline manual installs.
- Run package scripts with `nr <script>` when no alias is being used; script names should follow the project.
- Common personal aliases may map to scripts such as `start`, `dev`, `build`, `build --watch`, `test`, `test -u`, `test --watch`, `watch`, `play`, `typecheck`, `lint`, `lint --fix`, and `release`.
- Project navigation may use personal helpers under `~/i/<namespace>/<project>`, for example personal projects under `~/i/guanyme/`.
- Run temporary Node commands with `npx <tool>`.
- For supported `create-*` scaffolds, manual use prefers `na create <name>`.
- For agent non-interactive scaffolding, use `pnpm create <name>` unless the user explicitly asks for another command.
- Use `uv` and `uvx` for Python dependencies and one-off Python tools.
- Runtime versions come from mise. The global defaults live in `~/.config/mise/config.toml`; a project pins its own with `mise.toml`, `.node-version`, or the `packageManager` field in `package.json`.
- mise reads `packageManager` and `devEngines`, but **not** the traditional `engines.node` field. A project that relies on `engines.node` needs `mise.toml` or `.node-version` instead.
- In scripts, systemd units, CI and anything else non-interactive, call the shims by absolute path (`~/.local/share/mise/shims/<tool>`). `mise activate` only runs in interactive shells.
- **Never write a version number into an executable path.** `.../node-versions/v24.15.0/installation/bin/node` breaks the moment the runtime is upgraded; the shims resolve the version themselves.

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
