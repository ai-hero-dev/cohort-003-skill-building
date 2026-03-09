# Project Memory

## Effect ecosystem dependency management

- When installing new `@effect/*` packages, use `npm install --force` instead of `--legacy-peer-deps`. The `--legacy-peer-deps` flag corrupts the lockfile by removing existing `@effect/*` peer dependencies (e.g., `@effect/rpc`, `@effect/sql`, `@effect/experimental`).
- `@effect/platform-node@0.94.2` has peer deps on `@effect/cluster`, `@effect/rpc`, `@effect/sql` that were previously resolved. `--legacy-peer-deps` removes them.

## Testing patterns

- Tests use `@effect/vitest` with `it.effect()` for Effect-based tests. Import `describe`, `it`, `expect` from `@effect/vitest` and `vi`, `beforeEach` from `vitest`.
- DB tests use PGlite with `drizzle-kit/api` `pushSchema` for schema setup.
