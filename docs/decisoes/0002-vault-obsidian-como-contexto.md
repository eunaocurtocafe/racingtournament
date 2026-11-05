---
resumo: A pasta docs/ é um vault do Obsidian que guarda o contexto do projeto para pessoas e para o Claude
data: 2026-11-05
status: Aceita
---

# 0002 — Vault do Obsidian como contexto

## Contexto

Queremos um sistema que dê contexto e direcione o raciocínio do Claude ao longo do projeto, fazendo-o ler só o necessário.

## Decisão

- `docs/` é um vault do Obsidian versionado no repositório.
- `CLAUDE.md` (lido automaticamente pelo Claude em toda sessão) é o mapa: lista cada nota com "abra quando…".
- Conhecimento (o quê e por quê) fica no vault; procedimentos (como fazer) ficam em skills em `.claude/`.
- Notas curtas, um assunto por nota, com `resumo` no frontmatter; pastas com `_indice.md`.
- O vault é atualizado na mesma tarefa e no mesmo commit da mudança que ele descreve.

## Alternativas consideradas

- **Vault fora do repositório**: não seria versionado junto com o código e ficaria fora de sincronia.
- **Um único documento grande**: obrigaria a ler tudo a cada tarefa.

## Consequências

O Obsidian é só o editor: nada depende de plugins. Consultas como Dataview não servem para guardar informação, porque o Claude as vê como texto cru. Configurações pessoais do Obsidian (`workspace`) ficam fora do Git.
