# CLAUDE.md

## Project overview

This repository is a content-driven project for curating and publishing a list of recommended airport/VPN services, with a focus on price, performance, trial availability, and practical usage notes. The public-facing content is primarily in `README.md`, and the project includes contribution guidance in `CONTRIBUTING.md`.

From the repository docs, this is not a typical application codebase. It is closer to a generated documentation project: airport recommendations are maintained as structured data and then exported into user-facing Markdown documents.

## Repository purpose

- Maintain a ranked list of recommended airports/VPN services
- Publish pricing, trial/use notes, and suitability by user scenario
- Allow community submissions and corrections through issues/PRs
- Keep generated docs synchronized with source data

## Important repo conventions

The project documentation explicitly states that the canonical data source is `data/airports.json`, and the generated documentation files are:

- `README.md`
- `README-SIMPLE.md`
- `docs/blacklist.md`

According to `CONTRIBUTING.md`, any PR affecting airport data should regenerate all derived docs and validate the output before submission.

## Expected project workflow

The repo docs mention these commands:

```bash
node scripts/sync-from-astro.js --local ../vpsknow/src/pages/airport-recommendations.astro --dry-run
node scripts/sync-from-astro.js --local ../vpsknow/src/pages/airport-recommendations.astro
npm run generate
npm run validate
git diff --check
```

This suggests a Node-based generation pipeline, even though the current public GitHub snapshot here appears minimal. If files such as `package.json`, `scripts/`, or `data/` are absent locally, check whether you are on a partial clone or a branch that has not yet been synced.

## Files to inspect first

- `README.md` — main public content and rankings
- `CONTRIBUTING.md` — contribution process, validation steps, and data rules
- `LICENSE` — project license

## Contribution expectations

When editing airport-related data:

- Prefer updating the source data rather than hand-editing generated docs
- Regenerate derived files after changes
- Validate the repo before submitting a PR
- Keep structured fields consistent with the schema described in the contribution guide

## Data and schema notes

From `CONTRIBUTING.md`, active airport entries should include fields such as:

- `name`
- `url`
- `lineType`
- `pricing`
- `tags`

Optional but common fields include:

- `coupon`
- `logoSvg`
- `description`
- `features`
- `accessType`
- `isNoAff`

The repo also has category conventions such as:

- `free_trial`
- `budget`
- `balanced`
- `premium`
- `payAsYouGo`

and top-level arrays like:

- `no_aff`
- `directory_only`
- `defunct`

## Content quality guidance

When adding or editing recommendations:

- Favor verifiable, current pricing and feature claims
- Preserve neutrality and avoid unsupported marketing language
- Clearly distinguish official pricing from user-reported notes
- If a provider is defunct or risky, document it in the appropriate issue/report workflow

## Recommended tasks for an AI contributor

- Update existing recommendation data with current pricing or eligibility details
- Add missing entries based on verified sources
- Fix broken links, formatting issues, or stale trial notes
- Ensure generated Markdown docs remain synchronized with source data
- Validate against the project’s documented commands and repo conventions

## Notes for this checkout

This repository snapshot currently exposes only:

- `README.md`
- `CONTRIBUTING.md`
- `LICENSE`

If the project has additional files in your local environment (such as `data/`, `scripts/`, or `package.json`), treat those as the authoritative working tree for changes. The repository’s contribution rules should be followed even if the public GitHub view appears minimal.

## Quick summary

This is a metadata-and-docs repository for a curated airport recommendation list. The main goals are accuracy, transparency, and generated-document consistency. Do not make ad hoc edits to README output if a data source and generation step exist for the project.
