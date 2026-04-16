# 13 - Plano de Recuperação de Desastres (DR / BCP)

Falhas críticas em provedores de nuvem ocorrem anualmente. Incidentes de "DROP TABLE" e *Ransomware* ocorrem a cada hora. Desenhar com mentalidade SRE exige que documentemos como o *software volta à vida* após a perda de uma região inteira.

## Objetivos Críticos de Resgate

- [ ] **RTO (Recovery Time Objective)**: Tempo prometido ao C-Level para trazer os sistemas principais de volta (ex: < 4 horas)?
- [ ] **RPO (Recovery Point Objective)**: Quantos minutos ou horas de dados de vendas a empresa aceita "perder" se o banco principal cair? (Ponto ótimo de backup).

## Multi-Zona e Redundância a Frio

- Como sua infraestrutura responde à falha de uma *Availability Zone (AZ)* inteira?
- Os scripts de Terraform (IaC - Infraestrutura como Código) possuem o estado pronto para subir outro datacenter na zona *US-East-2* caso a *US-East-1* falhe permanentemente (Arquitetura a frio / Standby)?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Recuperação de Desastres (DR)

Nosso banco MySQL tira um snapshot na AWS todo dia meia-noite. E temos o Terraform do cluster K8S pronto.
```

> **Razão**: Se a região cair ao meio-dia, você acabou de jogar *12 horas de faturamento da manhã no lixo* (inaceitável para o CEO). Você está cobrindo o mínimo, mas como a equipe sobe esse Terraform quando o alerta toca?

### ✅ Exemplo Bom

```markdown
# Recuperação do Módulo "Transações V2"

- **RTO (Alvo de Retorno):** `No máximo 2 horas` – O Banco Aurora utiliza Auto-Failover (< 60 segundos). O cluster ECS possui Autoscaling multi-zonal e subirá containers em *eu-west-1b* se a *1a* cair.
- **RPO (Aceitação de Dados):** `No máximo 5 minutos` – Banco possui Backup Contínuo (AWS PITR - Point-in-Time Recovery). No pior cenário, perdemos apenas os logs transacionais dos últimos 4.9 minutos.
```

> **Razão**: O documento tranquiliza investidores e lideranças de que as leis de SLA corporativo e RPOs curtos foram incorporados ao software antes dele ser construído e precificado.
