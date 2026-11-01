# Release vX.Y.Z

| Campo | Valor |
| --- | --- |
| Data prevista | AAAA-MM-DD |
| Responsável | |
| Trilha da Google Play | interna · fechada · aberta · produção |
| Specs incluídas | SPEC-NNN |

## 1. Conteúdo

| Spec / correção | Status | Observação |
| --- | --- | --- |

## 2. Qualidade

- [ ] Todas as specs incluídas estão **Implementadas**, com todos os critérios de aceite validados.
- [ ] Suíte completa, typecheck, lint e build passaram (registrar o resultado real abaixo).
- [ ] Revisões de segurança das specs com gatilho concluídas, sem bloqueios.
- [ ] Testes manuais das jornadas críticas em aparelho real: leitura, assinatura com teste, compra de créditos, criação de história, barreira parental, exclusão de conta.

## 3. Compatibilidade

- [ ] Mudanças de API compatíveis com as versões do app em uso.
- [ ] Migrações de banco testadas e com plano de rollback.
- [ ] Configurações comerciais (preços, pacotes, franquias, limites) revisadas para o ambiente de produção.

## 4. Google Play

- [ ] `versionCode` e `versionName` atualizados.
- [ ] Produtos e assinaturas configurados e testados com contas de teste de licença.
- [ ] Público-alvo e política de Famílias conferidos (DP-051).
- [ ] Formulário de segurança dos dados (Data safety) coerente com o inventário de dados.
- [ ] Política de privacidade e termos publicados e acessíveis.
- [ ] Mecanismo de denúncia de conteúdo gerado por IA presente (DP-054).
- [ ] Notas da versão em português.

## 5. Operação

- [ ] Monitoramento de erros, de custo de IA e alertas ativos.
- [ ] Teto de custo de IA configurado.
- [ ] Plano de rollback (desativar funcionalidade por configuração ou voltar versão).

## 6. Registro

| Verificação | Resultado real | Quem | Data |
| --- | --- | --- | --- |
