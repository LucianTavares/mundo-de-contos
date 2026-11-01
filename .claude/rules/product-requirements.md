# Requisitos de produto

## Fonte das regras de negócio

Toda regra de negócio implementada precisa citar a sua fonte: uma regra `RN-xx` de uma especificação aprovada, que por sua vez cita `DP-xxx` ou `RF-*`.

Ordem de precedência das fontes: especificação aprovada → `DP-xxx` ([PRODUCT_DECISIONS.md](../../docs/product/PRODUCT_DECISIONS.md)) → ADR aceito → `RF-*`/`RNF-*` ([PRODUCT_REQUIREMENTS.md](../../docs/product/PRODUCT_REQUIREMENTS.md)) → demais documentos de produto.

## O que não é fonte de regra

- [OPEN_QUESTIONS.md](../../docs/product/OPEN_QUESTIONS.md): uma "Recomendação" não é uma decisão.
- Itens marcados como `[Proposta]`, `[Hipótese]` ou `[Aberto]`.
- Especificações em `Rascunho` ou `Em revisão`.
- Suposições do agente, "boas práticas de mercado" ou comportamento de outros apps.

## Quando a fonte não existir ou for ambígua

1. Pare a implementação daquele ponto.
2. Registre a lacuna como questão em aberto na especificação (e, se for de produto, proponha uma `QA-xx`).
3. Pergunte ao responsável pelo produto, apresentando opções e uma recomendação.
4. Valores numéricos ainda não decididos (por exemplo, a franquia do Premium, [QA-02](../../docs/product/OPEN_QUESTIONS.md#qa-02)) entram como **configuração**, nunca como constante inventada.

## Invariantes críticas

Antes de mudar qualquer fluxo, confira se ele toca uma destas decisões. Elas valem em todo o código.

| Invariante | Fonte |
| --- | --- |
| Nenhuma publicidade, em nenhuma modalidade | DP-012 |
| A criança não acessa compras, configurações, perfis nem conta; tudo isso fica atrás da barreira parental | DP-035, DP-048 |
| O leitor não exibe ofertas, preços nem atalhos para áreas adultas | RF-LEI-04 |
| Sem fotos reais de crianças | DP-025 |
| O perfil infantil guarda só apelido e faixa etária | DP-044 |
| O nome da criança não é enviado ao provedor de IA | DP-045 |
| Chaves de IA nunca ficam no app | DP-036 |
| Falha de geração não consome crédito em definitivo | DP-022 |
| Ordem de consumo: promocionais → cota da assinatura → comprados | DP-050, DP-058 |
| Créditos comprados não expiram; histórias criadas nunca ficam inacessíveis | DP-040, DP-021 |
| Movimentações de crédito são auditáveis (livro-razão) | DP-023 |
| Preços, pacotes, franquias e limites são configuráveis, nunca fixos no código de domínio | DP-024 |
| SDKs de terceiros precisam ser compatíveis com a política de Famílias da Google Play | DP-051 |
| Funcionalidades futuras (PDF, narração, iOS) não entram sem decisão | DP-038 |

## Mudança de requisito

Se o responsável mudar um requisito durante a tarefa, atualize primeiro a especificação original (seção de histórico) e a decisão correspondente (`/registrar-decisao`), e só então o código.
