# 03 - Baseline de Regressão (Cenários Atuais)

Como garantiremos que o novo sistema faz *exatamente* o que o antigo faz nos fluxos críticos? Precisamos de uma "foto" do comportamento atual antes de qualquer alteração.

## Fluxos Críticos e Dados de Saída

- Para a entrada `X`, o sistema legado hoje retorna a saída `Y`.
- [ ] Fluxo 1 (ex: Cálculo de taxa de juros).
- [ ] Fluxo 2 (ex: Geração de arquivo de remessa).

## Estratégia de Teste Espelho

- Como simularemos as mesmas entradas nos dois sistemas e compararemos as saídas automaticamente?

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 03 - Baseline de Regressão

Nós vamos testar manualmente os fluxos principais e ver se o resultado é parecido.
```

> **Razão**: "Parecido" não é suficiente em sistemas críticos (ex: financeiro). O teste manual é lento e não garante a precisão necessária para uma modernização invisível ao usuário.

### ✅ Exemplo Bom

```markdown
# 03 - Baseline de Regressão: Módulo de Cálculo

## Cenários de Ouro (Golden Sets)

Mapeamos 1.000 perfis de clientes reais (anonimizados) no banco legado.
- **Ação**: Executar o script de cálculo de juros para esses 1.000 casos e salvar os resultados em um arquivo CSV.
- **Validação**: O novo código em Node.js deve gerar um CSV idêntico (diferença de 0 centavos) para os mesmos 1.000 perfis.

## Testes de Integração Legados

Utilizaremos os 50 testes de integração existentes como barreira de segurança. Se o legado estiver quebrado hoje, não iniciaremos a modernização desse módulo até que o comportamento original seja estabilizado.
```

> **Razão**: Baseia-se em dados reais e automação (Golden Sets) para garantir que a lógica de negócio centenária do legado seja preservada perfeitamente na nova tecnologia.
