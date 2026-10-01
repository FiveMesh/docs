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
- `dashboard/` documents workspace, organization, billing and Agent flows.
- `cdn/` documents FiveMesh CDN setup and operations.
- `cache/` documents FiveMesh Cache setup and operations.
- `voice/` documents FiveMesh Voice setup and operations.
- `logs/` documents event ingestion, Explorer and staff viewer setup.
- `account/` documents servers, API keys and personal settings.
- `api-reference/` documents public identity, CDN and Logs endpoints.
- `sdk/` documents FiveM SDK installation, CDN helpers and Logs exports.
- `reference/` contains the V2 upgrade checklist and troubleshooting.

Use the current `../app`, `../api-worker`, `../logs-worker` and `../sdk` implementation to verify behavior. The docs theme follows the `../web` marketing palette. Service credentials in examples are placeholders; validation must not mutate customer resources.

## Writing rules

Read `AGENTS.md` before changing docs. Keep content customer-facing, operational and specific to FiveMesh workflows.
