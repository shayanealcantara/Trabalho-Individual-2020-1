# Trabalho Individual - GCES - 2020/1

[![Maintainability](https://api.codeclimate.com/v1/badges/057f0b9189dadc5da694/maintainability)](https://codeclimate.com/github/shayanealcantara/Trabalho-Individual-2020-1/maintainability)

[![Ci Actions Status](https://github.com/shayanealcantara/Trabalho-Individual-2020-1/workflows/CI/badge.svg)](https://github.com/shayanealcantara/Trabalho-Individual-2020-1/actions)

[![codecov](https://codecov.io/gh/shayanealcantara/Trabalho-Individual-2020-1/branch/master/graph/badge.svg?token=QDP7ZBH2RZ)](https://codecov.io/gh/shayanealcantara/Trabalho-Individual-2020-1)

A Gestão de Configuração de Software é parte fundamental no curso de GCES, e dominar os conhecimentos de configuração de ambiente, containerização, virtualização, integração e deploy contínuo tem se tornado cada vez mais necessário para ingressar no mercado de trabalho.

Para exercitar estes conhecimentos, você deverá aplicar os conceitos estudados ao longo da disciplina no produto de software contido neste repositório.

O sistema se trata de uma aplicação Web, cuja funcionalidade consiste na pesquisa e exibição de perfis de usuários do GitHub, que é composta de:

- Front End escrito em Javascript, utilizando os frameworks Vue.JS e Quasar;
- Back End escrito em Ruby on Rails, utilizado em modo API;
- Banco de Dados PostgreSQL;

Para executar a aplicação na sua máquina, basta seguir o passo-a-passo descrito no arquivo [Descrição e Instruções](Descricao-e-Instrucoes.md).

## Critérios de avaliação

### 1. Containerização

A aplicação deverá ter seu ambiente completamente containerizado. Desta forma, cada subsistema (Front End, Back End e Banco de Dados) deverá ser isolado em um container individual.

Deverá ser utilizado um orquestrador para gerenciar comunicação entre os containers, o uso de credenciais, networks, volumes, entre outras configurações necessárias para a correta execução da aplicação.

Para realizar esta parte do trabalho, recomenda-se a utilização das ferramentas:

- Docker versão 17.04.0+
- Docker Compose com sintaxe na versão 3.2+

### 2. Integração contínua

Você deverá criar um 'Fork' deste repositório, onde será desenvolvida sua solução. Nele, cada commit submetido deverá passar por um sistema de integração contínua, realizando os seguintes estágios:

- Build: Construção completa do ambiente;
- Testes: Os testes automatizados da aplicação devem ser executados;
- Coleta de métricas: Deverá ser realizada a integração com algum serviço externo de coleta de métricas de qualidade;

O sistema de integração contínua deve exibir as informações de cada pipeline, e impedir que trechos de código que não passem corretamente por todo o processo sejam adicionados à 'branch default' do repositório.

Para esta parte do trabalho, poderá ser utilizada qualquer tecnologia ou ferramenta que o aluno desejar, como GitlabCI, TravisCI, CircleCI, Jenkins, CodeClimate, entre outras.

### 3. Deploy contínuo (Extra)

Caso cumpra todos os requisitos descritos acima, será atribuída uma pontuação extra para o aluno que configure sua pipeline de modo a publicar a aplicação automaticamente, sempre que um novo trecho de código seja integrado à branch default.

## Solução

A proposta de solução foi elaborada primeiramente a partir do uso de containerização utilizando Docker e Docker-Compose.

Para a Integração contínua, foi utilizada a ferramenta nativa do Github, o Github Actions, através do [workflow](https://github.com/shayanealcantara/Trabalho-Individual-2020-1/actions?query=workflow%3ACI) desenvolvido, que pode ser executado a cada push ou pull request feitos para as branches estáveis do projeto.

Para a coleta de métricas é utilizada a ferramenta [Code Climate](https://codeclimate.com/github/shayanealcantara/Trabalho-Individual-2020-1) e [Codecov](https://codecov.io/gh/shayanealcantara/Trabalho-Individual-2020-1), que geram relatórios sobre o código deste repositório. A Codecov em específico possui, além de sua própria interface, um funcionamento aliado a um bot que gera dados na própria página de criação de um pull request.

## Guia de Execução

Essa aplicação tem seu ambiente configurado através de conteiners [Docker](https://www.docker.com), portanto, tem como pré-requisitos a instalação do [Docker](https://www.docker.com/get-started) e [Docker-compose](https://docs.docker.com/compose/install/).

Também é necessário ter o [Git](https://git-scm.com) instalado para clonar o repositório.

Clonagem do repositório:

`git clone https://github.com/shayanealcantara/Trabalho-Individual-2020-1.git`

Execução do conteiner:  

`docker-compose up`  

Após esses passos a aplicação deverá estar acessível em:

`localhost:8080`

Para a execução dos testes dentro do conteiner:

`sudo docker exec -it api_rails bash`

`bundle exec rails test`
