# Formulários, captação e recuperação de acesso

Use para criar ou revisar formulários, captação, login e recuperação de acesso; aplique apenas os fluxos existentes.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Inventarie formulários, campos, destinos, tipos de usuário, regras e integrações.
2. Implemente clareza, validação acessível, estados e persistência; valide e proteja dados também no servidor.
3. Teste envio de ponta a ponta: resposta, armazenamento, notificação, destino e evento; teste falha, reenvio e duplicidade.
4. Quando houver conta, teste cadastro, login, recuperação e MFA aplicáveis, inclusive expiração, erros e retomada.
5. Verifique teclado, celular e tecnologias assistivas, com evidências e sem dados reais desnecessários.

## Formulários, WhatsApp e captação

- [ ] Todos os formulários do projeto foram inventariados, inclusive os presentes em modais, rodapés, páginas secundárias e versões mobile.
- [ ] Cada formulário foi enviado de verdade em produção com um registro técnico identificável.
- [ ] O backend rejeita payload ausente, inválido, excessivo ou enviado por origem não autorizada.
- [ ] O envio possui proteção proporcional contra spam e abuso, como rate limit, honeypot, desafio ou WAF.
- [ ] Tentativas repetidas usam idempotência ou outra proteção contra leads, pedidos e notificações duplicados.
- [ ] Redirecionamento pós-envio acontece somente após o backend confirmar o registro.
- [ ] O redirecionamento foi validado por allowlist e não aceita uma URL arbitrária retornada pela API.
- [ ] O registro completo chegou ao banco, CRM, planilha ou outro destino definido.
- [ ] Campos de origem, página, referência e UTMs foram preservados no registro.
- [ ] Notificação chegou ao destinatário correto e permite responder ao contato quando aplicável.
- [ ] Falha da notificação não apaga nem duplica um registro já salvo.
- [ ] Retry do mesmo envio não dispara nova notificação quando não cria um novo registro.
- [ ] Email de confirmação ao usuário chegou, se houver.
- [ ] Logs permitem auditar falhas sem registrar segredos ou dados pessoais desnecessários.
- [ ] WhatsApp com número correto.
- [ ] WhatsApp com mensagem pré-preenchida e referência suficiente para localizar o registro.
- [ ] Nome, email, telefone, faturamento e outros dados pessoais não aparecem na URL do WhatsApp ou em parâmetros públicos.
- [ ] Botões de WhatsApp testados no desktop.
- [ ] Botões de WhatsApp testados no celular.
- [ ] Foi confirmado que abrir o WhatsApp não equivale a enviar a mensagem; o armazenamento anterior ao redirecionamento cobre abandono nessa etapa.
- [ ] Telefone clicável no mobile, se aplicável.
- [ ] Links `mailto:` funcionando, se usados.
- [ ] Evento de redirecionamento ou clique no WhatsApp é separado do evento de lead confirmado.
- [ ] Os eventos foram conferidos no GTM Preview, GA4 DebugView, Google Ads, Meta Events Manager e ferramenta de sessão aplicável.

---

## Formulários: experiência, validação e recuperação de acesso

> Conteúdo inicial baseado em fontes oficiais de 25/10/2026; orientações principais revisadas em 13/11/2026. Aplicar a todos os formulários: contato, newsletter, cadastro, login, recuperação de senha, perfil, busca/filtros, checkout e uploads. Marcar `N/A` nos fluxos inexistentes. Este guia reúne captação e destino; complemente com [Segurança, backup e manutenção](Seguran%C3%A7a%2C%20backup%20e%20manuten%C3%A7%C3%A3o.md).
>
> Os itens abaixo são uma síntese prática para QA; recomendações de produto não são todas exigências normativas. Para acessibilidade, usar WCAG 2.2 AA como referência e verificar os critérios aplicáveis. Não basta marcar “funcionou”: testar correção de erro e recuperação de falha.

### Clareza, campos e instruções

