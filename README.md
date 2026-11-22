# Remote integration template

A 1weavr integration that runs on **your own server**. 1weavr calls your endpoint when something happens
(a capture is made or fixed) and when it needs an answer from you (the facts shown on a capture).

This one tells your service about new and fixed captures and shows what it says back, for example which release
holds a fix.

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
