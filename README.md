# Action of Action

A GitHub action for building GitHub actions.

Push contents in ./dist directory to remote origin as an orphan and add tags for source branch and product branch.

## Prerequisites

- Use pnpm and set `packageManager` in package.json.

## Usage

```yml
name: Build

on:
  push:
    branches:
      - main

jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - uses: wdzeng/action-of-action@v2
```
