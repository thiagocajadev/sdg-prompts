# 04 - Validação do Hello World

## O que foi validado?

- [ ] A aplicação está rodando.
- [ ] O primeiro endpoint foi exposto.
- [ ] O primeiro teste está passando.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 04 - Validação do Hello World

## O que foi validado?

Tá tudo certo, o app subiu local.
```

> **Razão**: Como você prova o sucesso? Onde está o log de healthcheck?

### ✅ Exemplo Bom

```markdown
# 04 - Validação do Hello World

## O que foi validado?

- [x] Resposta 200 OK no endpoint `/health`.
- [x] Log de inicialização exibe "Server listening on port 8080".
- [x] O comando `npm test` executou o primeiro teste básico com sucesso.
```

> **Razão**: Oferece evidências concretas e rastreáveis da inicialização bem-sucedida.
