# Integrações e automações

Use para instalar ou revisar integrações, notificações e fluxos entre serviços.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Mapeie origem, destino, credenciais, eventos, responsáveis e dependências.
2. Configure o fluxo autorizado e mecanismos de autenticação, erro e repetição adequados.
3. Teste ponta a ponta, falha HTTP, timeout, duplicidade e recuperação com dados controlados.
4. Confirme destino e monitoramento e documente a operação e alternativa manual.

## Integrações e automações

- [ ] CRM conectado, se aplicável.
- [ ] Email marketing conectado, se aplicável.
- [ ] SMTP/Resend/Mailgun testado, se aplicável.
- [ ] Integrações com gerenciador de tarefas, automação, webhook ou planilha foram testadas, se aplicável.
- [ ] Endpoints, workflows e destinos legados ou desativados não continuam referenciados pelo site.
- [ ] Webhooks com autenticação ou verificação de assinatura quando suportada, e logs úteis sem expor segredos ou dados pessoais desnecessários.
- [ ] Erros de automação monitoráveis; testar repetição e idempotência em eventos que possam chegar mais de uma vez.
- [ ] Respostas HTTP não exitosas são verificadas; a aplicação não trata apenas erros de rede como falha.
- [ ] Dependências externas possuem timeout e comportamento de fallback definido.
- [ ] Fallback manual documentado.
- [ ] Acessos externos documentados em local seguro, quando aplicável.

---
