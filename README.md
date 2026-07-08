# FiveMesh Docs

Mintlify documentation for FiveMesh.

## Local commands

Install the Mintlify CLI globally if needed:

```bash
npm i -g mint
```

Run a local preview:

```bash
npm run dev
```

Validate the docs:

```bash
npm run validate
npm run broken-links
```

## Structure

- `docs.json` controls navigation, branding, navbar links and footer links.
- `index.mdx` and `quickstart.mdx` introduce the docs.
- `dashboard/` documents workspace, organization and billing flows.
- `cdn/` documents FiveMesh CDN setup and operations.
- `cache/` documents FiveMesh Cache setup and operations.
- `voice/` documents FiveMesh Voice setup and operations.
- `account/` documents servers and service API keys.
- `reference/` contains troubleshooting material.

## Writing rules

Read `AGENTS.md` before changing docs. Keep content customer-facing, operational and specific to FiveMesh workflows.
