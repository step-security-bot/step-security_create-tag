[![StepSecurity Maintained Action](https://raw.githubusercontent.com/step-security/maintained-actions-assets/main/assets/maintained-action-banner.png)](https://docs.stepsecurity.io/actions/stepsecurity-maintained-actions)

# create-tag

A GitHub Action to tag a commit with a valid semantic version.

For example:

```yaml
name: Tag

on:
  workflow_dispatch:
    inputs:
      version:
        description: 'Release version (e.g. v0.1.0)'
        required: true
      message:
        description: 'Tag message'
        required: true

jobs:
  create-tag:
    runs-on: ubuntu-18.04

    steps:
      - name: Checkout
        uses: actions/checkout@v7

      - name: Create Tag
        uses: step-security/create-tag@v1
        with:
          version: ${{ github.event.inputs.version }}
          message: ${{ github.event.inputs.message }}
          token: ${{ secrets.GITHUB_TOKEN }}
```
