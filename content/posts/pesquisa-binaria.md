---
title: "Pesquisa binária"
date: 2023-08-27T11:30:03+00:00
# weight: 4999
# aliases: ["/first"]
tags: ["algoritmos"]
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

## Pesquisa binária

Às vezes realizamos uma simples tentativa “achamos que é uma tratativa simples” definimos um array para receber uma quantidade de informações como por exemplo nomes. Até aqui tudo bem, queremos pesquisar um nome e encontrar ele no array, mas será que realmente algum dia paramos e pensamos se esta abordagem é correta ? Se você automaticamente disse que sim parabéns, pare a leitura imediatamente.

Um tempo atrás quando aprendi a programar que não faz muito tempo, somente 4 anos (sim somente 4 anos, antes disso eu fazia alguns sites em html, css e muito pouco de javascript e acha que programava, mas somente depois que me aprofundei nos estudos percebi que eu não sabia nada e que realmente ainda não sei nada, ainda tem chão muita coisa para se aprender, eu era um tolo em pensar que programava, mas hoje sei e entendo que eu realmente estava mentindo pra mim mesmo), eu vivo me perguntando sobre diversas abordagens sobre “por que isso é feito dessa forma”, “Eu posso melhorar isso de alguma maneira?”, “Realmente não existe outra forma de otimizar essa função?” Se você também vive fazendo essa pergunta, entendo que você apenas quer realmente entender o que acontece debaixo dos panos e mergulhar mais profundamente para resolver essa questão na sua cabeça. Normalmente quando me faço essa pergunta eu viajo em meus pensamos e inicio uma série “Pesquisas sem parar”, fico perdido em assuntos que muitas vezes ficam complexos e complicados, onde preciso até mesmo parar um pouco e continuar depois com a cabeça mais fria e tranquila, pois atualmente em pleno século 21 ano 2023, somos bombardeados de informações pela internet, diante de tanta informação é difícil separar o que realmente é válido e o que não é válido (Esse pensamento eu me refiro a conteúdos de ócio criativo, não navegação em aplicativos como Instagram, Facebook ou qualquer outro feed de rolarem que te transforma em modo zumbi). Isso pra mim é puro lixo.

Estudando assuntos sobre algoritmos, descobri a pesquisa binária e sinceramente queria eu descobrir isso muito antes (eu ouvia falar, cheguei a ver na faculdade, mais não foi algo que me aprofundei para entender de fato, hoje como decidi ser um melhor programador, estou começando do início, desde o início de fato), uma parada simples mais que ao mesmo tempo é incrível, estou em uma ansiedade tremenda para ir mexer nos meus código pois já consegui pensar em várias situações onde irei usar a pesquisa binária.

Pensando de uma forma simples, se você pergunta a um programador com pouca experiência, o que ele faria em um array com 240K posições, normalmente o mesmo iria dizer fazer um foreach para percorrer o array e encontrar a posição desejada, mas imagina que se a posição de um array fosse exatamente a 240.000, iríamos percorrer o array 240.000 vezes? Claro que não, por esse motivo podemos usar a pesquisa binária que irá salvar a sua vida, mas antes vamos ver uma situação simples.

Nosso array tem 100 posições sendo:

```go
var array = [100]int{1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100}
```

Imaginamos isso em uma conversa de 2 pessoas, uma irá chutar o número e a segunda vai dizer se está correto, baixo ou alto

- Eren: 1
  - Mikasa: muito baixo
- Eren: 7
  - Mikasa: muito baixo
- Eren: 50
  - Mikasa: muito baixo
- Eren: 75
  - Mikasa: muito alto

(Sim os nomes são de personagens de animes, foda-se eu gosto) Nessa conversa simples, sabemos que o numero está dentro de 50 a 75, mais pensando melhor agora que sabemos, eliminamos uma enorme quantidade de busca, e com isso conseguindo fazer o próximo chute com mais precisão, e assim por diante até encontrar o número desejado.

- Eren: 63
  - Mikasa: alto demais

Agora que sabemos que o 64 é alto demais, posso fazer o próximo chute, pois está entre o 50 e 64. No caso o valor correto seria 55. Isso é uma pesquisa binária, sendo possível eliminar metade dos números a cada tentativa. Imagina a seguinte situação ao invés de percorrer 100 vezes o array, podemos percorrer somente 7 com a pesquisa binária

```go
Tamanho array = 100 -> 50 -> 25 -> 13 -> 7 -> 4 -> 2 -> 1
```

Entendeu como é simples, realizamos a busca somente 7 vezes, ao invés de 100 vezes. Agora na situação inicial com o nosso array de 240.000, não precisamos percorrer ele inteiro, somente 18 vezes, teremos um ganho incrível dessa forma. Segue um exemplo utilizando Go:

## Pesquisa binária em Go

```go
package main

import (
  "fmt"
)

func main() {
  var array = [100]int{1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100}
  var numero = 55
  var inicio = 0
  var fim = len(array) - 1
  var meio = 0
  var achou = false

  for inicio <= fim {
    meio = (inicio + fim) / 2
    if array[meio] == numero {
      achou = true
      break
    } else {
      if array[meio] < numero {
        inicio = meio + 1
      } else {
        fim = meio - 1
      }
    }
  }

  if achou {
    fmt.Println("O número", numero, "foi encontrado na posição", meio)
  } else {
    fmt.Println("O número", numero, "não foi encontrado")
  }
}
```

## Algoritmo de pesquisa binária

Todos os exemplos eu tirei do livro que estou lendo. Segue o link do livro:

- [Algoritmos: Teoria e Prática](https://amzn.to/47jr5o6)

Bom, esse é o meu primeiro artigo, tentei ser o mais claro possível para que eu consiga visualizar minhas informações no futuro. Tchau!