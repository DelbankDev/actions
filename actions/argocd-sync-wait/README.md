# argocd-sync-wait

Valida estado `Healthy/Synced` no ArgoCD e, opcionalmente, executa `argocd app sync` antes.

## Inputs

- `argocd-server` (obrigatorio)
- `argocd-username` (opcional quando usar token)
- `argocd-password` (opcional quando usar token)
- `argocd-token` (opcional alternativa)
- `app-name` (obrigatorio)
- `sync` (opcional, default `false`)
- `revision` (opcional)
- `timeout-seconds` (opcional, default `300`)
- `insecure` (opcional, default `false`)

## Comportamento

- `sync=false`: executa apenas `argocd app wait --health --sync`.
- `sync=true`: executa `argocd app sync` e depois `argocd app wait --health --sync`.

## Uso

```yaml
- uses: ./actions/argocd-sync-wait
  with:
    argocd-server: ${{ vars.ARGOCD_SERVER }}
    argocd-username: ${{ secrets.ARGOCD_USERNAME }}
    argocd-password: ${{ secrets.ARGOCD_PASSWORD }}
    app-name: my-app
    sync: "false"
```
