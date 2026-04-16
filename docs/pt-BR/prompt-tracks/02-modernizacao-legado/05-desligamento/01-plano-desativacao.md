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
# SPEC-015: Desativação do Módulo de Vendas V1

## 1. Contexto
Desligamento definitivo do software legado para eliminar riscos de segurança e reduzir o custo de infraestrutura (TCO).

## 2. Resultados Esperados (Success Metrics)
* Economia imediata de $850/mês em custos de nuvem.
* 100% de tráfego redirecionado via 301 para a versão V2.

## 3. Escopo e Cenários (User Stories)
* **Isolamento:** Revogar acesso de escrita no DB e configurar redirecionamento Nginx.
* **Desativação:** Desligamento de instâncias EC2 e remoção definitiva do banco RDS.

## 4. Restrições e Regras de Negócio
* Período de monitoramento de "Somente Leitura" por 15 dias.
* Dump final obrigatório no S3 Deep Glacier para retenção legal (5 anos).

## 5. Fora de Escopo
* Desativação de outros módulos legados (CRM, Logística).
* Migração de logs de movimentação financeira (mantidos no Glacier).

## 6. Definição de Pronto (DoD)
- [ ] Nginx retornando 301 para todas as rotas V1.
- [ ] RDS deletado após validação do dump no Glacier.
- [ ] Instâncias legadas terminadas.
```

> **Razão**: Profissionalismo puro. Desligar um software é tão técnico quanto construí-lo. Mitigamos falhas, cuidamos da retenção contábil de dados e celebramos a economia exata de dólares em infraestrutura.
