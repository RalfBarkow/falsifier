# Repository Guidelines

## Project Structure & Module Organization
- `SPEC.md` captures the full Incisive Falsifier charter; review it before adjusting workflows or deliverables.
- Tonel sources reside in `src/`; the primary package is `Falsifier` and should contain only behaviour needed for the agent runtime.
- Shared analysis notes belong in `lepiter/`; keep exploratory drafts and research artefacts there instead of cluttering `src/`.
- Sync updates between `README.md` (public overview) and `SPEC.md` (operational detail) whenever you change scope or responsibilities.

## Build, Test, and Development Commands
- `pharo-ui Pharo.image` — open a development image; load the agent via the Metacello snippet provided in `README.md`.
- `./pharo Pharo.image eval --save "Metacello new baseline: 'Falsifier'; load"` — headless load that persists the image with this baseline.
- `workspace-repo-init falsifier` — (from the Codex dev shell) scaffold a clean checkout under `~/workspace` and automatically whitelist it in the workspace `.gitignore`.

## Coding Style & Naming Conventions
- Follow Pharo idioms: UpperCamelCase classes, lowerCamelCase methods, and protocol tags that describe intent (`critique`, `utilities`, `tests`).
- Document public entry points with short class or method comments referencing the relevant section in `SPEC.md`.
- Keep responsibilities isolated; favour small methods that mirror SPEC “Process” stages to aid review.

## Testing Guidelines
- Place executable examples in a `Falsifier-Tests` package (create it if absent) and commit Tonel files under `src/`.
- Use class names like `FalsifierCritiqueTest` for scenario coverage aligned with the falsification workflow.
- Run SmalltalkCI before publishing: `./pharo Pharo.image smalltalkCI .smalltalk.ston`.

## Commit & Pull Request Guidelines
- Write imperative commit subjects (e.g. `Refine falsification charges`) and reference SPEC sections in the body (`Refs SPEC §Process`).
- Pull requests should outline motivation, SPEC impacts, tests run, and any new Lepiter material added.
- Attach sample falsification outputs or Lepiter links when they help reviewers understand behavioural changes.
