# 01 - Contexto e Escopo

## Visão Geral

- Qual é o valor de negócio imediato desta funcionalidade?
- Quem solicitou (Stakeholder) e quem é o usuário primário?

## User Stories (Histórias de Usuário)

- [ ] **Como** [papel], **eu quero** [ação], **para que** [valor].

## Critérios de Aceitação

- [ ] Critério 1 (ex: O usuário deve receber um e-mail de confirmação).
- [ ] Critério 2 (ex: O botão de delete deve estar desativado para usuários 'Viewer').

## Fora do Escopo (Non-Goals)

- O que não será entregue agora para garantir a velocidade do lançamento?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Contexto e Escopo: Tela de Login

Queremos que o usuário entre no sistema.
```

> **Razão**: Vago. Não define critérios de aceitação (ex: o que acontece se a senha estiver errada?) nem o que está fora do escopo (ex: recuperação de senha por SMS).

### ✅ Exemplo Bom

```markdown
# SPEC-001: Integração com Stripe (Pagamentos)

## 1. Contexto
Permitir que clientes logados alterem seu cartão de crédito para garantir que cobranças futuras ocorram sem interrupções no serviço.

## 2. Resultados Esperados (Success Metrics)
* Redução de 5% no churn causado por falhas de pagamento.
* Taxa de sucesso de 99% nas validações de novos cartões.

## 3. Escopo e Cenários (User Stories)
* **Cenário A:** Usuário atualiza cartão com sucesso.
* **User Story:** Como cliente assinado, desejo alterar meu cartão de crédito para que minhas cobranças ocorram em um novo método de pagamento.

## 4. Restrições e Regras de Negócio
* Validação do cartão em tempo real via API do Stripe.
* Mostrar apenas os últimos 4 dígitos do cartão atual por segurança.

## 5. Fora de Escopo
* Remoção do único cartão ativo sem inserção de um substituto.
* Suporte a Boleto ou Pix nesta fase.

## 6. Definição de Pronto (DoD)
- [ ] Interface de atualização de cartão funcional.
- [ ] Webhook de confirmação do Stripe integrado.
- [ ] Testes de validação de cartão passando.
```

> **Razão**: Define o comportamento esperado e as restrições, protegendo a regra de negócio de cobrança.
