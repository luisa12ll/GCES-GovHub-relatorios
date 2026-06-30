# Diário de Bordo – Ana Letícia Melo Pereira

**Disciplina:** Gerência de Configuração e Evolução de Software (GCES)

**Equipe:** Gov Hub BR

**Comunidade/Projeto de Software Livre:** Gov Hub BR

---

## Sprint 1 – [21/04/2026 – 04/05/2026]

**DAG de Ingestão PIM-PF Brasil (IBGE)**

---

## 1. Resumo da Sprint

A Issue #38 solicitou a criação de uma DAG dedicada no Apache Airflow para a ingestão diária dos dados da **Pesquisa Industrial Mensal — Produção Física Brasil (PIM-PF Brasil)**, divulgada mensalmente pelo IBGE por meio da API SIDRA (agregado 8888).

Antes desta entrega, o projeto já possuía uma DAG genérica (`ibge_ingest_dag`) que ingeria vários datasets do IBGE a partir de uma Airflow Variable de configuração. A demanda era isolar a PIM-PF em uma DAG própria, seguindo o padrão de ownership e observabilidade adotado pelo repositório.

| Atributo | Valor |
|---|---|
| Issue | #38 |
| Repositório | `GovHub-br/data-application-gov-hub` |
| Pesquisa IBGE | PIM-PF Brasil — SIDRA tabela 8888 |
| Tabela destino | `ibge.ibge_pim_pf_brasil` (PostgreSQL) |
| Schedule | `@daily` (configurável via Airflow Variable) |
| Padrão de carga | `ON CONFLICT DO UPDATE` — idempotente |

---

## 2. O Que Foi Realizado na Sprint

### 2.1 `ibge_pim_pf_brasil_ingest_dag.py`

Foi criado o arquivo da DAG principal com os seguintes elementos:

- **`DEFAULT_CONFIG`**: dicionário Python com todos os parâmetros da requisição à API IBGE — agregado, variáveis, períodos, nível geográfico, localidade, classificação e categoria.
- **Override via Airflow Variable**: a DAG lê a Variable `IBGE_PIM_PF_BRASIL_CONFIG` (JSON) dentro da task (evitando parse no scheduler) e mescla com o `DEFAULT_CONFIG` para permitir overrides parciais.
- **Task `fetch_and_store`**: única task da DAG, responsável por: (1) ler a config efetiva, (2) chamar `ClienteIBGE.get_dados_agregados()`, (3) transformar a resposta com `ClienteIBGE.transformar_resposta()`, (4) conectar ao PostgreSQL via `get_postgres_conn()` e (5) persistir via `ClientPostgresDB.insert_data()` com `ON CONFLICT DO UPDATE`.
- **Tratamento de erros diferenciado**:
  - `AirflowFailException` → API retornou `None`
  - `AirflowSkipException` → resposta sem registros (sem novas publicações no período)
  - `AirflowException` → erros inesperados
- **Chave primária composta**: `(variavel_id, localidade_id, periodo, classificacao_id, categoria_id)` — garante idempotência e captura de revisões retroativas.
- **Schedule dinâmico**: usa `get_dynamic_schedule()` com default `@daily`, permitindo ajuste por Variable sem deploy.

### 2.2 `README.md`

Foi criada documentação detalhada para a pasta de DAGs IBGE, incluindo:

- Tabela resumo de todas as DAGs IBGE do projeto
- Seção dedicada à `ibge_pim_pf_brasil_ingest_dag`: fonte de dados, frequência, schema da tabela destino, configuração via Airflow Variable e estratégia de carga incremental
- Instruções para descobrir IDs de variáveis/classificações/categorias via a API de metadados do IBGE
- Explicação da estratégia dos 13 períodos e da idempotência via `ON CONFLICT DO UPDATE`
- Orientação sobre quando criar DAGs dedicadas vs. usar a DAG genérica

---

## 3. Como Executar o Projeto

### Pré-requisitos

- Python 3.10+
- Apache Airflow 2.x (recomendado: via `docker-compose` do projeto)
- PostgreSQL acessível com credenciais configuradas no Airflow
- Variáveis de ambiente e Connections definidas conforme o README raiz do repositório

### 3.1 Subindo o ambiente local

```bash
docker compose up -d
docker compose ps   # aguarde todos os containers ficarem healthy
```

### 3.2 Verificando os arquivos no lugar certo

```
airflow_lappis/dags/data_ingest/ibge/ibge_pim_pf_brasil_ingest_dag.py
airflow_lappis/dags/data_ingest/ibge/README.md
```

O Airflow detecta novos arquivos na pasta `dags/` automaticamente — aguarde ~30 segundos.

### 3.3 Verificando a DAG na UI

1. Acesse `http://localhost:8080`
2. Procure por `ibge_pim_pf_brasil_ingest_dag`
3. Certifique-se de que está "Unpaused" (toggle azul)

### 3.4 Configuração via Airflow Variable (opcional)

Em **Admin > Variables**, crie `IBGE_PIM_PF_BRASIL_CONFIG` com o JSON:

