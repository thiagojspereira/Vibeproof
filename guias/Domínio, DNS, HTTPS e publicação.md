# Domínio, DNS, HTTPS e publicação

Use ao lançar ou migrar domínios, hospedagem e endpoints.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Inventarie DNS, domínio canônico, subdomínios, certificados e dependências antes de alterar.
2. Configure e teste redirecionamentos, HTTPS e callbacks aplicáveis, preservando caminhos e parâmetros necessários.
3. Planeje retorno e publique no ambiente autorizado; repita os testes no endereço público.

## Domínio, DNS, SSL e publicação

- [ ] Domínio final confirmado.
- [ ] DNS revisado e apontamento correto.
- [ ] Domínio canônico (`www` ou sem `www`) definido e redirecionamento entre versões funcionando.
- [ ] HTTPS ativo, certificado SSL válido e renovação automática confirmada.
- [ ] Quando o projeto usar Supabase, o domínio técnico público foi revisado; se o `project ref` aleatório aparecer em OAuth, e-mails ou outras superfícies visíveis, configurar um **vanity subdomain** legível (`marca.supabase.co`) antes do lançamento, quando o plano e a disponibilidade permitirem.
- [ ] Antes de contratar um custom domain pago no Supabase, confirmar se o vanity subdomain incluído no plano atende ao projeto.
- [ ] Após ativar ou trocar o domínio do Supabase, adicionar o novo callback (`https://<vanity-subdomain>/auth/v1/callback`) em cada provedor OAuth e preservar o callback anterior até concluir a validação.
- [ ] Login social testado pelo novo domínio até o seletor ou consentimento, sem `redirect_uri_mismatch`, com o nome e o domínio exibidos ao usuário conferidos.
- [ ] Ambiente de produção definido.
- [ ] Cache/CDN configurado, se aplicável.
- [ ] Backup antes da publicação feito.
- [ ] Plano simples de rollback definido.
- [ ] Produção publicada sem erro.
- [ ] URL final abre corretamente.

---

### Checklist de domínio, HTTPS e URLs canônicas

Aplicar ao lançar um site e revisar após mudanças de domínio, hospedagem, proxy ou redirecionamento:

- [ ] **Definir o endereço principal:** escolher HTTPS com ou sem `www` para o site público. Registrar separadamente subdomínios que tenham outra função, como aplicativo, API ou demonstração; eles não precisam apontar para a página inicial do site.
- [ ] **Testar as quatro entradas:** acessar `http://dominio`, `http://www.dominio`, `https://dominio` e `https://www.dominio`. As versões alternativas que representem o mesmo site devem chegar ao endereço principal em HTTPS. Conferir também HTTP e HTTPS dos subdomínios públicos relevantes, incluindo o acesso ao aplicativo.
- [ ] **Conferir a resposta HTTP:** usar as ferramentas de rede do navegador ou `curl -I` para confirmar um redirecionamento permanente **301 ou 308**; a barra de endereço sozinha não mostra o código. Quando houver requisições que não sejam GET, avaliar **308**, que preserva o método e o corpo. Evitar cadeias desnecessárias e loops.
- [ ] **Testar páginas internas e parâmetros:** conferir pelo menos uma página representativa, como `/contato` ou um artigo, e uma URL com parâmetros. O redirecionamento deve preservar o caminho e os parâmetros necessários, levando à página equivalente; não enviar todas as páginas para a inicial. Validar casos especiais de integrações e endpoints antes de alterar suas regras.
- [ ] **Conferir a canônica de cada página indexável:** inspecionar o HTML entregue e, quando necessário, o conteúdo renderizado. A tag `rel="canonical"` deve indicar a URL HTTPS final e equivalente daquela página, sem passar por outro redirecionamento. Páginas diferentes, como termos e privacidade, não devem herdar a canônica da página inicial por engano. A canônica é uma indicação; o Google pode escolher outra URL.
- [ ] **Alinhar os sinais:** usar as URLs finais nos links internos, no sitemap e, quando possível, em perfis e citações controlados pela empresa. Validar que as URLs do sitemap são acessíveis e adequadas à indexação.
- [ ] **Verificar depois da publicação:** repetir os testes HTTP e HTTPS, conferir a resposta final e as tags nas páginas publicadas e usar a inspeção de URL do Search Console para comparar a canônica declarada com a escolhida pelo Google. A escolha do Google pode levar tempo para ser atualizada.

Abrir uma página em HTTP sem redirecionamento pode expor dados em trânsito, sobretudo em login e formulários; priorizar a correção na camada que recebe o acesso público. Sites duplicados não significam automaticamente uma divisão de 50% do orçamento de rastreamento nem uma penalidade. Uma canônica que redireciona deve ser corrigida para deixar os sinais claros, sem presumir uma perda geral de confiança do Google.

**Referências:** [redirecionamentos e Google Search](https://developers.google.com/search/docs/crawling-indexing/301-redirects), [como indicar URLs canônicas](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls) e [orçamento de rastreamento](https://developers.google.com/crawling/docs/crawl-budget).

O Google informa que seus recursos de IA seguem os fundamentos de SEO: não exigem arquivos especiais de IA nem um schema específico. A página precisa estar indexada e elegível para aparecer com um snippet; cumprir requisitos não garante exibição. Isso reforça a prioridade da base técnica e editorial sobre “truques de GEO”. [Google Search Central](https://developers.google.com/search/docs/appearance/ai-features).

**Fontes dos posts:** [Suraj Sharma](https://x.com/suraj_sharma14/status/2106240327569035424), [Manoj Ahirwar](https://x.com/manoj_ahi/status/2113665767065665830) e [Ross Simmonds](https://x.com/TheCoolestCool/status/2110823024362766390).
