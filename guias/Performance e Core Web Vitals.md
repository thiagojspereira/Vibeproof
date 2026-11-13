# Performance e Core Web Vitals

Use para diagnosticar e melhorar desempenho em páginas e jornadas relevantes.

## Como usar

1. Defina o objetivo, o ambiente, as páginas e os fluxos abrangidos; identifique responsáveis e integrações existentes.
2. Para revisar, observe o funcionamento real e registre os achados antes de propor correções. Para implementar, adapte os passos abaixo à arquitetura e ao escopo autorizado.
3. Marque somente o que foi efetivamente verificado; registre N/A com motivo e separe falhas, pendências e limitações. Não presuma que uma configuração no código comprova o resultado.
4. Teste os fluxos aplicáveis de ponta a ponta, inclusive falhas e produção quando autorizado. Registre evidências, destino, responsável e próximos passos sem guardar segredos ou dados pessoais.
5. Confira a documentação oficial e as regras vigentes quando for executar: produtos, interfaces, requisitos legais e recomendações podem mudar.

## Roteiro de execução

1. Selecione URLs, dispositivos e condições; registre a linha de base e dados reais separados dos testes de laboratório.
2. Investigue a causa das métricas ruins e priorize impacto antes de alterar recursos.
3. Otimize recursos críticos, imagens, fontes, scripts e cache conforme o diagnóstico.
4. Repita as medições em condições comparáveis e confirme se mudanças não prejudicaram experiência ou funcionalidades.

Referência: os limiares e métricas devem ser conferidos na documentação atual do web.dev; use dados de campo quando disponíveis.

## Performance

- [ ] PageSpeed testado em mobile e desktop.
- [ ] Quando houver dados de campo, conferir no percentil 75, separados por celular e desktop: LCP até 2,5 s, INP até 200 ms e CLS até 0,1. Sem dados de campo, registrar a lacuna e usar laboratório para diagnóstico, não como substituto de visitas reais.
- [ ] Imagens em WebP/AVIF quando possível.
- [ ] Carregamento tardio aplicado a recursos fora da tela quando útil; não atrasar a imagem principal candidata a LCP.
- [ ] CSS/JS desnecessário removido.
- [ ] Fontes otimizadas.
- [ ] Cache configurado.
- [ ] Compressão ativa.
- [ ] CDN ativa, se aplicável.
- [ ] Vídeos otimizados.
- [ ] Scripts de terceiros revisados.
- [ ] Site testado em conexão móvel.

---

Referência: [web.dev — Core Web Vitals](https://web.dev/articles/vitals).
