# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 1.0.0 (2026-01-06)


### Features

* initial mistral-codestral.nvim plugin release ([b08ff7b](https://github.com/jrollin/mistral-codestral.nvim/commit/b08ff7b46533f8272b2a3177b293276632084eef))
* setup automated releases ([58728a9](https://github.com/jrollin/mistral-codestral.nvim/commit/58728a9aa3d46b20b40387615914fe0ef1c0868d))


### Bug Fixes

* resolve all luacheck warnings ([a290d6c](https://github.com/jrollin/mistral-codestral.nvim/commit/a290d6c681028a7222804639e8aaca3a4f631ddb))

## [Unreleased]

## [0.0.0] - 2026-01-03

### Added
- Initial mistral-codestral.nvim plugin release
- Intelligent code completion using Mistral Codestral API
- Support for blink.cmp and nvim-cmp completion engines
- Virtual text inline suggestions (GitHub Copilot style)
- Context-aware completions via LSP integration
- Smart caching for repeated completions (5-second TTL)
- Buffer and filetype exclusions (help, neo-tree, terminals)
- Non-blocking async API calls with configurable timeout
- Comprehensive diagnostic scripts:
  - `debug_completion.lua` - Full diagnostic check (`:DiagnoseMistral`)
  - `direct_test.lua` - Step-by-step verification
  - `verify_fix.lua` - Verify response parsing fix
  - `diagnose.sh` - Quick command-line diagnostic
- Full test suite (integration, plugin, API tests)
- Health check command (`:checkhealth mistral-codestral`)
- Complete documentation suite in `/docs`:
  - Architecture documentation with flow diagrams
  - Configuration guide
  - Virtual text mode documentation
  - Completion engines setup guide
  - Troubleshooting guide
  - Quick start guide
  - Testing guide

### Fixed
- Response parsing bug in API handling
  - Issue: Plugin was looking for `response.choices[1].text` but Mistral API returns completions in `response.choices[1].message.content`
  - Fix: Updated response parsing to handle both formats for compatibility
  - Impact: Completions now work correctly for all users

### Documentation
- Streamlined quick-start.md to true "30-second" verification
- Enhanced testing-guide.md with cross-references
- Consolidated testing documentation to reduce ~40% redundancy
- Improved docs/README.md navigation structure
- All docs follow DRY principle with strategic cross-references
- Abstracted hardcoded plugin paths to `<plugin-dir>` convention
- Enhanced cross-linking between troubleshooting resources

### Changed
- Organized all test files and documentation into proper structure:
  - `docs/` - All documentation
  - `tests/` - All test files and fixtures
  - `scripts/` - Utility scripts
- Updated main README with testing section
- Improved error handling in diagnostic scripts
- Removed outdated `test-report.md` (snapshot no longer relevant)
- Removed legacy `reference.md` (replaced by CONFIGURATION.md)
