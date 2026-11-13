# Finalização, produção e acompanhamento

Use para coordenar a entrega geral de um site, sem exigir ferramentas ou recursos que não se apliquem.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Defina ambiente, responsáveis, escopo e critérios para o projeto.
2. Execute os guias temáticos necessários e registre itens não aplicáveis.
3. Prepare publicação e retorno; após publicação autorizada valide jornadas e integrações reais.
4. Acompanhe 24 horas a 7 dias quando pertinente e registre limitações e pendências.

Os critérios abaixo são uma lista de verificação: ferramentas como GTM, GA4, GSC, Bing e pixels só são obrigatórias se forem necessárias ou aprovadas para o projeto.

## Informações do projeto

- [ ] Nome do projeto/site:
- [ ] URL de testes/staging:
- [ ] URL final de produção:
- [ ] Responsável técnico:
- [ ] Responsável pela aprovação:
- [ ] Data prevista de publicação:
- [ ] Tipo de projeto:
  - [ ] Site institucional
  - [ ] Landing page
  - [ ] Blog/conteúdo
  - [ ] Ecommerce
  - [ ] SaaS/app
  - [ ] Site local
  - [ ] Projeto com mídia paga
  - [ ] Migração de site antigo
  - [ ] Outro:
- [ ] O que será considerado “finalizado” está claro.
- [ ] Pendências conhecidas estão listadas.

---

## Revisão geral pós-deploy de testes

- [ ] Site e todas as páginas principais abrem corretamente no ambiente de testes.
- [ ] Não há telas quebradas, erros visíveis, placeholders, lorem ipsum ou imagens temporárias esquecidas.
- [ ] Todos os botões, links, âncoras, modais e CTAs foram acionados individualmente.
- [ ] CTAs repetidos em header, menu mobile, hero, conteúdo e rodapé levam ao destino correto.
- [ ] Estados de carregamento, sucesso, erro e tentativa repetida foram testados.
- [ ] Links internos/externos e botões têm destino correto e não estão quebrados.
- [ ] Menu principal, menu mobile e rodapé revisados e funcionando.
- [ ] Páginas legais acessíveis, se aplicável.
- [ ] Página 404 revisada.
- [ ] Console do navegador revisado para erros críticos.
- [ ] Fluxos principais testados do começo ao fim, também com falha simulada da API ou integração.

---

## Documentação final

- [ ] URL final registrada.
- [ ] Data de publicação registrada.
- [ ] Stack usada registrada.
- [ ] Domínio/hosting registrados.
- [ ] Ferramentas conectadas registradas.
- [ ] IDs seguros registrados, sem segredos.
- [ ] Acessos documentados em local seguro.
- [ ] Responsável pela manutenção definido.
- [ ] Frequência de backup definida.
- [ ] Pendências documentadas.
- [ ] Melhorias futuras listadas.
- [ ] Arquivos/assets organizados.
- [ ] Checklist final marcado como concluído.

---

## Validação final de produção

- [ ] Site publicado.
- [ ] HTTPS funcionando.
- [ ] Domínio principal abrindo.
- [ ] `www`/sem `www` redirecionando corretamente.
- [ ] Domínio técnico/vanity subdomain do Supabase e callbacks OAuth validados em produção, se aplicável.
- [ ] Quando houver login social ou passkey, executar o fluxo real autorizado até acessar a área protegida e voltar a entrar; registrar separadamente o que foi validado com provedor/dispositivo reais, simuladores e inspeção de código. Se não for possível usar conta técnica segura em produção, registrar a pendência sem tratar testes simulados como prova real.
- [ ] Página inicial carregando sem erro.
- [ ] Páginas principais abrindo.
- [ ] Formulários testados em produção.
- [ ] Um lead técnico por formulário foi confirmado no armazenamento e removido ou identificado claramente depois do teste.
- [ ] Notificações de cada formulário foram confirmadas no destinatário real.
- [ ] Cenários de erro, retry e duplicidade foram validados sem criar conversões falsas.
- [ ] WhatsApp testado em produção.
- [ ] GA4 recebendo tráfego em tempo real.
- [ ] GTM publicado.
- [ ] Meta Pixel recebendo evento.
- [ ] Google Ads tag testada, se aplicável.
- [ ] Clarity recebendo sessão.
- [ ] Campos de formulário estão mascarados nas gravações e nenhum dado pessoal aparece em eventos ou URLs.
- [ ] GSC inspecionado.
- [ ] Sitemap enviado.
- [ ] Cache limpo.
- [ ] Screenshot/registro da publicação salvo, se necessário.

---

## Pós-publicação: 24h a 7 dias

- [ ] GA4 conferido após 24h.
- [ ] Meta Pixel conferido após 24h.
- [ ] Google Ads conversões conferidas, se houver tráfego.
- [ ] Clarity conferido.
- [ ] Search Console conferido.
- [ ] Erros 404 conferidos.
- [ ] Velocidade reavaliada.
- [ ] Leads reais conferidos.
- [ ] Pendências pós-lançamento registradas.
- [ ] Melhorias futuras listadas.
- [ ] Relatório simples de entrega criado, se necessário.

---

## Critérios mínimos para considerar finalizado

Um projeto só deve ser considerado finalizado quando, no mínimo:

- [ ] Domínio final e HTTPS funcionando.
- [ ] Páginas principais revisadas e sem quebras visuais.
- [ ] Mobile aprovado.
- [ ] Formulários/WhatsApp funcionando.
- [ ] Guia de formulários verificado: erros visíveis e corrigíveis, acessibilidade, preservação de dados e recuperação de acesso testados nos fluxos aplicáveis.
- [ ] Cada formulário salva no destino correto antes de redirecionar e possui evidência de teste ponta a ponta em produção.
- [ ] Favicon e imagem de compartilhamento configurados.
- [ ] SEO básico configurado.
- [ ] Sitemap e robots revisados.
- [ ] Google Search Console configurado.
- [ ] Bing Webmaster Tools configurado e sitemap processado para sites públicos indexáveis.
- [ ] Política de crawlers de busca/IA e bloqueios da Cloudflare conferidos na URL pública final, conforme a decisão do projeto.
- [ ] GTM instalado e publicado.
- [ ] GA4 recebendo dados.
- [ ] Conversões principais rastreadas.
- [ ] Conversões foram conferidas sem duplicidade e sem PII em GTM, GA4, Google Ads, Meta e ferramentas de comportamento aplicáveis.
- [ ] APIs públicas de captação possuem validação server-side, CORS, proteção contra abuso e idempotência proporcional ao risco.
- [ ] Quando houver login, área privada ou dados de mais de um usuário/empresa, autenticação server-side, autorização por registro e RLS/isolamento equivalente foram testados com identidades distintas.
- [ ] Quando houver upload, os limites, tipos permitidos, armazenamento privado/público e acesso aos arquivos foram testados conforme o risco.
- [ ] Nenhum segredo foi encontrado no cliente, no repositório, no histórico do Git ou nos artefatos de deploy; credenciais anteriormente expostas foram rotacionadas.
- [ ] Auditoria de dependências e headers de segurança foi concluída conforme a arquitetura do projeto.
- [ ] Meta Pixel configurado se necessário para o uso autorizado de mídia Meta e compatível com as escolhas de privacidade.
- [ ] Google Ads tag/conversão configurada, se houver uso de mídia Google.
- [ ] Clarity configurado, quando fizer sentido.
- [ ] Política de privacidade publicada.
- [ ] Backup e acessos documentados.
- [ ] Pendências restantes documentadas como melhoria futura, não como requisito crítico.
