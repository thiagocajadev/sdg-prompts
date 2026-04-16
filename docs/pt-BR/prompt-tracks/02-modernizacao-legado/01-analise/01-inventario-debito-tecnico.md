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
# 01 - Inventário de Débito Técnico: App de Pagamentos

## Gargalos Tecnológicos

- **Node.js v12**: Versão sem suporte de segurança. Bloqueia o uso de bibliotecas modernas de criptografia.
- **ORM Legado**: Gera queries N+1 no módulo de extrato, consumindo 80% dos recursos do banco em horários de pico.

## Localização da Complexidade

- **`PaymentService.js`**: 5.400 linhas de código com 42 responsabilidades diferentes. Qualquer alteração aqui tem 30% de chance de quebrar o fluxo de estorno.
```

> **Razão**: Quantifica o risco (versão sem suporte, consumo de 80% de recursos) e identifica o arquivo exato que trava a produtividade do time.
