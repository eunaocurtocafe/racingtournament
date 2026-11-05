---
resumo: Objetivo, público e escopo do Racing Tournament
atualizado: 2026-11-05
---

# Visão do produto

## Problema

Um grupo de amigos corre junto em um simulador e quer acompanhar quem está ganhando: pontos, campeonatos, histórico e melhores voltas. Hoje os resultados ficam espalhados em prints.

## Solução

Um app que recebe os **prints da tela de resultado** de cada corrida, extrai os dados (posições, pilotos, tempos, melhor volta) e mantém automaticamente:

- Pontuação por corrida e por campeonato
- Classificação de campeonatos com várias etapas
- Ranking geral de maiores vencedores
- Histórico de corridas e de cada piloto
- Melhores voltas (por pista, por carro, geral)

## Público

O grupo de amigos (poucos usuários). O organizador cadastra corridas e campeonatos.

## Em aberto

- [ ] **Simulador usado** (iRacing, Assetto Corsa, ACC, F1, Gran Turismo…): define como ler os prints → registrar em [[simulador]]
- [ ] **Plataforma**: site no navegador, app de celular ou só no computador → registrar em [[decisoes/_indice|decisões]]
- [ ] Quem pode enviar prints: só o organizador ou todos os amigos?
- [ ] Sistema de pontuação → [[pontuacao]]

## Fora do escopo (por enquanto)

- Integração direta com a API ou telemetria do simulador (a entrada são prints)
- Corridas abertas ao público fora do grupo

Veja também: [[roadmap]], [[arquitetura]].
