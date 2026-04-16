# 01 - Inventário de Débito Técnico

Antes de modernizar, precisamos mapear onde o sistema está "doente". Débito técnico não é apenas código feio; é qualquer decisão que gera custo ou risco excessivo hoje.

## Mapeamento de Tecnologias Obsoletas

- [ ] Linguagens, Frameworks ou Bibliotecas que não recebem mais atualizações (End-of-life).
- [ ] Versões de Banco de Dados ou Sistemas Operacionais legados.

## Complexidade e Pontos de Falha

- Onde estão os "God Objects" (classes/objetos que fazem tudo)?
- Quais módulos têm a maior taxa de erros ou incidentes reportados?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Inventário de Débito Técnico

O código está muito bagunçado e é difícil de ler. Precisamos refatorar os controllers.
```

> **Razão**: Subjetivo. "Ser difícil de ler" é um sintoma, não o diagnóstico técnico. Quais os impactos de negócio desse "código bagunçado"?

### ✅ Exemplo Bom

```markdown
# SPEC-013: Liquidação de Débito Técnico (Pagamentos)

## 1. Contexto
Mapear e planejar a correção de fragilidades críticas no módulo de pagamentos que geram risco financeiro e operacional.

## 2. Resultados Esperados (Success Metrics)
* Redução de 30% na taxa de erros em estornos de pagamentos.
* Economia de 80% nos recursos do banco de dados em horários de pico.

## 3. Escopo e Cenários (User Stories)
* **Risco A:** Node.js v12 sem suporte de segurança.
* **Risco B:** `PaymentService.js` com 5.400 linhas de código altamente acoplado.

## 4. Restrições e Regras de Negócio
* A modernização não deve interromper o fluxo de pagamentos atual.
* Priorização absoluta para falhas de segurança críticas (versão do Node).

## 5. Fora de Escopo
* Refatoração visual do dashboard administrativo.
* Melhoria de performance em módulos não críticos (ex: Relatórios).

## 6. Definição de Pronto (DoD)
- [ ] Upgrade do ambiente para Node.js LTS concluído.
- [ ] Plano de decomposição do `PaymentService` aprovado.
```

> **Razão**: Quantifica o risco (versão sem suporte, consumo de 80% de recursos) e identifica o arquivo exato que trava a produtividade do time.
