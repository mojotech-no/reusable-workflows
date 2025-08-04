# reusabe-workflows
Reusable workflows

## Container Scan

Scan your Docker

Workflow: [.github/workflows/container-scan.yml](.github/workflows/container-scan.yml)

Example use:

```yaml
name: Container Scan

on:
  workflow_dispatch:
    inputs:
        image_tag_to_scan:
          description: "Desired image tag to scan (0.0.0, main..)"
          required: true
          type: string
          default: "latest"

permissions:
  contents: read
  security-events: write
  packages: read
  actions: read

jobs:
  container-scan:
    uses: mojotech-no/reusable-workflows/.github/workflows/container-scan.yml@main
    secrets:
      ghcr_github_token: ${{ secrets.ghcr_github_token }}
    with:
      image_tag_to_scan: ${{ inputs.image_tag_to_scan }}
```

Benefit:

Let this repo handle the internal maintenance of keeping needed actions for the workflow up to date,
particularly the action for the actual container scan which requires a special interest to maintain.
