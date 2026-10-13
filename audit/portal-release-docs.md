# Portal release documentation — October 13, 2026

Prepared customer guides for Portal setup, dashboard operations and personal
player uploads. Added the Portal navigation group, linked the guides from the
docs entry points and updated CDN metadata/retention documentation. Legacy
upload-portal documentation links now redirect to the current Portal guides.

Verified behavior against the released app (`1cb6116`) and Portal Worker
(`fa00b32`), including the actual UI labels, registered-server ownership,
account access gate, Discord installation, upload formats and size bounds,
per-player UTC allowances, role checks, restrictions, shared CDN expiration,
Discord metadata and the distinction between Portal deletion and CDN deletion.

At the user's request, customer-facing Portal content uses “FiveMesh Portal”
without a prerelease qualifier. The current per-account access requirement is
documented without exposing the internal feature-flag implementation.

Mintlify build validation and broken-link checks pass. All three guides render
in the existing local Mintlify preview, including the sidebar, steps, tables,
expiration guidance and public-link privacy note. The setup preview remains
open for review. No product code, production configuration or customer data
was changed. Documentation has not been pushed or published.
