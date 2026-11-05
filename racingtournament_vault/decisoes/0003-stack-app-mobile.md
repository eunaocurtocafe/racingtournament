---
resumo: App em React Native + Expo, dados no Supabase e leitura de prints por IA com visão (Claude) via backend
data: 2026-11-05
status: Aceita
---

# 0003 — Stack do app mobile

## Contexto

- O app precisa rodar em **iOS e Android** (4 pilotos, cada um no próprio celular).
- Todos precisam ver os mesmos dados (classificação, histórico).
- A única entrada de resultados é **uma imagem**: foto da tela tirada com a câmera do celular ou print da galeria. **Não haverá integração nenhuma com o simulador** (nem telemetria, nem API).
- O grupo joga em cross-play (PC + console), então muitas imagens serão fotos de TV/monitor, com reflexo, ângulo e moiré.

## Decisão

- **App:** React Native com **Expo** (TypeScript). Um código só para iOS e Android; testes no celular via Expo Go.
- **Backend e dados:** **Supabase** (Postgres, autenticação, storage para as imagens, Edge Functions).
- **Leitura dos prints:** modelo de visão do **Claude** (API da Anthropic), que recebe a imagem e devolve os resultados em JSON estruturado.
  - A chamada à API é feita **no backend** (Supabase Edge Function), nunca no app: a chave da API não pode ir dentro do aplicativo.
- **Revisão humana:** antes de salvar, o app mostra o resultado lido para quem enviou conferir e corrigir. Só depois disso a corrida conta pontos.

## Alternativas consideradas

- **Flutter**: também atende iOS e Android; preterido pelo ecossistema JS/TS maior e pelo Expo facilitar teste e distribuição.
- **PWA (site instalável)**: evita a conta Apple, mas com integração pior com câmera/galeria. Fica como plano B se o custo da Apple pesar.
- **OCR tradicional (ex.: ML Kit no aparelho)**: gratuito, mas frágil com fotos de TV e não entende a estrutura da tabela.
- **Telemetria UDP do F1 25**: dados exatos, mas é integração com o simulador, que está fora do escopo por decisão do usuário.
- **Firebase**: equivalente ao Supabase; Supabase escolhido pelo banco relacional (corridas, campeonatos e pontuação são dados bem relacionais).

## Consequências

- Custo: API do Claude por imagem (centavos); Supabase no plano gratuito; conta Apple Developer (US$ 99/ano) para distribuir no iPhone fora do Expo Go.
- Precisamos de prints/fotos reais do F1 25 para calibrar a leitura e montar testes.
- O cadastro de pilotos precisa de apelidos por plataforma (EA ID, Steam, PSN/Xbox).
