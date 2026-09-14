# Chef K Guest Restaurant

Mobile-first single-page website for Chef K Guest Restaurant, an outdoor dhaba-style dining spot in Gujranwala.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
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

- `artifacts/chef-k-guest-restaurant/src/App.tsx` — page content, navigation, reservation modal, gallery lightbox, and conversion links
- `artifacts/chef-k-guest-restaurant/src/index.css` — restaurant visual system, textures, responsive layout, and motion
- `artifacts/chef-k-guest-restaurant/index.html` — SEO metadata and Restaurant JSON-LD
- `attached_assets/` — owner-provided assets; the current build intentionally does not use stock or generated photography

## Architecture decisions

- The restaurant site is frontend-only; reservation intent is handled through direct phone and WhatsApp actions rather than a database-backed booking flow.
- Image areas use branded CSS fallback panels until the restaurant's own photography is supplied, avoiding stock or generated images that would misrepresent the venue.
- The design uses a warm rustic-modern visual language with semantic sections and in-page anchors to keep the experience fast and conversion-focused on phones.

## Product

Visitors can understand the restaurant's atmosphere, browse menu highlights, explore the venue gallery, read testimonials, get directions, and reserve by phone or WhatsApp.

## User preferences

- Use only the restaurant's own provided photography; do not add stock or generated restaurant images.

## Gotchas

- The web build expects `PORT` and `BASE_PATH` from the managed workflow; for a direct build use `PORT=5000 BASE_PATH=/`.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
