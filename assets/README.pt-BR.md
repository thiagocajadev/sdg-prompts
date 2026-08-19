<div align="center">
  <h1>Spec-Driven Guide</h1>

  <img src="img/sdg-agents-icon-light.svg" alt="Spec-Driven Guide" width="480">

  <p>
    <img src="https://img.shields.io/github/package-json/v/thiagocajadev/spec-driven-guide-prompts/main?label=vers%C3%A3o" alt="Versão">
    <img src="https://img.shields.io/badge/License-ISC-blue.svg" alt="License: ISC">
    <img src="https://img.shields.io/badge/Protocol-SDG-orange.svg" alt="Protocol: SDG">
    <img src="https://img.shields.io/badge/Style-Writing%20Soul-blueviolet.svg" alt="Style: Writing Soul">
  </p>

  <p>
    <a href="../README.md"><b>🇺🇸 English Version</b></a> | 
    <a href="README.pt-BR.md">🇧🇷 Versão em Português</a> | 
    <a href="CHANGELOG.md"><b>📜 Changelog</b></a> | 
    <a href="https://specdrivenguide.org"><b>🌐 specdrivenguide.org</b></a> | 
    <a href="https://github.com/thiagocajadev/spec-driven-guide"><b>⚙️ spec-driven-guide</b></a>
  </p>
</div>

**Spec-Driven Guide** é uma coleção de trilhas de prompts e regras de governança para times que trabalham ao lado de agentes de IA. Cada trilha é uma sequência de arquivos Markdown entregues ao agente, uma fase por vez.

## 🎯 O Objetivo

Escreva a especificação primeiro e depois codifique apenas o que ela descreve. No protocolo **SDG (Guia de Especificações)**, toda tarefa parte de um contrato escrito, então o motivo de cada mudança fica registrado ao lado do código.

## 🗺️ Estrutura do Projeto

A documentação e as trilhas existem em dois espelhos: Inglês (`../docs/en/`) e Português Brasileiro (`../docs/pt-BR/`).

### [Guias e Manuais](../docs/pt-BR/)

- [**Guia de Especificações**](../docs/pt-BR/guia-especificacoes.md): o ciclo de tarefas de 5 fases (SPEC, PLAN, CODE, TEST, END) explicado passo a passo.
- [**Metodologia e Referências**](REFERENCES.pt-BR.md): de onde vem o padrão SPEC e as fontes por trás dele.

### [Trilhas de Prompts](../docs/pt-BR/prompt-tracks/)

Três trilhas, uma para cada nível de maturidade do projeto:

1. [**00 - Modo Lite**](../docs/pt-BR/prompt-tracks/00-modo-lite/): ciclo curto para landing pages e MVPs.
2. [**01 - Nova Evolução**](../docs/pt-BR/prompt-tracks/01-nova-evolucao/): caminho completo para uma aplicação greenfield, construída do zero.
3. [**02 - Modernização de Legado**](../docs/pt-BR/prompt-tracks/02-modernizacao-legado/): refatoração e migração de um sistema brownfield com o padrão Strangler Fig.

## 📖 Conceitos

Os termos técnicos usados nas trilhas, agrupados por onde aparecem.

**O ciclo:** as cinco fases de uma tarefa

