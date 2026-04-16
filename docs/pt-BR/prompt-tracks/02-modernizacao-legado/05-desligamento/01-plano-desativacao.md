# 01 - Plano de Desativação (Sunset Plan)

O Plano de Desativação (Sunset Plan) é a etapa final da modernização de um sistema legado (Brownfield). Assim que 100% das rotas e dados estiverem no sistema novo, o antigo TEM que ser desligado. Código sem manutenção deixado online é a principal porta de entrada para falhas de segurança na empresa.

## Fase 1: Isolamento e Modos de Somente Leitura

- **Redirecionamento**: Todo o tráfego do domínio legado está agora (via proxy/DNS) trafegando estritamente para o software novo?
- **Congelamento**: O banco de dados legado foi travado como `Read-Only` para garantir que nenhum usuário ou rotina esquecida continue criando lixo técnico?

## Fase 2: Terminação e Desativação Física

- **Dependências Órfãs**: Deletamos todos os crons e rotinas agendadas (background jobs)?
- **O Fim**: Desligamento oficial da máquina virtual (EC2), cluster ou app service legado.
- **Retenção de Dados e Backups**: O dump final do banco legado foi armazenado em um local frio (ex: Amazon S3 Glacier) pelo período de retenção legal antes de deletar o banco quente na nuvem?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Shutdown

O sistema novo lançou semana passada. Paramos de usar o velho. No final do ano o sysadmin apaga o servidor.
```

> **Razão**: Extremamente perigoso. O que garante que nenhum cliente B2B continue usando a API do backend antigo? Se o dashboard velho tiver vulnerabilidades e continuar rodando sem manutenção até o fim do ano, hackers usarão essa ponte para roubar dados (Shadow IT).

### ✅ Exemplo Bom

```markdown
# Plano de Desativação: Módulo de Vendas V1

## Fase 1: Isolamento

- As rotas `/v1/sales` foram configuradas via Nginx para disparar um `301 Redirect` para o novo `/v2/sales`.
- O DB MySQL Legado teve sua senha de `writer` revogada, operando apenas como uma `read-only replica`. Ficará assim por 15 dias (Período de Monitoramento de Fumaça).

## Fase 2: Desativação Física (20/08/2026)

- Desligamento de todas as instâncias EC2 V1 identificadas sob a Tag AWS `env:legacy-sales`.
- Dump completo gerado e enviado ao **S3 Deep Glacier** com regra de Lifecycle para expurgo definitivo em 5 anos (Conformidade Fiscal/Legal).
- Drop definitivo do banco RDS legado, resultando em uma economia de $850/mês de Cloud TCO.
```

> **Razão**: Profissionalismo puro. Desligar um software é tão técnico quanto construí-lo. Mitigamos falhas, cuidamos da retenção contábil de dados e celebramos a economia exata de dólares em infraestrutura.