- [ ] Cada formulário tem finalidade clara e solicita apenas os dados necessários; campos opcionais não impedem concluir a tarefa.
- [ ] Labels permanecem visíveis durante o preenchimento; placeholder não substitui label.
- [ ] Todo controle possui nome acessível associado ao rótulo visível; IDs são únicos mesmo quando o formulário aparece mais de uma vez na página.
- [ ] Obrigatoriedade e campos opcionais são indicados de forma consistente; asteriscos, quando usados, são explicados e não dependem só de cor.
- [ ] Restrições relevantes aparecem antes do erro: formato, limite de caracteres, unidade, tamanho de arquivo e política de senha.
- [ ] Exemplos ajudam sem parecer valores já preenchidos; instruções essenciais não ficam apenas em tooltip ou hover.
- [ ] Campos relacionados estão agrupados visualmente e semanticamente; grupos de radios/checkboxes usam `fieldset`/`legend` ou equivalente acessível.
- [ ] Checkboxes representam escolhas independentes; radios representam uma escolha entre opções; nenhum valor padrão presume uma decisão relevante do usuário.
- [ ] Rótulo do botão descreve a ação: “Criar conta”, “Salvar alterações”, “Solicitar orçamento” ou “Pagar R$ …”, conforme o contexto.
- [ ] Ação principal, voltar e cancelar são distinguíveis; não há botão de limpar/reset que apague tudo por engano.

