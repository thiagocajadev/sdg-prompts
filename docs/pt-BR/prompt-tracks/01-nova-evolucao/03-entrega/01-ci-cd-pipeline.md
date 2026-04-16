# 01 - Pipeline de CI/CD (Integração e Entrega Contínua)

O pipeline é a espinha dorsal biológica do seu sistema de entrega. Ele garante que cada linha de código seja validada e entregue sem intervenção manual e sem o risco do "funcionou na minha máquina".

## Estágios do Pipeline

1.  **Build**: Compilação e verificação de integridade dos pacotes.
2.  **Lint e Segurança**: Verificação estática de estilo de código e busca por vulnerabilidades em dependências.
3.  **Testes**: Execução de Testes Unitários e de Integração.
4.  **Deploy em Staging (ambiente de homologação)**: Publicação automática para validação da equipe interna.
5.  **Smoke Tests (Testes de Fumaça)**: Validação rápida das rotas críticas em Staging.
6.  **Deploy em Produção**: Promoção do código aprovado para o usuário final.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 01 - Pipeline de CI/CD

Nós usamos o GitHub Actions. Ele roda os testes e depois sobe para a Vercel.
```

> **Razão**: Vago. Como lidamos com falhas no pipeline? Existe algum teste pós-deploy? Como é a estratégia de rollback se algo quebrar em produção?

### ✅ Exemplo Bom

```markdown
# 01 - Pipeline de CI/CD: Projeto V3

## Estratégia de Deploy

- **Estratégia**: Blue-Green Deployment (evita tempo de inatividade ao alternar entre duas versões em paralelo).
- **Garantia**: O comando `npm run build` deve passar com 0 avisos (warnings).
- **Segurança**: O pipeline bloqueia o deploy se encontrar segredos (tokens) expostos no código.

## Ambientes

- **Pushes na develop**: Vão para `staging.meuapp.com`.
- **Merge na main**: Dispara um **Canary Release** para 10% dos usuários iniciais em `meuapp.com`.
```

> **Razão**: Define estratégias reais de disponibilidade (Blue-Green/Canary) e estabelece travas de segurança automáticas.
