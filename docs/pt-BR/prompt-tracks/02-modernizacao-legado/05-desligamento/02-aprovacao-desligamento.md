# 02 - Aprovação: Sunset e Desativação Final

## Checklist de Artefatos

- [ ] 01-plano-desativacao.md (Evidências de Read-Only aplicado e redirecionamentos DNS).

## Aprovação Executiva (A Despedida)

- **Líder Técnico da Migração**: [Assinatura/Data]
- **Time de Custos/Financeiro (FinOps)**: [Assinatura/Data]
- **Dono do Produto (PM)**: [Assinatura/Data]

## Definição de Conclusão da Modernização

- [ ] Domínio legado não roteia mais tráfego ativo (uso 0 status no API Gateway).
- [ ] Backup final exportado para retenção (Cold Storage).
- [ ] Faturas (Billing) confirmam que instâncias legadas foram removidas do custo de nuvem.
- [ ] DNS antigo apontando oficialmente 100% para o novo Ingress Controller.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Aprovação Sunset

## Checklist

- [x] Desligamos tudo.

## Definição de Conclusão

- [x] O sistema parou de cobrar.
```

> **Razão**: Desligou "quando" e "como"? E os 5 anos de backups exigidos por lei? A migração falhou em um ponto silencioso.

### ✅ Exemplo Bom

```markdown
# Aprovação Sunset: Extinção Completa

## Aprovações Finais

- **Tech Lead**: Renato Vanes (20/09/2026) confirmou via Datadog 0 RPS no Node Legado por 30 dias ininterruptos.
- **FinOps**: Claire River (21/09/2026) provou a remoção do cluster AKS antigo e do banco RDS T3 no painel de Custos. Redução de ~$2.500 validada!

## Definição de Conclusão (O Troféu)

- [x] Retenção em Glacier aprovada pelo Chief Legal Officer.
- [x] DNS CNAME legado alterado para ALB v2.

## Cerimônia de Fim de Projeto

Modernização oficialmente Encerrada. O repositório GitHub legado `vendas-delphi-legacy` foi Arquivado. 🚀
```

> **Razão**: Encerramento monumental de um trabalho de nível Staff. Sem pontas soltas, redução de custos oficial com FinOps endossando o ROI do projeto, arquivos mortos seguros e repo "Archived". Todos celebram uma transição blindada.
