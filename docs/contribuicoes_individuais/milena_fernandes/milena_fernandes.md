# Diário de Bordo – Milena Fernandes Rocha

**Equipe:** Gov Hub BR
**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint

Esta sprint teve como foco a ambientação técnica no projeto, abrangendo a configuração do ambiente de desenvolvimento, análise da documentação oficial e compreensão da arquitetura de dados adotada pela plataforma.

Foi realizada a exploração dos pipelines existentes e da organização do repositório, com ênfase na estrutura de DAGs e no fluxo de ingestão de dados. Como resultado prático, foram desenvolvidas as primeiras DAGs, consolidando o entendimento sobre orquestração de workflows e integração entre componentes do sistema.

---

### Atividades Realizadas

| Data  | Atividade                                                            | Tipo   | Link/Referência                                                                                                 | Status    |
| ----- | -------------------------------------------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------- | --------- |
| 06/04 | Configuração do ambiente local (containers, dependências e serviços) | Código | [imagem](assets/dags.png)                                                                                       | Concluído |
| 08/04 | Estudo da documentação oficial e fluxo de contribuição               | Estudo | [Guia](https://gov-hub.io/govhub/comunidade/guia-contribuicao/)                                                 | Concluído |
| 12/04 | Análise da estrutura do repositório e pipelines de dados existentes  | Estudo | [fork de exploração](https://github.com/MilenaFRocha/data-application-cidades)                                  | Concluído |
| 13/04 | Criação de templates padronizados para issues (bug/feature)          | Código | [commit](https://github.com/GovHub-br/data-application-cidades/commit/61a36c70f40d2e3fd211749a9fb6cec04cc0b6cc) | Concluído |
| 15/04 | Desenvolvimento de DAGs para ingestão de dados (ETL inicial)         | Código | [branch](https://github.com/GovHub-br/data-application-cidades/commits/feature/ingestao-dados-habitacao/)       | Concluído |

---

### Maiores Avanços

* Compreensão da arquitetura do projeto, incluindo organização em camadas e separação entre ingestão, processamento e disponibilização de dados.
* Entendimento do funcionamento de pipelines orquestrados por DAGs, incluindo dependências entre tarefas e agendamento.
* Capacidade de configurar e executar o ambiente local com os serviços necessários (ex: banco de dados, orquestrador, containers).
* Implementação das primeiras DAGs de ingestão, aplicando conceitos básicos de ETL (extração, transformação e carga).
* Padronização inicial do processo de contribuição por meio da criação de templates para issues.

---

### Maiores Dificuldades

* Configuração do ambiente local, especialmente em relação a conflitos de portas, variáveis de ambiente e dependências entre serviços.
* Curva de aprendizado inicial na compreensão da estrutura das DAGs e do fluxo completo de execução dos pipelines.
* Entendimento das integrações entre os componentes do sistema (ex: fontes de dados, armazenamento e orquestração).

---

### Aprendizados

* Uso prático de GitHub em fluxo colaborativo: criação de branches, commits, issues e organização de contribuições.
* Estruturação de pipelines de dados utilizando DAGs, incluindo definição de tarefas, dependências e agendamento.
* Conceitos fundamentais de ETL aplicados ao contexto do projeto.
* Boas práticas iniciais de padronização e documentação em projetos de software livre.

---

### Plano Pessoal para a Próxima Sprint

* [ ] Submeter pelo menos 1 Pull Request com código revisado e validado.
* [ ] Participar ativamente de revisões de código (code review).
* [ ] Evoluir as DAGs desenvolvidas, incluindo tratamento de erros e validação de dados.
* [ ] Implementar testes básicos para garantir a confiabilidade dos pipelines.
* [ ] Aprofundar o entendimento sobre a arquitetura de dados do projeto (armazenamento e consumo).


---


## Sprint 1 – [21/04/2026 – 11/05/2026]

### Resumo da Sprint

Sprint dedicada a encontrar a primeira issue para contribuir. Fui designada para a issue [20](https://github.com/GovHub-br/data-application-cidades/issues/20) utilizei uma branch já criada para o desenvolvimento da mesma e consegui meu [PR aprovado](https://github.com/GovHub-br/data-application-cidades/pull/23).



### Atividades Realizadas

| Data  | Atividade                                       | Tipo (Código/Doc/Discussão/Outro) | Link/Referência                                                                                                                     | Status    |
|-------|-------------------------------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 14/05 | Designada para issue e estudo da mesma                          | Estudo                            | [Issue 20](https://github.com/GovHub-br/data-application-cidades/issues/20) | Concluído |
| 16/05 | Commit feito              | Desenvolvimento                            | [Commit](https://github.com/GovHub-br/data-application-cidades/commit/a062068db7f8e511c064afbe79e9dc303f887c5f)                                                                       | Concluído |
| 18/05 | PR Aprovado                                    | Configuração                      | [PR](https://github.com/GovHub-br/data-application-cidades/commit/a062068db7f8e511c064afbe79e9dc303f887c5f)                                                     | Concluído |


### Detalhamento das Atividades Realizadas

A issue basicamente era fazer DBTs das camadas bronze, silver e gold para plotagem de gráficos no Superset a partir das golds. Ao analisar os DBTs já desenvolidos percebi que não era necessário bronze e nem silver, apenas a gold pois as ouyras já estavam prontas. Estruturei os sql´s e testei. Populou certo o banco e pude assim fazer o [gráfico de execução financeira x execução física](assets/grafico_superset.png) .



### Maiores Avanços

* Ter contribuido .

### Maiores Dificuldades

* Entender todo o processo e objetivo da issue

### Aprendizados

* Aprendi como funciona DBT

### Plano Pessoal para a Próxima Sprint

* [ ] Procurar outras issue 
* [ ] Poder aprimorar meus conhecimentos técnicos e conhecer novas ferramentas

---



## Sprint 2 – [12/05/2026 – 26/05/2026]

### Resumo da Sprint

Sprint dedicada à contribuição no projeto Gov Hub BR. Implementei minha segunda feature junto com o [Lucas Martins](/contribuicoes_individuais/lucas_martins/lucas_martins.md): um helper para enviar notificações de falhas de tasks do Airflow via Telegram. A feature foi implementada, testada e teve um pull request aberto no repositório principal do projeto.

### Atividades Realizadas

| Data  | Atividade                                      | Tipo (Código/Doc/Discussão/Outro) | Link/Referência                                                                      | Status    |
|-------|------------------------------------------------|-----------------------------------|-------------------------------------------------------------------------------------|-----------|
| 23/05 | Análise da issue #293 de Telegram                | Análise                           | [Issue #293](https://github.com/GovHub-br/data-application-gov-hub/issues/293)       | Concluído |
| 24/05 | Implementação do helper de notificação via Telegram | Código                            | [telegram_helpers.py](https://github.com/martinsglucas/data-application-gov-hub/blob/feat/webhook-alerta-telegram/airflow_lappis/helpers/telegram_helpers.py)         | Concluído |
| 24/05 | Testes da feature e abertura de PR              | Código                            | [PR #321](https://github.com/GovHub-br/data-application-gov-hub/pull/321)            | Concluído |
| 02/0 | Documentação do diário de bordo                 | Documentação                      | -                                                                                    | Concluído |

### Detalhamento das Atividades Realizadas

Os seguintes prints documentam o processo de desenvolvimento da feature de notificações via Telegram:

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">1. Issue #293 - Observabilidade com Telegram</span></summary>

Issue de feature que propõe a implementação de um webhook do Airflow para notificar falhas de tasks via Telegram

![Issue #293 - Observabilidade com Telegram](../lucas_martins/assets/sprint-2/issue.png)
<p align="center"><i><b>Fonte:</b> Lucas Martins</i></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">2. Fork do Repositório</span></summary>

Fork do repositório data-application-gov-hub criado para realização das contribuições

![Fork do Repositório](../lucas_martins/assets/sprint-2/fork.png)
<p align="center"><i><b>Fonte:</b> Lucas Martins</i></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">3. Dashboard do Airflow</span></summary>

Dashboard do Airflow exibindo os logs de execução da DAG api_contratos_dag com as tasks relacionadas à feature implementada

![Dashboard do Airflow](../lucas_martins/assets/sprint-2/airflow.png)
<p align="center"><i><b>Fonte:</b> Lucas Martins</i></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">4. Implementação da Feature - telegram_helpers.py</span></summary>

Código da implementação do helper para envio de mensagens via Telegram, incluindo função de callback para notificar falhas de tasks

![Implementação - telegram_helpers.py](../lucas_martins/assets/sprint-2/code.png)
<p align="center"><i><b>Fonte:</b> Lucas Martins</i></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">5. Notificação de Falha via Telegram</span></summary>

Screenshot da notificação de falha recebida no Telegram, mostrando detalhes da DAG, task, data de execução, erro e logs

![Notificação de Falha via Telegram](../lucas_martins/assets/sprint-2/alerta.png)
<p align="center"><i><b>Fonte:</b> Lucas Martins</i></p>
</details>

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">6. Pull Request #321 - Webhook Alerta Telegram</span></summary>

Pull request com a implementação completa da feature de notificações de falhas do Airflow via Telegram

![Pull Request #321](assets/pr_issue_293.png)
<p align="center"><i><b>Fonte:</b> Milena Rocha</i></p>
</details>

### Maiores Avanços

* Segundo pull request aberto no projeto Gov Hub BR.
* Implementação bem-sucedida de feature de observabilidade com Telegram para o Airflow.
* Compreensão da arquitetura e fluxo de desenvolvimento do projeto Gov Hub BR.

### Maiores Dificuldades

* Sem maiores dificuldades significativas, mas o processo de configuração do ambiente local e entendimento da estrutura do projeto exigiu um esforço inicial considerável.

### Aprendizados

* Arquitetura do projeto Gov Hub BR e seu pipeline de dados.
* Integração de webhooks do Airflow para observabilidade e notificações.
* Uso de bibliotecas externas (httpx) para fazer requisições HTTP.
* Uso do bot do Telegram

### Plano Pessoal para a Próxima Sprint

- [ ] Revisar feedback do PR #321 e implementar melhorias sugeridas
- [ ] Trabalhar em novas features ou bug fixes relacionados ao projeto
- [ ] Aprofundar conhecimento em Airflow DAGs e tasks
- [ ] Colaborar com outros membros da equipe em code reviews


    


