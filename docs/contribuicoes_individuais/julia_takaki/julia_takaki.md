# Diário de Bordo – Júlia Takaki Neves

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)  
**Equipe:** Gov Hub BR  
**Projeto:** Gov Hub BR  

---

## Sprint 0 – [06/04/2026 – 20/04/2026]

### Resumo da Sprint

A Sprint 0 teve como objetivo principal a adaptação ao projeto, com foco na compreensão da arquitetura, preparação do ambiente e alinhamento com as práticas da comunidade. Ao final do período, já foi possível executar o sistema localmente e entender o fluxo geral de funcionamento.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
|--------|----------|-----------------------------------|-----------------|--------|
| 09/04 | Criação e preparação do repositório de trabalho (fork + organização inicial) | Código | [Repositório](https://github.com/luisa12ll/gov-hub.git) | Concluído |
| 11/04 | Estudo das diretrizes do projeto e entendimento do fluxo de contribuição | Estudo | [Guia](https://gov-hub.io/govhub/comunidade/guia-contribuicao/) | Concluído |
| 14/04 | Análise da arquitetura e funcionamento da plataforma | Estudo | [E-book](https://gov-hub.io/govhub/ebook-viewer/) | Concluído |
| 15–18/04 | Configuração do ambiente e validação da execução local do sistema | Código | [Instalação](https://gov-hub.io/govhub/documentacao/instalacao/) | Concluído |
| 15–19/04 | Estruturação e organização da documentação da equipe | Documentação | [Pages](https://luisa12ll.github.io/GCES-GovHub-relatorios/#/) | Concluído |

### Maiores Avanços

* Passei a entender o projeto como um pipeline de dados completo, e não apenas como uma aplicação isolada;
* Consegui executar todos os serviços necessários localmente, validando o fluxo de ponta a ponta;
* Estruturei um ambiente de documentação reutilizável para a equipe;
* Ganhei clareza sobre como contribuir sem quebrar padrões do projeto.

### Maiores Dificuldades

* O processo de setup foi mais complexo do que o esperado devido à quantidade de serviços integrados;
* Houve inconsistências na configuração inicial que exigiram ajustes iterativos;
* No início, a arquitetura do sistema não era intuitiva, exigindo leitura aprofundada para compreensão.

### Aprendizados

* Projetos open source exigem forte aderência a padrões já estabelecidos;
* A configuração de ambiente é parte crítica da produtividade em projetos reais;
* Ferramentas como Airflow, DBT e Superset fazem parte de um ecossistema integrado;
* Documentação bem estruturada reduz atrito dentro da equipe.

### Plano Pessoal para a Próxima Sprint

* [ ] Identificar tarefas de baixa complexidade para primeira contribuição prática;
* [ ] Aprofundar o entendimento sobre os dados manipulados pelo sistema;
* [ ] Participar mais ativamente das discussões técnicas da equipe;
* [ ] Evoluir de execução local para contribuição efetiva no código;
* [ ] Garantir consistência entre documentação e desenvolvimento.

---

## Sprint 1 – [21/04/2026 – 04/05/2026]

### Resumo da Sprint

Durante esta sprint, o foco foi validar o processo de configuração e execução do projeto a partir da perspectiva de um novo contribuidor. Para isso, foi realizada uma tentativa de instalação seguindo exclusivamente as instruções disponibilizadas na documentação oficial do repositório, especialmente o README.

Ao longo desse processo, foram identificadas dificuldades que impediam a execução completa do projeto apenas com as informações disponíveis. As inconsistências observadas foram mais evidentes em ambiente Windows, embora também tenham sido encontradas limitações na documentação para Linux. Como resultado, foi aberta a Issue #103 relatando os problemas encontrados e sugerindo melhorias na documentação.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
|--------|----------|-----------------------------------|-----------------|--------|
| 04/05 | Validação da documentação de instalação e abertura de issue reportando problemas encontrados | Documentação/Discussão | [Issue](https://github.com/GovHub-br/gov-hub/issues/103) | Concluído |

### Maiores Avanços

* Identificação de pontos de melhoria na documentação do projeto;
* Registro formal de dificuldades encontradas durante a instalação;
* Contribuição para o aprimoramento da experiência de novos contribuidores.

### Maiores Dificuldades

* Executar o projeto utilizando apenas as instruções disponíveis na documentação;
* Resolver problemas específicos relacionados ao ambiente Windows;
* Determinar quais problemas eram causados pela configuração local e quais estavam relacionados à documentação.

### Aprendizados

* Importância de documentações claras e reproduzíveis em projetos open source;
* Necessidade de validar instruções em diferentes sistemas operacionais;
* Valor do feedback de usuários e contribuidores para a evolução de projetos colaborativos.

### Plano Pessoal para a Próxima Sprint

* [ ] Acompanhar a análise da Issue #103 pelos mantenedores;
* [ ] Validar possíveis melhorias realizadas na documentação;
* [ ] Continuar contribuindo com sugestões relacionadas à experiência de onboarding e documentação do projeto.

---

## Sprint 2 – [05/05/2026 – 24/05/2026]

### Resumo da Sprint

Durante esta sprint, participei da elaboração do Código de Conduta do projeto Gov Hub BR em conjunto com outro integrante da equipe. A atividade teve como objetivo definir diretrizes de comportamento e convivência para a comunidade, contribuindo para a organização e governança do projeto.

Para a realização da atividade, foram pesquisados modelos amplamente utilizados em projetos open source, que serviram como base para a adaptação do documento ao contexto do Gov Hub BR.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
|------|------------|-----------------------------------|-----------------|---------|
| 22/05 | Estudo de códigos de conduta utilizados em comunidades open source | Estudo | Contributor Covenant e referências da comunidade open source | Concluído |
| 24/05 | Elaboração do arquivo `CODE_OF_CONDUCT.md` para o projeto Gov Hub BR | Documentação | [Issue #277](https://github.com/GovHub-br/data-application-gov-hub/issues/277) [Pull Request](https://github.com/GovHub-br/data-application-gov-hub/pull/322) | Concluído |

### Maiores Avanços

* Criação do Código de Conduta do projeto;
* Aplicação de boas práticas de governança utilizadas em comunidades open source;
* Contribuição para um ambiente mais organizado e acolhedor para novos contribuidores.

### Maiores Dificuldades

* Adaptar modelos existentes ao contexto específico do projeto;
* Definir uma linguagem clara e alinhada com a documentação já existente;
* Identificar quais diretrizes seriam mais relevantes para a comunidade.

### Aprendizados

* Importância dos códigos de conduta em projetos colaborativos;
* Boas práticas de governança em comunidades de software livre;
* Processo de construção de documentação voltada para a comunidade.

### Plano Pessoal para a Próxima Sprint

* [ ] Acompanhar a revisão da [Issue #277](https://github.com/GovHub-br/data-application-gov-hub/issues/277);
* [ ] Realizar novas contribuições para o projeto;
* [ ] Participar de discussões e revisões de documentação.

## Sprint 3 – [25/05/2026 – 08/06/2026]

### Resumo da Sprint

Durante esta sprint, o foco principal foi acompanhar a evolução da contribuição realizada na sprint anterior, relacionada à criação do arquivo `CODE_OF_CONDUCT.md` para o projeto Gov Hub BR.

Após a submissão da Pull Request referente à Issue #277, foi realizado o acompanhamento do processo de revisão, análise dos feedbacks recebidos e validação da contribuição conforme os padrões adotados pelo projeto. Essa etapa permitiu compreender melhor o fluxo colaborativo de projetos open source e a importância da revisão por outros contribuidores antes da integração de novas alterações.

### Atividades Realizadas

| Data | Atividade | Tipo (Código/Doc/Discussão/Outro) | Link/Referência | Status |
|------|-----------|-----------------------------------|-----------------|--------|
| 25/05 - 01/06 | Acompanhamento da revisão da contribuição referente ao `CODE_OF_CONDUCT.md`             | Documentação/Discussão            | [Issue #277](https://github.com/GovHub-br/data-application-gov-hub/issues/277)      | Concluído |
| 02/06 - 08/06 | Análise dos feedbacks e validação dos ajustes solicitados durante o processo de revisão | Documentação                      | [Pull Request #322](https://github.com/GovHub-br/data-application-gov-hub/pull/322) | Concluído |

### Maiores Avanços

* Acompanhamento do ciclo completo de uma contribuição, desde a criação do documento até o processo de revisão;
* Maior compreensão do fluxo de Pull Requests em projetos open source;
* Evolução da percepção sobre a importância de revisão colaborativa para garantir qualidade e padronização;
* Consolidação da contribuição relacionada à governança do projeto Gov Hub BR.

### Maiores Dificuldades

* Entender quais ajustes eram necessários para manter a contribuição alinhada aos padrões existentes no projeto;
* Acompanhar o processo de revisão e considerar as sugestões feitas pelos mantenedores;
* Garantir que o documento permanecesse adequado ao contexto da comunidade.

### Aprendizados

* Pull Requests funcionam como mecanismos de validação e melhoria contínua em projetos colaborativos;
* A comunicação entre contribuidores e mantenedores é essencial para evolução de projetos open source;
* Documentações de governança possuem impacto direto na organização e sustentabilidade da comunidade.

### Plano Pessoal para a Próxima Sprint

* [ ] Continuar buscando novas oportunidades de contribuição no projeto;
* [ ] Explorar issues relacionadas a melhorias técnicas ou documentação;
* [ ] Aprofundar o conhecimento sobre os componentes internos do Gov Hub BR;
* [ ] Participar mais ativamente das discussões da comunidade.
