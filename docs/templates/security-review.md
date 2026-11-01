# Revisão de segurança — SPEC-NNN Título

| Campo | Valor |
| --- | --- |
| Revisor | |
| Data | AAAA-MM-DD |
| Gatilhos presentes | autenticação · autorização · compras · créditos · dados de crianças · provedor de IA · moderação · barreira parental · arquivos · SDK de terceiros |

## 1. Ativos e dados

| Dado ou ativo | Sensibilidade | Onde é armazenado | Quem acessa | Retenção |
| --- | --- | --- | --- | --- |

## 2. Ameaças consideradas

| Ameaça | Cenário | Controle | Situação |
| --- | --- | --- | --- |
| Acesso a recurso de outra conta | | Verificação de dono no servidor | |
| Concessão duplicada de créditos | | Idempotência | |
| Fraude de compra | | Validação no servidor com a Google Play | |
| Vazamento de dado de criança ao provedor | | Marcador do nome (DP-045) | |
| Conteúdo impróprio entregue | | Moderação em camadas (DP-054) | |
| Criança acessando área adulta | | Barreira parental (DP-048) | |
| Segredo exposto no app ou em log | | security.md | |
| Abuso ou custo descontrolado | | Limites por conta e tetos (RNF-SEC-04, RNF-COST) | |

## 3. Checklist

- [ ] Nenhum segredo no app, no código, nos testes ou nos logs.
- [ ] Autorização por recurso verificada no servidor.
- [ ] Entradas validadas na borda.
- [ ] Dados de crianças limitados a apelido e faixa etária; nome fora das chamadas ao provedor.
- [ ] Operações com efeito são idempotentes.
- [ ] Logs sem dados pessoais nem conteúdo de histórias.
- [ ] URLs de arquivos privados com controle de acesso ou expiração.
- [ ] Novos SDKs compatíveis com a política de Famílias; sem identificador de publicidade.
- [ ] Inventário de dados e política de privacidade continuam corretos.

## 4. Achados

| # | Severidade | Descrição | Ação | Situação |
| --- | --- | --- | --- | --- |

## 5. Conclusão

- [ ] Sem bloqueios
- [ ] Bloqueado até resolver os achados
