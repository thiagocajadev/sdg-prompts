# 01 - Escopo do Projeto e MVP (O Contrato Ágil / SPEC)

Este documento estabelece os limites exatos do que será — e do que NÃO será — entregue no projeto pago. O objetivo é evitar o desvio de escopo e garantir que a expectativa do cliente esteja alinhada com a entrega técnica.

## O Que Faremos (Dentro do Escopo / MVP)

- **Resumo Executivo**: Qual problema o cliente quer resolver? (ex: "Criar uma página para coletar e-mails para o lançamento de um produto digital").
- **Lista Bruta de Funcionalidades**:
  - Homepage com copy (redação publicitária) estático.
  - Formulário de captura de Nome e E-mail integrado ao Mailchimp.
- **Quais Telas (UI)** serão desenhadas? (Especificar se é página única, tamanhos de tela, etc.).

## Fora do Escopo

- O que será deixado para uma eventual V2/V3 e cobrado separadamente no futuro? (Isso protege você contra horas de trabalho não combinadas).
  - Ex: "Não construiremos um sistema de Admin/Login para a página neste momento."
  - Ex: "Não integraremos o envio automático de SMS nesta fase."

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# Escopo

Construir o site institucional para a clínica odontológica.
```

> **Razão**: Péssimo. Na última semana de entrega, o dentista pergunta: "E o sistema para agendar pacientes pelo WhatsApp através do site, como o concorrente tem? Você não fez?". Como o escopo não excluiu isso (Fora do Escopo), o cliente acha que você falhou ou que fará de graça.

### ✅ Exemplo Bom

```markdown
# SPEC-006: Site da Clínica Sorriso Feliz

## 1. Contexto
A clínica deseja presença digital para campanhas no Google Ads e uma forma eficiente de coletar leads qualificados no site.

## 2. Resultados Esperados (Success Metrics)
* Aumento de 20% no agendamento de consultas iniciais.
* Taxa de conversão da Landing Page acima de 5%.

## 3. Escopo e Cenários (User Stories)
* **Escopo:** Landing Page responsiva com formulário de contato e galeria de fotos.
* **Ação:** Redirect dinâmico para WhatsApp com mensagem pré-preenchida.

## 4. Restrições e Regras de Negócio
* O formulário deve validar e-mails corporativos.
* O site deve ser indexável (SEO básico).

## 5. Fora de Escopo
* Painel administrativo (CMS) para troca de fotos.
* Integração direta com softwares de agendamento médico.

## 6. Definição de Pronto (DoD)
- [ ] Formulário de contato verificado e enviando e-mails.
- [ ] Layout responsivo testado em mobile e desktop.
- [ ] Links de WhatsApp funcionais.
```

> **Razão**: Defesa absoluta. A agência sabe que precisará apenas de ferramentas simples como Netlify e E-mail. Quando o cliente trouxer a integração de agendamento, será um novo orçamento.
