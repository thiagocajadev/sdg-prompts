# 03 - Template de ADR (Architectural Decision Record)

Este modelo padrão deve ser utilizado para documentar toda e qualquer decisão arquitetural estruturante ao longo da vida do projeto. Um ADR (Architectural Decision Record — registro de decisão arquitetural) garante que o contexto histórico da decisão (Por que não usamos a ferramenta X?) seja preservado para sempre.

## Contexto e Problema

- **Status:** [Proposto | Aceito | Rejeitado | Obsoleto]
- **Qual a dor técnica atual?** O que motivou o time a buscar uma nova solução arquitetural ou inserir uma nova dependência pesada?

## Opções Consideradas

- Opção 1: [Nome e Breve Descrição] (Prós e Contras)
- Opção 2: [Nome e Breve Descrição] (Prós e Contras)

## Decisão (O que iremos fazer)

- A Opção X foi a escolhida por causa de [Racional].

## Consequências e Trade-offs (Ganhos e Perdas)

- O que perdemos com essa decisão? (ex: +Custo, curva de aprendizado mais íngreme).
- O que ganhamos? (ex: +Escalabilidade, -Latência).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# ADR: Migrar para Postgres

**Status:** Feito
Escolhemos o PostgreSQL porque o MySQL estava lento e o CTO mandou. Vamos ganhar velocidade.
```

> **Razão**: Falta métricas. "Estava lento" não é uma métrica. Quais foram os trade-offs avaliados? Quais versões de PG vs MySQL operaram sob estresse? Quem herdar isso no futuro não saberá o peso *real* da decisão técnica.

### ✅ Exemplo Bom

```markdown
# ADR: Migrar Fila RabbitMQ para AWS SQS

**Status:** Aceito

## Contexto

Temos 1M de jobs/dia e o cluster RabbitMQ on-premise gerenciado por nós consome 20h/mês de DevOps apenas em patches e monitoramento de OOM (Out-of-memory).

## Opções Consideradas

- 1. **RabbitMQ Cloud Pago**: Custo de $500/mês. Preserva nosso código atual.
- 2. **AWS SQS**: Custo estimado de $8/mês graças ao baixo throughput; exige reescrita da interface `IMessageQueue` do backend.

## Decisão

A Opção 2 (SQS) foi a escolhida devido à margem de custo imbatível a longo prazo e por ser totalmente serverless.

## Consequências

- Ganhos: Zero horas em manutenção de infra, custo reduzido de $500 para $8.
- Perdas: Refatoração estimada em 1 sprint (~12 pontos) no Backend para troca de bibliotecas.
```

> **Razão**: Histórico perfeito. Alguém daqui a 3 anos lê este documento e entende perfeitamente as pressões de custo e operação da época. Ninguém irá debater e reacender o desejo de voltar para o RabbitMQ sem um argumento mais sólido.
