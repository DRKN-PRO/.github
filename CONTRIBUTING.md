# Contributing to DRKN

Thank you for improving DRKN. Changes must preserve explicit repository
ownership, versioned contracts, and fail-closed operational safety.

## Before opening a change

1. Choose the repository that owns the behavior.
2. Open or reference an issue for changes that affect contracts or operations.
3. Never include credentials, private account data, production exports, or
   real financial instructions in an issue, commit, fixture, or log.
4. Keep changes focused. Do not combine product behavior, dependency upgrades,
   and deployment changes unless they are inseparable.

## Development workflow

1. Branch from the current default branch.
2. Follow the repository README and `AGENTS.md` boundaries.
3. Add or update tests for changed behavior.
4. Run the repository's documented quality gate.
5. Complete every section of the pull-request template.
6. Request review from the responsible owner.

## Contract changes

Changes to OpenAPI, Snapshot V2, artifact manifests, worker inventories,
database schema requirements, or release composition must include:

- the old and new contract identities;
- compatibility results for every consumer;
- migration and rollback implications;
- updated fixtures and deterministic tests.

## Safety boundaries

Development and CI must not place trades, cancel orders, send user-visible
Telegram messages, publish CMS content, upload videos, or use production
credentials. Use mocks, dry-run modes, and disposable state.

## Commit and review quality

Use concise, imperative commits with a clear scope, such as `refactor:`,
`fix:`, `test:`, `docs:`, `docker:`, or `infra:`. Review focuses on correctness,
ownership, security, compatibility, observability, and rollback—not only style.
