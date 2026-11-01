---
paths:
  - "apps/mobile/**"
---

# Mobile

> Caminho provisório até o ADR de estrutura do monorepo. Direção tecnológica: React Native + Expo + TypeScript (DP-010); detalhes em ADR.

## Princípios

- O app exibe estado e coleta intenções; **quem decide é o servidor**. Direitos de acesso, saldo de créditos, limites e preços vêm do backend ou da loja (RNF-PORT-01, DP-024).
- Nenhum segredo no app (DP-036).
- Compatibilidade com iOS: evite APIs exclusivas de Android fora de adaptadores isolados.

## Segurança infantil na interface

- Compras, assinatura, configurações, perfis e conta ficam atrás da barreira parental (DP-035, DP-048).
- O leitor não exibe ofertas, preços, botões de compra nem atalhos para áreas adultas (RF-LEI-04).
- Sem autoplay, contadores de sequência, notificações insistentes ou outros mecanismos para prender a criança na tela (DP-005).
- Nenhum anúncio e nenhum SDK de publicidade (DP-012).

## Dependências nativas e SDKs

- Prefira módulos do Expo SDK. Um módulo nativo novo exige justificativa (regra 4 de [general-engineering.md](general-engineering.md)).
- SDKs de terceiros (analytics, crash, login) só se forem compatíveis com a política de Famílias da Google Play, sem coletar identificadores de publicidade (DP-051).

## Compras

- O fluxo usa o Google Play Billing. O app envia o comprovante ao servidor e só libera conteúdo após a confirmação dele (RF-MON-08).
- Trate os estados pendente, cancelado, recusado e já usado de forma explícita.

## Interface e acessibilidade

- Todos os textos de interface ficam externalizados, nunca fixos no componente (RNF-I18N-01).
- Contraste e tamanho de texto adequados à leitura em voz alta; área de toque adequada (RNF-ACC-01).
- Telas adultas compatíveis com o TalkBack (RNF-ACC-02).
- Pré-carregue a próxima página do leitor (RNF-PERF-01).

## Estado e dados locais

- Não armazene dados da criança além do necessário para exibição. Cache local apenas do conteúdo já acessado.
- Tokens de sessão em armazenamento seguro do sistema, nunca em armazenamento comum.
