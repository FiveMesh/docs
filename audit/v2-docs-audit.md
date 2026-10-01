# FiveMesh V2 documentation audit

Reviewed on 2026-10-01 against the current local release source. Changes are local only; do not push until publication is intended because Mintlify deploys on push.

## Scope and source of truth

All 47 published MDX pages were reviewed. Navigation contains exactly those 47 pages; each has title and description frontmatter. Two obsolete upload portal pages were removed, with redirects to current CDN workflows. Nine pages were added.

| Area | Source reviewed | Revision |
| --- | --- | --- |
| Dashboard, ownership, roles, billing, service onboarding, Agent and account | `../app/src/components`, `../app/src/server/routes`, `../app/src/shared/subscription-plans.ts`, `../app/src/lib/auth-permissions.ts` | `16c5550` |
| Public identity, CDN and Logs queries | `../api-worker/src/routes`, `../api-worker/src/services` | `a15ddb8` |
| Logs ingestion validation, batching and retries | `../logs-worker/src/index.ts`, `../logs-worker/src/batch-coordinator.ts` | `720d5d1` |
| SDK exports, configuration and automatic logging | `../sdk/src`, release workflow | `1f578a5` |
| In-game Logs viewer and ACE controls | `../fivemesh-logs/README.md`, server resource | `764290c` |
| Marketing palette and typography | `../web/DESIGN.md`, `../web/app/components/marketing/editorial-home.css` | `b580276` |

## Corrections

- Customer account owns resources and subscription; organizations are optional collaboration. Billing remains personal.
- Current sidebar server selection replaces removed all-server Cache and Voice tabs. Dashboard UUIDs and cfx.re join codes are distinguished.
- Server API Keys have fixed CDN upload and Logs read/write permissions. Developer keys support selected actions and CDN path restrictions.
- Cache onboarding documents detected/manual endpoints, managed domains and verified custom domains. Examples use the generated registration URL and current `fileserver_add "."` form.
- Voice configuration includes all generated ConVars and retry provisioning. Removal instructions cover the external server configuration.
- CDN guides cover provisioning, supported slug characters, placeholders, active retention, workspace purge and service deletion/cancellation.
- Logs activation, source administration, plan retention, 10,000-row dashboard exports, automatic integrations, optional staff viewer, ingestion and public query references are documented.
- Dashboard Explorer follows retention; SDK/public API queries are limited to seven days. Pagination preserves original request bounds and filters.
- Accepted Logs responses use HTTP 202; request IDs are in headers and error bodies. Rejected batches and unchanged retries do not add usage.
- Existing EUR overage and observation-period billing details are preserved.
- LB-Scripts credentials stay server-side, the broken Lua formatting call is corrected, and missing custom upload-method selection is included.
- Removed stale release TODOs and unreleased API promises. Release links resolve to SDK v0.1.5 and Logs viewer v0.1.2.
- New Agent, account settings, V2 checklist, SDK Logs, whoami, CDN purge and Logs API pages are included in navigation.
- Maintainer instructions and this report are excluded from publication.

## Validation

| Check | Result |
| --- | --- |
| Mintlify CLI | `4.2.965` |
| `mint validate` | Passed |
| `mint broken-links` | Passed |
| Anchors, redirects, snippets and external links | `mint broken-links --check-anchors --check-redirects --check-snippets --check-external` passed |
| Navigation and page inventory | 47 pages; no missing files, unlisted pages or missing frontmatter |
| Local HTTP page check | All 47 pages returned 200 with the expected page title |
| Lua snippets | All 24 parsed successfully with luaparse |
| JavaScript snippets | Both passed `node --check` |
| JSON snippets | All 12 parsed successfully |
| Browser preview | Overview, Cache guide and identity/query endpoint navigation checked; query playground uses `https://api.fivemesh.io/v1/logs/query` |
| Responsive/theme preview | Dark/light desktop and 390 × 844 mobile override checked; no document horizontal overflow, mobile menu renders correctly; override reset |
| Custom API action styles | Computed background, text and icon colors match the configured warm palette in both themes |
| `git diff --check` | Passed |

Checks validate the documentation, source consistency and rendered examples. No authenticated customer uploads, purges, key rotations, billing actions or service changes were performed. Lua/JavaScript snippets were syntax-checked, not executed against a live FiveM server.

## External navigation links

All 15 final navigation/support/release links returned HTTP 200 at the time of checking. The two former LB product URLs (`lbscripts.com/phone` and `lbscripts.com/tablet`) returned 404 and were replaced with the current official documentation pages.

The Discord public invitation page returned 200. A supplementary Discord invite API check returned 503, so guild membership/invite validity was not independently confirmed through that API. A page status does not exercise sign-in, account permissions or service functionality.

