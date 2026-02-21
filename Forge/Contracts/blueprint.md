# Blueprint: Just a Timer

## Product Intent
- Simple timer app with an animated character face that reacts to time passing.
- For everyday users (cooking, workouts, studying) seeking charming, personality-driven timers.
- Core goal: Make timers delightful instead of clinical.

## Core Invariants
- Timer always runs accurately and persists state across app restarts.
- Animated face must clearly show time progression (calm → anxious → celebratory).
- One-tap presets (5min, 15min, 1hr) must always be visible and functional.
- Completion triggers sound and haptic feedback without fail.
- UI remains minimal; no cluttered settings or secondary features.

## MVP Scope
### In Scope (Phase 1 & 2)
- Timer countdown with 1-second accuracy.
- Animated face with three emotional states tied to time remaining.
- Quick preset buttons (5, 15, 60 minutes).
- Sound notification on completion.
- Haptic feedback on completion.
- Minimal, focused UI.

### Not in Scope
- Custom timer presets or timer history.
- Multiple simultaneous timers.
- Background operation / push notifications.
- Settings panel or theme customization.
- Social sharing or multiplayer features.

## Layer Boundaries
- Routes: Timer input, preset selection, completion acknowledgment.
- Services: Timer state machine, animation loop, notification triggers.
- Repositories: Local state persistence (device storage).
- UI: Single screen with face animation, preset buttons, time display.

## Deployment
- Web app (React/TypeScript) running locally in development.
- Stateless countdown logic; persistent state in browser localStorage.
- Docker optional; primary target is modern browser (Chrome, Safari, Firefox).