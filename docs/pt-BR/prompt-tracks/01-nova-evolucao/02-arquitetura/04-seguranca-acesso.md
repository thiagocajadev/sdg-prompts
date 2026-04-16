# 04 - Segurança e Acesso

## Modelo de AuthN/AuthZ (Autenticação e Autorização)

- [ ] **Provedor**: [ex: Supabase Auth, Auth0, Firebase Auth, JWT próprio].
- [ ] **Mecanismo**: [ex: RBAC (Role-Based Access Control), ABAC (Attribute-Based Access Control)].
- [ ] **Tokens**: [ex: JWT com expiração de 15min + Refresh Token de 7 dias].

## Proteção de Dados e Infraestrutura

- Como as chaves de API e segredos são gerenciados?
- Uso de HTTPS/TLS e proteção contra ataques comuns.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 04 - Segurança e Acesso

Vamos usar login com e-mail e senha. As senhas ficam no banco criptografadas.
```

> **Razão**: Vago e inseguro. Qual algoritmo de hash? Como funciona o controle de permissões (quem pode acessar o quê)?

### ✅ Exemplo Bom

```markdown
# 04 - Segurança e Acesso: Plataforma de Admin

## Autenticação (AuthN)

Utilizaremos o **Supabase Auth** com persistência em JWT.
- **MFA (Multi-Factor Authentication)**: Obrigatório para usuários com nível de acesso administrativo.

## Autorização (AuthZ)

- **Modelo RBAC**: Definiremos três níveis de acesso: `Viewer` (leitura), `Editor` (escrita) e `Admin` (gestão de usuários).
- **RLS (Row Level Security)**: Aplicaremos políticas de segurança diretamente no PostgreSQL para garantir que um usuário só acesse os seus próprios registros.
```

> **Razão**: Define ferramentas específicas (Supabase, RBAC, RLS) e estabelece camadas de defesa profundas, como o MFA para administradores.
