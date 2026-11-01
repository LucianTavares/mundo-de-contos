---
name: registrar-decisao
description: Registra decisões de produto tomadas pelo responsável (novas DP-xxx) a partir de respostas a questões em aberto (QA-xx) e propaga a decisão pelos documentos de produto.
argument-hint: "[QA-xx: decisão; QA-yy: decisão]"
disable-model-invocation: true
---

# Registrar decisão de produto

Respostas recebidas: `$ARGUMENTS`

Somente o responsável pelo produto decide. Esta skill registra o que ele decidiu; ela não decide.

## 1. Interpretar

- Associe cada resposta a uma `QA-xx` de [OPEN_QUESTIONS.md](../../../docs/product/OPEN_QUESTIONS.md).
- Se a resposta for ambígua ou não cobrir toda a questão, **pergunte antes de escrever**. Não complete com a recomendação.
- Confira se a decisão conflita com alguma `DP` existente. Se conflitar, aponte o conflito e pergunte.

## 2. Registrar em `PRODUCT_DECISIONS.md`

- Próximo número: o maior `DP-xxx` + 1.
- Adicione a linha na tabela "Questões decididas", com a coluna Origem (`QA-xx`, ou "(parcial)") e data absoluta. Atualize a frase "Registradas em".
- Se a decisão substituir outra `DP`, indique isso nas duas.
- Se resolver uma observação da seção 3, marque-a como **Resolvida**.

## 3. Atualizar `OPEN_QUESTIONS.md`

- Tabela-resumo: `✅ Decidida → DP-xxx` ou `◐ Parcial → DP-xxx (o que falta)`.
- Na seção da questão, logo abaixo do título: `- **Status:** ✅ Decidida em AAAA-MM-DD: resumo → [DP-xxx](PRODUCT_DECISIONS.md#questões-decididas).` A seção fica como histórico.

## 4. Propagar

- Procure referências à questão: `grep -rn "qa-NN" docs/`.
- Substitua marcações como `⚠ QA-xx`, `[Aberto]` e "Depende de QA-xx" pela decisão, citando a `DP`, em `BUSINESS_MODEL.md`, `PRODUCT_REQUIREMENTS.md`, `USER_JOURNEYS.md`, `MVP_SCOPE.md` (seção 4) e nas specs.
- Se uma spec **Aprovada** for afetada, atualize o histórico dela e volte o status para Em revisão.

## 5. Lacunas novas

Se a decisão criar uma lacuna ou um conflito, abra uma nova `QA-xx` (com âncora `<a id="qa-NN"></a>`, contexto, opções e recomendação) e adicione-a à tabela-resumo. Uma recomendação nunca é registrada como decisão.

## 6. Verificar

Confirme que todas as referências a questões têm âncora:

```bash
comm -23 <(grep -rohE 'qa-[0-9]+' docs | sort -u) <(grep -ohE 'id="qa-[0-9]+"' docs/product/OPEN_QUESTIONS.md | grep -oE 'qa-[0-9]+' | sort -u)
```

A saída deve ser vazia.

## 7. Relatar

Decisões registradas (`DP` ↔ `QA`), arquivos alterados, novas questões abertas e conflitos encontrados.
