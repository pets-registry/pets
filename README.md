# Pets Registry — the `pets` org index

This org is the **pets registry** for the [Kirn language](https://github.com/rkriad585/kirn).
It does **not** hold any pets itself, and it does **not** run any build workflow. It is
only the **name → repo index** so that `kirn i <name>` can resolve a short registry name.

## How it actually works (the flow)

1. A **pet developer** runs, in their own repo:

     `kirn new pets <petname>`

   That scaffolds the **default hello-world pets template** and **auto-initializes the
   Auto Build & Release workflow** — in *the developer's repo*, on their own GitHub repo:
   `.github/workflows/kirn-pets-release.yml`. Nothing is added to this registry by that
   action.

2. The developer **pushes the pet to their GitHub account** and tags it (`v*`). Their
   repo's own tag-triggered *Auto Build & Release* workflow then `kirn build pets`'s and
   publishes a tagged release artifact.

3. Anyone else installs it:

   - `kirn i <name>`                 — registered name → resolved against this index
   - `kirn i <user>/<repo>`          — full owner/repo form
   - `kirn i [https://]<git-host>/<user>/<repo>` — third-party git host (gitlab/codeberg)

## What lives here (nothing else)

- `registry.toml` — the index `kirn i <name>` resolves against. **Empty**: per §13.1
  there are no built-in pets. A pet becomes a *registered name* only when its repo joins
  this org as a tagged release.
- `README.md` — this landing (mirrors the `pets-registry.github.io` pages site).
- `LICENSE.txt` — MIT (2026 Kirn).

The **workflow template that `kirn new pets` auto-initializes** lives in `src/tools/…`
template scaffolding in the main repo (the ding pet template), not here.
