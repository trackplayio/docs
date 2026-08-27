# TrackPlay documentation

The customer-facing docs for TrackPlay, published with Mintlify at
[docs.trackplay.io](https://docs.trackplay.io). Everything a customer reads about the
player, the analytics, the integrations, and the APIs lives here.

## Where the product actually lives

Docs drift because the code moves and nobody opens this repo. Three repos, and the two
you will be checking your writing against are not this one:

| Repo | What it holds |
| --- | --- |
| `trackplay-app` | The Laravel app, the Vue dashboard, and the player build (`lambda-function-clone`, `lambda-function-clone-v2`). Player options, analytics queries, cart integration UI, billing. |
| `trackplay-events` | The service behind `e.trackplay.io`. Event ingest, the accepted payload schema, cart postback receivers, outbound pixels, the manifest gate, the identity pixel. |
| `trackplay-docs` | This repo. |

Two internal files in `trackplay-app` are worth reading before a large edit:

- `docs/FEATURES_MASTER.md` is the internal source of truth for what every feature is
  and whether it may be marketed. It carries status labels (Live, Internal, Parked) and
  its own correction notes. Treat it as a checklist and an index of where code lives.
  Do not treat it as evidence. Confirm in code before you publish a claim.
- `CLAUDE.md` carries the rule this repo exists to satisfy: **any change to what a
  customer sees or does ships with its documentation, in the same change.** That covers
  a new or removed feature, UI copy, an event name or payload, an API shape, a default,
  plan gating, and player behavior.

## The rule that keeps this repo honest

Before publishing a claim, find the code that proves it. A feature can exist in the
runtime and still be hidden, unverified, plan-gated, or deliberately parked. Documenting
one of those tells a customer to set up something that will not work.

Two failures that already happened, and are why this section exists:

- The GTM page listed a `trackplay_conversion` event the runtime had removed, and told
  customers to fire a pixel on an event that never fires.
- Feature pages claimed automatic split-test winner selection, which does not exist, and
  listed the wrong set of cart platforms.

Say what goes wrong, not only the happy path. Name the error code. If a number is a
default, give the default. If a value is an estimate, say it is an estimate.

## Preview locally

```bash
npm i -g mintlify
mintlify dev
```

Run it from the repo root, the directory holding `docs.json`. If a page loads as a 404,
you are running from the wrong directory. If `mintlify dev` will not start, run
`mintlify install` to reinstall dependencies.

## How the site is put together

**`docs.json`** is the navigation and the theme. Mintlify builds only the pages listed
in it. A new `.mdx` file that is not added to `docs.json` is invisible on the site, and
nothing warns you. Two tabs are defined: Guides and API Reference.

**Pages** are one `.mdx` per topic, in a directory per area: `get-started`, `player`,
`configuration`, `embed`, `analytics`, `split-tests`, `integration`, `events`,
`identity`, `api-reference`.

**`api-reference/openapi.json`** generates the Endpoints section of the API Reference
tab, so the playground works and the schema cannot drift from the prose. Hand-written
API prose belongs in a guide page that links to the reference, never in a second copy of
the schema. When an endpoint changes, change the spec.

**`snippets/`** holds reusable `.mdx` fragments imported into pages.

**Not published:** this README and `STYLE.md`. Mintlify only builds what `docs.json`
lists.

## Voice and format

`STYLE.md` is the standard every `.mdx` here is held to. Read it before writing. The two
rules that are broken most often:

1. **No em-dashes and no en-dashes.** Use a full stop, a contrast comma, a colon, or
   parentheses.
2. **No contractions.** `cannot`, `does not`, `it is`, `you are`.

There is also a banned-word list (`comprehensive`, `powerful`, `seamless`, `robust`,
`simply`, `just`, `easy`, and more). `STYLE.md` carries the full list, the Mintlify
component conventions, the frontmatter shape, and the code-sample rules.

Placeholder token in every sample is `tplt_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`. Base URLs
are `https://app.trackplay.io` for the app API and `https://e.trackplay.io` for events.

## Publishing

The Mintlify GitHub App deploys the default branch to production on push. Install it
from the Mintlify dashboard.

## Known cleanup

- `images/` and `logo/` are unreferenced Mintlify starter-kit leftovers. No page and no
  config points at them.
- `docs.json` loads the site logo from a remote `storage.googleapis.com/elasticfunnels`
  URL rather than from this repo, so the branding depends on a bucket this repo does not
  own.
