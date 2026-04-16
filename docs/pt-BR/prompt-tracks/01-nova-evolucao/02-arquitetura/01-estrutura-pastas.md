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
# SPEC-011: Estrutura de Pastas Hexagonal

## 1. Contexto
Organizar o repositório para garantir alta manutenibilidade e separação rigorosa entre domínio e infraestrutura.

## 2. Resultados Esperados (Success Metrics)
* Zero dependências cíclicas entre pacotes.
* Possibilidade de trocar o banco de dados sem alterar a lógica de negócio.

## 3. Escopo e Cenários (User Stories)
* **Estrutura:** `/domain` (Entidades), `/application` (Casos de Uso), `/infrastructure` (Drivers).
* **Mapeamento:** `/infrastructure/persistence` (PostgreSQL), `/infrastructure/http` (REST).

## 4. Restrições e Regras de Negócio
* A pasta `/domain` não pode importar nenhuma biblioteca externa de infraestrutura.
* Comunicação entre camadas deve ocorrer estritamente através de interfaces (Ports).

## 5. Fora de Escopo
* Definição de estrutura para micro frontend (foco no backend).
* Configurações de monorepo avançado.

## 6. Definição de Pronto (DoD)
- [ ] Árvore de diretórios inicial criada.
- [ ] Boilerplate seguindo o padrão Hexagonal validado.
```

> **Razão**: Define o propósito de cada pasta e justifica a estrutura com base na manutenibilidade (facilidade de alteração).
