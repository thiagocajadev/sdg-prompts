# 03 - Aprovação da Migração Operacional

## Checklist de Artefatos

- [ ] 01-roadmap-migracao.md (Definido)
- [ ] 02-estrategia-sincronizacao-dados.md (Testado com sucesso n-vezes)

## Aprovação Operacional

- **SRE / DevOps**: [Assinatura/Data]
- **Time de Operações / Suporte**: [Assinatura/Data]

## Definição de Prontidão (Ready for Rollout)

- [ ] *Dry-run* (carga fantasma) da migração de dados concluída com sucesso.
- [ ] Plano de rollback testado e métricas de tempo limite aprovadas (ex: MTTR < 10min).
- [ ] Janela de manutenção comunicada oficialmente aos stakeholders corporativos.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - Aprovação da Migração

## Checklist

- [x] Migrar e re-testar.

## Definição de Prontidão

- [x] O script está na máquina e pronto para rodar e virar as APIs.
```

> **Razão**: Como você prova que o script de migração não corrompe o Banco B? E pior, se corromper, como você volta o usuário para um Banco A intacto?

### ✅ Exemplo Bom

```markdown
# 03 - Aprovação da Migração

## Aprovação Operacional

- **DevOps**: Bruno Costa (Aprovado em 20/07/2026)

## Definição de Prontidão

- [x] 01-roadmap-migracao.md (Janela definida para Sábado 02:00 AM)
- [x] 02-estrategia-sincronizacao-dados.md (Sincronização bidirecional via Kafka testada)
- [x] Rollback testado em ambiente isolado (O roteador DNS leva 59 segundos para cancelar a migração caso o health check da infra nova fique vermelho).
```

> **Razão**: Evidência de alta maturidade operacional. Os tempos de sincronização de dados e acionamento de rollback são cronometrados, convertendo o momento caótico e crítico de um deploy legado em um procedimento controlado.
