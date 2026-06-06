# nextjs-i18n-seo-skill

A reusable agent skill for Next.js App Router SEO and internationalization workflows.

## What This Repo Is

This repository is a skill package, not a Next.js application.

It is designed to be usable by any agent system that supports a `SKILL.md`-style skill format.

## Files

- `README.md`: repository overview
- `SKILL.md`: trigger metadata and workflow guidance
- `agents/openai.yaml`: UI metadata for skill pickers
- `LICENSE`: repository license

## Scope

This published version is intentionally generic. It covers:

- localized routing
- Metadata API
- canonical URLs
- hreflang alternates
- sitemap and robots
- Open Graph and Twitter cards
- `opengraph-image.tsx` and `twitter-image.tsx`
- JSON-LD

It does not hardcode project-specific file paths, helper names, or locale models.

## Suggested Repo Name

`nextjs-i18n-seo-skill`

This name makes it clear that the repository contains a reusable skill while staying neutral about which agent runtime uses it.

## Publish

This directory is already laid out to work as a standalone repository root:

```text
.
  README.md
  SKILL.md
  LICENSE
  agents/openai.yaml
```

You can `cd` into this directory and run `git init`, or copy these files into a new repository root.

## Pairing Model

This skill works best when a project also has a local overlay skill that captures repo-specific helpers and conventions.
