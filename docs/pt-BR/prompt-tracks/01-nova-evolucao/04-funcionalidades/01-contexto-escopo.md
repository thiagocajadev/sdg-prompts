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
# 01 - Contexto e Escopo: Integração com Stripe

## User Story

Como cliente assinado, desejo alterar meu cartão de crédito para que minhas cobranças futuras ocorram em um novo método de pagamento.

## Critérios de Aceitação

- [x] O usuário deve visualizar apenas os 4 últimos dígitos do cartão atual.
- [x] A validação do novo cartão deve ocorrer em tempo real via API do Stripe.

## Fora do Escopo

Não permitiremos a remoção do único cartão ativo sem a inserção de um substituto.
```

> **Razão**: Define o comportamento esperado e as restrições, protegendo a regra de negócio de cobrança.
