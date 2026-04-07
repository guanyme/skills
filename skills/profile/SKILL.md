---
name: profile
description: 'Use when working on frontend projects, JavaScript/TypeScript tooling, Python tooling, project setup, dependency installation, formatting, linting, testing, command execution, or runtime environment management. Covers the preferred stack and default commands for Vite+, vp, vpx, uv, uvx, editor, shell, Git, and code style. Prefer uv and uvx for Python dependencies and one-off Python tools; avoid global pip installs.'
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

| Category                  | Preference                                   |
| ------------------------- | -------------------------------------------- |
| Web Toolchain             | Vite+ via `vp`                               |
| Package Manager Interface | `vp install`, `vp add`, `vp remove`          |
| Formatting                | `vp fmt`                                     |
| Linting and Checks        | `vp lint`, `vp check`                        |
| Testing                   | `vp test`                                    |
| Python Tool               | uv, uvx (avoid global pip installs)          |
| Run Command               | `vp exec`, `vpx`, uvx (avoid global install) |
| Node Version Manager      | `vp env`                                     |
| Editor                    | VS Code + Vitesse Dark theme                 |
| Shell                     | Oh My Zsh + Starship                         |
| Font                      | FiraCode Nerd Font                           |
| Git                       | Disable CRLF auto-conversion, Ed25519 SSH    |

## Code Style

| Category     | Preference |
| ------------ | ---------- |
| Indent       | 2 spaces   |
| Line Endings | LF         |
| Semicolons   | No         |
| Quotes       | Single     |
| Theme Color  | #3498db    |
