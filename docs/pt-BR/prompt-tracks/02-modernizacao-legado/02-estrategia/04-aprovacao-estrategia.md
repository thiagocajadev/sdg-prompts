# 04 - Aprovação da Estratégia de Modernização

## Checklist de Artefatos

- [ ] 01-abordagem-modernizacao.md (Definido)
- [ ] 02-versionamento-coexistencia.md (Validado tecnicamente)
- [ ] 03-triagem-novas-demandas.md (Alinhado com produto)

## Aprovação dos Stakeholders

- **CTO / Líder Técnico**: [Assinatura/Data]
- **Product Manager**: [Assinatura/Data]

## Definição de Prontidão (Ready for Refactor/Preparation)

- [ ] A estratégia de coexistência de dados foi testada em ambiente de laboratório.
- [ ] O time de produto concorda com o congelamento de novas funções no legado.
- [ ] O plano de rollback (em caso de falha na integração entre sistemas) está definido.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 04 - Aprovação da Estratégia

## Checklist

- [x] Escolhemos o jeito de fazer.

## Definição de Prontidão

- [x] Vamos começar amanhã.
```

> **Razão**: Vago. Não especifica qual abordagem foi escolhida (Strangler ou Big Bang) nem se o plano de rollback foi validado com o time de infraestrutura.

### ✅ Exemplo Bom

```markdown
# 04 - Aprovação da Estratégia: Core V2

## Checklist

- [x] 01-abordagem-modernizacao.md (Strangler Fig via Kong Gateway)
- [x] 02-versionamento-coexistencia.md (Replicação assíncrona aprovada)

## Aprovação dos Stakeholders

- **PO**: Renato Vanes (Aprovado em 20/05/2026) – Concorda com o congelamento do módulo de Login no legado por 60 dias.
```

> **Razão**: Traz compromissos reais de stakeholders e detalhes técnicos que protegem o projeto contra mudanças de direção repentinas.
