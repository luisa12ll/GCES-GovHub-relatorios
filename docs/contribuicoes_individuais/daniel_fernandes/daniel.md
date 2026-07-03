# Sprint 4 – 09/06/2026 a 30/06/2026

## Resumo da Sprint

Na Sprint 4, meu foco foi contribuir para a melhoria da qualidade e confiabilidade dos dados do projeto GovHub, especificamente no domínio do MCID, relacionado aos dados de empreendimentos FAR.

A principal entrega foi a implementação de testes de integridade em dbt para validar os modelos `empreendimento_far` e `evolucao_financeira`. A contribuição incluiu a criação de modelos dbt a partir das fontes do schema `mcid`, definição de testes no `schema.yml`, criação de macros reutilizáveis para validação de faixas numéricas e unicidade composta, além de um teste SQL específico para consistência das datas de contratação, conclusão e entrega.

## Atividades Realizadas

| Data | Atividade | Tipo | Link/Referência | Status |
|------|------------|------|----------------|---------|
| 30/06 | Criação dos modelos dbt para `empreendimento_far` e `evolucao_financeira` | Código | Commit `396a4ae` | ✅ Concluído |
| 30/06 | Configuração da source `mcid` no dbt | Código | `models/sources.yml` | ✅ Concluído |
| 30/06 | Adição da configuração de materialização e schema para modelos MCID | Código | `dbt_project.yml` | ✅ Concluído |
| 30/06 | Criação de testes de integridade para campos obrigatórios, unicidade, UFs válidas e faixas numéricas | Código/Testes | `schema.yml` | ✅ Concluído |
| 30/06 | Criação da macro `accepted_numeric_range` para validar valores mínimos e máximos | Código/Testes | `macros/tests/accepted_numeric_range.sql` | ✅ Concluído |
| 30/06 | Criação da macro `unique_combination_of_columns` para validar unicidade composta | Código/Testes | `macros/tests/unique_combination_of_columns.sql` | ✅ Concluído |
| 30/06 | Criação de teste SQL para validar consistência entre datas de contratação, conclusão e entrega | Código/Testes | `tests/test_empreendimento_far_datas_contratacao.sql` | ✅ Concluído |

## Maiores Avanços

- Implementei testes de integridade para os dados de empreendimentos FAR do MCID.
- Criei validações para garantir que a chave primária `apf` seja única e não nula.
- Adicionei validação para garantir que os valores de `uf` estejam dentro das siglas válidas dos estados brasileiros.
- Desenvolvi uma macro reutilizável para validar faixas numéricas, aplicada em campos financeiros e percentuais.
- Desenvolvi uma macro para validar unicidade composta entre colunas, utilizada no modelo `evolucao_financeira`.
- Criei um teste específico para verificar inconsistências entre datas de contratação, conclusão e entrega.
- Configurei os modelos dbt para consumir corretamente as tabelas do schema `mcid`.

## Maiores Dificuldades

- Entender a estrutura do projeto dbt dentro do repositório.
- Identificar onde declarar as `sources`, modelos, `schemas` e testes personalizados.
- Compreender como escrever testes genéricos reutilizáveis no dbt usando macros.
- Definir regras de validação coerentes para os dados de empreendimentos FAR.
- Ajustar os testes para cobrir a integridade dos dados sem criar validações excessivamente rígidas.

## Aprendizados

- Aprendi como estruturar testes de dados em dbt usando `schema.yml`.
- Aprendi a criar macros de testes genéricos reutilizáveis no dbt.
- Entendi melhor como declarar `sources` e modelos dentro da organização do projeto.
- Aprendi a validar qualidade de dados considerando unicidade, nulidade, domínio de valores e faixas numéricas.
- Ganhei mais familiaridade com o fluxo de contribuição em um projeto real de engenharia de dados.

## Plano Pessoal para a Próxima Sprint

Não há próximas sprints previstas.