# Diário de Bordo – João Guilherme Fonseca

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint
Breve descrição das atividades e reflexões.

### Atividades Realizadas
| Data  | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
| ----- | --------- | --------------------------------- | --------------- | ------ |
| 20/08 | Configuração inicial do ambiente | Código | – | Concluído |
| 22/08 | Leitura e estudo da documentação do projeto | Estudo | [link wiki] | Concluído |
| 24/08 | Abertura de issue para bug em módulo X | Discussão | [link issue] | Concluído |

### Maiores Avanços
* Aprendi a rodar a aplicação localmente.
* Entendi melhor a organização do repositório.

### Maiores Dificuldades
* Ambiente demorou para configurar por falta de dependências.
* Imcompatibilidade das versões do Python
* Erro no Docker ao tentar dar build pela primeira vez.

### Aprendizados
* Fluxo de contribuição do projeto.

### Plano Pessoal para a Próxima Sprint
* [ ] Contribuir com pelo menos 1 PR.
* [ ] Participar da revisão de código de um colega.

### Comprobátorios

* Build do ambiente no Docker
![Docker](assets/docker.jpg)

* Airflow
![Airflow](assets/Airflow.jpg)

* Jupyter
![Jupyter](assets/jupyter.jpg)

* Superset
![Superset](assets/superset.jpg)


## Sprint 1 – [21/04/2026 – 04/05/2026]

### Resumo da Sprint

Durante a Sprint 1, o foco principal foi realizar uma imersão no projeto, com ênfase em estudar a documentação do projeto, configurar o ambiente de desenvolvimento local e compreender o fluxo e arquitetura geral da aplicação. Embora não tenha resultado em contribuições via Pull Requests, essa etapa foi fundamental para construir uma base sólida de conhecimento sobre o projeto.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
|------|-----------|-----------------------------------|-----------------|--------|
| 20/08 | Configuração inicial do ambiente de desenvolvimento | Código | - | Concluído |
| 22/08 | Leitura e estudo da documentação do projeto data-application-gov-hub | Estudo | [Wiki do Projeto] | Concluído |
| 24/08 | Análise do fluxo e arquitetura do projeto | Documentação | [README.md] | Concluído |
| 26/08 | Exploração da estrutura de diretórios e componentes principais | Estudo | - | Concluído |

### Maiores Avanços

- **Ambiente configurado com sucesso**: Consegui configurar localmente todas as dependências necessárias para executar o projeto data-application-gov-hub, incluindo Docker, serviços auxiliares e variáveis de ambiente.

- **Entendimento do projeto**: Adquiri conhecimento sobre a arquitetura do projeto, seus principais módulos (airflow, superset, aplicações Python), fluxo de dados e tecnologias utilizadas.

- **Familiarização com o repositório**: Compreendi a estrutura do repositório, convenções de código e fluxo de trabalho esperado para futuras contribuições.

### Maiores Dificuldades

- **Falta de issues "good first issue"**: A principal dificuldade encontrada foi a ausência de issues abertas rotuladas como "good first issue" ou com nível de dificuldade adequado para que podesse contribuir, o que impossibilitou a realização de contribuições práticas com Pull Requests durante a sprint.

### Aprendizados

- Melhor compreensão do fluxo de trabalho em projetos open source e uso de GitHub Issues.
- Conhecimento aprofundado sobre a estrutura do projeto data-application-gov-hub, seus componentes e dependências.
- Experiência com ferramentas de containerização e orquestração de ambientes.

### Plano Pessoal para a Próxima Sprint

- ☐ Contribuir com pelo menos 1 Pull Request.
- ☐ Participar de discussões e revisões de código de colegas.
- ☐ Aprofundar conhecimento em módulos específicos do projeto (Airflow ou Superset).

## Sprint 2 – [05/05/2026 - 25/05/2026]

### Resumo da Sprint
Nesta sprint, o foco principal foi garantir a confiabilidade do módulo de ingestão de dados da Câmara dos Deputados. A meta foi alcançada com o desenvolvimento completo da suíte de testes unitários para a classe `ClienteDeputados`, atingindo 100% de cobertura (line e behavioral coverage). O processo envolveu a criação de mocks de paginação complexos e a validação rigorosa do tratamento de exceções e logs gerados pela aplicação.

### Atividades Realizadas

| Data | Atividade | Tipo | Link/Referência | Status |
| :--- | :--- | :--- | :--- | :--- |
| 05/05 | Busca de novas Issues para contribuir | Estudo | [Issues - GovHub](https://github.com/GovHub-br/data-application-gov-hub/issues) | Concluído |
| 22/05 | Desenvolvimento do `test_cliente_deputados.py` (Issue #310) | Código | Doc | [Link Issue](https://github.com/GovHub-br/data-application-gov-hub/issues/310) | Concluído |
| 03/06 | Abertura do PR (Issue #310) | Código | Doc | [Link PR](https://github.com/GovHub-br/data-application-gov-hub/pull/338) | Concluído |

### Maiores Avanços
* Implementação bem-sucedida da validação de logs (warnings e errors) em cenários de falha da API usando o context manager `assertLogs`.
* Criação de testes robustos para paginação que diferenciam corretamente uma "lista vazia" (fim de dados) de um retorno None (falha na API).
### Maiores Dificuldades
* Isolar a lógica do loop infinito (while True) nos métodos `get_all_deputados` e `get_deputados_atuais` para testar os cenários de quebra sem causar loops infinitos reais.
* Garantir a simulação correta dos variados retornos malformados (HTML de erro, timeout, JSON sem chaves esperadas) sem acionar chamadas de rede externas.

### Aprendizados
* Aprofundamento no uso da biblioteca `unittest.mock`, especificamente o uso de `side_effect` para iterar sobre retornos diferentes em chamadas sequenciais (essencial para simular paginação).
* Importância de testar a emissão de logs da aplicação, garantindo que o sistema seja facilmente monitorável em produção caso a API governamental caia.

### Plano Pessoal para a Próxima Sprint
- [ ] Ter o novo PR aprovado por todos os revisores.
- [ ] Buscar novas issues para contribuir.
