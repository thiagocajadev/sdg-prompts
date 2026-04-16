# 01 - Estrutura de Pastas

## Padrão Arquitetural Escolhido

- [ ] **Hexagonal (Ports & Adapters)**: Separação rigorosa da lógica de negócio de infraestrutura.
- [ ] **Vertical Slice**: Organização por funcionalidades (features) em vez de camadas técnicas.
- [ ] **Layered (N-Camadas)**: Divisão clássica (Controllers, Services, Repositories).

## Mapa de Diretórios

Descreva a árvore de diretórios do projeto:

```text
src/
  domain/       # Regras de negócio puras (entidades e casos de uso)
  application/  # Serviços e orquestração
  infrastructure/ # Implementações técnicas (DB, API, Filas)
  main/         # Composição e inicialização
```

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Estrutura de Pastas

Vamos usar o padrão do framework.
/controllers
/models
/views
```

> **Razão**: Vago e dependente demais do framework (acoplamento). Não explica onde fica a lógica de negócio complexa.

### ✅ Exemplo Bom

```markdown
# 01 - Estrutura de Pastas: Arquitetura Hexagonal

## Mapa de Diretórios

- **/domain**: Contém as Entidades ricas e as Interfaces (Ports) do sistema. Zero dependência externa.
- **/application**: Casos de Uso (Use Cases) que orquestram o domínio.
- **/infrastructure**:
  - **/persistence**: Implementações do PostgreSQL (Adapters).
  - **/http**: Controladores e rotas da API.

## Racional

Esta estrutura foi escolhida para permitir a troca do banco de dados ou da interface de entrada (ex: de REST para gRPC) sem tocar na lógica de negócio central.
```

> **Razão**: Define o propósito de cada pasta e justifica a estrutura com base na manutenibilidade (facilidade de alteração).
