---
name: stock-pet-development
description: Develops and tests the Stock Pet Tauri application, including manifest-driven PNG animation playback, stock-state mapping, settings, transparent desktop windows, and mock stock data. Use for all implementation, refactoring, testing, and review work in this workspace.
---

# Stock Pet Development Skill

## Required reading order

1. `/AGENTS.md`
2. `/docs/01_PRODUCT_REQUIREMENTS.md`
3. `/docs/02_TECH_ARCHITECTURE.md`
4. `/docs/03_ANIMATION_ASSET_SPEC.md`
5. `/docs/04_DEVELOPMENT_PLAN.md`
6. `/docs/05_TEST_CHECKLIST.md`

## Workflow

1. Identify the current phase.
2. Inspect only files needed for that phase.
3. Produce an implementation plan with:
   - files to create or modify
   - design decisions
   - risks
   - tests
   - explicit out-of-scope items
4. Wait for user approval before implementation when the change is larger than a minor fix.
5. Implement the smallest coherent slice.
6. Run relevant tests and builds.
7. Verify the UI when applicable.
8. Summarize:
   - changed files
   - commands run
   - results
   - remaining issues
   - next recommended task

## Non-negotiable animation rules

- Never hardcode frame counts.
- Never infer frame order from directory sorting when a manifest is present.
- Never rename, delete, crop, recolor, resize, or overwrite user graphics unless explicitly asked.
- Treat `manifest.json` as the animation source of truth.
- Support zero, one, and multiple frame cases safely.
- Clean up timers/listeners when components unmount.
- Keep animation playback independent from stock-provider implementation.

## Safety rules

- Work only inside the project workspace.
- Do not run recursive deletion commands.
- Do not access unrelated user directories.
- Do not expose or commit secrets.
- Do not connect a real stock API before Phase 5.
- Do not add trading or order features.
