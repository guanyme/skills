---
name: convention
description: 'Project conventions and documentation standards. Use when creating, writing, or reviewing README files, documentation structure, or project-level conventions. Use when the user asks how to write a README or needs bilingual documentation. Topics: README, documentation, convention, standard, format, bilingual, Chinese, English, README.zh.'
---

# Convention

Project conventions and documentation standards.

## README

Project README must provide both English (`README.md`) and Chinese (`README.zh.md`) versions, following a fixed structure:

- One `#` (H1): project name
- `{{emoji}} {{description}}` directly under H1
- Tech stack table (if applicable) directly under `{{emoji}} {{description}}`
- Three `##` (H2) sections as the main structure: Install, Usage, License (Chinese: 安装, 使用说明, 使用许可)
- Additional content under `###` (H3) titles within corresponding H2 sections as needed
- No other H1 or H2 sections allowed

### Example

```md
# my-app

🚀 A Vue 3 application

| Category  | Stack      |
| --------- | ---------- |
| Framework | Vue 3      |
| UI        | shadcn-vue |
| Deploy    | Vercel     |

## Install

...

## Usage

### Development

...

### Build

...

## License

[MIT](https://opensource.org/licenses/MIT) © {{author}}
```
