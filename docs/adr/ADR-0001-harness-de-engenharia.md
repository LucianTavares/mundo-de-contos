# ADR-0001 — Harness de engenharia para desenvolvimento assistido por agentes

| Campo | Valor |
| --- | --- |
| Status | Aceito |
| Data | 2026-11-01 |
| Decisores | Responsável pelo produto (aceite em 2026-11-01) |
| Decisões de produto relacionadas | DP-008 (Harness Engineering + SDD), DP-009 |
| Substitui | — |

## Contexto

O Mundo de Contos será desenvolvido em grande parte com o Claude Code. Sem estrutura, um agente tende a inventar regras de negócio, perder decisões já tomadas, declarar tarefas concluídas sem validação e consumir contexto com documentação irrelevante para a tarefa.

A [DP-008](../product/PRODUCT_DECISIONS.md#plataforma-e-engenharia) define que nenhuma funcionalidade é implementada antes da aprovação de sua especificação. A versão instalada do Claude Code (2.1.314) oferece: `CLAUDE.md`; regras modulares em `.claude/rules/`, com carregamento condicional por caminho (campo `paths`); e skills em `.claude/skills/`, que podem ser invocadas pelo usuário ou pelo modelo, ou restritas ao usuário (`disable-model-invocation`).

## Decisão

1. **`CLAUDE.md` como índice curto:** fontes de verdade em ordem de precedência, mapa das regras, skills e documentos. Nenhum conteúdo extenso dentro dele.
2. **Regras em `.claude/rules/`, divididas por assunto:**
   - sempre carregadas: `general-engineering`, `product-requirements`, `architecture`, `security`;
   - carregadas por caminho: `backend` (`apps/api/**`), `mobile` (`apps/mobile/**`), `testing` (`apps/**`, `packages/**`), `documentation` (`docs/**`, `**/*.md`).
3. **Skills apenas para fluxos repetíveis:** `nova-spec`, `novo-adr`, `registrar-decisao` (só por pedido do usuário) e `verificar-entrega`.
4. **Sem `.claude/commands/`:** na versão instalada, skills cobrem o mesmo uso que comandos e, além disso, podem ser acionadas pelo modelo e ter arquivos de apoio. Manter os dois mecanismos duplicaria o fluxo.
5. **Fluxo SDD documentado** em [SDD_WORKFLOW.md](../engineering/SDD_WORKFLOW.md), com dois portões (spec aprovada; ADRs aceitos), fluxo simplificado com critérios explícitos e rastreabilidade `DP/RF → SPEC → RN → CA → ET → teste → commit`.
6. **Artefatos versionados no repositório:** `docs/specs/SPEC-NNN-slug/`, `docs/adr/`, `docs/templates/`.
7. **Caminhos provisórios:** `apps/api`, `apps/mobile` e `packages/` são suposições até o ADR de estrutura do monorepo, que deve ajustar o campo `paths` das regras.

## Alternativas consideradas

| Alternativa | Prós | Contras | Motivo da rejeição |
| --- | --- | --- | --- |
| Um único `CLAUDE.md` com todas as regras | Simples | Todo o conteúdo carregado em toda sessão; difícil de manter; mistura assuntos | Custo de contexto e de manutenção |
| `.claude/commands/` em vez de skills | Formato conhecido | Sem invocação pelo modelo nem arquivos de apoio | Skills cobrem o mesmo uso com mais recursos |
| Hooks automáticos (typecheck/lint após edição) já agora | Validação contínua automática | Ainda não há código nem comandos de build | Adiado para quando o monorepo existir |
| Especificações fora do repositório (wiki, ferramenta externa) | Edição colaborativa | O agente perde acesso confiável; versões se desencontram do código | A documentação é parte do produto |

## Consequências

- **Positivas:** contexto previsível e enxuto; regras específicas carregadas só quando relevantes; rastreabilidade de ponta a ponta; decisões não se perdem.
- **Negativas e custos:** mais documentos para manter; aprovações explícitas do responsável tornam-se um passo obrigatório.
- **O que passa a ser obrigatório:** declarar o fluxo no início de cada tarefa; relatório final no formato da [Definition of Done](../engineering/DEFINITION_OF_DONE.md); spec aprovada antes de código de produto.
- **Impacto em segurança, privacidade e custo:** as regras tornam explícitas as invariantes de privacidade infantil e de custo; não há custo operacional novo.
- **Impacto na futura versão iOS:** nenhum.

## Validação

Revisar este ADR quando o monorepo for criado (ajuste de `paths`, avaliação de hooks e permissões) e depois das três primeiras specs implementadas, verificando se os portões e o fluxo simplificado estão funcionando sem burocracia excessiva.

## Referências

- [CLAUDE.md](../../CLAUDE.md)
- [SDD_WORKFLOW.md](../engineering/SDD_WORKFLOW.md)
