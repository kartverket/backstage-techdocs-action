# backstage-techdocs-action

This action generates static documentation from your Backstage TechDocs and deploys it to GCS using WIF.

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
        uses: kartverket/backstage-techdocs-action@v1
        with:
          entity_kind: '<kind-lowercase>'
          entity_name: '<same-as-repo>'
          gcs_bucket_name: '<bucket-name>'
          workload_identity_provider: 'projects/<projectno>/locations/global/workloadIdentityPools/<wif-pool>/providers/<provider>'
          service_account: '<gcp-service-account-email>'
          project_id: '<gcp-project-id>'
```
