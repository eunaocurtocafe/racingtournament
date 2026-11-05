---
resumo: Objetivo, público e escopo do Racing Tournament
atualizado: 2026-11-05
---

# Visão do produto

## Problema

Um grupo de amigos corre junto no F1 25 e quer acompanhar quem está ganhando: pontos, campeonatos, histórico e melhores voltas. Hoje os resultados ficam espalhados em prints.

## Solução

Um app de celular (iOS e Android) que recebe uma **imagem da tela de resultado** de cada corrida (foto tirada com a câmera do celular ou print da galeria), extrai os dados (posições, pilotos, tempos, melhor volta) e mantém automaticamente:

- Pontuação por corrida e por campeonato
- Classificação de campeonatos com várias etapas
- Ranking geral de maiores vencedores
- Histórico de corridas e de cada piloto
- Melhores voltas (por pista, por carro, geral)

## Público

O grupo de amigos (hoje 4 pilotos), cada um com o app no próprio celular (iOS ou Android) e vendo os mesmos dados. O organizador cadastra corridas e campeonatos.

## Em aberto

- [x] **Simulador usado**: EA Sports F1 25 → [[simulador]]
- [x] Onde jogam o F1 25: cross-play, 2 no PC e 2 no console → [[simulador]]
- [x] **Plataforma do app**: celular, funcionando em **iOS e Android**
- [x] Stack do app → [[0003-stack-app-mobile]]
- [ ] Quem pode enviar prints: só o organizador ou todos os amigos?
- [ ] Sistema de pontuação → [[pontuacao]]

## Fora do escopo (por enquanto)

- Qualquer integração com o F1 25 (API, telemetria): a entrada é só imagem, por câmera ou galeria
- Corridas abertas ao público fora do grupo

Veja também: [[roadmap]], [[arquitetura]].
