# Action of Action

A GitHub action for building GitHub actions written in TypeScript. It does the following things:

1. Downloads the source action project.
2. Runs `pnpm build` to build the source action project. This should transpiles the TypeScript action to JavaScript.
3. Retrieves the transpiled files under a directory (e.g. `dist/`) and pushes them to remote destination branch (e.g.
  `origin/release`).
4. Adds and pushes three version tags `vX`, `vX.X`, and `vX.X.X` to remote destination branch, and a source tag
   `src-X.X.X` to remote source (`origin/HEAD`). For pre-releases, only one version tag `vX.X.X-alpha|beta-X` is pushed
   to remote destination branch.

## Prerequisites

- The project can be installed using pnpm.
- The pnpm version is described in the `packageManager` field in package.json.
- The action can be built by `build` command defined in `scripts` field in package.json.
- The project version is specified in `version` field in package.json.
- The project version is a semver. For pre-releases, only `alpha` and `beta` are allowed.

## Inputs

All inputs are optional.

- github-token: the GitHub token to use; default to `${{ github.token }}`
- dist-dir: the directory under which files are to be pushed; default to `./dist`
- remote-name: remote name to download and push the source and destination action; default to `remote`
- dist-branch: target branch to push the built action; default to `release`
- user-name: commit user for the build; default to `bot`
- user-email: commit user email for the build; default to `bot@hyperbola.me`

## Usage

```yml
name: Build

on:
  push:
    branches:
      - main

jobs:
  build:
    name: Build action
    runs-on: ubuntu-latest
    steps:
      - uses: wdzeng/action-of-action@v3
```

You don't need to run `actions/checkout`. This action does that for you.
