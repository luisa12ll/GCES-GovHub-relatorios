# Diário de Bordo – Lucas Guimarães Borges

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint

Durante a Sprint 0, o foco principal foi a ambientação no projeto Gov Hub BR, compreendendo sua estrutura, propósito e fluxo de funcionamento. As atividades concentraram-se na configuração do ambiente de desenvolvimento, leitura da documentação oficial e estudo dos materiais disponibilizados, como o e-book do projeto.

Além disso, houve o primeiro contato prático com o fluxo de contribuição em um projeto de software livre, incluindo leitura de código, entendimento das dependências (como Airflow, Superset e dbt) e realização de commits no repositório oficial.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 15/04 - 17/04 | Leitura e estudo da documentação do projeto | Estudo | [Link](https://gov-hub.io/govhub/documentacao/instalacao/#make-test) | Concluído |
| 17/04 | Configuração inicial do ambiente | Código | [Comprobatórios](#comprobatórios) | Concluído |
| 17/04 | Leitura do e-book | Estudo | [Link](https://gov-hub.io/govhub/ebook-viewer/) | Concluído |
| 17/04 | Contribuição para o arquivo de build do projeto | Código | [Link commit](https://github.com/GovHub-br/data-application-gov-hub/commit/7c110e594a8017a52895f5b86b484d09f9e2b250) | Concluído |
| 17/04 | Contribuição para a documentação do projeto | Documentação | [Link commit 1](https://github.com/GovHub-br/gov-hub/commit/13fe3153e24e1c3ff6aa46f87ba467442104df41) <br>  [Link commit 2](https://github.com/GovHub-br/gov-hub/commit/e5dd9f6536826da7bbde5abe53307569356f7e04) | Concluído |

### Maiores Avanços

* Consegui configurar e rodar a aplicação do GovHub localmente, validando toda a stack (Airflow, Superset e dbt);
* Identifiquei gargalos no processo de setup e contribui diretamente com melhorias no build e na documentação do projeto;
* Realizei minhas primeiras contribuições efetivas no repositório oficial, incluindo código e documentação;
* Compreendi a arquitetura geral da aplicação e o fluxo de dados entre os componentes do ecossistema;

### Maiores Dificuldades

* Configuração inicial do ambiente local;
* Entendimento inicial da integração entre as ferramentas do projeto (Airflow, Superset e dbt);

### Aprendizados

* Processo completo de setup de um ambiente de dados utilizando Airflow, Superset e dbt;
* Importância de uma documentação clara e bem estruturada em projetos open source;
* Leitura e entendimento da arquitetura utilizada no GovHub;

### Plano Pessoal para a Próxima Sprint

* [ ] Aprofundar o entendimento da camada de dados;
* [ ] Explorar issues abertas para identificar oportunidades de contribuição técnica;
* [ ] Submeter pelo menos 1 Pull Request com melhoria relevante no projeto;

### Comprobatórios

1. Instalação das dependências com `make setup`

![Instalação das dependências com `make setup`](./assets/sprint0/img01.png)

2. Subindo o ambiente com `docker compose`

![Subindo o ambiente com `docker compose`](./assets/sprint0/img02.png)

3. Configuração das variáveis dentro do airflow

![Configuração das variáveis dentro do airflow](./assets/sprint0/img03.png)

4. Conexão do airflow com o banco de dados

![Conexão do airflow com o banco de dados](./assets/sprint0/img04.png)

5. Conexão do superset com o banco de dados bem sucedida

![Conexão do superset com o banco de dados bem sucedida](./assets/sprint0/img05.png)

6. Configuração do dbt

![Configuração do dbt](./assets/sprint0/img06.png)

![Configuração do dbt](./assets/sprint0/img07.png)

## Sprint 1 – [21/04/2026 – 04/05/2026]

### Resumo da Sprint

Durante a Sprint 1, o foco principal foi identificar e resolver issues abertas no projeto Gov Hub BR. As atividades concentraram-se na análise de problemas relatados, compreensão dos requisitos, implementação de soluções e submissão de Pull Requests para contribuir efetivamente ao projeto.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 03/05 - 04/05 | Identificar possíveis issues para contribuir | Discussão | [Issues do projeto](https://github.com/orgs/GovHub-br/projects/4/views/1?filterQuery=oss) | Concluído |
| 04/05 | Contribuição resolvendo a issue #255 | Código | [Link commit](https://github.com/GovHub-br/data-application-gov-hub/commit/0274e87032891d9e9d4d7fd7f70c6507d1338ec9) | Concluído |

### Maiores Avanços

* Identifiquei as principais issues abertas do projeto para a disciplina de GCES;
* Contribuí para uma issue no repositório oficial, resolvendo problemas reais do projeto;
* Consegui que meu Pull Request fosse aprovado e mergeado para a branch principal;

### Maiores Dificuldades

* Encontrar uma issue para contribuir que eu soubesse fazer no momento;

### Aprendizados

* Configuração do Airflow via CLI;

### Plano Pessoal para a Próxima Sprint

* [ ] Contribuir para outra issue;
* [ ] Submeter pelo menos 1 Pull Request com melhoria relevante no projeto;

## Sprint 2 – [05/05/2026 – 25/05/2026]

### Resumo da Sprint

Durante a Sprint 2, atuei na resolução da issue #116, implementando um pipeline de extração para dados do Censo Demográfico 2022 sobre Quilombolas. A entrega envolveu leitura via FTP do IBGE, parsing específico para planilhas com cabeçalhos complexos e carga idempotente no PostgreSQL.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 05/05 - 25/05 | Implementação do pipeline da issue #116 | Código | [Issue #116](https://github.com/GovHub-br/data-application-gov-hub/issues/116) | Concluído |
| 18/05 | Abertura do PR da issue #116 | Código/Doc | [PR #287](https://github.com/GovHub-br/data-application-gov-hub/pull/287) | Concluído |
| 25/05 | Commit final da entrega da issue #116 | Código | [Commit](https://github.com/GovHub-br/data-application-gov-hub/commit/4cfd3e7434529bbff515018eb675c984c6f34f2e) | Concluído |

### Principais Contribuições

* Implementação da DAG `quilombolas_alfabetizacao_censo_dag` para ingestão dos dados de Quilombolas do Censo 2022;
* Coleta dos dados via FTP (`ftp.ibge.gov.br`) com processamento dos arquivos `.xlsx` e índices `.txt`;
* Desenvolvimento do parser `quilombolas_parser.py` com flattening de cabeçalhos duplos/triplos;
* Carga no schema `censo_demografico` com nomenclatura `Q_A_C_D_*`, incluindo metadados e idempotência com `ON CONFLICT DO UPDATE`;
* Inclusão de comentários de tabela/coluna e criação de restrições únicas para PK composta quando necessário;
* Criação de testes unitários para o parser em `tests/test_quilombolas_parser.py`.

### Maiores Avanços

* Resolvi uma issue de maior complexidade técnica, com impacto direto na ingestão de dados do projeto;
* Padronizei o pipeline seguindo o padrão já utilizado no projeto (`mulheres_ingest_dag`);
* Estruturei uma solução robusta para dados com layout irregular em planilhas do IBGE.

### Maiores Dificuldades

* Entender o fluxo de funcionamento do Airflow e a orquestração completa da DAG;
* Lidar com os formatos de planilhas e cabeçalhos complexos do IBGE.

### Aprendizados

* Como projetar e implementar uma DAG no Airflow;
* Como organizar parsing, carga idempotente e testes para pipelines de dados.

### Plano Pessoal para a Próxima Sprint

* [ ] Acompanhar revisão dos mantenedores e ajustar o PR, se necessário;
* [ ] Contribuir com novas melhorias focadas em qualidade e testes.

## Sprint 3 – [26/05/2026 – 08/06/2026]

### Resumo da Sprint

Na Sprint 3, o foco foi contribuir na issue #306 com ênfase em testes para o repositório. O PR foi aberto e está aguardando aprovação dos mantenedores.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 26/05 - 27/05 | Desenvolvimento da solução da issue #306 com foco em testes | Código/Testes | [Issue #306](https://github.com/GovHub-br/data-application-gov-hub/issues/306) | Concluído |
| 27/05 | Abertura do PR da issue #306 | Código/Doc | [PR #329](https://github.com/GovHub-br/data-application-gov-hub/pull/329) | Concluído |
| 27/05 - 03/06 | Resolução da [Issue #318](https://github.com/GovHub-br/data-application-gov-hub/issues/318) | Código | [Issue #318](https://github.com/GovHub-br/data-application-gov-hub/issues/318) | Concluído |
| 31/05 | Commit final da entrega da issue #306 | Código | [Commit](https://github.com/GovHub-br/data-application-gov-hub/commit/a9ee872650713062e7acd99d40ad73ee6154348a) | Concluído |

### Maiores Avanços

* Estruturei uma contribuição orientada a testes para melhorar a confiabilidade da plataforma;
* Submeti o PR #329 e ele foi integrado a branch main sem problemas.

### Maiores Dificuldades

* Não havia testes prévios suficientes para servir como padrão;
* Foi necessário construir os testes do zero, definindo estratégia e estrutura inicial.

### Aprendizados

* Aprendi como contribuir com testes no repositório;
* Aprendi mais sobre definição de estratégia de testes em um contexto com baixa cobertura inicial.

### Plano Pessoal para a Próxima Sprint

* [ ] Continuar evoluindo a suíte de testes do projeto.

## Sprint 4 – [09/06/2026 – 22/06/2026]

### Resumo da Sprint

Na Sprint 4, o foco foi contribuir na issue #319, #370, Projeto Individual no GitLab e Projeto Extra de Pipeline de dados não estruturados no GitHub. Os PR's foram abertos e estão aguardando aprovação dos mantenedores.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 13/06 | Desenvolvimento do projeto individual da disciplina | Código | [Projeto Individual GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-lucas-borges) | Concluído |
| 13/06 | Desenvolvimento do projeto extra de pipeline de dados não estruturados | Código | [Projeto Extra GitHub](https://github.com/lcsgborges/uda-housing-pipeline) | Concluído |
| 15/06 | PR aberto para realizar a issue #318 | Código | [PR](https://github.com/GovHub-br/data-application-gov-hub/pull/369) | Concluído |
| 15/06 | Commit final da entrega da issue #319 | Código | [Commit](https://github.com/GovHub-br/data-application-gov-hub/commit/c091abb710dae4b90c704f4e7e79097e6fc91edb) | Concluído |
| 15/06 | PR aberto para realizar a issue #301 | Código | [PR](https://github.com/GovHub-br/data-application-gov-hub/pull/370) | Concluído |

### Maiores Avanços

* Estruturei uma contribuição orientada a testes para melhorar a confiabilidade da plataforma;
* Submeti o PR para realizar issue #319 e ele foi integrado a branch main sem problemas.
* Submeti o PR para realizar issue #301 e estou aguardando ser integrado na branch main.
* Realizei os projetos individuais e extras propostos pela disciplina.

### Maiores Dificuldades

* Entender como funcionava Kubernetes e como integrar no projeto individual;
* Entender protocolos de comunicação no projeto individual;
* Implementar a pipeline de dados não estruturados para seguir os requisitos do projeto extra;

### Aprendizados

* Aprendi como contribuir com testes no repositório;
* Aprendi mais sobre definição de estratégia de testes em um contexto com baixa cobertura inicial.
* Aprendi mais sobre Kubernetes e certificados;

### Plano Pessoal para a Próxima Sprint

* [ ] Continuar evoluindo a suíte de testes do projeto;
