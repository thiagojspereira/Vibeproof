# SEO técnico, indexação e dados estruturados

Use para revisar rastreamento, indexação, estrutura e dados estruturados de páginas públicas.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Identifique URLs que devem ser indexadas, ambientes privados e resultados atuais.
2. Rastreie respostas, canônicas, sitemap, robots e diretivas; compare HTML inicial e renderizado.
3. Corrija causas comprovadas e alinhe links e dados estruturados ao conteúdo visível.
4. Após publicação autorizada, repita inspeções e registre indexação efetiva separadamente de solicitações e elegibilidade.

Para domínio e redirecionamentos consulte [Domínio, DNS, HTTPS e publicação](Dom%C3%ADnio%2C%20DNS%2C%20HTTPS%20e%20publica%C3%A7%C3%A3o.md). Para conteúdo consulte [SEO, AEO e GEO - conteúdo e páginas](SEO%2C%20AEO%20e%20GEO%20-%20conte%C3%BAdo%20e%20p%C3%A1ginas.md).

## SEO técnico básico

- [ ] Title tag única em cada página principal.
- [ ] Meta description única em cada página principal.
- [ ] H1 principal claro e hierarquia coerente por página; mais de um H1 não implica erro automaticamente.
- [ ] Hierarquia H2/H3 organizada.
- [ ] URLs amigáveis, com slugs curtos e claros.
- [ ] Canonical configurado.
- [ ] Sitemap.xml gerado.
- [ ] `robots.txt` criado/revisado e conferido na URL pública final, após CDN/Cloudflare: regras efetivamente servidas preservam o sitemap e não bloqueiam por engano os crawlers de busca desejados.
- [ ] Página inicial e demais páginas principais/importantes liberadas para indexação e efetivamente indexáveis.
- [ ] Páginas privadas e ambientes de teste protegidos por autenticação ou restrição de acesso; `robots.txt` e `noindex` não são proteção de dados. Para páginas públicas que não devem ser indexadas, permitir o rastreamento da diretiva `noindex`, pois bloqueá-la em `robots.txt` pode impedir que o Google a veja.
- [ ] Redirecionamentos permanentes 301 ou 308 configurados para URLs migradas, quando necessário.
- [ ] Erros 404 revisados.
- [ ] Conteúdo duplicado revisado.

---

## SEO avançado, local e GEO

- [ ] Schema Organization configurado, se aplicável.
- [ ] Schema LocalBusiness configurado, se aplicável.
- [ ] FAQ útil para o leitor pode ser incluído no conteúdo; não implementar `FAQPage` com a expectativa de resultado destacado no Google, pois esse recurso deixou de ser exibido em maio de 2026.
- [ ] Schema Article/BlogPosting avaliado para artigos, se fizer sentido ao conteúdo; identificar no `author` os autores reais exibidos na página, como `Person` ou `Organization`, conforme o caso, e incluir nome e URL de perfil que os identifique.
- [ ] Schema `Person` avaliado para pessoas relevantes e `ProfilePage` para páginas de perfil apropriadas. Relacionar o autor do artigo ao mesmo perfil de pessoa, quando aplicável.
- [ ] Em dados de pessoas, usar apenas informações pertinentes, verdadeiras e coerentes com o conteúdo visível: função, imagem, vínculo com a empresa, experiência, formação ou filiações, quando aplicáveis. Vincular perfis externos que realmente pertençam à pessoa; não exigir Wikipedia, Wikidata ou ID no Knowledge Graph.
- [ ] Validar a marcação e verificar sua correspondência com a página. Dados estruturados ajudam na compreensão, mas não garantem resultado destacado nem melhor posição.
- [ ] Breadcrumbs configurados, se aplicável.
- [ ] Nome, endereço e telefone consistentes, se aplicável.
- [ ] Cidade/região trabalhada no conteúdo quando relevante.
- [ ] Google Business Profile considerado, se aplicável.
- [ ] Marca explicada de forma clara para mecanismos de busca e IA.
- [ ] Página “Sobre” ajuda a definir a entidade/marca.
- [ ] Serviços/produtos descritos objetivamente.
- [ ] FAQ responde perguntas reais do público.
- [ ] Conteúdo tem dados factuais fáceis de extrair.
- [ ] Informações de contato claras e rastreáveis.

