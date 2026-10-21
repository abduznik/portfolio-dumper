# Changelog

All notable changes to this project are documented here. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and each version corresponds to a milestone in the [roadmap](ROADMAP.md).

## [0.1.0] - 2026-10-21

First tagged version. Fixes the verified bugs in the original page.

### Fixed
- The profile README is found regardless of file name or case (it used to require exactly `README.md`), and a missing one is noted in the output instead of silently skipped. [#2](https://github.com/abduznik/portfolio-dumper/issues/2)
- The stat cards reset on every run, and are hidden in README-only mode, so they no longer show the previous run's numbers. [#3](https://github.com/abduznik/portfolio-dumper/issues/3)
- Status and error messages are rendered as text rather than HTML, closing an HTML-injection path through the input field. [#4](https://github.com/abduznik/portfolio-dumper/issues/4)
- Rate-limit, invalid-token and network failures now say what happened, when the limit resets and how to raise it. The empty-input `alert()` is now an inline message. [#7](https://github.com/abduznik/portfolio-dumper/issues/7)
- The README and the token hint no longer claim that a token unlocks private repositories; that is tracked in [#5](https://github.com/abduznik/portfolio-dumper/issues/5) for 0.2.0.

### Added
- Single-repository ingestion includes repository metadata (description, URL, homepage, language, topics, license, stars, forks, last push) and honours the ingestion mode. A repository without a README is reported as such. [#6](https://github.com/abduznik/portfolio-dumper/issues/6)
- Input parsing accepts `@handle`, query strings and fragments, `.git` and SSH clone URLs, and `github.com/orgs/<org>` pages, and rejects invalid names with a clear message. [#8](https://github.com/abduznik/portfolio-dumper/issues/8)
- Organisation pages are ingested using the organisation's `.github/profile/README.md`. [#8](https://github.com/abduznik/portfolio-dumper/issues/8)
- The site footer shows the current version and links to this changelog.

### Changed
- In "Everything" mode a profile without a README now gets a `*No profile README found.*` line in the output.
- A "user or organization not found" error is reported before any other request, at the cost of one extra API request per profile ingest.
