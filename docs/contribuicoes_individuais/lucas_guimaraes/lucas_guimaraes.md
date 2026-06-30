# Diário de Bordo – Lucas Guimarães Borges

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint

Durante a Sprint 0, o foco principal foi a ambientação no projeto Gov Hub BR e a compreensão de sua estrutura, seu propósito e seu fluxo de funcionamento. As atividades concentraram-se na configuração do ambiente de desenvolvimento, na leitura da documentação oficial e no estudo dos materiais disponibilizados, como o e-book do projeto.

Além disso, houve o primeiro contato prático com o fluxo de contribuição em um projeto de software livre, incluindo a leitura do código, o entendimento das dependências (como Airflow, Superset e dbt) e a realização de commits no repositório oficial.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 15/04 - 17/04 | Leitura e estudo da documentação do projeto | Estudo | [Link](https://gov-hub.io/govhub/documentacao/instalacao/#make-test) | Concluído |
| 17/04 | Configuração inicial do ambiente | Código | [Comprobatórios](#comprobatórios) | Concluído |
| 17/04 | Leitura do e-book | Estudo | [Link](https://gov-hub.io/govhub/ebook-viewer/) | Concluído |
| 17/04 | Contribuição para o arquivo de build do projeto | Código | [Link do commit](https://github.com/GovHub-br/data-application-gov-hub/commit/7c110e594a8017a52895f5b86b484d09f9e2b250) | Concluído |
| 17/04 | Contribuição para a documentação do projeto | Documentação | [Link do commit 1](https://github.com/GovHub-br/gov-hub/commit/13fe3153e24e1c3ff6aa46f87ba467442104df41) <br> [Link do commit 2](https://github.com/GovHub-br/gov-hub/commit/e5dd9f6536826da7bbde5abe53307569356f7e04) | Concluído |

### Maiores Avanços

* Consegui configurar e executar a aplicação do Gov Hub localmente, validando todo o conjunto de tecnologias (Airflow, Superset e dbt);
* Identifiquei gargalos no processo de configuração e contribuí diretamente com melhorias no build e na documentação do projeto;
* Realizei minhas primeiras contribuições efetivas no repositório oficial, incluindo código e documentação;
* Compreendi a arquitetura geral da aplicação e o fluxo de dados entre os componentes do ecossistema.

### Maiores Dificuldades

* Configuração inicial do ambiente local;
* Entendimento inicial da integração entre as ferramentas do projeto (Airflow, Superset e dbt).

### Aprendizados

* Processo completo de configuração de um ambiente de dados utilizando Airflow, Superset e dbt;
* Importância de uma documentação clara e bem estruturada em projetos de código aberto;
* Leitura e entendimento da arquitetura utilizada no Gov Hub.

### Plano Pessoal para a Próxima Sprint

* [ ] Aprofundar o entendimento da camada de dados;
* [ ] Explorar issues abertas para identificar oportunidades de contribuição técnica;
* [ ] Submeter pelo menos um Pull Request com uma melhoria relevante para o projeto.

### Comprobatórios

1. Instalação das dependências com `make setup`

![Instalação das dependências com `make setup`](./assets/sprint0/img01.png)

2. Inicialização do ambiente com `docker compose`

![Inicialização do ambiente com `docker compose`](./assets/sprint0/img02.png)

3. Configuração das variáveis no Airflow

![Configuração das variáveis no Airflow](./assets/sprint0/img03.png)

4. Conexão do Airflow com o banco de dados

![Conexão do Airflow com o banco de dados](./assets/sprint0/img04.png)

5. Conexão bem-sucedida do Superset com o banco de dados

![Conexão bem-sucedida do Superset com o banco de dados](./assets/sprint0/img05.png)

6. Configuração do dbt

![Configuração do dbt](./assets/sprint0/img06.png)

![Configuração do dbt](./assets/sprint0/img07.png)

## Sprint 1 – [21/04/2026 – 04/05/2026]

### Resumo da Sprint

Durante a Sprint 1, o foco principal foi identificar e resolver issues abertas no projeto Gov Hub BR. As atividades concentraram-se na análise dos problemas relatados, na compreensão dos requisitos, na implementação de soluções e na submissão de Pull Requests, com o objetivo de contribuir efetivamente para o projeto.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 03/05 - 04/05 | Identificação de possíveis issues para contribuição | Discussão | [Issues do projeto](https://github.com/orgs/GovHub-br/projects/4/views/1?filterQuery=oss) | Concluído |
| 04/05 | Contribuição para a resolução da issue #255 | Código | [Link do commit](https://github.com/GovHub-br/data-application-gov-hub/commit/0274e87032891d9e9d4d7fd7f70c6507d1338ec9) | Concluído |

### Maiores Avanços

* Identifiquei as principais issues abertas do projeto para a disciplina de GCES;
* Contribuí para a resolução de uma issue no repositório oficial, solucionando um problema real do projeto;
* Consegui que meu Pull Request fosse aprovado e integrado à branch principal.

### Maiores Dificuldades

* Encontrar uma issue para a qual eu pudesse contribuir com o conhecimento que possuía naquele momento.

### Aprendizados

* Configuração do Airflow via CLI.

### Plano Pessoal para a Próxima Sprint

* [ ] Contribuir para outra issue;
* [ ] Submeter pelo menos um Pull Request com uma melhoria relevante para o projeto.

## Sprint 2 – [05/05/2026 – 25/05/2026]

### Resumo da Sprint

Durante a Sprint 2, atuei na resolução da issue #116, implementando um pipeline de extração de dados do Censo Demográfico 2022 sobre quilombolas. A entrega envolveu a leitura dos dados via FTP do IBGE, o parsing específico de planilhas com cabeçalhos complexos e a carga idempotente no PostgreSQL.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 05/05 - 25/05 | Implementação do pipeline da issue #116 | Código | [Issue #116](https://github.com/GovHub-br/data-application-gov-hub/issues/116) | Concluído |
| 18/05 | Abertura do PR da issue #116 | Código/Doc | [PR #287](https://github.com/GovHub-br/data-application-gov-hub/pull/287) | Concluído |
| 25/05 | Commit final da entrega da issue #116 | Código | [Commit](https://github.com/GovHub-br/data-application-gov-hub/commit/4cfd3e7434529bbff515018eb675c984c6f34f2e) | Concluído |

### Principais Contribuições

* Implementação da DAG `quilombolas_alfabetizacao_censo_dag` para a ingestão dos dados de quilombolas do Censo 2022;
* Coleta dos dados via FTP (`ftp.ibge.gov.br`) com o processamento dos arquivos `.xlsx` e índices `.txt`;
* Desenvolvimento do parser `quilombolas_parser.py` com o achatamento de cabeçalhos duplos e triplos;
* Carga no esquema `censo_demografico` com nomenclatura `Q_A_C_D_*`, incluindo metadados e idempotência com `ON CONFLICT DO UPDATE`;
* Inclusão de comentários em tabelas e colunas e criação de restrições de unicidade para chaves primárias compostas, quando necessário;
* Criação de testes unitários para o parser em `tests/test_quilombolas_parser.py`.

### Maiores Avanços

* Resolvi uma issue de maior complexidade técnica, com impacto direto na ingestão de dados do projeto;
* Padronizei o pipeline seguindo o padrão já utilizado no projeto (`mulheres_ingest_dag`);
* Estruturei uma solução robusta para dados com formato irregular em planilhas do IBGE.

### Maiores Dificuldades

* Entender o fluxo de funcionamento do Airflow e a orquestração completa da DAG;
* Lidar com os formatos de planilhas e cabeçalhos complexos do IBGE.

### Aprendizados

* Como projetar e implementar uma DAG no Airflow;
* Como organizar o parsing, a carga idempotente e os testes para pipelines de dados.

### Plano Pessoal para a Próxima Sprint

* [ ] Acompanhar a revisão dos mantenedores e ajustar o PR, se necessário;
* [ ] Contribuir com novas melhorias focadas em qualidade e testes.

## Sprint 3 – [26/05/2026 – 08/06/2026]

### Resumo da Sprint

Na Sprint 3, o foco foi contribuir para a resolução da issue #306, com ênfase nos testes do repositório. O PR foi posteriormente aprovado e integrado à branch main.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 26/05 - 27/05 | Desenvolvimento da solução da issue #306 com foco em testes | Código/Testes | [Issue #306](https://github.com/GovHub-br/data-application-gov-hub/issues/306) | Concluído |
| 27/05 | Abertura do PR da issue #306 | Código/Doc | [PR #329](https://github.com/GovHub-br/data-application-gov-hub/pull/329) | Concluído |
| 27/05 - 03/06 | Resolução da [issue #318](https://github.com/GovHub-br/data-application-gov-hub/issues/318) | Código | [Issue #318](https://github.com/GovHub-br/data-application-gov-hub/issues/318) | Concluído |
| 31/05 | Commit final da entrega da issue #306 | Código | [Commit](https://github.com/GovHub-br/data-application-gov-hub/commit/a9ee872650713062e7acd99d40ad73ee6154348a) | Concluído |

### Maiores Avanços

* Estruturei uma contribuição orientada a testes para melhorar a confiabilidade da plataforma;
* Submeti o PR #329, que foi integrado à branch main sem problemas.

### Maiores Dificuldades

* Não havia testes prévios em quantidade suficiente para estabelecer um padrão;
* Foi necessário construir os testes do zero, definindo uma estratégia e uma estrutura iniciais.

### Aprendizados

* Aprendi como contribuir com testes no repositório;
* Aprendi mais sobre a definição de uma estratégia de testes em um contexto com baixa cobertura inicial.

### Plano Pessoal para a Próxima Sprint

* [ ] Continuar evoluindo a suíte de testes do projeto.

## Sprint 4 – [09/06/2026 – 30/06/2026]

### Resumo da Sprint

Na Sprint 4, o foco foi contribuir para a resolução das issues #318, #319 e #301, além de desenvolver o projeto individual no GitLab e o projeto extra de pipeline de dados não estruturados no GitHub. Os PRs referentes às issues #318 e #301 foram aprovados pelos mantenedores e integrados à branch main em 29/06.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 13/06 | Desenvolvimento do projeto individual da disciplina | Código | [Projeto Individual GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-lucas-borges) | Concluído |
| 13/06 | Desenvolvimento do projeto extra de pipeline de dados não estruturados | Código | [Projeto Extra GitHub](https://github.com/lcsgborges/uda-housing-pipeline) | Concluído |
| 15/06 | Abertura do PR para resolver a issue #318 | Código | [PR](https://github.com/GovHub-br/data-application-gov-hub/pull/369) | Concluído |
| 15/06 | Commit final da entrega da issue #319 | Código | [Commit](https://github.com/GovHub-br/data-application-gov-hub/commit/c091abb710dae4b90c704f4e7e79097e6fc91edb) | Concluído |
| 15/06 | Abertura do PR para resolver a issue #301 | Código | [PR](https://github.com/GovHub-br/data-application-gov-hub/pull/370) | Concluído |
| 29/06 | Aprovação e integração do PR da issue #318 | Código | [Link do commit](https://github.com/GovHub-br/data-application-gov-hub/commit/a9ab04aa68853c64f240aefcada556af9fd8977d) | Concluído |
| 29/06 | Aprovação e integração do PR da issue #301 | Código | [Link do commit](https://github.com/GovHub-br/data-application-gov-hub/commit/5deb520f590e32dd1d90820cf10cbb0ab17c2ea6) | Concluído |

### Maiores Avanços

* Estruturei uma contribuição orientada a testes para melhorar a confiabilidade da plataforma;
* Submeti o PR para resolver a issue #318, que foi aprovado e integrado à branch main em 29/06;
* Submeti o PR para resolver a issue #301, que foi aprovado e integrado à branch main em 29/06;
* Realizei os projetos individual e extra propostos pela disciplina.

### Maiores Dificuldades

* Entender como o Kubernetes funcionava e como integrá-lo ao projeto individual;
* Entender os protocolos de comunicação utilizados no projeto individual;
* Implementar o pipeline de dados não estruturados de acordo com os requisitos do projeto extra.

### Aprendizados

* Aprendi como contribuir com testes no repositório;
* Aprendi mais sobre a definição de uma estratégia de testes em um contexto com baixa cobertura inicial;
* Aprendi mais sobre Kubernetes e certificados.

### Plano Pessoal para a Próxima Sprint

* Não há próximas sprints.
