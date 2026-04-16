# 01 - Visão do Projeto

## Qual Problema Estamos Resolvendo?

- Resumo curto e direto do problema de negócio.
- O que acontece hoje se nada for feito?

## Objetivos de Negócio de Alto Nível

- [ ] Objetivo 1 (ex: Aumentar a conversão em 20%).
- [ ] Objetivo 2 (ex: Reduzir o tempo de resposta do suporte).

## Público-Alvo e Stakeholders

- Quem são os usuários finais?
- Quem são os tomadores de decisão (Stakeholders)?

## Diferenciação (Vantagem Competitiva)

- Por que este projeto é único?
- Qual é o "fator uau" ou o principal diferencial técnico/comercial?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Visão do Projeto

## Qual Problema Estamos Resolvendo?

Queremos um app de entrega de comida.

## Objetivos

Fazer o app funcionar e ser rápido.
```

> **Razão**: Vago demais. "Ser rápido" não é um objetivo mensurável. Para quem é o app? Por que ele é necessário?

### ✅ Exemplo Bom

```markdown
# SPEC-009: App de Entrega Local

## 1. Contexto
Restaurantes locais perdem 30% da margem em taxas para grandes aplicativos de entrega e não possuem controle sobre os dados dos seus clientes.

## 2. Resultados Esperados (Success Metrics)
* Lançar um MVP que reduza a taxa por entrega para no máximo 5%.
* Aumentar em 20% a retenção de clientes via cupons diretos.

## 3. Escopo e Cenários (User Stories)
* **User Story (B2B):** Como dono de restaurante, quero gerenciar meus dados para não depender de terceiros.
* **User Story (B2C):** Como cliente, quero cupons de fidelidade para economizar em pedidos recorrentes.

## 4. Restrições e Regras de Negócio
* O lojista deve gerenciar cupons sem intervenção técnica externa.
* O sistema deve garantir a propriedade e o controle dos dados pelo restaurante.

## 5. Fora de Escopo
* Integração com frotas de entrega terceirizadas nesta fase.
* Desenvolvimento de aplicativos nativos iOS/Android.

## 6. Definição de Pronto (DoD)
- [ ] MVP com fluxo de pedido e fidelidade concluído.
- [ ] Base de dados estruturada para controle do lojista.
```

> **Razão**: Define claramente o problema financeiro (margem de lucro) e objetivos tangíveis que justificam o investimento no projeto.
