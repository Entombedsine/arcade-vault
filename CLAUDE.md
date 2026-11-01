# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Arcade Vault: a platform to play games online and compete for the highest score (see `README.md`, written in Spanish). The project follows a spec-driven workflow (`/spec` and `/spec-impl`) using the skills from `Klerith/fernando-skills` (`npx skills@latest add Klerith/fernando-skills`). The repo is still the freshly scaffolded Create Next App (`app/layout.tsx`, `app/page.tsx`); no game, score or backend code exists yet.

## Commands

```bash
npm run dev     # next dev
npm run build   # next build
npm run start   # next start
npm run lint    # eslint (flat config, eslint.config.mjs)
```

There is no test runner configured.

## Next.js version warning

`next` is 16.4.3 with React 19.3.0. It has breaking changes versus older Next.js, so read the relevant guide in `node_modules/next/dist/docs/` (`01-app`, `02-pages`, `03-architecture`) before writing Next.js code, and heed deprecation notices. `AGENTS.md` carries this rule and is re-added by `next dev`; keep it committed.

## Architecture notes

- App Router only (`app/` at the repo root, no `src/`). The path alias `@/*` maps to the repo root.
- `next.config.ts` enables non-default settings that affect how code must be written:
  - `cacheComponents: true` and `partialPrefetching: true`: Cache Components / partial prerendering behavior. Check the docs for the rules on dynamic data and caching before fetching data in components.
  - `experimental.agentFeedback: true`.
  - Tailwind v4 is wired through a Turbopack rule (`@tailwindcss/turbopack` loader on `*.css`) rather than PostCSS, so styling relies on Turbopack (`next dev`/`next build` default).
