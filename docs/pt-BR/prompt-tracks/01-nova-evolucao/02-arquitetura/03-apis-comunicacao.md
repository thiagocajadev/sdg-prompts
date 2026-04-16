# 03 - APIs e Comunicação

## Estilo de Comunicação

- [ ] **REST (REpresentational State Transfer)**: Síncrona, baseada em recursos HTTP.
- [ ] **GraphQL**: Lado do cliente define o formato dos dados.
- [ ] **gRPC (Google Remote Procedure Call)**: Alta performance, baseada em Protocol Buffers.
- [ ] **Asíncrona (Event-Driven)**: Baseada em Message Brokers ( RabbitMQ, Kafka, SQS).

## Contratos e Documentação

Como os contratos das APIs serão mantidos e compartilhados entre as equipes?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - APIs e Comunicação

Vamos usar REST para tudo e mandar JSON.
```

> **Razão**: Vago. Como as APIs são documentadas? Existe algum gateway? Como lidamos com falhas de comunicação?

### ✅ Exemplo Bom

```markdown
# 03 - APIs e Comunicação: Ecossistema Checkout

## Estilo de Comunicação

- **REST (JSON)**: Para comunicação entre o Frontend e o Backend via API Gateway (Kong).
- **gRPC**: Para comunicação interna entre os microserviços de Inventário e Preço (alta performance).
- **Event-Driven (RabbitMQ)**: Para notificar o serviço de Logística quando um pagamento for confirmado (asíncrono).

## Contratos

Utilizaremos **OpenAPI (Swagger)**. O arquivo `swagger.yaml` é a fonte da verdade e o código é gerado automaticamente a partir dele.
```

> **Razão**: Detalha a tecnologia para cada caso de uso específico (síncrona vs asíncrona) e estabelece o Swagger como o contrato formal (fonte da verdade).