---

**Referências:** [Google: dados estruturados de artigos e autoria](https://developers.google.com/search/docs/appearance/structured-data/article), [Google: páginas de perfil](https://developers.google.com/search/docs/appearance/structured-data/profile-page) e [diretrizes gerais de dados estruturados](https://developers.google.com/search/docs/appearance/structured-data/sd-policies).

## Bing Webmaster Tools e descoberta por IA

- [ ] Propriedade do domínio adicionada e verificada no Bing Webmaster Tools (pode ser importada do Google Search Console).
- [ ] Sitemap canônico enviado e processamento conferido no Bing Webmaster Tools.
- [ ] Inspeção/indexação das páginas principais revisada; erros de rastreamento corrigidos.
- [ ] IndexNow avaliado para sites com criação, atualização ou remoção frequente de URLs; se adotado, confirmar o envio de URLs reais.
- [ ] Registrado que Bing Webmaster Tools ajuda a descobrir e diagnosticar páginas no Bing, mas não é requisito nem garantia de aparição no ChatGPT Search ou em respostas de IA.
- [ ] Para páginas públicas que devem aparecer em respostas de IA, verificar as regras efetivas do `robots.txt` para `OAI-SearchBot` (ChatGPT Search), `ChatGPT-User` (acesso por solicitação do usuário), `Claude-SearchBot` e `Claude-User` (Anthropic), `PerplexityBot`/`Perplexity-User` (quando aplicável), além de `Googlebot` e `bingbot`.
- [ ] Separar a decisão sobre uso para treinamento: `GPTBot` (OpenAI) e `ClaudeBot` (Anthropic) têm função diferente dos robôs de busca. `Google-Extended` é um token de controle de usos do Gemini, inclusive treinamento e grounding; não é um crawler HTTP separado e bloqueá-lo não retira o site da Busca Google.
- [ ] Na Cloudflare, conferir o `robots.txt` realmente entregue, AI Crawl Control, políticas de bots de IA, WAF, desafios, rate limits e regras personalizadas. Verificar se algum deles bloqueia ou desafia os crawlers de busca/acesso escolhidos nas páginas públicas, inclusive ao acessar o sitemap. Corrigir conforme a política do projeto, preservando áreas privadas e staging.
- [ ] Confirmar em logs/eventos da Cloudflare e na resposta HTTP que os acessos desejados não recebem bloqueio ou desafio; testar em produção sem concluir que um `User-Agent` simulado prova a identidade ou o acesso de um crawler real.

Referências: [OpenAI — crawlers](https://developers.openai.com/api/docs/bots), [Anthropic — robôs do Claude](https://support.claude.com/en/articles/8896518-does-anthropic-crawl-data-from-the-web-and-how-can-site-owners-block-the-crawler), [Google — crawlers e Google-Extended](https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers), [Bing Webmaster Tools](https://www2.bing.com/webmasters/help/refreshed-webmaster-tools-7c7d2533) e [Cloudflare — `robots.txt` gerenciado](https://developers.cloudflare.com/bots/additional-configurations/managed-robots-txt/).

---

## Base técnica para descoberta e leitura

O checklist de Suraj Sharma e os posts de Manoj e Ross apontam para os mesmos grupos de problemas. Em uma aplicação concreta, a inspeção deve identificar a causa antes de aplicar mudanças genéricas.

| Frente | O que conferir |
|---|---|
| Acesso e indexação | URLs públicas acessíveis, bloqueios de robôs ou infraestrutura, diretivas de indexação e inspeção das páginas importantes. |
| Descoberta | Sitemap atualizado, navegação e links internos que levem às páginas relevantes; páginas órfãs. |
| URLs e duplicação | Canonicals coerentes, redirecionamentos necessários e ausência de cadeias evitáveis. |
| Conteúdo renderizado | Resposta principal e informações importantes disponíveis em texto acessível ao rastreador. |
| Estrutura da página | Título, cabeçalhos, descrição e dados estruturados compatíveis com o conteúdo visível. |
| Experiência | Imagens adequadas, estabilidade visual, velocidade e uso em dispositivos móveis. |
| Manutenção | Links quebrados, informações desatualizadas, conteúdo superficial e páginas sem função clara. |

### Checklist complementar de correções

- [ ] **Rastreamento e indexação:** conferir se o `robots.txt` permite ao Googlebot acessar as páginas e os recursos públicos que devem ser rastreados. Verificar `noindex` tanto na meta tag quanto no cabeçalho HTTP `X-Robots-Tag` e remover diretivas indevidas das páginas que devem ser indexadas; preservar as exclusões intencionais.
- [ ] **Sitemap:** criar ou atualizar o sitemap XML com URLs canônicas, acessíveis e destinadas à indexação. Enviá-lo pelo relatório de sitemaps do Search Console e conferir erros de processamento. O envio facilita a descoberta, mas não garante indexação.
- [ ] **Renderização e links:** confirmar que conteúdo e navegação importantes ficam acessíveis aos rastreadores. Avaliar renderização no servidor ou pré-renderização quando houver problema concreto; links inseridos por JavaScript podem ser rastreáveis quando usam `<a href>` com URLs válidas.
- [ ] **Títulos e estrutura:** revisar títulos e meta descrições das páginas importantes para que descrevam seu conteúdo e sejam distintos quando apropriado. Usar cabeçalhos claros e uma hierarquia coerente; um H1 principal é uma convenção útil, não uma exigência universal.
- [ ] **Dados estruturados:** avaliar marcações compatíveis com o conteúdo visível e os recursos atualmente suportados, como `Article` quando pertinente. Validar sintaxe e elegibilidade; não presumir exibição. `FAQPage` não gera mais resultado destacado de FAQ no Google.
- [ ] **Navegação:** acrescentar breadcrumbs quando ajudarem o visitante a entender e percorrer a hierarquia; avaliar `BreadcrumbList` coerente com a navegação visível. Ligar páginas relevantes que estejam órfãs a partir de outras páginas úteis; decidir separadamente o destino de páginas sem função clara.
- [ ] **Imagens:** escrever texto alternativo que descreva a função ou o conteúdo das imagens informativas; em imagens puramente decorativas, usar `alt=""` quando apropriado. Redimensionar e comprimir imagens e avaliar WebP ou outro formato adequado, preservando qualidade e compatibilidade.
- [ ] **Experiência:** medir o CLS e buscar **0,1 ou menos no percentil 75** das visitas reais, separando celular e desktop quando houver dados. Avaliar a velocidade com métricas e condições explícitas; menos de dois segundos pode ser uma meta interna, não um requisito universal para todas as páginas.
- [ ] **Conteúdo e autoria:** revisar textos genéricos, repetitivos ou sem informação útil, inclusive os gerados com IA, corrigindo fatos e acrescentando conhecimento próprio. Identificar autores ou responsáveis reais e apresentar uma bio verificável quando ela ajudar o leitor a avaliar o conteúdo.
- [ ] **Links e autoridade:** corrigir links quebrados relevantes e cadeias de redirecionamento evitáveis. Buscar referências e backlinks editoriais em fontes confiáveis e pertinentes ao público, sem presumir ganho garantido de posicionamento.

**Referências:** [sitemaps e envio ao Google](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap), [diretivas noindex](https://developers.google.com/search/docs/crawling-indexing/block-indexing), [links rastreáveis](https://developers.google.com/search/docs/crawling-indexing/links-crawlable), [breadcrumbs](https://developers.google.com/search/docs/appearance/structured-data/breadcrumb) e [medição de CLS](https://web.dev/articles/cls).

### Verificação do site publicado após as correções

Depois da publicação autorizada, rastrear as URLs reais do site e comparar as respostas com o resultado esperado. Conferir códigos HTTP, destinos e cadeias de redirecionamento, links quebrados, canônicas, sitemap, `robots.txt` e diretivas de indexação no HTML e nos cabeçalhos. Comparar o HTML inicial com a página renderizada para identificar conteúdo ou links dependentes de JavaScript; confirmar que os links relevantes têm URLs rastreáveis. Usar a inspeção de URL do Search Console em páginas representativas e investigar divergências. Registrar limitações do rastreamento e corrigir problemas encontrados antes de considerar a verificação concluída.

Referências adicionais: [Google — mudanças na Busca](https://developers.google.com/search/updates), [Google — noindex](https://developers.google.com/search/docs/crawling-indexing/block-indexing) e [Google — recursos de IA](https://developers.google.com/search/docs/appearance/ai-features).
