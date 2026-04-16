<div align="center">
  <h1>SDG Prompts — Spec-Driven Guide</h1>

  <img src="img/sdg-agents-icon-light.svg" alt="SDG Prompts Logo" width="480">

  <p>
    <img src="https://img.shields.io/badge/version-1.1.0-blue.svg" alt="Version: 1.1.0">
    <img src="https://img.shields.io/badge/License-ISC-blue.svg" alt="License: ISC">
    <img src="https://img.shields.io/badge/Protocol-SDG-orange.svg" alt="Protocol: SDG">
    <img src="https://img.shields.io/badge/Style-Writing%20Soul-blueviolet.svg" alt="Style: Writing Soul">
  </p>

  <p>
    <a href="../README.md"><b>🇺🇸 English Version</b></a> | 
    <a href="README.pt-BR.md">🇧🇷 Versão em Português</a> | 
    <a href="../CHANGELOG.md"><b>📜 Changelog</b></a> | 
    <a href="https://specdrivenguide.org"><b>🌐 specdrivenguide.org</b></a>
  </p>
</div>

Bem-vindo ao ecossistema **SDG Prompts**. Este repositório contém uma coleção estruturada de trilhas de prompts e protocolos de governança projetados para guiar agentes de IA autônomos e desenvolvedores através do ciclo de vida de desenvolvimento de software.

## 🎯 O Objetivo

Oferecemos uma estrutura onde o código se torna o resultado natural de uma especificação precisa. Ao aderir ao protocolo **SDG (Guia de Especificações)**, os desenvolvedores garantem que cada mudança permaneça rastreável, modular e alinhada aos requisitos de negócio.

## 🗺️ Estrutura do Projeto

Este projeto organiza a documentação e as trilhas em espelhos de Inglês (`../docs/en/`) e Português Brasileiro (`../docs/pt-BR/`).

### 📜 [Guias e Manuais](../docs/pt-BR/)

- [**Guia de Especificações**](../docs/pt-BR/guia-especificacoes.md): Manual detalhado sobre o ciclo de tarefas de 5 fases (SPEC, PLAN, CODE, TEST, END).
- [**Metodologia e Referências**](REFERENCES.pt-BR.md): Origens e DNA teórico por trás do padrão SPEC.

### 🏗️ [Trilhas de Prompts](../docs/pt-BR/prompt-tracks/)

Oferecemos três trilhas distintas adaptadas à maturidade do projeto:

1. [**00 - Modo Lite**](../docs/pt-BR/prompt-tracks/00-modo-lite/): Fluxo de trabalho acelerado para landing pages e MVPs (Produtos Mínivos Viáveis).
2. [**01 - Nova Evolução**](../docs/pt-BR/prompt-tracks/01-nova-evolucao/): Caminho padrão para construção de aplicações escaláveis do zero (Greenfield).
3. [**02 - Modernização de Legado**](../docs/pt-BR/prompt-tracks/02-modernizacao-legado/): Guia técnico para refatoração e migração de sistemas existentes (Brownfield) usando o padrão Strangler Fig.

<details>
<summary><b>🧠 Anatomia de uma boa SPEC (Exemplo)</b></summary>

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

## 🧠 Como usar estas trilhas

1. **Identifique a Maturidade**: Determine se seu projeto é um protótipo, uma nova construção ou um sistema legado.
2. **Siga o Ciclo**: Cada trilha consiste em arquivos Markdown numerados. Execute-os sequencialmente. Estes arquivos garantem que o seu processo de desenvolvimento siga um fluxo lógico e seguro.
3. **Protocolo Writing Soul**: Toda a documentação segue o padrão **Writing Soul** — pedagógico, calmo e direto. Use estes prompts para alimentar seu Agente de IA para obter resultados consistentes e de alta qualidade.

## Licença

Este projeto está licenciado sob a [Licença ISC](LICENSE).

---

_Desenvolvido para Staff Engineers e Desenvolvedores Nativos de IA que valorizam a precisão sobre a velocidade._
