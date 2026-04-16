# 01 - RFC (Request for Comments) e Mudanças de Arquitetura

## Motivação e Problema da Mudança

- O que motivou a evolução desta arquitetura em um sistema já vivo (ex: gargalo de performance no banco relacional obrigando o uso de NoSQL, ou troca de provedor de nuvem)?
- Qual o impacto de *Não Fazer Nada* (Status Quo) comparado ao esforço da mudança?

## Alternativas Consideradas

- Quais foram os "Caminhos B e C" que o time rejeitou antes de propor o "Caminho A"?
- Por que a opção escolhida é a mais adequada hoje (Custo x Retorno)?

## Plano de Execução e Rollback (Reversão)

- Como a base de código atual será migrada para a nova fundação sem *Downtime* (tempo de inatividade)?
- Qual o limite aceitável de erros para abortar a mudança e retornar ao estado anterior?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - RFC: Trocar Banco de Dados

## Motivação

O MongoDB está lento.

## Alternativas

O PostgreSQL é melhor.

## Execução

Vamos fazer um script no sábado.
```

> **Razão**: RFC sem base científica. Desconsidera que não existe "bala de prata" e tenta infligir uma mudança radical na estrutura sem analisar o custo de migração de dados e o tempo fora do ar (*downtime*).

### ✅ Exemplo Bom

```markdown
# 01 - RFC: Desacoplar Módulo de Notificação para Mensageria (RabbitMQ)

## Motivação

**Problema**: Requisições de e-mail síncronas via API causam *Timeouts* de 5s em horários de pico (Black Friday), travando as threads da aplicação principal.

## Alternativas Consideradas

1. **Pagar por instâncias maiores (Scale Up)**: Rejeitado por não ser financeiramente escalável a longo prazo.
2. **RabbitMQ (Escolhido)**: Garante asincronicidade com custo zero de licença.

## Execução

- **Shadow**: Na primeira semana, o RabbitMQ será habilitado mas publicará logs invisíveis enquanto o código síncrono continua ativo, apenas para checar consistência.
- **Rollback**: Se a taxa de sucesso cair abaixo de 99.9%, desligamos a *Feature Flag* `UseAsyncNotifications` no dashboard remoto em tempo real, sem necessidade de *Deploy*.
```

> **Razão**: Abordagem madura, avaliando custos financeiros e garantindo que o plano não cause pânico ao negócio por possuir travas de segurança (*Feature Flags*) em tempo real.
