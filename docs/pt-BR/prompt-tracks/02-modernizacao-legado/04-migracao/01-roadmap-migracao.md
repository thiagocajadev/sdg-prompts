# 01 - Roadmap de Migração por Domínios

A migração não deve ser feita por "pastas de arquivos", mas sim por "capacidades de negócio" (domínios). Isso permite desligar módulos inteiros do legado de forma independente.

## Sequência de Migração

1.  **Módulo X**: [Data Estimada] (ex: Autenticação).
2.  **Módulo Y**: [Data Estimada] (ex: Catálogo de Produtos).

## Dependências de Circuito

- Se migrarmos o "Módulo Y", como ele continuará consultando os dados que ainda estão no legado ("Módulo Z")? (Uso de **Anti-Corruption Layers - ACL**).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Roadmap de Migração

Vamos começar pelo banco de dados e depois vamos subindo para as APIs. Previsão de 4 meses.
```

> **Razão**: Tentar migrar "por camadas técnicas" (banco, depois API) é a receita para o fracasso. Você terá um banco novo sem utilidade e um sistema legado tentando acessá-lo via gambiarras, aumentando a complexidade em vez de reduzi-la.

### ✅ Exemplo Bom

```markdown
# SPEC-014: Roadmap Estratégico E-Commerce V2

## 1. Contexto
Modernização faseada do E-commerce legada para garantir continuidade de negócio e evolução técnica por domínios.

## 2. Resultados Esperados (Success Metrics)
* Zero incidentes durante a migração de domínios críticos.
* Manutenção de 100% da integridade de dados entre novo e velho sistema.

## 3. Escopo e Cenários (User Stories)
* **Fase 1 (Dezembro):** Autenticação (Login na infra nova).
* **Fase 2 (Janeiro):** Carrinho (Sincronização Redis/SQL).
* **Fase 3 (Fevereiro):** Checkout (Processamento 100% novo).

## 4. Restrições e Regras de Negócio
* Uso obrigatório de Anti-Corruption Layer (ACL) para tradução de IDs.
* O módulo de Logística deve permanecer operacional no legado até a Fase 4.

## 5. Fora de Escopo
* Migração total do banco de dados em uma única etapa (Big Bang).
* Refatoração de funcionalidades que serão descontinuadas.

## 6. Definição de Pronto (DoD)
- [ ] Serviço ACL validado em produção.
- [ ] Autenticação migrada com sucesso.
```

> **Razão**: Abordagem orientada a valor (domínios). Permite que partes do sistema sejam modernizadas e validadas em produção enquanto o restante continua operando normalmente.
