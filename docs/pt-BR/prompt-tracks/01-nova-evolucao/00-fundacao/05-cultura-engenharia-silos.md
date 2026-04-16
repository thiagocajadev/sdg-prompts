# 05 - Cultura de Engenharia e Silos

## Leis de Engenharia e Princípios

- Quais princípios técnicos regem este projeto (ex: Código Limpo, YAGNI, TDD)?
- Como garantimos a qualidade do código no dia a dia?

## Gestão de Silos e Comunicação

- Silos são áreas isoladas onde o conhecimento fica retido em poucas pessoas. Como evitaremos isso?
- Canais de comunicação oficiais (ex: Slack, Discord, Email).
- Frequência de alinhamentos (ex: Dailies, Weeklies).

## Gestão de Débito Técnico

- Como as decisões rápidas (atalhos) serão registradas e quando serão pagas?
- Uso de `TODO` e `FIXME` no código vinculados a tickets.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 05 - Cultura de Engenharia

## Princípios

Fazer código bom e rápido.

## Comunicação

Falar no WhatsApp quando precisar.
```

> **Razão**: WhatsApp para decisões técnicas gera perda de histórico e silos de informação. "Código bom" é subjetivo.

### ✅ Exemplo Bom

```markdown
# 05 - Cultura de Engenharia

## Princípios

- **YAGNI (You Ain't Gonna Need It):** Não implementaremos funcionalidades "para o futuro".
- **Revisão por Pares:** Nenhum código entra em produção sem pelo menos uma aprovação de outro desenvolvedor.

## Gestão de Silos

- **Documentação viva:** Decisões arquiteturais devem ser registradas como ADRs (Architectural Decision Records) neste repositório.
- **Pareamento:** Incentivamos o Pair Programming (programação em par) em tarefas complexas para espalhar o conhecimento.

## Comunicação

Utilizaremos o Slack como canal assíncrono oficial. Decisões tomadas em chamadas devem ser resumidas em texto no canal do projeto.
```

> **Razão**: Estabelece regras claras que protegem a saúde do projeto a longo prazo e garantem que o conhecimento não fique "preso" na cabeça de um único desenvolvedor.
