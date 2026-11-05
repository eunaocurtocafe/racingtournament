---
name: commit
description: Cria commits seguros neste repositório (racingtournament). Use sempre que for fazer commit, salvar alterações no Git, preparar um push ou quando o usuário pedir "commita", "salva no git", "manda pro GitHub". Revisa o que entra, bloqueia segredos e arquivos indevidos, escreve mensagem padronizada e confere o resultado para que nada se perca.
---

# Commit seguro

Objetivo: todo commit sai revisado, com mensagem padronizada, e **nenhuma alteração do usuário é perdida ou sobrescrita**.

## Regras que nunca podem ser quebradas

- Nunca use `git reset --hard`, `git checkout -- <arquivo>`, `git restore` sem `--staged`, `git clean -f`, `git stash drop`/`clear` ou `git push --force` sem pedido explícito do usuário **para aquela ação**. Se parecer necessário, pare e pergunte.
- Nunca use `--no-verify` nem pule hooks. Se um hook falhar, corrija a causa e crie um **novo** commit (não use `--amend` depois de um hook falhar: o commit não foi criado e o amend alteraria o anterior).
- Não use `git commit --amend` em commit que já foi enviado ao GitHub.
- Não use `git add -A` / `git add .` às cegas: adicione arquivos pelo nome depois de revisá-los.
- Não faça push a menos que o usuário tenha pedido.
- Se a branch atual for `main` e a mudança for grande ou arriscada, sugira criar uma branch antes (`git switch -c <tipo>/<descricao-curta>`).

## Passo a passo

1. **Levantar o estado** (rodar juntos):
   - `git status --short --branch`
   - `git diff` e `git diff --staged`
   - `git log --oneline -5` (para seguir o estilo de mensagens existente)
   - `git stash list` (para não esquecer trabalho guardado)

2. **Revisar o que vai entrar.** Bloqueie e avise o usuário se encontrar:
   - Segredos: `.env`, chaves de API, tokens, senhas, `*.pem`, `credentials*.json`, strings como `sk-`, `ghp_`, `AKIA`, `password=`.
   - Arquivos gerados ou pesados: `node_modules/`, `dist/`, `build/`, `.venv/`, `__pycache__/`, bancos locais (`*.db`, `*.sqlite`), arquivos acima de ~10 MB. Sugira incluí-los no `.gitignore`.
   - Prints de corrida (imagens de teste): só entram se forem fixtures intencionais (ex.: `tests/fixtures/`). Pergunte em caso de dúvida.
   - Mudanças que não têm relação com a tarefa: deixe de fora e mencione ao usuário.

3. **Separar em commits lógicos.** Uma mudança coerente por commit. Se o diff mistura assuntos (ex.: correção de bug + nova feature), faça commits separados.

4. **Adicionar pelo nome:** `git add caminho/arquivo1 caminho/arquivo2`. Depois confira com `git diff --staged --stat`.

5. **Escrever a mensagem** no padrão Conventional Commits, em português:

   ```
   <tipo>(<escopo opcional>): <resumo no imperativo, até ~72 caracteres>

   <corpo opcional: o porquê da mudança, não o como>

   Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>
   ```

   Tipos: `feat` (funcionalidade), `fix` (correção), `refactor`, `docs`, `test`, `chore` (manutenção, configs), `style`, `perf`, `build`, `ci`.
   Escopos sugeridos para este projeto: `ocr` (leitura de prints), `pontuacao`, `campeonato`, `pilotos`, `historico`, `ui`, `api`, `db`.

   Exemplos:
   - `feat(ocr): ler posições e tempos do print de resultado`
   - `fix(pontuacao): não pontuar piloto que abandonou`

   Use um heredoc para passar a mensagem (Bash):
   ```bash
   git commit -F - <<'EOF'
   feat(campeonato): permitir criar campeonato com várias etapas

   Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>
   EOF
   ```

6. **Conferir o resultado:** `git status --short --branch` e `git log --oneline -3`. Confirme que não ficou nada não commitado sem querer e que o commit tem os arquivos certos (`git show --stat HEAD`).

## Quando o usuário pedir push

1. `git fetch origin`
2. Compare: `git status -sb` (mostra `ahead`/`behind`).
   - Só `ahead`: `git push` (na primeira vez de uma branch: `git push -u origin <branch>`).
   - `behind` ou divergente: **não force.** Rode `git pull --rebase origin <branch>`. Se houver conflito, mostre os arquivos em conflito ao usuário, resolva preservando as duas versões quando fizer sentido, e só continue (`git rebase --continue`) com o conteúdo conferido. Na dúvida, `git rebase --abort` e pergunte.
3. Push recusado: leia a mensagem de erro e explique ao usuário. Nunca tente `--force` como solução.
4. Depois do push, confirme com `git status -sb` que a branch está sincronizada com `origin`.

## Ao terminar

Diga ao usuário, em uma ou duas linhas: quais commits foram criados (hash curto + mensagem), o que ficou de fora e por quê, e se houve push ou não.
