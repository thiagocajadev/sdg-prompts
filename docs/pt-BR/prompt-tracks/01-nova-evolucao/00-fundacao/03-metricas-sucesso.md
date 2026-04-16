# 03 - Métricas de Sucesso

## Métricas de Desempenho (KPIs Tecnológicos)

- [ ] Latença/Tempo de Resposta (ex: < 200ms para 95% das requisições).
- [ ] Taxa de Erro (ex: < 0.1% em produção).
- [ ] Cobertura de Testes (ex: Mínimo de 80% em lógica de negócio).

## Métricas de Valor (KPIs de Negócio)

- [ ] Adoção (ex: 50 usuários ativos na primeira semana).
- [ ] Conversão (ex: Redução de 20% no abandono de checkout).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - Métricas de Sucesso

## Métricas

O app deve ser rápido e não cair.
Todo mundo deve gostar de usar.
```

> **Razão**: Subjetivo e impossível de medir. "Rápido" para um usuário pode ser 2 segundos, para outro 200ms.

### ✅ Exemplo Bom

```markdown
# 03 - Métricas de Sucesso

## Métricas de Desempenho

- [ ] **Lighthouse:** Score de performance acima de 90 em conexões 4G.
- [ ] **Uptime:** Disponibilidade de 99.9% (máximo de 43 minutos de queda por mês).

## Métricas de Valor

- [ ] **Eficiência:** Redução do tempo de cadastro de produto de 15 minutos para menos de 3 minutos.
- [ ] **Retenção:** Menos de 5% de desinstalação nos primeiros 7 dias após o lançamento.
```

> **Razão**: Define números claros e prazos. Permite que a equipe de engenharia e produto saiba exatamente se o projeto foi um sucesso técnico e comercial.
