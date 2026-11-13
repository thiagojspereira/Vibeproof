# LGPD, privacidade e cookies

Use para mapear dados, revisar avisos, controles e consentimento conforme o contexto do projeto.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Mapeie dados, finalidades, bases legais, fornecedores, retenção e fluxos; envolva responsável jurídico quando necessário.
2. Prepare políticas e escolhas de privacidade coerentes com o tratamento real.
3. Configure controles antes de carregar tecnologias opcionais conforme a decisão jurídica aplicável; teste aceite, recusa, alteração e retirada.
4. Confira transmissão, gravações, logs e URLs; teste direitos do titular, descadastro e retenção aplicáveis.

## Verificação prática

- [ ] Inventariar cookies, armazenamento, scripts e chamadas de terceiros antes e depois de cada escolha; classificar finalidade e necessidade com o responsável pelo tratamento.
- [ ] Conferir que escolhas são compreensíveis, registradas quando necessário, acessíveis novamente e respeitadas após recarga, alteração e retirada. Testar em janela limpa e em mais de uma página.
- [ ] Quando houver Consent Mode, definir estados iniciais por finalidade antes das tags e atualizá-los após a escolha. Na implementação básica do Google, tags são bloqueadas sem consentimento; na avançada podem ser enviados sinais sem cookies mesmo com recusa. Verificar a decisão aplicável, inclusive chamadas de terceiros: Consent Mode sozinho não demonstra conformidade.
- [ ] Mapear recebimento e atendimento de pedidos dos titulares, prazo e exclusão/retenção com responsáveis; revisar compartilhamento e contratos com fornecedores.
- [ ] Testar que formulário, gravação de sessão, eventos e URLs não expõem dados pessoais sem necessidade. Conteúdo jurídico e base legal dependem da realidade e da avaliação competente do projeto.

## LGPD, privacidade e cookies

- [ ] Política de privacidade publicada.
- [ ] Política de cookies publicada, se necessário.
- [ ] Termos de uso publicados, se necessário.
- [ ] Banner configurado quando necessário; se o tratamento depender de consentimento, oferecer escolha real e acessível de aceitar, recusar e alterar a decisão, sem condicionar indevidamente o serviço ao aceite integral.
- [ ] Consent Mode v2 avaliado/configurado, se necessário.
- [ ] Formulários têm aviso de finalidade, se necessário.
- [ ] Nenhum dado sensível enviado para GA4/GTM/Pixel.
- [ ] Campos sensíveis mascarados em ferramentas de gravação.
- [ ] ReCAPTCHA/anti-spam avaliado.
- [ ] Consentimento do formulário é registrado com versão/data quando necessário.
- [ ] URLs de redirecionamento e eventos não expõem dados pessoais em query strings.
- [ ] Página/processo de descadastro, se houver email marketing.

---

Referências: [ANPD — guia sobre cookies](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-cookies-e-protecao-de-dados-pessoais.pdf/%40%40display-file/file) e [Google — modos de consentimento](https://developers.google.com/tag-platform/security/concepts/consent-mode).
