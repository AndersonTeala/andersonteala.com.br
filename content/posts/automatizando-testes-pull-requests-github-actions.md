---
title: "Automatizando Testes e Pull Requests com GitHub Actions"
date: 2023-09-18T11:30:03+00:00
weight: 3
# aliases: ["/first"]
tags: ["gitHub", "actions", "CI/CD", "automação", "testes", "pull requests"]
author: "Anderson Teala"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: ""
canonicalURL: ""
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/AndersonTeala"
    Text: "GitHub"
    appendFilePath: true # to append file path to Edit link
---

## Introdução

Hoje eu vim escrever um pouco sobre automação de processos no github pois é essencial para melhorar a eficiência e a qualidade do desenvolvimento do seu software.

Olá pessoal beleza, aqui é o Teala, espero que estejam bem! Hoje eu vim escrever um pouco sobre automação de processos no github pois é essencial para melhorar a eficiência e a qualidade do desenvolvimento do seu software.

Mais antes quero entrar em um outro assunto que, quem nunca subiu um código “Na minha máquina funciona” pois é, essa é a famosa frase quando um amigo iniciante nos envia o link para visualizarmos “localhost:8080” sim senhores eu já vi isso acontecer mais admito nunca fiz isso. Assim como todo mundo eu começei codando sem ter experiência nenhuma e sem saber porra nenhuma mesmo, e está tudo bem foda-se, ninguém nasce sabendo, com isso você irá aprendendo com o dia a dia, com erros e tentativas, mais isso é conversa para outro dia, pois o assunto aqui é outro.

Antigamente quando começei a codar, eu e um amigo iniciamos um projeto de ecommerce, sim pode dar risada eramos novato que mal saiu das fraudas e queria ir para marte, quem nunca né? Mais o engraçado era que nosso projeto ecommerce era até que interessante, esse realmente nunca saiu do papel, atualmente tenho outros projetos com ele que funcionam e estão em produção, mais esse abandonamos de fato. Só que o engraçado foi que esse projeto ele estava desenvolvendo o backend e eu o frontend (Eu vou tentar encontrar esse projeto e anexo aqui) mais continuando, quando ele me enviou a pasta do backend para testar localmente, foi o máximo, nada funcionava, eu estava em um ambiente linux e ele em um ambiente windows, a pasta onde tinha as imagens estava como “c://home/…..” acreditem estava assim, mais claro, eramos novatos, iriamos saber disso somente depois que percebemos o inevitável, foi somente com o dia a dia quebrando a cara e aprendendo com isso, mais hoje podemos facilmente resolver essa situação com um arquivo .env, docker etc…. (outro assunto para outro dia)

Mesmo resolvendo isso com variaveis de ambiente e um docker-compose, ainda temos ambientes diferentes, e muito diferentes, mais imagino o seguinte, desenvolvendo uma aplicação para importar X arquivo no banco de dados X, onde temos uma série de validações e funções para diversas validações que esperamos que a rotina realize, até mesmo conexão e dependencia de um redis e etc… pois é ao codar lindo e maravilhoso durante a noite inteira nosso código funciona e faz exatamente o que esperamos, mais imagine o seguinte, ao realizar um deploy desse código em produção ou passar para outro dev ele simplementes não funciona e você pensa, caralho fudeo.

Pois é, fudeo mesmo éééé o que que há velhinho????

## Introdução ao GitHub Actions

GitHub Actions, é um poderosa ferramente meus amigos para automação oferencia pelo GitHub que pernite você criar fluxos de trabalho personalizados, para executar ações específicas sempre que ocorrerem eventos em seu repositório, Isso inclui a capacidade de executar testes automaticamente, criar pull requests e muito mais.

### Seu Fluxo de Trabalho

A primeira etapa para automatizar seus testes e pull requests é configurar um fluxo de trabalho no seu repositório GitHub. Isso é feito criando um arquivo YAML no diretório .github/workflows do seu repositório. Vamos dar uma olhada em um exemplo de arquivo de configuração:

```yaml
name: Test Go code with .env setup, PostgreSQL, and Redis

on:
  push:
    branches:
      - main

jobs:
  setup:
    runs-on: ubuntu-latest

    steps:
      # ... Configurações de ambiente e preparação de artefatos ...

  test:
    needs: setup
    runs-on: ubuntu-latest

    steps:
      # ... Download de artefatos e execução de testes ...

  create_pull_request:
    needs: test
    runs-on: ubuntu-latest
    steps:
      # ... Criação de um pull request após os testes bem-sucedidos ...
```

### Passo a Passo

