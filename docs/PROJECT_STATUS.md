# SpeedMind AI Turbo — Project Status

**Milestone:** v0.5.0  
**Edition:** Free trial (no payment integration)  
**Status:** Development handoff; not yet verified as a public production deployment.

## Product purpose

SpeedMind AI Turbo is an AI gateway / model router, not a new foundation model. It aims to expose one service interface for multiple model providers and route requests across FAST, SMART, and DEEP model tiers.

## Milestones

### v0.4.0 — Gateway foundation

The previous handoff reported:
- FAST / SMART / DEEP and AUTO routing.
- Adaptive promotion from FAST to SMART based on recent errors or latency.
- Optional fallback model IDs for transient provider failures.
- Optional response caching and concurrency controls.
- Protected metrics endpoint and a basic dashboard.
- Process-local metrics, including request counts, provider errors, fallback attempts, cache hits/misses, route counts, and provider latency percentiles.

Known limitation: process-local metrics reset on restart and are not aggregated across multiple workers.

### v0.5.0 — Account and free-trial foundation

The previous handoff reported these features:
- User registration and login.
- Password hashing.
- User-specific API keys: create, list, revoke.
- SQLite persistence.
- Usage counters and free-trial quota enforcement.
- Existing model routing retained.

Reported test result: **40 automated tests passed**.

## Trial policy (reported defaults)

| Item | Default |
|---|---:|
| Free requests | 100 per account per month |
| Active API keys | Up to 5 per account |
| Quota reset | Monthly |
| Parallel task accounting | Each task consumes one request |
| Payment / subscription | Not enabled |

Confirm the actual environment configuration before inviting external users. Trial usage is free to end users, but upstream model-provider API calls may incur costs for the operator.

## Verification boundaries

The v0.5.0 handoff reported 40 passing tests. The following were not confirmed:
- Live calls to real model providers.
- Actual provider latency and cost measurements.
- Docker image build and container runtime.
- Public deployment, HTTPS, production database backups, or load testing.
- A complete end-user web registration/dashboard interface.

Do not describe the service as production-ready until these checks are completed.

## Security checklist before public beta

- Store only password hashes; use a modern password-hashing algorithm.
- Store API keys hashed where feasible; show plaintext only once at creation.
- Keep provider secrets in server-side environment variables or a secret manager.
- Enforce per-user authentication, quotas, and rate limits on every protected route.
- Configure HTTPS, CORS, secure cookies/token expiry, and request-size limits.
- Back up SQLite or migrate to a managed database before multi-instance deployment.
- Add audit logs and key-rotation/revocation procedures.
