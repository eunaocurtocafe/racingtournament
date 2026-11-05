# Racing Tournament

App que recebe prints de resultados de corridas que um grupo de amigos faz em um simulador e organiza pontuação, campeonatos, maiores vencedores, histórico e melhores voltas.

Repositório: https://github.com/eunaocurtocafe/racingtournament (branch `main`). Idioma do projeto: português.

## Como usar este arquivo

Este é o **mapa** do projeto. Não leia o vault inteiro: pela descrição abaixo, abra só as notas que a tarefa pede. As notas ficam em `docs/` (vault do Obsidian) e se ligam por `[[links]]`: um `[[nome]]` aponta para `docs/**/nome.md`.

## Mapa do vault (`docs/`)

| Nota | Abra quando |
|---|---|
| [visao](docs/visao.md) | Precisar do objetivo, do público, do escopo ou do que está fora do escopo |
| [arquitetura](docs/arquitetura.md) | For escrever código: stack, módulos, onde fica cada coisa |
| [roadmap](docs/roadmap.md) | For escolher a próxima tarefa ou checar o que já está pronto |
| [dominio/_indice](docs/dominio/_indice.md) | Mexer em regras do negócio: pontuação, campeonatos, pilotos, simulador, formato dos prints |
| [decisoes/_indice](docs/decisoes/_indice.md) | Antes de mudar algo já decidido, ou para entender por que algo é como é |

## Harness (`.claude/`)

- Skill `commit`: use para qualquer commit ou push.
- Agente `github-specialist`: operações Git/GitHub maiores (branches, conflitos, rebase, recuperação de trabalho).

## Regras de trabalho

- **Mantenha o vault atualizado na mesma tarefa** que muda o projeto, e inclua as notas no mesmo commit:
  - Decisão tomada (stack, regra, formato): crie uma nota em `docs/decisoes/` a partir de `_modelo.md` e adicione ao índice.
  - Feature concluída ou iniciada: atualize `docs/roadmap.md`.
  - Regra de negócio definida: registre em `docs/dominio/`.
  - Nota nova: adicione ao índice da pasta e, se for de primeiro nível, a este mapa.
- Notas curtas, um assunto por nota. Se uma nota passar de ~150 linhas, divida.
- Não use consultas de plugins do Obsidian (Dataview etc.) para guardar informação: escreva o conteúdo em texto.
- Se uma nota contradiz o código, o código é a verdade: corrija a nota e avise o usuário.
- Não invente regras de negócio (pontuação, critérios de desempate etc.): pergunte ao usuário e registre a resposta.
