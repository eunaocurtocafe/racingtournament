---
resumo: Stack, fluxo de envio de prints, módulos e organização do código
atualizado: 2026-11-05
---

# Arquitetura

Decisão completa e alternativas em [[0003-stack-app-mobile]].

## Stack

- **App:** React Native + Expo (TypeScript), iOS e Android
- **Backend:** Supabase (Postgres, Auth, Storage, Edge Functions)
- **Leitura dos prints:** Claude (visão) chamado por uma Edge Function
- **Entrada de dados:** só imagem, pela câmera do celular ou pela galeria. Sem integração com o F1 25.

## Fluxo de envio de uma corrida

1. Usuário toca em "Nova corrida" e escolhe **Tirar foto** (câmera) ou **Escolher da galeria**.
2. App envia a imagem para o Supabase Storage.
3. Edge Function manda a imagem ao Claude e recebe o resultado em JSON (posição, nome, tempo/gap, melhor volta, status DNF/DSQ).
4. Nomes do jogo são mapeados para pilotos cadastrados pelos apelidos; nome desconhecido → app pergunta quem é.
5. **Tela de revisão:** usuário confere e corrige tudo.
6. Ao confirmar, a corrida é salva e a pontuação ([[pontuacao]]) é calculada.

Regra: a chave da API do Claude fica só no backend. Nunca no código do app.

## Módulos

| Módulo | Responsabilidade |
|---|---|
| Captura | Câmera e galeria, envio da imagem |
| Leitura de prints | Edge Function que extrai os resultados da imagem |
| Pilotos | Cadastro e apelidos por plataforma (EA ID, Steam, PSN/Xbox) |
| Corridas | Registrar cada corrida com seus resultados e a imagem original |
| Pontuação | Aplicar as regras de [[pontuacao]] |
| Campeonatos | Etapas, classificação, desempates |
| Estatísticas | Ranking geral, histórico, melhores voltas |

## Estrutura de pastas

_Preencher quando o código existir._
