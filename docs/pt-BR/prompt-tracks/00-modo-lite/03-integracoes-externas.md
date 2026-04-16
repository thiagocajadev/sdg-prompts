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
# Integrações de API da Sorriso Feliz

## E-mails Transacionais (Formulário para a Clínica)

- **Provedor:** Utilizaremos a [API do Resend](https://resend.com) no domínio do cliente `contato@sorrisofeliz.com`.
- **Rotas Seguras:** Criamos um endpoint Serverless (Edge API na Vercel) na rota `POST /api/leads`. O formulário do cliente React chama este endpoint sem nenhum token. O processamento no Node.js (lado do servidor) consumirá o token protegido via variável de ambiente da Vercel e o injetará no Resend: `RESEND_API_KEY`.

## Checkout (Planejado)

- **Gateway:** Quando os clientes pagarem por consultas diretas (Stripe Hosted Checkout), as variáveis públicas serão inseridas em `NEXT_PUBLIC_PUBLISHABLE_KEY`, mas os webhooks retornarão com assinatura criptográfica `STRIPE_WEBHOOK_SECRET` validada em `/api/stripe-webhook`.
```

> **Razão**: Mapeia exatamente quais frentes de terceiros são utilizadas, como as chaves serão chamadas e protege o projeto contra falhas críticas de segurança que poderiam arruinar o MVP.
