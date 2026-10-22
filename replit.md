# All In One General Store

A kirana storefront for customers in Vatva, Ahmedabad, with a local-only owner demo for managing products and orders.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/general-store run dev` — run the storefront preview
- `pnpm --filter @workspace/general-store run typecheck` — typecheck the storefront
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/general-store/src/` — storefront and owner demo UI
- `artifacts/general-store/imported-source/` — user-provided starter code and setup notes for reference
- `lib/api-spec/openapi.yaml` — shared API contract, not currently used by the storefront

## Architecture decisions

- The first preview keeps demo products, cart, language, and orders in browser localStorage; this is not shared across customers or devices.
- Owner tools are demo-only and do not provide real authentication.

## Product

- Customers can browse products, add items to a cart, and submit a demo order.
- The owner demo can manage products and order statuses.
- The starter includes English, Hindi, and Gujarati translations.

## User preferences

_No additional preferences recorded._

## Gotchas

- Do not collect real customer details or use the local demo for live orders. Real authentication, shared storage, payment, privacy, and server-side order-hour enforcement need to be set up before launch.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
