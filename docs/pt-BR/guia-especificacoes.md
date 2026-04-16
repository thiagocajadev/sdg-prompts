# Guia de Especificações (Ciclo de tarefas em 5 fases)

O **Guia de Especificações (SDG — Spec-Driven Guide)** estabelece um ciclo de vida padronizado para cada tarefa. O objetivo é garantir que o código seja escrito apenas após a aprovação total da intenção e do plano de implementação.

O ciclo segue cinco fases obrigatórias: **SPEC → PLAN → CODE → TEST → END**.

> [!TIP]
> **DNA Teórico**: Quer entender as origens do padrão SPEC? Leia nossa [**Metodologia e Referências**](../assets/REFERENCES.pt-BR.md) para um detalhamento dos pilares centrais e material de origem arquitetural.

---

## 1. Fase: SPEC (O contrato)

**Objetivo:** Definir o contrato de implementação e os critérios de verificação.

- **Processo**: O agente analisa a requisição (ex: via `feat:` ou `fix:`) e produz uma especificação formal.
- **Estrutura Obrigatória (6 Passos)**:
  1. **Contexto**: Por que isso está sendo construído e para quem.
  2. **Resultados Esperados**: Métricas de sucesso ou impacto de negócio esperado.
  3. **Escopo e Cenários**: Histórias de usuário e cenários explícitos de comportamento.
  4. **Limites e Regras de Negócio**: Elegibilidade, prazos e restrições técnicas.
  5. **Limitações (Fora de Escopo)**: O que explicitamente NÃO será tratado.
  6. **Definição de Pronto (DoD)**: Checklist final de verificação da tarefa.
- **Mandato**: O agente deve parar e aguardar a aprovação explícita da especificação pelo desenvolvedor antes de avançar para o plano.

### Exemplo de Padrão Ouro:
```markdown
# SPEC-001: Sistema de Cancelamento de Assinatura (Self-Service)

## 1. Contexto
Atualmente o cancelamento é via chat, gerando carga no suporte. Esta spec automatiza o fluxo via painel.

## 2. Resultados Esperados
* Redução de 40% nos tickets de suporte.
* Retenção de 10% via ofertas de downgrade.

## 3. Escopo e Cenários
* **Cenário A:** Usuário cancela e perde acesso ao fim do ciclo.
* **Cenário B:** Usuário aceita desconto para ficar.

## 4. Limites e Regras
* Apenas planos Premium/Standard. Enterprise segue fluxo manual.

## 5. Limitações
* Estornos automáticos (processados manualmente).

## 6. Definição de Pronto
- [ ] Integração API Stripe.
- [ ] E-mail de confirmação enviado.
```

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
