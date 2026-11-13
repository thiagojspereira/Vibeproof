# Navegação, estados e interações

Use para revisar a experiência funcional de interfaces e seus estados.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Mapeie jornadas e componentes presentes, inclusive busca, tabelas, modais e mídia.
2. Percorra navegação e estados de carregamento, erro, vazio, sucesso e recuperação.
3. Teste mouse, toque e teclado, movimento reduzido e condições reais; reproduza falhas de serviços.
4. Registre o comportamento observado e reteste os fluxos corrigidos.

## Experiência de navegação e estados da interface

Aplicar aos recursos existentes; marcar `N/A` quando ausentes. Formulários e componentes abertos continuam concentrados no guia de formulários, sem repetir seus testes aqui.

### Navegação e orientação

- [ ] A localização atual fica clara no menu e na página; logo, breadcrumbs quando necessários e links de retorno ajudam a sair de páginas internas sem depender da home.
- [ ] Voltar/Avançar do navegador preservam o contexto esperado: filtros, página da lista e posição de rolagem, quando pertinente; nenhuma navegação cria um ciclo sem saída. O retorno do detalhe à lista mantém os mesmos critérios.
- [ ] URLs internas abrem diretamente e sobrevivem a recarga; links compartilhados levam ao recurso correto, inclusive depois do login quando necessário.
- [ ] Em navegação sem recarga, título da aba, foco e anúncio da nova página são atualizados; a rolagem diferencia avanço para outra página de retorno à lista.
- [ ] Links de navegação permitem abrir em nova aba e copiar endereço; botões executam ações. Abrir outra janela/aba ou baixar um arquivo não acontece de forma surpreendente.
- [ ] Âncoras posicionam o título abaixo do cabeçalho fixo; sticky e scroll não escondem conteúdo nem prendem a navegação em uma seção.
- [ ] Ajuda e suporte, quando oferecidos em várias telas, mantêm localização/ordem consistentes e destino funcional.

### Listas, busca, filtros e tabelas

- [ ] Diferenciar primeiro uso sem dados, busca sem resultados e falha ao carregar; cada estado oferece ação pertinente, como criar primeiro registro, limpar filtros ou tentar novamente.
- [ ] Busca, filtros e ordenação mostram o que está ativo e permitem limpar; modificar critérios reinicia a paginação quando necessário e respostas antigas não substituem a busca atual.
- [ ] Quando útil ao compartilhamento, busca/filtros/paginação ficam na URL sem expor dados pessoais.
- [ ] Paginação e “Carregar mais” indicam continuidade e fim; excluir o último item da página não deixa uma página vazia artificial.
- [ ] Tabelas preservam a relação entre cabeçalhos e valores; versão mobile permite consultar e agir sem esconder informação essencial. Rolagem horizontal necessária fica perceptível.
- [ ] Ordenação diferencia números, datas e texto corretamente; itens selecionados e alcance de ações em lote ficam claros, inclusive entre páginas e após filtrar.
- [ ] Atualização em tempo real não reorganiza a lista sob o clique nem desloca o foco; dados desatualizados e atualização pendente são indicados quando afetam decisões.

### Modais, avisos e ações auxiliares

