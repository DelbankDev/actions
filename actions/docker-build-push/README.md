# docker-build-push

Faz login no registry, builda e publica imagem com tag de build e, opcionalmente, `latest`.

## Inputs

- `registry` (obrigatorio)
- `image` (opcional, sem tag)
- `image-namespace` (opcional; obrigatorio quando `image` nao for informado)
- `repository` (opcional; obrigatorio quando `image` nao for informado)
- `ref-name` (opcional; obrigatorio quando `image` nao for informado)
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

Ou gerar o nome automaticamente:

```yaml
- id: docker
  uses: ./actions/docker-build-push
  with:
    registry: registry.digitalocean.com
    image-namespace: delbank-1
    repository: ${{ gitea.repository }}
    ref-name: ${{ gitea.ref_name }}
    registry-username: ${{ secrets.REGISTRY_USERNAME }}
    registry-password: ${{ secrets.REGISTRY_PASSWORD }}
    build-id: "${{ gitea.run_number }}-gitea"
```

## Erro comum

Se aparecer `invalid reference format: repository name must be lowercase`, o valor de `image` esta invalido.

- Garanta que `image` esteja em lowercase.
- Garanta formato sem tag, por exemplo: `registry.digitalocean.com/org/app`.
- Em pipelines com variavel, ajuste `vars.IMAGE` no repositório consumidor.
