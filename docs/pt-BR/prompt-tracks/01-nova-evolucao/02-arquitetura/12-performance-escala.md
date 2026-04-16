# 12 - SLAs de Performance e Escala (Operações)

Sistemas distribuídos que não preveem contenção de tráfego sofrerão indisponibilidade em cascata (Avalanche de Timeouts). O arquiteto precisa definir os limites de dor do seu sistema no contrato.

## Alavancas de Resiliência

- [ ] **Rate Limiting (Limite de Taxa)**: A API bloqueará clientes que chamarem mais de `100 req/min`? (Proteja seu banco de dados).
- [ ] **Circuit Breakers (Disjuntores)**: Se o microserviço parceiro cair (ex: Gateway de Pagamento), quanto tempo nosso serviço continuará esperando resposta antes de "abrir o circuito" e falhar rápido via fail-fast (< 500ms)?
- [ ] **Latência Alvo (SLOs - Objetivos de Nível de Serviço)**: O percentil p95 rigoroso deve ser `< 250ms`.

## Táticas Estruturais (Cache vs Sync)

- A leitura será pesada? O que vai para o Cache (`Redis/Memcached`) e o que buscará o armazenamento primário diretamente? Utilizaremos filas asíncronas (Kafka/SQS) para o modelo de escrita (CQRS)?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Escalabilidade

Vai aguentar a Black Friday porque nossa nuvem é elástica (Autoscaling).
```

> **Razão**: Promessa falsa. Escalar 1.000 instâncias de Frontend para bater em um único banco de dados estressado só vai esgotar o pool de conexões mais rápido (DDoS interno).

### ✅ Exemplo Bom

```markdown
# Performance: Módulo de Carrinho V2

## Latência P95 (Alvo)

- Listar Carrinho (GET): `< 150ms`.
- Pagar Carrinho (POST): `< 850ms` (Devido à latência de adquirente externo).

## Medidas Anti-Avalanche

- Redis Cache para os 50 itens mais vendidos (10m de TTL).
- Conexão HTTP do Stripe terá um **timeout rigoroso de 3 segundos**. Se o Stripe não retornar, o código lança um `PaymentGatewayTimeoutException` salvando no banco como Pendente.
- **Rate Limit (API Gateway):** 30 requisições por IP por minuto.
```

> **Razão**: Define regras e gatilhos rigorosos. O administrador do sistema (Sysadmin) só precisa ler este documento para configurar corretamente o firewall; o desenvolvedor de backend não esquecerá de configurar o Timeout no seu cliente HTTP.
