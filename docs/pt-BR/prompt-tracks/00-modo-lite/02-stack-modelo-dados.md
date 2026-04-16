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
# SPEC-007: Stack e Ambiente da LP Sorriso Feliz

## 1. Contexto
Definição da infraestrutura mínima para entrega rápida e segura da Landing Page da Clínica.

## 2. Resultados Esperados (Success Metrics)
* Tempo de carregamento da página (LCP) < 1.5s.
* Setup inicial do desenvolvedor em menos de 10 minutos.

## 3. Escopo e Cenários (User Stories)
* **Ambiente:** Node.js v18.x + Next.js (Pages Router) + TailwindCSS.
* **Dados:** Tabela `leads` no Supabase (id, name, email, whatsapp).

## 4. Restrições e Regras de Negócio
* Uso obrigatório de `React Hook Form` para validação de formulários.
* Acesso ao banco restrito via políticas de RLS no Supabase.

## 5. Fora de Escopo
* Configuração de ambiente de CI/CD complexo (foco em vercel manual).
* Cache de borda via Redis (foco em custo zero).

## 6. Definição de Pronto (DoD)
- [ ] Arquivo `.env.example` funcional.
- [ ] Tabela de leads criada e acessível.
- [ ] Comando `npm run dev` executando sem erros.
```

> **Razão**: Direto ao ponto e prático. Um segundo desenvolvedor Frontend entrará no projeto, clonará, entenderá os formulários e o executará em menos de 10 minutos de leitura.
