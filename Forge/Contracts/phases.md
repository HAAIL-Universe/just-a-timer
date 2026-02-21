## Phases Contract – Just a Timer

### Phase 0: Backend Scaffold
**Objective:** Set up minimal backend infrastructure with timer state management and API endpoints.

**Deliverables:**
- Express.js server scaffold with environment configuration
- SQLite database with timer history schema
- Database migrations for tables: timers, preset_configs
- REST API endpoints: POST /api/timers (start), PUT /api/timers/:id (update state), GET /api/timers/:id (fetch status)
- Boot script and dev server startup
- Error handling and request validation middleware

**Schema coverage:**
- timers (id, duration_ms, elapsed_ms, status, created_at, completed_at)
- preset_configs (id, label, duration_ms)

**Exit criteria:**
- Server starts cleanly and listens on configured port
- Database initializes with schema on first run
- All API endpoints respond with correct JSON payloads
- Timer state persists across requests
- Dev environment ready for frontend integration

---

### Phase 1: Frontend & Ship
**Objective:** Build complete UI with animated timer face, presets, and API integration; deploy and document.

**Deliverables:**
- React app with home page containing timer display and preset buttons
- Animated face component (SVG or Canvas) that reacts to time passing (calm → anxious → celebratory)
- Start/pause/stop/reset controls
- Quick preset buttons (5min, 15min, 1hr) with one-tap initiation
- Real-time countdown display with MM:SS format
- Sound and haptic feedback on timer completion
- API integration layer connecting UI to backend endpoints
- Responsive design for mobile and desktop
- README.md with setup, usage, and deployment instructions
- Production build and deployment to hosting platform

**Schema coverage:**
- N/A (frontend only; uses Phase 0 API contracts)

**Exit criteria:**
- Timer starts, counts down, and completes successfully from UI
- Animated face visibly changes emotional state during countdown
- Presets trigger timers without manual input
- Sound and haptics fire on completion
- API calls succeed and update timer state in backend
- App runs in production environment
- README contains complete build and run instructions
- All UI is responsive and functional on mobile devices