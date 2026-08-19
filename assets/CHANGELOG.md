# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

### Fixed

## [1.1.3] - 2026-08-19

### Fixed
- Renamed the project to **Spec-Driven Guide** in both READMEs, in the Claude Code governance header and in the release script. The leftovers from the previous rename (`SDG Prompts`, `SDG Agents`, `SDG-Agents`) left a reader with three names for one project.
- Pointed the version badge and the `package.json` metadata at `spec-driven-guide-prompts`. The badge resolved `sdg-prompts`, a path that stopped answering once the repository was renamed, and `repository`, `bugs` and `homepage` relied on a GitHub redirect.
- Linked the `spec-driven-guide` CLI from the navigation bar of both READMEs, beside `specdrivenguide.org`. Neither README pointed at the package that runs these tracks.

## [1.1.2] - 2026-07-22

### Fixed
- Rewrote both READMEs (EN/PT-BR) in the Writing Soul voice: removed inflated openers, passive constructions, unglossed jargon and every em dash.
- Added a **Concepts** table to both READMEs, grouped in four blocks (cycle, project maturity, specification, governance), so newcomers can decode the technical terms used across the tracks.
- Added explicit ASCII anchors (`phase-*` / `fase-*`) to the phase headings of both guides, so cross-links no longer depend on accented or renamed heading text.

## [1.1.1] - 2026-06-29

### Fixed
- Corrected broken relative links to `assets/REFERENCES*.md` in the EN/PT-BR guides and to `LICENSE` in `assets/README.pt-BR.md` (wrong directory depth).

## [1.1.0] - 2026-04-16

### Added
- New **Methodology & References** documentation in `assets/` (EN/PT-BR).
- Standardized 6-step SPEC pattern naming and structure for all tracks.

### Changed
- Modernized all 50+ prompt tracks to the mandatory 6-step SPEC pattern.
- Reorganized project structure: `README.md` (root), `README.pt-BR.md` (`assets/`), `CHANGELOG.md` (root).
- Improved link integrity and cross-language navigation across the entire ecosystem.

### Removed
- Obsolete "Creative Assets" section and related files.
- Obsolete "UI Specification Guide" from documentation.

## [1.0.0] - 2026-04-16

### Added
- Initial release of the **SDG Prompts** ecosystem.
- Complete documentation tracks in English (`en/`) and Brazilian Portuguese (`pt-BR/`).
- Spec-Driven Governance Guide.
- Prompt tracks for Lite Mode, New Evolution, and Legacy Modernization.
- Automated versioning setup with `bumpp`.
- Regional badges (US/BR) and Version status.
