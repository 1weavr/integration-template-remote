# Remote integration template

Tells your server when a capture is made or fixed, and shows the facts your server answers on each capture. 1weavr
sends every call as an HTTPS `POST` to `runtime.endpoint`, and your server answers it.

## The calls your server answers

| Call | Manifest entry | Input | Output | Limit |
|---|---|---|---|---|
| `event.deliver` (`item.made`) | `events.out` → `actions.onMade` | `{ event: { id, type, at }, item }`: `item` has `id`, `ref`, `title`, `description`, `status`, `labels`, `pictures`, `capture.page` | `{}`, optionally with `activity.add` effects | 10 s, 6 retries |
| `event.deliver` (`item.fixed`) | `events.out` → `actions.onFixed` | the same, with `event.type: "item.fixed"` | `{}`, optionally with `activity.add` effects | 10 s, 6 retries |
| `zone.render` (`item.facts`) | `contributes["item.facts"].render` → `actions.deployFacts` | `{ zone, subject, item }`: `item` as above, without diagnostics or project | `{ blocks: [{ type: "fact", name, value }], ttl }`; `ttl` is how many seconds 1weavr shows it before asking again (300 when absent) | 3 s, no retry |

`event.deliver` is retried, so the same `event.id` can arrive more than once: treat it as idempotent. The manifest
declares no connection, so installing it asks nobody to sign in to your service.

Every call carries `protocol`, `call`, a unique `delivery` id, the `integration`, the `installation` and its
`input`. The answer repeats `call` and `delivery` and is either `{ ok: true, output, effects? }` or
`{ ok: false, error: { code, message } }`, where `code` is `refused`, `failed`, `unauthenticated` or `rate_limited` and
`message` is shown to people as written. An answer that does not match its call's shape is refused and logged.

## What is in it

```
manifest.json   what it is, your endpoint, the events it hears, and what it adds to a capture
icon.svg        its icon in the catalogue (square, flat colour)
fixtures/       test cases: a call, what goes in, and the answer your server must give
```

## Make it yours

1. Press **Use this template** and make your own repository.
2. In `manifest.json`, change `id`, `name`, `summary`, `description` and `links`, and set `runtime.endpoint` and
   `hosts` to your server's address.
3. Keep a test case in `fixtures/` for each call your server answers.
4. Before it can be listed publicly, `links.privacy`, `links.terms` and a description of 200 characters or more
   are required.

The full guide, with the manifest, test cases and publishing: https://1weavr.com/docs/build-an-integration

## Questions

Email support@1weavr.com, or open an issue on this repository.

## Licence

MIT: copy it, change it and ship it as your own. See `LICENSE`.
