# Retag Docker Image Action

Composite action that logs in to a Docker registry and retags an image using `docker buildx imagetools`.

## Inputs

- `image` (required): Docker image name (e.g. org/image)
- `registry-hostname` (optional): Docker registry hostname (e.g. cr.production.casavo.tech). If not provided, cr.production.casavo.tech is used.
- `source-tag` (required): Source tag of the Docker image to retag.
- `target-tag` (required): New tag to assign to the Docker image.
- `registry-username` (optional): Docker registry username. If not provided, no login will be performed.
- `registry-password` (optional): Docker registry password. If not provided, no login will be performed.

## Example usage

```yaml
jobs:
  retag:
    runs-on: ubuntu-latest
    steps:
      - uses: casavo/action-retag-docker-image@v1
        with:
          image: org/image
          registry-hostname: cr.production.casavo.tech
          source-tag: ${{ github.sha }}
          target-tag: production
          registry-username: ${{ secrets.CR_USERNAME }}
          registry-password: ${{ secrets.CR_PASSWORD }}
```
