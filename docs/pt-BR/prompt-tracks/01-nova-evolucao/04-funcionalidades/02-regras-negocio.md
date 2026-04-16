# 02 - Regras de Negócio

## Lógica Principal

- Descreva o motor da funcionalidade. Como o sistema processa a informação?

## Fluxogramas e Decisões

- Utilize Mermaid.js ou texto estruturado para definir caminhos de `IF/THEN`.

## Edge Cases (Casos de Exceção)

- [ ] O que acontece se a API externa estiver fora do ar?
- [ ] O que acontece se o usuário tentar burlar uma restrição?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Regras de Negócio

O sistema valida o cupom e dá o desconto.
```

> **Razão**: Vago. O desconto é sobre o total ou o item? Cupons são cumulativos? O que acontece se o cupom estiver expirado?

### ✅ Exemplo Bom

```markdown
# SPEC-002: Sistema de Cupons de Desconto

## 1. Contexto
Implementar um motor de cupons para campanhas de marketing, permitindo descontos percentuais controlados por validade e uso.

## 2. Resultados Esperados (Success Metrics)
* Aumento de 10% no volume de vendas em campanhas promocionais.
* Zero pedidos com valor negativo devido a erros de cálculo.

## 3. Escopo e Cenários (User Stories)
* **Cenário A:** Aplicação de cupom válido sobre o carrinho.
* **Cenário B:** Tentativa de uso de cupom expirado ou sem estoque.

## 4. Restrições e Regras de Negócio
* Desconto aplicado apenas sobre o valor dos produtos (exclui frete).
* Validar `usage_limit` e datas `start_date` / `end_date`.
* Retornar `422` com mensagem clara se o cupom estiver inválido.

## 5. Fora de Escopo
* Cupons cumulativos (apenas um cupom por pedido).
* Descontos progressivos baseados no valor total.

## 6. Definição de Pronto (DoD)
- [ ] Lógica de cálculo verificada com testes unitários.
- [ ] API de aplicação de cupom implementada.
- [ ] Logs de auditoria para cada cupom gerado.
```

> **Razão**: Define regras matemáticas e lógicas granulares, facilitando a implementação de testes que cubram todos os cenários sem adivinhação.
