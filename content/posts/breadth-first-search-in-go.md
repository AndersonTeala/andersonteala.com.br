---
title: "Explorando Pesquisa em Largura (Breadth-First Search) com Go: Encontrando Vendedores"
date: 2023-11-22T20:59:03+00:00
# weight: 4998
# aliases: ["/first"]
tags: ["algoritmos", "go", "breadth-first-search", "busca-em-largura"]
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
# searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
editPost:
    URL: "https://github.com/AndersonTeala/breadth-first-search"
    Text: "GitHub"
    appendFilePath: false # to append file path to Edit link
---

## Explorando Pesquisa em Largura (Breadth-First Search) com Go: Encontrando Vendedores

Às vezes realizamos uma simples tentativa “achamos que é uma tratativa simples” definimos um array para receber uma quantidade de informações como por exemplo nomes. Até aqui tudo bem, queremos pesquisar um nome e encontrar ele no array, mas será que realmente algum dia paramos e pensamos qual é a abordagem correta ?

Fala ai pessoal beleza, aqui é o Teala!  E estou aqui para compartilhar com vocês um pouco do meu conhecimento sobre algoritmos. Hoje vamos falar sobre Pesquisa em Largura (Breadth-First Search).

Nas minhas aventuras de estudos sobre algoritmos, estou atualmente realizando a leitura de um livro chamado [Entendendo algoritmos](https://amzn.to/47P5MLn). Neste livro o autor [Aditya Y. Bhargava](https://www.linkedin.com/in/adityabhargava/) aborda diversos assuntos sobre algoritmos, e um deles é a Pesquisa em Largura (Breadth-First Search).

## O que é Pesquisa em Largura (Breadth-First Search) ?

Vamos lá. É uma técnica utilizada em algoritmos de grafos para realizar a busca de um vértice inicial até um vértice final. A Pesquisa em Largura conhecida como (Breadth-First Search) é basicamente utilizar uma fila para realizar uma busca, ou seja, o primeiro elemento a entrar na fila é o primeiro a sair.

## Como funciona a Pesquisa em Largura (Breadth-First Search) ?

A Pesquisa começa a partir de um vértice inicial, e a partir dele explora todos os seus vizinhos antes de mover para os vizinhos dos vizinhos. Em outras palavras, a Pesquisa em Largura (Breadth-First Search) explora os vértices mais próximos antes de explorar os vértices mais distantes. Realmente sempre verificando o primeiro elemento da fila.

Vamos imaginar o seguinte, que você mora em um condomínio (onde existe outros condomínios ao lado também), e você quer saber se algum dos seus vizinhos são vendedores de sorvetes (Estou dando um exemplo bem simples com sorvete para simplificar o entendimento, e por que também estamos em um calor de 40 graus aqui). Então você monta uma lista com todos os seus vizinhos e passa a bater na porta de cada um deles (estou imaginando essa cena), perguntando a cada vizinho um a um se ele é vendedor de sorvete, se caso ele não vende sorvete você risca o nome dele do topo da lista e coloca no final da lista todos os vizinhos do seu vizinho que você acabou de bater na porta dele e passa a bater na porta do vizinho da sua lista seguinte, porém sempre lembrando que cada um dos seus vizinhos possui outros vizinhos, e que cada vizinho, possui outros vizinhos, praticamente como em uma rede social, amigos de amigos de amigos de amigos, e assim por diante. Caso você encontre um vizinho que vende sorvete você para de bater na porta dos seus vizinhos e vai comprar sorvete com ele. Basicamente é isso que a Pesquisa em Largura (Breadth-First Search) faz.

## Vamos para a prática

Desenvolvi um pequeno exemplo simples em Go, para que você possa entender melhor como funciona a Pesquisa em Largura (Breadth-First Search). Vou explicar cada trecho de código e disponibilizar o código fonte no final do artigo. Este código em Go gera nomes falsos e verifica se algum desses nomes é um vendedor ("salesman").

- Importando as bibliotecas necessárias:
  - No inicio do código utilizo um pacote principal e a importação de três pacotes: fmt para formatação de saída, strings para manipulação de strings e github.com/brianvoe/gofakeit/v6 para geração de dados falsos.

```go
package main

import (
    "fmt"
    "strings"

    "github.com/brianvoe/gofakeit/v6"
)
```

- Variáveis globais:
  - Declarei duas variáveis globais, myName e initName.

```go
var myName string = "Anderson Teala"
var initName string = "Me"
```

- Função personIsASalesman:
  - Esta função recebe um nome como parâmetro e verifica se as duas primeiras letras do nome formam a string contida em initName. Retorna true se for o caso, indicando que a pessoa é um vendedor.

```go
func personIsASalesman(name string) bool {
    person := string(name[0]) + string(name[1])
    if person == initName {
        return true
    } else {
        return false
    }
}
```

- Função generateFakeName:
  - Esta função gera uma lista de nomes falsos usando a biblioteca gofakeit e retorna essa lista.

```go
func generateFakeName(quantityNames int) []string {
    fakeNamesMap := []string{myName}

    gofakeit.Seed(0)
    for i := 0; i < quantityNames; i++ {
        fakeNamesMap = append(fakeNamesMap, gofakeit.Name())
    }

    return fakeNamesMap
}
```

- Função findSeller:
  - Esta função procuro por um vendedor na lista dos nomes falsos. Ela usa a função personIsASalesman para verificar se um nome é de um vendedor. Se encontrar um vendedor, imprime a mensagem indicando o nome e o índice em que foi encontrado. Caso contrário, continua gerando mais nomes falsos.

```go
func findSeller(fakeNames []string) bool {
    verifiedNames := []string{}
    for index := 0; index < len(fakeNames); index++ {
        name := fakeNames[index]
        personHasBeenVerified := strings.Contains(strings.Join(verifiedNames, ","), name)
        if !personHasBeenVerified {
            if personIsASalesman(name) {
                fmt.Println("Person: "+name+", found in the index", index)
                return true
            } else {
                verifiedNames = append(verifiedNames, name)
                namesGenerated := generateFakeName(10)
                fakeNames = append(fakeNames, namesGenerated...)
            }
        }
    }
    fmt.Println("verifiedNames", verifiedNames)
    return false
}
```

- Função main:
  - A função main inicia o processo gerando uma lista de 10 nomes falsos e em seguida chama a função findSeller para procurar por um vendedor nesta lista. O resultado é impresso no console.

```go
func main() {
    fakeNames := generateFakeName(10)
    findSeller(fakeNames)
}
```

## Conclusão

- A Pesquisa em Largura (Breadth-First Search) é uma técnica muito útil para encontrar o caminho mais curto entre dois vértices em um grafo.
- Ela também pode ser usada para encontrar o caminho mais curto em uma árvore, pois uma árvore é um tipo especial de grafo.
- Você consegue encontrar se existe um caminho de A para B.
- Se o vendedor de sorvete existir, você encontrará ele no caminho mais curto.
- Lembre-se que a lista deve ser uma fila, ou seja, o primeiro elemento a entrar na fila é o primeiro a sair. Caso contrário você não encontrará o caminho mais curto.
- Cada vizinho verificado deve ser retirado e não verificado novamente. Caso contrário você entra em um loop infinito.

## Referência do livro

- [Entendendo Algoritmos](https://amzn.to/47P5MLn)

## Código fonte

- [Breadth-First Search](https://github.com/AndersonTeala/breadth-first-search)