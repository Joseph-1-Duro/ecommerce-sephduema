# Sephduema ecommerce

A pnpm workspace managed with Turborepo. Both applications currently show their standard starter screens.

## Applications

| App                | Framework                        | Styling                   | Development URL       |
| ------------------ | -------------------------------- | ------------------------- | --------------------- |
| `apps/admin-panel` | React with Vite and React Router | Plain CSS                 | http://localhost:5173 |
| `apps/storefront`  | Next.js App Router               | Plain CSS and CSS Modules | http://localhost:3000 |

Both applications use strict TypeScript.

## Development

Use Node.js 24 or later and the pnpm version pinned in the root `package.json`.

```sh
pnpm install
pnpm dev
```

To run one application:

```sh
pnpm --filter admin-panel dev
pnpm --filter storefront dev
```

## Checks and builds

```sh
pnpm lint
pnpm check-types
pnpm build
```

Shared packages live in `packages/`. Follow [AGENTS.md](AGENTS.md) and [GIT_CONVENTIONS.md](GIT_CONVENTIONS.md) when making changes.
