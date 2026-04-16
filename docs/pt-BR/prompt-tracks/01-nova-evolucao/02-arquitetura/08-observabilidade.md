# 08 - Observabilidade

## Pilares de Monitoramento

- [ ] **Logging Centralizado**: [ex: ELK Stack, Datadog Logs, CloudWatch].
- [ ] **Métricas de Infra e Negócio**: [ex: Prometheus + Grafana].
- [ ] **Rastreamento Distribuído (Tracing)**: [ex: OpenTelemetry, Jaeger].

## Estratégia de Alertas

- Quando o sistema deve notificar os desenvolvedores? (ex: Erros 5xx > 1% em 5 minutos).
- Onde os alertas são recebidos? (ex: Canal do Slack #alerts-prod, PagerDuty).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 08 - Observabilidade

Nós usamos logs no console para ver o que está acontecendo.
```

> **Razão**: Insustentável em produção. `stdout` é efêmero e não permite análise histórica ou correlação de erros entre diferentes serviços.

### ✅ Good Example

```markdown
# 08 - Observabilidade: Módulo de Checkout

## Estratégia

- **Log Centralizado**: Utilizaremos **Datadog Logs**. Cada rastro de log deve incluir o `correlation-id` da requisição para facilitar o rastreio fim-a-fim.
- **Traces**: Implementaremos o **OpenTelemetry (OTEL)** para identificar gargalos de latência entre o Backend e o Banco de Dados.

## Alertas Críticos

- **Pico de Erros**: Se a taxa de erros `500` for maior que 2% ao longo de 5 minutos, um alerta urgente será enviado para o canal de Ops no Slack.
```

> **Razão**: Estabelece padrões de rastreabilidade (Correlation ID) e regras automáticas de alerta que protegem a saúde do ambiente de produção.
