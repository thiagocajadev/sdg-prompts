# 02 - Post-mortems de Incidentes (Análise de Quedas)

## Timeline (Linha do Tempo) e Impacto

- Qual foi a linha do tempo exata desde o início da falha sistêmica até a recuperação total (*Time to Recovery*)?
- Quantos usuários ou transações foram impactados pelo fora do ar (*downtime*)? Havia alertas cobrindo este tipo específico de falha?

## Análise de Causa Raiz ("Os 5 Porquês")

- Como o sistema quebrou? (Evite apontar dedos para pessoas *"Alguém errou"*; foque no processo *"O pipeline deixou passar"*).
- Qual foi o "gatilho oculto" que não apareceu no ambiente de Staging ou Homologação?

## Plano de Ação (Action Items)

- O que o time **precisa implementar** no código, na infraestrutura ou no CI/CD para que esta falha **nunca** mais aconteça de forma estrutural no futuro?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Post-Mortem: Banco de Dados Caiu

## Impacto

Ficou ruim à tarde e os clientes reclamaram.

## Causa Raiz

O João rodou o comando de migração errado na produção.

## Plano de Ação

O João vai tomar mais cuidado e fará um curso de SQL.
```

> **Razão**: Cultura de culpa clássica. Condenar o desenvolvedor não resolve a fragilidade sistêmica. Em 6 meses, outra pessoa rodará o comando errado novamente porque o pipeline continua frouxo.

### ✅ Exemplo Bom

```markdown
# 02 - Post-Mortem: Queda do Banco Mestre (DB-Outage)

## Timeline

- `14:02 PM`: Uso de CPU do PostgreSQL atinge 100%.
- `14:05 PM`: Gateway começa a retornar Status 504 no App para ~4.500 usuários conectados.
- `14:26 PM`: Rollback manual do *Target Group*, restaurado à normalidade. Duração de **24 min**.

## Análise de Causa Raiz

1. **Por que a CPU explodiu?** Query N+1 de um relatório pesado subido hoje de manhã.
2. **Por que passou no CI?** Falta de métricas de volume de dados no pipeline de *Load Test* (Teste de Carga).

## Plano de Ação

- **[Amanhã]**: Adicionar limite global de paginação obrigatório `limit(50)` na API Base.
- **[Até Sexta]**: Integrar `k6` ao CI com um banco clonado a 10% do volume, bloqueando qualquer query superior a 500ms.
```

> **Razão**: Profissionaliza a falha. Sem caça às bruxas, a queda se torna a semente genética de uma proteção automatizada no futuro da infraestrutura da empresa.
