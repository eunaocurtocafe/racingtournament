---
resumo: Commits e operações Git seguem regras que evitam perda de trabalho
data: 2026-11-05
status: Aceita
---

# 0001 — Fluxo Git seguro

## Contexto

O usuário quer que os commits saiam sempre padronizados e que nenhuma informação se perca no Git.

## Decisão

- Skill `.claude/skills/commit`: revisão do diff, bloqueio de segredos e arquivos gerados, arquivos adicionados pelo nome, Conventional Commits em português, push só quando pedido e sem `--force`.
- Agente `.claude/agents/github-specialist`: operações maiores (branches, conflitos, rebase), sempre com backup (stash ou branch `backup/...`) antes de mexer no histórico.

## Alternativas consideradas

- **Só instruções no CLAUDE.md**: menos detalhado e sem um agente dedicado para operações arriscadas.

## Consequências

Commits mais lentos (há revisão), mas previsíveis. O `gh` CLI foi instalado em 2026-11-05 e é usado para PRs, issues e releases.
