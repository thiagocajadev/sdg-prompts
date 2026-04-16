# Guia de especificação de UI — Projetando interfaces para agentes de IA

> **Público:** Líderes técnicos e engenheiros que comunicam requisitos de UI (Interface do Usuário) por meio de especificações técnicas precisas.
>
> **Princípio fundamental:** Agentes de IA funcionam como motores de execução para design tokens (tokens de design — variáveis estéticas) e contratos de layout fornecidos. A precisão na densidade das informações iniciais reflete diretamente na qualidade do resultado.

---

## Por que as especificações de UI falham

Pedidos de UI (Interface do Usuário) vagos produzem resultados genéricos. Os agentes recorrem aos padrões mais comuns de seu treinamento quando existem lacunas na especificação. A padronização dos seguintes dados evita desvios arquiteturais:

1. **Sistema Visual** — paleta (OKLCH), preset (estilo pré-definido) e tipografia.
2. **Conteúdo Estrutural** — seções, hierarquia de componentes e fontes de dados.
3. **Estado de Execução** — interações e estados de ciclo de vida (carregamento, vazio ou erro).
4. **Restrições Negativas** — exclusões explícitas para evitar desvios lógicos.

---

## Template de prompt de UI

Copie e preencha este modelo ao solicitar qualquer trabalho de interface (página, componente ou tela):

```markdown
## Pedido de UI

### 1. Contexto

Para que serve esta interface? Quem a utiliza? Qual problema ela resolve?

- Público: [desenvolvedores / consumidores / operação interna / etc.]
- Propósito: [entrada de dados / visualização de dados / marketing / onboarding / etc.]

### 2. Identidade Visual

- Paleta: [Padrão Zinco+Azul | Personalizada: primária=___ secundária=___]
  OU: "Seguir a paleta existente do projeto"
- Preset: [BENTO | GLASS | CLEAN | MONO | NEOBRUTALISM | PAPER]
  OU: "Seguir o preset do projeto"
- Tipografia: [Precision/Dev | Premium/SaaS | Editorial | Bold | Corporate | Startup | Luxury]
  OU: "Usar as fontes do projeto"
- Tema: [Apenas claro | Apenas escuro | Ambos (padrão)]

### 3. Seções e Componentes

Liste cada seção visível em ordem, de cima para baixo:

- [ ] Nome da seção — breve descrição do conteúdo
- [ ] Nome da seção — breve descrição do conteúdo

### 4. Interações e Estados

- O que acontece no clique/hover (passar o mouse)/foco?
- Quais estados devem ser tratados? [Carregamento | Vazio | Erro | Desativado]
- Alguma animação? [Nenhuma | Entrada sutil | Explícita: ___]

### 5. Restrições

- O que NÃO deve ser incluído?
- Breakpoints (pontos de quebra) fixos ou restrições de layout?
- Alguma limitação de componente ou biblioteca?

### 6. Referência

- Página ou componente existente mais próximo para derivação: [nome ou "nenhum"]
- Referência visual (se houver): [URL ou descrição]
```

---

## Aprenda por exemplo

### ❌ Especificação Fraca (Baixa Densidade)

```markdown
Crie um dashboard para meu app SaaS com cards mostrando métricas e uma tabela.
Deixe com visual moderno e profissional com tema escuro.
```

> **Razão da falha:** A ausência de definição da paleta força a escolha arbitrária de cores. Termos como "moderno" e "profissional" são subjetivos e ativam padrões genéricos de treinamento da IA. A falta de enumeração das seções resulta em invenção de layout. O esquecimento dos estados (carregamento/vazio) gera contratos de execução incompletos.

---

### ✅ Especificação Forte (Alta Densidade)

