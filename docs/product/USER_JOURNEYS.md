# Mundo de Contos — Jornadas do Usuário

> **Status:** rascunho para aprovação · **Versão:** 0.1 · **Atualizado em:** 2026-10-31

As jornadas descrevem o comportamento esperado de ponta a ponta. Elas não definem layout nem textos finais; esses detalhes ficam para as especificações de cada funcionalidade.

Nas jornadas, **"responsável"** é sempre o adulto. Pontos ainda não decididos aparecem como **⚠ QA-xx**.

---

## Perfis ilustrativos

Os perfis abaixo são **ilustrativos** e servem para orientar o design. Não resultam de pesquisa e devem ser validados.

| Perfil | Contexto | O que busca |
| --- | --- | --- |
| **Responsável de bebê (0 a 2)** | Rotina intensa, pouco tempo, lê no colo antes de dormir. | Histórias curtas, imagens grandes, nada de anúncios ou estímulos excessivos. |
| **Responsável de criança de 2 a 4** | A criança pede "de novo!"; fase de emoções intensas e novas rotinas. | Histórias sobre situações do dia a dia (dormir, dividir, escola) e repetição. |
| **Responsável de criança de 4 a 6** | Criança curiosa, gosta de aventuras e de se ver nas histórias. | Criar histórias em que a criança é a heroína; participação maior na leitura. |

---

## Mapa das jornadas

| ID | Jornada | Modalidade |
| --- | --- | --- |
| J-01 | Primeiro acesso e criação do primeiro perfil | Todas |
| J-02 | Leitura compartilhada na hora de dormir | Todas |
| J-03 | Descobrir uma história Premium e iniciar o teste gratuito | Free → Teste |
| J-04 | Criar uma história personalizada | Teste, Premium, Avulso |
| J-05 | Falha na geração da história | Teste, Premium, Avulso |
| J-06 | Comprar créditos sem assinar | Free → Avulso |
| J-07 | Atingir o limite de gerações do teste | Teste |
| J-08 | Cancelamento e fim da assinatura | Premium → Ex-assinante |
| J-09 | Criança tenta acessar uma área restrita | Todas |
| J-10 | Gerenciar perfis infantis | Todas |
| J-11 | Trocar de aparelho e restaurar compras | Todas |
| J-12 | Excluir a conta | Todas |

---

## J-01 — Primeiro acesso e criação do primeiro perfil

**Objetivo:** o responsável entende a proposta e lê a primeira história em poucos minutos.