| Conceito | O que significa |
| --- | --- |
| [SPEC](../docs/pt-BR/guia-especificacoes.md#fase-spec) | O contrato escrito: contexto, métricas, escopo, regras e o que fica de fora. O agente não escreve código antes dele existir |
| [PLAN](../docs/pt-BR/guia-especificacoes.md#fase-plan) | A estratégia técnica: quais arquivos mudam, em que ordem e quais os riscos envolvidos |
| [CODE](../docs/pt-BR/guia-especificacoes.md#fase-code) | A execução, limitada ao que o PLAN descreveu |
| [TEST](../docs/pt-BR/guia-especificacoes.md#fase-test) | A prova de que cada cenário da SPEC se comporta como está escrito |
| [END](../docs/pt-BR/guia-especificacoes.md#fase-end) | A entrega: commit, documentação e fechamento da tarefa |

<br>

**Maturidade do projeto:** vocabulário para escolher a trilha

| Conceito | O que significa |
| --- | --- |
| MVP | Produto Mínimo Viável. A menor versão que já entrega valor e pode ser testada com usuários reais |
| Greenfield | Projeto sem código existente. Você escolhe a stack e a arquitetura sem legado a preservar |
| Brownfield | Sistema já em produção. Toda mudança convive com código, dados e decisões que vieram antes |
| Strangler Fig | Migração por substituição. O sistema novo é construído ao lado do antigo e assume rota por rota, até o antigo poder ser desligado. Sem reescrita total |

<br>

**Especificação:** as partes de um documento SPEC

| Conceito | O que significa |
| --- | --- |
| Success Metrics | Os números que dizem que a entrega funcionou: tickets evitados, retenção, tempo de resposta |
| User Story | Um cenário escrito do ponto de vista do usuário, descrevendo ação e resultado esperado |
| Constraints | Regras de negócio que limitam a solução: elegibilidade, prazos, permissões |
| Out of Scope | O que fica de fora desta entrega de propósito, escrito para o escopo não crescer em silêncio |
| Definition of Done | O checklist que fecha a tarefa. Enquanto houver item em aberto, a tarefa não está pronta |

<br>

**Governança:** como agentes e documentação se mantêm consistentes

| Conceito | O que significa |
| --- | --- |
| Trilha de prompts | Uma sequência numerada de arquivos Markdown. Cada arquivo é um passo do ciclo, executado em ordem |
| Agente de IA | O modelo que lê os prompts e produz o trabalho: código, testes ou documentação |
| Writing Soul | O padrão de escrita deste projeto: pedagógico, calmo e direto, sem enrolação |

<details>
<summary><b>Anatomia de uma boa SPEC (Exemplo)</b></summary>

# SPEC-001: Sistema de Cancelamento de Assinatura (Self-Service)

## 1. Contexto

Atualmente, o cancelamento de assinaturas é feito apenas via chat humano, gerando alta carga no suporte e frustração ao cliente. Esta spec define a automação do fluxo de cancelamento diretamente pelo painel do usuário.

## 2. Resultados Esperados (Success Metrics)

- Redução de 40% nos tickets de suporte relacionados a cancelamento.
- Retenção de 10% dos usuários através de ofertas de "downgrade" durante o fluxo.
- Atualização imediata do status da assinatura no banco de dados e gateway de pagamento.

## 3. Escopo e Cenários (User Stories)

- **Cenário A:** Usuário cancela e perde acesso ao final do período pago (pro-rata).
- **Cenário B:** Usuário aceita uma oferta de desconto para não cancelar.
- **Cenário C:** Usuário com faturas pendentes é impedido de cancelar via self-service.

## 4. Limites e Regras de Negócio (Constraints)

- **Elegibilidade:** Apenas usuários com plano "Premium" ou "Standard" podem cancelar via painel. Planos "Enterprise" exigem contato com o Gerente de Conta.
- **Prazo:** O cancelamento deve ser solicitado até 24h antes da próxima renovação para evitar cobranças indesejadas.
- **Reversibilidade:** O usuário pode reativar a assinatura com um clique até o último dia do ciclo atual.

## 5. Limitações (Out of Scope)

- Estornos (Refunds) automáticos não serão tratados nesta versão (devem ser manuais via admin).
- Cancelamentos de contas suspensas por fraude.

## 6. Definição de Pronto (Definition of Done)

- [ ] Integração com a API do Stripe para cancelar renovação.
- [ ] Envio de e-mail de confirmação de encerramento.
- [ ] Log de motivo de cancelamento salvo para o time de Produto.

<br>

---

</details>

## Como utilizar estas trilhas

1. **Identifique a maturidade**: protótipo, construção nova ou sistema legado. Essa escolha define a trilha.
2. **Siga o ciclo**: execute os arquivos numerados em ordem. Cada um deixa o projeto em um estado conhecido antes do próximo começar.
3. **Mantenha a voz**: os prompts seguem o padrão **Writing Soul**. Use a mesma voz nos seus arquivos e o agente terá um só tom para copiar.

## Licença

Este projeto está licenciado sob a [Licença ISC](../LICENSE). [**Changelog**](CHANGELOG.md)

---

_Feito para Staff Engineers e desenvolvedores nativos de IA que preferem precisão a velocidade._
