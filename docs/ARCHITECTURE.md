# Architecture — Voyager

## Intent

Voyager is a Next.js travel brand experience covering destinations, vacation rentals, travel styles, technology story, testimonials, FAQ, and request/contact flows, plus a dashboard shell.

## System shape

App Router pages under `src/app`. Prefer server components for content pages; keep interactive islands client-side.

## Stack decisions

- Next.js 15
- React 19
- TypeScript
- Tailwind CSS
- Framer Motion
- pnpm

## Boundaries

- Secrets stay in environment variables / secret managers — never in git.
- Client bundles only receive public configuration (`NEXT_PUBLIC_*` / `VITE_*`).
- Tenant or role checks belong in middleware / server layers, not UI-only gates.
- Heavy or long-running work should not run inside short-lived serverless handlers unless designed for it.

## Quality bar

- Prefer typed contracts at API and domain boundaries.
- Ship a vertical slice (auth → persisted outcome) before a broad feature surface.
- Document trade-offs in PRs when changing data models or auth.

