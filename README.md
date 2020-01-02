# GitHub Action: Detect PR file changes
Detects whether or not a file in a provided path has been changed.

Useful for preventing steps in workflows, can provide multiple paths as regular expressions

## Example Usage

```yaml

name: Test Workflow

on: [pull_request]

jobs:

  test:
    runs-on: ubuntu-latest
    env:
      GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
    steps:
      - name: Get Changed Files
        id: changed
        uses: foodee/pr-includes-file-change@master
        with:
          paths: ^asdf.js ^main.js

      - name: Echo Match
        if: steps.changed.outputs.matched == 'true'
        run: echo Matched

```

