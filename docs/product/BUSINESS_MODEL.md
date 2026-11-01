# Mundo de Contos — Modelo de Negócio

> **Status:** rascunho para aprovação · **Versão:** 0.1 · **Atualizado em:** 2026-10-31
> **Decisões de referência:** [DP-011 a DP-024](PRODUCT_DECISIONS.md#monetização)

Legenda: **[Aprovado]** decisão registrada · **[Hipótese]** a validar · **[Aberto]** depende de questão em aberto · **[Proposta]** recomendação ainda não aprovada.

---

## 1. Resumo

O Mundo de Contos combina três fontes de valor:

1. **Free**: porta de entrada sem custo e sem publicidade, com uma amostra da biblioteca.
2. **Premium (assinatura mensal)**: biblioteca completa e criação de histórias personalizadas.
3. **Créditos avulsos**: criação de histórias personalizadas sem assinatura.

A biblioteca autoral tem **custo marginal de IA praticamente nulo**, pois é produzida uma única vez. A geração personalizada tem **custo variável por história**. O modelo de negócio precisa proteger a margem desse custo variável com limites, franquias e preços configuráveis.

---

## 2. Modalidades

### 2.1 Free — [Aprovado] [DP-013](PRODUCT_DECISIONS.md#monetização)

- 10 histórias selecionadas da biblioteca.
- Leitura ilustrada.
- Favoritos.
- Um perfil infantil.
- Sem geração de histórias por IA.
- Sem publicidade.

### 2.2 Premium — [Aprovado] [DP-014](PRODUCT_DECISIONS.md#monetização), [DP-015](PRODUCT_DECISIONS.md#monetização)

| Item | Definição | Status |
| --- | --- | --- |
| Preço | R$ 14,90 por mês | [Hipótese] [H-01](PRODUCT_DECISIONS.md#h-01) |
| Periodicidade | Mensal | [Aprovado]. Outras periodicidades: [Aberto] [QA-09](OPEN_QUESTIONS.md#qa-09) |
| Teste gratuito | 7 dias | [Aprovado] |
| Limite de gerações no teste | 2 gerações (configurável) | [Aprovado] [DP-039](PRODUCT_DECISIONS.md#questões-decididas) |
| Franquia mensal de gerações | Teto mensal; direção entre 5 e 10, a fechar após análise de custos | [Aberto] [QA-02](OPEN_QUESTIONS.md#qa-02) |
| Biblioteca completa | Sim | [Aprovado] |
| Geração com IA | Sim | [Aprovado] |
| Personagens personalizados | Sim | [Aprovado] |
| Perfis infantis | Até 5, incluindo o perfil principal | [Aprovado] [DP-041](PRODUCT_DECISIONS.md#questões-decididas) |
| Coleção pessoal | Sim | [Aprovado]. Escopo: [Aberto] [QA-07](OPEN_QUESTIONS.md#qa-07) |
| PDF e narração | Evolução futura | Fora do MVP |

**Transparência obrigatória [Aprovado] [DP-016](PRODUCT_DECISIONS.md#monetização):** antes da contratação, o responsável vê preço, periodicidade, data de início da cobrança (fim do teste) e como cancelar.

### 2.3 Compra avulsa de créditos — [Aprovado] [DP-017](PRODUCT_DECISIONS.md#monetização), [DP-018](PRODUCT_DECISIONS.md#monetização)

| Pacote | Preço inicial | Preço por história | Status |
| --- | --- | --- | --- |
| 1 história | R$ 3,90 | R$ 3,90 | [Hipótese] [H-02](PRODUCT_DECISIONS.md#h-02) |
| 3 histórias | R$ 9,90 | R$ 3,30 | [Hipótese] |
| 5 histórias | R$ 14,90 | R$ 2,98 | [Hipótese] |

- A assinatura **não** é obrigatória para comprar créditos.
- Créditos **não** dão acesso à biblioteca Premium completa.
- Pacotes e preços são **configuráveis** fora do código de domínio ([DP-024](PRODUCT_DECISIONS.md#monetização)).

---

## 3. Matriz de direitos de acesso

Estados do responsável:

- **Free**: nunca assinou ou não tem assinatura ativa e não tem créditos.
- **Teste**: dentro do período de teste gratuito do Premium.
- **Premium**: assinatura ativa e paga.
- **Avulso**: sem assinatura, com saldo de créditos comprados ou promocionais.
- **Ex-assinante**: assinatura encerrada; pode ter créditos remanescentes.

Um mesmo responsável pode acumular estados, por exemplo Premium com créditos comprados.

| Recurso | Free | Teste | Premium | Avulso | Ex-assinante |
| --- | --- | --- | --- | --- | --- |
| 10 histórias gratuitas | ✅ | ✅ | ✅ | ✅ | ✅ |
| Biblioteca completa | ❌ | ✅ | ✅ | ❌ | ❌ |
| Leitor ilustrado | ✅ | ✅ | ✅ | ✅ | ✅ |
| Favoritos | ✅ | ✅ | ✅ | ✅ | ✅ (ver [QA-08](OPEN_QUESTIONS.md#qa-08)) |
| Perfis infantis ([DP-041](PRODUCT_DECISIONS.md#questões-decididas)) | 1 (principal) | 5 ([DP-057](PRODUCT_DECISIONS.md#questões-decididas)) | 5 | 1 (principal) ([DP-057](PRODUCT_DECISIONS.md#questões-decididas)) | 1 ativo (principal); demais em [QA-38](OPEN_QUESTIONS.md#qa-38) |
| Gerar história com IA | ❌ | ✅ até 2 ([DP-039](PRODUCT_DECISIONS.md#questões-decididas)) | ✅ conforme franquia ([QA-02](OPEN_QUESTIONS.md#qa-02)); depois, créditos comprados ([DP-058](PRODUCT_DECISIONS.md#questões-decididas)) | ✅ consumindo créditos | ✅ apenas com créditos remanescentes |
| Personalizar personagem | ❌ | ✅ | ✅ | ✅ ([DP-042](PRODUCT_DECISIONS.md#questões-decididas)) | ✅ ao gerar com créditos |
| Acessar histórias já criadas | — | ✅ | ✅ | ✅ | ✅ ([DP-021](PRODUCT_DECISIONS.md#monetização)) |
| Comprar créditos | ✅ | ✅ | ✅ | ✅ | ✅ |
| Publicidade | Nunca | Nunca | Nunca | Nunca | Nunca |

---

## 4. Créditos

### 4.1 Tipos de crédito — [Aprovado] [DP-019](PRODUCT_DECISIONS.md#monetização)

| Tipo | Origem | Sobrevive ao fim da assinatura? | Expira? |
| --- | --- | --- | --- |
| **Comprado** | Compra avulsa via Google Play | Sim ([DP-020](PRODUCT_DECISIONS.md#monetização)) | Não ([DP-040](PRODUCT_DECISIONS.md#questões-decididas)) |
| **Promocional** | Campanhas, cortesias e compensações (origens em [QA-10](OPEN_QUESTIONS.md#qa-10)) | [Aberto] | [Aberto] [QA-04](OPEN_QUESTIONS.md#qa-04) |
| **Da assinatura** | Franquia do teste ou do Premium | Não (vinculado ao período) [Proposta] | Ao fim do período [Proposta]; acúmulo entre períodos em [QA-02](OPEN_QUESTIONS.md#qa-02) |

> Se o Premium tiver geração ilimitada ([QA-02](OPEN_QUESTIONS.md#qa-02)), "créditos da assinatura" passam a ser um direito de uso sujeito a limites antiabuso, e não um saldo numérico. O livro-razão continua registrando cada consumo.

### 4.2 Regras de negócio — [Aprovado]

1. Créditos de origens diferentes têm saldos separados ([DP-019](PRODUCT_DECISIONS.md#monetização)).
2. Créditos comprados permanecem após o cancelamento ou o término da assinatura ([DP-020](PRODUCT_DECISIONS.md#monetização)).
3. Histórias criadas permanecem acessíveis ([DP-021](PRODUCT_DECISIONS.md#monetização)).
4. Falha na geração não consome definitivamente um crédito ([DP-022](PRODUCT_DECISIONS.md#monetização)).
5. Toda compra e toda movimentação de crédito têm histórico auditável ([DP-023](PRODUCT_DECISIONS.md#monetização)).

### 4.3 Ciclo de vida de um crédito — [Proposta]

Proposta para atender às regras 4 e 5. A formalização técnica será feita em ADR.

```text
                ┌──────────── falha na geração ───────────┐
                ▼                                          │
 CONCEDIDO ──► DISPONÍVEL ──► RESERVADO ──► geração ok ──► CONSUMIDO
 (compra,                                                    │
  promoção,                                                  └─► ESTORNADO (reembolso,
  assinatura)    DISPONÍVEL ──► EXPIRADO (se houver expiração)     ver QA-30)
```

- **Reserva:** quando o responsável confirma a criação, um crédito é reservado; o saldo disponível diminui, mas o crédito ainda não foi consumido.
- **Confirmação:** a história concluída com sucesso confirma o consumo.
- **Liberação:** falha definitiva (após as retentativas) devolve o crédito ao saldo disponível.
- **Registro imutável:** cada transição gera um lançamento em um livro-razão do tipo "somente acréscimo" (*append-only*), com data, origem, motivo e referência (compra, história ou campanha). O saldo é derivado dos lançamentos.

### 4.4 Ordem de consumo — [Aprovado] [DP-050](PRODUCT_DECISIONS.md#questões-decididas)

Cada contexto tem saldo separado. Ao criar uma história, o consumo segue a ordem:

1. créditos **promocionais**;
2. **cota da assinatura** (teste ou Premium);
3. créditos **comprados**, apenas quando não há assinatura ativa (nunca assinou, cancelou ou não renovou).

Quando a cota de uma assinatura ativa se esgota, os créditos comprados podem ser usados ([DP-058](PRODUCT_DECISIONS.md#questões-decididas)).

### 4.5 Reembolsos e estornos — [Aberto] [QA-30](OPEN_QUESTIONS.md#qa-30)

Reembolsos concedidos pela Google Play precisam refletir no saldo (lançamento de estorno). Ainda falta definir a política quando os créditos reembolsados já foram consumidos.

---

## 5. Configurabilidade — [Aprovado] [DP-024](PRODUCT_DECISIONS.md#monetização)

Devem ser alteráveis **sem mudança no código de domínio**:

| Item | Onde vive (proposta) |
| --- | --- |
| Preço de assinatura e de pacotes | Google Play Console (produto e preço por região) |
| Quantidade de créditos por pacote | Configuração do backend, associada ao ID do produto na loja |
| Pacotes ativos e inativos | Configuração do backend e da loja |
| Limite de gerações do teste | Configuração do backend |
| Franquia mensal do Premium | Configuração do backend |
| Limites antiabuso (gerações por hora ou dia) | Configuração do backend |
| Quantidade de perfis por modalidade | Configuração do backend |
| Histórias incluídas no Free | Metadado do catálogo |

Alterações de configuração que afetam clientes (preço, franquia, limites) precisam de registro de quem alterou, quando e o valor anterior.

---

## 6. Implicações da Google Play

Pontos a confirmar na especificação de billing e com a política vigente da Google Play:

- **Bens digitais** (assinatura e créditos) usam o **Google Play Billing** no Android.
- A **assinatura** é configurada como produto de assinatura, com oferta de teste gratuito. A elegibilidade ao teste é controlada pela loja, o que reduz o abuso de testes repetidos na mesma conta Google.
- **Créditos** são produtos de compra única do tipo **consumível**.
- **Cancelamento** é feito pela Google Play. O app deve explicar como cancelar e oferecer atalho para a gestão de assinaturas.
- Toda compra é **validada no servidor** antes de conceder direitos ou créditos, de forma idempotente (a mesma compra nunca concede créditos duas vezes).
- **Público-alvo declarado:** público misto, seguindo a política de Famílias desde o início ([DP-051](PRODUCT_DECISIONS.md#questões-decididas)).
- **Conteúdo gerado por IA:** a Google Play exige que apps com conteúdo gerado por IA ofereçam uma forma de denúncia dentro do app, atendida pelo "Reportar história" ([DP-054](PRODUCT_DECISIONS.md#questões-decididas)). Confirmar os requisitos vigentes.
- **Conta de organização:** a publicação é feita por PJ ([DP-053](PRODUCT_DECISIONS.md#questões-decididas)).
- A **taxa de serviço** da loja reduz a receita líquida; o percentual aplicável precisa ser confirmado.

---

## 7. Economia unitária

Ainda não há dados de custo. Esta seção define **como** a viabilidade será calculada; os valores serão preenchidos após o spike técnico ([D-06](MVP_SCOPE.md#9-dependências)).

### 7.1 Variáveis

| Variável | Descrição |
| --- | --- |
| `P` | Preço bruto ao consumidor |
| `T_loja` | Taxa da Google Play sobre `P` |
| `T_imp` | Tributos sobre a receita ([QA-31](OPEN_QUESTIONS.md#qa-31)) |
| `RL` | Receita líquida = `P × (1 − T_loja) − tributos` |
| `CMH` | Custo médio por história gerada = texto + imagens (capa, introdução, páginas, encerramento) + moderação + retentativas + armazenamento + infraestrutura |
| `F` | Gerações médias por assinante por mês (uso real, limitado pela franquia) |
| `CF` | Custo fixo médio por usuário ativo (infraestrutura, entrega da biblioteca, suporte) |

### 7.2 Condições de viabilidade

- **Crédito avulso:** `RL_por_crédito − CMH > 0`, com margem-alvo a definir. O pacote de 5 créditos é o de menor receita por história (R$ 2,98 bruto) e deve ser a referência mínima.
- **Premium:** `RL_mensal − (F × CMH) − CF > 0` para o assinante típico, e o pior caso (`F` = franquia máxima) deve ser no mínimo neutro.
- **Teste gratuito:** custo esperado = `limite_teste × CMH × uso_médio`, tratado como custo de aquisição.

### 7.3 Alavancas de custo

- Limite de gerações no teste e franquia no Premium.
- Quantidade de páginas por história ([H-04](PRODUCT_DECISIONS.md#h-04)), possivelmente menor para 0 a 2 anos.
- Resolução e formato das imagens.
- Teto de retentativas por geração.
- Escolha de provedor e modelo por etapa (texto × imagem).
- Biblioteca pré-produzida (sem custo marginal de IA por leitura).

---

## 8. Métricas de negócio

- Conversão Free → teste; teste → Premium pago.
- Retenção mensal de assinantes e motivos de cancelamento.
- Receita e conversão por pacote de créditos.
- Proporção de compradores avulsos que depois assinam.
- `CMH` real e sua distribuição; custo de IA por assinante.
- Taxa de falha de geração e créditos liberados por falha.
- Reembolsos e estornos.

---

## 9. Riscos de negócio

Os riscos estão consolidados em [MVP_SCOPE.md — Riscos](MVP_SCOPE.md#8-riscos), em especial R-01 (custo de IA), R-07 (conversão e canibalização), R-10 (abuso) e R-12 (reconciliação de billing).
