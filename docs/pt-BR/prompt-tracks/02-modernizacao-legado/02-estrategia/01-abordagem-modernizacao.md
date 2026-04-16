# 01 - Abordagem de Modernização (Big Bang vs. Strangler)

Como atacaremos o monolito legado? A escolha da estratégia dita o risco e o tempo para o primeiro retorno de valor ao negócio.

## Estratégias Consideradas

- [ ] **Big Bang (Reescrita Total)**: Construir tudo do zero e substituir de uma vez. (Risco alto, ROI demorado).
- [ ] **Strangler Fig (Padrão Estrangulamento)**: Substituir partes gradualmente, funcionalidade por funcionalidade. (Risco baixo, ROI rápido).
- [ ] **Refatoração Tática (In-place)**: Melhorar o código atual sem trocar a tecnologia.

## Racional da Escolha

Por que a estratégia escolhida é a mais segura para este contexto específico?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Abordagem de Modernização

Vamos reescrever tudo do zero em Node.js porque o código antigo é ruim.
```

> **Razão**: Escolha emocional. Reescrever do zero (Big Bang) geralmente falha porque o novo sistema nunca alcança as funcionalidades do antigo em tempo hábil, gerando fadiga no projeto e perda de investimento.

### ✅ Exemplo Bom

```markdown
# 01 - Abordagem de Modernização: Projeto Checkout

## Estratégia: Strangler Fig (Estrangulamento)

Utilizaremos um **API Gateway** (Proxy) à frente do sistema legado.
1. Começaremos migrando apenas a rota de "Consulta de Frete" para um novo microserviço.
2. O Proxy direcionará o tráfego de frete para o novo código e manterá o restante (Pagamentos, Carrinho) no legado.
3. Repetiremos o processo até que o legado não tenha mais tráfego ativo.

## Racional

Isso permite que a empresa comece a colher os frutos da modernização (maior velocidade no Frete) em apenas 2 semanas, em vez de esperar 6 meses por uma reescrita total.
```

> **Razão**: Abordagem técnica e pragmática que foca na entrega contínua de valor e redução de riscos operacionais.
