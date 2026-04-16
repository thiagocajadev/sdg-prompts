# 03 - Aprovação da Entrega

## Checklist de Prontidão (Production Readiness)

- [ ] Pipeline de CI/CD aprovado.
- [ ] Padrões de qualidade e auditoria automática completos.
- [ ] Documentação de deploy (Manual ou Automática) validada.
- [ ] Equipe de suporte/negócio avisada sobre o lançamento.

## Aprovação Final

- **Líder de Dev**: [Assinatura/Data]
- **Líder de Ops/SRE**: [Assinatura/Data]

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - Aprovação da Entrega

O código está na main e o app está no ar.
```

> **Razão**: Vago. O "estar no ar" não significa que a operação está ciente ou que os logs estão sendo monitorados corretamente.

### ✅ Exemplo Bom

```markdown
# 03 - Aprovação da Entrega: Versão 1.5.0

## Checklist

- [x] Testes de carga validados (suporta 200 req/s).
- [x] Dashboard de monitoramento no Grafana aprovado pelo time de SRE.
- [x] **Rollback Testado**: Verificamos que o sistema retorna à versão anterior em 60 segundos se o deploy falhar.

## Aprovação Final

- **SRE**: Andre Castro (18/05/2026)
```

> **Razão**: Detalhamento técnico que envolve não apenas o código, mas a capacidade operacional de manter o sistema vivo e o seguro em caso de falha (Rollback).
