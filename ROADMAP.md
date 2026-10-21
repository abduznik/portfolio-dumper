# Roadmap

Portfolio Dumper turns a GitHub person or organisation into clean, LLM-friendly Markdown. The long-term aim is to be the **person-level counterpart to tools like GitIngest**: they answer "what is in this codebase?", this answers "who is this developer and what have they built?"

## How versions work

Work is grouped into [milestones](https://github.com/abduznik/portfolio-dumper/milestones) of a few issues each. **Closing a milestone ships a version**:

| Milestone | Version bump |
|---|---|
| Each roadmap milestone | next minor while pre-1.0 (`0.1.0`, `0.2.0`, ...) |
| `v1.0.0` | the portfolio generator and a stable core/CLI interface |
| A fix between milestones | patch (`0.1.1`), no milestone needed |

### Release checklist

1. Every issue in the milestone is closed, or has been moved to a later milestone with a comment saying why.
2. In `CHANGELOG.md`, give the release its version and date.
3. Bump the version in the site footer (`#siteVersion` in `index.html`).
4. Merge to `main` (this deploys the site and publishes the Docker image).
5. Tag and release: `git tag vX.Y.Z && git push origin vX.Y.Z`, then create a GitHub Release from the changelog entry.
6. Close the milestone.

## Milestones

### [v0.1.0](https://github.com/abduznik/portfolio-dumper/milestone/1): Fix the basics
Verified bugs in the original page.
- [#2](https://github.com/abduznik/portfolio-dumper/issues/2) Profile README lookup is case-sensitive and silently skipped
- [#3](https://github.com/abduznik/portfolio-dumper/issues/3) Stats cards show the previous run's numbers
- [#4](https://github.com/abduznik/portfolio-dumper/issues/4) User input is written to innerHTML
- [#6](https://github.com/abduznik/portfolio-dumper/issues/6) Single-repo ingestion omits repo metadata and ignores the mode selector
- [#7](https://github.com/abduznik/portfolio-dumper/issues/7) Show a useful message on rate limits
- [#8](https://github.com/abduznik/portfolio-dumper/issues/8) Harden input parsing (query strings, .git, @user, org profiles)

### [v0.2.0](https://github.com/abduznik/portfolio-dumper/milestone/2): Core and CLI
Make the logic reusable and add a terminal front-end.
- [#9](https://github.com/abduznik/portfolio-dumper/issues/9) Extract a DOM-free core module and add tests
- [#10](https://github.com/abduznik/portfolio-dumper/issues/10) CLI mode: npx portfolio-dumper <user|url>
- [#11](https://github.com/abduznik/portfolio-dumper/issues/11) Output controls: forks, archived, sort, limit, min-stars, language
- [#5](https://github.com/abduznik/portfolio-dumper/issues/5) PAT does not unlock private repos
- [#17](https://github.com/abduznik/portfolio-dumper/issues/17) Self-hosted CSS/fonts and release hygiene

### [v0.3.0](https://github.com/abduznik/portfolio-dumper/milestone/3): LLM-ready output
Make the output fit prompts.
- [#12](https://github.com/abduznik/portfolio-dumper/issues/12) Token budget and JSON/XML output formats
- [#13](https://github.com/abduznik/portfolio-dumper/issues/13) Pinned repos, language breakdown and private repos via GraphQL
- [#20](https://github.com/abduznik/portfolio-dumper/issues/20) Prompt presets

### [v0.4.0](https://github.com/abduznik/portfolio-dumper/milestone/4): Reach
More ways to run it.
- [#14](https://github.com/abduznik/portfolio-dumper/issues/14) Shareable deep links
- [#15](https://github.com/abduznik/portfolio-dumper/issues/15) GitHub Action to keep a PORTFOLIO.md up to date
- [#16](https://github.com/abduznik/portfolio-dumper/issues/16) MCP server

### [v1.0.0](https://github.com/abduznik/portfolio-dumper/milestone/5): Portfolio
- [#18](https://github.com/abduznik/portfolio-dumper/issues/18) Generate a shareable portfolio page from the dump
- [#19](https://github.com/abduznik/portfolio-dumper/issues/19) Organisations, multi-user comparison and other Git providers

## Principles

- **Static and secure.** No backend, no accounts, no stored tokens. Anything that needs a secret runs locally.
- **No build step for the page.** `index.html` should keep working from a plain file server.
- **Zero runtime dependencies** for the core and the CLI.
