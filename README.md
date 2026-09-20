# Pets Registry — `pets`

The **Pets Registry** for the [Kirn language](https://github.com/kirn-lang/kirn): the
ecosystem where Kirn **pets** (pydoc/godoc-spirit inline-doc'd libraries and tools) are
discovered, installed and updated.

- **Landing / search UI:** https://pets-registry.github.io
- **docs (learn Kirn / k-docs):** https://rkriad585.github.io/kirn

## What this repo is

- `registry.toml` — the registry **index** that `kirn i <name>` resolves against.
- `.github/workflows/pets-build-release.yml` — the **Auto Build & Release** template that
  `kirn new pets <name>` auto-initializes in every pets repo: **tag-triggered**; on a pushed
  `v*` tag the workflow runs `kirn build pets` and publishes a release artifact + rust-style
  installers, so anyone can install the pet with:

  ```sh
  kirn i <name>                     # by registry name
  kirn i <user>/<repo>              # by owner/repo
  kirn i [https://]gitlab.com/<user>/<repo>   # third-party git host
  ```

## No built-in pets

Per plan section 13.1 there are **no built-in pets**. Std pets live in their own repos on
this org and are pushed + tagged; `kirn setup` auto-installs them **globally**
(`~/.kirn/pets`) so they work on any project. Nothing in this index is hardcoded — it is
populated by the Auto Build & Release workflow on tag.

## Adding a pets

1. `kirn new pets <name>` — scaffolds a template + the Auto Build & Release workflow.
2. Push it to `https://github.com/pets-registry/<name>`.
3. Tag it (`v*`) — the workflow builds, registers it on this index, and publishes an
   installable release. Done; nothing to hand-edit here.

## License

MIT — see `LICENSE`. © 2026 Kirn (pets-registry).
