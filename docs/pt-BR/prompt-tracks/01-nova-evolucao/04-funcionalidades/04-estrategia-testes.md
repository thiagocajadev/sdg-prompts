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
# 04 - Estratégia de Testes: Sistema de Checkout

## Cenários de Teste

- **Unitário**: Testar se o cálculo de ICMS está correto para diferentes estados (cenários: SP, RJ, MG).
- **Integração**: Validar se o status do pedido muda para `pago` após o recebimento do webhook do Stripe.
- **E2E (Caminho Feliz)**: Usuário adiciona item -> Preenche endereço -> Paga -> Recebe tela de sucesso.

## Dados de Teste

Utilizaremos o cartão de teste do Stripe `4242...` para garantir que o fluxo de pagamento real não seja disparado.
```

> **Razão**: Define níveis de teste (Unitário, Integração, E2E) e especifica dados reais para simular cenários complexos, garantindo a robustez da entrega.
