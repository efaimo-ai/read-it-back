# Changelog

All notable changes to read-it-back are documented here. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); this project uses
[Semantic Versioning](https://semver.org/).

## [0.1.0] - 2026-11-16

> **Published without provenance.** This is the first version of `read-it-back` on
> npm, and it came from an authenticated session: npm's trusted publishing is
> configured from an existing package's settings page, so it cannot create a
> package that has never been published. From the next version the release
> workflow publishes it, with SLSA provenance naming the commit that built it.

### Added

- **The skill is installable.** `npx read-it-back` copies `SKILL.md` and its
  `references/` into `./.claude/skills/read-it-back/`, with `--global`, `--dir`,
  `--check`, `--print`, `--uninstall` and `--force`. The installer reads every
  byte back after writing it and fails if what landed is not what it wrote, and
  it prints how many files it installed rather than only that it succeeded.
- Three exit codes rather than two: 0 installed or already identical, 1 present
  and different, 2 could not run at all. "It differs" and "I could not do this"
  are different answers and collapsing them is how a broken install reads as a
  clean one.
- CI on four cells (Ubuntu and Windows, Node 20 and 24), including an end to end
  run that packs the package the way npm would, installs it from that tarball,
  and installs the skill from there.

### Changed

- **Renamed from `read-back` to `read-it-back`.** npm compares package names
  without punctuation, so `read-back` is refused while `readback` exists. The
  skill name, the package name, the install directory and the repository
  change together. GitHub redirects the old repository address.
- The description also covers writing such a command for a script or CI step,
  so the command fails when nothing matched. An eval case that asked for a CI
  one-liner never loaded the skill before this line.
- The description now names the writes the skill is for (shell commands and
  scripts) and says to skip it after an edit tool that already fails on a
  missing match, which is what the body always said.
- Step 1 carries the counting code it calls the most valuable habit, plus the
  `grep -c` form for sed.
- A PowerShell tell: double-quoted `$` expansion, the backtick escape, and the
  Windows PowerShell 5.1 encoding default of `Set-Content` and `Add-Content`.
- The failure gallery's examples use generic paths.

### Notes

- The package version and the version in `SKILL.md` frontmatter are one number,
  pinned by a test.

[0.1.0]: https://github.com/efaimo-ai/read-it-back/releases/tag/v0.1.0
