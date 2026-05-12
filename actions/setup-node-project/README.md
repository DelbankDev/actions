# setup-node-project

Configura Node.js e instala dependencias com `npm ci`.

## Inputs

- `node-version` (opcional): versao do Node.
- `working-directory` (opcional, default `.`): pasta do projeto.

## Uso

```yaml
- uses: ./actions/setup-node-project
  with:
    node-version: "24"
    working-directory: "."
```
