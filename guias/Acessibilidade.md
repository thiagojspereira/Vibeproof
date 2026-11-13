# Acessibilidade

Use para implementar ou revisar acessibilidade em páginas e fluxos existentes.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Identifique padrões, tecnologias assistivas, páginas e jornadas relevantes.
2. Execute os testes manuais abaixo com teclado, zoom e leitor de tela; combine com verificações automatizadas.
3. Corrija componentes e conteúdo afetados e repita as jornadas, registrando dispositivos e limitações.

## Acessibilidade

- [ ] Fontes legíveis.
- [ ] Botões com texto claro.
- [ ] Imagens importantes com alt text.
- [ ] Toda funcionalidade essencial é operável por teclado, com ordem lógica, foco visível e não ocultado por camadas fixas; componentes customizados têm interação equivalente à nativa e não há armadilha de foco fora de modais.
- [ ] Links com nomes descritivos.
- [ ] Sem texto essencial preso dentro de imagem.
- [ ] Idioma da página e mudanças relevantes de idioma estão identificados; landmarks, títulos e ordem de leitura continuam coerentes com a apresentação visual.
- [ ] Há mecanismo para pular blocos repetidos e chegar ao conteúdo principal; elementos decorativos e conteúdo oculto não poluem a navegação assistiva.
- [ ] Aumento de espaçamento de texto pelo usuário não corta conteúdo nem ações: entrelinhas de 1,5×, após parágrafos de 2×, letras de 0,12× e palavras de 0,16× do tamanho da fonte, nos contextos aplicáveis.
- [ ] Tooltip/conteúdo exibido por hover ou foco pode ser alcançado e dispensado sem desaparecer antes da leitura; ajuda essencial não depende dele.
- [ ] Gráficos e indicadores comunicam valores/estados também por texto ou alternativa acessível; legenda e significado não dependem apenas de cor.

- [ ] Layout permanece utilizável com zoom e largura de 320 CSS px; instruções, erros longos e textos ampliados não são cortados.

- [ ] Texto, bordas essenciais e foco têm contraste adequado; erro e obrigatoriedade continuam identificáveis sem perceber cores.

- [ ] Alvos atendem ao mínimo de 24×24 CSS px ou às condições de espaçamento/exceções da WCAG 2.2; buscar áreas maiores para conforto no toque.

- [ ] Testar ao menos um leitor de tela com navegador compatível, além de teclado e aparelho mobile; análise automática sozinha não comprova acessibilidade.

Referências complementares: [W3C — foco não ocultado](https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html) e [ajustes de espaçamento](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html).

---
