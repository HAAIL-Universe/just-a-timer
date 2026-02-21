# UI Contract: Just a Timer

## 1. App Shell & Layout

**Structure:**
- Single-screen full-viewport layout with portrait-first responsive design
- Centered, vertically stacked composition: animated character → timer display → controls
- Safe area padding for notches/bottom bars
- No bottom navigation; all controls inline

**Navigation:**
- None required (single screen)
- Settings accessible via minimal gear icon or long-press gesture

---

## 2. Screens/Views

### Main Timer Screen
**Layout:**
- Top: Animated face character (responsive SVG, ~40% of viewport height)
- Middle: Large timer display (HH:MM:SS or MM:SS format)
- Bottom: Control buttons (Start, Pause, Reset) + Quick Preset buttons (5m, 15m, 1hr)

**Key Interactions:**
- Tap Start/Pause to begin/pause countdown
- Tap Reset to clear and return to 00:00
- Tap preset buttons for instant setup (dismisses any current input)
- Long-press on timer display to manually enter time
- Character reacts dynamically: calm at >50% time, mildly anxious at 25–50%, panicked at <25%, celebratory on completion

**Completion State:**
- Overlay modal or screen flip showing celebration animation
- Sound + haptic feedback triggered
- Dismiss button to reset and return to input state

---

## 3. Component List

**Reusable Components:**
- `AnimatedFace` — SVG-based character with expression states (calm, anxious, panicked, celebrating)
- `TimerDisplay` — Large mono/serif numeric display, supports MM:SS and HH:MM:SS
- `ControlButton` — Primary action button (Start, Pause, Reset) with active/inactive states
- `PresetButton` — Quick-tap preset (5m, 15m, 1hr)
- `TimeInput` — Manual text input field for custom duration (appears on long-press)
- `CompletionOverlay` — Full-screen celebration modal with dismiss button

---

## 4. Visual Style

**Color Palette:**
- Background: Soft off-white or light gray (#F5F5F5)
- Primary action (Start): Warm green (#4CAF50) or vibrant teal
- Secondary action (Pause): Neutral gray (#888888)
- Accent (Presets): Light blue or playful purple
- Character face: Warm skin tone, expressive eyes/mouth
- Text: Dark gray/charcoal (#333333)

**Typography:**
- Timer display: Large, bold, monospace (e.g., `Courier New`, `JetBrains Mono`) at 72–120px
- Labels/buttons: Clean sans-serif (e.g., `Inter`, `Segoe UI`) at 16–18px
- Minimal hierarchy; prioritize readability

**Animations:**
- Character expression transitions: 300–500ms easing (ease-in-out)
- Button presses: 150ms scale feedback
- Completion celebration: 1–2s loop (confetti, spin, bounce)

---

## 5. Key User Flows

**Flow 1: Quick Timer (Preset)**
- User opens app → Taps "15m" preset → Timer starts automatically → Character animates through states → Completion celebration

**Flow 2: Custom Duration (Manual Input)**
- User opens app → Long-presses timer display → Types duration (e.g., "10:30") → Taps Start → Waits and watches character react → Hits completion

**Flow 3: Pause & Resume**
- User starts timer → Taps Pause mid-countdown → Character freezes in current mood → Taps Start to resume → Character resumes animation through time states