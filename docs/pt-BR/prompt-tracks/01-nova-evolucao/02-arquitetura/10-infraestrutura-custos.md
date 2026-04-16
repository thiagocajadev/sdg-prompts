# 10 - Infraestrutura e Custos (FinOps)

## Estratégia de Nuvem e Provisionamento

- [ ] **Provedor**: [ex: AWS, Google Cloud, Azure, Vercel].
- [ ] **Provisionamento**: [ex: Terraform, CloudFormation, Manual via Console].
- [ ] **Serviços**: [ex: Serverless, Kubernetes, Instâncias Dedicadas].

## Gestão de Custos (FinOps)

- Estimativa de custo mensal inicial.
- Como escalaremos os custos conforme o uso (Unit Economics)?
- Alertas de orçamento (Billing Alerts) configurados?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 10 - Infraestrutura e Custos

O app vai rodar na Amazon (AWS). O custo vai ser baixo no começo porque não temos muitos usuários.
```

> **Razão**: Vago. O que é "baixo"? Se um processo travar e consumir recursos infinitamente, como saberemos o custo?

### ✅ Exemplo Bom

```markdown
# 10 - Infraestrutura e Custos: Projeto V3

## Provedor e Serviços

- **Infra**: AWS utilizando **Terraform (IaC)** para garantir que o ambiente de Staging seja idêntico ao de Produção.
- **Compute**: AWS Lambda (Serverless) para as funções de API, visando custo zero quando não houver tráfego.

## FinOps

- **Estimativa**: Esperamos gastar menos de $50/mês para os primeiros 10 mil usuários ativos (MAU).
- **Controle**: Alerta de Billing configurado para disparar um e-mail ao chegar em $10 (investigação) e $40 (alerta crítico).
```

> **Razão**: Define o método de provisionamento (IaC) e estabelece limites financeiros reais, protegendo o orçamento do projeto.
