# Mundo de Contos — Visão do Produto

> **Status:** rascunho para aprovação · **Versão:** 0.1 · **Atualizado em:** 2026-10-31
> **Fonte:** Pacote de Prompts de Engenharia — Prompt 1 (Product Foundation)

## Mapa da documentação de produto

Cada documento tem uma responsabilidade única. Os demais documentos referenciam os itens por ID, em vez de repeti-los.

| Documento | Responsabilidade | IDs |
| --- | --- | --- |
| [PRODUCT_VISION.md](PRODUCT_VISION.md) | Por que o produto existe, para quem e quais princípios o guiam | — |
| [PRODUCT_REQUIREMENTS.md](PRODUCT_REQUIREMENTS.md) | O que o produto deve fazer (requisitos funcionais e não funcionais) | `RF-*`, `RNF-*` |
| [BUSINESS_MODEL.md](BUSINESS_MODEL.md) | Modalidades, direitos de acesso, créditos, preços e economia unitária | — |
| [USER_JOURNEYS.md](USER_JOURNEYS.md) | Como os responsáveis usam o produto, de ponta a ponta | `J-*` |
| [MVP_SCOPE.md](MVP_SCOPE.md) | O que entra e o que fica fora do MVP; riscos e dependências | `R-*`, `D-*` |
| [PRODUCT_DECISIONS.md](PRODUCT_DECISIONS.md) | Registro de decisões aprovadas e de hipóteses a validar | `DP-*`, `H-*` |
| [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md) | Questões que ainda precisam de decisão, com recomendações | `QA-*` |

