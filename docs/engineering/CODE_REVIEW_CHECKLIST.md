# Checklist de Code Review

> **Status:** em vigor · **Versão:** 1.0 · **Atualizado em:** 2026-11-01

Checklist canônico para revisar qualquer mudança. Os registros de review ([template](../templates/code-review.md)) referenciam os itens pelo ID `CR-xx`.

Os itens marcados com **★** são obrigatórios também no fluxo simplificado.

## Rastreabilidade

- **CR-01 ★** A mudança está ligada a uma spec (`SPEC-NNN`) ou, no fluxo simplificado, à fonte do comportamento esperado.
- **CR-02** Toda regra de negócio no código corresponde a uma `RN` da spec, e nenhuma regra foi inventada.
- **CR-03** Os critérios de aceite cobertos pela mudança estão identificados.

## Regras de negócio e produto

- **CR-04 ★** Nenhuma invariante crítica foi violada ([product-requirements.md](../../.claude/rules/product-requirements.md#invariantes-críticas)).
- **CR-05** Valores comerciais e limites vêm de configuração, não de constantes (DP-024).
- **CR-06** Nenhuma funcionalidade futura ou fora do escopo da spec foi incluída.

## Arquitetura

- **CR-07 ★** O domínio não importa framework, ORM, SDK nem infraestrutura.
- **CR-08 ★** Sem dependências circulares novas.
- **CR-09 ★** Sem lógica duplicada; o código existente foi reutilizado ou extraído.
- **CR-10** Contratos públicos alterados têm avaliação de impacto e, se incompatíveis, plano de migração.
- **CR-11** Decisões arquiteturais novas têm ADR.
- **CR-12** Toda nova dependência tem justificativa (necessidade, alternativas, licença, tamanho, privacidade).

## Código

- **CR-13 ★** Typecheck, lint e build passam, sem `@ts-ignore`, `eslint-disable` ou `any` não justificados e aprovados.
- **CR-14** Nomes revelam intenção; funções pequenas; comentários explicam o porquê.
- **CR-15** Erros são tratados explicitamente, sem exceções engolidas.
- **CR-16** Dinheiro em centavos inteiros; datas em UTC.

## Testes

- **CR-17 ★** Nenhum teste foi removido, desativado ou enfraquecido.
- **CR-18** Cada `CA` coberto tem teste nomeado com `SPEC-NNN CA-xx`.
- **CR-19** Correções de bug têm teste de regressão.
- **CR-20** Os testes são determinísticos e não chamam provedores reais.
- **CR-21 ★** Os resultados de teste reportados vêm de execução real.

## Segurança e privacidade

- **CR-22 ★** Nenhum segredo no código, nos testes, nos logs ou no app.
- **CR-23 ★** Nenhum dado de criança além de apelido e faixa etária; o nome não vai ao provedor de IA.
- **CR-24** Toda leitura ou escrita de recurso verifica se ele pertence à conta autenticada.
- **CR-25** Entradas validadas na borda.
- **CR-26** Operações com efeito (compras, créditos, criação) são idempotentes.
- **CR-27** Logs sem dados pessoais nem conteúdo de histórias.
- **CR-28** Revisão de segurança registrada, quando há gatilho.

## Custo e desempenho

- **CR-29** Chamadas a provedores pagos são medidas e atribuídas (RNF-COST-01) e têm teto de retentativas.
- **CR-30** Sem consultas N+1 ou carregamento desnecessário em listas e no leitor.

## Interface e criança (mobile)

- **CR-31** Áreas adultas atrás da barreira parental; leitor sem elementos comerciais.
- **CR-32** Textos externalizados; acessibilidade (contraste, área de toque, TalkBack nas telas adultas).
- **CR-33** SDKs novos compatíveis com a política de Famílias (DP-051).

## Documentação

- **CR-34 ★** A documentação afetada foi atualizada (spec, índices, `CLAUDE.md`).
- **CR-35** Arquivos criados e alterados foram informados com justificativa.
