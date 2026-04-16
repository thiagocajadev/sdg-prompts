# 03 - Triagem de Novas Demandas (Legado vs. Novo)

O maior erro em uma modernização é continuar alimentando o monolito legado com novas funcionalidades enquanto tenta matá-lo. Precisamos de um filtro rigoroso.

## Onde a Nova Demanda Deve Nascer?

- [ ] **Novo Sistema**: Padrão para 90% das novas funcionalidades.
- [ ] **Legado**: Apenas correções de bugs críticos ou alterações legais que não podem esperar o fim da migração.

## Lei da Escoteiro para o Legado

- Se for estritamente necessário mexer no legado, como podemos deixar o código um pouco melhor ou mais preparado para a migração futura?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - Triagem de Novas Demandas

Tudo o que for novo nós vamos tentar fazer no sistema novo.
```

> **Razão**: Vago. O "tentar fazer" abre margem para pressões de prazo onde o desenvolvedor acaba cedendo e criando código novo no legado "porque é mais rápido agora", aumentando o débito que precisará ser migrado depois.

### ✅ Exemplo Bom

```markdown
# 03 - Triagem de Novas Demandas: Projeto Omni

## Matriz de Decisão

- **Funcionalidade Inédita**: Obrigatoriamente no sistema novo (Node.js). Se o dado estiver no legado, criamos uma API de leitura temporária.
- **Mudança em Fluxo Existente**:
  - Se faltar mais de 3 meses para a migração do módulo: Faz no legado de forma minimalista.
  - Se faltar menos de 3 meses: Antecipa a migração do módulo e faz no novo.

## Racional

Evitar o "Inchaço do Balde Furado". Cada hora gasta criando lógica nova no legado é uma hora a mais que o time levará para desligá-lo definitivamente.
```

> **Razão**: Estabelece uma política clara (Matriz de Decisão) que protege a capacidade do time de focar na modernização e evita o desperdício de esforço em tecnologia morta.
