# Design técnico — SPEC-NNN Título

| Campo | Valor |
| --- | --- |
| Spec | [spec.md](spec.md) |
| Status | Rascunho · Em revisão · Aceito |
| Autor | |
| ADRs relacionados | ADR-NNNN |

## 1. Resumo

Como a solução atende à spec, em um parágrafo.

## 2. Componentes afetados

| Componente / módulo | Tipo de mudança | Camada (domínio, aplicação, infraestrutura, interface) |
| --- | --- | --- |
| | novo / alterado | |

## 3. Modelo de domínio

Entidades, valores, políticas e invariantes. Como cada `RN` é aplicada.

| RN | Onde é aplicada | Como |
| --- | --- | --- |
| RN-01 | | |

## 4. Contratos públicos

| Contrato | Novo / alterado | Compatível com versões anteriores? | Plano de migração |
| --- | --- | --- | --- |
| API / esquema / mensagem / produto na loja / configuração | | Sim / Não | |

Detalhe dos payloads, erros e versões.

## 5. Dados

- Tabelas, colunas, índices e migrações.
- Retenção e exclusão (inclusive na exclusão de conta).
- Dados pessoais armazenados e justificativa.

## 6. Fluxo técnico

Sequência de chamadas (app → API → fila → worker → provedor → storage). Diagrama em texto se ajudar.

## 7. Integrações externas

Provedores, portas e adaptadores, limites, retentativas, idempotência, comportamento em falha.

## 8. Segurança e privacidade

Autenticação, autorização por recurso, validação de entrada, segredos, logs, LGPD, política de Famílias.

## 9. Custos operacionais

Estimativa por operação, limites, medição e alertas.

## 10. Observabilidade

Logs (sem dados pessoais), métricas e alertas.

## 11. Alternativas consideradas

| Alternativa | Por que não foi escolhida |
| --- | --- |

## 12. Riscos técnicos

| Risco | Mitigação |
| --- | --- |

## 13. Dependências novas

| Pacote | Necessidade | Alternativas | Licença | Impacto (tamanho, privacidade) |
| --- | --- | --- | --- | --- |
