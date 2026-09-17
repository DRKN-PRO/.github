# DRKN

> AI-native trading intelligence infrastructure

![AI infrastructure](https://img.shields.io/badge/AI-infrastructure-8B5CF6?style=flat-square)
![Financial systems](https://img.shields.io/badge/financial-systems-0F172A?style=flat-square)
![Security](https://img.shields.io/badge/security-fail--closed-10B981?style=flat-square)
![Delivery](https://img.shields.io/badge/delivery-immutable-111827?style=flat-square)

**Logo placeholder:** dark navy / electric violet / signal green

## About DRKN

DRKN is an AI-powered crypto intelligence and trading infrastructure platform.
It combines account analysis, an operator copilot, automation, market-data
processing, content delivery, and financial execution controls behind explicit
service and artifact contracts.

The platform is organized as four independently versioned repositories. Each
repository has one source-of-truth responsibility and communicates across
boundaries through versioned APIs, snapshots, and release manifests.

## Architecture

```mermaid
flowchart TB
    U[User] --> W[DRKN Web]
    W -->|OpenAPI contract| A[Backend API]
    A --> Q[Workers and automation]
    Q --> S[Signal Router]
    Q --> M[Market data and exchanges]
    A --> D[(PostgreSQL)]
    Q --> D
    C[Content authority] -->|Snapshot V2| W
    C -->|Revision-checked commands| A
    I[Infrastructure and release control] -.-> W
    I -.-> A
    I -.-> C

    classDef edge fill:#111827,stroke:#8b5cf6,color:#f8fafc
    classDef core fill:#0f172a,stroke:#10b981,color:#f8fafc
    classDef data fill:#020617,stroke:#64748b,color:#f8fafc
    class U,W,C edge
    class A,Q,S,M,I core
    class D data
```

Release flow:

```mermaid
flowchart LR
    B[Backend image] --> R[Multi-repository release manifest]
    W[Web image] --> R
    C[Content image] --> R
    R --> V[Compatibility, provenance, and attestation]
    V --> P[Immutable production release]
    P --> O[Health and observability]
```

## Core products

| Product | Responsibility |
|---|---|
| Account Lab | Explainable account scoring, risk pillars, and findings |
| Copilot | AI-assisted market and account intelligence |
| Automations | Deterministic event, queue, and workflow execution |
| Signal Router | Idempotent signal routing and delivery controls |
| Content platform | Versioned editorial authority, Snapshot V2, and publishing pipelines |

## Repository map

| Repository | Source authority | Runtime output |
|---|---|---|
| `drkn-web` | React user experience and public content presentation | Immutable static web image |
| `drkn-backend` | FastAPI, financial domain, workers, OpenAPI, and migrations | API and worker image |
| `drkn-content` | Editorial state, publication policy, and media workflows | Content authority and worker image |
| `drkn-infra` | Release contracts, Docker orchestration, observability, and rollback | Signed multi-repository release |

## Technology stack

| Layer | Technologies |
|---|---|
| Web | React, TypeScript, Vite, Tailwind CSS, nginx |
| Services | Python 3.13, FastAPI, Pydantic, background workers |
| Data | PostgreSQL, Redis, immutable content snapshots |
| Delivery | Docker, Compose, GitHub Actions, GHCR |
| Operations | Prometheus, Grafana, Alertmanager, structured logs |

## Engineering principles

- Explicit ownership: one authoritative repository for each responsibility.
- Contracts over source coupling: OpenAPI, Snapshot V2, and artifact manifests.
- Immutable delivery: releases and images are addressed by digest, not branch name.
- Fail-closed financial safety: deployment checks never bypass execution guards.
- Reproducible runtime: lock-based builds with no production source mounts.
- Observable systems: release identity, health, logs, and metrics are operational contracts.

## Security philosophy

DRKN treats financial execution, credentials, release provenance, and content
publication as distinct trust boundaries. Secrets are injected only at
runtime. CI uses mocked or dry-run integrations and never places trades, sends
user-visible messages, or publishes external content.

Please use GitHub private vulnerability reporting from the affected
repository's **Security** tab. Do not disclose suspected vulnerabilities in a
public issue.

## Contribution philosophy

Changes should be small, testable, and owned by the repository that controls
the behavior. Contract changes require compatibility evidence. Production
behavior, database authority, financial safeguards, and publishing side
effects must remain explicit in every pull request.

See the organization contribution and security policies before opening a
change. Public contribution intake is intentionally limited while operational
and disclosure workflows mature.

---

**Website:** not published · **Social channels:** not published
