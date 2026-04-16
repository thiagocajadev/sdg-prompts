# 06 - Design System e UX (Experiência do Usuário)

## Identidade Visual e Tokens

- **Paleta**: Escolha da paleta OKLCH e regra de distribuição de cor (ex: 60-30-10).
- **Tipografia**: Definição das fontes de Display (títulos) e Body (corpo).
- **Preset de UI**: Escolha do estilo visual padrão (ex: BENTO, GLASS, CLEAN).

## Acessibilidade e Padrões UX

- Foco em **WCAG AA** (padrão internacional de acessibilidade na web).
- Navegação por teclado e semântica HTML.
- Estados de UI: Tratamento obrigatório de Loading, Empty e Error.

---

## Aprenda por Exemplos

### ❌ Exemplo Ruim

```markdown
# 06 - Design System e UX

O site vai ser bonito e fácil de usar. Vamos usar as cores da logo.
```

> **Razão**: Vago. O que significa "fácil de usar"? Quais são os tokens de acessibilidade? Como os componentes se comportam em diferentes telas?

### ✅ Exemplo Bom

```markdown
# 06 - Design System e UX: Portal do Paciente

## Identidade Visual

- **Paleta**: Zinco para neutros e Azul Primário (H=250) para ações.
- **Preset**: **CLEAN + GLASS** para passar a sensação de higiene e tecnologia médica.

## Experiência do Usuário (UX)

- **Acessibilidade**: Contraste mínimo de 4.5:1 em todos os textos. Suporte completo a leitores de tela via ARIA labels.
- **Micro-interações**: Feedback visual (spinner ou skeleton) dentro de 100ms após qualquer interação que dependa da rede.
```

> **Razão**: Define padrões técnicos (contraste, ARIA, tempos de resposta) que garantem uma experiência de uso profissional e inclusiva.
