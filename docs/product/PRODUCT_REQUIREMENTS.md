# Mundo de Contos — Requisitos de Produto

> **Status:** rascunho para aprovação · **Versão:** 0.1 · **Atualizado em:** 2026-10-31

Este documento descreve **o que** o produto deve fazer, não **como** será implementado. Cada requisito será detalhado em uma especificação própria (SDD) antes da implementação ([DP-008](PRODUCT_DECISIONS.md#plataforma-e-engenharia)).

**Colunas:**

- **Origem:** decisão (`DP`) que fundamenta o requisito, ou "Derivado" quando decorre logicamente de decisões aprovadas.
- **Escopo:** `MVP` ou `Futuro`.
- **Status:** `Aprovado` ou `Depende de QA-xx`.

---

## 1. Requisitos funcionais

### 1.1 Conta do responsável (RF-CON)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-CON-01 | O responsável cria uma conta, com login Google ou link mágico por e-mail, sem senha. A conta é obrigatória em todas as modalidades. | DP-003, DP-047 | MVP | Aprovado |
| RF-CON-02 | O responsável acessa a mesma conta em outro dispositivo Android e recupera os direitos de acesso, os créditos e as histórias criadas. | Derivado de DP-020, DP-021 | MVP | Aprovado |
| RF-CON-03 | O responsável pode encerrar a sessão. | Derivado | MVP | Aprovado |
| RF-CON-04 | O responsável pode excluir a conta e os dados associados, inclusive os dos perfis infantis, a partir do app. O app informa as consequências (por exemplo, a perda de histórias criadas e de créditos) e explica que a assinatura na Google Play deve ser cancelada à parte. | DP-037 | MVP | Aprovado. Prazos de retenção de registros fiscais e de compras definidos internamente ([DP-052](PRODUCT_DECISIONS.md#questões-decididas)) |
| RF-CON-05 | O responsável aceita os termos de uso e a política de privacidade antes de usar o produto. | DP-037, DP-052 | MVP | Aprovado. Documentos produzidos internamente |

### 1.2 Perfis infantis (RF-PER)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-PER-01 | O responsável cria um perfil infantil apenas com apelido (ou primeiro nome) e faixa etária. | DP-037, DP-044 | MVP | Aprovado |
| RF-PER-02 | O número de perfis respeita o limite da modalidade (Free: 1; Premium: 5), configurável. | DP-041 | MVP | Aprovado. Teste: 5; só créditos: 1 ([DP-057](PRODUCT_DECISIONS.md#questões-decididas)) |
| RF-PER-03 | O responsável edita e exclui perfis. | DP-037 | MVP | Aprovado |
| RF-PER-04 | O perfil ativo orienta as sugestões de conteúdo por faixa etária. | DP-031 | MVP | Depende de [QA-34](OPEN_QUESTIONS.md#qa-34) |
| RF-PER-05 | Perfis infantis não têm login, senha nem acesso próprio. | DP-035 | MVP | Aprovado |
| RF-PER-06 | O primeiro perfil criado é o perfil principal. Quando a assinatura termina, apenas ele permanece ativo. | DP-041 | MVP | Aprovado. Os demais perfis são arquivados e reativados quando a pessoa assina de novo ([DP-055](PRODUCT_DECISIONS.md#questões-decididas)). O principal pode ser trocado em Configurações ([DP-059](PRODUCT_DECISIONS.md#questões-decididas)) |

### 1.3 Biblioteca (RF-BIB)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-BIB-01 | O catálogo exibe as histórias autorais organizadas nas seis categorias aprovadas. | DP-029 | MVP | Aprovado |
| RF-BIB-02 | Cada história indica a faixa etária recomendada. | DP-031 | MVP | Aprovado |
| RF-BIB-03 | O responsável filtra o catálogo por categoria e por faixa etária. | DP-029, DP-031 | MVP | Aprovado |
| RF-BIB-04 | Dez histórias ficam disponíveis no Free; as demais exigem Premium (ou teste). | DP-013, DP-030 | MVP | Seleção depende de [QA-17](OPEN_QUESTIONS.md#qa-17) |
| RF-BIB-05 | Histórias indisponíveis na modalidade atual ficam visíveis com indicação discreta de bloqueio. Ao tocar nelas, o fluxo de assinatura só abre depois da barreira parental. | DP-035, Derivado | MVP | Aprovado |
| RF-BIB-06 | A visibilidade, a classificação e a inclusão de histórias no Free são alteradas sem publicar uma nova versão do app. | DP-024 | MVP | Aprovado |
| RF-BIB-07 | Compra avulsa não libera histórias Premium da biblioteca. | DP-018 | MVP | Aprovado |

### 1.4 Leitor (RF-LEI)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-LEI-01 | O leitor apresenta uma página por vez, com ilustração grande e texto legível. | DP-033 | MVP | Aprovado |
| RF-LEI-02 | A navegação entre páginas é simples (toque ou gesto de deslizar), com indicação de progresso. | DP-033 | MVP | Aprovado |
| RF-LEI-03 | O mesmo leitor atende histórias da biblioteca e histórias personalizadas. | DP-033, DP-034 | MVP | Aprovado |
| RF-LEI-04 | O leitor **não** exibe ofertas, preços, botões de compra nem atalhos para áreas adultas durante a leitura. | DP-012, DP-035 | MVP | Aprovado |
| RF-LEI-05 | Ao final da história, o responsável pode favoritar, reler ou voltar. | DP-013 | MVP | Aprovado |
| RF-LEI-06 | O leitor permite retomar a leitura na página em que parou. | Derivado | MVP | [Proposta] a aprovar |
| RF-LEI-07 | Leitura sem conexão para histórias já acessadas. | — | A definir | Depende de [QA-18](OPEN_QUESTIONS.md#qa-18) |
| RF-LEI-08 | Ajustes de leitura (tamanho de fonte, modo noturno para a hora de dormir). | — | A definir | Depende de [QA-29](OPEN_QUESTIONS.md#qa-29) |
| RF-LEI-09 | Narração em áudio. | DP-014 | Futuro | — |

### 1.5 Favoritos e Minha coleção (RF-COL)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-COL-01 | O responsável marca e desmarca histórias da biblioteca como favoritas. | DP-013 | MVP | Aprovado |
| RF-COL-02 | A aba Minha coleção reúne os favoritos e as histórias personalizadas criadas. | DP-014, DP-021, DP-032 | MVP | Organização depende de [QA-07](OPEN_QUESTIONS.md#qa-07) |
| RF-COL-03 | Histórias criadas permanecem acessíveis em qualquer modalidade, inclusive após o fim da assinatura. | DP-021 | MVP | Aprovado |
| RF-COL-04 | Comportamento dos favoritos de histórias Premium após o fim da assinatura. | DP-018 | MVP | Depende de [QA-08](OPEN_QUESTIONS.md#qa-08) |
| RF-COL-05 | Histórias criadas ficam associadas ao perfil infantil para o qual foram feitas. | Derivado | MVP | [Proposta] a aprovar |
| RF-COL-06 | O responsável pode excluir uma história criada. | DP-037 | MVP | [Proposta] a aprovar |
| RF-COL-07 | Exportação em PDF. | DP-014 | Futuro | — |

### 1.6 Personagens (RF-PERS)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-PERS-01 | O responsável escolhe um personagem ilustrado pré-criado como base. | DP-026 | MVP | Aprovado |
| RF-PERS-02 | O responsável personaliza tom de pele; tipo, textura e cor de cabelo; comprimento e penteado; características visuais; roupas e acessórios. | DP-026 | MVP | Lista de opções depende do trabalho de arte ([D-03](MVP_SCOPE.md#9-dependências)) e de [QA-28](OPEN_QUESTIONS.md#qa-28) |
| RF-PERS-03 | As opções são apresentadas de forma visual (amostras), sem rótulos que classifiquem pessoas em categorias étnicas ou raciais rígidas. | DP-027 | MVP | [Proposta] a aprovar |
| RF-PERS-04 | O personagem mantém aparência consistente em todas as páginas da história. | DP-028 | MVP | Viabilidade depende de [H-07](PRODUCT_DECISIONS.md#h-07) |
| RF-PERS-05 | O personagem configurado é salvo, associado ao perfil infantil e reutilizado em novas histórias. | DP-028, DP-046 | MVP | Aprovado |
| RF-PERS-06 | Nenhuma fotografia real é enviada, processada ou armazenada. | DP-025 | MVP | Aprovado |
| RF-PERS-07 | A personalização está disponível para quem tem direito de geração (teste, Premium ou créditos). | DP-014, DP-042 | MVP | Aprovado |
| RF-PERS-08 | Personagens secundários (irmãos, animais de estimação). | — | A definir | Depende de [QA-36](OPEN_QUESTIONS.md#qa-36) |

### 1.7 Criação de histórias personalizadas (RF-CRI)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-CRI-01 | A aba Criar permite que responsáveis com direito de geração (teste, Premium ou créditos) criem uma história personalizada. | DP-014, DP-017 | MVP | Aprovado |
| RF-CRI-02 | Usuários sem direito de geração veem a proposta da funcionalidade e as opções de teste ou de compra, sempre atrás da barreira parental. | DP-013, DP-035 | MVP | Aprovado |
| RF-CRI-03 | O responsável define o perfil infantil, o personagem e os parâmetros da história, apenas por opções guiadas (sem texto livre). | DP-026, DP-043 | MVP | Aprovado. A lista de opções será definida na especificação |
| RF-CRI-13 | O nome da criança não é enviado ao provedor de IA; o servidor o insere no texto após a geração. | DP-045 | MVP | Aprovado. Viabilidade confirmada no spike ([D-06](MVP_SCOPE.md#9-dependências)) |
| RF-CRI-14 | O responsável pode reportar uma história gerada, passando pela barreira parental. A história reportada sai da coleção até a revisão; se a denúncia proceder, o crédito é compensado. | DP-054 | MVP | Aprovado |
| RF-CRI-04 | Antes de confirmar, o app mostra o que será consumido (crédito ou franquia) e o saldo restante. | DP-016, DP-023 | MVP | Aprovado |
| RF-CRI-05 | A história gerada tem capa, introdução, cerca de 5 a 7 páginas e encerramento. A quantidade de páginas é configurável. | DP-034 | MVP | Aprovado |
| RF-CRI-06 | O texto e as imagens respeitam a faixa etária do perfil. | DP-031 | MVP | Aprovado |
| RF-CRI-07 | A geração é assíncrona. O responsável pode sair da tela e acompanhar o estado (na fila, gerando, pronta, falhou). | DP-010 | MVP | Forma de aviso depende de [QA-25](OPEN_QUESTIONS.md#qa-25) |
| RF-CRI-08 | Entradas e saídas passam por moderação de segurança infantil antes de a história ser entregue. | DP-037, P3 da visão | MVP | Aprovado ([DP-054](PRODUCT_DECISIONS.md#questões-decididas)). A política será redigida em `docs/content/CONTENT_POLICY.md` |
| RF-CRI-09 | Falha definitiva libera o crédito reservado e informa o responsável de forma clara e acolhedora. | DP-022 | MVP | Aprovado |
| RF-CRI-10 | A história concluída é salva automaticamente em Minha coleção. | DP-014, DP-021 | MVP | Aprovado |
| RF-CRI-11 | Regenerar ou editar uma história gerada. | — | A definir | Depende de [QA-15](OPEN_QUESTIONS.md#qa-15) |
| RF-CRI-12 | O limite de gerações do teste e a franquia do Premium são aplicados pelo servidor. | DP-015, DP-024 | MVP | Teste: 2 gerações ([DP-039](PRODUCT_DECISIONS.md#questões-decididas)). Franquia Premium: [QA-02](OPEN_QUESTIONS.md#qa-02) |

### 1.8 Monetização (RF-MON)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-MON-01 | A tela de assinatura informa preço, periodicidade, duração do teste, data de início da cobrança e como cancelar. | DP-016 | MVP | Aprovado |
| RF-MON-02 | O responsável assina o Premium com teste gratuito pelo Google Play Billing. | DP-010, DP-015 | MVP | Aprovado |
| RF-MON-03 | O responsável compra pacotes de créditos sem precisar assinar. | DP-017 | MVP | Aprovado |
| RF-MON-04 | Os pacotes exibidos e seus preços vêm de configuração e da loja, não de valores fixos no app. | DP-024 | MVP | Aprovado |
| RF-MON-05 | O responsável vê o saldo de créditos separado por origem (comprados, promocionais, assinatura). | DP-019 | MVP | [Proposta] a aprovar (exibir separado ou total) |
| RF-MON-06 | O responsável consulta o histórico de compras e de movimentações de créditos. | DP-023 | MVP | [Proposta] a aprovar (nível de detalhe visível ao usuário) |
| RF-MON-07 | O app oferece "restaurar compras" e atalho para gerenciar ou cancelar a assinatura na Google Play. | DP-016 | MVP | Aprovado |
| RF-MON-08 | Direitos e créditos só são concedidos após validação da compra no servidor, sem concessão duplicada. | DP-023, DP-036 | MVP | Aprovado |
| RF-MON-09 | Reembolsos e cancelamentos informados pela loja atualizam direitos e saldos. | DP-023 | MVP | Política de créditos consumidos depende de [QA-30](OPEN_QUESTIONS.md#qa-30) |
| RF-MON-10 | Fluxos de compra jamais são acionados a partir de telas usadas pela criança sem passar pela barreira parental. | DP-035 | MVP | Aprovado |
| RF-MON-11 | O consumo segue a ordem: promocionais → cota da assinatura → comprados (estes quando não há assinatura ativa ou quando a cota se esgota). | DP-050, DP-058 | MVP | Aprovado |

### 1.9 Controle parental (RF-PAR)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-PAR-01 | Compras, assinatura, configurações, gestão de perfis e conta ficam atrás de uma barreira parental. | DP-035 | MVP | Aprovado. Mecanismo: desafio simples por escrito, sem PIN ([DP-048](PRODUCT_DECISIONS.md#questões-decididas)) |
| RF-PAR-02 | A confirmação de consumo de crédito na aba Criar exige a barreira parental. | DP-035, Derivado | MVP | [Proposta] a aprovar |
| RF-PAR-03 | A barreira parental é acessível a adultos com deficiência e não depende só de leitura rápida ou coordenação motora fina. | Derivado | MVP | [Proposta] a aprovar |

### 1.10 Início e configurações (RF-INI, RF-CFG)

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-INI-01 | A tela Início apresenta sugestões de leitura para o perfil ativo e atalho para continuar a última leitura. | DP-032 | MVP | Aprovado |
| RF-INI-02 | A tela Início dá acesso ao perfil e às configurações (atrás da barreira parental). | DP-032, DP-035 | MVP | Aprovado |
| RF-INI-03 | A tela Início traz mensagens que incentivam a leitura compartilhada, sem incentivar o uso solitário da tela por bebês. | DP-005 | MVP | Aprovado |
| RF-CFG-01 | As configurações reúnem: conta, perfis, assinatura, créditos, privacidade, termos, suporte e exclusão de conta. | DP-016, DP-037 | MVP | Aprovado |

### 1.11 Operação do produto (RF-OPS)

Capacidades internas necessárias para operar o MVP. A forma de entrega (painel administrativo, scripts, configuração versionada) será decidida na especificação técnica; **não** se assume um painel administrativo completo.

| ID | Requisito | Origem | Escopo | Status |
| --- | --- | --- | --- | --- |
| RF-OPS-01 | Publicar, atualizar e despublicar histórias da biblioteca e seus metadados. | DP-029 | MVP | Aprovado |
| RF-OPS-02 | Alterar pacotes, limites e franquias com registro de quem alterou e quando. | DP-024 | MVP | Aprovado |
| RF-OPS-03 | Consultar o livro-razão de créditos de um usuário para suporte e auditoria. | DP-023 | MVP | Aprovado |
| RF-OPS-04 | Conceder créditos promocionais ou de compensação, com motivo registrado. | DP-019 | MVP | Origens dependem de [QA-10](OPEN_QUESTIONS.md#qa-10) |
| RF-OPS-05 | Acompanhar o custo de IA por período e por história, com alertas de limite. | P9 da visão | MVP | Teto depende de [QA-33](OPEN_QUESTIONS.md#qa-33) |

---

## 2. Requisitos não funcionais

| ID | Categoria | Requisito |
| --- | --- | --- |
| <a id="rnf-priv"></a>**RNF-PRIV-01** | Privacidade | Coletar sobre a criança apenas os dados estritamente necessários à funcionalidade, com finalidade documentada para cada dado. |
| **RNF-PRIV-02** | Privacidade | Dados de crianças não são usados para publicidade, perfilamento comercial nem treinamento de modelos. Contratos com provedores de IA devem garantir isso ([QA-23](OPEN_QUESTIONS.md#qa-23)). |
| **RNF-PRIV-03** | Privacidade | Dados enviados a provedores de IA são minimizados: sem o nome da criança ([DP-045](PRODUCT_DECISIONS.md#questões-decididas)) e sem identificadores da conta. |
| **RNF-PRIV-04** | Privacidade | Bibliotecas de terceiros (analytics, monitoramento de erros) passam por avaliação de privacidade antes de serem incluídas e precisam ser compatíveis com a política de Famílias da Google Play ([DP-051](PRODUCT_DECISIONS.md#questões-decididas), [QA-26](OPEN_QUESTIONS.md#qa-26)). |
| <a id="rnf-sec"></a>**RNF-SEC-01** | Segurança | Nenhuma chave de provedor de IA ou segredo de servidor é embarcado no app ([DP-036](PRODUCT_DECISIONS.md#segurança-e-privacidade)). |
| **RNF-SEC-02** | Segurança | Toda comunicação entre app e backend é criptografada em trânsito; dados sensíveis são criptografados em repouso. |
| **RNF-SEC-03** | Segurança | Imagens e histórias privadas só são acessíveis ao responsável dono, por meio de URLs com controle de acesso ou expiração. |
| **RNF-SEC-04** | Segurança | O backend aplica limites de requisição e de geração por conta para evitar abuso. |
| <a id="rnf-cost"></a>**RNF-COST-01** | Custo | Toda operação com custo variável (IA, armazenamento, transferência) é medida e atribuída a uma história ou a um usuário. |
| **RNF-COST-02** | Custo | As retentativas de geração têm teto configurável. |
| **RNF-COST-03** | Custo | Há alertas para quando o custo agregado ultrapassar um limite configurável. |
| **RNF-AUD-01** | Auditabilidade | Movimentações de créditos são registradas em livro-razão imutável; o saldo é reconstituível a partir dos lançamentos. |
| **RNF-AUD-02** | Auditabilidade | Mudanças de configuração comercial são registradas com autor, data e valor anterior. |
| **RNF-CONF-01** | Configurabilidade | Preços, pacotes, franquias, limites e quantidade de perfis são alteráveis sem mudança no código de domínio ([DP-024](PRODUCT_DECISIONS.md#monetização)). |
| **RNF-REL-01** | Confiabilidade | O processamento de compras é idempotente: notificações repetidas da loja não duplicam créditos. |
| **RNF-REL-02** | Confiabilidade | A geração tolera falhas de provedores, com retentativa e liberação do crédito em caso de falha definitiva. |
| **RNF-ACC-01** | Acessibilidade | O texto do leitor tem contraste adequado e tamanho legível para leitura em voz alta pelo adulto; os elementos interativos têm área de toque adequada para o público. |
| **RNF-ACC-02** | Acessibilidade | Telas adultas são compatíveis com leitores de tela do Android (TalkBack). |
| **RNF-PERF-01** | Desempenho | As páginas do leitor carregam sem espera perceptível na troca de página, com pré-carregamento da página seguinte. Metas numéricas serão definidas na especificação do leitor. |
| **RNF-PERF-02** | Desempenho | O app funciona de forma aceitável em aparelhos Android intermediários. Os aparelhos de referência serão definidos na especificação técnica. |
| **RNF-PORT-01** | Portabilidade | Regras de negócio e direitos de acesso ficam no backend, de forma independente da loja, para permitir a futura versão iOS ([DP-007](PRODUCT_DECISIONS.md#plataforma-e-engenharia)). |
| **RNF-I18N-01** | Idioma | Textos de interface ficam externalizados (não fixos no código), mesmo com o MVP apenas em português brasileiro. |
| **RNF-OBS-01** | Observabilidade | Erros, latência de geração, taxa de falha e custo são monitorados, sem registrar conteúdo pessoal desnecessário nos logs. |
| **RNF-TEST-01** | Testabilidade | Regras de créditos, direitos de acesso e limites têm testes automatizados derivados das especificações. |
