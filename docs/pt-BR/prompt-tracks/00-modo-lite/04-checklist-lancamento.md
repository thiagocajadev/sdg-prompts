# 04 - Checklist de Lançamento

Lançar um MVP ou Landing Page rapidamente não significa apenas subir arquivos no servidor. Seu cliente espera polimento, velocidade e um SEO impecável para compartilhamento. Este é o portão final, sua Garantia de Qualidade (QA) pessoal.

## Configuração de Domínio e Segurança

- [ ] O domínio personalizado está vinculado no servidor (Vercel/Netlify/Cloudflare)?
- [ ] O certificado SSL (HTTPS) está ativo (Cadeado Verde)?
- [ ] Você testou o acesso sem 'www' (ex: `site-cliente.com.br`) e o tráfego foi redirecionado corretamente para evitar penalidades do Google por conteúdo duplicado?
- [ ] Referência: # 01 - Escopo e MVP (O Contrato Ágil / SPEC)

## SEO e Compartilhamento Social (OpenGraph)

- [ ] As `Meta Tags` básicas (Título, Descrição) foram declaradas para o Google?
- [ ] As imagens de `Og:Image` (OpenGraph — metadados para redes sociais) estão hospedadas para que o link apareça com uma miniatura bonita ao ser postado no WhatsApp ou Instagram?
- [ ] Existe um `Favicon` (ícone da aba do navegador) real ou você esqueceu o logo padrão da plataforma de hospedagem?

## Integrações em Produção e Performance (Core Web Vitals)

- [ ] As tags do Google Analytics (GA4) e Meta Pixel (Facebook) foram injetadas para que o time de Marketing possa rastrear os acessos?
- [ ] A pontuação no Chrome Lighthouse para Mobile é superior a 90 em Performance e Acessibilidade? (Utilize WebP para imagens e reduza o JavaScript desnecessário).
- [ ] O teste com dados reais de formulário ("Sr. João Silva, joao@gmail.com") realmente chegou na caixa de entrada do cliente sem cair na flag de SPAM (lixo eletrônico)?

---

> **Razão**: Executar este checklist coroa a qualidade implacável do desenvolvedor ou agência. Seu projeto só está completo quando todas as caixas acima forem marcadas positivamente. Nada vende melhor um trabalho ágil do que um link sem erros grosseiros e uma miniatura que gera orgulho visual para o cliente.
