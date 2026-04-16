# 01 - Visão de Modernização do Legado

Trabalhar em um sistema legado (Brownfield) exige uma mentalidade de cirurgião, não de demolidor. O objetivo é substituir partes do motor sem parar o carro em movimento.

## O Que é Sucesso na Modernização?

- Menos custos operacionais?
- Velocidade de desenvolvimento (Time to Market) aumentada?
- Eliminação de falhas de segurança críticas?

## O Custo de "Não Fazer Nada"

- Quanto a empresa perde hoje por causa das limitações deste sistema?
- Qual o risco de obsolescência ou falta de profissionais que dominam a tecnologia atual?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Visão do Legado

O sistema atual em PHP 5 é ruim e lento. Queremos reescrever tudo em Node.js.
```

> **Razão**: Vago e emocional. "Ser ruim" não justifica um investimento de meses ou anos. Por que o PHP 5 é o problema? Qual o risco real?

### ✅ Exemplo Bom

```markdown
# 01 - Visão de Modernização: Core Bancário

## O Que é Sucesso?

Reduzir o tempo de processamento do fechamento diário de 6 horas para menos de 30 minutos, permitindo operações em tempo real.

## O Custo de Não Fazer Nada

A versão atual da biblioteca de criptografia não recebe mais patches de segurança desde 2021. O risco de um vazamento de PII (dados sensíveis) é crítico, podendo gerar multas de até R$ 50M pela LGPD. Além disso, o custo de servidor (Cloud TCO) é 4x maior do que o necessário por falta de arquitetura elástica.
```

> **Razão**: Justifica a mudança através de números (6h vs 30min), riscos financeiros reais (multas da LGPD) e economia direta na conta da nuvem.
