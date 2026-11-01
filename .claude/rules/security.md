# Segurança e privacidade

O produto trata dados de crianças e de pagamentos. Na dúvida, escolha a opção mais restritiva e pergunte.

## Dados de crianças (LGPD e DP-037)

- Colete apenas apelido e faixa etária no perfil infantil (DP-044). Nenhum outro dado da criança sem decisão registrada.
- Sem fotos reais (DP-025).
- O nome da criança nunca vai para o provedor de IA. Use um marcador e faça a substituição no servidor (DP-045).
- Dados de crianças não são usados para publicidade, perfilamento nem treinamento de modelos (RNF-PRIV-02).
- A exclusão de conta remove os dados da criança, salvo as retenções legais documentadas (RF-CON-04).

## Segredos

- Nenhum segredo no app: chaves de IA, credenciais de banco, chaves de serviço da Google Play (DP-036). O app é considerado público e engenharia reversa é esperada.
- Segredos só em variáveis de ambiente ou no gerenciador de segredos do ambiente. Nunca em código, testes, logs ou documentação.
- Arquivos `.env` nunca são versionados; versione apenas um `.env.example` sem valores reais.

## Autorização e acesso

- Toda leitura ou escrita de recurso do responsável (perfis, histórias, créditos) verifica no servidor se o recurso pertence à conta autenticada.
- Imagens e histórias privadas são servidas apenas por URLs com controle de acesso ou expiração (RNF-SEC-03).
- Direitos de acesso (Premium, teste, créditos) são decididos no servidor. O app apenas exibe.

## Compras e créditos

- Compras são validadas no servidor junto à Google Play antes de conceder qualquer direito (RF-MON-08).
- O processamento é idempotente: a mesma compra ou notificação nunca concede créditos duas vezes (RNF-REL-01).
- O livro-razão de créditos é apenas de acréscimo; correções são novos lançamentos, nunca edições (RNF-AUD-01).

## Entradas, saídas e abuso

- Valide toda entrada na borda (DTOs com validação), inclusive o apelido da criança (DP-054).
- Conteúdo gerado passa pela moderação antes da entrega; na dúvida, não entregue (DP-054).
- Aplique limites de requisição e de geração por conta (RNF-SEC-04).

## Logs e observabilidade

- Não registre em log: nome da criança, conteúdo de histórias, tokens, e-mails completos ou dados de pagamento.
- Use identificadores internos para correlacionar eventos.

## Dependências e SDKs

- Toda nova dependência é justificada (regra 4 de [general-engineering.md](general-engineering.md)).
- SDKs de terceiros no app precisam ser compatíveis com a política de Famílias da Google Play, e identificadores de publicidade não são coletados (DP-051).

## Revisão de segurança obrigatória

Use [docs/templates/security-review.md](../../docs/templates/security-review.md) quando a mudança tocar: autenticação, autorização, compras, créditos, dados de crianças, integração com provedores de IA, moderação, barreira parental, uploads ou armazenamento de arquivos, ou quando adicionar SDK de terceiros.
