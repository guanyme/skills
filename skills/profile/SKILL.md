---
name: profile
description: 'Use when working on frontend projects, JavaScript/TypeScript tooling, Python tooling, project setup, dependency installation, formatting, linting, testing, command execution, or runtime environment management. Covers the preferred stack and default commands for fnm, ni, nr, npx, na, uv, uvx, editor, shell, Git, aliases, and code style. Prefer project-local agent documentation for project-specific toolchains, fnm for Node versions, ni for dependency installs, nr for package scripts, npx for common one-off Node tools, na create for supported create-* scaffolds in manual use, pnpm create for non-interactive agent scaffolding unless told otherwise, and uv/uvx for Python dependencies and one-off Python tools; avoid global pip installs.'
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

| Category             | Preference                                                    |
| -------------------- | ------------------------------------------------------------- |
| Dependency Install   | `ni`; use `ni --prefer-offline` for offline-friendly installs |
| Package Scripts      | `nr <script>`; aliases are for personal interactive use       |
| One-off Node Tool    | `npx <tool>`                                                  |
| Create Scaffolding   | Manual: `na create <name>`; agent: `pnpm create <name>`       |
| Python Tool          | uv, uvx (avoid global pip installs)                           |
| Node Version Manager | fnm                                                           |
| Editor               | VS Code + Vitesse Dark theme                                  |
| Shell                | Oh My Zsh + Starship                                          |
| Font                 | FiraCode Nerd Font                                            |
| Git                  | Disable CRLF auto-conversion, Ed25519 SSH                     |

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

## Code Style

| Category     | Preference |
| ------------ | ---------- |
| Indent       | 2 spaces   |
| Line Endings | LF         |
| Semicolons   | No         |
| Quotes       | Single     |
| Theme Color  | #3498db    |
