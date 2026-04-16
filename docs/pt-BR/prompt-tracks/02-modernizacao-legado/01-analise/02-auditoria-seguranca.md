# 02 - Auditoria de Segurança do Legado

Sistemas legados são frequentemente o elo mais fraco na segurança de uma empresa. Muitas vulnerabilidades são introduzidas por falta de conhecimento das ameaças modernas ou por tecnologias que não possuem mais defesas ativas.

## Superfície de Ataque e Riscos Mapeados

- [ ] Métodos de autenticação obsoletos ou senhas armazenadas sem hash forte.
- [ ] Endpoints de API sem limites de taxa (Rate Limit) ou validação de entrada.
- [ ] Vazamento de segredos (chaves de API) no histórico do Git ou arquivos de configuração.

## Plano de Contenção Imediata

Existem falhas que precisam ser corrigidas AGORA, antes mesmo de iniciar a modernização? (Ex: Troca de chaves comprometidas).

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 02 - Auditoria de Segurança

Nós vimos que o login está inseguro e vamos consertar isso na nova versão.
```

> **Razão**: Perigoso. Se o sistema está vivo hoje e o login está inseguro, esperar 3 meses pela nova versão é um convite para um desastre. Qual a ação imediata para mitigar o risco?

### ✅ Exemplo Bom

```markdown
# 02 - Auditoria de Segurança: Portal do Cliente

## Riscos Críticos Encontrados

- **Insecure Direct Object Reference (IDOR)**: Um usuário logado consegue visualizar o documento de outro usuário apenas alterando o ID na URL (`/docs/123` para `/docs/124`).
- **Segredos Expostos**: A chave de produção do AWS S3 está em texto limpo no arquivo `config.php`.

## Contenção Imediata

1. Habilitaremos um WAF (Web Application Firewall) para bloquear tentativas de exploração conhecidas.
2. Iniciaremos o rodízio imediato das chaves da AWS e moveremos para variáveis de ambiente protegidas.
```

> **Razão**: Identifica falhas graves (IDOR) e propõe soluções de contenção imediatas que não dependem do fim do projeto de modernização.
