---
name: nextjs-i18n-seo
description: Use when building or reviewing Next.js App Router SEO and internationalization: localized routes, Metadata API, canonical URLs, hreflang alternates, sitemap, robots, Open Graph, Twitter cards, opengraph-image or twitter-image routes, and JSON-LD.
---

# Next.js i18n SEO

Use this skill for public-discovery work in a Next.js App Router codebase: metadata, canonical URLs, hreflang, localized routing, sitemap, robots, JSON-LD, Open Graph, Twitter cards, and social image routes.

## First Checks

1. Read the local Next.js docs before changing Next APIs.
   - Search under `node_modules/next/dist/docs/` for `metadata`, `generateMetadata`, `sitemap`, `robots`, `opengraph-image`, and `twitter-image`.
   - Prefer local docs over memory for Metadata API shapes and file conventions.
2. Inspect the nearest existing route pattern before adding a new one.
3. Reuse project helpers for locale parsing, URL building, SEO metadata, and JSON-LD when they already exist.

## Route Structure

Common App Router patterns for localized public pages:

- A default-locale route plus locale-prefixed wrappers.
- A single route tree where locale is always part of params.
- Shared metadata builders reused by multiple route entries.

Prefer the project's existing pattern. Do not introduce a new locale-routing style if the codebase already has one.

## Metadata Checklist

When adding or reviewing page metadata, check:

- `title` and `description` are localized and match the page intent.
- `alternates.canonical` points at the preferred page URL.
- `alternates.languages` covers translated variants with valid hreflang URLs.
- `openGraph` includes `type`, `title`, `description`, `url`, and `images` when appropriate.
- `twitter` has an explicit `card`, `title`, `description`, and image when appropriate.
- Article or content detail pages include publication and modification times when the project already models them.
- Metadata is built from stable route helpers rather than hand-assembled strings when possible.

## i18n Routing

For locale-aware routes:

- Convert route params into a validated locale as early as possible.
- Reject invalid locale params consistently with the surrounding app pattern.
- Build locale switcher targets from a single source of truth.
- Prefer shared path builders for canonical URLs, alternates, and internal navigation.
- When some content is untranslated, generate alternates only for locales that actually exist.

## Sitemap + Robots

- `app/sitemap.ts` should emit absolute URLs.
- Include localized alternates in sitemap rows when the project supports them.
- Use content timestamps for `lastModified` when available.
- Keep priorities and change frequencies conservative and consistent.
- `app/robots.ts` should point to the sitemap and exclude non-public areas such as admin surfaces.
- If publishing content affects discovery surfaces, update revalidation paths for sitemap and affected public routes.

## Open Graph + Twitter

- Prefer route-based social images with `opengraph-image.tsx` and `twitter-image.tsx` when the codebase uses them.
- Reuse shared image renderers or shared metadata helpers where available.
- Avoid mixing unrelated fallback images across sections unless that is already the established project behavior.
- Keep localized OG locale values aligned with the route locale.

## JSON-LD

- Render JSON-LD with a dedicated component or shared helper rather than inline string assembly throughout the app.
- Use schema builders when multiple pages share the same shape.
- Keep natural-language JSON-LD fields localized.
- Prefer `@graph` when combining page entity, breadcrumb, FAQ, site, or organization data.
- Only emit JSON-LD when the page has enough stable data to form a valid entity.

## Implementation Pattern

When the project has shared helpers, prefer this order:

1. Route/path helpers
2. Locale helpers
3. Shared metadata builders
4. Shared JSON-LD builders
5. Shared social-image renderers

If those abstractions do not exist, add only the smallest reusable helper that clearly reduces duplication.

## Testing

Add focused tests around the changed discovery surface:

- Route metadata or `generateMetadata`
- Locale routing and alternate URL generation
- `app/sitemap.ts`
- `app/robots.ts`
- JSON-LD rendering
- `opengraph-image` and `twitter-image` routes when changed

Run the smallest relevant test slice first, then broaden only if shared helpers changed.
