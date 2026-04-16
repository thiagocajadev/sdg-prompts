# 02 - Estratégia de Versionamento e Coexistência

Como o novo sistema e o legado viverão juntos sem corromper dados um do outro durante a transição? Esta é a fase mais crítica da modernização.

## Pontes de Integração e Versionamento

- Como sinalizaremos para os clientes da API qual versão eles devem usar? (ex: Header `X-API-Version`, URL `/v1/` vs `/v2/`).
- Onde os dados serão a "fonte da verdade" durante a transição? (ex: O banco legado continua soberano e o novo banco é apenas uma réplica até o desligamento total).

## Gestão de Tráfego (Proxy/Gateway)

- Utilizaremos um roteador inteligente para enviar uma porcentagem do tráfego para a nova versão? (Canary Deployment).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Versionamento e Coexistência

Nós criamos uma branch `new-version` e quando estiver pronto trocamos a URL no DNS.
```

> **Razão**: Abordagem arriscada. Não lida com a coexistência de dados (o que acontece se um usuário criar um registro na versão nova e outro usuário tentar ler na versão velha?).

### ✅ Exemplo Bom

```markdown
# 02 - Versionamento e Coexistência: Módulo Fiscal

## Sincronização de Dados

Utilizaremos o padrão **Parallel Run** (Execução Paralela):
1. O novo sistema gravará os dados em seu próprio banco de dados (PostgreSQL).
2. Imediatamente após, ele disparará um evento para uma fila asíncrona que espelhará essa gravação no banco legado (Oracle).
3. **Fonte da Verdade**: Durante os primeiros 30 dias, o Banco Oracle permanece como a verdade absoluta para auditoria.

## Versionamento de API

- Legado: `api.empresa.com.br/v1/...`
- Novo: `api.empresa.com.br/v2/...`
Utilizaremos o **Kong API Gateway** para rotear o tráfego com base na URL.
```

> **Razão**: Estabelece uma estratégia de espelhamento que protege a integridade dos dados históricos e permite uma reversão rápida se o novo sistema apresentar instabilidade.
