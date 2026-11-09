# Evidências verificadas em 09/11/2026

Aplicação: https://rodrigobolgheroni.github.io/atividadecicd/

Pull request integrado: https://github.com/RodrigoBolgheroni/atividadecicd/pull/1

| Experimento | Execução real | Resultado |
| --- | --- | --- |
| PR válido, commit 02830a7 | https://github.com/RodrigoBolgheroni/atividadecicd/actions/runs/42608790016 | CI aprovada; deploy ignorado |
| Erro proposital no PR, commit 6466a4e | https://github.com/RodrigoBolgheroni/atividadecicd/actions/runs/42608908034 | CI reprovada; deploy ignorado |
| Correção, commit 0f67a8f | https://github.com/RodrigoBolgheroni/atividadecicd/actions/runs/42609097990 | CI aprovada; deploy ignorado |
| Merge na main, commit 319f1c5 | https://github.com/RodrigoBolgheroni/atividadecicd/actions/runs/42609171319 | CI e deploy aprovados |
| Atualização visível, commit b93c2e1 | https://github.com/RodrigoBolgheroni/atividadecicd/actions/runs/42609419802 | CI e deploy aprovados; nova frase confirmada no site |

O erro proposital foi uma imagem sem alt dentro de head. O html-validate apontou 10 erros e encerrou com código 1. O trecho foi removido antes do merge. As capturas das execuções são páginas reais do GitHub; os JSONs de jobs vieram da API, e as capturas do site vieram do endereço público.

Verificações de navegador: Chrome em 1440, 768, 390 e 320 px; HTTP 200, imagens carregadas, âncoras válidas, ausência de rolagem horizontal, teclado e fontes alternativas. O modo de movimento reduzido foi ativado. Não foi feita auditoria completa com leitor de tela.

A frase de encerramento mudou de “Sua viagem começa com curiosidade.” para “Próxima parada: descobrir o Japão.”. A publicação inicial e a atualizada foram registradas separadamente.

Os arquivos de apoio estão em `evidencias/`. O relatório único em PDF é o entregável preparado para o formulário da atividade.
