---
paths:
  - "apps/api/**"
---

# Backend

> Caminho provisório até o ADR de estrutura do monorepo. Direção tecnológica: NestJS + TypeScript + PostgreSQL (DP-010); detalhes em ADR.

## Organização

- Monólito modular: um módulo NestJS por contexto de negócio (por exemplo: contas, perfis, catálogo, histórias, créditos, billing). Os nomes finais serão definidos em ADR.
- Em cada módulo, separe domínio, aplicação, infraestrutura e interface ([architecture.md](architecture.md)).
- O domínio não importa `@nestjs/*`, ORM, SDKs de provedores nem bibliotecas HTTP.
- Módulos se comunicam por serviços de aplicação ou eventos explícitos, nunca acessando o repositório de outro módulo.

## API

- Payloads validados na borda (DTOs). Nada não validado chega à aplicação.
- Erros com formato consistente e códigos estáveis. Não exponha stack traces nem detalhes de provedores.
- Operações que criam efeitos (criar história, conceder créditos, processar compra) aceitam chave de idempotência.
- Mudança de contrato segue as regras de contratos públicos de [architecture.md](architecture.md).

## Persistência

- Migrações versionadas, revisadas e aplicáveis para frente. Nunca edite uma migração já aplicada em ambiente compartilhado.
- O livro-razão de créditos é apenas de acréscimo. O saldo é derivado dos lançamentos ou de uma projeção reconstruível a partir deles.
- Valores monetários em centavos (inteiros). Datas em UTC.

## Processamento assíncrono

- Jobs são idempotentes e podem ser reexecutados com segurança.
- Retentativas têm teto configurável (RNF-COST-02). Esgotado o teto, a falha libera o crédito reservado (DP-022).
- Estados da geração são explícitos e persistidos (por exemplo: na fila, gerando, pronta, falhou).

## Provedores externos (IA, Google Play, storage)

- Acessados apenas por portas (interfaces) do domínio, com adaptadores na infraestrutura.
- Nos testes, use implementações falsas das portas; testes automatizados nunca chamam provedores reais.
- Registre o custo de cada chamada a provedor de IA associado à história (RNF-COST-01).

## Configuração

- Preços, pacotes, franquias, limites e quantidade de perfis vêm de configuração (DP-024), com registro de quem alterou e quando (RNF-AUD-02).
- A configuração é validada na inicialização: o serviço não sobe com configuração inválida.
