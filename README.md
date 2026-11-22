# Remote integration template

A 1weavr integration that runs on **your own server**. 1weavr calls your endpoint when something happens
(a capture is made or fixed) and when it needs an answer from you (the facts shown on a capture).

This one tells your service about new and fixed captures and shows what it says back, for example which release
holds a fix.

## Status

This template is ahead of the platform. Read this before you build on it:

- **The remote runtime is not available yet.** Today 1weavr runs only its built-in integrations. If you upload this
  integration now, every call answers "The remote runtime is not available on this server yet". Its manifest and test
  cases are checked, but nothing runs.
- **There is no command-line tool yet** to run the test cases on your machine. They will run in 1weavr's developer
  console once the runtime is there.
- **Uploading packages is not built yet** either. Watch this repository: this README changes as each of these ships.

## What is in it

```
manifest.json   what it is, your endpoint, the events it hears, and what it adds to a capture
icon.svg        its icon in the catalogue (square, flat colour)
fixtures/       test cases: a call, what goes in, and the answer your server must give
```

There is no server code here yet. How 1weavr signs its requests to your endpoint is still being designed, and a
server that cannot check those signatures should not be copied. The server code lands here once the format is
settled.

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
