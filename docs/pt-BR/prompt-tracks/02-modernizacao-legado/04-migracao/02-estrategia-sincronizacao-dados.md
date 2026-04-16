# 02 - Estratégia de Sincronização de Dados

## Modelo de Sincronia (Sincronização)

- **Unidirecional**: O legado envia dados para o novo sistema.
- **Bidirecional**: Mudanças em um sistema são refletidas no outro em tempo real.
- **Double-Write**: O código da aplicação escreve simultaneamente nos dois bancos de dados.

## Trilha de ETL (Extract, Transform, Load)

- Qual ferramenta ou script garantirá a conversão dos dados antigos (ex: string formatada `"1"`) para a nova tipagem no banco (Boolean puro)?
- Haverá uma tabela espelho ou *Read-replica* para desonerar o banco legado principal durante a migração?

## Rollback e Descarte do Legado

- Qual o critério e o prazo estimado para "desligar" a escrita no sistema antigo com segurança?
- Como um rollback de emergência re-sincronizará dados que já foram persistidos apenas no banco moderno?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Sincronização de Dados

## Modelo de Sincronia

Vamos continuar gravando na nova API e torcer para o sistema legado não precisar ler isso.

## Trilha ETL

Copiar os dados do MySQL usando um script em Python no final do dia.
```

> **Razão**: Como a operação continua online enquanto o script Python roda livremente? Se o script falhar no meio do caminho, quebramos os dois bancos simultaneamente.

### ✅ Exemplo Bom

```markdown
# 02 - Sincronização de Dados

## Modelo de Sincronia

- **Bidirecional Contínua**: Utilizaremos o **Debezium (CDC - Change Data Capture)** para ouvir as alterações do MongoDB (Legado) para o PostgreSQL (Novo) via Kafka. O microserviço de usuários disparará o inverso via API Legada no callback.

## Trilha ETL

- **Heavy Load Batch**: Migrações históricas pesadas serão feitas às 03:00 AM (Domingo) através de rotinas otimizadas via AWS Glue, mapeando colunas obsoletas para `.jsonb`.

## Descarte

- **Período de Banco Sombrio (Shadow DB)**: O banco antigo rodará em modo *Read-Only* por 14 dias pós-migração. Se o PostgreSQL quebrar de forma irreversível, usamos um script de Glue inverso e viramos a chave do roteador de volta para o MongoDB.
```

> **Razão**: Abordagem tolerante a falhas. Baseia-se no modelo industrial de CDC (eventos em tempo real), reduzindo drasticamente as inconsistências para os usuários do sistema misto.
