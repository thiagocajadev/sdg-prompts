# 02 - Aprovação da Refatoração de Preparação

## Checklist de Artefatos

- [ ] 01-backlog-limpeza.md (Higiene concluída)

## Aprovação Técnica

- **Líder de Engenharia**: [Assinatura/Data]
- **QA / Test Lead**: [Assinatura/Data]

## Definição de Prontidão (Ready for Migration)

- [ ] Código morto removido e verificado (Lighthouse/Istanbul).
- [ ] Pontos de acoplamento de banco de dados mapeados e isolados.
- [ ] Variáveis de ambiente configuradas e segredos removidos dos arquivos de código.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Aprovação da Refatoração

## Checklist

- [x] Limpamos o código e agora está mais fácil de ler.

## Definição de Prontidão

- [x] Podemos começar a migrar o banco de dados.
```

> **Razão**: Vago. Como a equipe de QA garantiu que a "limpeza" do código legado não causou efeitos colaterais em áreas que não foram tocadas?

### ✅ Exemplo Bom

```markdown
# 02 - Aprovação da Refatoração: Prep-V2

## Aprovação Técnica

- **Engenharia**: Robert Coast (12/06/2026) – Confirmação de que 2.000 linhas de código morto foram removidas.
- **QA**: Sarah Lane (13/06/2026) – Bateria de testes de regressão passou com 0 bugs após a remoção do código morto.

## Definição de Prontidão

- [x] O arquivo `Settings.xml` não possui mais credenciais de banco (agora via Vault/Env).
```

> **Razão**: Oferece evidências numéricas de redução de complexidade e confirmação de segurança (remoção de credenciais), garantindo que o legado está pronto para ser "estrangulado" com segurança.
