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
# 01 - Roadmap de Migração: E-Commerce V2

## Fases por Domínio

1. **Autenticação (Dezembro)**: Primeiro módulo, permite que o usuário logue na infra nova enquanto navega no site velho.
2. **Carrinho (Janeiro)**: Migração do estado das compras. Exige sincronização em tempo real entre o Redis novo e o banco SQL legado.
3. **Checkout (Fevereiro)**: O momento da verdade. O pagamento passa a ser processado 100% pelo código novo.

## Anti-Corruption Layer (ACL)

Criaremos um serviço intermediário que traduz os IDs hexadecimais do novo banco para os IDs incrementais do legado, garantindo que o módulo de "Envio/Logística" (que ainda estará no legado) não quebre.
```

> **Razão**: Abordagem orientada a valor (domínios). Permite que partes do sistema sejam modernizadas e validadas em produção enquanto o restante continua operando normalmente.
