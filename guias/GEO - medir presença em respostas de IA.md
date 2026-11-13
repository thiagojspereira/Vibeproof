# GEO - medir presença em respostas de IA

Use para investigar e acompanhar menções, recomendações e citações em assistentes de IA.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Defina perguntas e condições comparáveis, separando descoberta e marca.
2. Registre cada resposta e suas fontes por sistema e rodada.
3. Calcule menções e citações separadamente e examine padrões com cautela.
4. Priorize hipóteses úteis e repita o teste para observar tendências; compare com resultados de negócio sem confundir métricas.

## Como medir sem misturar os resultados

Os posts recomendam Search Console, GA4, Bing Webmaster Tools e observação das respostas de IA. A síntese prática é manter três perguntas separadas:

- **Busca:** quais consultas e páginas ganham impressões, cliques e tráfego relevante?
- **Negócio:** quais páginas trazem cadastros, contatos, ativações ou vendas?
- **IA:** em quais perguntas a marca ou página aparece, em qual sistema e com qual fonte citada?

Para acompanhar IA, registrar pergunta, sistema, data, resposta e fonte. Uma consulta isolada serve como observação, não como medida estável de presença. Também não se deve tratar um relatório de tráfego de busca como prova automática de todas as citações em ChatGPT, Gemini ou Perplexity.

O Google inclui o desempenho de seus recursos de IA no tráfego geral do tipo de pesquisa Web do Search Console. Isso não equivale a um painel abrangente de citações em todos os assistentes. [Google Search Central](https://developers.google.com/search/docs/appearance/ai-features).

## Playbook: testar recomendações de IA em chats temporários

Adaptado do artigo de [Mudassar Khan — How to track your brand in ChatGPT, Gemini and Perplexity without paying for a tool](https://x.com/mudassarkahn/status/2113180141627265305), publicado em 22/10/2026 e consultado em 25/10/2026. O objetivo é descobrir como a marca aparece nas respostas e usar as lacunas observadas para orientar conteúdo, comparações e presença em fontes externas.

### 1. Definir e manter as perguntas

Criar um conjunto inicial de **20 perguntas reais de compradores**, distribuídas entre categoria, problema, comparação e alternativas. Buscar ideias nas consultas do Search Console, nas perguntas relacionadas dos buscadores e nas dúvidas de vendas e suporte.

Exemplos para um produto de fidelidade digital:

- Categoria: “Qual o melhor cartão fidelidade digital para uma cafeteria pequena no Brasil?”
- Problema: “Como fazer os clientes voltarem à minha barbearia sem dar desconto em toda visita?”
- Comparação: “Cartão fidelidade de papel ou digital: qual funciona melhor para salão de beleza?”
- Alternativas: “Quais alternativas ao [concorrente] atendem pequenos negócios no Brasil?”

Manter as perguntas idênticas entre rodadas. Nos testes de descoberta, evitar inserir o nome da própria marca, pois isso induz sua presença na resposta. Perguntas específicas sobre a marca podem formar um conjunto separado.

### 2. Executar em sessões limpas

- Começar com uma amostra proporcional ao objetivo e ao esforço disponível; se for útil medir tendência com mais detalhe, o método do autor propõe 20 perguntas, 5 vezes por sistema, totalizando 100 respostas. Registrar o tamanho da amostra e não extrapolar resultados de poucas respostas.
- No ChatGPT, usar **chat temporário novo para cada execução**, sem reaproveitar a conversa anterior.
- Manter idioma, localização e condições de teste comparáveis. Registrar modelo, uso de busca e configurações relevantes; não presumir que chat temporário elimina toda personalização.
- Executar a rodada em um intervalo curto e repetir no mesmo dia da semana.
- Separar os resultados de ChatGPT, Gemini, Perplexity e outros sistemas, sem misturá-los em uma única pontuação.

### 3. Registrar uma linha por resposta

| Campo | O que registrar |
|---|---|
| Data e rodada | Quando o teste foi realizado. |
| Sistema e modelo | Assistente, modelo exibido e uso de busca. |
| Pergunta e execução | Identificador, texto exato e repetição de 1 a 5. |
| Resposta completa | Texto ou referência que permita revisar o resultado. |
| Marcas mencionadas | Própria marca e concorrentes apresentados. |
| Marca mencionada? | 1 quando aparece no texto; 0 quando não aparece. |
| Marca recomendada? | Registrar separadamente se houve recomendação favorável, simples menção ou ressalva. |
| Site citado? | 1 quando uma URL própria aparece como fonte; 0 quando não aparece. |
| Fontes citadas | URLs e domínios usados na resposta. |
| Observações | Erros factuais, informações antigas e critérios de escolha apresentados. |

### 4. Calcular presença e citações

**Taxa de menção = respostas que mencionam a marca ÷ total de respostas**, para o mesmo sistema, período e conjunto de perguntas.

**Taxa de citação = respostas que citam uma URL própria ÷ total de respostas**, nas mesmas condições.

Exemplo: aparecer em 31 de 100 respostas corresponde a 31% de menções. Menção, recomendação e citação são resultados distintos: a IA pode citar um artigo do site e recomendar um concorrente, ou recomendar a marca com uma fonte de terceiros.

Acompanhar também os principais concorrentes. Priorizar a frequência de presença ao longo de várias rodadas; a posição em uma lista isolada não deve ser tratada como ranking estável.

### 5. Transformar as respostas em melhorias

| Padrão observado | Próxima análise ou ação |
|---|---|
| A marca não aparece em perguntas comerciais relevantes | Verificar se o site explica claramente o caso de uso, o público e os critérios que aparecem nas respostas. Avaliar uma página nova ou melhoria da existente. |
| Comparações e alternativas favorecem concorrentes | Identificar quais comparações úteis faltam e produzir conteúdo com critérios verificáveis. |
| A marca aparece, mas o site não é citado | Examinar as fontes escolhidas e o que elas oferecem de mais claro, específico ou confiável. |
| Alguns domínios são citados repetidamente | Avaliar publicações, diretórios, comunidades e listas pertinentes para possível presença editorial da marca. |
| A IA apresenta informação incorreta ou antiga | Conferir o site e as fontes externas, corrigir informações sob controle da empresa e repetir o teste depois. |

Priorizar mudanças pela relevância comercial e pela evidência disponível. O teste aponta hipóteses; uma ausência isolada não comprova defeito no site, e uma alteração não garante recomendação futura.

### 6. Repetir e avaliar a tendência

Repetir em intervalos viáveis, mantendo perguntas e condições comparáveis e registrando alterações no site e mudanças de modelo. O autor sugere acompanhamento semanal por quatro semanas; adaptar ao projeto e evitar conclusões fortes com poucas observações.

O autor apresenta faixas aproximadas para interpretar variações com 100 respostas. Não adotá-las como limiares estatísticos universais: execuções podem ser correlacionadas, e mudanças de sistema, busca ou configuração afetam a comparação. Pequenas oscilações merecem novas observações antes de motivar decisões.

Cruzar a presença nas respostas com tráfego de referência, cadastros, ativações e vendas. Visibilidade em IA, tráfego e resultado comercial devem permanecer separados na análise.


