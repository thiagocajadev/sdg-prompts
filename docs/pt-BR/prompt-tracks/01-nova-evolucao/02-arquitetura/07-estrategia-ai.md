# 07 - Estratégia de IA (Inteligência Artificial)

## Modelos e Integrações

- [ ] **Provedor de LLM (Large Language Model)**: [ex: OpenAI GPT-4, Anthropic Claude, Gemini, Llama local].
- [ ] **Arquitetura de Dados**: [ex: RAG (Retrieval-Augmented Generation) com banco vetorial Pinecone/Milvus].
- [ ] **Orquestração**: [ex: LangChain, LlamaIndex, SDKs nativos].

## Governança de Prompts e Custos

- Como os prompts serão versionados?
- Estratégia de Proxy: Verificação de segurança e controle de custos (rate limit por usuário).
- Gestão de Contexto: Quantidade máxima de tokens por requisição.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 07 - Estratégia de IA

Vamos usar o ChatGPT para responder as dúvidas dos usuários no site.
```

> **Razão**: Vago. Qual modelo específico (3.5 ou 4)? Como evitar que ele invente informações (alucinações)? Como monitorar o custo das chamadas?

### ✅ Exemplo Bom

```markdown
# 07 - Estratégia de IA: Assistente de Suporte V1

## Arquitetura de Inteligência

- **Modelos**: Utilizaremos o **GPT-4o-mini** via API da Azure OpenAI (garantindo privacidade de dados corporativos).
- **Estratégia**: Implementaremos **RAG** utilizando o banco de dados da central de ajuda como fonte da verdade. O sistema só responde o que estiver no contexto fornecido.

## Governança

- **Proxy de IA**: Todas as chamadas passam por um Gateway que limita cada usuário a 50 requisições por dia para proteger o orçamento do projeto.
- **Avaliação**: Utilizaremos o **RAGAS** para medir a fidelidade das respostas da IA semanalmente.
```

> **Razão**: Detalha a privacidade (Azure), a técnica contra alucinações (RAG) e a proteção financeira do projeto (Proxy e monitoramento).