```json
{
  "agregado": 8888,
  "variaveis": "all",
  "periodos": "-13",
  "nivel": "N1",
  "localidade": "1",
  "classificacao_id": null,
  "categoria": null
}
```

Se a Variable não existir, o `DEFAULT_CONFIG` hardcoded na DAG é usado automaticamente.

### 3.5 Disparando manualmente

Pela UI: clique em ▶ (Trigger DAG) na `ibge_pim_pf_brasil_ingest_dag`.

Ou via CLI:

```bash
docker compose exec airflow-scheduler \
  airflow dags trigger ibge_pim_pf_brasil_ingest_dag
```

### 3.6 Verificando os dados no banco

```bash
docker compose exec postgres \
  psql -U <usuario> -d <banco> \
  -c "SELECT COUNT(*) FROM ibge.ibge_pim_pf_brasil;"
```

---

## 4. Maiores Aprendizados

### 4.1 Por que DAGs dedicadas por dataset

Um dos principais aprendizados foi entender a motivação arquitetural por trás das DAGs dedicadas em vez de uma única DAG genérica parametrizada:

- **Observabilidade independente**: falha na PIM-PF não aparece misturada com SINAPI ou PIB na UI do Airflow.
- **Schedule independente**: cada pesquisa pode ter sua própria cadência sem afetar as demais.
- **Ownership claro**: o campo `owner` na `default_args` identifica o responsável por cada pipeline.
- **Facilidade de depuração**: o `dag_id` aparece em todos os logs, tornando o rastreamento trivial.

### 4.2 Idempotência com `ON CONFLICT DO UPDATE`

A estratégia de usar `INSERT ... ON CONFLICT (chave_primária) DO UPDATE` foi central nesta sprint. Ela resolve dois problemas de uma vez: permite reexecutar a DAG quantas vezes for necessário sem duplicar registros, e captura automaticamente revisões retroativas que o IBGE publica — o valor atualizado simplesmente sobrescreve o anterior na chave primária composta.

A escolha de 13 períodos (em vez de apenas 1 ou 3) cobre o janelamento típico de revisões da série PIM-PF sem pesar excessivamente nas execuções diárias.

### 4.3 Separação entre código do scheduler e do worker

Aprendemos que parsear variáveis de configuração no top-level do arquivo DAG (fora de tasks) é uma anti-pattern no Airflow: o scheduler importa todos os arquivos de DAGs periodicamente para descobrir novas DAGs e mudanças, e lógica cara ou com side-effects nesse escopo impacta diretamente a performance do scheduler. Por isso, a leitura da Airflow Variable foi colocada dentro da task `fetch_and_store`.

### 4.4 Hierarquia de exceções do Airflow

O uso correto de `AirflowFailException`, `AirflowSkipException` e `AirflowException` foi um aprendizado prático importante: cada uma sinaliza um estado distinto na UI do Airflow (failed, skipped, error), permitindo que alertas e SLAs sejam configurados com precisão — em vez de tratar tudo como um erro genérico.

---

## 5. Maiores Dificuldades

### 5.1 Compreender a estrutura da API IBGE SIDRA

A API de Dados Agregados do IBGE tem uma estrutura de resposta complexa: cada combinação de variável × localidade × período × classificação × categoria gera um registro separado, e os campos de IDs são strings mesmo sendo numéricos. Entender como o `ClienteIBGE.transformar_resposta()` achata essa estrutura hierárquica em registros tabulares levou tempo de leitura de código e experimentação com a API.

### 5.2 Definir a chave primária composta corretamente

Identificar quais campos formam uma chave única na tabela `ibge.ibge_pim_pf_brasil` exigiu análise cuidadosa do modelo de dados da SIDRA. A inclusão de `classificacao_id` e `categoria_id` (que podem ser `null` ou concatenados com pipe) foi necessária porque um mesmo período e variável pode ter múltiplos valores para diferentes classificações industriais (indústria geral, extrativa, de transformação etc.).

### 5.3 Navegar em uma base de código existente e seguir seus padrões

Trabalhar em um repositório open-source em andamento exigiu leitura prévia de outras DAGs (como `ibge_ingest_dag`) para entender os utilitários disponíveis (`ClienteIBGE`, `ClientPostgresDB`, `get_postgres_conn`, `get_dynamic_schedule`) e respeitar as convenções de nomenclatura, logging e estrutura de arquivos já estabelecidas. Divergir dos padrões do projeto poderia resultar em rejeição no Pull Request.

### 5.4 Escrever documentação técnica de qualidade

Produzir um README útil — que vai além de "o que o código faz" e explica decisões de design, parâmetros de configuração e estratégias de carga — foi desafiador. Exige colocar-se no lugar de um mantenedor futuro que não acompanhou o desenvolvimento e precisa entender, depurar e evoluir a DAG sem ajuda externa.

### 6. Plano Pessoal para a Próxima Sprint
- [ ] Ter o feedbakc sobre o PR e corrigir quaisquer erros identificados
- [ ] Ter o PR aprovado
- [ ] Encontrar novas issues mais complexas para contribuir