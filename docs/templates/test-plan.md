# Plano de testes — SPEC-NNN Título

| Campo | Valor |
| --- | --- |
| Spec | [spec.md](spec.md) |
| Plano | [plan.md](plan.md) |

## 1. Estratégia

Quais níveis serão usados e por quê. Quais portas terão implementações falsas.

## 2. Matriz critério × teste

| CA | Cenário | Nível | Nome do teste / arquivo | Automatizado? | Status |
| --- | --- | --- | --- | --- | --- |
| CA-01 | | unitário / integração / contrato / e2e / manual | `SPEC-NNN CA-01 — …` | Sim / Não (motivo) | Pendente / Passou / Falhou |

## 3. Casos de borda e falhas

| Caso | Comportamento esperado | Teste |
| --- | --- | --- |
| Falha do provedor / timeout | | |
| Requisição repetida (idempotência) | | |
| Recurso de outra conta | Acesso negado | |
| Limite atingido | | |

## 4. Dados de teste

Fixtures e fábricas. **Nunca** usar dados reais de pessoas ou de crianças.

## 5. Verificações manuais

Para o que não puder ser automatizado: passos, aparelho ou emulador, resultado esperado, quem executou, data e resultado.

## 6. Fora do escopo de testes

O que não será testado e por quê.

## 7. Resultado

| Data | Comando ou execução | Resultado real |
| --- | --- | --- |
