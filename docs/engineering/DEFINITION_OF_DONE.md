# Definition of Ready e Definition of Done

> **Status:** em vigor · **Versão:** 1.0 · **Atualizado em:** 2026-11-01

Este documento define quando uma especificação está pronta para ser implementada e quando uma etapa, uma funcionalidade ou uma mudança simples está concluída. Uma tarefa só é declarada concluída quando **todos** os itens aplicáveis estiverem cumpridos e evidenciados.

## 1. Definition of Ready (spec pronta para implementação)

- [ ] Todas as seções do [template](../templates/feature-spec.md) estão preenchidas ou marcadas como "Não se aplica", com motivo.
- [ ] Toda regra `RN-xx` cita a sua fonte (`DP`, `RF` ou `RNF`).
- [ ] Todo critério de aceite `CA-xx` é verificável e está ligado a pelo menos uma `RN`.
- [ ] Nenhuma questão em aberto **bloqueante** na spec.
- [ ] Valores ainda não decididos estão modelados como configuração.
- [ ] Dependências (outras specs, ADRs, decisões) identificadas.
- [ ] Status **Aprovada**, definido pelo responsável pelo produto.

## 2. Done por etapa (`ET-xx`)

- [ ] O código implementa apenas o escopo da etapa.
- [ ] Os testes dos `CA` cobertos pela etapa foram escritos e passam.
- [ ] Typecheck, lint e build sem erros, sem supressões não aprovadas.
- [ ] Nenhum teste existente foi removido, desativado ou enfraquecido.
- [ ] Sem lógica duplicada nem dependência circular nova.
- [ ] Itens ★ do [checklist de review](CODE_REVIEW_CHECKLIST.md) conferidos.

## 3. Done por funcionalidade (spec)

- [ ] Todas as etapas do plano estão concluídas.
- [ ] **Todos os `CA` foram validados**, com evidência (teste automatizado ou verificação manual registrada no plano de testes).
- [ ] Checklist completo de code review registrado.
- [ ] Revisão de segurança registrada, quando houver gatilho ([security.md](../../.claude/rules/security.md#revisão-de-segurança-obrigatória)).
- [ ] Contratos públicos alterados documentados, com avaliação de impacto.
- [ ] ADRs necessários aceitos e referenciados no design.
- [ ] Custos operacionais novos medidos ou instrumentados (RNF-COST-01).
- [ ] Documentação atualizada: status da spec → Implementada, índices, `CLAUDE.md` (se houver comandos novos), docs de produto afetados.

## 4. Done no fluxo simplificado

- [ ] Os critérios do fluxo simplificado ([SDD_WORKFLOW §3](SDD_WORKFLOW.md#3-escolha-do-fluxo)) continuam valendo.
- [ ] A fonte do comportamento esperado foi identificada.
- [ ] Em correção de bug, existe um teste de regressão que falhava antes da correção.
- [ ] Testes afetados, typecheck e lint executados.
- [ ] Itens ★ do checklist de review conferidos.

## 5. Relatório final obrigatório

Toda tarefa termina com este relatório. Use `/verificar-entrega` para gerá-lo.

```markdown
## Resultado

**Fluxo:** completo | simplificado — motivo.
**Spec:** SPEC-NNN (status) | não se aplica — motivo.

### Arquivos
| Arquivo | Ação | Justificativa |
| --- | --- | --- |
| caminho | criado / alterado / removido | por quê |

### Validações executadas
| Comando | Resultado real |
| --- | --- |
| `comando` | resumo fiel da saída (ex.: 42 passed, 0 failed) |

### Validações não executadas
| Validação | Motivo | O que falta para executar |
| --- | --- | --- |

### Critérios de aceite
| CA | Status | Evidência |
| --- | --- | --- |
| CA-01 | ✅ validado / ❌ falhou / ⏳ não validado | teste ou verificação |

### Pendências e decisões necessárias
- ...
```

## 6. Regras de honestidade

- "Concluído" exige todos os `CA` validados. Se algum não foi validado, o status é "parcial", com a lista do que falta.
- Resultados de testes são copiados da execução real. Nunca estimados, resumidos de memória ou presumidos.
- Se uma validação não pôde ser executada (ambiente indisponível, dependência ausente, sem permissão), isso aparece na tabela "Validações não executadas".
