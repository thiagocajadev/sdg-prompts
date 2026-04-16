# 11 - Privacidade e Conformidade de Dados

A arquitetura deve nascer juridicamente protegida contra multas milionárias e em conformidade com as leis de proteção de dados (LGPD/GDPR).

## Estratégia Privacy By Design

- [ ] **Mapeamento de PII (Personally Identifiable Information — informações de identificação pessoal)**: Quais dados sensíveis estamos coletando (CPF, e-mail, telefone)?
- [ ] **Mascaramento de Logs**: Dados sensíveis nunca devem aparecer em texto limpo nos logs (obsfuscation).
- [ ] **Direito ao Esquecimento**: Como os dados de um usuário serão excluídos definitivamente se ele solicitar?

## Conformidade e Auditoria

- Onde os dados estão fisicamente armazenados (Soberania de Dados)?
- Como garantimos que apenas as pessoas autorizadas acessem os dados sensíveis?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Privacidade

Nós salvamos os dados do cliente no banco MySQL e temos SSL no site. O banco está criptografado no disco da Amazon.
```

> **Razão**: Simplista. Criptografar o disco e usar SSL evita invasões de hackers, mas não resolve a conformidade real (LGPD/GDPR) sobre o uso e a exclusão da informação pelo próprio dono do dado.

### ✅ Exemplo Bom

```markdown
# Privacy By Design: Módulo de Perfil V2

- **PII Mapeado (Tabela `Users`):** As colunas `cpf`, `phone` e `email` são classificadas como PII de nível A.
- **Mascaramento de Logs**: Nossa biblioteca `pino-logger` foi configurada nativamente para ofuscar estas chaves. Elas NUNCA aparecerão em texto limpo no Datadog.
- **Exclusão (LGPD):** Caso a rota `DELETE /account` seja disparada:
  1. Os dados reais de PII na tabela `Users` sofrem um *Hard Delete*.
  2. O histórico em `Sales` permanece (Exigência Legal/Fiscal), mas sua Chave Estrangeira é mapeada para um sistema interno de `anon-ledger`, impedindo a identificação primária.
```

> **Razão**: A arquitetura já prevê a perda de dados "pai" sem quebrar o sistema e garante que logs não vazem informações sensíveis.
