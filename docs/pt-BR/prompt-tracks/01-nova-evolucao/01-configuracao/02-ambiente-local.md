# 02 - Ambiente Local

## Pré-requisitos

- O que o desenvolvedor precisa ter instalado (ex: Docker, Taskfile, Make)?
- Versão mínima das ferramentas.

## Como Executar

1.  [ ] Clonar o repositório.
2.  [ ] Instalar as dependências.
3.  [ ] Iniciar os containers.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Ambiente Local

## Pré-requisitos

Docker e Python.

## Como Executar

Rode docker-compose up.
```

> **Razão**: E se o Docker Compose falhar? Onde estão as variáveis de ambiente (.env) necessárias?

### ✅ Exemplo Bom

```markdown
# 02 - Ambiente Local

## Pré-requisitos

Docker 24+, Python 3.11, Make 4.3+.

## Como Executar

1. Copie .env.example para .env.
2. Execute `make setup` para baixar imagens e rodar as migrações.
3. Teste o acesso em `localhost:8080/health`.
```

> **Razão**: Fornece versões mínimas, passos claros de configuração inicial (.env) e um teste final de verificação.
