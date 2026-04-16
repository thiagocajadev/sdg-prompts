# 03 - Integrações de Terceiros e Chaves Sensíveis

APIs e serviços de terceiros são os "blocos mágicos" que resolvem 80% da lógica de negócio em produtos Lite. Em vez de reinventar um servidor de envio de e-mail ou construir um sistema de cobrança complexo, a Landing Page ou MVP consumirá APIs prontas (como Resend, Mailchimp e Stripe).

## Conectores do Projeto e Variáveis de Ambiente

- Você enviará e-mails? Qual fornecedor (provider)? Como o React na Vercel chamará a API sem vazar dados de acesso no Frontend? (Dica: Next.js API Routes).
- Pagamento e Checkout: Qual Gateway de pagamento utilizaremos que não exija conformidade com normas complexas de segurança (PCI compliance)?
- O sistema de autenticação (Auth) é próprio (ex: Supabase, Auth0) ou teremos Google Login?

## Mapeamento de Credenciais (Vault/Env)

- NÃO armazene nada sensível no código (hardcoded) ou no Git. As integrações devem utilizar e declarar a taxonomia de variáveis de ambiente (`.env`) esperada pelo projeto.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Integração

Disparamos o formulário para o mailchimp da empresa. O Front-end faz um fetch com o token.
```

> **Razão**: Perigo grave de segurança e falta de maturidade técnica. O Frontend (lado do cliente) não deve carregar chaves do Mailchimp, caso contrário, qualquer visitante poderia capturar seu token de Newsletter e deletar sua base de clientes livremente.

### ✅ Exemplo Bom

```markdown
# SPEC-008: Integrações da Sorriso Feliz

## 1. Contexto
Conectar a Landing Page com serviços de e-mail e pagamento para viabilizar a operação digital de forma segura.

## 2. Resultados Esperados (Success Metrics)
* 100% de e-mails entregues na caixa de entrada da recepção via Resend.
* Validação de webhooks com 100% de integridade e assinatura verificada.

## 3. Escopo e Cenários (User Stories)
* **E-mail:** Integração com Resend via Edge API Routes (Segurança).
* **Pagamento:** Stripe Hosted Checkout para serviços premium e consultas.

## 4. Restrições e Regras de Negócio
* Nunca expor a `RESEND_API_KEY` no lado do cliente (Frontend).
* Utilizar `NEXT_PUBLIC_PUBLISHABLE_KEY` para o frontend e segredos no backend.
* Validar assinatura de webhooks (`STRIPE_WEBHOOK_SECRET`) obrigatoriamente.

## 5. Fora de Escopo
* Integração com Mailchimp ou outros CRMs nesta fase inicial.
* Pagamentos recorrentes (Assinaturas complexas).

## 6. Definição de Pronto (DoD)
- [ ] Rota `POST /api/leads` funcional e validada em produção.
- [ ] Validação de segredos em produção via painel Vercel.
- [ ] Teste de ponta a ponta de envio de e-mail bem-sucedido.
```

> **Razão**: Mapeia exatamente quais frentes de terceiros são utilizadas, como as chaves serão chamadas e protege o projeto contra falhas críticas de segurança que poderiam arruinar o MVP.
