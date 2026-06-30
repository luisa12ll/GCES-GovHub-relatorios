# Diário de Bordo – João Vitor Lopes Ribeiro

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0

### Resumo da Sprint

Essa sprint foi destinada ao entendimento e ambientação do projeto. Os esforços dessa etapa foram destinados ao estudo da documentação do GovHubBR, com o intuito de compreender o objetivo do projeto e sua arquitetura, bem como subir o ambiente de execução da solução localmente.

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 21/04 | Configuração inicial do ambiente | Código | – | Concluído |
| 20/04 | Leitura e estudo da documentação do projeto | Estudo | [link wiki](https://gov-hub.io/govhub/comunidade/guia-contribuicao/) | Concluído |
| 21/04 | Abertura de issue para bug em módulo X | Discussão | [link issues](https://github.com/GovHub-br/data-application-gov-hub/issues) | Em andamento |

### Maiores Avanços

* Entendi melhor o objetivo do GovHubBR.
* Entendi melhor a arquitetura do GovHubBR.
* Aprendi como contribuir ao projeto segundo às diretrizes guia de contribuição.
* Aprendi a rodar a aplicação localmente utilizando docker.

    Docker

![docker_containers](./assets/sprint0/docker_containers.png)

     Airflow (List Task Instance)

![airflow_list_task_instance](./assets/sprint0/airflow.png)

    Superset

![superset](./assets/sprint0/superset.png)
    
    DBT debug

![dbt_debug](./assets/sprint0/dbt_debug.png)
    
    DBT run

![dbt_run](./assets/sprint0/dbt_run.png)


### Maiores Dificuldades
* Incompatibilidade da versão python local com a exigida pelo projeto

![incompatible_python_version](./assets/sprint0/incompatible_python_version.png)

### Aprendizados
* Utilização da ferramenta 'uv' para seleção de um versão python.
* Melhor compreensão do projeto.
* Fluxo de contribuição do projeto.

### Plano Pessoal para a Próxima Sprint
* [ ] Identificar Issue para contribuir.
* [ ] Contribuir com pelo menos 1 PR.
* [ ] Participar da revisão de código de um colega.


## Sprint 1

Durante a Sprint 1, o foco principal foi a busca por identificar issues nos repositórios do projeto e contribuir com ao menos um pull request.  

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 21/04 - 04/05 | Busca por issues para contruibuir | Discussão | [Issues abertas disponíveis a contribuição](https://github.com/GovHub-br/data-application-gov-hub/issues?q=is%3Aissue%20state%3Aopen%20label%3AOSS) | Concluído |
| 13/04 | Definição da escolha e estudo de issue para resolução | Estudo | [Comentário na issue](https://github.com/GovHub-br/data-application-gov-hub/issues/121#issuecomment-4444620055) | Concluído |

### Maiores avanços

* Estudo da issue [Extração - Unidades de Conservação](https://github.com/GovHub-br/data-application-gov-hub/issues/121) para contribuição me permitiu entender o funcionamento dos DAG's utilizados no projeto e estratégias de extrações de dados de arquivos *.xlsx*.

### Maiores dificuldades

* Falta de issues para contribuição
    * A issue estudada para contruibuição já havia sido escolhida por uma dupla no grupo, como isso não estava visível no repositório acabei por investir tempo para seu estudo/resolução que não foi até então aproveitado.

### Aprendizados

* Funcionamento dos DAG's na ingestão de dados
* Estratégias de extrações de dados de arquivos *.xlsx*

### Plano Pessoal para a Próxima Sprint
- [x] Identificar Issue para contribuir.
- [x] Contribuir com pelo menos 1 PR.

## Sprint 2

### Resumo da Sprint

Durante a Sprint 2, o foco principal foi novamente a busca por identificar issues nos repositórios do projeto e contribuir com ao menos um pull request. Nela foi implementado um workflow para auto-atribuição de issues utilizando GitHub Actions com o intuito de facilitar o fluxo de contribuição no projeto..

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 22/05 | Escolha da Issue | Discussão | [Comentário na issue](https://github.com/GovHub-br/data-application-gov-hub/issues/292#issuecomment-4519763868) | Concluído |
| 25/05 | Desenvolvimento da solução a issue | Código | [Commit](https://github.com/Joa0V/data-application-gov-hub/commit/86076bf70bb346f3ccec9a33788c0f1515c3e1af) | Conclído |
| 25/05 | Abertura do pull request | Código/Doc | [Pull Request](https://github.com/GovHub-br/data-application-gov-hub/pull/327) | Concluído, aguardando review |

### Maiores Avanços

* Primeira contribuição prática para o projeto.
* Maior familiaridade com o fluxo de contribuição open source do projeto.


### Principais contribuições

* Implementação de um workflow para auto-atribuição de issues nos repositórios do projeto
    * Ativado apenas em comentários em issues, excluíndo comentários em PR's
    * Parsing de comandos ('/take' e '/issue')
    * Validação baseadas nas permissões no repositório

### Maiores dificuldades

* Entender as limitações e comportamentos do GitHub Actions em repositórios de teste.
    * Os testes do workflow tiveram de ser realizados em um repositório diferente do projeto principal. Dessa forma, os testes cobriram principalmente a lógica implementada, mas não toda a execução no ambiente final do projeto.

### Aprendizados

* Funcionamento básico do github actions.
* Estruturação de workflows automatizados
* Validação de permissões e labels em automações do GitHub.

### Plano Pessoal para a Próxima Sprint
* [ ] Acompanhar andamento do PR aberto e aplicar possíveis ajustes solicitados durante o review..
* [ ] Identificar Issue para contribuir.
* [ ] Contribuir com pelo menos 1 PR.