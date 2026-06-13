# FiveMesh Docs Agent Guide

## Project context

This repository is the Mintlify documentation site for FiveMesh.

FiveMesh is a cloud infrastructure platform for FiveM servers, powered by sCloud. It is not a gaming-themed product page and it is not only a CDN. The documentation should explain the operational platform: account setup, workspaces, subscriptions, CDN asset delivery, Cache resource proxying, server registration, organizations and service access.

Use the website repository's `BRANDING.md` and `AGENTS.md` as product context when copy or positioning is unclear.

## Stack

- Mintlify
- MDX pages
- `docs.json` for navigation, branding, links and site settings

Use the local Mintlify skills in `.agents/skills` before changing Mintlify configuration or content. Favor current Mintlify documentation when a component or `docs.json` setting is uncertain.

## Voice and terminology

- Use active voice and second person.
- Keep sentences concise.
- Use sentence case for headings.
- Use **bold** for UI labels, buttons and dashboard tabs.
- Use code formatting for file names, paths, commands, product keys and route-like values.
- Use "workspace" for the active personal or organization context.
- Use "organization" for team-owned workspaces.
- Use "registered server" for a cfx.re server connected under **Account**.
- Use "FiveMesh CDN" for public asset hosting and delivery.
- Use "FiveMesh Cache" for resource download proxying through `fileserver_add` and `adhesive_cdnKey`.

## Content boundaries

- Document customer-facing workflows only.
- Do not mention internal implementation providers, storage buckets, databases, queues or infrastructure vendors unless the product UI exposes them.
- Do not promise unreleased modules. Mention future areas only as "coming later" when the dashboard already labels them that way.
- Do not invent metrics, limits, customer names, SLA terms, API endpoints or domain names.
- If a value must be verified later, add an MDX comment in this form: `{/* TODO: Verify ... */}`.

## Visual and brand direction

- Keep the docs serious, minimal and infrastructure-focused.
- Avoid purple or blue gradients, glassmorphism, neon effects, gaming visuals and hype-heavy copy.
- Use Mintlify components sparingly. Cards should be used for navigation or clearly framed examples, not for every paragraph.

## Workflow

- Read `docs.json` before changing navigation.
- Search existing pages before creating new pages.
- Every MDX page needs `title` and `description` frontmatter.
- Use root-relative internal links without `.mdx`.
- Add new pages to `docs.json`.
- Run `mint broken-links` and `mint validate` when the CLI is available.
- If the Mintlify CLI cannot run locally, explain what failed.
