---
name: novo-adr
description: Registra uma decisão de arquitetura (ADR-NNNN) no Mundo de Contos. Use quando uma decisão técnica escolher ou trocar tecnologia, biblioteca estrutural, provedor ou serviço externo, definir a estrutura do monorepo ou um contrato público, ou afetar segurança, privacidade, custo operacional ou a portabilidade para iOS.
argument-hint: "[título da decisão]"
---

# Novo ADR

Argumento recebido: `$ARGUMENTS`. Critérios para abrir um ADR: [architecture.md](../../rules/architecture.md#quando-abrir-um-adr).

## Passos

1. Leia o índice [docs/adr/README.md](../../../docs/adr/README.md) e confira se já existe um ADR sobre o tema. Se existir e estiver aceito, o novo ADR **substitui** o anterior; não edite a decisão do antigo.
2. **Numeração:** o maior `ADR-NNNN` + 1, com quatro dígitos. Arquivo `docs/adr/ADR-NNNN-slug.md`, slug em kebab-case sem acentos.
3. Preencha a partir de [docs/templates/adr.md](../../../docs/templates/adr.md):
   - contexto com as restrições reais (`DP`, `RNF`, custos);
   - pelo menos duas alternativas, com prós e contras concretos;
   - consequências, inclusive segurança, privacidade, custo e iOS;
   - toda biblioteca ou serviço proposto com necessidade, licença e impacto.
4. Status **Proposto**. Adicione a linha no índice.
5. Se a decisão vier de um candidato listado em `PRODUCT_DECISIONS.md` (seção "Candidatos a ADR"), cite-o.

## Ao terminar

- Apresente a decisão, as alternativas e as consequências ao usuário e peça o aceite. **Nunca** marque como Aceito por conta própria.
- Após o aceite: atualize o status e a data, marque o ADR substituído (se houver) como "Substituído por ADR-NNNN" e referencie o ADR nas specs e regras afetadas (por exemplo, o campo `paths` em `.claude/rules/`).
