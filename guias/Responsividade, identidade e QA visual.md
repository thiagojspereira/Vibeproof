# Responsividade, identidade e QA visual

Use para revisar identidade, acabamento e adaptação visual em telas e navegadores relevantes.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Defina páginas, temas, dispositivos, estados e referências atuais do projeto.
2. Percorra as páginas em desktop e celular, incluindo conteúdo realista e componentes abertos; observe cortes, sobreposições e interação.
3. Confira identidade, ícones e compartilhamento; valide movimento em execução e acessibilidade nas condições aplicáveis.
4. Registre larguras, navegador, evidências e limitações; corrija e repita a inspeção nas superfícies afetadas.

## Identidade visual e acabamento

- [ ] Logo correto aplicado e versões testadas em fundos claros/escuros, se aplicável.
- [ ] Cores oficiais e fontes corretas aplicadas.
- [ ] A seleção de texto possui cores explícitas em `::selection` (e `::-moz-selection`, quando necessário), com contraste visível entre texto, seleção e fundo da página.
- [ ] A seleção de texto foi testada nos principais fundos claros, escuros e coloridos do site, inclusive em temas alternativos, sem ficar invisível ou ambígua.
- [ ] Favicon testado no navegador em modo claro e escuro; usar o isotipo oficial com contraste adequado em cada modo, sem depender de um único arquivo claro ou escuro.
- [ ] Favicon adaptativo configurado com SVG e `prefers-color-scheme`, ou arquivos próprios com `media`, preservando a marca; incluir fallback PNG quando necessário.
- [ ] Favicon conferido no tamanho real da aba (16–32 px), sem margens excessivas, cortes ou perda de legibilidade; testar troca de tema e recarga para conferir cache e atualização.
- [ ] Apple touch icon instalado.
- [ ] Ícones Android/PWA instalados, se aplicável.
- [ ] Imagem de compartilhamento social criada como representação fiel da primeira dobra aprovada, sem mockup genérico ou reconstrução visual pobre do site.
- [ ] Open Graph image configurada em formato social adequado, preferencialmente `1200×630`, com URL absoluta e arquivo acessível publicamente.
- [ ] Se a atualização frequente justificar, avaliar geração automática da Open Graph image; uma imagem estática revisada também pode atender ao projeto.
- [ ] A imagem gerada automaticamente foi comparada visualmente com a primeira dobra real em desktop e não apresenta fontes ausentes, imagens incompletas, animações em estado intermediário, banners indevidos ou cortes ruins.
- [ ] Atualizações relevantes da primeira dobra regeneram a imagem e alteram seu nome, hash ou versão na URL para reduzir problemas de cache das plataformas sociais.
- [ ] Prévia de compartilhamento no WhatsApp testada.
- [ ] Prévia de compartilhamento no Facebook/LinkedIn testada, se aplicável.
- [ ] Título do site correto no navegador.
- [ ] Nome da marca consistente.
- [ ] Ícones revisados.
- [ ] Imagens com nomes organizados.

## Padrão recomendado: Open Graph image automática e fiel ao site

Automatizar a OG image como uma captura real do site, em vez de pedir ao framework ou a uma IA que reconstrua a primeira dobra:

1. Manter a primeira dobra determinística para captura: sem cookie banner, chat, cursor, dados pessoais ou conteúdo aleatório; pausar vídeos e animações no estado visual aprovado.
2. Após o deploy de staging ou produção, usar Playwright/Chromium para abrir a URL final em viewport controlado, aguardar fontes e imagens e capturar a área definida.
3. Quando a home não se adaptar bem à proporção `1.91:1`, criar uma rota interna de captura, como `/og-preview`, que reutilize os mesmos componentes, assets, fontes, cores e conteúdo do hero. A rota existe para reenquadrar a primeira dobra em `1200×630`, não para criar uma arte diferente.
4. Salvar o resultado como JPG ou PNG otimizado no destino público do projeto e atualizar `og:image`, `twitter:image`, largura, altura e texto alternativo.
5. Executar a captura novamente quando componentes, assets, fontes ou conteúdo da primeira dobra mudarem. Usar hash no nome do arquivo ou versão na URL para invalidar caches sociais.
6. Se a geração fizer parte do deploy, definir tratamento para falha e preservar uma OG válida; bloquear o deploy somente quando a imagem for requisito crítico do projeto.
7. Validar a imagem final e a prévia real de compartilhamento; a automação elimina o trabalho manual, mas não elimina o QA visual.

Critério de aceite: ao comparar lado a lado, a OG image deve ser reconhecida imediatamente como a primeira dobra do site, apenas reenquadrada para o formato social.

---

## Responsividade e QA visual

- [ ] Home e páginas principais testadas visualmente em desktop e mobile.
- [ ] Tablet testado, se possível.
- [ ] Botões clicáveis no mobile.
- [ ] Textos sem corte.
- [ ] Imagens sem distorção.
- [ ] Espaçamentos revisados.
- [ ] Componentes interativos revisados também abertos: dropdowns, seletores, calendários, menus e popovers mantêm o padrão visual e funcionam sem cortes ou sobreposições indevidas (consulte o guia de formulários).
- [ ] Rodapé responsivo.
- [ ] Sobreposições e modais aprovados conforme o guia de navegação e estados, se houver.
- [ ] Testado no Chrome.
- [ ] Testado no Safari/iPhone, se possível.
- [ ] Testado no Edge/Firefox, se relevante.

---
