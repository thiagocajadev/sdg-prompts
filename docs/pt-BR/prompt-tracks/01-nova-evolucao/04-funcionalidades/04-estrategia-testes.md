# 04 - Estratégia de Testes

## Planilha de Cobertura

- [ ] **Testes Unitários**: Validação de funções puras e regras de negócio isoladas.
- [ ] **Testes de Integração**: Comunicação entre a aplicação e o banco de dados ou APIs externas.
- [ ] **Testes E2E (End-to-End)**: Simulação completa da jornada do usuário no navegador ou app.

## Casos de Teste (Cenários)

- **Caminho Feliz**: [Descreva o cenário de sucesso].
- **Caminho de Erro**: [Descreva os principais cenários de falha esperados].

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 04 - Estratégia de Testes

Vou testar o login no manual e depois fazer uns testes unitários.
```

> **Razão**: Teste manual não é escalável e não garante que mudanças futuras não quebrem o que já funciona (regressão). Quais são os cenários de erro (ex: senha errada, usuário bloqueado)?

### ✅ Exemplo Bom

```markdown
# SPEC-004: Estratégia de Testes (Checkout)

## 1. Contexto
Plano de validação para o fluxo de checkout, garantindo resiliência em falhas e precisão nos cálculos.

## 2. Resultados Esperados (Success Metrics)
* Cobritura de 90% para lógica de impostos (ICMS).
* Zero falhas de integração não detectadas entre Checkout e Stripe.

## 3. Escopo e Cenários (User Stories)
* **Unitário:** Cálculo de ICMS para diferentes estados (SP, RJ, MG).
* **Integração:** Validação de webhook do Stripe e mudança de status do pedido.
* **E2E:** Jornada completa do usuário desde o carrinho até a tela de sucesso.

## 4. Restrições e Regras de Negócio
* Utilizar cartão de teste do Stripe (`4242...`) para evitar transações reais.
* Mocks obrigatórios para serviços externos em testes unitários.

## 5. Fora de Escopo
* Testes de carga (> 1000 transações/segundo).
* Testes manuais de interface visual.

## 6. Definição de Pronto (DoD)
- [ ] Suíte de testes unitários passando no CI.
- [ ] Teste E2E cobrindo o "Caminho Feliz" finalizado.
- [ ] Script de população de dados de teste criado.
```

> **Razão**: Define níveis de teste (Unitário, Integração, E2E) e especifica dados reais para simular cenários complexos, garantindo a robustez da entrega.
