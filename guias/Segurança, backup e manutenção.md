# Segurança, backup e manutenção

Use para avaliar riscos e executar medidas de proteção proporcionais à arquitetura.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Inventarie dados, acessos, integrações e fronteiras de confiança; priorize fluxos expostos e dados sensíveis.
2. Revise autenticação, autorização, segredos, dependências e proteção das entradas.
3. Teste isolamento e fluxos negativos com dados fictícios em ambiente apropriado, sem presumir que uma tela bloqueada protege a API.
4. Verifique backup, restauração e manutenção conforme o risco; registre achados, correções e limitações.

## Segurança, backup e manutenção

- [ ] CMS atualizado, se houver.
- [ ] Plugins atualizados, se houver.
- [ ] Tema atualizado, se houver.
- [ ] Dependências inventariadas e revisadas, se projeto custom.
- [ ] Auditoria automatizada de dependências foi executada; vulnerabilidades relevantes foram corrigidas, mitigadas ou justificadas antes da publicação.
- [ ] Usuários administrativos revisados.
- [ ] Senhas fortes.
- [ ] 2FA ativado onde possível.
- [ ] Usuários desnecessários removidos.
- [ ] Backups automáticos ativos.
- [ ] Restauração de backup testada periodicamente em ambiente apropriado; registrar data, resultado e pendência quando ainda não houver teste.
- [ ] Firewall/WAF avaliado, se aplicável.
- [ ] Login protegido, se WordPress.
- [ ] Comentários desativados, se não usados.
- [ ] XML-RPC desativado, se WordPress e se fizer sentido.
- [ ] Monitoramento de uptime avaliado.
- [ ] Segredos e chaves privadas existem somente no backend ou cofre apropriado, nunca no HTML, JavaScript público, repositório ou analytics.
- [ ] Histórico do Git, logs de build e artefatos de deploy foram verificados para segredos; qualquer credencial que tenha sido exposta foi revogada e rotacionada, não apenas removida do arquivo atual.
- [ ] Chaves deliberadamente publicáveis, como uma `anon key` ou `publishable key`, estão claramente separadas de chaves privilegiadas; `service role`, admin keys e credenciais privadas nunca chegam ao cliente.
- [ ] Dados trafegam por HTTPS e a proteção em repouso, dos backups e de campos especialmente sensíveis foi confirmada conforme o risco e os recursos do provedor.
- [ ] Autenticação e autorização são verificadas no servidor em toda operação protegida; esconder elementos na interface não é tratado como controle de acesso.
- [ ] Rotas e consultas que recebem IDs verificam a permissão sobre o registro solicitado e impedem acesso horizontal entre usuários, contas ou empresas.
- [ ] RLS ou mecanismo equivalente de isolamento está ativo nas tabelas expostas e foi testado com usuários/empresas distintos, inclusive para leitura, criação, alteração e exclusão aplicáveis.
- [ ] Com dados fictícios em ambiente de testes, criar usuários A e B em contas/empresas distintas, sem permissão compartilhada. Em sessões independentes (navegadores diferentes ou janela normal e anônima), abrir um registro privado como A e tentar acessar sua URL como B: o conteúdo não deve ser exposto.
- [ ] Repetir diretamente nas APIs e demais pontos de acesso a dados, usando a sessão de B e o identificador do registro de A: testar leitura, alteração e exclusão aplicáveis, além de criação associada indevidamente à conta de A. Conferir respostas e estado dos dados; uma tela bloqueada ou botão oculto não comprova a proteção.
- [ ] Corrigir falhas na autorização do servidor, nas políticas RLS ou no mecanismo equivalente, considerando empresa, vínculo, papel e operação permitida; repetir os testes negativos e os acessos legítimos após a correção. Aplicar aos recursos e perfis relevantes e registrar pendências: passar em um exemplo não garante o isolamento de toda a aplicação.
- [ ] APIs aceitam somente campos explicitamente permitidos; propriedades de permissão, proprietário, empresa, preço, status ou função não podem ser alteradas por mass assignment.
- [ ] Senhas são processadas por provedor confiável ou protegidas com hash adaptativo e salt individual; priorizar Argon2id. Para legado com bcrypt, verificar o limite de 72 bytes e evitar truncamento silencioso; nunca usar criptografia reversível ou hash genérico simples. Conferir parâmetros atuais da OWASP.
- [ ] Cookies de sessão usam `Secure`, `HttpOnly` e `SameSite` compatíveis com o fluxo; proteção contra CSRF foi aplicada quando a arquitetura depender de cookies para autenticação.
- [ ] CORS/origens permitidas foram revisados nas APIs públicas.
- [ ] Validação e normalização são feitas novamente no servidor; validação do navegador não é tratada como segurança.
- [ ] Consultas ao banco usam parâmetros, ORM seguro ou query builder; valores recebidos do usuário não são concatenados em SQL ou comandos equivalentes.
- [ ] Entradas são escapadas antes de aparecerem em email, painel, logs ou HTML para reduzir risco de XSS/injeção.
- [ ] Uploads exigem as permissões apropriadas e verificam extensão permitida, conteúdo/tipo real, tamanho e quantidade; `accept` e MIME informado pelo navegador não bastam. Nomes e destinos são controlados pela aplicação e arquivos enviados não podem ser executados como código.
- [ ] Arquivos privados usam armazenamento privado e URLs assinadas com validade curta; uploads públicos foram uma decisão consciente e não expõem documentos ou dados pessoais.
- [ ] Respostas de API retornam somente os campos necessários ao cliente e não expõem dados pessoais desnecessários, campos internos, tokens, segredos ou registros de outros usuários.
- [ ] Headers de segurança foram revisados conforme a arquitetura, incluindo CSP, HSTS, `X-Content-Type-Options`, proteção contra framing e `Referrer-Policy`, sem bloquear integrações legítimas do projeto.
- [ ] Banco e integrações usam o menor nível de privilégio necessário.
- [ ] Rate limit, idempotência e tratamento de concorrência foram testados nas rotas públicas críticas.
- [ ] Respostas de erro não expõem stack trace, credenciais, estrutura interna ou dados de outros usuários.

---

Referência: [OWASP — armazenamento de senhas](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html).