| Destination | Verified link |
| --- | --- |
| Dashboard | https://app.fivemesh.io |
| Billing | https://app.fivemesh.io/billing |
| Marketing | https://fivemesh.io |
| Pricing | https://fivemesh.io/pricing |
| Status | https://status.fivemesh.io |
| Support | https://discord.gg/wBJamWETxr |
| GitHub | https://github.com/FiveMesh |
| X | https://x.com/fivemesh_ |
| SDK release | https://github.com/FiveMesh/sdk/releases/latest |
| Logs viewer release | https://github.com/FiveMesh/fivemesh-logs/releases/latest |
| Origin firewall ranges | https://www.cloudflare.com/ips/ |
| LB Phone | https://docs.lbscripts.com/phone/ |
| LB Tablet | https://docs.lbscripts.com/tablet/ |
| LB Phone installation | https://docs.lbscripts.com/phone/installation/ |
| LB Tablet installation | https://docs.lbscripts.com/tablet/installation/ |

## Application discrepancy to address separately

The current CDN settings UI presents **Rename public URL** and prepares `confirmPublicSlugChange`. However, `app/src/server/routes/cdn.ts` rejects a changed slug after onboarding, and the API client input does not declare that confirmation field. The docs therefore explain that the current service keeps the slug fixed and directs customers to support. Making rename functional requires an application change and a corresponding follow-up docs edit; this audit did not change application code.

## Theme colors

Mintlify configuration follows the current marketing palette and defaults to dark mode while preserving the light/system choices. A small CSS override targets the API action that otherwise uses a hardcoded blue color. Standard semantic warnings, HTTP method badges and syntax highlighting remain visible.

| Token | Before | After |
| --- | --- | --- |
| Primary | `#18181B` | `#20221F` |
| Light accent | `#FAFAFA` | `#EEEEE7` |
| Dark accent | `#18181B` | `#20221F` |
| Light background | Mintlify default | `#F7F6F2` |
| Dark background | Mintlify default | `#121310` |
| API action light: background / text / icon | `#3064E3` / `#FFFFFF` / `#FFFFFF` | `#20221F` / `#F7F6F2` / `#F7F6F2` |
| API action dark: background / text / icon | `#3064E3` / `#FFFFFF` / `#FFFFFF` | `#EEEEE7` / `#121310` / `#121310` |

Mintlify settings and CSS support were checked against [official customization documentation](https://www.mintlify.com/docs/customize/custom-scripts). LB installation instructions were checked against [LB Phone](https://docs.lbscripts.com/phone/installation/) and [LB Tablet](https://docs.lbscripts.com/tablet/installation/).

## Published page inventory

Each entry below was reviewed and returned HTTP 200 in the local preview.

| Page | Title |
| --- | --- |
| `account/api-keys` | API keys |
| `account/servers` | Registered servers |
| `account/settings` | Account settings |
| `api-reference/authentication` | Authentication |
| `api-reference/cache` | FiveMesh Cache API |
| `api-reference/cdn-endpoints/bulk-delete-objects` | Bulk delete objects |
| `api-reference/cdn-endpoints/bulk-upload-objects` | Bulk upload objects |
| `api-reference/cdn-endpoints/create-upload-url` | Create an upload URL |
| `api-reference/cdn-endpoints/delete-object` | Delete one object |
| `api-reference/cdn-endpoints/list-objects` | List objects |
| `api-reference/cdn-endpoints/purge-objects` | Purge CDN objects |
| `api-reference/cdn-endpoints/upload-base64-object` | Upload one Base64 object |
| `api-reference/cdn-endpoints/upload-object` | Upload one object |
| `api-reference/cdn-endpoints/upload-with-url` | Upload with an upload URL |
| `api-reference/cdn` | FiveMesh CDN API |
| `api-reference/introduction` | API reference |
| `api-reference/logs-ingestion` | Ingest log events |
| `api-reference/logs-query` | Query log events |
| `api-reference/logs` | FiveMesh Logs API |
| `api-reference/voice` | FiveMesh Voice API |
| `api-reference/whoami` | Inspect an API key |
| `cache/operations` | Cache operations |
| `cache/setup` | Set up FiveMesh Cache |
| `cdn/object-browser` | CDN object browser |
| `cdn/settings` | CDN settings |
| `cdn/setup` | Set up FiveMesh CDN |
| `dashboard/agent` | FiveMesh Agent |
| `dashboard/billing` | Billing |
| `dashboard/organizations` | Organizations |
| `dashboard/overview` | Dashboard overview |
| `dashboard/workspaces` | Workspaces |
| `index` | FiveMesh documentation |
| `integrations/lb-scripts` | LB-Scripts |
| `logs/operations` | Logs operations |
| `logs/setup` | Set up FiveMesh Logs |
| `quickstart` | Quickstart |
| `reference/troubleshooting` | Troubleshooting |
| `reference/v2-upgrade` | V2 upgrade checklist |
| `sdk/installation` | Installation |
| `sdk/introduction` | FiveM SDK |
| `sdk/logs` | SDK Logs |
| `sdk/presigned-uploads` | Scoped upload URLs |
| `sdk/screenshots` | Screenshots |
| `sdk/server-exports` | Server exports |
| `sdk/troubleshooting` | SDK troubleshooting |
| `voice/operations` | Voice operations |
| `voice/setup` | Set up FiveMesh Voice |
