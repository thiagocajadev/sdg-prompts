# 02 - Padrões de Qualidade

A qualidade não deve ser subjetiva. Ela deve ser auditável de forma automática pelo seu pipeline e pela revisão por pares.

## Critérios de Qualidade de Código

- [ ] **Linter**: Configurado para bloquear estilos de código fora do padrão.
- [ ] **Análise Estática (SonarQube)**: Bloqueio de dívidas técnicas e bugs críticos potenciais.
- [ ] **Cobertura de Código (Code Coverage)**: Nível mínimo acordado (ex: 80% das rotas críticas).

## Documentação de Suporte

- O código é autoexplicativo ou possui comentários em lógicas complexas?
- Existe um README atualizado para o módulo?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Padrões de Qualidade

Nós tentamos escrever código limpo e seguir as melhores práticas.
```

> **Razão**: Vago. O que é "código limpo" para um dev, pode não ser para outro. Falta o mecanismo de auditoria automático.

### ✅ Exemplo Bom

```markdown
# 02 - Padrões de Qualidade: Core API

## Auditoria Automática

- **Linting**: Configuramos o `ESLint` com o preset `AirBnB` rígido. O pipeline falha se houver um erro de estilo.
- **Complexidade Ciclomática**: Bloquearemos funções com score superior a 10 no SonarCloud (evita funções gigantes e difíceis de testar).

## Cobertura de Testes

Focaremos em 100% de cobertura nos serviços de cálculo financeiro. Áreas de UI podem ter cobertura menor (50%), focada nos fluxos de usuário felizes.
```

> **Razão**: Define ferramentas (ESLint, SonarCloud) e métricas numéricas, permitindo que a qualidade seja garantida sem depender apenas da vontade individual.
