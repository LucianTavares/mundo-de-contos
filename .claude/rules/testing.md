---
paths:
  - "apps/**"
  - "packages/**"
---

# Testes

## Princípios

- Todo critério de aceite (`CA-xx`) de uma spec tem pelo menos um teste automatizado, ou uma justificativa registrada no plano de testes para ser verificado manualmente.
- O nome do teste cita a spec e o critério: `describe('SPEC-004 CA-02 — libera o crédito quando a geração falha', ...)`.
- Correção de bug começa com um teste que reproduz o bug e falha.
- Testes são determinísticos: sem dependência de horário real, aleatoriedade sem semente, rede ou ordem de execução.

## Proibições

- Remover, desativar (`skip`, `only`, `xit`, comentar) ou afrouxar asserções para a suíte passar.
- Chamar provedores reais (IA, Google Play, storage) em testes automatizados. Use as implementações falsas das portas.
- Usar dados reais de pessoas ou de crianças em fixtures.
- Afirmar que testes passaram sem ter executado. Copie no relatório o comando e o resumo real da saída.

## Níveis

| Nível | Foco | Exemplos |
| --- | --- | --- |
| Unitário | Domínio e políticas puras | Ordem de consumo de créditos, cálculo de saldo, limites de perfis |
| Integração | Aplicação + infraestrutura real local (banco de teste) | Repositórios, migrações, idempotência de compras |
| Contrato | Fronteiras públicas | Formato da API, mensagens de fila |
| End-to-end | Jornadas críticas | Criar história, comprar créditos, barreira parental |

Regras de créditos, direitos de acesso e limites têm cobertura obrigatória em testes unitários (RNF-TEST-01).

## Ao terminar

Execute a suíte afetada, o typecheck e o lint. Se algum não puder ser executado, informe qual, por quê e o que falta (regra 11 de [general-engineering.md](general-engineering.md)).
