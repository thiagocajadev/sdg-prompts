# 01 - Backlog de Limpeza e Preparação

Antes de "estrangular" o legado, precisamos deixar o terreno limpo. Refatorar o legado não significa torná-lo perfeito, mas sim torná-lo *previsível* para ser substituído.

## Tarefas de Higiene Técnica

- [ ] **Remoção de Código Morto**: Deletar funções, variáveis ou arquivos que não são chamados por ninguém (utilize ferramentas de análise estática).
- [ ] **Padronização de Entradas/Saídas**: Garantir que as APIs do legado enviem dados em formatos consistentes (ex: datas sempre em ISO-8601).
- [ ] **Externalização de Configurações**: Mover senhas e URLs de arquivos de código para variáveis de ambiente.

## Desacoplamento de Infraestrutura

- O código legado acessa o banco de dados diretamente em todos os lugares? Podemos mover isso para um "Repositório" centralizado antes da migração?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Backlog de Limpeza

Vamos apagar o código que não usa e organizar as pastas do sistema atual.
```

> **Razão**: Vago. O que acontece se você apagar algo que é usado apenas por um processo automático mensal (cron job)? Como provar que a limpeza não quebrou o sistema?

### ✅ Exemplo Bom

```markdown
# 01 - Backlog de Limpeza: Módulo de Cadastro

## Remoção de Código Morto

Identificamos, através do **Istanbul/NYC Coverage**, que 15% do arquivo `UserActions.php` nunca é executado. Faremos o *Delete* dessas funções.

## Preparação para Migração

As datas de nascimento no banco legado estão em 4 formatos diferentes. Criaremos um "Decorator" (limpador) na camada de saída da API legado para que o novo sistema receba sempre `YYYY-MM-DD`. Isso evitará falhas de tipagem no novo código em TypeScript.
```

> **Razão**: Utiliza ferramentas (Istanbul) para justificar a limpeza e resolve problemas de inconsistência de dados (formatos de data) antes que eles contaminem o novo sistema.
