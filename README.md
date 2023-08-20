# GitHub Actions - Auto-tag

Delete and re-release tags so that other modules can use something similar to carets (^)

Caret (^) requirements are not supported by github-action e.g. @^2 does not work

The action will tag v2 when 2.5.0 is released and v0.3 when 0.3.5 is released

The new 'v' tag will point to the same sha  e.g. the sha of v2 will equal the sha of 2.5.0

This allows modules to include workflows using the @v2 or @v0.3 syntax

Using the 'v' prefix to avoid confusion with the '2' branch naming convention that Silverstripe uses

## Usage

This action has no configuration or inputs - just add the following workflow verbatim.

**.github/workflows/auto-tag.yml**
```yml
name: Auto-tag

on:
  push:
    tags:
      - '*.*.*'
  workflow_dispatch:

jobs:
  auto-tag:
    name: Auto-tag
    runs-on: ubuntu-latest
    steps:
      - name: Auto-tag
        uses: silverstripe/gha-auto-tag@v1
```
