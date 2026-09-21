# Filter FabJS Online Filter Library

Official static distribution repository for Filter FabJS native v2 filters.
The application remains the primary browser. Built-in filters are not migrated.

- `registry.json`: only publication ID, revision and date, plus catalogue version.
- `source/<id>.json`: canonical editable native v2 source.
- `filters/<id>-r<revision>.png`: exact 512 × 512 portable PNG, sample plus embedded filter.
- `reference/README.md`: approved reference image policy.
- `site/index.html`: minimal landing page.
- `dist/`: generated Pages output; never commit it.

Target site: https://anthonychimming.github.io/filter-fabjs-library/

Target feed: https://anthonychimming.github.io/filter-fabjs-library/catalogue.json

The initial registry is intentionally empty. No approved production reference image
or packages were supplied. Automated fixtures live only in the main app's tests.
The endpoints are usable only after the Pages workflow successfully deploys.

## Validator setup

The sole publishing implementation lives in the main
[Filter FabJS repository](https://github.com/anthonychimming/filter-fabjs), under
`tools/online-library/publish-library.mjs`. CI checks out that repository separately.
It reuses the native, PNG, portable-content and manifest validators; runtime
validation is also retained in the app.

Set repository Actions variable `FILTER_FABJS_VALIDATOR_REF` to the full 40-character
commit SHA containing the completed Stage 5 tool and its Stage 1–4 dependencies.
This is a deliberate release pin, not a moving branch. An unset/non-SHA value fails
CI before checkout. Upgrade it only after reviewing and verifying a new validator
release. No production fallback to `main` exists.

The current app has no npm dependencies or lockfile. CI uses `npm ci --ignore-scripts`
if a future pinned validator includes a lockfile; otherwise it verifies that there
are no dependencies. No install or package lifecycle script is needed today.

## Local use (Node 22)

With sibling `filter-fabjs` and `filter-fabjs-library` checkouts, run from the app:

```sh
npm run library:validate -- --library-root ../filter-fabjs-library
npm run library:build -- --library-root ../filter-fabjs-library --out ../filter-fabjs-library/dist
```

Before publishing, compare against the last published library commit:

```sh
npm run library:build -- --library-root ../filter-fabjs-library --base-ref <published-library-commit> --generated-at 2026-09-20T12:00:00Z
```

`--base-ref` is resolved in the library Git repository without checking out or
executing its contents. `--base-root` accepts a separate base checkout for tests or
local review. Without a base, structural/current-content validation still works,
but historical mutation/revision checks cannot be certified. Output is restricted
to the library's `dist/`; an existing non-generated directory is never replaced.

## CI and deployment

PR validation uses read-only `contents: read`, no secrets or deployment, and compares
with the target base SHA. Pages runs only on trusted `main` pushes/manual execution;
its read-only build compares with the push's previous SHA (manual: first parent).
No unavailable base is silently ignored. Protect `main` against force-push and
require **Validate library / validate** before merging. Manual rebuild is for an
already validated main history, not a way to skip reviewing earlier commits.

In Settings → Pages, select **GitHub Actions**. The deploy job depends on successful
validation/build and uses the `github-pages` environment with only `contents: read`,
`pages: write`, `id-token: write`. It uploads generated files without transformation.
See GitHub's [custom Pages workflow documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).

The catalogue is mutable, guarded by the app's monotonic version/fallback rules.
PNG URLs are immutable and historical PNGs remain in every deployment. There are no
rewrite rules or SPA fallbacks for missing package paths. Same PNG serves preview
and download, byte for byte. Users may also download files directly from GitHub.

## Licence

Repository code and contributed filter definitions use GPL-2.0-or-later, matching
Filter FabJS; see LICENSE. Reference artwork needs its own explicit, compatible
rights/provenance record. No rights to unsupplied artwork are assumed.

See CONTRIBUTING.md for authoring, revision rules and release QA.
