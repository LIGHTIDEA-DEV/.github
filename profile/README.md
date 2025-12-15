# Welcome to LIGHTIDEA-DEV

## About
This organization hosts all source code for the LIGHTIDEA platform.

## Branch Strategy
We follow a structured Git workflow:

- `main` – Production-ready code (protected)
- `dev` – Integration branch
- `feature/*` – Feature development
- `hotfix/*` – Emergency production fixes

## Workflow Rules
- No direct pushes to `main`
- All changes go through Pull Requests
- CI checks must pass before merge
- Code reviews are mandatory

## CI/CD
- Jenkins handles builds, tests, and deployments
- Docker images are built and tagged automatically
