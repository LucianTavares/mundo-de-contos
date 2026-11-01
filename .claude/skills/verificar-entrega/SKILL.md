---
name: verificar-entrega
description: Confere a Definition of Done de uma tarefa do Mundo de Contos e gera o relatório final com arquivos alterados, validações realmente executadas e status de cada critério de aceite. Use antes de declarar qualquer tarefa, etapa ou spec como concluída.
argument-hint: "[SPEC-NNN | SPEC-NNN ET-xx | descrição da mudança]"
---

# Verificar entrega

Escopo: `$ARGUMENTS`. Referência: [docs/engineering/DEFINITION_OF_DONE.md](../../../docs/engineering/DEFINITION_OF_DONE.md).

## Passos

1. **Fluxo e escopo:** identifique se a tarefa usou o fluxo completo ou o simplificado e qual seção da Definition of Done se aplica (etapa, funcionalidade ou fluxo simplificado). No simplificado, confirme que os critérios continuam valendo.
2. **Arquivos:** liste os arquivos criados, alterados e removidos. Use `git status` e `git diff --stat` se o diretório for um repositório git; caso contrário, use o registro da própria sessão e diga que não há git. Justifique cada arquivo.
3. **Validações:** execute os comandos de teste, typecheck, lint e build listados no `CLAUDE.md` para o escopo afetado. Copie o resumo **real** da saída. Se um comando não existir ou não puder rodar, registre-o em "Validações não executadas", com motivo e o que falta.
4. **Critérios de aceite:** para cada `CA` do escopo, aponte a evidência (teste que passou, ou verificação manual registrada no plano de testes). Sem evidência, o status é ⏳ não validado.
5. **Review:** confira os itens ★ do [checklist](../../../docs/engineering/CODE_REVIEW_CHECKLIST.md); no fluxo completo, todos os itens aplicáveis. Verifique se há gatilho de revisão de segurança.
6. **Documentação:** status da spec, índices (`docs/specs/README.md`, `docs/adr/README.md`), `CLAUDE.md` e docs de produto afetados.
7. **Relatório:** gere o relatório no formato da seção 5 da Definition of Done.

## Regras

- O status final é **concluído** somente se todos os `CA` do escopo estiverem ✅. Caso contrário, é **parcial**, com a lista do que falta.
- Nunca invente saídas de comandos nem marque ✅ sem evidência.
- Se algum item falhar, não o conserte silenciosamente dentro desta verificação: reporte-o e proponha a correção.
