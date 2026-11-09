PLEASE IMPLEMENT THIS PLAN:
# Site sobre o Japão com pipeline CI/CD e relatório do exercício

### Objetivo

Criar o site **Japão em três paradas**, armazená-lo no [repositório atividadecicd](https://github.com/RodrigoBolgheroni/atividadecicd) e automatizar sua validação e publicação no GitHub Pages. Documentar o uso da IA e reunir os resultados em um único PDF, conforme o exercício.

### 1. Desenvolver o site usando frontend-design

- Criar uma página em português para pessoas que querem conhecer o Japão, com abertura, destinos — Tóquio, Quioto e Osaka —, cultura e gastronomia. Usar textos curtos e informativos.
- Aplicar a skill **frontend-design** com uma identidade inspirada nos mapas ferroviários japoneses. O elemento principal será uma linha ilustrada que conecta os três destinos; os demais elementos terão composição simples.
- Usar azul `#164B73`, branco `#F7FAFC`, cinza `#D8E1E7`, verde `#1D8065` e coral `#E86658`. Combinar **Zen Kaku Gothic New** nos títulos e **Noto Sans** no corpo, com fontes alternativas do sistema.
- Implementar em HTML e CSS, com navegação por âncoras e ilustrações SVG locais. Incluir HTML semântico, contraste adequado, foco visível, textos alternativos e layout adaptável a celular e computador.
- Manter os arquivos publicáveis em `site/`, com caminhos relativos compatíveis com o endereço `/atividadecicd/`. Revisar o resultado visual em navegador antes de concluir.

### 2. Preparar o projeto e a CI

- Conferir novamente o conteúdo do repositório antes de trabalhar e preservar eventuais alterações existentes.
- Criar um README com descrição, execução local e endereço publicado.
- Adicionar **html-validate** como dependência de desenvolvimento, com arquivo de versões travadas e comando `npm run check`. O site continuará estático; Node.js será usado somente na validação.
- Criar `.github/workflows/ci-cd.yml` com gatilhos `push` na `main` e `pull_request` destinado à `main`.
- No job `ci`, executar checkout, configurar Node.js 24, instalar dependências com `npm ci` e executar `npm run check`. Qualquer erro deve encerrar o job com falha.

### 3. Configurar a publicação automática

- Habilitar GitHub Pages com **GitHub Actions** como origem.
- Criar o job `deploy` com dependência explícita de `ci` e condição que permita execução somente em push na `main`.
- Configurar Pages, empacotar apenas `site/` e publicar usando as actions oficiais. Associar o job ao ambiente `github-pages` e conceder as permissões `pages: write` e `id-token: write` necessárias, seguindo a [documentação oficial](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).
- Usar o endereço retornado pelo deploy no README e no relatório. O endereço esperado é `https://rodrigobolgheroni.github.io/atividadecicd/`.
- Justificar a escolha: GitHub Pages atende à aplicação estática e permite demonstrar o fluxo completo dentro do GitHub.

### 4. Validar e guardar evidências

- Executar a validação local e revisar o site em larguras de celular e computador, incluindo navegação por teclado, fontes, ilustrações e links internos.
- Abrir um pull request com alteração válida e registrar a CI aprovada, com o deploy ignorado.
- Introduzir temporariamente um erro de HTML nesse pull request, registrar a falha da CI e depois corrigi-lo. Não integrar o erro à `main`.
- Integrar a versão válida à `main` e registrar CI aprovada, deploy concluído e site acessível.
- Publicar uma pequena alteração visível para comprovar que a pipeline atualiza a aplicação automaticamente.

### 5. Documentar e entregar

- Registrar desde o início cada interação relevante com a IA: prompt, resultado, problema encontrado e alteração realizada. Preservar os prompts reais e identificar alterações manuais.
- Produzir um único PDF com link do repositório, URL do site, conteúdo final do workflow, prompts, histórico das alterações, total de prompts e breve análise do processo.
- Incluir capturas e links das execuções de CI/CD, além de imagens do site publicado. Relatar problemas reais, sem inventar falhas ou evidências.
- Salvar o relatório final na pasta de entregáveis e deixá-lo pronto para envio pelo formulário informado no enunciado.

**Premissas e limites:** o site será estático, sem backend, contas de usuário ou APIs. Será necessário acesso ao repositório para configurar Actions e Pages. O enunciado pede um projeto previamente desenvolvido; criar o site agora apresenta uma divergência que deverá ser registrada e confirmada com o professor.

Este plano ainda não executa a criação nem testa a pipeline; a comprovação dependerá das execuções reais no GitHub.
