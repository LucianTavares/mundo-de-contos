# Fluxo de Spec-Driven Development (SDD)

> **Status:** em vigor · **Versão:** 1.0 · **Atualizado em:** 2026-11-01
> **Decisão de referência:** [DP-008](../product/PRODUCT_DECISIONS.md#plataforma-e-engenharia) · [ADR-0001](../adr/ADR-0001-harness-de-engenharia.md)

Este documento define como qualquer mudança no Mundo de Contos sai de uma solicitação e chega a código validado. Vale para pessoas e para agentes de IA.

**Princípio central:** a especificação aprovada é a fonte de verdade. O código implementa a especificação; se o código precisar ser diferente, a especificação muda primeiro.

---

## 1. Artefatos

| Artefato | Template | Onde vive | Obrigatório |
| --- | --- | --- | --- |
| Especificação de funcionalidade | [feature-spec.md](../templates/feature-spec.md) | `docs/specs/SPEC-NNN-slug/spec.md` | Sempre no fluxo completo |
| Design técnico | [technical-design.md](../templates/technical-design.md) | `docs/specs/SPEC-NNN-slug/design.md` | Quando há impacto técnico (quase sempre) |
| Plano de implementação | [implementation-plan.md](../templates/implementation-plan.md) | `docs/specs/SPEC-NNN-slug/plan.md` | Sempre no fluxo completo |
| Plano de testes | [test-plan.md](../templates/test-plan.md) | `docs/specs/SPEC-NNN-slug/test-plan.md` | Sempre no fluxo completo |
| Revisão de segurança | [security-review.md](../templates/security-review.md) | `docs/specs/SPEC-NNN-slug/security-review.md` | Quando há gatilho de [security.md](../../.claude/rules/security.md) |
| Registro de code review | [code-review.md](../templates/code-review.md) | Descrição do PR ou `docs/specs/SPEC-NNN-slug/review.md` | Sempre |
| ADR | [adr.md](../templates/adr.md) | `docs/adr/ADR-NNNN-slug.md` | Quando há decisão de arquitetura |
| Checklist de release | [release-checklist.md](../templates/release-checklist.md) | `docs/releases/vX.Y.Z.md` | A cada publicação |

Índices: [docs/specs/README.md](../specs/README.md) e [docs/adr/README.md](../adr/README.md).

## 2. Ciclo de vida da especificação

```text
Rascunho ──► Em revisão ──► Aprovada ──► Em implementação ──► Implementada
                 │                                                   │
                 └──── volta a Rascunho se houver mudanças           └──► Substituída (por SPEC-NNN)
```

| Status | Quem muda | Significado |
| --- | --- | --- |
| Rascunho | Agente ou pessoa | Em escrita. **Não pode ser implementada.** |
| Em revisão | Agente ou pessoa | Pronta para avaliação do responsável pelo produto. |
| Aprovada | **Somente o responsável pelo produto** | Fonte de verdade. Pode ser implementada. |
| Em implementação | Agente ou pessoa | Etapas do plano em andamento. |
| Implementada | Agente ou pessoa, após a Definition of Done | Todos os critérios de aceite validados. |
| Substituída | Agente ou pessoa | Uma spec mais nova assume o assunto. |

**O agente nunca marca uma spec como Aprovada por conta própria.** Ele a coloca em revisão e pede a aprovação explicitamente.

## 3. Escolha do fluxo

No início de toda tarefa, o agente declara qual fluxo vai usar e por quê. O responsável pode mudar a escolha.

### Fluxo simplificado: critérios

Use o fluxo simplificado **somente se todos** os critérios forem verdadeiros:

1. Não cria nem altera regra de negócio, requisito ou critério de aceite.
2. Não altera contrato público ([architecture.md](../../.claude/rules/architecture.md#contratos-públicos)).
3. Não adiciona, remove nem atualiza em versão major nenhuma dependência.
4. Não toca em área sensível: autenticação, autorização, compras, créditos, dados de crianças, provedores de IA, moderação, barreira parental, armazenamento de arquivos.
5. Fica restrita a um módulo e é fácil de reverter.

Exemplos que se encaixam: correção de texto ou erro de digitação; refatoração interna sem mudança de comportamento, já coberta por testes; correção de bug cujo comportamento esperado **já está** na spec; ajuste visual sem mudança de fluxo; atualização de documentação.

Se qualquer critério deixar de valer durante o trabalho, pare e mude para o fluxo completo.

## 4. Fluxo completo

| # | Passo | O que fazer | Saída |
| --- | --- | --- | --- |
| 1 | **Entender a solicitação** | Reformular o pedido, identificar o objetivo e quem é afetado. Perguntar se houver ambiguidade. | Entendimento confirmado |
| 2 | **Consultar documentação e código** | Ler as fontes de verdade (ver `CLAUDE.md`), specs relacionadas, ADRs e o código existente. Procurar lógica reutilizável. | Lista de fontes e de código relacionado |
| 3 | **Identificar requisitos** | Listar `DP`, `RF`, `RNF` e jornadas aplicáveis. Separar o que é decidido do que é proposta ou questão em aberto. | Requisitos com fonte; lacunas |
| 4 | **Criar ou atualizar a especificação** | `/nova-spec`. Regras de negócio `RN-xx`, sempre com fonte. Lacunas viram questões em aberto da spec. | `spec.md` em Rascunho |
| 5 | **Definir critérios de aceite** | `CA-xx` no formato Dado/Quando/Então, verificáveis e ligados às `RN`. Colocar a spec Em revisão. | **Portão 1:** spec Aprovada pelo responsável |
| 6 | **Avaliar impactos arquiteturais** | Design técnico: módulos, contratos, dados, custos, segurança. Abrir ADRs se necessário (`/novo-adr`). | `design.md`; ADRs. **Portão 2:** ADRs necessários aceitos |
| 7 | **Criar o plano de implementação** | Etapas `ET-xx` pequenas, cada uma entregável e testável, ligadas aos `CA`. Plano de testes. | `plan.md`, `test-plan.md` |
| 8 | **Implementar em pequenas etapas** | Uma etapa por vez. Cada etapa compila, passa nos testes e pode ser revisada sozinha. | Código + testes por etapa |
| 9 | **Executar testes** | Testes da etapa, suíte afetada, typecheck, lint, build. Reportar saídas reais. | Evidência de execução |
| 10 | **Revisar segurança e qualidade** | [CODE_REVIEW_CHECKLIST.md](CODE_REVIEW_CHECKLIST.md); revisão de segurança se houver gatilho. | Registro de review |
| 11 | **Atualizar documentação** | Status da spec, índices, `CLAUDE.md` (se houver novos comandos), docs de produto afetados. | Docs coerentes |
| 12 | **Registrar decisões relevantes** | ADRs para decisões técnicas; `/registrar-decisao` para decisões de produto tomadas pelo responsável. | Decisões registradas |

Ao final, use `/verificar-entrega` para conferir a [Definition of Done](DEFINITION_OF_DONE.md) e gerar o relatório.

### Portões

- **Portão 1 (spec aprovada):** sem ele, nenhum código de produto é escrito. Protótipos descartáveis para investigar viabilidade (spikes) são permitidos, desde que fiquem fora de `apps/` e `packages/` e sejam marcados como descartáveis.
- **Portão 2 (ADRs aceitos):** as etapas que dependem de um ADR só começam depois que ele é aceito. Etapas independentes podem avançar.

## 5. Fluxo simplificado

1. Entender e declarar por que a mudança se encaixa nos critérios da seção 3.
2. Localizar a fonte (spec, `DP` ou `RF`) que define o comportamento esperado.
3. Implementar. Em correção de bug, primeiro um teste que reproduz o bug.
4. Executar os testes afetados, o typecheck e o lint.
5. Revisar os itens marcados com ★ no [checklist de review](CODE_REVIEW_CHECKLIST.md).
6. Entregar o relatório final ([Definition of Done](DEFINITION_OF_DONE.md#5-relatório-final-obrigatório)).

## 6. Controle de mudanças

- **Toda funcionalidade relevante** tem uma spec identificável (`SPEC-NNN`), listada no índice.
- **Mudança de requisito** atualiza a spec original: o histórico de alterações registra o que mudou, por quê e qual `DP` motivou. Uma spec Implementada que muda volta para Em revisão.
- **Mudança arquitetural relevante** tem um ADR. Um ADR aceito não é editado: um novo ADR o substitui.
- **Ao final de toda tarefa**, o agente informa os arquivos criados e alterados, com justificativa.

## 7. Rastreabilidade

```text
DP-xxx / RF-*  ──►  SPEC-NNN  ──►  RN-xx  ──►  CA-xx  ──►  ET-xx  ──►  teste "SPEC-NNN CA-xx …"  ──►  commit [SPEC-NNN]
                                     │
                                     └──►  ADR-NNNN (quando a regra exige decisão técnica)
```

Toda linha de código de regra de negócio pode ser rastreada até uma `RN`, que cita a sua fonte.

---

## 8. Exemplo: criação de história personalizada

> **Exemplo ilustrativo.** Não é uma especificação aprovada e não deve ser implementado. Os IDs `SPEC-XXX` são fictícios. Os IDs `DP`, `RF` e `QA` são reais.

### Passo 1 — Entender a solicitação

> "Quero que o responsável consiga criar uma história em que a criança é a protagonista."

Objetivo: permitir que um responsável com direito de geração crie uma história personalizada, ilustrada, e a leia no leitor. Afeta o responsável (fluxo e créditos) e a criança (conteúdo). **Fluxo completo**, porque toca créditos, dados de crianças, provedores de IA e moderação.

### Passo 2 — Consultar documentação e código

- Produto: [J-04 e J-05](../product/USER_JOURNEYS.md#j-04--criar-uma-história-personalizada), [RF-CRI-01 a 14](../product/PRODUCT_REQUIREMENTS.md#17-criação-de-histórias-personalizadas-rf-cri), RF-PERS, RF-MON-11, [BUSINESS_MODEL §4](../product/BUSINESS_MODEL.md#4-créditos).
- Decisões: DP-014, DP-017, DP-022, DP-028, DP-034, DP-039, DP-042, DP-043, DP-045, DP-046, DP-050, DP-054, DP-058.
- Código: nenhum ainda. Em um caso real, procurar módulos de créditos, perfis e personagens já existentes para reutilizar.

**Achado importante:** a criação depende do modelo de créditos (reserva, consumo, liberação, ordem de consumo). Seguindo [MVP_SCOPE §10](../product/MVP_SCOPE.md#10-sequência-sugerida-de-especificações-sdd), o modelo de créditos vira uma **spec separada e pré-requisito** (`SPEC-XXA — Créditos e direitos de acesso`), e a criação (`SPEC-XXB`) depende dela.

### Passo 3 — Identificar requisitos

| Situação | Item | Tratamento |
| --- | --- | --- |
| Decidido | DP-043 opções guiadas; DP-045 nome não vai ao provedor; DP-050/DP-058 ordem de consumo; DP-022 falha não consome | Viram `RN` com fonte |
| Configuração | Franquia do Premium ([QA-02](../product/OPEN_QUESTIONS.md#qa-02)); páginas por história (DP-034) | Entram como configuração, sem valor inventado |
| Proposta, não decisão | RF-PAR-02 (barreira parental na confirmação de consumo); ciclo reserva → consumo ([BUSINESS_MODEL §4.3](../product/BUSINESS_MODEL.md#43-ciclo-de-vida-de-um-crédito--proposta)) | **Não** viram regra. RF-PAR-02 vai para as questões da spec; o ciclo de reserva vai para o design ou ADR como mecanismo técnico que atende à DP-022 |
| Em aberto | [QA-12](../product/OPEN_QUESTIONS.md#qa-12) gênero gramatical | **Bloqueia a aprovação** (afeta o texto gerado) |
| Em aberto | Lista concreta das opções guiadas (temas, cenários, valores) | Nova questão de produto; bloqueia a aprovação |
| Em aberto | [QA-23](../product/OPEN_QUESTIONS.md#qa-23) provedores de IA | Não bloqueia a spec; bloqueia o Portão 2 (ADR) |
| Em aberto | [QA-25](../product/OPEN_QUESTIONS.md#qa-25) aviso de história pronta | Fora do escopo desta spec; nela, apenas o estado dentro do app |
| Dependência | Política de conteúdo (D-05), escrita na preparação da Play Console | O mecanismo de moderação é especificado agora; as regras de conteúdo entram como configuração antes do lançamento |

### Passo 4 — Especificação (trecho de `spec.md`)

| ID | Regra de negócio | Fonte |
| --- | --- | --- |
| RN-01 | Só inicia a criação quem tem direito de geração: cota de teste ou Premium, créditos promocionais ou créditos comprados. | DP-014, DP-017, DP-039 |
| RN-02 | O consumo segue a ordem: promocionais → cota da assinatura → comprados. | DP-050, DP-058 |
| RN-03 | Uma geração que falha em definitivo não consome crédito. | DP-022 |
| RN-04 | Os parâmetros da história vêm exclusivamente de opções guiadas; o único texto livre é o apelido já salvo no perfil. | DP-043, DP-054 |
| RN-05 | O nome da criança nunca é enviado ao provedor de IA. | DP-045 |
| RN-06 | A história tem capa, introdução, N páginas (configurável, referência 5 a 7) e encerramento. | DP-034 |
| RN-07 | O conteúdo passa pela verificação automática antes da entrega; na dúvida, não é entregue. | DP-054 |
| RN-08 | O personagem usado é o salvo no perfil e mantém a aparência em todas as páginas. | DP-028, DP-046 |
| RN-09 | A história concluída é salva automaticamente em Minha coleção. | RF-CRI-10, DP-021 |

### Passo 5 — Critérios de aceite (trecho)

- **CA-01** (RN-02): **Dado** um responsável em teste, com 2 gerações de cota e 1 crédito promocional, **quando** confirma uma criação, **então** o crédito promocional é usado e a cota continua com 2.
- **CA-02** (RN-02): **Dado** um assinante Premium sem cota restante e com 3 créditos comprados, **quando** confirma uma criação, **então** 1 crédito comprado é usado.
- **CA-03** (RN-03): **Dado** que a geração falhou após o teto de retentativas, **quando** o job termina, **então** o crédito volta ao saldo, um lançamento de liberação é registrado e o responsável vê a mensagem de falha com o crédito devolvido.
- **CA-04** (RN-05): **Dado** um perfil com apelido "Lia", **quando** a geração é solicitada ao provedor, **então** nenhuma requisição ao provedor contém "Lia", e a história entregue contém "Lia" no texto.
- **CA-05** (RN-07): **Dado** que a verificação reprova a saída em todas as tentativas, **quando** o teto é atingido, **então** a história não é entregue e vale o CA-03.
- **CA-06** (RN-01): **Dado** um responsável Free sem créditos, **quando** abre Criar, **então** não consegue iniciar a criação, e as ofertas só aparecem depois da barreira parental.

A spec vai para **Em revisão**. O agente apresenta as questões bloqueantes (QA-12, opções guiadas, RF-PAR-02) e **pede a aprovação**. A implementação não começa antes do Portão 1.

### Passo 6 — Impactos arquiteturais (trecho de `design.md`)

- **Módulos:** histórias (novo), créditos (da `SPEC-XXA`), perfis e personagens (existentes), moderação (novo, atrás de uma porta).
- **Contratos públicos novos:** `POST` de criação com chave de idempotência; consulta do estado da história; mensagem do job de geração; formato da história no storage.
- **ADRs necessários:** processamento assíncrono (fila e workers); provedor de IA e porta de abstração; estratégia de consistência do personagem; substituição do nome por marcador. Todos estão nos [candidatos a ADR](../product/PRODUCT_DECISIONS.md#candidatos-a-adr).
- **Custo:** registrar o custo por chamada e por história (RNF-COST-01); teto de retentativas configurável.
- **Segurança:** gatilhos presentes (créditos, dados de crianças, provedor de IA, moderação), logo há revisão de segurança obrigatória.

### Passo 7 — Plano de implementação (trecho de `plan.md`)

| Etapa | Entrega | CA | Depende de |
| --- | --- | --- | --- |
| ET-01 | Caso de uso "solicitar criação": valida direito e reserva o crédito via `SPEC-XXA` | CA-01, CA-02, CA-06 | SPEC-XXA implementada |
| ET-02 | Endpoint de criação com idempotência e endpoint de estado | CA-06 | ET-01 |
| ET-03 | Job de geração com provedor **falso**, montagem da estrutura da história (RN-06) | — | ADR de processamento assíncrono |
| ET-04 | Marcador do nome e substituição no servidor | CA-04 | ET-03 |
| ET-05 | Verificação de conteúdo (porta + implementação falsa) e teto de retentativas com liberação | CA-03, CA-05 | ET-03 |
| ET-06 | Adaptador do provedor real de IA | — | ADR do provedor |
| ET-07 | Telas do fluxo Criar no app (opções guiadas, revisão, estados) | CA-06 | ET-02 |
| ET-08 | Salvar em Minha coleção e abrir no leitor | — | ET-05, ET-07 |

### Passos 8 a 12 — Execução

- **8–9:** cada `ET` é implementada com seus testes (`describe('SPEC-XXB CA-04 …')`). Depois de cada etapa, rodar os testes afetados, o typecheck e o lint, e registrar a saída real.
- **10:** checklist de code review + revisão de segurança ([security-review.md](../templates/security-review.md)), com atenção especial a CA-04 (privacidade) e à idempotência.
- **11:** spec → Implementada; índice de specs atualizado; J-04 revisada, se o fluxo final mudou algum detalhe.
- **12:** ADRs aceitos referenciados no design; se o responsável decidiu QA-12 e as opções guiadas durante o processo, `/registrar-decisao` cria as novas `DP`.

---

## 9. Evolução do harness

Quando o monorepo existir, avaliar (com ADR):

- hooks do Claude Code que executem typecheck e lint automaticamente após edições;
- permissões em `.claude/settings.json` para os comandos de build e teste do projeto;
- novas skills, **somente** se surgir um fluxo repetível que as justifique.
