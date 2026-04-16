# 03 - Controle de Versão e Gestão

## Estratégia de Branches (Versionamento)

- Qual fluxo padrão será adotado (GitHub Flow, GitFlow, Trunk-Based)?
- Quais as regras de nomenclatura para criação de novas branches?

## Padrão de Commit

- O projeto adotará _Conventional Commits_?
- Haverá proteção passiva (**Revisão do desenvolvedor**) ou proteção ativa (Husky/Commitlint antes do push)?

## Rastreabilidade e Gestão de Tarefas

- Qual é a ferramenta oficial de rastreio (Jira, Linear, Azure DevOps)?
- Como o PR (Pull Request) se vincula à tarefa de negócio descrita na especificação?
- Qual a regra de transição de status dos cards quando o código é integrado (merged)?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - Controle de Versão e Gestão

## Estratégia de Branches

Vamos usar Git básico. Cria a branch com a funcionalidade e depois joga na master.

## Padrão de Commit

Escreva algo entendível, ex: "subindo correções da tela de login" e "wip".

## Rastreabilidade

Quando a tarefa acabar, avise a gerência no Slack e mova o card do Trello para Done.
```

> **Razão**: Falta total de governança e rastreabilidade. Em pouco tempo, o repositório terá conflitos graves de integração, impossibilidade de gerar *Changelogs* automáticos e a gerência não saberá qual código em produção pertence a qual especificação.

### ✅ Exemplo Bom

```markdown
# 03 - Controle de Versão e Gestão

## Estratégia de Branches (Versionamento)

- **Fluxo**: GitHub Flow (Trunk-Based simplificado).
- **Nomenclatura**: Obrigatório seguir o padrão e o ID da spec (ex: `feat/AUTH-102-implement-oauth`, `fix/AUTH-105-token-timeout`).

## Padrão de Commit

- **Padrão**: Conformidade estrita com *Conventional Commits* (`feat:`, `fix:`, `chore:`, `refactor:`).
- **Garantia**: Uso de `Husky` + `Commitlint` bloqueando commits fora do padrão via *pre-commit*.

## Rastreabilidade e Gestão de Tarefas

- **Rastreio**: Linear (Issue Tracker).
- **Vinculação**: Todo PR deve conter o ID de rastreio no título (ex: "[AUTH-102] Implementar OAuth via Google").
- **Fluxo**: Integração do GitHub com Linear move os tickets para `In Review` na abertura do PR e para `Done` após o *Merge*.
```

> **Razão**: Cria uma trilha de auditoria perfeita (*End-to-End*). Cada linha de código alterada está vinculada a uma decisão de negócio e aprovação de PR. Além disso, releases semânticos podem ser publicados de forma 100% automática pelo CI/CD com base nos *Conventional Commits*.
