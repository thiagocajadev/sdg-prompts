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
# SPEC-012: Injeção de Dependência e Repositórios

## 1. Contexto
Implementar padrões de criação e acesso a dados para desacoplar a lógica de negócio de implementações técnicas.

## 2. Resultados Esperados (Success Metrics)
* 100% de testabilidade da lógica de vendas usando repositórios em memória.
* Facilidade de troca de gateway de pagamento (Stripe para Pagar.me).

## 3. Escopo e Cenários (User Stories)
* **Padrão Repository:** Interface `IOrderRepository` para abstrair o banco real.
* **Padrão Factory:** Criação de `PaymentGateway` dinâmica baseada no tipo de cartão.

## 4. Restrições e Regras de Negócio
* Uso obrigatório de Inversão de Dependência para serviços externos.
* Repositórios não devem conter lógica de negócio, apenas acesso a dados.

## 5. Fora de Escopo
* Implementação de CQRS complexo.
* Event Sourcing para auditoria de vendas.

## 6. Definição de Pronto (DoD)
- [ ] Interface `IOrderRepository` definida.
- [ ] Factory de pagamentos testada com múltiplos provedores.
```

> **Razão**: Contextualiza o padrão com um problema real (Vendas/Pagamento) e justifica através da testabilidade e flexibilidade.
