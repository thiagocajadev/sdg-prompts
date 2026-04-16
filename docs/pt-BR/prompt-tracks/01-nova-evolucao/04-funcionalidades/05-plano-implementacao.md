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
# SPEC-005: Roadmap de Implementação (Checkout)

## 1. Contexto
Sequenciamento técnico para a entrega do Módulo de Checkout de forma segura e incremental.

## 2. Resultados Esperados (Success Metrics)
* Rollback possível em menos de 10 segundos via Feature Flag.
* Deploy sem downtime para as versões legadas do sistema.

## 3. Escopo e Cenários (User Stories)
* **Tarefa 1:** Criar campo `tax_id` na tabela `Orders` (Permitir nulo).
* **Tarefa 2:** Implementar serviço `TaxCalculator` com 100% de testes unitários.

## 4. Restrições e Regras de Negócio
* Habilitação da regra via **Feature Flag** em Staging primeiro.
* Desativação instantânea da flag se erro P95 > 1s no Datadog.

## 5. Fora de Escopo
* Migrações de dados retroativas para pedidos antigos.
* Alteração manual de status de impostos no banco de dados.

## 6. Definição de Pronto (DoD)
- [ ] Feature Flag funcional e testada em Staging.
- [ ] Serviço `TaxCalculator` integrado ao fluxo principal.
- [ ] Plano de reversão documentado e verificado.
```

> **Razão**: Divide o trabalho de forma lógica e garante que o sistema pode ser revertido em segundos através de uma flag, sem a necessidade de um novo deploy de emergência.
