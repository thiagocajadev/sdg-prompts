# 02 - Padrões de Projeto (Design Patterns)

## Padrões Adotados

- [ ] **Repository Pattern**: Abstração da camada de persistência.
- [ ] **Dependency Injection (DI)**: Gestão de dependências e inversão de controle.
- [ ] **Singleton / Factory**: Criação controlada de instâncias.

## Racional dos Padrões

Explique o porquê da utilização de padrões específicos para resolver problemas de acoplamento ou complexidade.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Padrões de Projeto

Vamos usar Repository e Factory.
```

> **Razão**: Vago. Não explica onde ou por que esses padrões serão aplicados no projeto.

### ✅ Exemplo Bom

```markdown
# 02 - Padrões de Projeto: Módulo de Vendas

## Padrões Adotados

- **Repository Pattern**: Criaremos `IOrderRepository`. Isso permite testar a lógica de vendas usando um repositório em memória em vez de um banco real.
- **Factory**: Utilizada para construir objetos de `PaymentGateway` complexos baseados no tipo de cartão do cliente.

## Racional

O uso de Inversão de Dependência garantirá que nossa lógica de vendas não dependa diretamente da API do Stripe ou do Pagar.me, facilitando migrações futuras.
```

> **Razão**: Contextualiza o padrão com um problema real (Vendas/Pagamento) e justifica através da testabilidade e flexibilidade.
