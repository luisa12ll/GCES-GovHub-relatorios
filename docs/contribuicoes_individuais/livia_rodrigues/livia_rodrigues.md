# Diário de Bordo – Lívia Rodrigues Reis

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint

A Sprint 0 teve como principal objetivo a ambientação no projeto Gov Hub BR, com foco no entendimento da arquitetura, estudo das documentações e configuração do ambiente de desenvolvimento local. Durante esse período, consegui compreender o fluxo de contribuição do projeto, além de realizar a configuração do ambiente e iniciar interações com o repositório por meio da análise e abertura de issues.

### Atividades Realizadas

| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 18/04 | Configuração inicial do ambiente | Código | [Guia de Instalação](https://gov-hub.io/govhub/documentacao/instalacao/) | Concluído |
| 19/04 | Leitura e estudo da documentação do projeto | Estudo | [Documentação](https://gov-hub.io/govhub/sobre-projeto/overview/) | Concluído |
| 20/04 | Estudo do fluxo de contribuição e análise de issues | Estudo | [Guia de Contribuição](https://gov-hub.io/govhub/comunidade/guia-contribuicao/) | Concluído |

### Maiores Avanços

* Consegui configurar o ambiente local e rodar os principais serviços do projeto;
* Entendi a estrutura do repositório e como os componentes do projeto se conectam;
* Compreendi o fluxo de contribuição e a importância das issues dentro do projeto;
* Evoluí na leitura e interpretação de documentações técnicas.

### Maiores Dificuldades

* Complexidade na configuração inicial do ambiente devido à quantidade de ferramentas envolvidas;
* Necessidade de ajustes em dependências e versões para execução correta;
* Entendimento inicial da arquitetura do projeto exigiu mais tempo de estudo.

### Aprendizados

* Fluxo de contribuição em projetos open source;
* Importância da documentação para onboarding em projetos complexos;
* Configuração de ambientes utilizando múltiplas ferramentas integradas;
* Uso de GitHub Issues para organização e rastreabilidade de demandas.

### Plano Pessoal para a Próxima Sprint

* [ ] Identificar uma issue adequada para contribuição prática;
* [ ] Participar da revisão de código de um colega;
* [ ] Aprofundar o entendimento técnico sobre os componentes do projeto.

---

## Sprint 1 – [21/04/2026 – 04/05/2026]

### Resumo da Sprint

Nesta sprint trabalhei em dupla com a [Ana Letícia](https://github.com/analeticiaa) na **Issue #38** do repositório `data-application-cidades`, que solicitava a criação de uma DAG dedicada no Apache Airflow para a ingestão diária dos dados da **Pesquisa Industrial Mensal – Produção Física Brasil (PIM-PF Brasil)**, divulgada pelo IBGE através da API SIDRA (agregado 8888). O projeto já possuía uma DAG genérica de ingestão do IBGE, e nosso objetivo foi isolar a PIM-PF em uma DAG própria, seguindo o padrão de *ownership* e observabilidade adotado pelo repositório. Ao final da sprint, concluímos a implementação e abrimos o Pull Request para revisão dos mantenedores.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ---- | --------- | --------------------------------- | --------------- | ------ |
| 21/04 - 23/04 | Busca e análise de *good first issues* e estudo das DAGs existentes do IBGE | Estudo | [Issues - GovHub Cidades](https://github.com/GovHub-br/data-application-cidades/issues) | Concluído |
| 24/04 - 28/04 | Desenvolvimento da DAG de ingestão da PIM-PF Brasil (Issue #38) | Código | [Issue #38](https://github.com/GovHub-br/data-application-cidades/issues/38) | Concluído |
| 29/04 | Escrita da documentação (`README.md`) das DAGs IBGE | Doc | [Issue #38](https://github.com/GovHub-br/data-application-cidades/issues/38) | Concluído |
| 30/04 | Revisão em dupla do código e testes locais | Estudo/Código | - | Concluído |
| 04/05 | Abertura do Pull Request da Issue #38 | Código/Doc | [Issue #38](https://github.com/GovHub-br/data-application-cidades/issues/38) | Concluído |

### Implementação da Issue #38

O foco da entrega foi criar uma DAG dedicada (`ibge_pim_pf_brasil_ingest_dag`) para coletar, transformar e persistir os dados da PIM-PF Brasil de forma automatizada e idempotente. As principais atividades foram:

* **DAG dedicada por dataset:** criamos o arquivo `ibge_pim_pf_brasil_ingest_dag.py` com um `DEFAULT_CONFIG` contendo todos os parâmetros da requisição à API do IBGE (agregado, variáveis, períodos, nível geográfico, localidade, classificação e categoria), permitindo *override* parcial via Airflow Variable (`IBGE_PIM_PF_BRASIL_CONFIG`).
* **Task única `fetch_and_store`:** responsável por ler a configuração efetiva, chamar o `ClienteIBGE`, transformar a resposta, conectar ao PostgreSQL e persistir os dados com `INSERT ... ON CONFLICT DO UPDATE`.
* **Carga idempotente:** definimos uma chave primária composta `(variavel_id, localidade_id, periodo, classificacao_id, categoria_id)`, garantindo que a DAG possa ser reexecutada sem duplicar registros e captando automaticamente as revisões retroativas publicadas pelo IBGE.
* **Tratamento de erros diferenciado:** utilizamos `AirflowFailException`, `AirflowSkipException` e `AirflowException` para sinalizar corretamente cada estado na UI do Airflow (failed, skipped, error).
* **Documentação:** escrevemos um `README.md` para a pasta de DAGs do IBGE, descrevendo fonte de dados, frequência, schema da tabela destino, configuração via Airflow Variable e a estratégia de carga incremental.

### Maiores Avanços

* Entreguei, em dupla, uma DAG funcional e idempotente para ingestão da PIM-PF Brasil.
* Compreendi na prática a motivação arquitetural das DAGs dedicadas por dataset (observabilidade e *schedule* independentes, *ownership* claro).
* Aplicação prática da estratégia `ON CONFLICT DO UPDATE` para garantir confiabilidade da ingestão.
* Abertura e submissão do Pull Request da Issue #38.

### Maiores Dificuldades

* Compreender a estrutura de resposta da API SIDRA do IBGE, em que cada combinação de variável × localidade × período × classificação × categoria gera um registro separado.
* Definir corretamente a chave primária composta da tabela, considerando que `classificacao_id` e `categoria_id` podem ser nulos ou concatenados.
* Navegar em uma base de código existente, lendo outras DAGs para reutilizar os utilitários do projeto (`ClienteIBGE`, `ClientPostgresDB`, `get_postgres_conn`, `get_dynamic_schedule`) e respeitar as convenções do repositório.

### Aprendizados

* Entendimento aprofundado do funcionamento do Apache Airflow e do ciclo de vida de uma DAG.
* Boas práticas de separação entre código do *scheduler* e do *worker* (evitar parse de configuração no top-level do arquivo da DAG).
* Escrita de documentação técnica voltada ao mantenedor futuro.

### Plano Pessoal para a Próxima Sprint

- [X] Ter o PR aberto para revisão
- [X] Encontrar novas issues para contribuir em dupla
- [ ] Acompanhar e atender à revisão dos mantenedores

---

## Sprint 2 – [05/05/2026 – 17/05/2026]

### Resumo da Sprint

Continuei trabalhando em dupla com a [Ana Letícia](https://github.com/analeticiaa), desta vez na **Issue #311** do repositório `data-application-gov-hub`, filha da issue pai #305 ("Testes Unitários dos Clientes Airflow"). A demanda era criar o plugin `cliente_fgv.py` — responsável por encapsular as requisições HTTP à API de índices econômicos da FGV (Fundação Getulio Vargas) — e escrever seus respectivos testes unitários. Como o arquivo do cliente ainda não existia no repositório, tivemos que criá-lo seguindo o padrão dos demais clientes do projeto e, em seguida, cobri-lo com testes. Esta entrega foi desenvolvida em colaboração, com uso de co-autoria nos commits.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ---- | --------- | --------------------------------- | --------------- | ------ |
| 05/05 - 08/05 | Estudo da hierarquia de issues (#305 / #311) e dos clientes existentes (`cliente_base.py`, `cliente_abecip.py`) | Estudo | [Issue #311](https://github.com/GovHub-br/data-application-gov-hub/issues/311) | Concluído |
| 09/05 - 13/05 | Criação do plugin `cliente_fgv.py` seguindo o padrão do projeto | Código | [Issue #311](https://github.com/GovHub-br/data-application-gov-hub/issues/311) | Concluído |
| 14/05 - 16/05 | Escrita dos testes unitários (`test_cliente_fgv.py`) com mock das requisições HTTP | Código | [Issue #311](https://github.com/GovHub-br/data-application-gov-hub/issues/311) | Concluído |
| 17/05 | Revisão, execução dos testes/lint e abertura do Pull Request | Código/Doc | [Issue #311](https://github.com/GovHub-br/data-application-gov-hub/issues/311) | Concluído |

### Implementação da Issue #311

* **`cliente_fgv.py`:** criamos a classe `ClienteFgv`, herdando de `ClienteBase`, com os métodos `get_indices()` (lista de índices econômicos disponíveis) e `get_serie(codigo_serie, data_inicio, data_fim)` (dados de uma série temporal específica, com filtros opcionais de intervalo de datas e construção dinâmica dos `params`). Todos os métodos foram tipados de forma consistente com o restante do projeto.
* **`test_cliente_fgv.py`:** escrevemos quatro testes unitários cobrindo os cenários principais — sucesso do `get_indices()`, `get_serie()` com todos os parâmetros, `get_serie()` apenas com o `codigo_serie` (validando que parâmetros opcionais nulos não aparecem nos `params`) e um teste de isolamento de rede mockando diretamente o `httpx.Client`.

### Maiores Avanços

* Criação de um plugin novo do zero, respeitando o padrão de herança, tipagem e estrutura de testes do projeto.
* Cobertura de testes em dois níveis de isolamento (mock em `request()` e mock em `httpx.Client.request`).
* Prática de co-autoria em commits Git (`Co-authored-by`), reforçando a rastreabilidade das contribuições da dupla.

### Maiores Dificuldades

* Descobrir que o arquivo `cliente_fgv.py` citado na issue não existia: foi necessário investigar o repositório e inferir o padrão correto a partir de clientes similares (`cliente_abecip.py`).
* Sincronizar o *fork* com o `upstream` antes de iniciar o desenvolvimento, lidando com divergências de histórico.
* Entender a hierarquia entre a issue filha (#311) e a issue pai (#305) para delimitar corretamente o escopo da contribuição.

### Aprendizados

* A importância de ler o código existente antes de escrever qualquer linha nova.
* Técnicas de *mocking* em diferentes níveis para testar clientes HTTP sem dependência de rede real.
* Tratamento de parâmetros opcionais e construção dinâmica de `params` em requisições.
* Fluxo prático de trabalho colaborativo em dupla com co-autoria nos commits.

### Plano Pessoal para a Próxima Sprint

- [X] Acompanhar a revisão dos PRs abertos e atender aos apontamentos
- [X] Validar o merge das contribuições
- [ ] Iniciar os trabalhos individuais da disciplina

---

## Sprint 3 – [18/05/2026 – 01/06/2026]

### Resumo da Sprint

Nesta sprint, eu e a [Ana Letícia](https://github.com/analeticiaa) finalizamos o acompanhamento dos Pull Requests abertos nas sprints anteriores (Issues #38 e #311), atendendo aos comentários da revisão dos mantenedores até a aprovação. Em paralelo, busquei novas issues do GovHub para contribuir e participei da revisão de código de colegas, encerrando o ciclo de contribuições colaborativas antes de iniciar os trabalhos individuais da disciplina.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ---- | --------- | --------------------------------- | --------------- | ------ |
| 18/05 - 22/05 | Acompanhamento dos PRs e análise dos comentários da revisão | Código/Doc | [Issue #38](https://github.com/GovHub-br/data-application-cidades/issues/38) · [Issue #311](https://github.com/GovHub-br/data-application-gov-hub/issues/311) | Concluído |
| 23/05 - 27/05 | Desenvolvimento das alterações solicitadas na revisão | Código | - | Concluído |
| 28/05 | Participação na revisão de código de colegas | Discussão/Código | - | Concluído |
| 29/05 - 01/06 | Busca de novas issues e validação do merge das contribuições | Estudo | [Issues - GovHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Concluído |

### Maiores Avanços

* Atendimento aos pontos levantados na revisão dos PRs das Issues #38 e #311.
* Acompanhamento do processo de revisão até a aprovação/merge.
* Participação ativa na revisão de código de colegas, contribuindo com o fluxo do projeto.

### Maiores Dificuldades

* Adequar o código às solicitações dos mantenedores exigiu releitura das convenções do projeto.
* Conciliar o acompanhamento dos PRs com a busca por novas issues dentro do período da sprint.

### Aprendizados

* Compreensão mais sólida do ciclo de revisão em projetos open source.
* Importância de manter o acompanhamento contínuo dos PRs após a abertura.
* Valor da revisão de código entre pares para a qualidade do projeto.

### Plano Pessoal para a Próxima Sprint

- [X] Validar o merge final das contribuições no GovHub
- [X] Iniciar e desenvolver os trabalhos individuais da disciplina

---

## Sprint 4 – [02/06/2026 – 15/06/2026]

### Resumo da Sprint

Nesta sprint, foquei nos **trabalhos individuais da disciplina**. Foram dois projetos: o **trabalho individual** (obrigatório), com foco nas práticas de GCES — containerização, pipeline de CI/CD e qualidade de código — aplicadas de ponta a ponta sobre um projeto legado; e um **projeto de ponto extra**, um pipeline auditável de análise de dados não estruturados (UDA) para o setor habitacional.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ---- | --------- | --------------------------------- | --------------- | ------ |
| 02/06 | Estudo dos requisitos do trabalho individual e clonagem do repositório base | Estudo | [Repositório pessoal (GitLab)](https://gitlab.com/liviarodriguesre/trabalho-individual-gces-livia-rodrigues) | Concluído |
| 03/06 - 08/06 | Desenvolvimento do trabalho individual (containerização, CI/CD e qualidade de código) | Código | [Repositório oficial (GitLab)](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-livia-rodrigues) | Concluído |
| 09/06 - 12/06 | Desenvolvimento do projeto de ponto extra (pipeline UDA auditável) | Código | [PR #66](https://github.com/unb-Sistemas-de-Machine-learning/Projetos-Individuais-2026-1/pull/66) | Concluído |
| 13/06 - 15/06 | Ajustes finais, testes e documentação dos dois projetos | Código/Doc | - | Concluído |

### Projeto 1 – Trabalho Individual

O trabalho individual da disciplina consistiu em aplicar as práticas de GCES sobre um projeto, abordando as fases de **containerização (Docker)**, **pipeline de CI/CD (GitLab CI)** e **qualidade de código**.

Comecei o desenvolvimento no meu repositório pessoal, clonando o projeto base, e posteriormente migrei para o repositório oficial da disciplina, após o monitor me conceder acesso:

* **Repositório pessoal:** [trabalho-individual-gces-livia-rodrigues](https://gitlab.com/liviarodriguesre/trabalho-individual-gces-livia-rodrigues)
* **Repositório oficial da disciplina:** [trabalho-final-gces-livia-rodrigues](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-livia-rodrigues)

### Projeto 2 – Ponto Extra

Pipeline **auditável de análise de dados não estruturados (UDA)** para a conjuntura do setor habitacional. O objetivo foi extrair métricas operacionais de relatórios em PDF emitidos por incorporadoras (com layouts heterogêneos), em que abordagens tradicionais baseadas em *regex*/coordenadas quebram a cada mudança de layout.

* **Link:** [PR #66 – Projetos-Individuais-2026-1](https://github.com/unb-Sistemas-de-Machine-learning/Projetos-Individuais-2026-1/pull/66)
* **Arquitetura em três camadas:** ingestão (*polling* dos centros de RI com idempotência via SHA-256), processamento (extração de texto com PyMuPDF, *chunking* híbrido e extração via LLM com contrato semântico Pydantic) e serviço (catálogo SQLite com *lineage* e API REST `GET /api/conjuntura`).
* **Tecnologias:** Python, PyMuPDF, Pydantic, FastAPI e Claude API (com modo *offline* determinístico).
* **Destaques:** contratos semânticos anti-alucinação, rastreabilidade de dados (*data lineage*) via hash dos documentos e cobertura de testes (19 testes passando), validada contra layouts tabulares e em slides.

### Maiores Avanços

* Estruturei o trabalho individual com foco nas fases de containerização, CI/CD e qualidade de código sobre um projeto legado.
* Migração do desenvolvimento do repositório pessoal para o repositório oficial da disciplina.
* Entrega do projeto de ponto extra com um pipeline UDA auditável, testado e documentado.

### Maiores Dificuldades

* Adaptar e configurar o projeto legado para rodar em containers e integrar com o GitLab CI exigiu ajustes de dependências e ambiente.
* Migrar o trabalho do repositório pessoal para o oficial sem perder o histórico de contribuições.
* No projeto extra, lidar com a heterogeneidade dos layouts dos PDFs e garantir a extração confiável sem alucinações, usando contratos semânticos para validar os dados.

### Aprendizados

* Estruturação de um pipeline de GitLab CI do zero.
* Aplicação prática de containerização e do fluxo de DevOps em um projeto end-to-end, mesmo partindo de um código legado.
* Técnicas de extração de dados não estruturados com LLM de forma auditável, com idempotência e rastreabilidade de dados.

### Plano Pessoal para a Próxima Sprint

- [ ] Voltar a contribuir no GovHub