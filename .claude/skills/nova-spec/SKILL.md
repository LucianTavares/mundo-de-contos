---
name: nova-spec
description: Cria ou atualiza uma especificação de funcionalidade (SPEC-NNN) do Mundo de Contos seguindo o fluxo SDD. Use ao iniciar uma funcionalidade nova, quando um requisito de uma spec existente mudar, ou quando o usuário pedir uma especificação.
argument-hint: "[título da funcionalidade | SPEC-NNN para atualizar]"
---

# Nova especificação (ou atualização)

Siga os passos 1 a 5 de [docs/engineering/SDD_WORKFLOW.md](../../../docs/engineering/SDD_WORKFLOW.md). Argumento recebido: `$ARGUMENTS`.

## Atualizar uma spec existente (argumento `SPEC-NNN`)

1. Leia a spec e o índice [docs/specs/README.md](../../../docs/specs/README.md).
2. Aplique a mudança e registre-a no histórico de alterações (data, versão, o que mudou, motivo e fonte `DP`).
3. Se a spec estava Aprovada, Em implementação ou Implementada, volte o status para **Em revisão** e avise o usuário.
4. Atualize a data no índice.

## Criar uma spec nova

1. **Numeração:** leia o índice; o próximo número é o maior `SPEC-NNN` existente + 1, com três dígitos. Slug em kebab-case, sem acentos.
2. **Estrutura:** crie `docs/specs/SPEC-NNN-slug/spec.md` a partir de [docs/templates/feature-spec.md](../../../docs/templates/feature-spec.md), mantendo todas as seções. `design.md`, `plan.md` e `test-plan.md` são criados nos passos 6 e 7 do fluxo.
3. **Fontes:** leia as fontes de verdade listadas no `CLAUDE.md`, as jornadas e os requisitos relacionados, e as specs vizinhas. Procure código existente relacionado.
4. **Regras de negócio:** cada `RN-xx` cita a sua fonte (`DP`, `RF` ou `RNF`). Itens `[Proposta]`, `[Hipótese]`, `[Aberto]` e recomendações de `OPEN_QUESTIONS.md` **não** viram regra: vão para a seção "Questões em aberto".
5. **Valores não decididos** viram parâmetros configuráveis com "a definir" e a `QA` correspondente.
6. **Critérios de aceite:** `CA-xx` no formato Dado/Quando/Então, cada um citando as `RN` que valida.
7. **Escopo:** se a funcionalidade depender de outra ainda não especificada (por exemplo, créditos), proponha dividi-la em specs com dependência explícita.
8. **Índice:** adicione a linha no índice com status **Rascunho**.

## Ao terminar

- Coloque a spec em **Em revisão**.
- Apresente ao usuário: objetivo, regras com fonte, critérios de aceite e as questões em aberto, destacando as que **bloqueiam a aprovação**, cada uma com opções e recomendação.
- Peça a aprovação explicitamente. **Nunca** marque a spec como Aprovada por conta própria.
