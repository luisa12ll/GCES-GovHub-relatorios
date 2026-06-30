<p align="center">
  <img src="https://raw.githubusercontent.com/GovHub-br/gov-hub/main/docs/assets/logo.png" alt="GovHub Logo" width="300">
</p>


<p align="center">
  <img src="https://img.shields.io/badge/Status-Em%20Desenvolvimento-green?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Open%20Source-SIM-blue?style=for-the-badge" alt="Open Source">
</p>

# GCES · GovHub BR

> **Gerência de Configuração e Evolução de Software** > Contribuições open source ao ecossistema [GovHub](https://gov-hub.io) — Plataforma de transparência e dados públicos desenvolvida pelo Lab Livre · UnB.

---

## Sobre o Projeto

Este repositório centraliza os relatórios, documentos técnicos e a jornada de evolução da equipe durante a disciplina de **GCES (2026/1)** na Universidade de Brasília. Nosso foco é contribuir com melhorias na arquitetura de dados e na visualização de informações estratégicas do governo federal.

### Stack Tecnológica
A equipe opera com as seguintes tecnologias principais:
- **Orquestração:** Apache Airflow
- **Transformação:** dbt (Data Build Tool)
- **Visualização:** Apache Superset
- **Infraestrutura:** Docker & PostgreSQL

---

## Organização do Repositório

A documentação foi estruturada para facilitar a navegação e o rastreio das contribuições:

| Seção | Descrição |
| :--- | :--- |
| **Sprints** | Relatórios de cada ciclo de desenvolvimento e entregas coletivas. |
| **Contribuições**| Diários de bordo individuais de cada um dos 17 integrantes. |
| **Materiais**| Templates, modelos de relatórios e guias de referência. |

---

## Como Rodar Localmente

Para visualizar a documentação no navegador de forma simples, use o servidor HTTP embutido do Python.

1. No diretório raiz do repositório, execute:

```bash
python3 -m http.server 8000
```

Se o comando acima não funcionar no seu ambiente, tente:

```bash
python -m http.server 8000
```

2. Abra no navegador:

```text
http://localhost:8000/docs/
```

3. Para encerrar o servidor, use `Ctrl + C` no terminal.

### Opção com Watch (auto-reload)

Se quiser recarregamento automático da página ao editar os arquivos da documentação, use o Docsify CLI.

Pré-requisito: ter Node.js e npm instalados.

```bash
npx docsify-cli serve docs --port 8000
```

Depois, abra:

```text
http://localhost:8000
```

---

## Fluxo de Trabalho (Gitflow)

Para manter a integridade da branch `main`, adotamos as seguintes práticas:
- **Branches de Feature:** Alterações isoladas em `feature/nome-da-tarefa`.
- **Pull Requests:** O merge para a `main` requer revisão e aprovação.
- **Commits Semânticos:** Seguimos o padrão [Conventional Commits](https://www.conventionalcommits.org/).

---

## Equipe 

<div align="center">

| **[Ana Letícia](https://github.com/ghost)**<br><sub>211031584</sub> | **[Anna Clara](https://github.com/annacbrandao)**<br><sub>222006534</sub> | **[Artur Camargos](https://github.com/Arturdcr)**<br><sub>221038785</sub> | **[Gabriel Saraiva](https://github.com/gabrielsarcan)**<br><sub>202045769</sub> | **[Gabryel Sousa](https://github.com/gabryelns)**<br><sub>221022570</sub> | **[João Lucas](https://github.com/ghost)**<br><sub>222025324</sub> | **[João Vitor](https://github.com/Joa0V)**<br><sub>221022014</sub> |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| <img src="https://github.com/ghost.png" width="90"> | <img src="https://github.com/annacbrandao.png" width="90"> | <img src="https://github.com/Arturdcr.png" width="90"> | <img src="https://github.com/gabrielsarcan.png" width="90"> | <img src="https://github.com/gabryelns.png" width="90"> | <img src="https://github.com/ghost.png" width="90"> | <img src="https://github.com/Joa0V.png" width="90"> |

<br>

| **[Júlia Takaki](https://github.com/juliatakaki)**<br><sub>221029249</sub> | **[Letícia Cássia](https://github.com/HladczukLe)**<br><sub>221039209</sub> | **[Lívia Rodrigues](https://github.com/Liviarodrigues1)**<br><sub>180105051</sub> | **[Lucas Marques](https://github.com/LucasOliveiraDiasMarquesFerreira)**<br><sub>211062787</sub> | **[Lucas Guimarães](https://github.com/Lcsgborges)**<br><sub>222015159</sub> | **[Lucas Martins](https://github.com/martinsglucas)**<br><sub>221022088</sub> |
| :---: | :---: | :---: | :---: | :---: | :---: |
| <img src="https://github.com/juliatakaki.png" width="90"> | <img src="https://github.com/HladczukLe.png" width="90"> | <img src="https://github.com/Liviarodrigues1.png" width="90"> | <img src="https://github.com/LucasOliveiraDiasMarquesFerreira.png" width="90"> | <img src="https://github.com/Lcsgborges.png" width="90"> | <img src="https://github.com/martinsglucas.png" width="90"> |

<br>

| **[Luísa Ferreira](https://github.com/luisa12ll)**<br><sub>232014807</sub> | **[Maria Clara](https://github.com/alvezclari)**<br><sub>221008329</sub> | **[Maria Eduarda](https://github.com/mariadenis)**<br><sub>232014502</sub> | **[Matheus Brant](https://github.com/MatheussBrant)**<br><sub>222037737</sub> | **[Milena Fernandes](https://github.com/MilenaFRocha)**<br><sub>222022000</sub> | **[Rafael Melo](https://github.com/rmatuda)**<br><sub>222006383</sub> |
| :---: | :---: | :---: | :---: | :---: | :---: |
| <img src="https://github.com/luisa12ll.png" width="90"> | <img src="https://github.com/alvezclari.png" width="90"> | <img src="https://github.com/mariadenis.png" width="90"> | <img src="https://github.com/MatheussBrant.png" width="90"> | <img src="https://github.com/MilenaFRocha.png" width="90"> | <img src="https://github.com/rmatuda.png" width="90"> |

<br>

| **[Renann Gomes](https://github.com/renannogomes)**<br><sub>200043030</sub>
| :---: |
| <img src="https://github.com/renannogomes.png" width="90"> | 

</div>
