# Diário de Bordo – Matheus de Siqueira Brant

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 

### Resumo da Sprint
Nesta sprint, o foco principal foi configurar o ambiente do projeto e entender melhor como funciona o processo de contribuição.

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 17/04 | Leitura e estudo da documentação do projeto | Estudo | [link - Documentação](https://gov-hub.io/govhub/sobre-projeto/overview/) | Concluído |
| 19/04 | Configuração inicial do ambiente | Código | [link - Guia de instalação](https://gov-hub.io/govhub/documentacao/instalacao/) | Concluído |
| 20/04 | Rastreamento de good first issues | Estudo | [link - GitHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Em andamento |

### Atividades realizadas - detalhamento 



<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">1
. Subindo o ambiente com `docker compose`</span></summary>

![docker](assets/imagem01.png)

<p align="center"></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">2
. Configuração do Airflow e Superset + conexão do superset com o banco de dados bem sucedida</span></summary>

![airflow](assets/imagem02.png)
![superset](assets/imagem03.png)
<p align="center"></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">3.Configurando e utilizando o Superset</span></summary>

![airflow](assets/imagem04.png)
![superset](assets/imagem05.png)
<p align="center"></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">4. Api contratos dag e dados carregados</span></summary>

![airflow](assets/imagem06.png)
![superset](assets/imagem07.png)
<p align="center"></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">5. Configurações dbt</span></summary>

![airflow](assets/imagem06.png)
![superset](assets/imagem07.png)
<p align="center"></p>
</details>

### Maiores Avanços
* Consegui finalizar na configuração do ambiente local.
* Entendi melhor a estrutura do repositório.
* Comecei a explorar as issues do projeto.
* Aprendi melhor como o projeto está organizado.

### Maiores Dificuldades
* A configuração do ambiente levou mais tempo do que eu esperava.
* Tive dificuldade com algumas dependências e comandos.
* Entendimento inicial do projeto.


### Aprendizados
* Fluxo de contribuição do projeto.
* Organização geral do repositório.
* Etapas para rodar o projeto localmente.

### Plano Pessoal para a Próxima Sprint
* [ ] Escolher uma issue para trabalhar.
* [ ] Contribuir com pelo menos 1 PR.
* [ ] Participar da revisão de código de um colega.

---

## Sprint 1 

### Resumo da Sprint
Nesta sprint, estudei a estrutura do GovHub até identificar uma oportunidade de contribuição na documentação. A partir disso, abri a issue [#104](https://github.com/GovHub-br/gov-hub/issues/104) e desenvolvi uma nova página chamada `Sistemas Integrados`.

O diferencial dessa entrega foi criar uma página prática e objetiva, complementar à página `Sistemas Estruturantes`. Enquanto a página já existente explica o contexto dos sistemas, a nova página apresenta um panorama direto das integrações já implementadas no projeto.

### Atividades Realizadas
| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 21/04 - 23/04 | Estudo do repositório e da documentação até identificar uma oportunidade de contribuição | Estudo | GovHub BR | Concluído |
| 24/04 | Definição e abertura da issue sobre panorama das integrações do GovHub | Discussão/Doc | [Issue #104](https://github.com/GovHub-br/gov-hub/issues/104) | Concluído |
| 25/04 - 28/04 | Criação da página `Sistemas Integrados` no fork do projeto | Doc | [Issue #104](https://github.com/GovHub-br/gov-hub/issues/104) | Concluído |
| 29/04 | Ajuste do escopo da página para diferenciá-la de `Sistemas Estruturantes` | Doc | [Issue #104](https://github.com/GovHub-br/gov-hub/issues/104) | Concluído |
| 30/04 - 02/05 | Inclusão no menu e validação manual da documentação em ambiente local | Doc/Teste | [Issue #104](https://github.com/GovHub-br/gov-hub/issues/104) | Concluído |
| 04/05 | Abertura do Pull Request com a contribuição no fork | Doc | PR do fork GovHub | Concluído |

### Implementação da Issue #104

O foco desta entrega foi criar uma nova página de documentação voltada ao panorama das integrações existentes no GovHub.

As principais atividades foram:

- **Estudo do sistema:** analisei a estrutura do portal e da documentação até encontrar uma lacuna que pudesse ser tratada com uma contribuição pequena e útil.
- **Abertura da issue #104:** formalizei a proposta de criar uma página voltada às integrações já existentes no GovHub.
- **Criação da página `Sistemas Integrados`:** desenvolvi uma página com foco prático, listando sistemas e bases integrados.
- **Ajuste de escopo:** refinei o conteúdo para que a página não repetisse `Sistemas Estruturantes` e funcionasse como um inventário objetivo.
- **Validação local:** testei a navegação e o carregamento da página no ambiente local da documentação.

### Maiores Avanços
* Identifiquei uma oportunidade de contribuição após estudar o sistema.
* Criei uma página complementar à documentação existente, sem repetir o conteúdo conceitual.
* Validei a contribuição localmente antes de abrir o PR.
* Relacionei a entrega à issue #104 do repositório principal.

### Maiores Dificuldades
* No início, a página ficou muito parecida com `Sistemas Estruturantes`.
* Foi necessário entender a navegação do `mkdocs.yml` para posicionar corretamente a nova página.
* A validação precisou ser feita com Docker Compose, e não com `mkdocs` direto.

### Aprendizados
* Entendi melhor a organização da documentação do GovHub.
* Aprendi a diferenciar uma página conceitual de uma página de inventário prático.
* Pratiquei o fluxo de contribuição com fork, issue, commit e Pull Request.
* Aprendi a validar localmente um portal MkDocs com Docker Compose.

### Comprobatórios da Issue #104

- Página criada: `docs/sobre-projeto/sistemas-integrados.md`
- Item adicionado ao menu em `mkdocs.yml`
- Issue aberta no repositório principal: [#104](https://github.com/GovHub-br/gov-hub/issues/104)
- Pull Request aberto a partir do fork para o repositório GovHub

### Plano Pessoal para a Próxima Sprint
* [ ] Acompanhar a revisão do Pull Request e responder aos comentários dos mantenedores.
* [ ] Buscar uma nova contribuição no GovHub, preferencialmente envolvendo documentação ou integração de dados.

---

## Sprint 2

### Resumo da Sprint
Nesta sprint, o planejamento inicial era atuar na issue [[GCES] Ingestão BACEN - Crédito Imobiliário por PIB #40](https://github.com/GovHub-br/data-application-gov-hub/issues/40), relacionada à ingestão de dados do BACEN. Durante a análise inicial, encontrei dificuldades para avançar com segurança no escopo da ingestão, especialmente por envolver entendimento mais detalhado da fonte de dados e da estrutura esperada para o pipeline.

Diante disso, redirecionei minha contribuição para uma issue mais alinhada ao estado atual do projeto e ao meu entendimento da camada dbt: [Renomear tabela pessoas.hierarquia para pessoas.forca_trabalho #372](https://github.com/GovHub-br/data-application-gov-hub/issues/372). A partir dessa issue, trabalhei na refatoração do modelo de dados de pessoas, atualizando o nome do modelo `hierarquia` para `forca_trabalho`, ajustando referências downstream e documentando a mudança. A contribuição foi enviada por meio do Pull Request [GovHub-br/data-application-gov-hub#383](https://github.com/GovHub-br/data-application-gov-hub/pull/383).

### Atividades Realizadas
| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 09/06 - 11/06 | Análise inicial da issue de ingestão BACEN - Crédito Imobiliário por PIB | Estudo | [Issue #40](https://github.com/GovHub-br/data-application-gov-hub/issues/40) | Interrompido |
| 12/06 | Reavaliação do escopo e escolha de nova issue para contribuição | Discussão/Estudo | [Issue #372](https://github.com/GovHub-br/data-application-gov-hub/issues/372) | Concluído |
| 13/06 - 15/06 | Refatoração do modelo `pessoas.hierarquia` para `pessoas.forca_trabalho` | Código/dbt | [Issue #372](https://github.com/GovHub-br/data-application-gov-hub/issues/372) | Concluído |
| 15/06 - 16/06 | Atualização das referências downstream e da documentação do modelo no `schema.yml` | Código/Doc | `servidores_completos.sql`, `distribuicao_raca_cor_sexo_servidores_.sql`, `schema.yml` | Concluído |
| 16/06 | Criação de teste dbt para validar cargo de estagiários em `forca_trabalho` | Teste/dbt | `estagiarios_nome_cargo_not_null.sql` | Concluído |
| 17/06 | Abertura do Pull Request com a contribuição | Código/Doc | [PR #383](https://github.com/GovHub-br/data-application-gov-hub/pull/383) | Concluído |

### Implementação da Issue #372

O foco da entrega foi alinhar o nome do modelo de pessoas ao conceito de força de trabalho utilizado pelo dashboard do IPEA.

As principais atividades foram:

- **Renomeação do modelo dbt:** o modelo `pessoas.hierarquia` foi refatorado para `pessoas.forca_trabalho`, deixando o nome da tabela mais coerente com o domínio de negócio.
- **Atualização de referências downstream:** os modelos que consumiam `ref("hierarquia")` foram atualizados para `ref("forca_trabalho")`, evitando quebra no grafo dbt.
- **Atualização da documentação:** o `schema.yml` da camada gold foi ajustado para documentar o novo modelo `forca_trabalho`.
- **Validação específica para estagiários:** foi adicionado um teste singular dbt para garantir que registros de estagiários não fiquem com `nome_cargo` nulo ou vazio.
- **Abertura do PR:** a contribuição foi consolidada no Pull Request [#383](https://github.com/GovHub-br/data-application-gov-hub/pull/383).

### Maiores Avanços
* Consegui adaptar o planejamento da sprint após identificar dificuldades na issue de ingestão BACEN.
* Contribuí em uma refatoração importante da camada dbt de pessoas.
* Atualizei referências downstream para preservar a consistência do grafo de modelos.
* Adicionei validação dbt relacionada ao preenchimento do cargo de estagiários.
* Abri o Pull Request #383 no repositório `data-application-gov-hub`.

### Maiores Dificuldades
* A issue inicialmente escolhida, relacionada à ingestão BACEN, exigia um entendimento maior da fonte de dados e do desenho do pipeline, o que dificultou o avanço dentro do tempo da sprint.
* Foi necessário entender melhor a relação entre os modelos `hierarquia`, `servidores_completos` e as tabelas de dashboard.
* A validação completa com `dbt run` e `dbt test` não pôde ser concluída localmente por diferenças entre o ambiente local e o ambiente esperado do projeto, especialmente a configuração de database `analytics` e a ausência das fontes carregadas localmente.

### Aprendizados
* Entendi melhor como o dbt organiza dependências entre modelos por meio de `ref()`.
* Aprendi a fazer uma refatoração de modelo preservando referências downstream.
* Compreendi a importância de registrar limitações de validação no Pull Request quando o ambiente local não replica completamente o ambiente de dados real.
* Reforcei a importância de adaptar o escopo da contribuição quando uma issue se mostra mais complexa do que o previsto.

### Comprobatórios da Issue #372

- Issue trabalhada: [Renomear tabela pessoas.hierarquia para pessoas.forca_trabalho #372](https://github.com/GovHub-br/data-application-gov-hub/issues/372)
- Pull Request aberto: [GovHub-br/data-application-gov-hub#383](https://github.com/GovHub-br/data-application-gov-hub/pull/383)
- Modelo criado: `airflow_lappis/dags/dbt/ipea/models/pessoas_dbt/gold/forca_trabalho.sql`
- Teste criado: `airflow_lappis/dags/dbt/ipea/tests/estagiarios_nome_cargo_not_null.sql`

### Plano Pessoal para a Próxima Sprint
* [ ] Acompanhar a revisão do PR #383 e responder aos comentários dos mantenedores.
* [ ] Validar a execução completa em ambiente com fontes carregadas, caso seja solicitado na revisão.
* [ ] Buscar uma nova issue de contribuição, preferencialmente em dbt ou documentação de modelos.

---

## Sprint 3

### Resumo da Sprint
Nesta sprint, trabalhei na issue [Mapear uso de tabelas Raw/Bronze/Silver em gráficos e propor camada Gold #376](https://github.com/GovHub-br/data-application-gov-hub/issues/376), relacionada à identificação de gráficos e painéis que ainda dependem de dados fora da camada Gold.

O objetivo da contribuição foi rastrear as fontes de dados consumidas pelos dashboards atuais, identificar pontos em que a visualização depende de Raw, Bronze, Silver ou de exportadores sem linhagem versionada, e propor uma modelagem Gold para centralizar essas regras de negócio no dbt.

A contribuição foi enviada por meio do Pull Request [GovHub-br/data-application-gov-hub#423](https://github.com/GovHub-br/data-application-gov-hub/pull/423).

### Atividades Realizadas
| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 24/06 - 25/06 | Análise dos dashboards, arquivos JSON públicos e consultas versionadas no repositório de dados | Estudo/Doc | [Issue #376](https://github.com/GovHub-br/data-application-gov-hub/issues/376) | Concluído |
| 25/06 | Mapeamento das origens atuais dos gráficos e identificação de consumos em Gold, Silver/Bronze inferidos e origens sem exportador versionado | Doc | `gov-hub/docs/land/public/data/*.json`, `dashboard_servidores_dag.py`, `cliente_postgres.py` | Concluído |
| 25/06 - 26/06 | Elaboração da matriz de linhagem De -> Para relacionando gráfico, origem atual e Gold proposta | Doc | `docs/mapeamento_linhagem_dashboards_gold.md` | Concluído |
| 26/06 | Proposta técnica de novas tabelas/views Gold para Orçamento, Contratos, TEDs e Aposentadorias | Doc/dbt | [Issue #376](https://github.com/GovHub-br/data-application-gov-hub/issues/376) | Concluído |
| 26/06 | Configuração do ambiente Poetry para rodar a suíte de testes Python | Teste/Infra | `poetry run pytest tests` | Concluído |
| 26/06 | Preparação da mensagem de Pull Request referenciando a issue #376 | Doc/Discussão | [Issue #376](https://github.com/GovHub-br/data-application-gov-hub/issues/376) | Concluído |
| 26/06 | Abertura do Pull Request com a contribuição | Doc/Discussão | [PR #423](https://github.com/GovHub-br/data-application-gov-hub/pull/423) | Concluído |

### Implementação da Issue #376

O foco desta entrega foi produzir um relatório técnico de mapeamento e especificação, deixando a implementação das tabelas Gold para uma issue futura de desenvolvimento.

As principais atividades foram:

- **Mapeamento dos dashboards:** analisei os dashboards disponíveis no `gov-hub`, principalmente `Visão Geral IPEA`, `Acompanhamento Orçamentário` e `Dashboard de visão geral de pessoal`.
- **Rastreamento das fontes:** relacionei os arquivos JSON consumidos no front-end com os modelos dbt e consultas existentes no repositório `data-application-gov-hub`.
- **Identificação da camada atual:** diferenciei os gráficos que já consomem Gold daqueles que dependem de Silver/Bronze inferido ou de exportadores não versionados.
- **Criação da matriz de linhagem:** documentei a relação entre gráfico, origem atual e futura tabela/view Gold proposta.
- **Modelagem proposta:** especifiquei tabelas/views Gold para os domínios de Orçamento, Contratos, TEDs e Pessoas, incluindo granularidade, fontes recomendadas, colunas e regras de negócio.
- **Validação:** configurei o ambiente Poetry com Python 3.11 e rodei a suíte de testes do projeto.

### Maiores Avanços
* Entendi melhor a relação entre os dashboards públicos do GovHub e os modelos dbt do repositório de dados.
* Identifiquei que o dashboard novo de Pessoas já consome Gold, enquanto parte da página `Visão Geral IPEA` ainda depende de JSONs sem exportador versionado no repositório.
* Produzi uma matriz de linhagem De -> Para com os principais gráficos e cards analisados.
* Propus uma camada Gold mais adequada para centralizar regras de negócio hoje espalhadas entre front-end, JSONs e modelos intermediários.
* Consegui rodar a suíte de testes Python do projeto após ajustar o ambiente Poetry.

### Maiores Dificuldades
* Nem todos os JSONs consumidos pelo front-end possuem exportador versionado no repositório `data-application-gov-hub`, o que exigiu separar evidência direta de inferência técnica.
* Foi necessário cruzar informações entre dois repositórios: `data-application-gov-hub` e `gov-hub`.
* A validação inicial com `pytest` falhou por dependências ausentes no ambiente local, exigindo configuração do virtualenv Poetry com Python 3.11 e instalação das dependências mínimas.
* Como a issue pedia especificação para implementação futura, foi importante limitar a entrega ao relatório e não iniciar a criação das tabelas dbt.

### Aprendizados
* Aprendi a rastrear linhagem entre front-end, arquivos JSON, DAGs, consultas Python e modelos dbt.
* Entendi melhor a importância da camada Gold para evitar regras de negócio espalhadas em dashboards.
* Pratiquei a separação entre mapeamento documentado, inferência técnica e implementação efetiva.
* Reforcei a importância de validar contribuições documentais com a suíte de testes do projeto quando possível.

### Comprobatórios da Issue #376

- Issue trabalhada: [Mapear uso de tabelas Raw/Bronze/Silver em gráficos e propor camada Gold #376](https://github.com/GovHub-br/data-application-gov-hub/issues/376)
- Pull Request aberto: [GovHub-br/data-application-gov-hub#423](https://github.com/GovHub-br/data-application-gov-hub/pull/423)
- Relatório criado: `docs/mapeamento_linhagem_dashboards_gold.md`
- Matriz de linhagem: seção `Matriz de linhagem De -> Para`
- Propostas Gold documentadas:
  - `orcamento.dashboard_resumo_anual`
  - `orcamento.dashboard_orcamento_por_acao`
  - `orcamento.dashboard_execucao_por_elemento_despesa`
  - `contratos.dashboard_contratos_por_categoria`
  - `contratos.dashboard_orcamento_contratos`
  - `contratos.dashboard_top_fornecedores_natureza_despesa`
  - `contratos.dashboard_acompanhamento_orcamentario`
  - `contratos.dashboard_acompanhamento_orcamentario_mensal`
  - `ted.dashboard_teds_resumo`
  - `ted.dashboard_teds_detalhamento`
  - `pessoas.dashboard_aposentadorias_mensal`
- Validação executada: `poetry run pytest tests`
- Resultado dos testes: `42 passed`

### Plano Pessoal para a Próxima Sprint
* [ ] Acompanhar a revisão do PR #423 relacionado à issue #376.
* [ ] Ajustar o relatório caso os mantenedores peçam mais detalhes de linhagem ou modelagem.
* [ ] Buscar uma issue de implementação das tabelas Gold propostas, caso ela seja aberta pelo projeto.

---

## Sprint 4

### Resumo da Sprint
Nessa sprint, foquei totalmente na entrega do projeto individual da disciplina, o jogo `mk.js`. Dediquei meu tempo para atualizar o código legado para um ambiente Node moderno, automatizar testes e verificações de segurança no pipeline do GitLab, e estruturar a infraestrutura de execução com Docker, Kubernetes e Terraform.

O projeto foi desenvolvido no repositório [trabalho-final-gces-matheus-brant](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-matheus-brant), com a evolução registrada no histórico de [commits da branch main](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-matheus-brant/-/commits/main).

### Atividades Realizadas
| Atividade | Tipo | Referência | Status |
| --------- | ---- | ---------- | ------ |
| Modernização do projeto `mk.js` para execução com Node.js atual | Código/Infra | `package.json`, `.nvmrc`, `server/` | Concluído |
| Configuração de execução local, Docker e Docker Compose com Postgres | Infra | `Dockerfile`, `docker-compose.yml` | Concluído |
| Inclusão de build, lint, testes unitários, fuzzing, cobertura e auditoria de dependências | Teste/CI | Pipeline GitLab | Concluído |
| Configuração de verificações de segurança, SAST/SCA e qualidade com SonarCloud | Segurança/CI | `sonar-project.properties`, documentação de segurança | Concluído |
| Criação da estrutura de produção com imagem Node, imagem Nginx e publicação de imagens | Infra/CD | `Dockerfile.prod`, `Dockerfile.nginx` | Concluído |
| Criação dos manifests Kubernetes, Ingress com TLS, políticas de rede e infraestrutura com Terraform | Infra/DevOps | `k8s/`, Terraform | Concluído |
| Documentação do uso, execução, qualidade, segurança e evidências finais | Doc | `README.md`, `docs/SEGURANCA.md`, `docs/RELATORIO_FINAL.md` | Concluído |

### Entregas e Comprobatórios

- Repositório do projeto individual: [GitLab - trabalho-final-gces-matheus-brant](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-matheus-brant)
- Histórico de commits: [commits da branch main](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-matheus-brant/-/commits/main)
- Aplicação base: `mk.js`, com frontend em HTML5 Canvas/JavaScript e backend em Node.js/Express
- Execução local documentada com `npm start`
- Execução containerizada documentada com Docker e Docker Compose
- Testes e qualidade documentados com `npm run lint`, `npm run test:unit`, `npm run test:fuzz`, `npm test`, `npm run coverage` e `npm run audit`
- Infraestrutura documentada com Kubernetes, Ingress com TLS, políticas de rede e Terraform

### Aprendizados
* Pratiquei a modernização de uma aplicação legada em JavaScript/Node.js.
* Consolidei o uso de CI para build, lint, testes, fuzzing, cobertura e verificações de segurança.
* Aprofundei a integração entre aplicação, containers, banco de dados, Kubernetes e infraestrutura como código.
* Organizei as evidências do trabalho final em documentação reproduzível.

---

## Sprint 5

### Resumo da Sprint
Nesta sprint, trabalhei na issue [test: Implementar testes para mcid/metadata #297](https://github.com/GovHub-br/data-application-gov-hub/issues/297), relacionada à inclusão de testes básicos de integridade e nulidade nas tabelas de metadados do projeto dbt.

Durante a análise do repositório, verifiquei que não existia um diretório `airflow_lappis/dags/dbt/mcid` no checkout atual nem nas branches upstream consultadas. Por isso, concentrei a implementação nas tabelas `models_metadata` dos projetos dbt existentes no repositório, `ipea` e `mir`, registrando essa limitação na validação e na mensagem de PR.

A contribuição foi enviada por meio do Pull Request [GovHub-br/data-application-gov-hub#425](https://github.com/GovHub-br/data-application-gov-hub/pull/425).

### Atividades Realizadas
| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 29/06 | Análise da issue #297 e inspeção da estrutura dbt do repositório | Estudo/Código | [Issue #297](https://github.com/GovHub-br/data-application-gov-hub/issues/297) | Concluído |
| 29/06 | Verificação da ausência do diretório `dbt/mcid` no checkout e nas branches upstream | Estudo | `airflow_lappis/dags/dbt` | Concluído |
| 29/06 | Adição de testes `not_null` nos metadados dos projetos `ipea` e `mir` | Teste/dbt | `models/metadata/schema.yml` | Concluído |
| 29/06 | Criação do teste genérico `unique_combination_of_columns` para validar a chave composta `schema_name` + `table_name` | Teste/dbt | `macros/data_quality/unique_combination_of_columns.sql` | Concluído |
| 29/06 | Validação de sintaxe YAML e preparação da mensagem de Pull Request | Teste/Doc | `python3`, `git diff --check` | Concluído |
| 29/06 | Abertura do Pull Request com a contribuição | Teste/Doc | [PR #425](https://github.com/GovHub-br/data-application-gov-hub/pull/425) | Concluído |

### Implementação da Issue #297

O foco da entrega foi aumentar a cobertura de testes das tabelas de metadata do dbt, garantindo que campos essenciais estejam preenchidos e que cada modelo seja identificado de forma única pela combinação de schema e tabela.

As principais atividades foram:

- **Levantamento da estrutura dbt:** analisei os projetos disponíveis em `airflow_lappis/dags/dbt` e confirmei que os projetos existentes eram `ipea` e `mir`.
- **Investigação do escopo MCID:** busquei referências a `mcid` no checkout local e em branches remotas do upstream, mas não encontrei um projeto dbt `mcid`.
- **Testes de nulidade:** adicionei `not_null` para `database_name`, `materialization` e `run_id`, além dos testes já existentes para `schema_name`, `table_name` e `dt_transform`.
- **Teste de integridade:** criei o teste genérico `unique_combination_of_columns` para validar que a combinação `schema_name` + `table_name` não se repete em `models_metadata`.
- **Atualização dos schemas:** apliquei os testes em `airflow_lappis/dags/dbt/ipea/models/metadata/schema.yml` e `airflow_lappis/dags/dbt/mir/models/metadata/schema.yml`.

### Maiores Avanços
* Contribuí com testes dbt voltados à qualidade e governança da tabela de metadados.
* Criei um teste genérico reutilizável para validação de chave composta.
* Mantive a solução compatível com o padrão de macros `test_...` já usado no repositório.
* Documentei a limitação encontrada sobre a ausência do projeto dbt `mcid`.

### Maiores Dificuldades
* A issue mencionava explicitamente `mcid/metadata`, mas o repositório não possuía esse caminho na estrutura dbt atual.
* Foi necessário investigar o fork local e branches upstream para evitar criar arquivos em um projeto inexistente.
* Não foi possível executar `dbt parse` ou `dbt test` localmente porque o binário `dbt` não estava disponível no ambiente shell nem no ambiente Poetry.

### Aprendizados
* Entendi melhor como o dbt permite declarar testes genéricos por macros com prefixo `test_`.
* Aprendi a validar uma chave composta em dbt sem depender de pacotes externos como `dbt_utils`.
* Reforcei a importância de verificar a estrutura real do repositório antes de implementar exatamente o caminho descrito na issue.
* Pratiquei o registro transparente de limitações de ambiente e de escopo no PR.

### Comprobatórios da Issue #297

- Issue trabalhada: [test: Implementar testes para mcid/metadata #297](https://github.com/GovHub-br/data-application-gov-hub/issues/297)
- Pull Request aberto: [GovHub-br/data-application-gov-hub#425](https://github.com/GovHub-br/data-application-gov-hub/pull/425)
- Arquivos atualizados:
  - `airflow_lappis/dags/dbt/ipea/models/metadata/schema.yml`
  - `airflow_lappis/dags/dbt/mir/models/metadata/schema.yml`
- Macros criadas:
  - `airflow_lappis/dags/dbt/ipea/macros/data_quality/unique_combination_of_columns.sql`
  - `airflow_lappis/dags/dbt/mir/macros/data_quality/unique_combination_of_columns.sql`
- Validação executada: sintaxe YAML com `python3`
- Checagem executada: `git diff --check`
- Validação não executada: `dbt test`, por ausência do binário `dbt` no ambiente local

