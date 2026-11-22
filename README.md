# Remote integration template

Tells your own server about captures and shows what it says back, for example which release holds a fix. 1weavr
calls the endpoint in `runtime.endpoint`; your server does the work.

What it does in 1weavr, and which part of the manifest does it:

| Where | What happens | In `manifest.json` |
|---|---|---|
| A capture is made | Your server is told, with the capture's title, note, labels, pictures and page | `events.out` `item.made` → `actions.onMade` |
| A capture is fixed | Your server is told again | `events.out` `item.fixed` → `actions.onFixed` |
| Facts, on a capture | Rows your server answers, such as "Fixed in: 4.2", kept for as long as it says (`ttl`) | `contributes["item.facts"]` → `actions.deployFacts` |
| Activity, on a capture | A line your server adds when it has something to say | `contributes["item.activity"]`, `effects: ["activity.add"]` |

It needs no connection: nobody signs in to your service to install it.

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
