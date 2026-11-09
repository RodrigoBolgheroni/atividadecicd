# Japão em três paradas

Guia ilustrado de Tóquio, Quioto e Osaka em português. HTML e CSS estáticos, SVGs originais e identidade inspirada nos mapas ferroviários japoneses.

**Site:** https://rodrigobolgheroni.github.io/atividadecicd/

## Abrir localmente

Abra `site/index.html` no navegador ou execute `python -m http.server 8000 --directory site` e acesse http://localhost:8000.

## Validar

Use Node.js 24 (>=24.8):

```sh
npm ci
npm run check
```

O html-validate verifica estrutura e regras de HTML. Não substitui a revisão visual, o teste de links e a avaliação de acessibilidade no navegador.

## CI/CD

O workflow `.github/workflows/ci-cd.yml` valida em push na `main` e pull requests destinados à `main`. O deploy depende da CI e publica apenas em push na `main`. Somente `site/` é enviado ao GitHub Pages. Em Settings > Pages, a origem deve ser GitHub Actions.

GitHub Pages atende ao projeto porque ele não precisa de servidor, banco de dados ou segredos externos. A publicação usa o token temporário do Actions, com permissões de escrita restritas ao job de deploy.

As fontes Google são opcionais: o layout tem fontes alternativas locais. Os SVGs fazem parte do projeto; o mapa é esquemático e não representa distâncias reais. As referências de conteúdo estão nos links da JNTO no site.

## Registro do laboratório

O registro de uso da IA e as evidências estão em `docs/`. A entrega reúne tudo em um PDF separado dos arquivos públicos do site. O projeto foi criado durante a atividade; o enunciado solicita projeto previamente desenvolvido, e essa diferença deve ser confirmada com o professor.