Referências: [W3C — labels](https://www.w3.org/WAI/tutorials/forms/labels/), [instruções](https://www.w3.org/WAI/tutorials/forms/instructions/) e [agrupamento](https://www.w3.org/WAI/tutorials/forms/grouping/).

### Digitação, formatos e preenchimento automático

- [ ] `type`, `inputmode` e `autocomplete` correspondem ao dado; o teclado mobile facilita email, telefone e números decimais.
- [ ] Nome, email, telefone e endereço aceitam preenchimento automático; testar valores preenchidos sem digitação manual.
- [ ] Login usa `autocomplete="username"` e `current-password`; criação/redefinição usa `new-password`; códigos usam `one-time-code` quando apropriado.
- [ ] Colar e usar gerenciadores de senha funciona, inclusive nos códigos de verificação; não exigir transcrição manual desnecessária.
- [ ] Identificadores como CEP, CPF e códigos preservam zeros iniciais; `type="number"` fica reservado a quantidades, não identificadores.
- [ ] Máscaras permitem colar, apagar, selecionar e editar no meio; aceitar entrada sem máscara quando não houver ambiguidade.
- [ ] Nomes reais com acentos, espaços, hífen e apóstrofo não são rejeitados por regex simplista; não exigir sobrenome quando não for necessário.
- [ ] Emails com `+`, subdomínios e domínios longos são aceitos; sugestão de correção de domínio não substitui o valor sem consentimento.
- [ ] Telefone aceita os países atendidos e explicita DDI; não pressupor formato brasileiro se o público for internacional.
- [ ] Datas, moeda, separadores decimais e fuso seguem o contexto; testar data impossível, ano bissexto e limites de período aplicáveis.
- [ ] Busca de CEP/endereço permite correção e alternativa manual quando o serviço falha ou não encontra o local.
- [ ] Normalização remove apenas o que foi definido como irrelevante; não alterar silenciosamente senha, nome ou conteúdo significativo.

Referências: [MDN — autocomplete](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/autocomplete), [inputmode](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode), [GOV.UK — validação tolerante a formatos](https://design-system.service.gov.uk/patterns/validation/) e [OWASP — validação de entradas](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html).

### Quando validar e como mostrar o erro

- [ ] Campos ainda não visitados não aparecem como inválidos ao abrir a tela; não acusar erro enquanto a pessoa ainda está começando a resposta.
- [ ] Validar no envio; validação ao sair do campo ou durante correção só é usada quando ajuda, sem roubar foco nem interromper a digitação.
- [ ] Após corrigir, a mensagem desatualizada desaparece ou é atualizada; não deixar o campo vermelho até outro envio sem necessidade.
- [ ] Cada erro de campo aparece junto ao respectivo controle e informa como corrigir; não depender só de toast, borda vermelha ou ícone.
- [ ] Após envio inválido, um resumo acessível com links aos campos é usado quando necessário para localizar os problemas; o foco vai ao resumo ou primeiro erro conforme a estrutura.
- [ ] Vários erros são apresentados juntos quando conhecidos; evitar obrigar a pessoa a descobrir um campo inválido por tentativa.
- [ ] Mensagens distinguem falta de preenchimento, formato incorreto, limite e regra de negócio; não usar apenas “Inválido” ou “Algo deu errado”.
- [ ] Erros retornados pelo servidor são associados ao campo correto; falha geral aparece no formulário sem responsabilizar um campo válido.
- [ ] Validações assíncronas ignoram respostas antigas; resultado de um email/CEP anterior não sobrescreve o valor atual.
- [ ] Regras do navegador e servidor são compatíveis, incluindo limites; desativar validação nativa só quando houver substituição completa e acessível.

Referências: [W3C — validação](https://www.w3.org/WAI/tutorials/forms/validation/), [notificações](https://www.w3.org/WAI/tutorials/forms/notifications/) e [GOV.UK — resumo de erros](https://design-system.service.gov.uk/components/error-summary/).

### Envio, espera, sucesso e falha

- [ ] O botão permite descobrir os erros ao tentar enviar; se ficar desabilitado por pré-condição, o motivo é perceptível e acessível.
- [ ] Durante envio, há indicação textual de progresso; o botão fica desabilitado para impedir submissões concorrentes e a proteção contra duplicidade também existe no servidor; spinner sozinho não explica o estado.
- [ ] Enter envia quando esperado, mas não transforma quebra de linha de textarea nem seleção de autocomplete em envio acidental; botões auxiliares usam `type="button"`.
- [ ] Requisição tem limite de espera e saída recuperável; o botão não fica eternamente preso em “Enviando…”.
- [ ] Falha de rede, timeout, indisponibilidade e limite de tentativas oferecem próximo passo útil; informar quando aguardar antes de tentar novamente.
- [ ] Valores não sensíveis permanecem após erro; senhas, códigos e anexos seguem tratamento seguro, com aviso se precisarem ser informados novamente.
- [ ] Quando há timeout após possível gravação, verificar o resultado ou reutilizar a mesma chave de idempotência antes de repetir a operação.
- [ ] Sucesso só aparece após confirmação real e esclarece o que aconteceu e o próximo passo; “Solicitação recebida” não promete aprovação ou entrega ainda pendente.
- [ ] Ao salvar alterações, fica claro se há dados não salvos, salvamento em curso ou falha; autosave não aparenta sucesso antes da persistência.
- [ ] Instrumentação distingue início, erro e conclusão sem enviar o conteúdo dos campos; conferir também URLs, gravações e ferramentas de erro.

Validação ponta a ponta do armazenamento, notificações e conversões: a seção de captação deste guia. Tratamento HTTP e integrações: [Integrações e automações](Integra%C3%A7%C3%B5es%20e%20automa%C3%A7%C3%B5es.md).

### Aparência e comportamento dos componentes abertos

- [ ] Abrir e inspecionar todos os dropdowns, selects, autocompletes, seletores de data/hora, menus de ações, tooltips e popovers; a revisão visual inclui o painel aberto, não apenas o acionador fechado.
- [ ] Painéis e opções seguem a identidade visual vigente da plataforma: tipografia, cores, bordas, raios, sombras, espaçamento, ícones e densidade. Corrigir listas com aparência genérica que destoem do campo e da interface ao redor.
- [ ] Conferir os estados normal, hover, foco por teclado, selecionado, desabilitado, carregando, vazio e erro; destaque de seleção e foco são legíveis e coerentes com a plataforma.
- [ ] Não considerar um select aprovado apenas porque o campo fechado recebeu CSS. Verificar a lista de opções real nos navegadores atendidos; quando o popup nativo impedir a aderência visual exigida, adotar um componente acessível com painel estilizado e testar sua interação completa.
- [ ] Diferenciar seleção de valor de menu de ações: o componente e sua semântica correspondem à tarefa; não aplicar comportamento de menu a uma lista de opções de formulário.
- [ ] O painel alinha com o acionador, tem largura coerente e acomoda rótulos longos; altura máxima e rolagem mantêm todas as opções alcançáveis sem estourar a viewport.
- [ ] A abertura se adapta ao espaço disponível, inclusive perto das bordas e no mobile; nenhum painel fica cortado por containers, atrás de modais ou sobreposto de forma a impedir a tarefa.
- [ ] Dentro de modal, portal/camada do dropdown mantém interação e foco corretos; rolar a página, redimensionar ou abrir o teclado virtual não deixa o painel solto ou desalinhado.
- [ ] Abrir, navegar, selecionar e fechar funciona por mouse, toque e teclado conforme o tipo de componente; testar setas, Enter/Espaço, Escape, Tab e busca por digitação quando aplicáveis. Fechar não altera o valor sem seleção e o foco retorna ao lugar esperado.
- [ ] Seleção atual é evidente e opções desabilitadas são distinguíveis; listas pesquisáveis mostram carregamento, nenhum resultado e falha com próximo passo útil.
- [ ] Quando existe apenas uma opção válida, avaliar se um valor fixo explicado resolve melhor que um dropdown sem escolha real.
- [ ] Testar estados abertos nos temas existentes, desktop e mobile, incluindo Safari/iOS quando atendido. Seletores do sistema podem ser usados quando forem adequados à experiência mobile; isso não dispensa corrigir a inconsistência visual exigida na superfície desktop.
- [ ] Registrar evidência com o componente aberto e testar a interação real; screenshot do campo fechado, inspeção do código ou build sem erros não aprovam esta revisão.

### Acessibilidade e uso no celular

- [ ] Ajuda e erro estão associados ao campo (`aria-describedby` ou equivalente); `aria-invalid` reflete o estado real.
- [ ] Atualizações de erro, espera e sucesso são anunciadas por leitor de tela sem anúncios repetitivos a cada tecla; live regions são usadas com moderação.
- [ ] Ao mudar etapa, o foco vai ao título ou conteúdo relevante; comportamento geral de modais segue [Navegação, estados e interações](Navega%C3%A7%C3%A3o%2C%20estados%20e%20intera%C3%A7%C3%B5es.md).
- [ ] Teclado virtual, cabeçalho fixo e rodapé sticky não escondem o campo focado, mensagens ou ação principal.
- [ ] Autenticação permite mecanismos de auxílio, como colar e gerenciadores; CAPTCHA/desafios têm alternativa acessível aplicável, sem depender só de quebra-cabeça visual.

Referências: [W3C — formulários](https://www.w3.org/WAI/tutorials/forms/), [autenticação acessível](https://www.w3.org/WAI/WCAG22/Understanding/accessible-authentication-minimum.html) e [tamanho dos alvos](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html).

### Login, cadastro e senhas — se houver conta

- [ ] Login, cadastro e “Esqueci minha senha” são fáceis de localizar; links preservam contexto não sensível quando útil.
- [ ] Email/senha incorretos recebem mensagem útil sem revelar qual conta existe; avaliar também diferenças em status HTTP e tempo de resposta.
- [ ] Contas não verificadas, acesso pendente ou bloqueio têm caminho de resolução apropriado sem expor dados a terceiros.
- [ ] Mostrar/ocultar senha funciona por teclado e leitor de tela, anuncia a ação/estado e não envia o formulário nem perde o texto.
- [ ] Evitar confirmação redundante de senha quando mostrar/ocultar e boa orientação resolvem o problema; se houver confirmação, divergência é explicada.
- [ ] Política aplicada igualmente no cadastro, troca e redefinição.
- [ ] Antes de implementar, discutir e registrar com o responsável a política de senhas do projeto: mínimo e máximo de caracteres, possibilidade de usar maiúsculas, minúsculas, números, símbolos, espaços e frases longas; decidir se alguma classe será obrigatória, considerando público, risco, MFA, acessibilidade e limites reais do provedor. Explicar a decisão e mostrar as regras na interface antes do envio.
- [ ] Usar como referência o NIST SP 800-63B-4: mínimo de 15 caracteres quando a senha é o único fator; mínimo de 8 pode ser usado quando a senha é utilizada exclusivamente como parte de MFA. São parâmetros de referência, não obrigação legal universal nem substituto da discussão sobre o projeto.
- [ ] Considerar permitir no mínimo 64 caracteres como limite máximo, espaços e caracteres Unicode; não truncar silenciosamente. O NIST desaconselha exigir combinações obrigatórias de maiúsculas, minúsculas, números e símbolos ou trocas periódicas sem evidência de comprometimento. Se houver regra externa ou limite do provedor, documentar e comunicar a exceção.
- [ ] Senhas comuns/comprometidas são bloqueadas no servidor; não enviar a senha em texto puro a serviços externos de consulta.
- [ ] Verificação de email oferece reenvio com limite, correção do endereço pelo fluxo apropriado e tratamento de link vencido ou usado.
- [ ] Login social trata cancelamento, provedor indisponível e callback inválido; não vincular contas só porque o email coincide sem garantias apropriadas.
- [ ] Para cada provedor social oferecido, testar o fluxo completo no domínio final: início, consentimento, callback, criação ou retomada da sessão, redirecionamento e acesso à área protegida; sair e entrar novamente com uma conta já vinculada. Chegar ao seletor do provedor não comprova o login.
- [ ] Testar cadastro novo e coincidência com conta existente, inclusive conta sem vínculo, não verificada, bloqueada ou de teste, quando aplicável. Oferecer orientação e recuperação seguras; só informar que um endereço está cadastrado quando o fluxo tiver prova apropriada de controle do endereço e isso não permitir enumeração indevida.
- [ ] Ao interromper ou concluir cadastro com provedor externo, preservar as escolhas não sensíveis necessárias ao onboarding e retomá-las no destino correto; falhas e recusas mostram uma saída útil na tela de origem, sem exigir senha de quem ainda não a cadastrou.
- [ ] Registrar etapas e falhas de autenticação com categorias úteis ao diagnóstico, sem email, tokens, códigos ou credenciais nos logs e analytics; proteger parâmetros temporários do callback contra vazamento e distinguir falha no provedor, vínculo, sessão e redirecionamento.
- [ ] Após autenticação, o retorno leva ao destino permitido; login expirado oferece reautenticação sem perder trabalho não sensível quando viável.
- [ ] Logout encerra a sessão; voltar no navegador não permite novas ações protegidas. Troca de email/senha exige reautenticação proporcional ao risco e comunicação de segurança.
- [ ] O isolamento de dados entre contas e usuários foi testado conforme [Segurança, backup e manutenção](Seguran%C3%A7a%2C%20backup%20e%20manuten%C3%A7%C3%A3o.md), além dos fluxos de login.

Referências: [GOV.UK — campo de senha](https://design-system.service.gov.uk/components/password-input/), [OWASP — autenticação](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) e [NIST SP 800-63B-4, seção 3.1.1](https://pages.nist.gov/800-63-4/sp800-63b.html). A referência NIST é orientação técnica, não obrigação legal universal.

### “Esqueci minha senha” e recuperação de acesso

- [ ] Testar pedido → recebimento → abertura do link → nova senha → login; não concluir o teste apenas pela tela “Email enviado”.
- [ ] Pedido retorna resposta equivalente para email existente ou inexistente, sem diferença explorável de tempo; não confirmar existência de conta.
- [ ] Orientar a conferir spam e oferecer reenvio limitado, correção do email e volta ao login; não prometer recebimento quando só houve aceite para processamento.
- [ ] Email identifica o serviço, usa domínio confiável e explica validade e procedimento quando o pedido não foi feito pelo titular.
- [ ] Tokens/códigos são imprevisíveis, armazenados com segurança, expiram e são consumidos uma única vez com proteção contra uso simultâneo.
- [ ] Links vencidos, adulterados ou usados mostram saída recuperável para solicitar outro; nunca página vazia ou erro técnico.
- [ ] Senha só muda após prova válida; solicitar recuperação não bloqueia nem altera a conta.
- [ ] Recuperação tem proteção contra abuso por conta/origem e tentativas de código; não usar perguntas pessoais como único meio de recuperar acesso.
- [ ] Token não vaza para analytics, logs ou terceiros via referência; página de redefinição evita recursos externos desnecessários e usa política de referência adequada.
- [ ] Após redefinir, notificar o titular, aplicar política de revogação das sessões existentes e direcionar ao login normal; não autenticar automaticamente pelo simples reset.
- [ ] Testar o link em outro navegador/dispositivo; recuperação de MFA ou perda do email tem procedimento próprio, se oferecida.

Referência: [OWASP — recuperação de senha](https://cheatsheetseries.owasp.org/cheatsheets/Forgot_Password_Cheat_Sheet.html).

### Códigos, MFA e links de acesso — se houver

- [ ] Código pode ser colado inteiro; se houver várias caixas, funcionam também seleção, apagar, teclado e leitor de tela.
- [ ] Email/telefone de destino aparece parcialmente mascarado; há caminho seguro para corrigir um destino errado.
- [ ] Código incorreto, vencido e excesso de tentativas têm mensagens e ações adequadas; reenvio informa quando estará disponível.
- [ ] Fica claro qual código vale após reenvio; anterior não continua válido indefinidamente.
- [ ] Voltar, recarregar e abrir o link duas vezes não cria sessões ou ações duplicadas; parâmetros de retorno são validados.
- [ ] Quando houver MFA, testar configuração, desafio, recuperação e códigos de backup; retirar/trocar fator exige comprovação adequada.
- [ ] Quando houver passkeys, testar cadastro, saída e entrada com credencial cadastrada, autenticação em dispositivo compatível, cancelamento, credencial ausente, remoção e alternativa de recuperação. Verificar origem/domínio e sessão resultante; distinguir autenticador virtual de prova com passkey real no dispositivo e domínio final.

Referências: [W3C — autenticação acessível](https://www.w3.org/WAI/WCAG22/Understanding/accessible-authentication-minimum.html) e [OWASP — autenticação](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html).

### Etapas, campos condicionais e rascunhos

- [ ] Formulários longos usam etapas coerentes quando isso melhora a tarefa; indicar posição e próximos passos sem prometer total incorreto em fluxos condicionais.
- [ ] Voltar permite editar sem apagar respostas; não exigir de novo dados já fornecidos no mesmo processo, salvo necessidade de segurança, validade ou outra exceção aplicável.
- [ ] Campos condicionais aparecem de modo compreensível; campos ocultos não geram erro inacessível nem enviam valores antigos indevidos.
- [ ] Mudança em resposta anterior recalcula dependências; valores incompatíveis são removidos ou reconfirmados explicitamente.
- [ ] Rascunho/retomada existe quando o esforço justificar; informar duração e respeitar privacidade em dispositivo compartilhado.
- [ ] Limite de sessão avisa e permite extensão quando aplicável; expiração oferece retomada segura e não apaga silenciosamente trabalho extenso.
- [ ] Sair com alterações importantes não salvas tem proteção proporcional; não depender exclusivamente de `beforeunload`, especialmente no mobile.

Referências: [W3C — formulários em etapas](https://www.w3.org/WAI/tutorials/forms/multi-page/) e [entrada redundante](https://www.w3.org/WAI/WCAG22/Understanding/redundant-entry.html).

### Uploads, pagamentos e ações de maior impacto

- [ ] Antes de anexar, informar formatos, tamanho e quantidade permitidos; oferecer seletor de arquivo além de arrastar e soltar.
- [ ] Mostrar arquivo escolhido, progresso real quando disponível, resultado e opções de remover/substituir; erro em um arquivo não apaga os demais sem necessidade.
- [ ] Upload interrompido não é exibido como concluído; validação, execução e armazenamento/acesso dos arquivos seguem [Segurança, backup e manutenção](Seguran%C3%A7a%2C%20backup%20e%20manuten%C3%A7%C3%A3o.md).
- [ ] Pagamentos, exclusões e compromissos relevantes oferecem revisão/correção, confirmação ou reversão apropriada ao risco.
- [ ] Checkout mostra valor total e condições antes da confirmação; preço e permissão são verificados no servidor.
- [ ] Pagamento pendente, recusado ou com autenticação adicional tem estado próprio; retorno do navegador não comprova liquidação.
- [ ] Recarregar, voltar e repetir após timeout não duplica cobrança/pedido; confirmação é reconciliada com o provedor.

Referências: [OWASP — uploads](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html) e [W3C — prevenção de erros em operações relevantes](https://www.w3.org/WAI/WCAG22/Understanding/error-prevention-legal-financial-data.html). Segurança complementar: [Segurança, backup e manutenção](Seguran%C3%A7a%2C%20backup%20e%20manuten%C3%A7%C3%A3o.md).

### Exemplos de mensagens para adaptar ao contexto

| Situação | Exemplo |
|---|---|
| Obrigatório vazio | “Informe seu email.” |
| Formato inválido | “Digite um email como nome@empresa.com.” |
| Regra de senha | “Use pelo menos 15 caracteres.” — somente se essa for a política real |
| Falha de autenticação | “Email ou senha incorretos. Tente novamente ou recupere sua senha.” |
| Pedido de recuperação | “Se houver uma conta com esse email, enviaremos as instruções para redefinir a senha.” |
| Link inválido/vencido | “Este link não é válido ou expirou. Solicite um novo link.” |
| Falha temporária | “Não foi possível concluir agora. Seus dados continuam preenchidos. Tente novamente.” — somente se os dados foram preservados |
| Envio com resultado incerto | “Ainda não conseguimos confirmar o envio. Verifique o status antes de tentar novamente.” — oferecer mecanismo real de consulta/reconciliação |
| Limite temporário | “Muitas tentativas. Tente novamente em …” — mostrar prazo real, quando disponível |
| Sucesso de captação | “Solicitação recebida. Entraremos em contato pelo email informado.” — somente se esse for o próximo passo real |

### Matriz mínima de testes e aceite

Executar por formulário/fluxo aplicável. Falhas destrutivas ou financeiras devem usar sandbox/ambiente controlado; em produção, validar o caminho real autorizado com dados técnicos identificáveis.

- [ ] Enviar vazio, com um erro, vários erros e correção parcial; confirmar texto, foco e desaparecimento do erro corrigido.
- [ ] Testar limites: mínimo/máximo, acima do máximo, espaços, acentos, colar, autofill e caracteres significativos ao contexto.
- [ ] Testar máscara e seletores com teclado, leitor de tela e celular; incluir teclado virtual aberto, zoom e mensagens longas.
- [ ] Testar rede lenta, desconexão, timeout e respostas 400/401/403/409/422/429/500 conforme o contrato da API.
- [ ] Testar clique duplo, Enter repetido, recarregar, voltar e duas abas; confirmar ausência de duplicidade e perda indevida de dados.
- [ ] Testar expiração de sessão e edição concorrente; conflitos não sobrescrevem alterações importantes silenciosamente.
- [ ] Nos fluxos de acesso, testar credencial incorreta, conta não verificada e links/códigos inválidos, expirados, reutilizados e reenviados.
- [ ] Confirmar resultado no servidor/destino e o que o usuário enxerga; nenhum sucesso falso, erro invisível ou tela sem saída.
- [ ] Registrar evidência curta por fluxo: URL, ambiente, cenário, resultado esperado/observado e dispositivo/navegador; não incluir senhas, tokens ou dados pessoais reais.
- [ ] Checklist só é aprovado com os cenários aplicáveis executados; itens apenas inspecionados no código e limitações de teste ficam explicitados.

**Bloqueiam a finalização:** não conseguir concluir/corrigir, erro sem orientação ou inacessível, recuperação de acesso quebrada, perda relevante de preenchimento, sucesso falso, duplicidade de efeito crítico, exposição de dados e barreira de acessibilidade no fluxo principal.

---
