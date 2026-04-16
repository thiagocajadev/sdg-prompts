# Origens e Referências: O Padrão SPEC

Este documento detalha o DNA metodológico por trás da estrutura **Standard Product Spec** (ou Spec Funcional) adotada neste guia. Nossa abordagem combina as melhores práticas de empresas que priorizam a **escrita antes da execução**.

---

## 🏗️ Pilares da Redução de Ambiguidade

A estrutura SPEC não é apenas um template; é um framework de pensamento crítico baseado em 6 passos:

### 1. Context (O "Porquê")
*   **Conceito**: *Outcome-over-Output*.
*   **Filosofia**: Um Spec não deve ser uma lista de tarefas, mas sim um argumento de negócio.
*   **Aprofundamento**:
    *   [The Pragmatic Engineer: How Stripe Builds Product (Part 1)](https://newsletter.pragmaticengineer.com/p/stripe)
    *   [The Pragmatic Engineer: How Stripe Builds Product (Part 2)](https://newsletter.pragmaticengineer.com/p/stripe-part-2)
    *   [Lenny's Newsletter: How Linear builds product](https://www.lennysnewsletter.com/p/how-linear-builds-product)

### 2. Success Metrics (O "Impacto")
*   **Conceito**: Mensurabilidade e ROI.
*   **Filosofia**: Se não há métrica de sucesso clara (ex: ganhos de eficiência), o Spec é considerado "vazio".
*   **Aprofundamento**:
    *   [Stripe Operating Principles & Writing Culture](https://www.tryexponent.com/blog/stripe-operating-principles)

### 3. Scope & Scenarios (O "O quê")
*   **Conceito**: Evolução dos *User Stories* com foco em *Jobs-to-be-Done* (JTBD).
*   **Filosofia**: Foca no cenário real do usuário e na jornada completa (POC vs MVP).
*   **Aprofundamento**:
    *   [Christensen Institute: Jobs-to-be-Done Theory](https://www.christenseninstitute.org/theory/jobs-to-be-done/)
    *   [Intercom: Jobs-to-be-Done Discussion](https://jobs-to-be-done.com/jobs-to-be-done-discussion-with-intercom-f57987239569)
    *   [Strategyn: History of JTBD](https://strategyn.com/jobs-to-be-done/history-of-jtbd/)
    *   [GoPractice: JTBD Theory and Frameworks](https://gopractice.io/product/jobs-to-be-done-the-theory-and-the-frameworks/)

### 4. Constraints & Business Rules (As "Regras")
*   **Conceito**: Limites lógicos e guardrails técnicos.
*   **Filosofia**: Estabelece os trilhos onde a solução deve rodar para garantir segurança e consistência.
*   **Aprofundamento**:
    *   [Stripe Atlas: Scaling Engineering and Decision Making](https://stripe.com/guides/atlas/scaling-eng)

### 5. Out of Scope (As "Fronteiras")
*   **Conceito**: Gerenciamento de Escopo e *Lean Development*.
*   **Filosofia**: Definir o que **NÃO** será feito evita desperdício de energia e o temido *scope creep*.
*   **Aprofundamento**:
    *   [Princípios do Manifesto Ágil](https://agilemanifesto.org/principles.html)

### 6. Definition of Done (O "Check-point")
*   **Conceito**: Contrato de Qualidade.
*   **Filosofia**: Um contrato inegociável que garante que o "Pronto" seja técnico, funcional e visual.
*   **Aprofundamento**:
    *   [Scrum.org: O que é a Definição de Pronto?](https://www.scrum.org/resources/what-definition-done)
    *   [Agile Alliance: Glossário da Definição de Pronto](https://agilealliance.org/glossary/definition-of-done/)
    *   [O Guia do Scrum (2020)](https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-US.pdf)
