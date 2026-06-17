# Diário de Bordo – Letícia de Cássia Hladczuk Rodrigues

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint
Essa sprint foi focada na familiarização com o projeto, o aprendizado do fluxo de contribuições e a configuração do ambiente.

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 15/04 | Leitura e estudo da documentação do projeto | Estudo | [link - Documentação](https://gov-hub.io/govhub/sobre-projeto/overview/) | Concluído |
| 17/04 | Configuração inicial do ambiente | Código | [link - Guia de instalação](https://gov-hub.io/govhub/documentacao/instalacao/) | Concluído |
| 17/04 | Rastreamento de good first issues | Estudo | [link - GitHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Em andamento |

### Maiores Avanços
* Consegui rodar a aplicação localmente. Containers Dockers rodando:

![Containers Docker](./assets/sprint0/containersDocker.png)

* Entendi melhor a organização do repositório.

* Configuração do Airflow e Superset.
![Superset](./assets/sprint0/superset.png)
![Superset](./assets/sprint0/airflow.png)


### Maiores Dificuldades
* Logo no início, tive problema com a versão do Python, precisando fazer o ajuste para a versão 3.11. 
![Erro Versão do Python](./assets/sprint0/erro_pyVersion.png)

* Tive dificuldades de configurar o WSL, pois foi a minha primeira vez usando.

* Erros de sintaxe nas variáveis de ambiente do Airflow.

### Aprendizados
* Entendimento na prática do fluxo de contribuição e arquitetura do projeto.
* Melhoria na leitura de logs para diagnosticar falhas de dependência entre serviços.


### Plano Pessoal para a Próxima Sprint
* [X] Buscar good first issues para começar a contribuir.
* [ ] Contribuir com pelo menos 1 PR.
* [X] Participar da revisão de código de um colega.

---

## Sprint 1 – [21/04/2026 – 04/05/2026]

### Resumo da Sprint
Trabalhei em parceria com o [Rafael Matuda](https://github.com/rmatuda) para desenvolver o fluxo de dados do IBGE focado no Censo Demográfico das Mulheres. Nosso principal objetivo foi criar uma solução de coleta e organização de dados capaz de lidar com a falta de padrão nas planilhas do governo. Garantimos que o sistema funcione de forma estável, não duplique informações caso precise ser reiniciado e esteja pronto para crescer no futuro. Ao final da sprint, concluímos a implementação e abrimos o Pull Request correspondente para revisão da equipe.

### Atividades Realizadas

| Data  | Atividade | Tipo | Link/Referência | Status |
| ----- | --------- | ---- | --------------- | ------ |
| 21/04 - 23/04 | Mapeamento inicial do projeto e busca por tarefas acessíveis (*good first issues*) | Estudo | [Issues - GovHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Concluído |
| 24/04 - 27/04 | Desenvolvimento do fluxo de dados do Censo das Mulheres (Issue #122) | Código | [Issue #122](https://github.com/GovHub-br/data-application-gov-hub/issues/122) | Concluído |
| 28/04 | Revisão do código | Estudo/Código | - | Concluído |
| 29/04 | Abertura do Pull Request para a Issue #122 | Código/Doc | [Link - PR](https://github.com/GovHub-br/data-application-gov-hub/pull/241) | Concluído |
| 01/05 | Recebimento da revisão dos mantenedores do projeto | Código | [Link - PR](https://github.com/GovHub-br/data-application-gov-hub/pull/241) | Concluído |
| 01/05 - 04/05 | Desenvolvimento das alterações solicitadas | Código | [Link - PR](https://github.com/GovHub-br/data-application-gov-hub/pull/241) | Concluído |
| 06/05 | Revisão e submissão das alterações | Código | [Link - PR](https://github.com/GovHub-br/data-application-gov-hub/pull/241) | Concluído |

### Implementação da Issue #122

O foco desta entrega foi criar um caminho totalmente automatizado para extrair, limpar e disponibilizar os dados do pacote "Mulheres" do Censo Demográfico 2022. 

As principais atividades foram:

* **Coleta automatizada:** Conectamos nosso sistema diretamente aos servidores do IBGE para ler e baixar os arquivos de forma dinâmica. Optamos por processar esses arquivos na memória, tornando o fluxo mais rápido e evitando sobrecarregar o armazenamento local.
* **Limpeza e organização dos dados:** Desenvolvemos regras inteligentes para ler as planilhas. O sistema agora ignora abas desnecessárias (como gráficos) e identifica automaticamente onde começam os dados reais. Além disso, padronizamos os nomes das colunas.
* **Armazenamento seguro:** Garantimos que os dados fossem salvos no banco de forma segura. Implementamos uma trava de segurança que limpa os registros anteriores antes de uma nova inserção, impedindo a duplicação de dados caso o processo precise rodar mais de uma vez. Também adicionamos colunas para rastrear de onde e quando cada dado veio. Após a revisão do PR, ajustamos a abordagem para utilizar a função `drop_duplicates()` em vez de remover diretamente os registros do banco."
* **Integração e documentação:** Conectamos esse novo fluxo com as ferramentas já utilizadas pelo projeto (dbt) e deixamos as tabelas e colunas devidamente documentadas no banco de dados para facilitar a vida dos próximos desenvolvedores ou analistas que forem utilizar essa base.

### Maiores Avanços
* Criamos uma solução para "fatiar" tabelas do governo que vinham agrupadas horizontalmente, utilizando as colunas em branco das próprias planilhas como guias de corte.
* Garantimos a confiabilidade da ingestão de dados ao criar um mecanismo de prevenção contra dados duplicados.
* Criação e submissão do Pull Request da Issue #122. 
* Conseguimos atender aos pontos levantados na revisão do PR.

### Maiores Dificuldades
* Lidar com os dados abertos do governo. Muitas planilhas utilizam células mescladas e espaços em branco apenas por motivos estéticos, o que dificulta bastante a leitura automatizada.
* As tabelas `.xlsx` possuem várias abas, fazendo necessária uma análise crítica para decidir o que precisaria ser lido para trazer os dados corretos. As abas preferencialmente lidas foram as últimas, onde tinham dados do SIDRA, trazendo de 1 a 3 tabelas por aba. Nesse processo, o complicado foi conseguir lidar com as diferentes estruturas que existiam de uma tabela para outra e/ou de um arquivo para outro.
* Foi necessário criar regras de exceção para algumas tabelas específicas, para que o nome das colunas viesse como solicitado na revisão do PR.
* Conectar no ambiente dbt local.
* Erro ao dar push na branch, sendo necessário fazer um fork do projeto.

### Aprendizados
* Compreensão aprofundada do projeto do GovHub.
* Aprofundei meu conhecimento em limpeza e transformação de dados com pandas, especialmente no tratamento de planilhas com estruturas irregulares.
* Adquiri conhecimento sobre o dbt.

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">Comprobatórios da Issue #122</span></summary>
<h3>Dag para extração das tabelas - <i>mulheres_censo_demografico_dag</i></h3>

![Dag mulheres_censo_demografico_dag](assets/sprint1/dag_ibge.png)

<h3>Tabelas extraídas no banco de dados PostgreSQL</h3>

![Tabelas extraídas no banco de dados postgres](assets/sprint1/tabelas_ibge.png)

<h3>Tabelas na camada Bronze do DBT</h3>

![Tabelas na camada Bronze do DBT](assets/sprint1/dbt_bronze_122.png)

</details>

### Plano Pessoal para a Próxima Sprint
- [X] Ter o PR aprovado
- [X] Encontrar novas issues para contribuir

---

## Sprint 2 – [05/05/2026 – 17/05/2026]
 
### Resumo da Sprint
Nesta sprint, trabalhei em parceria com o [Rafael Matuda](https://github.com/rmatuda) na Issue #276 do GovHub BR. Nosso foco foi estruturar o guia de contribuição (`CONTRIBUTING.md`) e preparar o PR para revisão.

### Atividades Realizadas
 
| Data | Atividade | Tipo | Link/Referência | Status |
| ---- | --------- | ---- | --------------- | ------ |
| 05/05 - 12/05 | Busca de novas issues para contribuir | Estudo | [Issues - GovHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Concluído |
| 13/05 - 17/05 | Desenvolvimento do `CONTRIBUTING.md` (Issue #276) | Doc | [Issue #276](https://github.com/GovHub-br/data-application-gov-hub/issues/276) | Concluído |

### Maiores Avanços
* Redação completa do `CONTRIBUTING.md`, suprindo uma lacuna importante de documentação no projeto.
* Preparação do PR para revisão dos mantenedores.

### Maiores Dificuldades
* Compreender todas as ferramentas e convenções reais do projeto para não documentar informações desatualizadas.
* Adequar a documentação à estrutura real do repositório exigiu maior imersão.

### Aprendizados
* Aprendi a importância de documentação viva e alinhada à realidade do projeto.
* Experiência prática no ciclo de revisão em projetos open source.
* Aprofundei a compreensão sobre boas práticas de contribuição colaborativa.

### Plano Pessoal para a Próxima Sprint
- [X] Abrir o Pull Request e acompanhar a revisão.
- [X] Buscar novas issues para contribuir.

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">Comprobatórios da Sprint</span></summary>
<h3>Pull Request #281</h3>

![Pull Request #281](assets/sprint2/pullRequest281.png)
</details>

---

## Sprint 3 – [18/05/2026 – 01/06/2026]

### Resumo da Sprint
Nesta sprint, eu e o [Rafael Matuda](https://github.com/rmatuda) finalizamos o PR da documentação de contribuição e acompanhamos sua evolução até o final do período. Enquanto o PR aguardava aprovação, continuei buscando novas issues do GovHub BR para contribuir com o projeto.

Abrimos 2 PRs, o primeiro foi mergeado por engano sem a revisão correta, tivemos que abrir outro para enviar as correções solicitadas. A aprovação e merge do segundo PR ocorreram posteriormente, no dia 27/06.

### Atividades Realizadas

| Data | Atividade | Tipo | Link/Referência | Status |
| ---- | --------- | ---- | --------------- | ------ |
| 18/05 | Finalização do PR do `CONTRIBUTING.md` | Doc | [Link - PR #281](https://github.com/GovHub-br/data-application-gov-hub/pull/281) | Concluído |
| 19/05 | Acompanhamento do PR e análise de comentários | Doc | [Link - PR #281](https://github.com/GovHub-br/data-application-gov-hub/pull/281) | Concluído |
| 27/05 | Abertura de novo PR corrigindo as alterações solicitadas | Doc | [Link - PR #330](https://github.com/GovHub-br/data-application-gov-hub/pull/330) | Concluída|
| 28/05 - 01/06 | Busca de novas issues para contribuir | Estudo | [Issues - GovHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Concluído |

### Maiores Avanços
* Enviei o PR de documentação de contribuição do projeto.
* Mantive o acompanhamento do processo de revisão até o fim da sprint.

### Maiores Dificuldades
* Achamos que o arquivo `CONTRIBUTING.md` tinha sido mergeado, pois os PRs tinham sido fechados. Isso atrasou um pouco a correção do arquivo.

### Aprendizados
* Entendi melhor o fluxo de contribuição após a revisão feita.

### Plano Pessoal para a Próxima Sprint
- [X] Acompanhar o resultado final do PR e validar o merge.
- [X] Avançar para o trabalho individual da disciplina.

<details>
<summary><span style="font-size: 1.25em; font-weight: bold; cursor: pointer;">Comprobatórios da Sprint</span></summary>
<h3>Pull Request #330</h3>

![Pull Request #330](assets/sprint3/pullRequest330.png)
</details>
---

## Sprint 4 – [02/06/2026 – 15/06/2026]

### Resumo da Sprint
Nessa sprint, foquei exclusivamente no projeto individual da disciplina.

### Atividades Realizadas

| Data | Atividade | Tipo | Link/Referência | Status |
| ---- | --------- | ---- | --------------- | ------ |
| 02/06 | Estudo sobre os requisitos do trabalho final | Código/Doc/Estudo | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-leticia-rodrigues/) | Concluído |
| 02/06 - 09/06 | Desenvolvimento das funcionalidades do projeto individual | Código | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-leticia-rodrigues/) | Concluído |
| 09/06 | Ajustes finais, testes e documentação do trabalho individual | Código/Doc | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-leticia-rodrigues/) | Concluído |

### Maiores Avanços
* Estruturei o projeto individual com foco nas fases de containerização, CI/CD e qualidade de código.
* Avancei no desenvolvimento das funcionalidades do projeto e em sua documentação.
* Mantive registro contínuo das entregas no repositório GitLab enquanto desenvolvia e testava o fluxo de DevOps.
* Entrega do trabalho individual.

### Maiores Dificuldades
* Adaptar o projeto para uma arquitetura mais moderna de backend/front-end exigiu ajustes em dependências e configuração.
* Validar o funcionamento em containers e garantir integração com GitLab CI trouxe desafios de ambiente e teste.

### Aprendizados
* Entendi melhor como estruturar um pipeline de GitLab CI.
* Aplicação prática de estruturar um projeto end-to-end por mais que já tivesse um código legado.

### Plano Pessoal para a Próxima Sprint
- [] Voltar a contribuir no GovHub
