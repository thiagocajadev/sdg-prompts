# Trilhas de Prompts — O Motor de Execução

As Trilhas de Prompts são sequências lógicas de instruções projetadas para guiar Agentes de IA e desenvolvedores através de diferentes tipos de projetos. Cada trilha adapta o rigor da governança e a profundidade da arquitetura conforme a complexidade da entrega.

## Trilhas Disponíveis

### [00 - Modo Lite (MVPs e Landing Pages)](00-modo-lite/)
Focada em velocidade extrema e validade comercial. Ideal para freelancers e agências que precisam entregar páginas de destino (landing pages) ou protótipos funcionais em menos de 48 horas.
- **DNA**: Simplicidade, Integrações de Terceiros e Checklist de Lançamento.

### [01 - Nova Evolução (Projetos do Zero)](01-nova-evolucao/)
A trilha padrão para construção de sistemas escaláveis partindo do zero (Greenfield). Segue rigorosamente as leis de engenharia e as fases de especificação profunda.
- **DNA**: Visão de Projeto, Arquitetura Robusta e Entrega Contínua.

### [02 - Modernização de Legado (Refatoração)](02-modernizacao-legado/)
Projetada para lidar com sistemas existentes que precisam de evolução, limpeza de débito técnico ou migração tecnológica.
- **DNA**: Análise de Inventário, Estratégia de Coexistência e Refatoração Gradual.

---

## Como utilizar as trilhas

1. **Escolha o contexto**: Identifique em qual estágio o seu projeto se encontra.
2. **Siga a numeração**: Os arquivos são numerados para garantir a ordem lógica (00 -> 01 -> 02...).
3. **Respeite os Gates**: Não avance para uma especificação de "Arquitetura" (02) sem antes ter a aprovação da "Fundação/Visão" (01).

---

## Padrão de Especificação (SPEC)

Toda nova funcionalidade no diretório `04-funcionalidades` deve seguir este padrão obrigatório de 6 passos:

```markdown
# SPEC-XXX: [Título]

## 1. Contexto
[Por que isso está sendo construído, o problema que resolve e o público-alvo.]

## 2. Resultados Esperados (Success Metrics)
* [Resultado mensurável A]
* [Resultado mensurável B]

## 3. Escopo e Cenários (User Stories)
* [Cenários detalhados e histórias de usuário.]

## 4. Restrições e Regras de Negócio
* [Limites lógicos e comportamentos obrigatórios.]

## 5. Fora de Escopo
* [O que NÃO será entregue nesta tarefa.]

## 6. Definição de Pronto (DoD)
- [ ] [Passos de verificação e critérios de aceite.]
```

---

## Exemplos de Qualidade Staff

### ❌ Exemplo Ruim (IA Genérica / Slop)

```markdown
# 04-01 - Melhoria no Sistema

## Contexto
Melhorar o sistema para os usuários e aumentar as vendas.

## Escopo
Tudo o que for necessário. Sem limites.

## Regras de Negócio
Sistema rápido. Usuários podem comprar coisas.

## Arquitetura
Melhores práticas de mercado. Integração com banco.
```

> **Razão**: Vago, sem métricas, sem definições técnicas e sem critérios claros de aceitação. Puro "IA slop".

### ✅ Exemplo Bom (Qualidade Staff)

```markdown
# SPEC-001: Checkout em Um Clique (Stripe)

## 1. Contexto
Reduzir o abandono de carrinho na etapa final de pagamento, simplificando o fluxo para usuários recorrentes.

## 2. Resultados Esperados (Success Metrics)
* Aumento de 15% na taxa de conversão para usuários que retornam.
* Tempo médio de checkout inferior a 10 segundos.

## 3. Escopo e Cenários (User Stories)
* **Cenário A:** Sucesso com cartão salvo e estoque > 0.
* **Cenário B:** Rollback atômico se o pagamento falhar após reserva de estoque.
* **User Story:** Como cliente recorrente, quero pagar com um clique para não ter que redigitar meus dados.

## 4. Restrições e Regras de Negócio
* Apenas para usuários logados com um `stripe_customer_id` válido.
* Verificação de estoque síncrona antes da confirmação do `PaymentIntent`.
* IDs de transação devem seguir o prefixo `chkt_` para rastreabilidade.

## 5. Fora de Escopo
* Migração total de gateway ou métodos alternativos (ex: Cripto).
* Armazenamento local de números de cartão (limite de PCI Compliance).

## 6. Definição de Pronto (DoD)
- [ ] Integração com Stripe Vault verificada.
- [ ] Webhook de pré-validação de inventário implementado.
- [ ] 100% dos cenários de pagamento e2e automatizados.
```

> **Razão**: Objetivos específicos, métricas de negócio, limites claros e estratégias de erro atômicas seguindo o protocolo SPEC de 6 passos.
