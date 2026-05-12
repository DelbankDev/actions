# docker-build-push

Faz login no registry, builda e publica imagem com tag de build e, opcionalmente, `latest`.

## Inputs

- `registry` (obrigatorio)
- `image` (obrigatorio, sem tag)
- `registry-username` (obrigatorio)
- `registry-password` (obrigatorio)
- `build-id` (obrigatorio)
- `push-latest` (opcional, default `true`)
- `context` (opcional, default `.`)
- `dockerfile` (opcional, default `Dockerfile`)

## Outputs

- `image_build_tag`
- `image_latest_tag`

## Uso

```yaml
- id: docker
  uses: ./actions/docker-build-push
  with:
    registry: registry.example.com
    image: registry.example.com/org/app
    registry-username: ${{ secrets.REGISTRY_USERNAME }}
    registry-password: ${{ secrets.REGISTRY_PASSWORD }}
    build-id: ${{ github.run_number }}
```
