# Action of Action

GitHub Action for building GitHub Action.

Push contents in ./dist directory to remote origin as an orphan and add tags for source branch and product branch.

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
      - uses: wdzeng/action-of-action@v1
        with:
          github-action: ${{ secrets.GITHUB_ACTION }}
```
