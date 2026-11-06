# mfeflow starter

A React micro-frontend project with a shell and two remotes, made with mfeflow 0.8.0.

It uses Module Federation 2.0 and Rsbuild. It builds, type checks, lints and tests out of the box.

## Use it

Pick one:

- Click **Use this template** on GitHub.
- Run `npx degit mfeflow/starter my-app`.
- Run `npm create mfeflow@latest` to start fresh and choose your own features.

Then, in the new folder:

```sh
pnpm install
pnpm mfeflow dev
```

Open http://localhost:4300. The shell loads the catalog and cart remotes at runtime.

Needs Node 22.12 or newer and pnpm.

## Commands

```sh
pnpm mfeflow dev       # shell and all remotes, one log per app
pnpm build             # build everything
pnpm typecheck
pnpm lint
pnpm test              # unit tests
pnpm test:e2e          # Playwright smoke test
pnpm mfeflow doctor    # checks versions, config and drift
pnpm mfeflow validate  # checks mfeflow.json and the registry files
```

`pnpm mfeflow check-compat` and `pnpm mfeflow budget` are also run in CI.

## What is inside

```
apps/shell      the host, on port 4300
apps/catalog    a remote, on port 4311
apps/cart       a remote, on port 4312
registry/envs   which build of each remote dev, staging and prod serve
env.ts          typed environment variables
e2e/            Playwright smoke test
mfeflow.json    what the CLI generated; `mfeflow add` and `upgrade` read it
```

Features switched on:

- `lint-oxlint`: oxlint with type-aware rules, plus Prettier
- `url-factory`: typed URLs for the remotes
- `env-t3`: environment variables checked with zod
- `testing`: Vitest unit tests and a Playwright smoke test
- `ci-github`: a pull request workflow in `.github/workflows/ci.yml`
- `git-hooks`: lefthook and commitlint

`registry/envs/staging` and `prod` point at `example.com`. Change them to where you host each remote.

## Change it

```sh
pnpm mfeflow add remote checkout   # a new remote, its registry files and its shell route
pnpm mfeflow add theming           # add a feature
pnpm mfeflow features              # list the features
```

To build on Vite instead of Rsbuild, make your own project with `npm create mfeflow@latest -- --bundler vite`.

## Upgrade

This repo was made with mfeflow 0.8.0. To move to a newer version:

```sh
pnpm mfeflow upgrade
```

It shows a diff and keeps files you changed.

## Docs

- [Quickstart](https://mfeflow.github.io/mfeflow/guide/quickstart)
- [Project structure](https://mfeflow.github.io/mfeflow/guide/project-structure)
- [All docs](https://mfeflow.github.io/mfeflow/)
- [mfeflow on GitHub](https://github.com/mfeflow/mfeflow)

## License

MIT