- Configuração do Ambiente (Setup):
  - Na seção setup, você pode configurar o ambiente necessário para seus testes. Isso pode incluir a inicialização de serviços Docker, a criação de arquivos de configuração ou qualquer outra configuração específica.
- Execução de Testes (Test):
  - A seção test é onde você executa seus testes. Você pode baixar artefatos gerados na seção de configuração do ambiente, executar seus testes e, se eles passarem, continuar para a próxima etapa.
- Criação de Pull Request (Create Pull Request):
  - A seção create_pull_request cria um pull request na branch main do seu repositório após os testes terem sido bem-sucedidos. Isso pode ser útil para garantir que apenas código testado e aprovado seja incorporado ao projeto principal.

### Gerenciando Artefatos

Uma parte importante desse processo é o compartilhamento de informações entre as etapas do fluxo de trabalho. Os “artefatos” são uma maneira de armazenar informações que podem ser acessadas entre as etapas. No exemplo acima, usamos a ação actions/upload-artifact para enviar artefatos gerados na etapa de configuração para a etapa de teste.

### Configurando Segredos

Sério isso é muito importante para autenticação e acesso a recursos privados, como repositórios privados do GitHub, é importante configurar segredos em seu repositório. Neste artigo, eu usei secrets.GIT_TOKEN como um exemplo de token de acesso para criar um pull request no GitHub.

## As Aventuras de CI/CD, o Mestre da Automação

“Meus caros, deixem-me contar uma história sobre um dia em que precisei recorrer ao CI/CD, essa arma secreta do mundo da tecnologia. A ocasião era uma missão delicada que envolvia a entrega de um software altamente confidencial. Era como se eu estivesse navegando em águas profundas e perigosas, cercado por tubarões famintos.

Era uma manhã chuvosa em algum lugar remoto, e eu estava cercado por uma equipe de desenvolvedores que estavam trabalhando incansavelmente para concluir o código de um projeto ultra-secreto. O que tornava tudo ainda mais desafiador era o prazo apertado e a necessidade de manter a operação sob total sigilo.

Foi nesse momento que eu soube que precisava do CI/CD ao meu lado. O CI/CD era como um aliado silencioso, um agente secreto infiltrado no mundo da automação de software. Ele podia automatizar o processo de construção, teste e implantação, garantindo que nosso software fosse entregue com precisão e eficiência.

Eu me virei para a equipe e disse: “Preparem-se, pois vamos implantar o CI/CD”. Todos sabiam que era um sinal de que estávamos prestes a entrar em território desconhecido. O CI/CD não era uma ferramenta qualquer; ele era como uma máquina bem azeitada, pronta para entrar em ação.

Assim que acionamos o CI/CD, ele começou a trabalhar sua magia. O código foi verificado, os testes automatizados foram executados e os artefatos foram criados. Era uma visão hipnotizante, observar como o CI/CD coordenava todas as partes móveis sem pestanejar.

E então veio a parte mais intrigante. O CI/CD orquestrou a implantação do software em nosso ambiente de produção, como um maestro conduzindo uma sinfonia. E o melhor de tudo, ele fez isso sem causar nenhuma interrupção para nossos usuários.

Enquanto eu observava a operação se desenrolar, não pude deixar de admirar a eficiência do CI/CD. Era como se ele estivesse dançando no limite entre o caos e a ordem, mantendo tudo sob controle.

Ao final da operação, olhei para a equipe e disse: “Missão cumprida”. Graças ao CI/CD, tínhamos entregado nosso software de maneira rápida e eficaz, mantendo nossos segredos seguros.

E assim, meus caros, essa é a história de como o CI/CD, essa ferramenta mágica da automação, nos ajudou a superar um dos desafios mais difíceis que já enfrentei. Às vezes, na vida do crime, é preciso recorrer às armas mais inesperadas para alcançar o sucesso.”

## Algoritmo de pesquisa binária

Todos os exemplos eu tirei do livro que estou lendo. Segue o link do livro:

- [Algoritmos: Teoria e Prática](https://amzn.to/47jr5o6)

## Conclusão

Automatizar testes e a criação de pull requests pode economizar tempo e melhorar a qualidade do seu código. O GitHub Actions oferece uma maneira poderosa de configurar esses processos de automação em seu repositório GitHub. Personalize o fluxo de trabalho de acordo com suas necessidades específicas e aproveite os benefícios da automação.

Espero que este artigo tenha sido útil para entender como automatizar testes e pull requests com o GitHub Actions. Lembre-se de ajustar as configurações para atender às necessidades do seu projeto e aproveitar ao máximo essa poderosa ferramenta de automação.

Segue agora uma pequena história sobre CI/CD, porém jamais saberemos se ela é de fato verdadeira.