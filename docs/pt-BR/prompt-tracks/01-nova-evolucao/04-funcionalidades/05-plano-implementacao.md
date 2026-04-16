# 05 - Plano de Implementação

## Sequência de Tarefas (Atômicas)

Liste as tarefas na ordem de execução para evitar bloqueios entre desenvolvedores:

1.  [ ] Criar migração de banco de dados para a tabela `X`.
2.  [ ] Implementar o serviço de lógica de negócio em `domain/services`.
3.  [ ] Criar os controladores e rotas da API.
4.  [ ] Integrar com o Frontend.

## Plano de Rollback (Reversão)

- Caso o deploy falhe, qual o procedimento para desfazer as alterações?
- Como lidar com migrações de dados que já foram executadas?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 05 - Plano de Implementação

Vou fazer o backend e depois o frontend. Se der erro eu dou ctrl+z.
```

> **Razão**: Vago. O "fazer o backend" pode envolver 10 tarefas diferentes. Plano de rollback inexistente (ctrl+z não funciona em banco de dados de produção).

### ✅ Exemplo Bom

```markdown
# 05 - Plano de Implementação: Módulo de Checkout

## Sequência de Tarefas

1. Criar novo campo `tax_id` na tabela `Orders` (Permitir nulo para compatibilidade).
2. Criar serviço `TaxCalculator` com 100% de testes unitários.
3. Habilitar a nova regra via **Feature Flag** apenas para o ambiente de Staging.

## Plano de Rollback

- **Código**: Desativar a Feature Flag no painel de controle (tempo estimado: 10s).
- **Dados**: O campo `tax_id` aceita nulos, portanto não quebra as versões anteriores do código se precisarmos reverter o binário.
```

> **Razão**: Divide o trabalho de forma lógica e garante que o sistema pode ser revertido em segundos através de uma flag, sem a necessidade de um novo deploy de emergência.