Decisões técnicas importantes serão registradas como ADRs na fase de arquitetura (ver [PRODUCT_DECISIONS.md](PRODUCT_DECISIONS.md#candidatos-a-adr)).

---

## 1. Visão

**O Mundo de Contos é uma biblioteca digital de histórias infantis, acolhedora e cuidadosamente ilustrada, onde responsáveis também podem criar histórias personalizadas em que a criança é protagonista.**

O produto existe para fortalecer momentos de conexão entre adultos e crianças por meio da leitura compartilhada.

A inteligência artificial é um meio, não a identidade do produto. A experiência deve lembrar uma estante de livros infantis, não uma interface genérica de IA.

## 2. Problema

Responsáveis por crianças pequenas querem ler com elas, mas enfrentam:

- dificuldade em encontrar conteúdo digital infantil seguro, bonito, sem anúncios e adequado à idade;
- pouca representatividade: muitas crianças não se reconhecem nos personagens dos livros;
- desejo de histórias que conversem com a rotina e as conquistas da criança (dormir, desfralde, primeiro dia na escola, chegada de um irmão);
- desconfiança em relação a aplicativos que capturam a atenção da criança, exibem publicidade ou coletam dados em excesso.

> Os itens acima são a premissa do produto e ainda não foram validados com pesquisa de usuários (ver hipóteses em [PRODUCT_DECISIONS.md](PRODUCT_DECISIONS.md#2-hipóteses-a-validar)).

## 3. Para quem

**Cliente e usuário administrador:** pais, mães e responsáveis por crianças de 0 a 6 anos que:

- desejam ler histórias com as crianças;
- valorizam conteúdo educativo, afetivo e visualmente bonito;
- desejam criar histórias em que a criança seja protagonista.

**Participante da leitura:** a criança. Ela participa da leitura junto ao adulto, mas **não** tem acesso independente a compras, configurações ou gerenciamento de conta.

## 4. Proposta de valor

1. **Biblioteca ilustrada** de histórias autorais, organizadas por tema e faixa etária.
2. **Histórias personalizadas** com IA, em que a criança é protagonista.
3. **Personagens configuráveis** que representam a diversidade com respeito.
4. **Conteúdo adaptado à idade**, do bebê à criança pré-escolar.
5. **Coleção pessoal** para guardar e reler as histórias favoritas e as criadas.
6. **Leitura como num livro ilustrado:** uma página por vez, ilustração grande, texto legível.
7. **Ambiente seguro:** sem anúncios, sem compras ao alcance da criança, com privacidade desde a concepção.

## 5. Princípios do produto

Estes princípios orientam decisões quando os requisitos não forem explícitos.

| # | Princípio | Na prática |
| --- | --- | --- |
| P1 | **Biblioteca primeiro, IA depois** | A navegação, a linguagem e o visual remetem a livros. Termos como "prompt", "modelo" ou "gerar com IA" não são o centro da interface. |
| P2 | **Leitura compartilhada** | O produto incentiva o adulto a ler *com* a criança. Não é posicionado como substituto da leitura presencial nem como forma de deixar bebês sozinhos diante da tela. |
| P3 | **Segurança infantil acima de conversão** | Nenhuma oferta, preço ou compra aparece em telas que a criança utiliza durante a leitura. Áreas adultas ficam atrás de barreira parental. |
| P4 | **Privacidade desde a concepção** | Coletar apenas o mínimo necessário sobre a criança. Nenhuma foto real no MVP. |
| P5 | **Transparência comercial** | Preço, periodicidade, início da cobrança e cancelamento sempre explícitos. Saldo de créditos sempre visível ao adulto. |
| P6 | **Sem publicidade** | Nenhuma modalidade exibe anúncios. |
| P7 | **Diversidade com respeito** | Personalização visual por características, não por categorias rígidas ou rótulos. |
| P8 | **Justiça com o cliente** | Falhas técnicas não consomem créditos; o que foi comprado ou criado não é perdido. |
| P9 | **Custo consciente** | Toda funcionalidade com custo variável (IA, armazenamento) nasce com limites e medição. |
| P10 | **Simplicidade** | Menos telas, menos opções, menos dependências. Evoluir só com necessidade concreta. |

## 6. O que o Mundo de Contos não é

- Não é um chatbot nem um "gerador de histórias" genérico.
- Não é uma plataforma de vídeos ou de entretenimento passivo.
- Não é um aplicativo para a criança usar sozinha.
- Não é um produto financiado por publicidade ou pela venda de dados.

## 7. Faixas etárias e diretrizes editoriais

| Faixa | Característica do conteúdo | Papel do adulto |
| --- | --- | --- |
| **0 a 2 anos** | Histórias curtas, imagens grandes, vocabulário simples. | Conduz a leitura. |
| **2 a 4 anos** | Repetição, emoções, situações familiares. | Leitura compartilhada. |
| **4 a 6 anos** | Aventuras, imaginação, pequenas jornadas. | Incentiva a participação crescente da criança. |

As diretrizes editoriais detalhadas (extensão do texto por página, vocabulário, temas sensíveis) dependem da política de conteúdo ([OPEN_QUESTIONS.md — QA-24](OPEN_QUESTIONS.md#qa-24)).

## 8. Categorias da biblioteca

1. Animais e natureza
2. Hora de dormir
3. Emoções e valores
4. Aventuras
5. Pequenas conquistas e autonomia
6. Família e carinho

## 9. Experiência em linhas gerais

- **Navegação inferior** com quatro áreas: **Início**, **Biblioteca**, **Criar** e **Minha coleção**.
- **Perfil e configurações** acessíveis a partir da tela Início.
- **Leitor:** uma página por vez no celular, ilustração grande, texto legível, navegação simples.
- **História personalizada:** capa, introdução, aproximadamente 5 a 7 páginas de história e encerramento.

Detalhes em [PRODUCT_REQUIREMENTS.md](PRODUCT_REQUIREMENTS.md) e [USER_JOURNEYS.md](USER_JOURNEYS.md).

## 10. Plataforma

- **Lançamento:** Android.
- **Evolução:** arquitetura preparada para uma futura versão iOS.
- **Idioma:** português brasileiro.

## 11. Como saberemos que estamos no caminho certo

Indicadores propostos (metas a definir após o baseline do MVP):

- **Indicador norte (proposta):** número de sessões de leitura concluídas por família ativa por semana — mede conexão por meio da leitura, não tempo de tela.
- **Saúde do negócio:** conversão do teste gratuito para assinatura paga, retenção mensal de assinantes, receita de créditos avulsos.
- **Saúde da operação:** custo médio por história gerada, taxa de sucesso de geração, tempo médio até a história ficar pronta.

A lista completa está em [MVP_SCOPE.md](MVP_SCOPE.md#7-métricas-de-acompanhamento).
