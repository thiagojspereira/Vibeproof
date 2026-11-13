# Analytics - GA4, GTM, Clarity e Search Console

Use para instalar, revisar ou diagnosticar mensuração e ferramentas de descoberta.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Confirme domínio, ambientes, contas, acessos e ferramentas necessárias; identifique instalações existentes para evitar duplicação.
2. Defina eventos, significado, origem, parâmetros, consentimento e resultado esperado; preserve dados pessoais fora das ferramentas.
3. Configure GTM e GA4 pelo método escolhido; adicione Clarity e Search Console quando pertinentes.
4. Teste consentimento aceito e negado, eventos reais e rejeitados, duplicidade, navegação e mascaramento; compare navegador e plataformas.
5. Publique quando autorizado, confira recebimento real e registre o que depende de processamento posterior.

## Google Tag Manager

- [ ] Container GTM criado ou confirmado.
- [ ] Código GTM instalado corretamente no site.
- [ ] GTM carregando em todas as páginas necessárias.
- [ ] GTM Preview testado.
- [ ] Tags, triggers e variáveis organizados com nomes claros.
- [ ] Não há tags nem containers duplicados.
- [ ] Data layer revisado, se usado.
- [ ] GTM publicado em produção após validação.

---

## GA4

- [ ] Propriedade GA4 criada ou confirmada.
- [ ] Stream web configurado.
- [ ] GA4 instalado via GTM ou método definido.
- [ ] Enhanced Measurement revisado.
- [ ] Page views chegando no Realtime.
- [ ] DebugView testado.
- [ ] Eventos definidos no plano de eventos deste guia disparam corretamente no GA4, com os eventos relevantes marcados como principais, quando aplicável.
- [ ] Tráfego interno filtrado, se possível.
- [ ] Retenção de dados revisada.
- [ ] Acessos administrativos documentados.

---

## Eventos e conversões

- [ ] Plano simples de mensuração definido.
- [ ] Conversão principal e conversões secundárias definidas.
- [ ] Cliques em CTA rastreados, se necessário.
- [ ] Envios de formulário rastreados.
- [ ] Evento de conversão dispara somente depois da confirmação real do backend ou do resultado de negócio definido.
- [ ] Erros de validação, falhas de API e simples abertura do formulário não disparam conversão.
- [ ] Cliques em WhatsApp rastreados.
- [ ] Cliques em telefone rastreados, se aplicável.
- [ ] Cliques em email rastreados, se aplicável.
- [ ] Downloads rastreados, se houver.
- [ ] Cadastro/compra/agendamento rastreado, se aplicável.
- [ ] Eventos nomeados de forma consistente.
- [ ] Parâmetros dos eventos seguem o contrato documentado e não contêm nome, email, telefone, mensagem ou outro dado pessoal.
- [ ] Definir o tratamento dos eventos antes da escolha de consentimento: não presumir que eventos anteriores serão reenviados; validar o comportamento desejado, sem guardar dados pessoais no `dataLayer` ou contornar a escolha da pessoa.
- [ ] Consentimento negado e consentimento aceito foram testados separadamente.
- [ ] O mesmo envio não gera duplicidade dentro de cada destino; o mesmo fato pode ser enviado legitimamente a plataformas diferentes, conforme consentimento e plano de mensuração.
- [ ] UTMs e origem chegam ao armazenamento do lead sem serem incluídas como PII nas ferramentas de analytics.
- [ ] Eventos testados em desktop e mobile.

Exemplos de nomes personalizados; antes de adotá-los, conferir os eventos recomendados da plataforma e evitar duplicação:

| Evento | Quando usar |
|---|---|
| `cta_clicked` | Clique em CTA principal ou secundário |
| `form_submitted` | Envio de formulário |
| `whatsapp_clicked` | Clique para WhatsApp |
| `phone_clicked` | Clique em telefone |
| `email_clicked` | Clique em email |
| `lead_generated` | Lead confirmado |
| `purchase_completed` | Compra concluída, se ecommerce |
| `signup_completed` | Cadastro concluído, se app/SaaS |
| `download_completed` | Download de material |

---

## Microsoft Clarity

- [ ] Projeto Clarity criado ou confirmado.
- [ ] Script instalado via GTM ou método definido.
- [ ] Sessões chegando no Clarity.
- [ ] Heatmaps funcionando.
- [ ] Máscara de campos sensíveis e conteúdo pessoal conferida nas configurações e em gravação de teste; não presumir que a máscara automática cobre tudo. Se usar Consent Mode do Clarity, testar sinais e verificar também eventuais chamadas sem cookies após recusa, conforme política do projeto.
- [ ] Gravações revisadas após teste.
- [ ] Configuração de privacidade revisada.
- [ ] Acesso documentado.

---

## Google Search Console

- [ ] Propriedade criada.
- [ ] Domínio verificado.
- [ ] Verificação por DNS ou tag confirmada.
- [ ] Sitemap enviado.
- [ ] Inspeção da URL principal feita.
- [ ] Inspecionar páginas importantes e, se necessário, solicitar indexação de URLs individuais; envio ou solicitação não garante indexação.
- [ ] Cobertura/indexação revisada.
- [ ] Experiência em dispositivos móveis revisada nas ferramentas disponíveis; não presumir que o relatório antigo Mobile Usability ainda exista.
- [ ] Core Web Vitals monitorado.
- [ ] Usuários/permissões documentados.

Referências: [Google — eventos principais e conversões](https://support.google.com/analytics/answer/13965727), [Microsoft — consentimento no Clarity](https://learn.microsoft.com/en-us/clarity/setup-and-installation/consent-management) e [Google — solicitar rastreamento](https://developers.google.com/search/docs/crawling-indexing/ask-google-to-recrawl).
