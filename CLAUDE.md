# CLAUDE.md

## Project: Personal GitHub Profile

Personal GitHub profile repository (github.com/aletsdelarosa). A markdown-only showcase of work experience, projects,
skills, and certifications.

### Key Context

- The owner is a Software Engineer with 10+ years of experience across iOS (Swift/SwiftUI), Flutter, web (React,
  Next.js, Angular, Laravel), and backend (C#, Node.js).
- Current role at eBay. Previous roles include Meta, GitHub (Codespaces), and Microsoft (Live Share).
- Currently runs a startup called My Digital Moment (wedding invites platform).
- Fluent in English and Spanish.

### Tech Stack

- Markdown (GitHub-Flavored)
- Node.js 25+ / pnpm 10.28
- Prettier (formatting) via `prettier.config.mjs`
- markdownlint-cli2 (linting) via `.markdownlint-cli2.yaml`
- Husky + lint-staged + commitlint (git hooks)
- GitHub Actions (CI)

### Project Structure

```text
aletsdelarosa/
  README.md               # GitHub profile page
  resume.pdf              # Downloadable resume
  CLAUDE.md               # Claude Code guidance
  package.json            # Dev tooling config
  prettier.config.mjs     # Prettier config
  .markdownlint-cli2.yaml # Markdownlint config
  commitlint.config.mjs   # Commit message validation
  .husky/                 # Git hooks
  .github/workflows/      # CI pipeline
  .vscode/                # IDE settings
```

### Conventions

#### README Section Order

1. Title + typing SVG animation (HTML)
2. Contact badges row (LinkedIn, Email, Blog, Resume -- HTML)
3. About Me (paragraph)
4. Work Experience (reverse-chronological entries)
5. Side Projects (table)
6. Education (emoji + bold entries)
7. Tech Stack (badge images grouped by category)
8. Certifications & Awards (emoji + bold entries)
9. Languages
10. GitHub stats widgets (HTML, dark/light aware)
11. Profile views counter (HTML)

#### Work Experience Entry Format

Each role follows this exact structure:

```markdown
### <img src="https://img.shields.io/badge/COMPANY-COLOR?style=flat&logo=LOGO&logoColor=white" alt="Company"/> &nbsp; Role Title

**Start Date -- End Date** · Location

[Optional product links with emoji]

- Bullet with impact metric in **bold**
- Another bullet
```

- Heading uses a shields.io badge image for the company logo.
- Date line is bold, followed by `·` and location.
- Optional links row uses emoji shortcodes (`:computer:`, `:iphone:`, `:robot:`).
- Bullets emphasize metrics: **1.6B+ users**, **75%**, **40%**, etc.

#### Side Projects Table Format

```markdown
| **[Name](url)** | Tech stack | One-line description |
```

#### Education / Certifications Format

```markdown
:emoji: **Title** -- Institution (Year)
```

#### External Services & URL Patterns

##### shields.io Badges

Header badges (contact row):

```text
https://img.shields.io/badge/LABEL-COLOR?style=for-the-badge&logo=LOGO&logoColor=white
```

Heading badges (work experience):

```text
https://img.shields.io/badge/COMPANY-COLOR?style=flat&logo=LOGO&logoColor=white
```

Tech stack badges:

```markdown
![Label](https://img.shields.io/badge/LABEL-COLOR?style=flat&logo=LOGO&logoColor=white)
```

Use `style=for-the-badge` only for the contact row. Use `style=flat` everywhere else.

##### Typing SVG

```text
https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=58A6FF&center=true&vCenter=true&width=600&lines=Line+1;Line+2;Line+3
```

Separate lines with `;`. URL-encode special characters.

##### GitHub Streak Stats

```text
https://streak-stats.demolab.com?user=aletsdelarosa&theme=THEME&hide_border=true
```

Themes: `github-dark-blue` (dark), `default` (light).

##### Profile Views Counter

```text
https://komarev.com/ghpvc/?username=aletsdelarosa&color=58A6FF&style=flat-square&label=Profile+Views
```

#### Dark/Light Mode Pattern

Use `<picture>` with `prefers-color-scheme` media queries for any dynamic image that should adapt to the viewer's GitHub
theme:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="dark-url" />
  <source media="(prefers-color-scheme: light)" srcset="light-url" />
  <img src="fallback-url" alt="Description" />
</picture>
```

The `<picture>` and `<source>` elements are in the markdownlint HTML allowlist. Currently used for the GitHub stats
widgets.

#### Editing Guidelines

- The README uses GitHub-flavored Markdown with emoji shortcodes (`:iphone:`, `:computer:`, `:trophy:`).
- Work experience is ordered reverse-chronologically.
- Each role includes bullet points highlighting impact with metrics where available.
- External links point to live apps/sites -- verify they still work before adding or changing links.
- Inline HTML is allowed for specific elements only (`p`, `a`, `img`, `br`, `hr`, `strong`, `em`, `code`, `details`,
  `summary`, `picture`, `source`).
- Line length limit is 120 chars (code blocks, tables, and headings are exempt).
- Use `<!-- markdownlint-disable MD013 -->` / `<!-- markdownlint-enable MD013 -->` around HTML blocks with long URLs
  that cannot be wrapped.
- Both `README.md` and `CLAUDE.md` must pass linting.

### Key Commands

```text
pnpm run format        # Prettier format all markdown
pnpm run format:check  # Prettier check (no write)
pnpm run lint:md       # Markdown lint check
pnpm run lint:md:fix   # Markdown lint with auto-fix
pnpm run fix           # Auto-format + auto-fix all markdown
pnpm run check         # Verify formatting + linting (no mutations)
```

### Pre-Completion Verification (Required)

Before completing any changes, run the full validation suite:

```bash
pnpm run check
```

All commands must exit with code 0. **After every edit to any `.md` file, run `pnpm check` and fix any violations before
considering the task done.**