```markdown
## Pedido de UI

### 1. Contexto

Dashboard de análise (analytics) para uma ferramenta B2B SaaS.
Público: equipe de operações internas (usuários avançados, 8+ horas/dia).
Propósito: monitorar a saúde do funil — volume, taxa de conversão e negócios bloqueados.

### 2. Identidade Visual

- Paleta: Padrão Zinco+Azul
- Preset: BENTO + GLASS
- Tipografia: Precision/Dev (JetBrains Mono para títulos, Inter para o corpo)
- Tema: Ambos (escuro como padrão)

### 3. Seções e Componentes

- [ ] Header (Cabeçalho) — logo do app à esquerda, avatar do usuário + notificações à direita.
- [ ] Linha de KPIs — 3 cards de métricas: Leads Totais, Taxa de Conversão, Tamanho Médio do Negócio.
- [ ] Gráfico do Funil — gráfico de barras horizontais por estágio (célula Bento, largura total).
- [ ] Tabela de Negócios — colunas ordenáveis: Negócio, Responsável, Estágio, Valor, Última Atividade.
- [ ] Sidebar (Barra lateral) — colapsável, links de navegação: Visão Geral / Negócios / Relatórios / Configurações.

### 4. Interações e Estados

- Cards de KPI: hover (passar o mouse) exibe tendência sparkline (últimos 30 dias).
- Tabela: destaque ao passar o mouse na linha, clique abre gaveta (drawer) com detalhes do negócio.
- Todas as seções de dados: necessário estado de skeleton loading (carregamento visual da estrutura).
- Estado vazio para a tabela: "Nenhum negócio corresponde aos seus filtros" + botão de limpar filtros.

### 5. Restrições

- Não utilize gráficos de pizza — apenas gráficos de barras e linhas.
- A tabela deve ter sticky-header (cabeçalho fixo) durante a rolagem.
- Sidebar (barra lateral) colapsada por padrão em telas < 1280px.
- Não adicione tooltips de onboarding ou modais.

### 6. Referência

- Derivar do componente DashboardPage existente.
- Referência visual: densidade de tabela do gerenciador de tarefas Linear.
```

> **Razão do sucesso:** A especificação da paleta garante a geração correta dos tokens OKLCH. O uso do preset define a linguagem visual. As seções enumeradas evitam a invenção de layout. Requisitos explícitos de estado garantem o tratamento de todo o ciclo de vida. Restrições negativas bloqueiam desvios comuns. A referência oferece ao motor de execução um ponto de partida e um alvo de densidade.

---

## Mapa de Identidade Visual

Correlacionando requisitos de UI com padrões técnicos:

| Você deseja...                       | Preset        | Sugestão de Paleta        | Tipografia      |
| :----------------------------------- | :------------ | :------------------------ | :-------------- |
| Dashboard B2B SaaS limpo             | BENTO + CLEAN | Zinco + Azul (H=250)      | Corporate       |
| Produto premium polido e em camadas  | BENTO + GLASS | Zinco + Violeta (H=290)   | Premium/SaaS    |
| Ferramenta de dev ou companheiro CLI | MONO          | Zinco monocromático       | Precision/Dev   |
| Landing page ou marketing ousado     | NEOBRUTALISM  | Croma Alto (Laranja H=70) | Bold/Expressive |
| Editorial ou docs com foco em texto  | PAPER         | Zinco + Ambar (H=80)      | Editorial       |
| Vibe de startup moderna ou app Next  | BENTO + CLEAN | Zinco + Azul (H=250)      | Startup/Modern  |
| Marca de luxo ou produto refinado    | GLASS + PAPER | Personalizada (perguntar) | Luxury/Refined  |

---

## Os 4 desvios mais comuns (e como evitá-los)

| Desvio               | Como aparece                            | Prevenção no prompt                                 |
| :------------------- | :-------------------------------------- | :-------------------------------------------------- |
| **Desvio de paleta** | Cores aleatórias, baixo contraste       | Sempre especifique a paleta ou diga "seguir o proj" |
| **Invenção de layout** | O agente adiciona seções não pedidas    | Liste cada seção explicitamente; adicione restrições |
| **Omissão de estado** | Falta carregamento/vazio/erro           | Enumere os estados na seção de interações           |
| **Poluição visual**  | Borda + sombra + cor de fundo excessiva | Especifique o preset — ele restringe a decoração    |

---

## Prompt Mínimo (Para momentos de pressa)

Quando a velocidade é mais importante que a precisão, forneça ao menos:

```markdown
## Pedido de UI (Mínimo)

Contexto: [1 frase — o que e para quem]
Paleta: [Padrão | Personalizada H=___]
Preset: [BENTO | GLASS | CLEAN | MONO | NEOBRUTALISM | PAPER]
Seções: [seção 1], [seção 2], [seção 3]
Estados obrigatórios: [Carregamento | Vazio | Erro]
NÃO inclua: [restrição 1], [restrição 2]
```

> **Razão:** Paleta e Preset são as duas entradas que evitam as falhas mais comuns. Todo o resto pode ser ajustado depois. Nunca omita esses dois.

---

> [!TIP]
> **A iteração técnica é contínua.** Uma especificação bem estruturada alcança alta precisão na primeira tentativa. Utilize prompts de refino focados em seções que exijam maior densidade.
