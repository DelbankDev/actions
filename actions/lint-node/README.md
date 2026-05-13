# lint-node

Executa o comando de lint em um projeto Node.

## Inputs

- `working-directory` (opcional, default `.`)
- `lint-command` (opcional, default `npm run lint`)
- `enforce` (opcional, default `true`)

## Pre-condicao

Rode `setup-node-project` antes para garantir dependencias instaladas.

## Uso

```yaml
- uses: ./actions/lint-node
  with:
    lint-command: "npm run lint"
    enforce: "true"
```

## Modo nao-bloqueante

```yaml
- uses: ./actions/lint-node
  with:
    lint-command: "npm run lint"
    enforce: "false"
```
