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
# 02 - Regras de Negócio: Sistema de Cupons

## Lógica de Desconto

1. Validar se o cupom existe e está com o status `ativo`.
2. Verificar se a data atual está entre `start_date` e `end_date`.
3. Aplicar o desconto `X%` apenas sobre o valor dos produtos (excluindo frete).

## Casos de Exceção

- **Cupom Expirado**: Retornar erro `422 Unprocessable Entity` com a mensagem "Este cupom expirou".
- **Tentativa de Reuso**: Se `usage_limit` do usuário for 0, bloquear aplicação.
```

> **Razão**: Define regras matemáticas e lógicas granulares, facilitando a implementação de testes que cubram todos os cenários sem adivinhação.
