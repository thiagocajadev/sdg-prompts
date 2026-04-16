# 02 - Definição do Problema

## Contexto e Situação Atual

- Como o processo funciona hoje (detalhadamente)?
- Quais ferramentas ou "quebra-galhos" são utilizados?

## Pontos de Dor (Pain Points)

- [ ] Ponto de dor 1 (ex: Lentidão no processamento de pedidos).
- [ ] Ponto de dor 2 (ex: Dados duplicados entre planilhas).

## Workflows (Fluxos de Trabalho) Principais

- Descreva os 2 ou 3 fluxos que são mais críticos para o sucesso do projeto.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Definição do Problema

## Situação Atual

O cliente usa planilhas Excel.

## Pontos de Dor

É difícil de usar e trava muito.
```

> **Razão**: Não descreve o *impacto*. Por que travar é um problema? Quanto tempo é perdido?

### ✅ Exemplo Bom

```markdown
# 02 - Definição do Problema

## Situação Atual

A equipe financeira recebe dados de 4 fontes diferentes (cartão, boleto, pix e dinheiro) e consolida tudo manualmente em um Excel compartilhado no final do dia.

## Pontos de Dor

- [ ] **Erro Humano:** 15% das entradas possuem divergência de centavos, gerando 4 horas extras semanais para correção.
- [ ] **Lentidão:** O fechamento mensal demora 5 dias úteis.

## Fluxos Críticos

O fluxo de "Conciliação Bancária Automática" é o núcleo do problema. O sistema deve ler os extratos e marcar as faturas como pagas sem intervenção humana.
```

> **Razão**: Quantifica o desperdício (15% de erro, 4 horas extras) e aponta exatamente qual parte da tecnologia resolverá o problema de raiz.
