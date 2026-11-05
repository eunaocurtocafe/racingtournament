---
resumo: Simulador usado (F1 25) e o formato dos prints de resultado
atualizado: 2026-11-05
---

# Simulador

## Simulador

**EA Sports F1 25** (informado pelo usuário em 2026-11-05).

- Plataforma: **cross-play**, 2 pilotos no PC e 2 no console (qual console: _a definir_)
- Consequências: os nomes no resultado podem vir em formatos diferentes (EA ID, Steam, PSN/Xbox); prints do console podem ser foto da TV tirada pelo celular, com reflexo e perspectiva, e não captura de tela limpa
- Modos usados (corrida online em lobby, liga, multiplayer local): _a definir_

## Tela de resultado

> **Preencher a partir de prints reais.** Não assuma o layout: confirme com as imagens.

A confirmar nos prints:

- Quais colunas aparecem (posição, piloto, equipe, tempo total ou gap, melhor volta, pit stops, penalidades, pontos)
- Como o nome do piloto aparece (gamertag / PSN / EA ID) → mapeamento para piloto em `pilotos`
- Como aparecem abandono (DNF), desclassificação (DSQ) e quem não largou
- Formato dos tempos (ex.: `1:32.456`) e idioma do jogo
- Se a melhor volta da corrida vem destacada
- Se o print é da corrida, da classificação (quali) ou de ambos

## Sem integração com o jogo

O app **não se integra ao F1 25** de nenhuma forma (nem telemetria, nem API). A única entrada é uma imagem da tela de resultado: foto tirada com a câmera do celular ou print salvo na galeria. Ver [[0003-stack-app-mobile]].

## Prints de exemplo

Guardar em `tests/fixtures/prints/` quando houver código de leitura.
