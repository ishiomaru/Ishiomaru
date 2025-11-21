# Repository Guidelines

## Project Structure & Module Organization
- `README.md` is the canonical profile page; every change targets this Markdown document, and its `<style>` block implements the Light Tritanopia palette, typography scale, and responsive layout described in `docs/design.md`.
- Supporting materials live in `docs/` (requirements, design, task tracking) and `docs-review` / `docs-sample` for reference drafts; keep discussions and decisions focused there to avoid bloating the README.
- Configuration files (`.markdownlint.json`) sit at the root; future GitHub Actions workflows (e.g., updating stats images under `assets/`) should land in `.github/workflows/` as outlined in the design requirements.

## Build, Test, and Development Commands
- There is no build step—this repository delivers a single README. Use `npx markdownlint README.md docs/**/*.md` to validate formatting before commits; it uses the root `.markdownlint.json`.
- Preview locally by opening `README.md` in a Markdown-supporting viewer or GitHub desktop; confirm responsive behaviors by resizing the window to mimic mobile widths (≤480px) as described in the requirements.
- GitHub Actions (scheduled via `update-stats.yml` once added) handles stats image generation. No npm scripts or bundlers are required.

## Coding Style & Naming Conventions
- Follow Markdown best practices: use GitHub-flavored Markdown headings, keep paragraphs concise, and lean on tables for structured data (e.g., stats/layout descriptions).
- Keep inline styles limited to the README’s `<style>` block; reuse the documented spacing (`space-*`) and font (`font-*`) tokens each time you add a section.
- Naming: treat new assets or workflow files with lowercase hyphenation (`update-stats.yml`, `stats-card.svg`) to stay consistent with the planned structure.

## Testing Guidelines
- The only automated check today is `markdownlint`; run it against docs and README after edits. There are no unit or integration tests yet.
- Include manual checks: confirm the first-view sections render in one viewport and that the cards/table maintain the Visual/Accessibility goals from `docs/design.md`.
- If you add tooling later (e.g., Lighthouse CI), document how to invoke it in this guide and under the relevant docs.

## Commit & Pull Request Guidelines
- Keep commit messages short and descriptive—use a conventional pattern such as `feat:`, `fix:`, or `chore:` followed by a brief summary (example: `chore: refresh README badges`).
- PRs should describe the user-facing change, reference any relevant issue or requirement from `docs/`, and explain how the new content or workflow preserves the minimal, responsive goals. Include screenshots if visual sections change.
- Before merging, rerun `npx markdownlint README.md docs/**/*.md` and review the rendered README to ensure layout and palette integrity.

## Agent Notes
- Treat this repo as documentation-first: every pull request should update the README or its supporting docs rather than introducing unrelated scripts.
- When in doubt about visual decisions, defer to the Light Tritanopia palette and the seven-section layout illustrated in `docs/design.md`.
