# Schema Contract: Just a Timer

## Conventions

- **Naming**: snake_case for tables and columns
- **IDs**: UUID primary keys (uuid type) for all tables
- **Timestamps**: created_at and updated_at (timestamptz) on all tables with history tracking
- **Soft deletes**: deleted_at column where applicable
- **Indexing**: Indexes on frequently queried foreign keys and soft delete filters

## Tables

### presets
Timer preset options available to users.
```sql
CREATE TABLE presets (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(50) NOT NULL,
  duration_seconds INTEGER NOT NULL,
  display_order INTEGER NOT NULL,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW(),
  UNIQUE(name),
  CHECK (duration_seconds > 0)
);
```

### timer_sessions
Records of active and completed timer runs.
```sql
CREATE TABLE timer_sessions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  duration_seconds INTEGER NOT NULL,
  preset_id UUID REFERENCES presets(id) ON DELETE SET NULL,
  started_at TIMESTAMPTZ NOT NULL,
  completed_at TIMESTAMPTZ,
  paused_at TIMESTAMPTZ,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW(),
  CHECK (duration_seconds > 0)
);

CREATE INDEX idx_timer_sessions_completed_at ON timer_sessions(completed_at);
CREATE INDEX idx_timer_sessions_started_at ON timer_sessions(started_at);
```

### animation_states
Stores the animation state progression (calm → anxious → celebratory) mapped to elapsed time.
```sql
CREATE TABLE animation_states (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  state_name VARCHAR(50) NOT NULL,
  threshold_percent INTEGER NOT NULL,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW(),
  UNIQUE(state_name),
  CHECK (threshold_percent >= 0 AND threshold_percent <= 100)
);
```

## Minimal Scope

This schema supports:
- Preset timer management (5min, 15min, 1hr quick access)
- Timer session tracking (start, pause, completion)
- Animation state progression tied to elapsed time
- No user accounts required (stateless MVP)