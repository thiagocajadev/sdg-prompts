# 01 - Stack Técnica

## Tecnologias Escolhidas

- **Linguagem**: [ex: Go, TS, C#]
- **Framework**: [ex: FastAPI, React, Gin]
- **Banco de Dados**: [ex: PostgreSQL, Redis]

## Racional da Escolha

- Por que escolhemos estas tecnologias em vez de outras?
- Quais são os prós e contras?

## Gestão de Versões (LTS) e Dependências

- Os frameworks e ambientes escolhidos são versões LTS (Long Term Support — com suporte de longo prazo)?
- Qual a estratégia para atualizações contínuas e mitigação de vulnerabilidades (ex: Dependabot, Renovate)?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Stack Técnica

## Tecnologias Escolhidas

Python e MySQL.

## Racional

Porque é o que a equipe sabe usar e é popular.

## Gestão de Versões

Vamos usar a mais nova ou a que funcionar.
```

> **Razão**: Popularidade não justifica decisões críticas de arquitetura. Onde está o balanço de perdas e ganhos (trade-off)?

### ✅ Exemplo Bom

```markdown
# 01 - Stack Técnica

## Tecnologias Escolhidas

Go 1.21, PostgreSQL 15, Redis 7.

## Racional da Escolha

O Go foi escolhido pela performance em concorrência (Goroutines) necessária para o processamento de 5k RPS, e o PostgreSQL pela consistência ACID em transações financeiras críticas.

## Gestão de Versões

- **Ambientes**: Somente versões pares do Node.js (ex: v20) e Go em suas versões suportadas.
- **Atualizações Automáticas**: Dependabot configurado via `.github/dependabot.yml` para atualizações de segurança semanais.
```

> **Razão**: Justifica a escolha baseada em requisitos não-funcionais (concorrência e consistência).
