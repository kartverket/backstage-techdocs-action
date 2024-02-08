# backstage-techdocs-action

This action generates static documentation from your Backstage TechDocs and deploys it to GCS.

## Usage

create techdocs.yaml in `.github/workflows` directory

```yaml
name: Publish TechDocs Site

on:
  push:
    paths:
     - "docs/**"
     - "mkdocs.yml"

jobs:
  publish-techdocs-site:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write
      id-token: write

    steps:
      - id: 'techdocs-action'
        uses: kartverket/backstage-techdocs-action@v3
        with:
          entity_kind: '<kind-lowercase>'
          entity_name: '<same-as-repo>'
```       gcs_bucket_name: ${{vars.BACKSTAGE_TECHDOCS_GCS_BUCKET_NAME_SANDBOX}}
          workload_identity_provider: ${{vars.BACKSTAGE_TECHDOCS_WIF_SANDBOX}}
          service_account: ${{vars.BACKSTAGE_TECHDOCS_SERVICE_ACCOUNT_SANDBOX}}
          project_id: ${{vars.BACKSTAGE_TECHDOCS_PROJECT_ID}}
```
