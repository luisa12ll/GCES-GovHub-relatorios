# Diário de Bordo – João Lucas Araujo Siqueira

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint
A Sprint 0 teve como principal objetivo a ambientação no projeto Gov Hub BR, com foco no entendimento da arquitetura, estudo das documentações e configuração do ambiente de desenvolvimento local. Durante esse período, consegui compreender o fluxo de contribuição do projeto, além de realizar a configuração do ambiente. 

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 15/04 | Leitura e estudo da documentação do projeto | Estudo | [link - Documentação](https://gov-hub.io/govhub/sobre-projeto/overview/) | Concluído |
| 17/04 | Configuração inicial do ambiente | Código | [link - Guia de instalação](https://gov-hub.io/govhub/documentacao/instalacao/) | Concluído |
| 19/04 | Rastreamento de good first issues | Estudo | [link - GitHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Em andamento |

### Maiores Avanços
* Consegui configurar e rodar todo o ambiente local utilizando Docker, incluindo serviços como Apache Airflow, Apache Superset e Jupyter.
![Containers Docker](./assets/airflow.png)
![Containers Docker](./assets/docker.png)
![Containers Docker](./assets/postgres.png)

* Entendi o fluxo completo do projeto de dados: ingestão (Airflow) → transformação (dbt) → visualização (Superset).
![Containers Docker](./assets/superset.png)


* Entendi melhor a organização do repositório, incluindo DAGs do Airflow, estrutura do dbt e configurações via .env.

### Maiores Dificuldades
* Problemas iniciais com dependências do ambiente (ex: conflito entre versões do Poetry e plugins).
* Entendimento inicial do fluxo entre múltiplas ferramentas (Airflow, dbt, Superset), que não é trivial.


### Aprendizados
* Como configurar conexões dentro do Airflow e do Superset.
* Boas práticas iniciais de padronização e documentação em projetos de software livre.
* Entendimento na prática do fluxo de contribuição e arquitetura do projeto.


### Plano Pessoal para a Próxima Sprint
* [X] Contribuir com pelo menos 1 PR.
* [ ] Participar da revisão de código de um colega.

---

## Sprint 1 – [21/04/2026 – 04/05/2026]

### Resumo da Sprint
Atuei no desenvolvimento do fluxo de dados do IBGE focado no Censo Demográfico de Quilombolas e Indígenas. O principal objetivo foi criar uma solução de coleta via FTP e organização de dados capaz de lidar com a extrema falta de padrão nas planilhas do governo. Garanti que o pipeline funcione de forma estável, não duplique informações caso precise ser reexecutado (idempotência) e documente as tabelas no banco de dados. Ao final da sprint, concluí a implementação e abri o Pull Request correspondente para revisão da equipe

### Atividades Realizadas

| Data  | Atividade | Tipo | Link/Referência | Status |
| ----- | --------- | ---- | --------------- | ------ |
| 21/04 - 01/05 | Mapeamento inicial do projeto e busca por tarefas acessíveis (*good first issues*) | Estudo | [Issues - GovHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Concluído |
| 01/05 | Desenvolvimento do fluxo de dados do Censo 2022 referentes a Quilombolas e Indígenas por sexo e idade. (Issue #119) | Código | [Issue #119](https://github.com/GovHub-br/data-application-gov-hub/issues/119) | Concluído |
| 10/05 | Revisão do código | Estudo/Código | - | Concluído |
| 11/05 | Abertura do Pull Request para a Issue #119 e espera da avaliação da equipe| Código/Doc | [Link - PR](https://github.com/GovHub-br/data-application-gov-hub/pull/270) | Em Andamento|



### Implementação da Issue #122

O foco desta entrega foi criar um caminho totalmente automatizado para extrair, limpar e disponibilizar os dados do pacote "Quilombolas e Indígenas por sexo e idade" do Censo Demográfico 2022. 

As principais atividades foram:

* **Coleta automatizada:** Conectei o sistema diretamente aos servidores FTP do IBGE utilizando o ClienteIBGE para ler e baixar os arquivos de forma dinâmica, varrendo subpastas específicas. Optei por processar esses arquivos em memória, tornando o fluxo muito mais rápido e evitando sobrecarregar o armazenamento local.
* **Limpeza e organização dos dados:** Desenvolvi código para processar planilhas altamente despadronizadas. O sistema ignora abas desnecessárias (como gráficos e notas) e possui um parser flexível capaz de distinguir Apêndices (focados em texto) de Tabelas (focadas em números). Além disso, apliquei a técnica de flattening (despivotamento) para achatar e normalizar cabeçalhos hierárquicos e mesclados.
* **Armazenamento seguro:** Garanti que os dados fossem salvos no schema censo_demografico de forma confiável. Implementei uma trava de idempotência (via DROP TABLE IF EXISTS) que limpa os registros anteriores antes de uma nova inserção, impedindo qualquer duplicação caso a DAG do Airflow precise ser reexecutada.


### Maiores Avanços
* Criação de uma solução robusta para o flattening de cabeçalhos mesclados do IBGE, juntando os "pedaços" de títulos hierárquicos e padronizando-os em colunas limpas e rastreáveis.
* Garantia de confiabilidade da ingestão de dados ao criar um mecanismo de prevenção contra dados duplicados.
* Criação e submissão do Pull Request da Issue #119. 

### Maiores Dificuldades
* Lidar com os dados abertos do governo. Muitas planilhas utilizam células mescladas e espaços em branco apenas por motivos estéticos, o que dificulta bastante a leitura automatizada.
* As tabelas `.xlsx` possuem várias abas, fazendo necessária uma análise crítica para decidir o que precisaria ser lido para trazer os dados corretos.  
* Enfrentar os bloqueios de Pre-commit e Pre-push acusando erros em arquivos legados de outros desenvolvedores da equipe;
* Erro ao dar push na branch, sendo necessário fazer um fork do projeto.
* Adequação do código para garantir qualidade ao bot do sonarqube sem perder a robustez do processamento

### Aprendizados
* Compreensão aprofundada do projeto do GovHub.
* Aprofundei meu conhecimento em limpeza e transformação de dados com pandas, especialmente no tratamento de planilhas com estruturas irregulares.
* Boas práticas de Clean Code e modularização de código para CI/CD e ferramentas de análise estática de código (SonarQube)
* Fluxo Git avançado para contribuição em organizações de software livre, incluindo o uso de Forks, reestruturação de commits e a flag --no-verify para lidar com dívida técnica de terceiros.

### Plano Pessoal para a Próxima Sprint
- [ ] Ter o feedbakc sobre o PR e corrigir quaisquer erros identificados
- [ ] Ter o PR aprovado
- [ ] Encontrar novas issues mais complexas para contribuir

## Sprint 2 – [05/05/2026 – 25/05/2026]
 
### Resumo da Sprint
Nesta sprint, trabalhei  na Issue #317 do GovHub BR. Meu foco foi implementar testes unitários para o arquivo pedido na issue. 
Demorei a abrir o Pull Request por conta de outras demandas pessoais mas agora está aberto e aguardando revisão. O PR que mandei na sprint anterior ainde está em análise dos mantenedores, então não tive oportunidade de participar de uma correção do PR anterior

### Atividades Realizadas
 
| Data | Atividade | Tipo | Link/Referência | Status |
| ---- | --------- | ---- | --------------- | ------ |
| 05/05 - 12/05 | Busca de novas issues para contribuir | Estudo | [Issues - GovHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Concluído |
| 13/05 - 17/05 | Desenvolvimento de estes unitarios para airflow_lappis/plugins/cliente_senadores.py. (Issue #317) | Doc | [Issue #317](https://github.com/GovHub-br/data-application-gov-hub/issues/317) | Concluído |
|01/06 | Revisão e abertura do Pull Request #333 | Doc | [Link - PR #333](https://github.com/GovHub-br/data-application-gov-hub/pull/333) | Concluído |


 
### Maiores Avanços
* Criação dos teste unitários solicitados 

### Maiores Dificuldades
* EScrever testes úteis para o problema. 
* Verificações de pré commits e pré push que pegavam arquivos que eu não alterei 

### Aprendizados
* Aprendi mais sobre o projeto e sobre testes unitários.

### Plano Pessoal para a Próxima Sprint
- [ ] Ter o novo PR aprovado por todos os revisores.
- [ ] Buscar novas issues para contribuir.
- [ ] Ter o PR anterior revisado.


## Sprint 3 – [18/05/2026 – 01/06/2026]
 
### Resumo da Sprint
Nessa Sprint não tive grandes avanços na contribuição do projeto do GovHub, além de ainda não ter os PRs mandados nas sprints anteriores revisados ou aprovados, logo foquei em começar a estudar o projeto individual.
### Atividades Realizadas
 
| Data | Atividade | Tipo | Link/Referência | Status |
| 01/06 | Leitura do enunciado da atividade extra     | Doc    | [Projeto Individual ](https://gitlab.com/unb-esw/gces/gces2026-1/projetoindividual) | Concluído |


 
### Maiores Avanços
-
### Maiores Dificuldades
* Ficar sem revisão dos PRs

### Aprendizados
-
### Plano Pessoal para a Próxima Sprint
- [ ] Ter os PRs aprovado por todos os revisores.


## Sprint 4 – [02/06/2026 – 15/06/2026]

### Resumo da Sprint
Nessa sprint, foquei totalmente na entrega do projeto individual da disciplina (o jogo mk.js). 

### Atividades Realizadas

| Data | Atividade | Tipo | Link/Referência | Status |
| ---- | --------- | ---- | --------------- | ------ |
| 02/06 - 04/06 | Atualização de dependências antigas do Node, criação do Dockerfile de desenvolvimento com hot-reload e persistência com Postgres (Fases 1 e 2) | Código / Docker | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-joao-siqueira) | Concluído |
| 04/06 - 06/06 | Configuração do ESLint global, criação do pipeline de Build & Lint, testes unitários com Jest no ciclo de falha/correção e testes de Fuzzing (Fases 3, 4 e 5) | Código / CI/CD | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-joao-siqueira) | Concluído |
| 06/06 - 08/06 | Integração de ferramentas de segurança  e análise de qualidade usando o SonarCloud no GitLab CI (Fases 6 e 7) | CI/CD / Segurança | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-joao-siqueira) | Concluído |
| 08/06 - 09/06 | Configuração do Docker de produção usando Nginx para servir o frontend e fazer proxy reverso para o Node.js (Fase 8) | Docker | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-joao-siqueira) | Concluído |
| 09/06 - 10/06 | Criação dos manifestos do Kubernetes, deploy automático e segurança de rede com HTTPS e Ingress (Fases 9 e 10) | Infra / IaC / CD | [Repositório GitLab](https://gitlab.com/unb-esw/gces/gces2026-1/trabalho-final-gces-joao-siqueira) | Concluído |

### Maiores Avanços

* A base do projeto individual foi estabelecida, priorizando a criação de containers, pipelines de integração e entrega contínuas (CI/CD) e a garantia da qualidade do software.
* Montei um pipeline de CI/CD bem completo no GitLab, rodando desde linter e testes até análises de segurança e envio automático da imagem de produção para o registry.
* O versionamento e o registro das entregas no repositório do GitLab foram mantidos de forma constante durante a criação e validação da esteira DevOps.
* Houve progresso significativo na implementação das funcionalidades do sistema e na elaboração da documentação técnica.
* Corrigi bugs e lints antigos que estavam quebrando o linter do frontend, além de modernizar o acesso à câmera no código do jogo.

### Maiores Dificuldades
* A migração do projeto para uma arquitetura mais moderna, com a separação entre front-end e back-end, exigiu ajustes estruturais, refatorações nas configurações e adequação das dependências.
* Foi necessário solucionar incompatibilidades causadas por dependências desatualizadas e corrigir problemas do ESLint que inicialmente não eram evidentes.
* A implantação da aplicação em containers e sua integração com o GitLab CI apresentaram desafios relacionados à configuração dos ambientes e à execução dos testes automatizados.
* A configuração do Nginx precisou ser adaptada para suportar conexões WebSocket utilizadas pelo socket.io, garantindo a comunicação adequada da aplicação.
* A configuração do Ingress no Kubernetes para utilização de HTTPS em ambiente local, com o cert-manager e um certificado autoassinado, exigiu ajustes adicionais para seu correto funcionamento.



### Aprendizados
* Aprendi a estruturar um pipeline completo no GitLab CI com gerenciamento de dependências e artefatos de cobertura de código.

### Plano Pessoal para a Próxima Sprint
- [x] Voltar a contribuir no GovHub

