# reusable-workflows
Reusable workflows

## Pinning version and Dependabot

Pin versions to commit SHAs and comment version, example:

```yaml
uses: mojotech-no/reusable-workflows/.github/workflows/zizmor.yml@a52c5287aaae4805754ef5914df92f0c6375ad58 # v0.0.0
```

which is good practice to keep away from supply chain attacks.

Configure Dependabot for your repo in order to get automatic PR's on new releases of this repo.

If you like to live dangerously, pin `main`.

## Zizmor
Scan your GitHub Actions and workflows. https://github.com/woodruffw/zizmor

Workflow: [.github/workflows/zizmor.yml](.github/workflows/zizmor.yml)

Example use:

```yaml
name: Zizmor

on:
  workflow_dispatch:

permissions:
  security-events: write
  contents: read # only needed for private repos
  actions: read # only needed for private repos

jobs:
  container-scan:
    uses: mojotech-no/reusable-workflows/.github/workflows/zizmor.yml@main
```

Benefit:

- Central maintenance to this repo.
- Possible to make this a required workflow for all/select repos using rulesets https://docs.github.com/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets .