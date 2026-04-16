# Guia: Escrita de Prompts Criativos (Multi-Engine)

> [!IMPORTANT]
> Este guia é destinado a Agentes de IA e desenvolvedores que utilizam IA generativa para recursos criativos. O foco está na ponte entre a intenção e o resultado visual.

## Estrutura do "Prompt Mestre"

Para resultados de alta qualidade, sempre estruture suas descrições visuais utilizando a tríade **"Escopo-Estilo-Detalhe"**:

1. **Escopo**: Qual é o objeto físico? (ex: "Um logo 2D minimalista", "Um mockup de alta fidelidade para landing page").
2. **Estilo**: Qual é a escola artística? (ex: "Bauhaus", "Glassmorphism" (efeito vário fosco), "Neobrutalista", "Design Suíço").
3. **Detalhe**: Iluminação, textura e restrições técnicas (ex: "Iluminação volumétrica", "Acabamento fosco", "Estilo vetorial --ar 1:1").

## Nuances Específicas de cada Motor (Engines)

### 1. Gemini (Visão e Geração)

- **Ponto forte**: Compreensão de lógica espacial complexa e metadados de "Writing Soul" (estético/voz do projeto).
- **Dica**: Forneça o conteúdo do arquivo `dna-marca.md` diretamente ao Gemini para extrair especificações visuais antes da escrita do prompt.
- **Uso**: Recomendado para gerar a **Estratégia de Marca** e layouts complexos de **Blueprint de Landing Page**.

### 2. GPT-4o / DALL-E 3

- **Ponto forte**: Precisão no texto dentro da imagem e detalhes ilustrativos.
- **Dica**: Quando precisar de texto na imagem (ex: nome no Logo), coloque-o entre "aspas".
- **Uso**: Ideal para **Logos** e fundos rápidos para **Redes Sociais**.

### 3. Claude 3.5+

- **Ponto forte**: Engenharia de prompts de alta fidelidade (O "Orquestrador").
- **Dica**: Peça ao Claude para gerar 3 variações de um prompt (Fotorrealista, Abstrato, Minimalista) antes de escolher.
- **Uso**: Recomendado para **Refinamento de Estilos** e **Planejamento de Carrosséis**.

## Anti-padrões na escrita de Prompts

- **Evite Indecisões**: Não diga "Um tipo de logo vermelho". Diga "Logo vermelho carmesim com detalhes dourados".
- **Evite Estilos Vagos**: Não diga "Bonito". Diga "Iluminação cinematográfica com resolução 8k".
- **Evite a falta de AR**: Nunca esqueça o aspect ratio (proporção de tela), que é obrigatório para Redes Sociais.
