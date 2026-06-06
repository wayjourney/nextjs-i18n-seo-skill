# nextjs-i18n-seo-skill

A reusable agent skill for Next.js App Router SEO and internationalization workflows.

## What This Repo Is

This repository is a skill package, not a Next.js application.

It is designed to be usable by any agent system that supports a `SKILL.md`-style skill format.

## What It Helps With

- localized route metadata
- canonical URLs
- hreflang alternates
- `app/sitemap.ts`
- `app/robots.ts`
- Open Graph and Twitter cards
- `opengraph-image.tsx` and `twitter-image.tsx`
- JSON-LD
- locale-aware SEO review checklists

## Files

- `README.md`: repository overview
- `SKILL.md`: trigger metadata and workflow guidance
- `agents/openai.yaml`: UI metadata for skill pickers
- `LICENSE`: repository license

## Suggested Repo Name

`nextjs-i18n-seo-skill`

This name makes it clear that the repository contains a reusable skill while staying neutral about which agent runtime uses it.

## Install Shape

Use this repository as a skill root:

```text
nextjs-i18n-seo-skill/
  README.md
  SKILL.md
  LICENSE
  agents/openai.yaml
```

Agents that support `SKILL.md`-style packages can load this repository directly or copy these files into a larger skills collection.

## Example Prompt

```text
Use $nextjs-i18n-seo to update this Next.js route's metadata, alternates, sitemap, and JSON-LD.
```

## Scope

This published version is intentionally generic.

It does not hardcode project-specific file paths, helper names, brand names, locale models, or routing conventions beyond common Next.js App Router patterns.

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

## Suggested GitHub Description

`Reusable agent skill for Next.js App Router i18n, metadata, sitemap, Open Graph, and JSON-LD workflows.`

## Suggested Topics

- `agent-skill`
- `nextjs`
- `i18n`
- `seo`
- `metadata`
- `sitemap`
- `json-ld`
