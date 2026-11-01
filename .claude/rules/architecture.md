# Arquitetura

## Diretrizes aprovadas

- **Monorepo com aplicações independentes** (DP-009). A estrutura exata será definida em ADR.
- **Sem microsserviços** sem necessidade concreta, demonstrada e registrada em ADR (DP-009).
- Direção tecnológica (DP-010): React Native + Expo + TypeScript (app); NestJS + TypeScript (backend); PostgreSQL; object storage; processamento assíncrono; Google Play Billing. Os detalhes de cada item serão formalizados em ADR.
- Arquitetura preparada para iOS (DP-007): regras de negócio e direitos de acesso vivem no backend, não no app (RNF-PORT-01).

## Camadas e dependências

- **Domínio:** entidades, regras e políticas puras. Não importa framework, ORM, SDK de provedor, HTTP nem fila.
- **Aplicação:** casos de uso que orquestram o domínio por meio de interfaces (portas).
- **Infraestrutura:** implementações das portas (banco, storage, provedores de IA, Google Play, fila).
- **Interface:** controllers HTTP, workers, telas.
- A dependência aponta sempre para dentro: interface → aplicação → domínio; infraestrutura → domínio (implementa portas).
- Sem dependências circulares entre módulos ou pacotes. Se surgir uma, extraia o conceito comum ou inverta a dependência.
- Código compartilhado entre apps vai para `packages/` só quando houver dois consumidores reais.

## Contratos públicos

Mudar qualquer item abaixo exige avaliação de impacto escrita (no design técnico) e, se incompatível, um plano de migração:

- API HTTP do backend (rotas, payloads, códigos de erro).
- Esquema do banco de dados e migrações.
- Mensagens de fila e jobs assíncronos.
- IDs de produtos e de assinaturas na Google Play.
- Chaves de configuração comercial (preços, pacotes, franquias, limites).
- Deep links e notificações push.
- Formato de histórias e páginas armazenadas no object storage.

O app publicado não se atualiza sozinho: mudanças de API precisam manter compatibilidade com as versões do app em uso.

## Quando abrir um ADR

Use `/novo-adr` quando a decisão:

- escolher ou trocar tecnologia, biblioteca estrutural, provedor ou serviço externo;
- definir ou mudar a estrutura do monorepo, a fronteira entre módulos ou um contrato público;
- afetar segurança, privacidade, custo operacional relevante ou a portabilidade para iOS;
- for difícil de reverter.

Os candidatos já identificados estão em [PRODUCT_DECISIONS.md](../../docs/product/PRODUCT_DECISIONS.md#candidatos-a-adr).
