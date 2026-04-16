# 05 - Auditoria de Segurança

## Vetores de Ataque Mapeados

- [ ] **SQL Injection**: Proteção garantida pelo uso de ORMs (Object-Relational Mapping) ou Query Builders com parametrização automática.
- [ ] **XSS (Cross-Site Scripting)**: Sanitização de entradas no Frontend e Backend.
- [ ] **CSRF (Cross-Site Request Forgery)**: Uso de tokens de validação em formulários e APIs.

## Ciclo de Auditoria

Como e quando o código será testado contra vulnerabilidades? (Analise estática via Snyk/SonarQube, Pentests manuais).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 05 - Auditoria de Segurança

Nós vamos conferir se o código está seguro antes de subir.
```

> **Razão**: Vago. O que significa "conferir"? Quais ferramentas serão usadas para automatizar essa verificação?

### ✅ Exemplo Bom

```markdown
# 05 - Auditoria de Segurança: API Gateway

## Ciclo de Auditoria

- **Estática (SAST)**: Utilizaremos o **Snyk** integrado ao CI/CD para bloquear qualquer PR que introduza dependências com vulnerabilidades conhecidas.
- **Dinâmica (DAST)**: Realizaremos um scan mensal automático utilizando o **OWASP ZAP** contra o ambiente de Staging.

## Proteções Específicas

- **CORS (Cross-Origin Resource Sharing)**: Restrito apenas aos domínios oficiais da empresa.
- **Rate Limit**: Proteção contra Brute Force (força bruta) na rota de login (limitado a 5 tentativas por minuto por IP).
```

> **Razão**: Define ferramentas de mercado (Snyk, OWASP ZAP) e estabelece políticas reais de bloqueio no ambiente de integração contínua (CI).
