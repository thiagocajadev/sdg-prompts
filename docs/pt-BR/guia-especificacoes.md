# Guia de Especificações (Ciclo de tarefas em 5 fases)

O **Guia de Especificações (SDG — Spec-Driven Guide)** estabelece um ciclo de vida padronizado para cada tarefa. O objetivo é garantir que o código seja escrito apenas após a aprovação total da intenção e do plano de implementação.

O ciclo segue cinco fases obrigatórias: **SPEC → PLAN → CODE → TEST → END**.

> [!TIP]
> **Análise profunda**: Se deseja entender o funcionamento interno, leia o [**Guia de Fluxo Interno do Agente**](agent-deep-flow.md) para ver o detalhamento dos subpassos e portas de decisão.

---

## 1. Fase: SPEC (O contrato)

**Objetivo:** Definir o contrato de implementação e os critérios de verificação.

- **Processo**: O agente analisa a requisição (ex: via `/sdg-feat` ou `/sdg-fix`) e produz uma especificação formal.
- **Padrões**:
  - Identificação do domínio (Backend, Frontend, Fullstack).
  - **Ciclo de Funcionalidade**: Foco em modelagem de domínio e lógica de negócio.
  - **Ciclo de Correção**: Execução de **Root Cause Analysis (RCA — análise de causa raiz)** para identificar o nível específico ou a violação de contrato.
  - Definição de entradas, saídas e restrições de hardware ou software.
  - Criação de um **Checklist de Verificação** (itens binários de aprovação ou falha).
- **Mandato**: O agente deve parar e aguardar a aprovação explícita da especificação pelo desenvolvedor antes de avançar para o plano.
- **Exceção de Raciocínio**: Modelos de raciocínio modernos podem prosseguir após emitir um bloco interno de `<thought>` (bloco de pensamento para validação de critérios).

---

## 2. Fase: PLAN (A estratégia)

**Objetivo:** Sequenciar a especificação em tarefas atômicas e executáveis.

- **Processo**: O agente elabora um roteiro lógico baseado na especificação aprovada.
- **Padrões**:
  - Produção de uma lista de tarefas numerada.
  - Uso do padrão Verbo de Ação + Objeto (ex: "1. Criar tipo de domínio de Usuário").
  - **Decomposição de Tarefas**: Divisão de tarefas complexas em subtarefas para manter a densidade vertical e evitar a exaustão do contexto (limite de memória da IA).
- **Mandato**: O agente deve parar e aguardar a aprovação explícita do plano pelo desenvolvedor.
- **Exceção de Raciocínio**: Modelos autônomos com raciocínio integrado podem avançar para a fase de código após validar que o plano reflete as leis de engenharia do projeto.

---

## 3. Fase: CODE (A execução)

**Objetivo:** Implementar o plano seguindo os padrões arquiteturais.

- **Processo**: O agente realiza as tarefas de implementação.
- **Padrões**:
  - Seguir a **Narrativa em Cascata** (chamadores definidos acima dos chamados).
  - Aderir ao estilo do projeto (Vertical Slice, MVC, etc.).
  - Implementar rigorosamente o que foi aprovado no plano (evitando YAGNI — funcionalidade desnecessária).
  - Notificar impedimentos imediatamente em vez de tentar contorná-los.

---

## 4. Fase: TEST (A verificação)

**Objetivo:** Garantir que a implementação corresponda ao checklist de verificação da especificação.

- **O que acontece:** O agente executa ou escreve testes e verifica cada item do checklist.
- **Comportamento do Agente:**
  - Cria novos testes se os itens do checklist não forem cobertos pelos existentes.
  - Reporta SUCESSO ou FALHA para cada item do checklist.
  - **Loop de Refatoração**: Se um teste falhar, o agente refatora o código e tenta novamente (até 3 vezes antes de parar para reportar um bloqueio).

---

## 5. Fase: END (A entrega)

**Objetivo:** Finalizar a tarefa, documentar as mudanças e preparar para o controle de versão.

- **O que acontece:** O agente resume o trabalho e atualiza os registros do projeto.
- **Comportamento do Agente:**
  - Resumo do que foi implementado (conectando com as tarefas do PLAN).
  - Adição de entradas no `CHANGELOG.md` seguindo o padrão [Keep a Changelog](https://keepachangelog.com/) (`### Added` para novidades, `### Fixed` para correções).
  - Proposta de uma mensagem de commit semântica (ex: `feat: ...` ou `fix: ...`).
  - Sugestão de próximos passos (Push, Deploy ou iniciar nova tarefa).

---

> [!IMPORTANT]
> O agente só escreve código após a aprovação das fases SPEC e PLAN. Este mecanismo mantém as mudanças rastreáveis a uma decisão explícita e evita suposições.
