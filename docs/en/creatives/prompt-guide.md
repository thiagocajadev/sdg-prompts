# Guide: Creative Prompting (Multi-Engine)

> [!IMPORTANT]
> This guide is for AI Agents and Developers using Generative AI for creative assets. It focuses on the bridge between intent and visual output.

## The "Master Prompt" Structure

For high-end results, always structure your visual descriptions using the **"Scope-Style-Detail"** triad:

1. **Scope**: What is the physical object? (e.g., "A minimalist 2D logo", "A high-fidelity landing page mockup").
2. **Style**: What is the artistic school? (e.g., "Bauhaus", "Glassmorphism", "Neobrutalist", "Swiss Design").
3. **Detail**: Lighting, texture, and technical constraints (e.g., "Volumetric lighting", "Matte finish", "Vector style --ar 1:1").

## Engine-Specific Nuances

### 1. Gemini (Vision & Gen)

- **Strength**: Understanding complex spatial logic and "Writing Soul" metadata.
- **Tip**: Provide the `brand-dna.md` content directly to Gemini to extract visual specs before prompting.
- **Usage**: Use for generating the **Brand Strategy** and complex **Landing Page Blueprints**.

### 2. GPT-4o / DALL-E 3

- **Strength**: Text accuracy and illustrative precision.
- **Tip**: When text is needed in the image (e.g., Logo name), put it in "quotes".
- **Usage**: Best for **Logos** and **Quick Social Media backgrounds**.

### 3. Claude 3.5+

- **Strength**: High-fidelity prompt engineering (The "Orchestrator").
- **Tip**: Ask Claude to generate 3 variations of a prompt (Photorealistic, Abstract, Minimalist) before choosing.
- **Usage**: Use for **Refining Styles** and **Planning Carousels**.

## Prompting Anti-Patterns

- **Avoid Hedging**: Don't say "A sort of a red logo". Say "Crimson red logo with gold accents".
- **Avoid Vague Style**: Don't say "Beautiful". Say "Cinematic lighting with 8k resolution".
- **Avoid Missing AR**: Never omit the aspect ratio (mandatory for Social Media).
