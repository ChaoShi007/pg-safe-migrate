# pg-safe-migrate

Open-source CLI & GitHub Action to lint PostgreSQL migrations for table-locking hazards and verify rollback safety against ephemeral Postgres containers.

## Core Scope (v1.0)
- **AST Linter (`/linter`)**: Detects lock-heavy DDL operations (e.g., `ADD COLUMN` with volatile defaults, non-concurrent `CREATE INDEX`, `ALTER COLUMN TYPE`).
- **Dry-Run & Rollback Runner (`/runner`)**: Spins up an ephemeral Postgres instance via Docker, runs `up.sql` -> `down.sql` -> `up.sql` idempotency checks.
- **GitHub Action (`/action`)**: Posts structured lock-risk summaries directly on PRs.
