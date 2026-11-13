# Mídia paga - Meta Ads, Google Ads e UTMs

Use para implementar ou revisar a medição de anúncios e atribuição; campanhas e orçamento exigem escopo próprio.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Identifique contas, domínio, eventos de negócio e integrações existentes; escolha quais conversões são principais e secundárias.
2. Defina UTMs e persistência da origem; não inclua dados pessoais em URLs.
3. Configure Pixel e tag Google Ads pelo método escolhido e vincule contas relevantes. Avalie CAPI e deduplicação com event_id quando usar navegador e servidor.
4. Teste evento somente após sucesso real, erros, repetição, consentimento e duplicidade; confira em ferramentas de diagnóstico e destino.
5. Publique a configuração autorizada e acompanhe o recebimento e a atribuição com tráfego real; diferenças entre plataformas não provam erro por si só.

Veja também: [Analytics - GA4, GTM, Clarity e Search Console](Analytics%20-%20GA4%2C%20GTM%2C%20Clarity%20e%20Search%20Console.md) e [LGPD, privacidade e cookies](LGPD%2C%20privacidade%20e%20cookies.md).

## Implementação orientada por conversão

- [ ] Identificar a ação de negócio confirmada (por exemplo, lead salvo ou compra aprovada), onde ocorre e como o sistema comunica sucesso ao navegador ou servidor. Não tratar clique, abertura ou requisição enviada como conversão concluída.
- [ ] Inventariar Google tag, GTM, Pixel, integrações nativas e eventos já instalados; definir uma única origem de cada conversão e evitar contagem duplicada entre importação GA4 e tag direta.
- [ ] No Google Ads, selecionar conta, ação e objetivo; configurar categoria, valor, contagem, janela e ação primária ou secundária conforme o negócio. Se usar tag direta, conferir ID e rótulo; se importar GA4, marcar o evento como principal no GA4, conferir vínculo e conversão criada no Ads, incluindo latência.
- [ ] Na Meta, confirmar empresa, conjunto de dados/pixel e domínio; mapear o evento padrão apropriado e testar no Gerenciador de Eventos. Se houver CAPI e navegador para o mesmo fato, combinar nome do evento e identificador para deduplicação conforme as regras vigentes.
- [ ] Definir consentimento e destino dos dados antes de ativar tags; conferir também os disparos do servidor e os parâmetros opcionais. Correspondência avançada ou conversões otimizadas exigem base, configuração e tratamento apropriados; não mandar dados pessoais em eventos comuns ou URLs.
- [ ] Construir URLs com nomenclatura consistente; quando aplicável, ativar marcação automática do Google Ads e testar preservação de identificadores de clique e UTMs em redirecionamentos. Se houver domínios diferentes, avaliar linker entre domínios; no GTM, configurar Conversion Linker quando necessário. Não presumir que UTM garante atribuição integral.
- [ ] Simular sucesso, falha, duplo clique e recusa/aceite. Conferir ferramentas de diagnóstico e plataformas; documentar atraso de processamento, limitações e conversões de teste, evitando contaminar dados reais.

## Meta Pixel

- [ ] Meta Pixel criado ou confirmado.
- [ ] Pixel instalado via GTM ou método definido.
- [ ] Evento PageView funcionando.
- [ ] Evento Lead configurado, se aplicável.
- [ ] Evento Contact configurado, se aplicável.
- [ ] Evento CompleteRegistration configurado, se aplicável.
- [ ] Eventos testados no Meta Events Manager.
- [ ] Domínio verificado no Business Manager, se necessário.
- [ ] Configurações de mensuração e requisitos atuais da Meta revisados para a conta e o domínio, se aplicável.
- [ ] Conversions API avaliada, se o projeto justificar.

---

## Google Ads tag e conversões

- [ ] Conta Google Ads correta confirmada, se aplicável.
- [ ] Google tag configurada, se necessário.
- [ ] Conversão principal criada.
- [ ] Conversões secundárias criadas, se necessário.
- [ ] Tag de conversão instalada via GTM ou método definido.
- [ ] Conversão testada.
- [ ] Remarketing configurado, se aplicável.
- [ ] Vinculação GA4 ↔ Google Ads revisada, se aplicável.
- [ ] Importação de conversões do GA4 avaliada.
- [ ] Conversões não duplicadas entre GA4 e Google Ads.

---

## UTMs e atribuição

- [ ] Padrão de UTMs definido.
- [ ] `utm_source` padronizado.
- [ ] `utm_medium` padronizado.
- [ ] `utm_campaign` padronizado.
- [ ] `utm_content` padronizado, se necessário.
- [ ] `utm_term` padronizado, se mídia paga.
- [ ] Links de campanha principais criados.
- [ ] UTMs testadas no GA4.
- [ ] Planilha/documento de UTMs criado, se necessário.

Padrão sugerido:

| Campo | Exemplo |
|---|---|
| utm_source | google, meta, instagram, newsletter |
| utm_medium | cpc, social, email, organic |
| utm_campaign | nome_da_campanha |
| utm_content | variacao_do_criativo |
| utm_term | palavra_chave |

---

Referências: [Google Ads — acompanhamento de conversões](https://support.google.com/google-ads/answer/7521212), [Google — eventos principais e conversões](https://support.google.com/analytics/answer/13965727) e [Meta — Conversions API](https://www.facebook.com/business/help/2041148702652965).
