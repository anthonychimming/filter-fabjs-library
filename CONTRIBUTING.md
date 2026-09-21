# Publishing filters

1. Author and test a native v2 filter with a stable portable ID (1–80 ASCII letters,
   digits, `_` or `-`). Keep IDs unique even ignoring case for portable checkouts.
2. Export canonical JSON to `source/<id>.json`. The embedded ID must match exactly.
3. Use the approved project-owned/licensed 512 × 512 reference described in
   `reference/README.md`; reset to authored defaults and render in Filter FabJS.
4. Export the portable PNG with FilterFabJS metadata as `filters/<id>-r1.png`.
   Packages must be 512 × 512 and no more than the runtime 8 MiB limit. Do not
   optimize, re-encode, strip metadata, or use screenshots as portable packages.
5. Add `{ "id": "<id>", "revision": 1, "publishedAt": "YYYY-MM-DD" }` to registry
   `filters`. Do not copy name/author/description/tags into the registry.
6. Increase `libraryVersion`, validate/build against published base, and open a PR.
7. Review Sample pixels manually, let validation pass, and merge to main. Pages
   deploys the validated output. No application release is needed for new content.

## Registry and revisions

Top level contains exactly `schema: "filter-fab-js/library-registry"`,
`schemaVersion: 1`, positive safe-integer `libraryVersion`, and `filters` (at most
1,000). Each entry contains exactly `id`, positive safe-integer `revision`, and a
real `publishedAt` calendar date. Array ordering is irrelevant; catalogue output
sorts by portable ID using deterministic ASCII ordering.

New IDs start at r1. Any source file or package change requires a higher revision
and new package filename; even a source formatting-only edit requires a bump in
base comparison. Unchanged source/package keeps its revision. Keep all historical
PNGs unchanged; never delete or rewrite a published URL. Revision increments need
not be +1. Reintroducing an ID removed from the registry requires a revision above
its retained history. Local no-base checks require r1 history for current rN.

Adding/removing an entry, changing its publication date, or publishing a revision
requires a higher libraryVersion. A content rollback uses a new filter revision
and a higher libraryVersion, never moves the current pointer backwards. Removing
an entry removes discovery only; keep its historical packages deployed.

Metadata is derived from validated source. Native source and embedded native
content must match (including explicit ID plus the app's normalized portable
comparison of metadata, tags, math mode, formulas and rich controls). The build
does not render formulas. PNG dimension/structure/envelope checks reuse the app
parser; its CRC coverage is the FilterFabJS metadata plus publishing IHDR. CI does
not certify image pixel provenance or replace runtime validation.

`generatedAt` is the explicit build timestamp (`--generated-at` for reproducible
builds); it is excluded from publication-change comparison. Same-content rebuilds
may keep libraryVersion. Package and source metadata/formula changes may not.

## Release QA

- Open the Pages landing page, catalogue JSON, and a real revisioned PNG.
- Confirm missing PNG paths return 404 rather than a successful HTML response.
- In Filter FabJS: local sources first; Source → Online; Sample/search/tags/favorite.
- Preview on your source image, Cancel; preview again, Apply; confirm unsaved state.
- Download PNG, re-import, and compare metadata/formulas/controls.
- Load Online, reload, go offline and enter Online: saved metadata remains usable.
  Reconnect and Retry. Packages are not persisted offline.
- Publish r1 → r2: catalogue uses r2, r1 URL remains accessible, app uses fresh r2.
- Recheck Built-in/My Filters, JSON/PNG import/export, Author Save/Delete, CPU/WebGPU.

Before first production content: approve reference artwork, supply reviewed native
sources and matching portable packages, and review the first 3–8 filters. Never
promote generated automated-test fixtures to production. Contributions are
GPL-2.0-or-later; retain appropriate artwork rights/attribution.
