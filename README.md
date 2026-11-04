# SpeedMind AI Turbo

SpeedMind AI Turbo is an AI model gateway and routing service. It provides a unified API layer for selecting model tiers, handling provider failures, caching eligible responses, and tracking basic usage metrics.

> Current documented milestone: **v0.5.0 — free trial edition**. This repository records the project status and roadmap. The executable source archive is not included in this commit.

## Current product direction

- Unified gateway for multiple model providers.
- FAST / SMART / DEEP routing, with AUTO selection.
- Optional fallback models for transient provider failures.
- Optional response caching and concurrency controls.
- Per-user accounts and API keys.
- Usage limits for free trials; no payments, subscriptions, or automatic charges.

## v0.5.0 free-trial scope

- User registration and login.
- Password hashing.
- Per-user API key creation, listing, and revocation.
- SQLite persistence.
- Usage counters and free-trial quota enforcement.
- Existing model-routing functionality retained.

Reported default trial policy:
- 100 requests per account per month.
- Up to 5 active API keys per account.
- Monthly quota reset.
- Each parallel task consumes one request.

These values should be checked against the deployed configuration before public launch.

## Development and verification status

The v0.5.0 development handoff reported **40 automated tests passing**. This is a recorded project status, not a claim that CI has run from this repository. Real provider credentials, live model calls, Docker image builds, and public deployment were not verified as part of that handoff.

See:
- [Project status](docs/PROJECT_STATUS.md)
- [Roadmap](docs/ROADMAP.md)

## Free-trial policy

The platform does not charge trial users at this stage. Third-party model providers may still charge the platform operator for API usage. Keep provider credentials server-side and never commit secrets, production environment files, or user API keys.
