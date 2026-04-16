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
# 03 - Arquitetura e Design: Módulo de Cupons

## API Contract (Novo Endpoint)

- **POST `/api/v1/coupons/apply`**
- **Input**: `{ "code": "SUMMER20", "order_id": "UUID" }`
- **Output (200 OK)**: `{ "applied": true, "new_total": 80.00, "discount_value": 20.00 }`

## Modelo de Dados (Schema)

- **Nova Tabela `coupons`**:
  - `id`: UUID (Primary Key)
  - `code`: VARCHAR(20) (Unique Index)
  - `discount_percentage`: DECIMAL(5,2)
  - `status`: ENUM('active', 'expired')
```

> **Razão**: Fornece especificações exatas de entrada e saída da API e a estrutura técnica do banco de dados, eliminando ambiguidades durante o desenvolvimento.
