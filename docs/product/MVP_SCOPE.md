# Mundo de Contos — Escopo do MVP

> **Status:** rascunho para aprovação · **Versão:** 0.1 · **Atualizado em:** 2026-10-31

## 1. Objetivo do MVP

Lançar no **Android** uma versão que valide, com o menor escopo possível:

1. que responsáveis usam o Mundo de Contos para **ler com as crianças** de forma recorrente (biblioteca + leitor);
2. que existe **disposição a pagar**, por assinatura ([H-01](PRODUCT_DECISIONS.md#h-01)) ou por créditos ([H-02](PRODUCT_DECISIONS.md#h-02));
3. que é possível gerar histórias personalizadas com **qualidade, segurança, consistência visual e custo** compatíveis com o preço ([H-07](PRODUCT_DECISIONS.md#h-07), [H-09](PRODUCT_DECISIONS.md#h-09)).

## 2. Princípios de corte

- Funcionalidade sem decisão aprovada **não entra** até ser decidida ([OPEN_QUESTIONS.md](OPEN_QUESTIONS.md)).
- Funcionalidade futura **não entra** sem nova decisão registrada ([DP-038](PRODUCT_DECISIONS.md#segurança-e-privacidade)).
- Na dúvida entre duas soluções, escolher a mais simples que preserve segurança infantil, privacidade e auditabilidade.
- Toda funcionalidade com custo variável entra com limites e medição.

---

## 3. Dentro do MVP

| Área | Inclui | Requisitos |
| --- | --- | --- |
| Conta | Cadastro do responsável, sessão, troca de aparelho, exclusão de conta, aceite de termos | RF-CON-01 a 05 |
| Perfis infantis | Criação, edição e exclusão com dados mínimos; limite por modalidade | RF-PER-01 a 05 |
| Biblioteca | Cerca de 30 histórias autorais, 6 categorias, faixas etárias, filtros, 10 gratuitas, indicação de bloqueio | RF-BIB-01 a 07 |
| Leitor | Página a página, ilustração grande, sem elementos comerciais, final com favoritar e reler | RF-LEI-01 a 05 (06 se aprovado) |
| Minha coleção | Favoritos e histórias criadas, acessíveis em qualquer modalidade | RF-COL-01 a 05 |
| Personagens | Bases ilustradas + personalização visual; consistência entre páginas; sem fotos | RF-PERS-01 a 07 |
| Criação | Fluxo de criação, revisão de consumo, geração assíncrona, estados, moderação, liberação de crédito em falha | RF-CRI-01 a 10, 12 |
| Monetização | Premium mensal com teste de 7 dias, pacotes de créditos, saldo, histórico, restaurar compras, validação no servidor | RF-MON-01 a 10 |
| Controle parental | Barreira parental em todas as áreas adultas e na confirmação de consumo | RF-PAR-01 a 03 |
| Início e configurações | Sugestões, continuar leitura, mensagens de leitura compartilhada, configurações | RF-INI-01 a 03, RF-CFG-01 |
| Operação | Publicação do catálogo, configuração comercial, consulta ao livro-razão, créditos promocionais, monitoramento de custo | RF-OPS-01 a 05 |
| Qualidade | Todos os requisitos não funcionais | RNF-* |

## 4. Dentro do MVP, mas com definição pendente

Estes itens estão no MVP, mas a especificação depende de decisões. As questões **bloqueantes** estão marcadas em [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md).

| Item | Questões |
| --- | --- |
| Franquia mensal do Premium | QA-02 |
| Créditos promocionais e reembolso | QA-10, QA-30 |
| Organização de Minha coleção e favoritos após a assinatura | QA-07, QA-08 |
| Gênero gramatical do protagonista | QA-12 |
| Provedores de IA | QA-23 |

## 5. Fora do MVP

### 5.1 Funcionalidades futuras já previstas

| Funcionalidade | Referência |
| --- | --- |
| Exportação de histórias em PDF | [DP-014](PRODUCT_DECISIONS.md#monetização) |
| Narração em áudio | [DP-014](PRODUCT_DECISIONS.md#monetização) |
| Versão iOS (com App Store e compras na Apple) | [DP-007](PRODUCT_DECISIONS.md#plataforma-e-engenharia) |

### 5.2 Explicitamente excluídos do MVP

| Item | Motivo |
| --- | --- |
| Fotografias reais de crianças | [DP-025](PRODUCT_DECISIONS.md#conteúdo-e-personagens) |
| Publicidade de qualquer tipo | [DP-012](PRODUCT_DECISIONS.md#monetização) |
| Acesso independente da criança (login infantil) | [DP-035](PRODUCT_DECISIONS.md#segurança-e-privacidade) |
| Microsserviços | [DP-009](PRODUCT_DECISIONS.md#plataforma-e-engenharia) |

### 5.3 Não previstos (candidatos a avaliação futura)

Itens que **não** constam nas decisões atuais. Só entram com decisão registrada.

- Versão web.
- Outros idiomas.
- Compartilhamento de histórias com familiares ([QA-27](OPEN_QUESTIONS.md#qa-27)).
- Plano anual ou familiar ([QA-09](OPEN_QUESTIONS.md#qa-09)).
- Livro impresso.
- Edição manual do texto gerado ([QA-15](OPEN_QUESTIONS.md#qa-15)).
- Programa de indicação.

---

## 6. Critérios de pronto do MVP

O MVP pode ser publicado quando:

1. Todas as questões **bloqueantes** de [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md) estiverem decididas e registradas em [PRODUCT_DECISIONS.md](PRODUCT_DECISIONS.md).
2. Cada funcionalidade do MVP tiver especificação aprovada e testes de aceitação passando.
3. As histórias da biblioteca inicial estiverem produzidas, revisadas e publicadas ([D-03](#9-dependências)).
4. O fluxo completo de compra, teste, cancelamento, reembolso e restauração tiver sido testado no ambiente de testes da Google Play.
5. O custo médio por história (`CMH`) tiver sido medido e a economia unitária revisada ([BUSINESS_MODEL.md §7](BUSINESS_MODEL.md#7-economia-unitária)).
6. Termos de uso, política de privacidade e consentimento estiverem produzidos e revisados internamente ([D-04](#9-dependências), [DP-052](PRODUCT_DECISIONS.md#questões-decididas)), e a declaração de público na Google Play seguir a [DP-051](PRODUCT_DECISIONS.md#questões-decididas).
7. A política de conteúdo e a moderação estiverem ativas e testadas com casos adversos.
8. O monitoramento de custo, erros e geração estiver ativo, com alertas.

## 7. Métricas de acompanhamento

As metas numéricas serão definidas após o baseline das primeiras semanas.

| Grupo | Métrica |
| --- | --- |
| Ativação | % de novos responsáveis que concluem a primeira leitura |
| Engajamento | Sessões de leitura concluídas por família ativa por semana (indicador norte proposto) |
| Retenção | Famílias ativas na semana 1 e na semana 4 após a instalação |
| Conversão | Free → teste; teste → pago; Free → compra de créditos |
| Criação | Histórias criadas por usuário com direito de geração; % de histórias concluídas que são lidas |
| Qualidade da geração | Taxa de sucesso, taxa de bloqueio pela moderação, tempo até a história ficar pronta |
| Custo | `CMH`, custo de IA por assinante, custo do teste por conversão |
| Confiança | Reembolsos, contatos de suporte por tema, avaliações na loja |

---

## 8. Riscos

| ID | Risco | Prob. | Impacto | Mitigação |
| --- | --- | --- | --- | --- |
| R-01 | Custo de IA por história acima do previsto, gerando margem negativa | Média | Alto | Spike de custo antes de fechar preços; limites e franquias configuráveis; alertas de custo; ajuste de páginas e resolução |
| R-02 | Personagem inconsistente entre páginas, quebrando a proposta de valor | Alta | Alto | Spike técnico dedicado ([H-07](PRODUCT_DECISIONS.md#h-07)); alternativas como composição sobre arte pré-produzida; restringir a personalização se necessário |
| R-03 | Conteúdo gerado inadequado para crianças | Média | Muito alto | Opções guiadas em vez de texto livre ([DP-043](PRODUCT_DECISIONS.md#questões-decididas)); moderação de entrada e saída; política de conteúdo; canal de denúncia; testes adversos |
| R-04 | Não conformidade com a legislação de proteção de crianças, de dados ou do consumidor, ou com as políticas da Google Play | Média-alta | Muito alto | Sem assessoria jurídica no MVP ([DP-052](PRODUCT_DECISIONS.md#questões-decididas)): checklist de conformidade baseado em guias oficiais (ANPD, Google Play); minimização de dados; política de Famílias desde o início ([DP-051](PRODUCT_DECISIONS.md#questões-decididas)); reavaliar a assessoria ao escalar |
| R-05 | Produção da biblioteca (texto, ilustração, revisão) atrasar o lançamento | Média | Alto | Textos de autoria própria ([DP-049](PRODUCT_DECISIONS.md#questões-decididas)), escritos em paralelo à engenharia; ilustrações por IA com curadoria ([DP-056](PRODUCT_DECISIONS.md#questões-decididas)); definir o guia de estilo cedo |
| R-06 | Percepção de "app genérico de IA" ou desconfiança de responsáveis em relação à IA | Média | Alto | Biblioteca como centro da experiência; transparência sobre o uso de IA; qualidade editorial. Com ilustrações por IA ([DP-056](PRODUCT_DECISIONS.md#questões-decididas)), guia de estilo e curadoria rigorosa são essenciais |
| R-07 | Baixa conversão ou canibalização (Free e créditos suficientes para a maioria) | Média | Alto | Acompanhar a conversão por coorte; ajustar a seleção do Free e os pacotes por configuração |
| R-08 | Geração demorada demais | Média | Médio | Processamento assíncrono com aviso; geração progressiva; medição contínua |
| R-09 | Dependência de provedores de IA (preço, disponibilidade, mudança de política) | Média | Alto | Camada de abstração de provedor (ADR); monitoramento; plano de contingência |
| R-10 | Abuso ou fraude (gerações automatizadas, exploração de reembolsos) | Baixa | Médio | Limites por conta no servidor; validação de compras; reconciliação de estornos |
| R-11 | Uso do produto por bebês sozinhos diante da tela, contrariando o posicionamento | Média | Médio | Mensagens de leitura compartilhada; leitor sem autoplay nem estímulos de retenção |
| R-12 | Divergência entre o livro-razão de créditos e a Google Play (pendentes, reembolsos, notificações repetidas) | Média | Alto | Processamento idempotente; reconciliação periódica; testes de cenários de loja |
| R-13 | Personalização percebida como estereotipada ou excludente | Média | Alto | Opções visuais sem rótulos; revisão por pessoas diversas; canal de feedback |
| R-14 | Crescimento de escopo pela quantidade de questões em aberto | Alta | Médio | Princípios de corte (§2); decidir primeiro as questões bloqueantes |

## 9. Dependências

| ID | Dependência | Necessária para |
| --- | --- | --- |
| D-01 | CNPJ ([DP-053](PRODUCT_DECISIONS.md#questões-decididas)); conta de desenvolvedor de organização na Google Play (exige número D-U-N-S), perfil de pagamentos e `applicationId` definido ([QA-32](OPEN_QUESTIONS.md#qa-32)) | Billing, testes internos, publicação |
| D-02 | Escolha e contratação de provedores de IA de texto e imagem, com termos de privacidade adequados ([QA-23](OPEN_QUESTIONS.md#qa-23)) | Criação de histórias |
| D-03 | Produção autoral da biblioteca inicial (texto, ilustrações, revisão) e da arte dos personagens base e das opções de personalização. Textos: [DP-049](PRODUCT_DECISIONS.md#questões-decididas); ilustrações por IA com curadoria: [DP-056](PRODUCT_DECISIONS.md#questões-decididas) | Biblioteca, personagens |
| D-04 | Conformidade conduzida internamente, na preparação da publicação na Play Console ([DP-052](PRODUCT_DECISIONS.md#questões-decididas)): inventário de dados, termos de uso, política de privacidade, consentimento do responsável e checklist de LGPD, ECA Digital e CDC ([QA-22](OPEN_QUESTIONS.md#qa-22)) | Publicação |
| D-05 | Política editorial e de segurança de conteúdo, em `docs/content/CONTENT_POLICY.md`, redigida na preparação da publicação na Play Console. Até lá, o conteúdo mínimo listado na [QA-24](OPEN_QUESTIONS.md#qa-24) orienta a especificação da moderação ([DP-054](PRODUCT_DECISIONS.md#questões-decididas)) | Moderação, criação, biblioteca |
| D-06 | Spike técnico: consistência de personagem, qualidade e custo por história, latência e estilo visual comum à biblioteca e às histórias geradas ([DP-056](PRODUCT_DECISIONS.md#questões-decididas)) | Validação de H-04, H-07, H-09, H-11; preços |
| D-07 | Infraestrutura: hospedagem do backend, banco, object storage, fila de processamento | Todo o produto |
| D-08 | Identidade visual e design system do Mundo de Contos | App, biblioteca, personagens |
| D-09 | Decisão das questões bloqueantes | Especificações do MVP |

## 10. Sequência sugerida de especificações (SDD)

A ordem é uma **proposta**: prioriza o que reduz risco cedo e o que tem menos dependências em aberto.

1. **Spike de geração** (D-06): não é funcionalidade; é investigação com relatório. Valida H-07 e H-09 antes de fechar preços.
2. **Modelo de direitos de acesso e créditos** (livro-razão, reserva, consumo, liberação, estorno) + ADR.
3. **Conta, perfis e barreira parental.**
4. **Catálogo e leitor.**
5. **Billing:** assinatura com teste e créditos, com validação no servidor.
6. **Personagens.**
7. **Criação de histórias:** pipeline assíncrono, moderação e estados.
8. **Minha coleção, Início e configurações.**
9. **Operação:** catálogo, configuração comercial e monitoramento de custo.
