# Mundo de Contos

Aplicativo mobile (Android primeiro) de histórias infantis ilustradas e personalizadas para responsáveis por crianças de 0 a 6 anos. Identificador técnico: `mundo-de-contos`. Idioma da documentação: português brasileiro.

**Fase atual:** fundação. Ainda não há código nem monorepo criado. Os comandos de build, teste e lint serão listados aqui quando o monorepo existir (ADR pendente).

## Como trabalhar neste repositório

1. Siga o fluxo **Spec-Driven Development**: [docs/engineering/SDD_WORKFLOW.md](docs/engineering/SDD_WORKFLOW.md). No início de cada tarefa, declare se usa o fluxo completo ou o simplificado, e por quê.
2. Só implemente o que tem **especificação aprovada** em [docs/specs/](docs/specs/README.md).
3. Antes de declarar uma tarefa concluída, cumpra a [Definition of Done](docs/engineering/DEFINITION_OF_DONE.md) e entregue o relatório final no formato definido nela.

## Fontes de verdade (em ordem de precedência)

1. Especificações **aprovadas**: [docs/specs/](docs/specs/README.md)
2. Decisões de produto: [docs/product/PRODUCT_DECISIONS.md](docs/product/PRODUCT_DECISIONS.md) (`DP-xxx`)
3. ADRs **aceitos**: [docs/adr/](docs/adr/README.md)
4. Requisitos: [docs/product/PRODUCT_REQUIREMENTS.md](docs/product/PRODUCT_REQUIREMENTS.md) (`RF-*`, `RNF-*`)
5. Demais documentos de produto: [visão](docs/product/PRODUCT_VISION.md), [modelo de negócio](docs/product/BUSINESS_MODEL.md), [jornadas](docs/product/USER_JOURNEYS.md), [escopo do MVP](docs/product/MVP_SCOPE.md)

[OPEN_QUESTIONS.md](docs/product/OPEN_QUESTIONS.md) **não** é fonte de regra: recomendações ali não são decisões. Em caso de conflito entre fontes, pare e pergunte.

## Regras permanentes (`.claude/rules/`)

| Arquivo | Quando é carregado |
| --- | --- |
| [general-engineering.md](.claude/rules/general-engineering.md) | Sempre. Inclui as regras inegociáveis do agente |
| [product-requirements.md](.claude/rules/product-requirements.md) | Sempre |
| [architecture.md](.claude/rules/architecture.md) | Sempre |
| [security.md](.claude/rules/security.md) | Sempre |
| [documentation.md](.claude/rules/documentation.md) | Ao trabalhar em `docs/**` e arquivos Markdown |
| [backend.md](.claude/rules/backend.md) | Ao trabalhar em `apps/api/**` |
| [mobile.md](.claude/rules/mobile.md) | Ao trabalhar em `apps/mobile/**` |
| [testing.md](.claude/rules/testing.md) | Ao trabalhar em `apps/**` e `packages/**` |

Os caminhos `apps/api`, `apps/mobile` e `packages/` são **provisórios** até o ADR de estrutura do monorepo; ajuste o campo `paths` das regras quando ele for aceito.

## Skills do projeto (`.claude/skills/`)

| Skill | Uso |
| --- | --- |
| `/nova-spec` | Criar ou atualizar uma especificação a partir dos templates |
| `/novo-adr` | Registrar uma decisão de arquitetura |
| `/registrar-decisao` | Registrar uma decisão de produto tomada pelo responsável (só por pedido explícito) |
| `/verificar-entrega` | Conferir a Definition of Done e produzir o relatório final da tarefa |

## Referências de engenharia

- [Fluxo SDD](docs/engineering/SDD_WORKFLOW.md) (inclui o exemplo completo da criação de história personalizada)
- [Definition of Done](docs/engineering/DEFINITION_OF_DONE.md)
- [Checklist de code review](docs/engineering/CODE_REVIEW_CHECKLIST.md)
- [Templates](docs/templates/)
