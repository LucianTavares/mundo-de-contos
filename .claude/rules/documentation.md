---
paths:
  - "docs/**"
  - "**/*.md"
---

# Documentação

A documentação é parte do produto: as especificações aprovadas são a fonte de verdade do código.

## Princípios

- Português brasileiro. Nomes técnicos e identificadores de código podem ficar em inglês.
- **Um dono por assunto.** Antes de criar um documento, procure se o assunto já tem dono e atualize-o. Os outros documentos referenciam por ID, sem copiar o conteúdo.
- Sem contradições: ao mudar uma informação, atualize ou remova as cópias e as referências afetadas.
- Datas absolutas (AAAA-MM-DD), nunca relativas ("semana que vem").
- Separe sempre o que é decisão aprovada, hipótese, proposta e questão em aberto.

## Identificadores

| Prefixo | Significado | Onde vive |
| --- | --- | --- |
| `DP-xxx` | Decisão de produto | `docs/product/PRODUCT_DECISIONS.md` |
| `H-xx` | Hipótese | `docs/product/PRODUCT_DECISIONS.md` |
| `QA-xx` | Questão em aberto | `docs/product/OPEN_QUESTIONS.md` |
| `RF-*`, `RNF-*` | Requisitos | `docs/product/PRODUCT_REQUIREMENTS.md` |
| `J-xx` | Jornada | `docs/product/USER_JOURNEYS.md` |
| `R-xx`, `D-xx` | Risco, dependência | `docs/product/MVP_SCOPE.md` |
| `SPEC-NNN` | Especificação de funcionalidade | `docs/specs/SPEC-NNN-slug/` |
| `RN-xx`, `CA-xx` | Regra de negócio e critério de aceite (locais à spec) | dentro da spec |
| `ET-xx` | Etapa do plano de implementação (local à spec) | `plan.md` da spec |
| `ADR-NNNN` | Decisão de arquitetura | `docs/adr/` |
| `CR-xx` | Item do checklist de code review | `docs/engineering/CODE_REVIEW_CHECKLIST.md` |

IDs nunca são reutilizados. Itens obsoletos são marcados como substituídos, não apagados.

## Quando atualizar

- Mudou requisito → atualize a spec original (histórico de alterações) antes do código.
- Mudou decisão de arquitetura → novo ADR que substitui o anterior; o antigo recebe o status "Substituído por".
- Código entregue → atualize os índices ([docs/specs/README.md](../../docs/specs/README.md), [docs/adr/README.md](../../docs/adr/README.md)) e o status da spec.
- Novos comandos de build ou teste → atualize o `CLAUDE.md`.

## Templates

Use sempre os templates de [docs/templates/](../../docs/templates/). Não remova seções: se uma não se aplicar, escreva "Não se aplica" e o motivo.
