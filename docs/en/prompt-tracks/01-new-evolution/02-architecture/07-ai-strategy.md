# 06 - AI Strategy

## AI Engine

- Which models (OpenAI, Claude, Llama 3) and what execution infrastructure?
- Local Model (Ollama) or Cloud (Vertex AI)?

## Integration and Tools

- Will we use the MCP (Model Context Protocol) to connect tools?
- How will RAG (Retrieval Augmented Generation) access external data?
- Agents (LangChain, CrewAI) or pure LLM?

## AI Privacy and Governance

- How do we prevent PII (Personally Identifiable Information) leakage in prompts?
- Is there an audit of AI inputs and outputs?

## Costs and Limits

- Monthly budget per million tokens (Input/Output).
- Rate limits per user.

---

## Learn by Examples

### ❌ Bad Example

```markdown
# 06 - AI Strategy

## AI Engine

Use ChatGPT for everything.

## Integration

Chat on the interface.

## Privacy

AI is smart and knows what it's doing.
```

> **Rationale**: Ignores token costs, privacy risks, and infrastructure (API SLA).

### ✅ Good Example

```markdown
# 06 - AI Strategy

## AI Engine

GPT-4o via Azure OpenAI (Ensures data does not train the model).

## Integration and Tools

- MCP (Model Context Protocol) to allow the AI to execute internal audit scripts.
- RAG via Pinecone (Vector DB) with 1000-token semantic chunking.

## Privacy

PII Preservation: Regex intercepting Tax IDs (CPFs) and names before sending to the API.

## Costs

- Budget: $5,000/month.
- Limit: 50 requests/hour per user.
```

> **Rationale**: Defines robust technological choices (Azure OpenAI, Pinecone, MCP), data governance (PII Regex), and financial control (tokens/requests).
