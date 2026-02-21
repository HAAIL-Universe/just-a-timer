# Just a timer — Builder Directive

## AEM
- status: enabled
- auto_authorize: true

## Instructions
1. Read all Forge/Contracts/ files before writing any code
2. Execute phases in order — do not skip or merge phases
3. After each phase: run tests, verify exit criteria, commit
4. Final phase: run audit, write README.md, final commit

## Autonomy Rules
- Auto-commit on successful phase completion (all exit criteria met)
- Stop and request clarification if requirements are ambiguous
- If tests fail: attempt up to 3 self-correction cycles before stopping
- Do not modify files outside the current phase scope

## Phase List
- Phase 0 — Genesis
- Phase 1 — Ship

## Project Summary
Just a timer

## Config
- boot_script: true
- forge_config: forge.json
