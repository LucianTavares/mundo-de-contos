# Engenharia geral

## Regras inegociáveis do agente

1. Nunca altere um contrato público sem avaliar e documentar o impacto. Contratos públicos estão listados em [architecture.md](architecture.md).
2. Nunca remova, desative (`skip`, `only`, comentário) ou enfraqueça testes para fazer a suíte passar.
3. Nunca ignore erros de TypeScript, lint ou build (`@ts-ignore`, `eslint-disable`, `any` para silenciar) sem uma justificativa aprovada pelo responsável e registrada no código.
4. Não adicione bibliotecas sem explicar a necessidade, as alternativas avaliadas e o impacto (tamanho, licença, manutenção, privacidade).
5. Não duplique lógica existente: procure antes de escrever e reutilize ou extraia.
6. Não introduza dependências circulares.
7. Não misture domínio com infraestrutura.
8. Não implemente regra de negócio sem fonte documental (ver [product-requirements.md](product-requirements.md)).
9. Não invente resultados de testes, comandos executados ou saídas. Reporte apenas o que de fato executou e observou.
10. Não declare uma tarefa concluída sem validar os critérios de aceite ([DEFINITION_OF_DONE.md](../../docs/engineering/DEFINITION_OF_DONE.md)).
11. Se não conseguir executar uma validação, diga isso explicitamente, com o motivo, e diga o que falta para executá-la.

## Forma de trabalhar

- Siga o [fluxo SDD](../../docs/engineering/SDD_WORKFLOW.md). Declare no início se a tarefa usa o fluxo completo ou o simplificado e por quê.
- Trabalhe em etapas pequenas, cada uma compilando e com testes passando.
- Prefira a solução mais simples que atenda à especificação. Não antecipe funcionalidades futuras.
- Considere o custo operacional: chamadas a IA, armazenamento e transferência têm custo e precisam de limites e medição.
- Não altere arquivos fora do escopo da tarefa. Se encontrar um problema fora do escopo, registre-o e informe, sem corrigir por conta própria.
- Ao terminar, informe os arquivos criados e alterados, com a justificativa de cada um.

## Código

- TypeScript em modo estrito, em todo o monorepo.
- Nomes de código em inglês. Textos de interface e documentação em português brasileiro.
- Funções pequenas, com nomes que revelam intenção. Comentários explicam o **porquê**, não o quê.
- Erros são tratados explicitamente. Não engula exceções.
- Datas em UTC no backend. Valores monetários em centavos (inteiros), nunca em ponto flutuante.

## Branches, commits e rastreabilidade

- **Todo commit vai para uma branch da tarefa. Nunca faça commit nem push diretamente na `main`.** A integração na `main` é feita pelo responsável (por exemplo, via pull request).
- Antes do primeiro commit de uma tarefa, crie a branch a partir da `main` atualizada, com o nome `tipo/descricao-curta` (tipos: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`), incluindo o ID da spec quando houver: `feat/spec-004-reserva-de-credito`.
- Commit e push somente quando o usuário pedir.
- Mensagens de commit no padrão Conventional Commits, citando a especificação ou o ADR quando houver (por exemplo, `feat(credits): reserva de crédito [SPEC-004]`).
- Uma mudança de comportamento sem especificação correspondente é um defeito de processo: pare e siga o fluxo.
