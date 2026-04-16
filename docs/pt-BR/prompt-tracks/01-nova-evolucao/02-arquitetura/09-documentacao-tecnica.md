# 09 - Documentação Técnica

## Documentação Viva e Automática

- [ ] **API Docs**: [ex: OpenAPI/Swagger, Redoc].
- [ ] **Documentação de Código**: [ex: JSDoc, GoDoc, Doxygen].
- [ ] **Diagramas**: [ex: Mermaid.js no Git, Lucidchart, Miro].

## Registros de Decisão Arquitetural (ADRs)

- Como as decisões técnicas complexas serão registradas? (ex: Pasta `/docs/adr` no repositório).
- O que deve ser incluído em um ADR? (Contexto, Opções, Decisão e Consequências).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 09 - Documentação Técnica

A gente explica o código por comentários. O resto o desenvolvedor descobre lendo as funções.
```

> **Razão**: Documentação não é apenas comentário de código. O "quem", "como" e "porquê" das decisões arquiteturais se perdem rapidamente sem um registro formal (ADR).

### ✅ Exemplo Bom

```markdown
# 09 - Documentação Técnica: Projeto Omni

## Estratégia

- **API**: Documentação automática via **Swagger UI** disponível em `/api/docs`.
- **Arquitetura**: Utilizaremos **ADRs** (Architectural Decision Records). Toda grande mudança técnica deve ser proposta como um novo arquivo em `.ai-backlog/adr/XXXX-titulo.md`.
- **Fluxos**: Diagramas de sequência gerados via **Mermaid.js** diretamente no README do módulo.

## Racional

Garantir que um novo desenvolvedor consiga entender o "porquê" de termos escolhido NoSQL em vez de Relacional daqui a 6 meses, sem precisar perguntar a quem já saiu da empresa.
```

> **Razão**: Cria um repositório de conhecimento sustentável e automatizado (Swagger e Mermaid), além de proteger o histórico de decisões (ADRs).