- [ ] Modal tem título acessível e fechamento identificável; fundo fica inerte e Tab permanece no modal. Escape e clique externo seguem comportamento apropriado ao risco, sem descartar trabalho inadvertidamente. Ao abrir, o foco entra no modal; ao fechar, retorna ao acionador.
- [ ] Modais longos permitem alcançar título, conteúdo e ações em telas baixas; fechar restaura a rolagem da página, sem salto ou bloqueio residual.
- [ ] Em modal longo no celular, rolar do início ao fim em movimentos curtos e lentos, nos dois sentidos, inclusive com teclado aberto e após fechá-lo. Observar pequenos retornos e disputa entre a rolagem do modal e da página de fundo quando a barra do navegador aparece ou desaparece; validar também os limites e a ação no fim. Quando possível, repetir em aparelho físico com navegador atendido e registrar o que não pôde ser testado.
- [ ] Toasts não cobrem ações e duram o suficiente para leitura; avisos importantes ou que exigem ação têm alternativa persistente e não desaparecem antes de serem utilizados.
- [ ] Copiar, compartilhar, exportar e baixar oferecem retorno real de sucesso/falha; testar permissões negadas e indisponibilidade da área de transferência ou API usada.
- [ ] Downloads entregam o arquivo correto com nome e formato úteis; exportações demoradas mostram como obter o resultado sem manter uma espera indefinida.
- [ ] Falta de permissão, recurso removido e funcionalidade indisponível têm explicação e saída apropriadas; não aparecem como tela vazia ou botão sem resposta.

### Acabamento em condições reais

- [ ] Comparar telas com conteúdo realista: nomes muito longos, números grandes, zero, campos ausentes e imagens quebradas; truncamento oferece acesso ao conteúdo completo quando necessário.
- [ ] Datas relativas, moeda, unidades e pluralização não geram ambiguidade; horários de agendamento deixam claro o fuso relevante para o usuário.
- [ ] Temas claro/escuro existentes cobrem também estados vazios, gráficos, ilustrações e componentes de terceiros; preferência é preservada e a carga inicial evita troca visual indevida de tema.
- [ ] Ícones e controles sobrepostos, especialmente o botão de fechar, têm contraste com o próprio fundo nos temas claro e escuro e nos estados normal, hover, foco e desabilitado; revisar os demais usos do componente compartilhado. O seletor de tema aparece apenas nas superfícies previstas para o projeto.
- [ ] Chat, banner de cookies, botão flutuante, barra de ação e navegação fixa foram testados simultaneamente; não cobrem conteúdo/ações nem competem pelo mesmo espaço.
- [ ] Áreas seguras do aparelho, orientação paisagem e variações de altura da barra do navegador foram verificadas; conteúdo não fica sob notch ou indicador de início.
- [ ] Carregamento de fontes, imagens e widgets não desloca o alvo durante o clique; reservar espaço e conferir também a primeira visita com cache vazio.
- [ ] Falha ou bloqueio de widget, vídeo ou script de terceiros não impede navegar nem deixa espaço quebrado; mostrar alternativa útil quando o recurso for essencial.

### Movimento, mídia e interação

- [ ] Animações, parallax e transições respeitam `prefers-reduced-motion`, mantendo conteúdo e ações acessíveis quando o efeito é reduzido ou removido.
- [ ] Conteúdo em movimento automático e atualizações contínuas oferecem pausa/parada/ocultação quando exigido pela WCAG; carrossel não troca o item enquanto a pessoa interage com ele.
- [ ] Áudio não começa inesperadamente; vídeos têm controles utilizáveis e legendas, transcrição e audiodescrição conforme o conteúdo e critérios aplicáveis.
- [ ] Testar início, progresso, fim, repetição e interrupção das animações; trocar de rota ou sair da viewport encerra trabalho contínuo desnecessário.
- [ ] Arrastar, deslizar ou gestos complexos têm alternativas por clique/toque simples e teclado quando aplicáveis; nenhuma ação essencial depende apenas de hover.
- [ ] Abas e acordeões expõem estado ativo/expandido e relação com o conteúdo; funcionam pelo padrão de teclado apropriado e não desmontam uma tarefa em andamento sem necessidade.

Referências de acessibilidade: [W3C — modais](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/), [ajuda consistente](https://www.w3.org/WAI/WCAG22/Understanding/consistent-help.html), [pausar movimento](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html) e [alternativas ao arraste](https://www.w3.org/WAI/WCAG22/Understanding/dragging-movements.html). Os demais itens são critérios práticos de revisão de produto, aplicáveis conforme o projeto.

---
