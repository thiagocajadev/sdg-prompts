# 02 - Stack Técnica e Dados Essenciais

Em projetos de ritmo acelerado, você não deve perder tempo justificando ADRs (registros de decisão técnica) complexos. Utilize o que permite entregar rapidamente e documente aqui apenas como o próximo programador pode executar o código.

## Principais Tecnologias

- Frontend Framework / SSR (Server-Side Rendering — renderização no lado do servidor): (Ex: Next.js, Vite + React).
- Estilização (Styling): (Ex: TailwindCSS V3, Radix UI).
- CMS / Backend-As-A-Service (Se aplicável): (Ex: Supabase, Strapi, Sanity).

## Como Executar o Projeto (Experience do Desenvolvedor - DX)

1. Instalar pacotes via `npm install` ou gerenciador de preferência.
2. Incluir o `.env` (especificar onde obter um de desenvolvimento).
3. Executar o comando `npm run dev`.

## Modelo de Dados Mínimo Viável (DB Schema)

- Se houver um banco de dados, cole apenas um Schema (esquema) minimalista ou texto descrevendo as coleções essenciais para que os desenvolvedores não precisem "pescar no escuro".
- Se houver um _Headless_ CMS (gestor de conteúdo sem interface) por trás, mapeie os tipos principais (_Types_).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Stack

Usando React. Para ligar rode npm start.
O banco de dados tem uma tabela de `leads`.
```

> **Razão**: Omite dezenas de bibliotecas secretas. Um desenvolvedor junior clona o projeto, roda npm start e a tela fica branca porque ele não configurou o `.env` do Supabase e nem sabia que você usou Vercel.

### ✅ Exemplo Bom

```markdown
# Stack e Ambiente: LP Sorriso Feliz

## Configuração Local

1. `git clone` seguido de `npm ci` (estamos utilizando a versão `v18.x` no nvm).
2. Solicite acesso ao DevSupabase no grupo do slack.
3. Copie o arquivo `.env.example` para `.env.local` e rode `npm run dev` na porta 3000.
   **Frontend:** Next.js (Pages Router) + TailwindCSS. Formulário construído com `React Hook Form`.

## Entidades Mínimas do Supabase

Para focar estritamente em contatos, temos apenas 1 tabela gerenciada no Supabase Cloud de Desenvolvimento:

- `leads (id: UUID, name: string, email: string, whatsapp: string, created_at: timestamp)`
```

> **Razão**: Direto ao ponto e prático. Um segundo desenvolvedor Frontend entrará no projeto, clonará, entenderá os formulários e o executará em menos de 10 minutos de leitura.
