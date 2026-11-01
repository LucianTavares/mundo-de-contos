# SPEC-NNN — Título da funcionalidade

| Campo | Valor |
| --- | --- |
| Status | Rascunho · Em revisão · Aprovada · Em implementação · Implementada · Substituída |
| Versão | 0.1 |
| Autor | |
| Aprovado por | (somente o responsável pelo produto) |
| Data de aprovação | AAAA-MM-DD |
| Specs relacionadas | SPEC-NNN (depende de / é base para) |
| Design técnico | [design.md](design.md) |
| Plano | [plan.md](plan.md) · [test-plan.md](test-plan.md) |

> Não remova seções. Se uma não se aplicar, escreva "Não se aplica" e o motivo.

## 1. Contexto

Por que esta funcionalidade existe agora. Qual problema do responsável ou da criança ela resolve. Links para visão, jornadas (`J-xx`) e decisões relevantes.

## 2. Objetivo

Uma ou duas frases, mensuráveis quando possível.

## 3. Escopo

### 3.1 Inclui

-

### 3.2 Não inclui

- (itens explicitamente fora, inclusive funcionalidades futuras relacionadas)

## 4. Requisitos

| Requisito | Fonte | Observação |
| --- | --- | --- |
| | RF-*, RNF-*, DP-xxx | |

## 5. Regras de negócio

Toda regra cita a sua fonte. Regras sem fonte vão para a seção 13 (Questões em aberto), não para esta tabela.

| ID | Regra | Fonte |
| --- | --- | --- |
| RN-01 | | DP-xxx / RF-* |

### Valores configuráveis

| Parâmetro | Valor inicial | Fonte do valor | Onde é configurado |
| --- | --- | --- | --- |
| | (ou "a definir" + QA-xx) | | |

## 6. Fluxos

### 6.1 Fluxo principal

1.

### 6.2 Fluxos alternativos

- **A1 —**

## 7. Falhas e exceções

| Situação | Comportamento esperado | Mensagem ao responsável | RN |
| --- | --- | --- | --- |
| | | | |

## 8. Segurança e privacidade

- Dados pessoais envolvidos (especialmente de crianças) e por que são necessários.
- Controles de acesso.
- Gatilhos de revisão de segurança presentes? (ver `.claude/rules/security.md`)
- Impacto na política de Famílias da Google Play (SDKs, dados).

## 9. Custos operacionais

Chamadas a provedores pagos, armazenamento e transferência. Limites e medição previstos.

## 10. Critérios de aceite

Formato Dado/Quando/Então. Cada critério é verificável e cita as `RN` que valida.

- **CA-01** (RN-01): **Dado** … **quando** … **então** …

## 11. Testes

| CA | Nível (unitário, integração, contrato, e2e, manual) | Observação |
| --- | --- | --- |
| CA-01 | | |

Detalhes em [test-plan.md](test-plan.md).

## 12. Dependências

| Tipo | Item | Situação |
| --- | --- | --- |
| Spec | SPEC-NNN | |
| ADR | ADR-NNNN | Proposto / Aceito |
| Decisão de produto | QA-xx | Aberta / DP-xxx |
| Externa | (provedor, conta, conteúdo) | |

## 13. Questões em aberto

| # | Questão | Bloqueia aprovação? | Encaminhamento |
| --- | --- | --- | --- |
| 1 | | Sim / Não | QA-xx proposta / pergunta ao responsável |

## 14. Métricas e observabilidade

Eventos e métricas para saber se a funcionalidade funciona e gera valor (sem dados de crianças).

## 15. Histórico de alterações

| Data | Versão | Alteração | Motivo / fonte |
| --- | --- | --- | --- |
| AAAA-MM-DD | 0.1 | Criação | |
