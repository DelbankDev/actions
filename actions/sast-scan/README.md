# sast-scan

Executa analise SAST com SonarQube e, opcionalmente, valida Quality Gate.

## Inputs

- `sonar-host-url` (obrigatorio)
- `sonar-token` (obrigatorio)
- `project-key` (opcional; default automatico `org:repo:branch`)
- `project-base-dir` (opcional, default `.`)
- `args` (opcional)
- `quality-gate` (opcional, default `false`)
- `quality-gate-timeout` (opcional, default `300`)

## Uso

```yaml
- uses: ./actions/sast-scan
  with:
    sonar-host-url: ${{ secrets.SONAR_HOST_URL }}
    sonar-token: ${{ secrets.SONAR_TOKEN }}
    quality-gate: "true"
```