1. O responsável instala o app e vê uma apresentação curta: biblioteca ilustrada, histórias personalizadas e leitura em família.
2. Cria a conta com login Google ou link mágico por e-mail ([DP-047](PRODUCT_DECISIONS.md#questões-decididas)) e aceita os termos e a política de privacidade ([DP-052](PRODUCT_DECISIONS.md#questões-decididas)).
3. Cria o **perfil principal**, informando apenas apelido (ou primeiro nome) e faixa etária ([DP-041, DP-044](PRODUCT_DECISIONS.md#questões-decididas)).
4. Vê uma mensagem sobre leitura compartilhada (o app é para ler **junto**). [DP-005](PRODUCT_DECISIONS.md#identidade-e-posicionamento)
5. Chega à tela Início, com sugestões das histórias gratuitas para a faixa etária do perfil.
6. Abre a primeira história.

**Regras:** nenhuma oferta de assinatura bloqueia o caminho até a primeira leitura [Proposta]. Nenhum dado além do necessário é solicitado.

**Exceções:** sem conexão no primeiro acesso → mensagem clara e opção de tentar novamente.

---

## J-02 — Leitura compartilhada na hora de dormir

**Objetivo:** ler uma história com a criança, sem distrações.

1. O responsável abre o app e, em Início, toca em "continuar lendo" ou escolhe uma sugestão (ou navega pela Biblioteca, filtrando por "Hora de dormir").
2. O leitor abre a capa. Uma página por vez, com ilustração grande e texto legível. [DP-033](PRODUCT_DECISIONS.md#experiência)
3. O adulto lê em voz alta; a criança pode virar as páginas com toque ou gesto.
4. No final: favoritar, reler ou voltar.
5. A história favoritada aparece em Minha coleção.

**Regras:** o leitor não mostra preços, ofertas nem atalhos para áreas adultas ([RF-LEI-04](PRODUCT_REQUIREMENTS.md#14-leitor-rf-lei)). Se a criança tocar fora das áreas de navegação, nada de inesperado acontece.

**Pendências:** modo noturno e tamanho de fonte ⚠ [QA-29](OPEN_QUESTIONS.md#qa-29) · leitura sem conexão ⚠ [QA-18](OPEN_QUESTIONS.md#qa-18).

---

## J-03 — Descobrir uma história Premium e iniciar o teste gratuito

**Objetivo:** converter o interesse em teste com total transparência.

1. Na Biblioteca, o responsável vê uma história com indicação discreta de "Premium".
2. Ao tocar nela, a **barreira parental** aparece ([J-09](#j-09--criança-tenta-acessar-uma-área-restrita)).
3. Após a barreira, a tela de assinatura mostra: o que o Premium inclui, o preço (R$ 14,90/mês, [H-01](PRODUCT_DECISIONS.md#h-01)), os 7 dias gratuitos, a data em que a cobrança começa, o limite de 2 gerações durante o teste e como cancelar. [DP-016](PRODUCT_DECISIONS.md#monetização)
4. O responsável confirma pela Google Play.
5. O servidor valida a compra e libera a biblioteca completa e a criação.
6. O app volta para a história que motivou a assinatura.

**Exceções:**

- Compra cancelada ou recusada → volta à Biblioteca sem penalidade.
- Compra pendente (método de pagamento com confirmação posterior) → o app informa que o acesso será liberado quando a loja confirmar.
- Conta já usou o teste → a loja oferece a assinatura sem teste; o app deve refletir isso corretamente.

---

## J-04 — Criar uma história personalizada

**Objetivo:** criar uma história em que a criança é protagonista, com previsibilidade de custo.

1. O responsável abre **Criar**.
   - Sem direito de geração: vê a proposta e as opções de teste ou créditos (atrás da barreira parental) → [J-03](#j-03--descobrir-uma-história-premium-e-iniciar-o-teste-gratuito) ou [J-06](#j-06--comprar-créditos-sem-assinar).
2. Escolhe o perfil infantil para quem é a história.
3. Escolhe ou cria o personagem: base ilustrada + personalização (pele, cabelo, penteado, características, roupas e acessórios). O personagem fica salvo no perfil para as próximas histórias ([DP-046](PRODUCT_DECISIONS.md#questões-decididas)). ⚠ [QA-28](OPEN_QUESTIONS.md#qa-28)
4. Define os parâmetros da história por **opções guiadas**, sem texto livre ([DP-043](PRODUCT_DECISIONS.md#questões-decididas)). O nome da criança não é enviado ao provedor de IA ([DP-045](PRODUCT_DECISIONS.md#questões-decididas)). ⚠ [QA-12](OPEN_QUESTIONS.md#qa-12) (gênero gramatical)
5. Revisão: resumo das escolhas e **o que será consumido**, conforme a ordem da [DP-050](PRODUCT_DECISIONS.md#questões-decididas), com o saldo antes e depois.
6. Confirma, passando pela barreira parental [Proposta, RF-PAR-02]. O crédito é **reservado**.
7. A história entra em geração assíncrona. O app mostra o estado e permite sair da tela.
8. Quando fica pronta, o responsável é avisado. ⚠ [QA-25](OPEN_QUESTIONS.md#qa-25)
9. A história (capa, introdução, páginas, encerramento) abre no leitor e fica salva em Minha coleção. O crédito é **consumido**.

**Regras:** entradas e saídas passam por moderação em camadas ([DP-054](PRODUCT_DECISIONS.md#questões-decididas)). O responsável pode reportar a história ([RF-CRI-14](PRODUCT_REQUIREMENTS.md#17-criação-de-histórias-personalizadas-rf-cri)). O personagem mantém aparência consistente em todas as páginas ([DP-028](PRODUCT_DECISIONS.md#conteúdo-e-personagens)).

**Exceções:** falha → [J-05](#j-05--falha-na-geração-da-história). Entrada recusada pela moderação → orientação gentil para ajustar, **sem** consumir crédito. Limite atingido → [J-07](#j-07--atingir-o-limite-de-gerações-do-teste).

---

## J-05 — Falha na geração da história

**Objetivo:** o responsável não perde dinheiro nem confiança.

1. A geração falha definitivamente, após as retentativas automáticas.
2. O crédito reservado é **liberado** e o lançamento fica registrado. [DP-022](PRODUCT_DECISIONS.md#monetização)
3. O responsável vê uma mensagem acolhedora: "Não conseguimos terminar esta história. Seu crédito foi devolvido."
4. Pode tentar novamente com as mesmas escolhas.

**Regras:** a mensagem nunca culpa o usuário nem expõe detalhes técnicos. O histórico de créditos mostra reserva e liberação.

---

## J-06 — Comprar créditos sem assinar

**Objetivo:** criar histórias personalizadas sem compromisso de assinatura.

1. Em Criar (ou em Configurações › Créditos), após a barreira parental, o responsável vê os pacotes disponíveis, com preço e quantidade vindos de configuração e da loja. [DP-024](PRODUCT_DECISIONS.md#monetização)
2. O app deixa claro que créditos **não** liberam a biblioteca Premium. [DP-018](PRODUCT_DECISIONS.md#monetização)
3. Escolhe o pacote e paga pela Google Play.
4. O servidor valida a compra e concede os créditos (tipo "comprado") uma única vez.
5. O saldo é atualizado e o responsável segue para [J-04](#j-04--criar-uma-história-personalizada).

**Exceções:** compra pendente → saldo creditado após a confirmação da loja. Reembolso posterior → estorno registrado. ⚠ [QA-30](OPEN_QUESTIONS.md#qa-30)

---

## J-07 — Atingir o limite de gerações do teste

1. Durante o teste, o responsável usa as 2 gerações permitidas ([DP-039](PRODUCT_DECISIONS.md#questões-decididas)).
2. Ao abrir Criar, vê quantas gerações usou, quando o teste termina e quando a franquia do Premium começa. ⚠ [QA-02](OPEN_QUESTIONS.md#qa-02)
3. Opções: usar créditos promocionais, se houver, ou aguardar a cota do Premium pago, que começa ao fim do teste. Também pode usar créditos comprados ou comprar um pacote ([DP-058](PRODUCT_DECISIONS.md#questões-decididas)).

**Regras:** a biblioteca completa continua acessível durante todo o teste.

---

## J-08 — Cancelamento e fim da assinatura

1. Em Configurações › Assinatura, o app explica como cancelar e oferece atalho para a gestão de assinaturas da Google Play.
2. O cancelamento acontece na loja. O acesso Premium continua até o fim do período pago (regra da loja).
3. Ao fim do período, o responsável passa a **Ex-assinante**:
   - mantém o acesso às histórias que criou [DP-021](PRODUCT_DECISIONS.md#monetização);
   - mantém os créditos comprados [DP-020](PRODUCT_DECISIONS.md#monetização);
   - volta a ter acesso apenas às 10 histórias gratuitas da biblioteca;
   - apenas o perfil principal permanece ativo ([DP-041](PRODUCT_DECISIONS.md#questões-decididas)); os demais ficam arquivados e voltam a ficar ativos se a pessoa assinar de novo; as histórias criadas para eles continuam legíveis ([DP-055](PRODUCT_DECISIONS.md#questões-decididas));
   - favoritos de histórias Premium ⚠ [QA-08](OPEN_QUESTIONS.md#qa-08).
4. O app comunica essas mudanças com clareza, sem tom punitivo.

---

## J-09 — Criança tenta acessar uma área restrita

1. A criança, com o celular, toca em algo que leva a compras, configurações, perfis ou conta.
2. A barreira parental aparece: um desafio simples por escrito, fácil para adultos e difícil para crianças pequenas ([DP-048](PRODUCT_DECISIONS.md#questões-decididas)).
3. Sem resposta correta, o app volta à tela anterior, sem penalidade nem mensagens assustadoras.

**Regras:** a barreira protege todos os pontos de [RF-PAR-01](PRODUCT_REQUIREMENTS.md#19-controle-parental-rf-par). A compra também é protegida pela autenticação da própria Google Play, configurada na conta do responsável.

---

## J-10 — Gerenciar perfis infantis

1. Em Configurações › Perfis (atrás da barreira parental), o responsável vê os perfis.
2. Pode criar perfis (Free: 1; Premium: até 5, [DP-041](PRODUCT_DECISIONS.md#questões-decididas)), editá-los ou excluí-los. Também pode trocar qual é o perfil principal ([DP-059](PRODUCT_DECISIONS.md#questões-decididas)).
3. Ao excluir, o app informa o que acontece com as histórias criadas para aquele perfil [Proposta].
4. O perfil ativo pode ser trocado a partir da tela Início.

---

## J-11 — Trocar de aparelho e restaurar compras

1. O responsável instala o app em outro aparelho e entra na mesma conta.
2. Perfis, favoritos, histórias criadas, créditos e assinatura são recuperados pelo servidor.
3. Se a assinatura não aparecer, "Restaurar compras" consulta a Google Play e revalida.

---

## J-12 — Excluir a conta

1. Em Configurações › Conta (atrás da barreira parental), o responsável escolhe "Excluir conta".
2. O app explica as consequências: perda de histórias criadas, perfis e créditos remanescentes; a assinatura precisa ser cancelada na Google Play.
3. O responsável confirma.
4. Os dados são excluídos, respeitando apenas as retenções exigidas por lei, definidas internamente ([DP-052](PRODUCT_DECISIONS.md#questões-decididas)).
5. O app confirma a exclusão e volta à tela inicial.
