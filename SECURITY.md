# Security policy

## Reporting a vulnerability

Do not open a public issue for a suspected vulnerability. Use GitHub private
vulnerability reporting from the affected repository's **Security** tab.

Include only the information needed to reproduce and assess the issue:

- affected repository and commit or release;
- impact and prerequisites;
- minimal reproduction steps;
- whether credentials, financial execution, or external publication may be involved;
- suggested mitigation, if known.

Do not include live credentials, private keys, customer data, account exports,
or unredacted production logs. Maintainers will coordinate disclosure after a
fix and operational mitigation are available.

## Security boundaries

- Secrets are runtime-injected and never committed or built into images.
- Financial tests are side-effect-free and cannot place or alter orders.
- Telegram, CMS, video, and YouTube tests use mocks or dry-run transports.
- Production artifacts are immutable and validated by digest and provenance.
- PostgreSQL migrations are owned exclusively by `drkn-backend`.
- Release composition, preflight, activation, and rollback are owned by
  `drkn-infra`.

## Supported versions

Security fixes are applied to the currently certified production release and
the default branches of affected repositories. Historical artifacts remain
immutable and are not patched in place.
