# Integration docs

Not published. Mintlify builds only what `docs.json` lists, and this file is not in it.
See the repo root `README.md` for how the docs are built and `STYLE.md` for the voice.

## The one rule specific to this directory

**Never write a cart's tracking-parameter list from memory, from another cart's page, or
from the vendor's own documentation.** Take it from the app's single source of truth:

`trackplay-app/resources/js/views/Integrations/cartSettings.js`

That file holds `parameterOptions` per cart, and it is the app-side mirror of the
receiver in `trackplay-events/src/services/carts/<cart>.js`. If the two disagree, the
receiver wins and the app file is a bug.

This matters more here than anywhere else in the docs. A wrong parameter name does not
throw. The link is accepted, the sale completes, the postback arrives without a session,
the conversion is filed as organic, and the integration keeps reading **Active**. The
customer sees healthy dashboards and silently loses attribution on every sale. Every cart
page except ElasticFunnels carried wrong values for months for exactly this reason.

The same file records which carts are `unverified` and hidden from the in-app catalogue.
A cart the app refuses to show is a cart the docs must not tell people to set up. Check
`resources/js/views/Integrations/integrations.js` (`SHIPPABLE_INTEGRATIONS`) before adding
a page.

## Second rule: the browser cannot report a conversion

A sale completes on the cart's domain after the viewer has left the page, so the player
is gone and no browser-side integration can ever see it. Do not document a conversion
event on GTM, Segment, or any other client-side destination. This has been shipped wrong
twice. Conversions arrive by cart postback or by webhook, never through the dataLayer.

## Pages here

`configuration.mdx` is the landing page. Cart platforms, tags and pixels, conversions and
outbound, and the ElevenLabs page are grouped under Integrations in `docs.json`.
