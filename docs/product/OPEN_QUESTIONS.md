# Mundo de Contos — Questões em Aberto

> **Status:** rascunho para aprovação · **Versão:** 0.1 · **Atualizado em:** 2026-10-31

Questões que precisam de decisão. Cada questão traz contexto, opções e uma **recomendação**, que **não** é decisão. Quando decidida, a questão recebe o status "Decidida → DP-xxx" e a decisão é registrada em [PRODUCT_DECISIONS.md](PRODUCT_DECISIONS.md).

**Prioridade:**

- **Bloqueante:** impede a especificação de uma funcionalidade do MVP.
- **Antes do lançamento:** precisa estar decidida antes da publicação, mas não bloqueia o início das especificações.
- **Pós-MVP:** pode aguardar.
- **✅ Decidida:** registrada em [PRODUCT_DECISIONS.md](PRODUCT_DECISIONS.md#questões-decididas). A seção da questão é mantida como histórico.

## Resumo

| ID | Questão | Prioridade | Responsável sugerido |
| --- | --- | --- | --- |
| QA-01 | Limite de gerações no teste gratuito | ✅ Decidida → DP-039 | Produto + Finanças |
| QA-02 | Franquia mensal de gerações no Premium | Antes do lançamento (direção: 5 a 10 por mês) | Produto + Finanças |
| QA-03 | Ordem de consumo de créditos | ✅ Decidida → DP-050 (pendência em QA-40) | Produto |
| QA-04 | Expiração de créditos | ✅ Decidida → DP-040 | Produto + Jurídico |
| QA-05 | Número de perfis por modalidade e regra para excedentes | ✅ Decidida → DP-041 (pendências em QA-37 e QA-38) | Produto |
| QA-06 | Personalização de personagem para quem não assina | ✅ Decidida → DP-042 | Produto |
| QA-07 | Organização de Minha coleção (favoritos × coleção pessoal) | Bloqueante | Produto + Design |
| QA-08 | Favoritos de histórias Premium após o fim da assinatura | Antes do lançamento | Produto |
| QA-09 | Plano anual ou outras periodicidades | Pós-MVP | Produto + Finanças |
| QA-10 | Origens de créditos promocionais no MVP | Antes do lançamento | Produto |
| QA-11 | Entradas do fluxo de criação | ✅ Decidida → DP-043 | Produto + Conteúdo |
| QA-12 | Gênero gramatical do protagonista | Bloqueante | Produto + Conteúdo |
| QA-13 | Uso do nome da criança e envio ao provedor de IA | ✅ Decidida → DP-045 | Produto + Jurídico |
| QA-14 | Dados do perfil infantil | ✅ Decidida → DP-044 | Produto + Jurídico |
| QA-15 | Regenerar ou editar uma história gerada | Antes do lançamento | Produto |
| QA-16 | Produção da biblioteca e do estilo visual | ✅ Decidida → DP-049, DP-056 | Produto + Conteúdo |
| QA-17 | Critério de seleção das 10 histórias gratuitas | Antes do lançamento | Produto + Conteúdo |
| QA-18 | Leitura sem conexão | Antes do lançamento | Produto |
| QA-19 | Autenticação e obrigatoriedade de conta | ✅ Decidida → DP-047 | Produto + Engenharia |
| QA-20 | Mecanismo da barreira parental | ✅ Decidida → DP-048 | Produto + Design |
| QA-21 | Público-alvo declarado na Google Play | ✅ Decidida → DP-051 | Produto |
| QA-22 | Conformidade legal e documentos jurídicos | ✅ Decidida → DP-052, DP-053 (execução interna) | Produto |
| QA-23 | Provedores de IA e garantias de privacidade | Bloqueante | Engenharia + Jurídico |
| QA-24 | Política de conteúdo e moderação | ✅ Decidida → DP-054 | Produto + Conteúdo |
| QA-25 | Aviso de história pronta | Antes do lançamento | Produto |
| QA-26 | Analytics e monitoramento | Antes do lançamento | Produto + Engenharia |
| QA-27 | Compartilhamento de histórias | Pós-MVP | Produto |
| QA-28 | Representação de deficiências e acessórios assistivos | Antes do lançamento | Produto + Conteúdo |
| QA-29 | Ajustes de leitura (fonte, modo noturno) | Antes do lançamento | Produto + Design |
| QA-30 | Reembolso de créditos já consumidos | Antes do lançamento | Produto + Jurídico |
| QA-31 | Tributação e obrigações fiscais | Antes do lançamento | Finanças + Jurídico |
| QA-32 | `applicationId` definitivo e conta de publicação | Antes do lançamento | Engenharia |
| QA-33 | Teto de custo de IA e alertas | Antes do lançamento | Produto + Finanças |
| QA-34 | Faixa etária do perfil filtra a biblioteca ou só sugere | Antes do lançamento | Produto |
| QA-35 | Personagem salvo e reutilizável | ✅ Decidida → DP-046 | Produto |
| QA-36 | Personagens secundários | Pós-MVP | Produto |
| QA-37 | Quantidade de perfis no teste gratuito e para quem só compra créditos | ✅ Decidida → DP-057 | Produto |
| QA-38 | Perfis além do principal quando a assinatura termina | ✅ Decidida → DP-055, DP-059 | Produto |
| QA-39 | Ilustração da biblioteca e estilo visual | ✅ Decidida → DP-056 | Produto + Conteúdo |
| QA-40 | Créditos comprados quando a cota do Premium ativo acaba | ✅ Decidida → DP-058 | Produto |

---

## Monetização e créditos

### <a id="qa-01"></a>QA-01 — Limite de gerações no teste gratuito

- **Status:** ✅ Decidida em 2026-10-31: 2 gerações → [DP-039](PRODUCT_DECISIONS.md#questões-decididas).
- **Contexto:** [DP-015](PRODUCT_DECISIONS.md#monetização) define que existe limite, mas não a quantidade.
- **Opções:** 1 história; 2 a 3 histórias; definir após o spike de custo.
- **Recomendação:** começar com um número pequeno (por exemplo, 2) e configurável. Fechar o valor após medir o `CMH`.
- **Impacto:** custo de aquisição; percepção de valor do teste.

### <a id="qa-02"></a>QA-02 — Franquia mensal de gerações no Premium

- **Status:** em aberto. A direção indicada é de 5 a 10 histórias por mês; o valor será fechado após a análise de custos (spike [D-06](MVP_SCOPE.md#9-dependências)). Não bloqueia especificações, porque o valor é configurável ([DP-024](PRODUCT_DECISIONS.md#monetização)), mas precisa estar definido antes do lançamento.
- **Contexto:** a [DP-024](PRODUCT_DECISIONS.md#monetização) menciona "franquias", mas não há valor definido. O pacote de 5 créditos custa o mesmo que um mês de Premium.
- **Opções:** (a) ilimitado com limite antiabuso; (b) N histórias por mês; (c) N por mês com acúmulo limitado.
- **Recomendação:** (b), com N configurável e definido após o spike. A geração ilimitada expõe a margem ao risco R-01. Para que a assinatura seja mais vantajosa que o pacote de 5, N deveria ser comparável ou superior a 5, desde que o custo permita.
- **Também decidir:** se a franquia não usada acumula para o mês seguinte (recomendação: não).

### <a id="qa-03"></a>QA-03 — Ordem de consumo de créditos

- **Status:** ✅ Decidida em 2026-10-31 → [DP-050](PRODUCT_DECISIONS.md#questões-decididas): promocionais → cota da assinatura → comprados (estes só sem assinatura ativa). Pendência em [QA-40](#qa-40).
- **Contexto:** existem três origens de crédito ([DP-019](PRODUCT_DECISIONS.md#monetização)):
  - **da assinatura**: a cota que vem com o teste (2 gerações) ou com o Premium (N por mês, [QA-02](#qa-02)); vale só dentro do período;
  - **comprados**: pacotes avulsos pagos pelo responsável; nunca expiram ([DP-040](PRODUCT_DECISIONS.md#questões-decididas));
  - **promocionais**: concedidos pela empresa, por exemplo como compensação pelo suporte ([QA-10](#qa-10)).

  Um mesmo responsável pode ter mais de um tipo ao mesmo tempo. Exemplo: comprou 5 créditos avulsos, depois assinou o Premium e recebeu a cota do mês. Ao criar uma história, o sistema precisa saber **qual saldo diminui**.
- **Por que importa:** se os créditos comprados fossem gastos primeiro, a cota do mês expiraria sem uso e o cliente perderia o que pagou.
- **Recomendação:** consumir primeiro o que expira antes: **cota da assinatura → promocionais → comprados**. Os créditos comprados ficam guardados para quando a cota acabar ou a assinatura terminar.
- **Também decidir:** se assinantes podem comprar pacotes avulsos quando a cota acaba. Recomendação: sim.

### <a id="qa-04"></a>QA-04 — Expiração de créditos

- **Status:** ✅ Decidida em 2026-10-31: créditos comprados não expiram → [DP-040](PRODUCT_DECISIONS.md#questões-decididas). A validade de créditos promocionais segue em aberto.
- **Contexto:** a [DP-020](PRODUCT_DECISIONS.md#monetização) garante que créditos comprados sobrevivem ao fim da assinatura, mas não fala em prazo.
- **Recomendação:** créditos **comprados não expiram** (mais simples e mais justo; reduz risco jurídico). Créditos **promocionais** podem ter validade informada na concessão. Validar com o jurídico.

### <a id="qa-05"></a>QA-05 — Número de perfis por modalidade e regra para excedentes

- **Status:** ✅ Decidida em 2026-10-31 → [DP-041](PRODUCT_DECISIONS.md#questões-decididas): perfil principal; Free 1; Premium 5; ao fim da assinatura, só o principal fica ativo. Pendências em [QA-37](#qa-37) e [QA-38](#qa-38).
- **Contexto:** Free tem 1 perfil; o Premium tem "mais perfis", sem número definido. A situação do comprador avulso e do ex-assinante também não está definida.
- **Recomendação:** Premium com limite configurável (por exemplo, 4). Avulso igual ao Free. Para o ex-assinante, manter os perfis excedentes e suas histórias criadas **visíveis**, mas permitir criar histórias novas apenas para um perfil escolhido. **Nunca excluir dados automaticamente.**

### <a id="qa-06"></a>QA-06 — Personalização de personagem para quem não assina

- **Status:** ✅ Decidida em 2026-10-31: personalização completa → [DP-042](PRODUCT_DECISIONS.md#questões-decididas).
- **Contexto:** a [DP-014](PRODUCT_DECISIONS.md#monetização) lista "personagens personalizados" no Premium, mas a [DP-017](PRODUCT_DECISIONS.md#monetização) permite gerar histórias sem assinatura.
- **Opções:** (a) o comprador avulso tem a mesma personalização do Premium; (b) o comprador avulso usa apenas personagens base, sem personalização; (c) personalização parcial.
- **Recomendação:** (a). A criança como protagonista é o valor central da compra; sem personalização, a compra avulsa perde sentido. Nesse caso, o diferencial do Premium passa a ser a biblioteca completa, a franquia e mais perfis.

### <a id="qa-07"></a>QA-07 — Organização de Minha coleção

- **Contexto:** "favoritos" (Free) e "coleção pessoal" (Premium) aparecem como recursos distintos, mas a aba Minha coleção existe para todos.
- **Recomendação:** Minha coleção com duas seções, **Favoritas** (histórias da biblioteca) e **Criadas** (personalizadas), disponível para todos. A seção Criadas só tem conteúdo para quem gerou histórias. Assim, "coleção pessoal" deixa de ser um recurso exclusivo e passa a ser consequência de criar histórias.

### <a id="qa-08"></a>QA-08 — Favoritos de histórias Premium após o fim da assinatura

- **Recomendação:** manter os favoritos visíveis com indicação de bloqueio. Ao tocar, abrir a barreira parental e depois a oferta de assinatura. Nada é apagado.

### <a id="qa-09"></a>QA-09 — Plano anual ou outras periodicidades

- **Contexto:** apenas o plano mensal foi definido.
- **Recomendação:** fora do MVP. Reavaliar após os dados de retenção.

### <a id="qa-10"></a>QA-10 — Origens de créditos promocionais no MVP

- **Opções:** compensação de suporte; campanhas; indicação.
- **Recomendação:** no MVP, apenas **compensação manual pelo suporte**, com motivo registrado. Campanhas e indicação ficam para depois.

### <a id="qa-30"></a>QA-30 — Reembolso de créditos já consumidos

- **Contexto:** a Google Play pode reembolsar uma compra cujos créditos já foram usados.
- **Opções:** saldo negativo; bloqueio de novas gerações até regularizar; absorver a perda.
- **Recomendação:** registrar o estorno sempre. Se não houver saldo, absorver no MVP e monitorar a frequência; nunca remover histórias já criadas. Validar com o jurídico.

### <a id="qa-31"></a>QA-31 — Tributação e obrigações fiscais

- **Contexto:** a tributação sobre assinatura e créditos afeta a receita líquida ([BUSINESS_MODEL.md §7](BUSINESS_MODEL.md#7-economia-unitária)).
- **Ação:** consulta contábil antes de fechar os preços. Com a publicação como PJ ([DP-053](PRODUCT_DECISIONS.md#questões-decididas)), verificar: enquadramento e regime tributário compatíveis com desenvolvimento e licenciamento de software (o MEI costuma não abranger essas atividades); tributação dos repasses da Google, que podem vir do exterior; emissão de notas fiscais.

### <a id="qa-33"></a>QA-33 — Teto de custo de IA e alertas

- **Recomendação:** definir um orçamento mensal de IA para o lançamento, com alertas em 50%, 80% e 100%, e um mecanismo para pausar novas gerações sem afetar a leitura.

---

## Criação, personagens e conteúdo

### <a id="qa-11"></a>QA-11 — Entradas do fluxo de criação

- **Status:** ✅ Decidida em 2026-10-31: opções guiadas, sem texto livre → [DP-043](PRODUCT_DECISIONS.md#questões-decididas).
- **Contexto:** não está definido o que o responsável informa para criar a história.
- **Opções:** (a) opções guiadas (tema, cenário, valor ou emoção, companheiro); (b) texto livre; (c) opções guiadas + campo curto opcional.
- **Recomendação:** (a) no MVP. Reduz o risco de conteúdo inadequado (R-03), o custo de moderação e a variabilidade de qualidade, e combina com a experiência de "livro" em vez de "chat". Avaliar (c) depois.

### <a id="qa-12"></a>QA-12 — Gênero gramatical do protagonista

- **Contexto:** o português exige flexão de gênero (ele/ela, "o menino"/"a menina", adjetivos). Os atributos aprovados de personalização não tratam disso.
- **Opções:** (a) o responsável escolhe a forma de tratamento (masculino ou feminino); (b) a mesma escolha, com opção de texto que evite marcações de gênero quando possível; (c) inferir pela aparência (**não recomendado**).
- **Recomendação:** (a) ou (b), como escolha explícita do responsável, independente da aparência do personagem. Decisão de produto e editorial.

### <a id="qa-13"></a>QA-13 — Uso do nome da criança e envio ao provedor de IA

- **Status:** ✅ Decidida em 2026-10-31: o nome não é enviado ao provedor → [DP-045](PRODUCT_DECISIONS.md#questões-decididas).
- **Contexto:** a criança como protagonista sugere usar o nome dela, que é um dado pessoal.
- **Recomendação:** usar **apelido ou primeiro nome** informado pelo responsável. Avaliar substituir o nome por um marcador na chamada ao provedor e inserir o nome real no servidor após a geração, para que o provedor nunca receba o dado. Validar a viabilidade no spike.

### <a id="qa-14"></a>QA-14 — Dados do perfil infantil

- **Status:** ✅ Decidida em 2026-10-31: apelido + faixa etária → [DP-044](PRODUCT_DECISIONS.md#questões-decididas).
- **Recomendação:** apenas **apelido** (para exibição e uso na história) e **faixa etária** (0 a 2, 2 a 4, 4 a 6). Sem data de nascimento, sem foto, sem sobrenome. Opcionalmente, o personagem associado.

### <a id="qa-15"></a>QA-15 — Regenerar ou editar uma história gerada

- **Recomendação:** no MVP, não há edição. Uma nova geração consome um novo crédito, exceto quando a moderação ou o suporte identificarem um defeito, caso em que o crédito é compensado.

### <a id="qa-16"></a>QA-16 — Produção da biblioteca e do estilo visual

- **Status:** ✅ Decidida em 2026-10-31: textos de autoria própria ([DP-049](PRODUCT_DECISIONS.md#questões-decididas)) e ilustrações por IA com curadoria ([DP-056](PRODUCT_DECISIONS.md#questões-decididas)).
- **Contexto:** não estão definidos os autores e ilustradores das cerca de 30 histórias, se haverá uso de IA na produção, nem como o estilo visual da biblioteca se relaciona com o das histórias geradas.
- **Por que importa:** o produto deve parecer uma biblioteca cuidadosamente ilustrada ([DP-004](PRODUCT_DECISIONS.md#identidade-e-posicionamento)). Estilos discrepantes entre a biblioteca e as histórias geradas prejudicam a experiência.
- **Ação:** definir responsáveis, cronograma, direitos autorais e diretrizes de estilo.

### <a id="qa-17"></a>QA-17 — Critério de seleção das 10 histórias gratuitas

- **Recomendação:** cobrir as três faixas etárias e as seis categorias, incluindo pelo menos uma história de "Hora de dormir" por faixa. A seleção é configurável ([RF-BIB-06](PRODUCT_REQUIREMENTS.md#13-biblioteca-rf-bib)).

### <a id="qa-24"></a>QA-24 — Política de conteúdo e moderação

- **Status:** ✅ Decidida em 2026-10-31: proposta em camadas aprovada → [DP-054](PRODUCT_DECISIONS.md#questões-decididas).
- **Ação:** escrever uma política editorial e definir como ela é aplicada às histórias geradas.
- **Recomendação:** segurança em camadas, da mais barata para a mais cara.
  1. **Prevenção pelo desenho.** Com opções guiadas ([DP-043](PRODUCT_DECISIONS.md#questões-decididas)), o único texto livre é o apelido da criança, validado contra uma lista de termos impróprios. A maior parte do risco de entrada desaparece.
  2. **Política como regra de geração.** A política editorial vira instrução para o modelo, com regras por faixa etária e saída estruturada página a página, validada no servidor.
  3. **Biblioteca como referência de voz.** Trechos das 30 histórias autorais ([DP-049](PRODUCT_DECISIONS.md#questões-decididas)) servem de exemplo de tom, ritmo e vocabulário. Assim, as histórias geradas soam como a biblioteca, o que reforça a [DP-004](PRODUCT_DECISIONS.md#identidade-e-posicionamento).
  4. **Verificação automática da saída.** Texto e imagens são verificados antes da entrega. Se reprovar, há nova tentativa dentro do teto de retentativas; se persistir, a geração falha e o crédito é liberado ([DP-022](PRODUCT_DECISIONS.md#monetização)). Na dúvida, não entregar.
  5. **Revisão humana.** No lançamento: leitura semanal de uma amostra das histórias geradas e de 100% das denunciadas.
  6. **Denúncia no app.** "Reportar história", atrás da barreira parental. A história denunciada sai da coleção até a revisão; se a denúncia proceder, o crédito é compensado.
- **Conteúdo mínimo da política:**
  - temas adequados por faixa etária;
  - temas sensíveis e como tratá-los (medo sem terror, separação, frustração, chegada de irmão);
  - temas proibidos: violência, armas, conteúdo sexual, linguagem imprópria, personagens e marcas de terceiros, estereótipos;
  - **comportamentos perigosos imitáveis**, risco específico de 0 a 6 anos: mexer no fogão, em remédios ou em tomadas, entrar na água sem um adulto, sair com estranhos;
  - regras de imagem: nada assustador, sem texto dentro da ilustração, personagem consistente.

  A política vale também para a biblioteca autoral.
- **Proposta:** após aprovação, registrar a política em `docs/content/CONTENT_POLICY.md`.

### <a id="qa-28"></a>QA-28 — Representação de deficiências e acessórios assistivos

- **Contexto:** "características visuais" pode incluir óculos, aparelho auditivo, cadeira de rodas e outras.
- **Recomendação:** incluir no MVP pelo menos óculos e aparelho auditivo, se a consistência visual for viável. Tratar outros itens conforme o spike e a revisão de representação.

### <a id="qa-35"></a>QA-35 — Personagem salvo e reutilizável

- **Status:** ✅ Decidida em 2026-10-31 → [DP-046](PRODUCT_DECISIONS.md#questões-decididas).
- **Recomendação:** sim. O personagem fica salvo e associado ao perfil infantil e é reutilizado nas próximas histórias. Isso reforça a identificação da criança e a consistência entre histórias.

### <a id="qa-36"></a>QA-36 — Personagens secundários

- **Recomendação:** fora do MVP como personagens personalizáveis. A história pode ter coadjuvantes genéricos definidos pelo tema.

---

## Experiência

### <a id="qa-18"></a>QA-18 — Leitura sem conexão

- **Recomendação:** no MVP, cache das páginas já abertas para tolerar conexão instável, sem gestão explícita de downloads.

### <a id="qa-20"></a>QA-20 — Mecanismo da barreira parental

- **Status:** ✅ Decidida em 2026-10-31: desafio por escrito, sem PIN → [DP-048](PRODUCT_DECISIONS.md#questões-decididas).
- **Opções:** desafio aritmético; instrução por escrito ("toque e segure..."); PIN definido pelo responsável; autenticação do aparelho.
- **Recomendação:** desafio simples por escrito, sem PIN no MVP (menos atrito e nada a recuperar). Garantir acessibilidade ([RF-PAR-03](PRODUCT_REQUIREMENTS.md#19-controle-parental-rf-par)).

### <a id="qa-25"></a>QA-25 — Aviso de história pronta

- **Opções:** notificação push; apenas indicação dentro do app.
- **Recomendação:** notificação push opcional, com permissão solicitada no momento da primeira criação (não no onboarding), além de indicação dentro do app.

### <a id="qa-27"></a>QA-27 — Compartilhamento de histórias

- **Recomendação:** fora do MVP. Exige análise de privacidade (histórias contêm o nome e a representação da criança).

### <a id="qa-29"></a>QA-29 — Ajustes de leitura

- **Recomendação:** no MVP, tamanho de fonte ajustável. Modo noturno como candidato forte, por causa da categoria "Hora de dormir".

### <a id="qa-34"></a>QA-34 — Faixa etária do perfil filtra a biblioteca ou só sugere

- **Recomendação:** a faixa etária **ordena e sugere**, sem esconder as outras histórias. O responsável decide o que ler.

---

## Conta, plataforma e conformidade

### <a id="qa-19"></a>QA-19 — Autenticação e obrigatoriedade de conta

- **Status:** ✅ Decidida em 2026-10-31: Google + link mágico, conta obrigatória → [DP-047](PRODUCT_DECISIONS.md#questões-decididas).
- **Opções:** e-mail com link mágico; e-mail e senha; login com Google; combinação.
- **Também decidir:** se o Free exige conta (recomendação: **sim**, para que favoritos e perfis não se percam ao trocar de aparelho e para vincular compras ao servidor).
- **Recomendação:** login com Google + e-mail com link mágico, sem senha. Formalizar em ADR.

### <a id="qa-21"></a>QA-21 — Público-alvo declarado na Google Play

- **Status:** ✅ Decidida em 2026-10-31: opção (b), público misto com política de Famílias → [DP-051](PRODUCT_DECISIONS.md#questões-decididas).
- **Contexto:** o produto é administrado por adultos, mas o conteúdo é destinado a crianças. A declaração de público-alvo na Play Console pode sujeitar o app à política de Famílias da Google Play, com exigências sobre SDKs, dados e conteúdo.
- **Opções:**
  - (a) declarar apenas adultos (18+), por ser um app para responsáveis;
  - (b) declarar **público misto**: adultos + as faixas infantis que cobrem 0 a 6 anos (na Play Console, "5 anos ou menos" e "6 a 8 anos"; confirmar na versão vigente).
- **Recomendação:** (b), adotando a política de Famílias desde o início.
  - Histórias infantis ilustradas são claramente atrativas para crianças. A Google avalia o público pelo conteúdo e pela ficha da loja, não só pela declaração; declarar apenas adultos traz risco de rejeição ou remoção.
  - O produto já atende boa parte do que a política exige: sem anúncios ([DP-012](PRODUCT_DECISIONS.md#monetização)), dados mínimos ([DP-044](PRODUCT_DECISIONS.md#questões-decididas)) e barreira parental antes de compras ([DP-048](PRODUCT_DECISIONS.md#questões-decididas)).
  - O custo principal é restringir SDKs de terceiros (analytics, monitoramento de erros, login) aos compatíveis com a política de Famílias, e não coletar identificadores de publicidade. Isso orienta a [QA-26](#qa-26).
- **Ação:** confirmar os requisitos na política vigente da Google Play antes de escolher SDKs e manter uma lista de SDKs aprovados.

### <a id="qa-22"></a>QA-22 — Conformidade legal e documentos jurídicos

- **Status:** ✅ Decidida em 2026-10-31: execução interna, sem assessoria no MVP ([DP-052](PRODUCT_DECISIONS.md#questões-decididas)); publicação como PJ ([DP-053](PRODUCT_DECISIONS.md#questões-decididas)). Os passos 1, 3 e 4 abaixo continuam válidos e são executados pela equipe; o passo 2 fica para quando houver escala. Nos entregáveis, a indicação de um encarregado de dados continua recomendada.
- **Ação:** revisão jurídica que cubra, no mínimo: LGPD (em especial o tratamento de dados de crianças e o consentimento do responsável), a legislação brasileira de proteção de crianças em ambientes digitais vigente (incluindo o Estatuto Digital da Criança e do Adolescente, Lei nº 15.211/2025 — aplicabilidade a confirmar), o Código de Defesa do Consumidor (assinatura, teste gratuito, direito de arrependimento) e a retenção de registros após a exclusão de conta.
- **Recomendação:** plano em quatro passos.
  1. **Preparação interna (sem custo jurídico).** Montar um inventário de dados: o que é coletado, por quê, onde fica, por quanto tempo e com quem é compartilhado, incluindo os provedores de IA. Graças às [DP-025](PRODUCT_DECISIONS.md#conteúdo-e-personagens), [DP-044](PRODUCT_DECISIONS.md#questões-decididas) e [DP-045](PRODUCT_DECISIONS.md#questões-decididas), o inventário é pequeno, o que reduz o tempo (e o custo) da assessoria.
  2. **Assessoria com escopo fechado.** Advogado(a) com experiência em LGPD e produtos digitais para crianças, cobrindo:
     - LGPD, art. 14: consentimento específico e em destaque do responsável e atendimento ao melhor interesse da criança;
     - Estatuto Digital da Criança e do Adolescente: quais obrigações se aplicam ao produto, como configurações protetivas por padrão e ferramentas de supervisão parental;
     - CDC e regras de comércio eletrônico: assinatura, teste gratuito, renovação automática, cancelamento e arrependimento;
     - retenção de dados após a exclusão da conta;
     - contratos com provedores de IA: proibição de treinar modelos com os dados, retenção e transferência internacional.
  3. **Entregáveis:**
     - termos de uso e política de privacidade em linguagem simples;
     - texto de consentimento do responsável no onboarding;
     - canal do encarregado de dados (no início, pode ser a própria pessoa idealizadora);
     - relatório de impacto à proteção de dados (RIPD), recomendado por envolver dados de crianças e IA.
  4. **Revisão contínua.** Toda especificação nova que trate dados pessoais inclui uma seção de privacidade.
- **Também verificar:** se a publicação será como pessoa física ou jurídica (afeta o perfil de pagamentos da Google Play e a tributação, [QA-31](#qa-31)).

### <a id="qa-23"></a>QA-23 — Provedores de IA e garantias de privacidade

- **Critérios mínimos:** não usar os dados enviados para treinamento; retenção mínima ou nula; local de processamento; qualidade em português; consistência de personagem (imagem); custo; limites de uso.
- **Ação:** avaliar no spike (D-06) e registrar em ADR.

### <a id="qa-26"></a>QA-26 — Analytics e monitoramento

- **Recomendação:** registrar apenas eventos de produto do **responsável**, sem dados da criança nem conteúdo das histórias. Escolher ferramentas compatíveis com a decisão de [QA-21](#qa-21).

### <a id="qa-32"></a>QA-32 — `applicationId` definitivo e conta de publicação

- **Contexto:** o identificador técnico `mundo-de-contos` não define o `applicationId` ([DP-002](PRODUCT_DECISIONS.md#identidade-e-posicionamento)).
- **Ação:** definir o domínio ou a organização dona do app e validar a disponibilidade antes do primeiro envio à Play Console. O `applicationId` não pode ser alterado depois da publicação.
- **Com a publicação como PJ ([DP-053](PRODUCT_DECISIONS.md#questões-decididas)):** a conta de desenvolvedor será de organização, o que exige um número D-U-N-S; o `applicationId` pode seguir o domínio da empresa (por exemplo, `br.com.<empresa>.mundodecontos`). Também é recomendado verificar a disponibilidade da marca "Mundo de Contos" no INPI e registrá-la.

---

## Questões surgidas das decisões de 2026-10-31

### <a id="qa-37"></a>QA-37 — Perfis no teste gratuito e para quem compra créditos

- **Status:** ✅ Decidida em 2026-11-01: teste 5, Premium 5, só créditos 1 → [DP-057](PRODUCT_DECISIONS.md#questões-decididas).
- **Pergunta:** quantos perfis infantis a conta pode ter em duas situações que a [DP-041](PRODUCT_DECISIONS.md#questões-decididas) não cobre: (1) durante os 7 dias de teste gratuito; (2) quando o responsável não assina, mas compra créditos avulsos.
- **Recomendação:**
  - **teste:** 5 perfis, como no Premium, porque o teste existe para demonstrar o Premium;
  - **comprador avulso sem assinatura:** 1 perfil (o principal). A compra avulsa concede geração e personalização ([DP-042](PRODUCT_DECISIONS.md#questões-decididas)), mas não os demais recursos do Premium ([DP-018](PRODUCT_DECISIONS.md#monetização)).
- **Impacto:** se o teste terminar sem conversão, vale a mesma regra do fim da assinatura ([QA-38](#qa-38)).

### <a id="qa-38"></a>QA-38 — Perfis além do principal quando a assinatura termina

- **Status:** ✅ Decidida em 2026-11-01: arquivar e reativar ao assinar de novo ([DP-055](PRODUCT_DECISIONS.md#questões-decididas)); o perfil principal pode ser trocado ([DP-059](PRODUCT_DECISIONS.md#questões-decididas)).
- **Contexto:** a [DP-041](PRODUCT_DECISIONS.md#questões-decididas) mantém ativo apenas o perfil principal, mas a [DP-021](PRODUCT_DECISIONS.md#monetização) garante o acesso a todas as histórias criadas, inclusive as feitas para os outros perfis.
- **Recomendação:**
  - os demais perfis ficam **arquivados**: não podem ser selecionados nem receber novas histórias, mas **não são excluídos**;
  - as histórias criadas para eles continuam legíveis em Minha coleção, cumprindo a [DP-021](PRODUCT_DECISIONS.md#monetização);
  - ao assinar novamente, os perfis arquivados voltam a ficar ativos, com os seus personagens;
  - o responsável pode excluir perfis arquivados quando quiser.
- **Também decidir:** se o responsável pode trocar qual é o perfil principal. Recomendação: sim, em Configurações, atrás da barreira parental. Sem isso, uma família com duas crianças ficaria presa à escolha feita no primeiro acesso.

### <a id="qa-39"></a>QA-39 — Ilustração da biblioteca e estilo visual

- **Status:** ✅ Decidida em 2026-10-31: opção (b), tudo por IA, com direção criativa e curadoria da pessoa idealizadora → [DP-056](PRODUCT_DECISIONS.md#questões-decididas). Continuam válidas as recomendações de guia de estilo e de direitos abaixo.
- **Contexto:** os textos das 30 histórias estão definidos ([DP-049](PRODUCT_DECISIONS.md#questões-decididas)). Falta definir quem ilustra e qual é o estilo visual, que precisa ser coerente com as histórias geradas e com os personagens personalizáveis.
- **Opções:**
  - (a) ilustrador(a) contratado(a) para tudo;
  - (b) ilustrações geradas por IA, com curadoria manual;
  - (c) misto: ilustrador(a) cria o guia de estilo e os personagens base; a IA produz as páginas, com curadoria.
- **Recomendação:** começar por um **guia de estilo visual** (paleta, traço, proporções dos personagens) antes de produzir qualquer página. A opção (c) tende a dar mais coerência entre a biblioteca e as histórias geradas, porque os mesmos personagens base e o mesmo estilo alimentam as duas. Validar custo e prazo.
- **Direitos:** garantir cessão de direitos patrimoniais (ilustrador) ou termos que permitam uso comercial (provedor de IA).
- **Bloqueia:** produção da biblioteca ([D-03](MVP_SCOPE.md#9-dependências)) e personagens base (RF-PERS-01).

### <a id="qa-40"></a>QA-40 — Créditos comprados quando a cota do Premium ativo acaba

- **Status:** ✅ Decidida em 2026-11-01: opção (b) → [DP-058](PRODUCT_DECISIONS.md#questões-decididas).
- **Contexto:** pela [DP-050](PRODUCT_DECISIONS.md#questões-decididas), créditos comprados só são usados quando não há assinatura ativa. Falta o caso de um assinante (ou alguém em teste) que esgota a cota do período e ainda tem créditos comprados, por exemplo de antes de assinar.
- **Opções:**
  - (a) os comprados ficam congelados enquanto a assinatura estiver ativa; o assinante aguarda a renovação da cota;
  - (b) os comprados passam a ser usados depois que a cota do período acaba;
  - (c) como (a), mas sem oferecer pacotes avulsos a quem tem assinatura ativa.
- **Recomendação:** (b). A cota da assinatura continua sendo usada antes e os comprados continuam por último, mas o cliente nunca fica com créditos pagos que não consegue usar, situação que costuma gerar reclamação e pedido de reembolso.
- **Também decidir:** se assinantes podem comprar pacotes. Com (a), a compra não faria sentido durante a assinatura, e o app deveria ocultar os pacotes.
