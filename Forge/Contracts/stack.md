# Just a timer — Technology Stack

## Backend
- **Stack:** Python 3.12+ / FastAPI

## Database
- **Engine:** PostgreSQL

## Auth
- **Method:** JWT bearer tokens

## Frontend
- **Framework:** React + TypeScript

## Testing
- **Framework:** pytest (backend), Vitest (frontend)

## Deployment
- **Platform:** Docker Compose
- **Scale:** <100 concurrent users

## Environment Variables

| Name | Description | Required |
|------|-------------|----------|
| DATABASE_URL | Database connection string | Yes |
| JWT_SECRET | Secret key for token signing | Yes |
| CORS_ORIGINS | Allowed CORS origins | Yes |

## forge.json

```json
{
  "project_name": "Just a timer",
  "backend": {
    "language": "python",
    "entry_module": "app.main",
    "test_framework": "pytest",
    "test_command": "pytest -x",
    "dependency_file": "requirements.txt",
    "venv_path": ".venv"
  },
  "frontend": {
    "enabled": true,
    "dir": "web",
    "build_cmd": "npm run build",
    "test_cmd": "npm test"
  }
}
```
