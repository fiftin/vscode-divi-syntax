# Repository Guidelines

## Project Structure & Module Organization
- `package.json` defines the VS Code contribution (language id, grammar path, activation data); keep schema-aligned so packaging succeeds.
- `language-configuration.json` sets editor behaviors (pair matching, commenting) and should evolve in lockstep with grammar keywords.
- `syntaxes/divi.tmLanguage.json` holds the TextMate rules; add new scopes inside the `repository` map and reuse shared patterns via `include` blocks.
- Generated artifacts such as `divi-shortcodes-syntax-0.1.0.vsix` live at the repo root; do not edit them manually—regenerate when grammar changes.

## Build, Test, and Development Commands
- `npm install -g @vscode/vsce` installs the packaging CLI once per workstation.
- `vsce package` (run from repo root) lints the manifest, compiles nothing, and emits `divi-shortcodes-syntax‑<version>.vsix`.
- `code --extensionDevelopmentPath=$(pwd)` launches VS Code with this extension linked for quick, iterative grammar testing.
- Inside VS Code press `F5` to start an Extension Development Host; open a `.divi` file from `test/fixtures` or your WordPress export to validate highlighting.

## Coding Style & Naming Conventions
- JSON files use 2-space indentation, double quotes, and sorted keys where it aids readability; avoid trailing commas because VS Code’s loader is strict.
- Scope names follow `domain.category.detail` (e.g., `punctuation.definition.tag.divi`), mirroring existing entries to keep them predictable for theming.
- When defining new shortcode matchers, prefer verbose, commented regex blocks to clarify the intended tokens.

## Testing Guidelines
- There is no automated test suite; rely on VS Code’s `Developer: Inspect TM Scopes` command to confirm new regex scopes fire as expected.
- Maintain a library of representative `.divi` snippets under `test/fixtures/` so reviewers can reproduce edge cases.
- Before packaging, open the generated `.vsix` in a clean VS Code profile to ensure no accidental dependencies on global settings.

## Commit & Pull Request Guidelines
- Git history favors concise, imperative summaries (“Add Divi shortcode VS Code syntax highlighting”); keep body text minimal but explain regex intent when non-trivial.
- Reference related issues in commit bodies or PR descriptions using `Fixes #123` to trigger automation.
- PRs should include: purpose, notable grammar/regex additions, verification steps (commands run, scopes inspected), and screenshots or GIFs showing before/after highlighting when user-facing colors change.
