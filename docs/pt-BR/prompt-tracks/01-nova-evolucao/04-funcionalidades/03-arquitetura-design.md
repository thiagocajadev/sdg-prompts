# 03 - Arquitetura e Design

## Design da API (Contrato)

Defina os novos endpoints ou alterações nos existentes:

- **Método**: [GET / POST / PUT / DELETE]
- **Rota**: `/api/v1/...`
- **Request Body (Corpo da Requisição)**:
- **Response Body (Corpo da Resposta)**:

## Mudanças no Modelo de Dados

- Quais tabelas ou campos serão criados ou alterados?
- Existe a necessidade de uma migração (migration)?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - Arquitetura e Design

Vou criar um campo `discount` na tabela de pedidos.
O endpoint vai ser `/desconto`.
```

> **Razão**: Vago. Qual o tipo de dado do campo (Decimal, Integer)? O endpoint é GET ou POST? Qual é o formato do JSON esperado?

### ✅ Exemplo Bom

```markdown
# SPEC-003: Arquitetura do Módulo de Cupons

## 1. Contexto
Estrutura técnica para suportar o motor de cupons (SPEC-002), garantindo performance e integridade dos dados.

## 2. Resultados Esperados (Success Metrics)
* Tempo de resposta da API de cupons < 200ms.
* Integridade referencial entre pedidos e cupons aplicados.

## 3. Escopo e Cenários (User Stories)
* **API:** POST `/api/v1/coupons/apply`.
* **Input:** `{ "code": "SUMMER20", "order_id": "UUID" }`.

## 4. Restrições e Regras de Negócio
* Tabela `coupons` com campos `id`, `code`, `discount_percentage`, `status`.
* Índice único no campo `code` para evitar duplicidade.

## 5. Fora de Escopo
* Dashboards administrativos para gestão de cupons.
* Migração de dados de cupons de sistemas legados.

## 6. Definição de Pronto (DoD)
- [ ] Schema do banco de dados aplicado via migration.
- [ ] Contrato da API validado com Swagger/Postman.
- [ ] Repositório de dados implementado e testado.
```

> **Razão**: Fornece especificações exatas de entrada e saída da API e a estrutura técnica do banco de dados, eliminando ambiguidades durante o desenvolvimento.
