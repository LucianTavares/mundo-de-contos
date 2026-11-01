# Mundo de Contos — Registro de Decisões de Produto

> **Status:** rascunho para aprovação · **Versão:** 0.1 · **Atualizado em:** 2026-10-31
> **Fonte:** Pacote de Prompts de Engenharia — Prompt 1 (Product Foundation)

Este é o registro oficial das decisões de produto. Os demais documentos referenciam decisões por ID (`DP-xxx`) e hipóteses por ID (`H-xx`).

## Como usar este registro

- **Decisão aprovada (`DP`)**: definida pelo responsável pelo produto. Só muda com uma nova decisão registrada aqui, que referencie a anterior como substituída.
- **Hipótese (`H`)**: premissa assumida para planejamento, que precisa de validação com dados, pesquisa ou experimento.
- **Questão em aberto (`QA`)**: ainda não decidida. Fica em [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md) e, quando decidida, vira uma `DP` aqui.
- **Decisão técnica**: registrada como ADR (ver [Candidatos a ADR](#candidatos-a-adr)), não neste documento.

Formato de uma nova entrada:

```text
### DP-NNN — Título
- Data: AAAA-MM-DD
- Decisão: ...
- Motivo: ...
- Consequências: ...
- Origem: (documento, reunião ou QA que originou)
- Substitui: (DP anterior, se houver)
```

---

## 1. Decisões aprovadas

As decisões **DP-001 a DP-038** têm data de registro **2026-10-31** e origem no **Prompt 1 (Product Foundation)**. A partir da DP-039, as decisões vêm das respostas às questões em aberto e indicam a questão de origem.

### Identidade e posicionamento

| ID | Decisão |
| --- | --- |
| **DP-001** | O nome oficial do produto é **Mundo de Contos**. O identificador técnico é `mundo-de-contos`. Nomes considerados anteriormente não devem ser usados. |
| **DP-002** | O identificador técnico **não** define o `applicationId` Android, que será definido e validado antes da publicação ([QA-32](OPEN_QUESTIONS.md#qa-32)). |
| **DP-003** | Público: pais, mães e responsáveis por crianças de **0 a 6 anos**. O produto é administrado por adultos. |
| **DP-004** | Posicionamento: **biblioteca digital infantil ilustrada combinada com criação de histórias personalizadas**. O produto não deve parecer uma interface genérica de IA. |
| **DP-005** | O produto não é posicionado como substituto da leitura presencial nem como estímulo para que bebês usem telas sozinhos. |
| **DP-006** | Idioma principal: **português brasileiro**. |

### Plataforma e engenharia

| ID | Decisão |
| --- | --- |
| **DP-007** | Plataforma inicial: **Android**. A arquitetura deve estar preparada para uma futura versão iOS. |
| **DP-008** | Abordagem de engenharia: **Harness Engineering + Spec-Driven Development**. Nenhuma funcionalidade é implementada antes da aprovação da sua especificação. |
| **DP-009** | Organização em **monorepo com aplicações independentes**. Nada de microsserviços sem necessidade concreta. Nenhuma dependência sem justificativa. |
| **DP-010** | Tecnologia pretendida: React Native com Expo e TypeScript (app); NestJS com TypeScript (backend); PostgreSQL; object storage; processamento assíncrono para geração de histórias e imagens; Google Play Billing. *A direção está aprovada; a formalização e os detalhes serão registrados em ADRs.* |

### Monetização

| ID | Decisão |
| --- | --- |
| **DP-011** | Três modalidades: **Free**, **Premium** (assinatura) e **compra avulsa de créditos**. Detalhes em [BUSINESS_MODEL.md](BUSINESS_MODEL.md). |
| **DP-012** | **Nenhuma modalidade exibe publicidade.** |
| **DP-013** | **Free** inclui: 10 histórias selecionadas da biblioteca, leitura ilustrada, favoritos e um perfil infantil. **Não** inclui geração de histórias por IA. |
| **DP-014** | **Premium** inclui: biblioteca completa, geração de histórias personalizadas com IA, personagens personalizados, mais perfis infantis e coleção pessoal. PDF e narração são evoluções futuras. |
| **DP-015** | O Premium oferece **teste gratuito de 7 dias**, com acesso aos recursos Premium e **limite de gerações de IA** para controle de custo (quantidade em [QA-01](OPEN_QUESTIONS.md#qa-01)). |
| **DP-016** | A assinatura é apresentada com clareza: preço, periodicidade, início da cobrança e condições de cancelamento. |
| **DP-017** | Usuários **sem assinatura** podem comprar pacotes de créditos para gerar histórias personalizadas. A assinatura não é obrigatória para comprar histórias. |
| **DP-018** | Compra avulsa **não** concede acesso à biblioteca Premium completa. |
| **DP-019** | Créditos **comprados**, **promocionais** e **da assinatura** são registrados separadamente. |
| **DP-020** | Créditos comprados continuam disponíveis após o cancelamento ou o término da assinatura. |
| **DP-021** | Histórias já criadas permanecem acessíveis ao usuário, independentemente da modalidade atual. |
| **DP-022** | Falha na geração **não consome definitivamente** um crédito. |
| **DP-023** | Compras e créditos têm **histórico auditável**. |
| **DP-024** | Preços, pacotes e franquias são **configuráveis sem alterar o código de domínio**, e o sistema deve suportar mudanças futuras nesses valores. |

### Conteúdo e personagens

| ID | Decisão |
| --- | --- |
| **DP-025** | **Sem fotografias reais de crianças no MVP.** |
| **DP-026** | O responsável seleciona **personagens ilustrados pré-criados** e personaliza: tom de pele; tipo, textura e cor de cabelo; comprimento e penteado; características visuais; roupas e acessórios. |
| **DP-027** | A personalização representa a diversidade com respeito, sem reduzir pessoas a categorias rígidas. |
| **DP-028** | O personagem mantém **consistência visual** em todas as páginas da história. |
| **DP-029** | A biblioteca inicial é composta por histórias **autorais**, organizadas em seis categorias: Animais e natureza; Hora de dormir; Emoções e valores; Aventuras; Pequenas conquistas e autonomia; Família e carinho. A quantidade planejada é de aproximadamente 30 (ver [H-05](#h-05)). |
| **DP-030** | **Dez** histórias da biblioteca são selecionadas para o plano gratuito (critério em [QA-17](OPEN_QUESTIONS.md#qa-17)). |
| **DP-031** | O conteúdo é organizado em três faixas etárias: **0 a 2**, **2 a 4** e **4 a 6 anos**, com as características descritas em [PRODUCT_VISION.md](PRODUCT_VISION.md#7-faixas-etárias-e-diretrizes-editoriais). |

### Experiência

| ID | Decisão |
| --- | --- |
| **DP-032** | Navegação inferior com quatro áreas: **Início**, **Biblioteca**, **Criar** e **Minha coleção**. Perfil e configurações ficam acessíveis pela tela Início. |
| **DP-033** | O leitor apresenta **uma página por vez** no celular, com ilustração grande, texto legível e navegação simples. |
| **DP-034** | A história personalizada tem **capa, introdução, aproximadamente 5 a 7 páginas de história e encerramento**. A quantidade de páginas pode ser ajustada conforme custo e qualidade (ver [H-04](#h-04)). |

### Segurança e privacidade

| ID | Decisão |
| --- | --- |
| **DP-035** | A criança **não** gerencia compras e **não** tem acesso independente a compras, configurações ou gerenciamento de conta. |
| **DP-036** | Chaves de provedores de IA **nunca** ficam no aplicativo. Toda chamada a provedores passa pelo backend. |
| **DP-037** | Não armazenar dados infantis desnecessários. **Privacidade desde a concepção.** |
| **DP-038** | Funcionalidades futuras **não** fazem parte do MVP, salvo decisão explícita registrada aqui. |

### Questões decididas

Registradas em 2026-10-31 (DP-039 a DP-056) e em 2026-11-01 (DP-057 a DP-059).

| ID | Decisão | Origem |
| --- | --- | --- |
| **DP-039** | O teste gratuito do Premium permite **2 gerações** de histórias personalizadas. O valor é configurável ([DP-024](#monetização)). | [QA-01](OPEN_QUESTIONS.md#qa-01) |
| **DP-040** | Créditos **comprados não expiram**. | [QA-04](OPEN_QUESTIONS.md#qa-04) |
| **DP-041** | Toda conta tem um **perfil infantil principal**, criado no primeiro acesso. **Free:** 1 perfil (o principal). **Premium:** até **5 perfis**, incluindo o principal. Quando a assinatura termina, **apenas o perfil principal permanece ativo** (tratamento dos demais perfis na [DP-055](#questões-decididas)). Os limites são configuráveis. | [QA-05](OPEN_QUESTIONS.md#qa-05) |
| **DP-042** | Quem compra créditos sem assinar tem a **mesma personalização de personagem** do Premium. | [QA-06](OPEN_QUESTIONS.md#qa-06) |
| **DP-043** | No MVP, a história é criada por meio de **opções guiadas**, sem campo de texto livre. | [QA-11](OPEN_QUESTIONS.md#qa-11) |
| **DP-044** | O perfil infantil armazena **apenas um apelido (ou primeiro nome) e a faixa etária** (0 a 2, 2 a 4, 4 a 6). Não são coletados data de nascimento, foto nem sobrenome. | [QA-14](OPEN_QUESTIONS.md#qa-14) |
| **DP-045** | O nome da criança **não é enviado ao provedor de IA**: o texto é gerado com um marcador, que o servidor substitui pelo nome depois. A viabilidade técnica será confirmada no spike de geração ([D-06](MVP_SCOPE.md#9-dependências)); se houver limitação, a decisão volta para revisão. | [QA-13](OPEN_QUESTIONS.md#qa-13) |
| **DP-046** | O personagem configurado é **salvo, associado ao perfil infantil e reutilizado** nas histórias seguintes. | [QA-35](OPEN_QUESTIONS.md#qa-35) |
| **DP-047** | Autenticação por **login com Google** ou **link mágico por e-mail**, sem senha. A conta é **obrigatória em todas as modalidades**, inclusive no Free. Os detalhes técnicos ficam em ADR. | [QA-19](OPEN_QUESTIONS.md#qa-19) |
| **DP-048** | A barreira parental é um **desafio simples por escrito**, sem PIN no MVP, acessível a adultos com deficiência. | [QA-20](OPEN_QUESTIONS.md#qa-20) |
| **DP-049** | As **30 primeiras histórias** da biblioteca são escritas pela pessoa idealizadora do produto, a partir da vivência com a filha. As ilustrações seguem a [DP-056](#questões-decididas). | [QA-16](OPEN_QUESTIONS.md#qa-16) |
| **DP-050** | **Ordem de consumo de créditos**, com saldos separados por contexto: (1) créditos **promocionais**; (2) **cota da assinatura** (teste ou Premium); (3) créditos **comprados**, usados apenas quando não há assinatura ativa (nunca assinou, cancelou ou não renovou). Quando a cota de uma assinatura ativa se esgota, vale a [DP-058](#questões-decididas). | [QA-03](OPEN_QUESTIONS.md#qa-03) |
| **DP-051** | Na Google Play, o app é declarado com **público misto** (adultos + faixas infantis até 6 anos) e segue a **política de Famílias desde o início**. SDKs de terceiros só entram se forem compatíveis com essa política, e identificadores de publicidade não são coletados. A equipe mantém uma lista de SDKs aprovados. | [QA-21](OPEN_QUESTIONS.md#qa-21) |
| **DP-052** | No MVP, a **conformidade legal e de privacidade é conduzida internamente**, sem assessoria jurídica contratada. A contratação será reavaliada quando houver escala e receita. | [QA-22](OPEN_QUESTIONS.md#qa-22) |
| **DP-053** | O app é publicado por **pessoa jurídica** (CNPJ), titular da conta de desenvolvedor e do perfil de pagamentos e controladora dos dados pessoais. | [QA-22](OPEN_QUESTIONS.md#qa-22) |
| **DP-054** | **Segurança de conteúdo em camadas**: prevenção pelo desenho (opções guiadas e validação do apelido); política editorial como regra de geração; histórias da biblioteca como referência de voz; verificação automática de texto e imagem antes da entrega (na dúvida, a história não é entregue e o crédito volta); revisão humana por amostragem e de 100% das denúncias; botão "Reportar história" atrás da barreira parental. A política editorial fica em `docs/content/CONTENT_POLICY.md` e vale também para a biblioteca. | [QA-24](OPEN_QUESTIONS.md#qa-24) |
| **DP-055** | Ao fim da assinatura, os perfis além do principal são **arquivados**, nunca excluídos automaticamente. As histórias criadas para eles continuam legíveis ([DP-021](#monetização)). Quando a pessoa assina de novo, os perfis voltam a ficar ativos, com seus personagens. | [QA-38](OPEN_QUESTIONS.md#qa-38) |
| **DP-056** | As **ilustrações da biblioteca e os personagens base são gerados por IA**, com direção criativa e curadoria da pessoa idealizadora do produto. | [QA-39](OPEN_QUESTIONS.md#qa-39) |
| **DP-057** | Limites de perfis por situação: **teste gratuito, 5**; **Premium, 5**; **quem só compra créditos, 1** (o principal). Complementa a [DP-041](#questões-decididas). | [QA-37](OPEN_QUESTIONS.md#qa-37) |
| **DP-058** | Quando a cota de uma assinatura ativa (teste ou Premium) se esgota, os **créditos comprados podem ser usados**, e eles continuam sendo os últimos na ordem de consumo ([DP-050](#questões-decididas)). Assinantes podem comprar pacotes avulsos. | [QA-40](OPEN_QUESTIONS.md#qa-40) |
| **DP-059** | O responsável pode **trocar qual é o perfil principal** em Configurações, atrás da barreira parental. | [QA-38](OPEN_QUESTIONS.md#qa-38) |

---

## 2. Hipóteses a validar

| ID | Hipótese | Como validar | Impacto se falsa |
| --- | --- | --- | --- |
| <a id="h-01"></a>**H-01** | A assinatura mensal de **R$ 14,90** é aceita pelo público e sustenta a operação. | Teste de preço; análise de conversão; cálculo de economia unitária com custo real por história. | Revisar preço, franquia ou estrutura do Premium. |
| <a id="h-02"></a>**H-02** | Pacotes de créditos de **R$ 3,90 (1)**, **R$ 9,90 (3)** e **R$ 14,90 (5)** são atrativos e têm margem positiva. | Medir o custo por história ([H-09](#h-09)); acompanhar a conversão por pacote. | Reprecificar os pacotes (configurável, [DP-024](#monetização)). |
| <a id="h-03"></a>**H-03** | Um teste gratuito de **7 dias** com gerações limitadas é suficiente para demonstrar valor e converter. | Taxa de conversão do teste; uso de gerações durante o teste. | Ajustar a duração do teste ou o limite de gerações. |
| <a id="h-04"></a>**H-04** | **5 a 7 páginas** equilibram qualidade narrativa e custo de geração. | Spike de geração; avaliação qualitativa com responsáveis; custo medido. | Ajustar a quantidade de páginas por faixa etária. |
| <a id="h-05"></a>**H-05** | **Cerca de 30 histórias** são suficientes para sustentar o valor percebido da biblioteca Premium no lançamento. | Consumo da biblioteca por assinante; pesquisa de satisfação. | Ampliar o catálogo ou definir uma cadência de novos lançamentos. |
| <a id="h-06"></a>**H-06** | **10 histórias gratuitas** geram engajamento sem canibalizar a assinatura. | Retenção do Free; conversão de Free para teste. | Ajustar a quantidade ou a seleção do Free. |
| <a id="h-07"></a>**H-07** | É tecnicamente viável manter a **consistência visual** do personagem entre as páginas com custo e latência compatíveis. | Spike técnico com provedores de imagem ([D-06](MVP_SCOPE.md#9-dependências)). | Rever a abordagem de ilustração (por exemplo, composição sobre arte pré-produzida) ou o escopo da personalização. |
| <a id="h-08"></a>**H-08** | Responsáveis valorizam a criança como protagonista o suficiente para pagar por isso. | Conversão para teste via aba Criar; compra de créditos; pesquisa. | Reposicionar o Premium com foco na biblioteca. |
| <a id="h-09"></a>**H-09** | O custo médio de uma história gerada (texto + imagens + moderação + infraestrutura) cabe na margem dos preços planejados. | Medir no spike e em produção. | Reduzir páginas e resolução, trocar de provedor ou reprecificar. |
| <a id="h-10"></a>**H-10** | Personagens ilustrados personalizáveis (sem fotos) bastam para a criança se reconhecer na história. | Testes qualitativos com famílias. | Ampliar as opções de personalização; reavaliar o uso de fotos em fase futura, com análise de privacidade. |
| <a id="h-11"></a>**H-11** | Os responsáveis aceitam aguardar a geração assíncrona da história (minutos, não segundos). | Medir o abandono durante a geração; pesquisa. | Otimizar o pipeline; gerar o texto primeiro e as imagens progressivamente. |

---

## 3. Observações sobre as decisões

Pontos identificados na análise das decisões, que **não alteram** nenhuma delas, mas precisam de atenção:

1. **Personagens personalizados × compra avulsa.** A [DP-014](#monetização) lista "personagens personalizados" como recurso Premium, mas a [DP-017](#monetização) permite que não assinantes gerem histórias, o que exige um personagem. É preciso definir o que o comprador avulso pode personalizar ([QA-06](OPEN_QUESTIONS.md#qa-06)). **Resolvida:** [DP-042](#questões-decididas).
2. **Favoritos × coleção pessoal.** O Free tem "favoritos" e o Premium tem "coleção pessoal", enquanto a aba "Minha coleção" existe para todos. É preciso definir o conteúdo da aba por modalidade ([QA-07](OPEN_QUESTIONS.md#qa-07)).
3. **Pacote de 5 créditos = preço da assinatura.** O pacote de 5 histórias (R$ 14,90) custa o mesmo que um mês de Premium. Isso só funciona como incentivo à assinatura se a franquia mensal do Premium for comparável ou superior ([QA-02](OPEN_QUESTIONS.md#qa-02)). A direção atual (5 a 10 histórias por mês) atende a essa condição.
4. **"Mais perfis infantis"** no Premium não tem quantidade definida ([QA-05](OPEN_QUESTIONS.md#qa-05)). **Resolvida:** [DP-041](#questões-decididas) (até 5 perfis).
5. **Perfil principal × histórias criadas.** A [DP-041](#questões-decididas) mantém ativo apenas o perfil principal após o fim da assinatura, mas a [DP-021](#monetização) garante o acesso a todas as histórias criadas, inclusive as feitas para os outros perfis. Ver [QA-38](OPEN_QUESTIONS.md#qa-38). **Resolvida:** [DP-055](#questões-decididas).

---

## Candidatos a ADR

Decisões técnicas a registrar em `docs/adr/` na fase de arquitetura. **Nenhuma está decidida neste documento**; a lista serve apenas como insumo.

| Tema | Motivação |
| --- | --- |
| Estrutura do monorepo e ferramentas de build | [DP-009](#plataforma-e-engenharia) |
| Stack do app (Expo/React Native) e estratégia para iOS | [DP-007](#plataforma-e-engenharia), [DP-010](#plataforma-e-engenharia) |
| Stack do backend (NestJS) e modelo de módulos | [DP-010](#plataforma-e-engenharia) |
| Processamento assíncrono (fila, workers, retentativas) | Geração de histórias e imagens |
| Modelo de créditos (livro-razão imutável, reserva, confirmação, liberação) | [DP-019](#monetização) a [DP-023](#monetização) |
| Integração com o Google Play Billing e validação de compras no servidor | [DP-011](#monetização), [DP-017](#monetização) |
| Configuração de preços, pacotes, franquias e limites | [DP-024](#monetização) |
| Provedores de IA (texto e imagem) e camada de abstração | [QA-23](OPEN_QUESTIONS.md#qa-23), [H-07](#h-07) |
| Estratégia de consistência visual do personagem | [DP-028](#conteúdo-e-personagens) |
| Moderação de conteúdo gerado | [DP-054](#questões-decididas) |
| Autenticação (Google e link mágico por e-mail) | [DP-047](#questões-decididas) |
| Substituição do nome da criança por marcador na geração | [DP-045](#questões-decididas) |
| Armazenamento e entrega de imagens (object storage e CDN) | Leitor e biblioteca |
| Observabilidade e controle de custos | [RNF-COST](PRODUCT_REQUIREMENTS.md#rnf-cost) |
