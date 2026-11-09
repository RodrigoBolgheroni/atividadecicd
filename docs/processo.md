# Registro do processo e do uso da IA

Data da atividade: 09/11/2026. Ferramenta: Codex, com IA generativa. Autor do repositório: Rodrigo Bolgheroni.

## Critério de contagem

Foram contabilizadas **6 mensagens humanas relevantes**: cinco solicitações e uma resposta com o repositório. O envio inicial do anexo sem pedido, os metadados da interface e a definição da skill não são prompts adicionais. Com a resposta de contexto excluída, são **5 solicitações**. Os comandos e ajustes autônomos do agente não são apresentados como novos prompts humanos.

## Interações reais

### 1. Planejamento inicial

Prompt: “Faça um plano de fazer o exercicio do pdf”

Resultado: leitura das três páginas do PDF e identificação dos requisitos de CI, CD, uso de IA, evidências e relatório único. Foi solicitado o projeto a utilizar.

### 2. Identificação do repositório

Resposta de contexto: “[https://github.com/RodrigoBolgheroni/atividadecicd.git](https://github.com/RodrigoBolgheroni/atividadecicd.git)”

Resultado: o repositório foi consultado e estava vazio. Problema: o enunciado pede um projeto já desenvolvido. A divergência foi informada ao usuário.

### 3. Esclarecimento dos pré-requisitos

Prompt: “Não entendi, o que preciso ter antes de começar o exercicio”

Resultado: explicação da necessidade de aplicação, repositório, acesso ao Actions e hospedagem. Nenhuma aplicação foi alterada nessa etapa.

### 4. Definição do site

Prompt: “continua o plano, e inclui o site que vai ser criado nele, cria um site sobre o japão usando [$frontend-design](C:\Users\rodrigob-ieg\\.agents\skills\frontend-design\SKILL.md) no plano”

Resultado: definição de um site estático sobre Japão e publicação no GitHub Pages. A skill frontend-design foi fornecida como referência. Direção escolhida: rota ferroviária ilustrada, Tóquio, Quioto e Osaka, com HTML, CSS e SVGs locais.

### 5. Consolidação

Prompt: “cria o plano”

Resultado: plano completo de criação do site, CI, publicação, falha controlada em PR, correção, atualização publicada e relatório.

### 6. Implementação

Prompt: “PLEASE IMPLEMENT THIS PLAN:” seguido do plano aprovado, preservado integralmente em `prompt-implementacao.md`.

Resultado: implementação e validação conduzidas pelo agente, com uso de ferramentas reais. O histórico de commits e as evidências documentam o que aconteceu; não foram criados prompts fictícios para cada correção.

## Evolução e problemas reais

- O conector GitHub permitiu consultar metadados, mas recusou gravação de arquivo e criação de PR com HTTP 403. Foi usado o Git HTTPS já autenticado e, para operações não cobertas, a API com a credencial local, sem expor seu valor.
- O Node.js padrão era 22.19, abaixo do requisito do html-validate atual. A instalação inicial mostrou aviso de compatibilidade. A validação e reinstalação foram repetidas explicitamente com o Node.js 24 do runtime disponível, alinhado à CI.
- A configuração inicial do validador continha `void-style: omitted`, opção inválida. A regra redundante foi removida; manteve-se o conjunto recomendado.
- A validação detectou dois `aria-label` em elementos genéricos que não podiam recebê-los. Os rótulos foram removidos preservando o conteúdo visível.
- O primeiro teste de imagens no navegador não esperava o carregamento de imagens com lazy loading. O teste foi ajustado para rolar até cada imagem e aguardar sua decodificação; isso foi uma correção no teste, não uma falha do site.
- Depois da primeira CI válida no PR, foi inserida deliberadamente uma imagem sem texto alternativo dentro de `head`. Esse erro foi um experimento controlado para demonstrar a falha da CI, e não um defeito descoberto em produção. A CI apontou 10 erros e falhou; a alteração foi removida e a nova CI passou antes do merge.

## Alterações manuais

Não houve edição manual do código pelo usuário durante a implementação observada. As alterações de código, configuração, testes e documentação foram feitas pelo agente. O usuário definiu o tema, informou o repositório, forneceu a skill e aprovou o plano. Não se atribuem ao usuário correções feitas automaticamente.

## Estratégia de publicação

GitHub Pages foi escolhido porque a aplicação é estática e não exige backend ou banco de dados. O workflow executa CI em push na main e em pull_request destinado à main. O job de deploy exige sucesso da CI e evento push na main; somente `site/` é empacotado. O token temporário do Actions dispensa segredos de serviços externos.

## Limites

O projeto foi criado durante esta atividade, embora o enunciado peça projeto previamente desenvolvido. A aceitação dessa diferença depende do professor. Os testes de teclado e HTML são verificações parciais de acessibilidade; não equivalem a uma auditoria completa com leitores de tela. O envio do relatório no formulário cabe ao aluno.

## Fontes

- Enunciado fornecido: Lab CICD-Pipeline.pdf, três páginas.
- GitHub Pages: https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages
- Conteúdo introdutório: páginas oficiais da JNTO sobre Tóquio, Quioto e Osaka, ligadas no site.
