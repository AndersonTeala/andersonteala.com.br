---
title: "Gerar imagens com I.A - ComfyUI"
date: 2025-10-05T10:14:37+00:00
## weight: 4998
## aliases: ["/first"]
tags: ["I.A", "confyui"]
author: "Anderson Teala"
## author: ["Me", "You"] ## multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: ""
canonicalURL: ""
## canonicalURL: "https://canonical.url/to/page"
disableHLJS: true ## to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
## searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: ## image path/url
    alt: "<alt text>" ## alt text
    caption: "<text>" ## display caption under cover
    relative: false ## when using page bundles set this to true
editPost:
    URL: "https://github.com/AndersonTeala/"
    Text: "GitHub"
    appendFilePath: false ## to append file path to Edit link
---

Hoje ta foda!!! acordei e decidi que iria subir um ComfyUI para gerar imagens com I.A, trouxa eu pensar que seria fácil, estava com uma preguiça enorme, e decidi pegar o primeiro repositório do github que encontrei que sobe um ComfyUI com vários modelos selecionados e etc… mais eu me fudi, claro sempre de costume eu valido para ver o Dockerfile, nada de subir o docker diretamente, vai que seja uma armadilha e colocam minha raiz, mais beleza arquivo Dockerfile validado, docker-compose também estava realmente show de bola, besta eu fui lá e subi o container, iniciou os download e para minha surpresa tive problemas com os modelos, era recente o repositório que baixei, tinha apenas 4 meses, mais como as coisas mudam rapidamente eu decidi montar o meu próprio, mais adianto, é chato pra caralho, tive vários problemas, varias situações chatas, e quero compartilhar hoje aqui com vocês caso queriam fazer essa aventura também.

Para montar e gerar as imagens foi tranquilo, apenas precisa procurar um pouco e entender como funciona para montar um Workflow, depois que entender como funciona fica fácil no final.

Meu maior problema foi para colocar os modelos, pois alguns as vezes estava funcionando e depois do nada não existia.

Mediante a todos os problemas que eu tive, decidi ir a fundo e descomplicar essa merda inteira, pois ComfyUI você acha que e fácil e simples? pois é foi enganado.

Fala ai pessoal tudo bem? Eu espero que sim! Aqui e o Teala e hoje eu quero falar de ComfyUI.

## O que e ComfyUI?

Resumo básico, é uma interface gráfica modular para Stable Diffusion, o modelo de IA usado para gerar imagens a partir de texto, imagens ou ambos, mais uma ferramenta que permite você montar workflows visuais para gerar imagens com I.A basicamente isso, vários “nós” que se conectam para varias etapas do processo, carrega um modelo, defini o prompt e pronto.

Mais ai meus amigos pensamos sobre workflows, nós que se conectam, prompts para gerar bem simples, pois é não é tão simples assim essa parada, alguns workflows são realmente complexos, mais você pode gerar alguns simples para começar.

A estrutura é simples de entender, chamada de Node-based system, onde cada nó executa uma função, carrega modelo, gera ruído, aplica prompt, decodifica imagem e etc. O grafo (Workflow) conecta nós nas entradas e saídas, segue um exemplo de um Wokflow um pouco chato. Visto assim sem entender o que cada nó está fazendo, realmente fica complexo na nossa cabeça, mais no final é simples, mesma coisa quando iniciamos um código, daqui a pouco a estrutura fica gigante, onde qualquer pessoa bate o olho no código bem estruturado que não tem muitos conhecimento e pensa ser um bicho de 7 cabeças.

![workflow001.png](/images/workflow001.png)

Utiliza um modelo baseado em checkpoints, loras, embeddings entre vários outros, onde sendo necessário informar um prompt positivo e outro negativo, explico daqui a pouco.

## Modelos

Todos os modelos de I.A carrega um banco de dados vetorial em memória da GPU, ou seja VRAM para processar, pois isso precisa de uma boa GPU para rodar, consegue com CPU, porém muito mais lenta, eu consegui rodar somente com CPU modelos de textos baseados no GPT da vida, porém muito mais muito lento consumindo 100% do meu server. Gerar imagem nem pensar.

Todos esses modelos como o GPT carrega os poderosos parâmetros, engraçado que uma vez, um cara que tinha uma I.A desenvolvida dentro da empresa dele (SEGUNDO PALABRAS DELE CLARO) a I.A tinha mais de 4 BILHÕES de parâmetros, foi engraçado por que todos que estavam na conversa sabia o que exatamente o cara estava falando, não surgiu uma risada pois era uma ambiente profissional, e o mais engraçado foi quando ele terminou a fala dele, ficou olhando para cada um, para ver se alguém tinha adorado ouvir aquilo, sério os olhos dele chega brilhava. Mais passou vergonha pois todos que estavam na conversa, entendia claramente sobre o assunto, mais vamos voltar para o que interessa.

Como disse o modelo GPT ou outros modelos, 2B, 4B, 7B, 350B.. e etc. São “BILHÕES” de parâmetros, imagina quando se ouve isso, o poder que não tem em cima de uma pessoa com zero conhecimentos no assunto. Mais isso nada mais é que um simples número, que representa qualquer coisa dentro de milhões de dados.

## Como eu entendo os modelos de IA (UM JEITO BEM GROSSEIRO)

De uma maneira bem simples, simplificada mesmo, eu gosto de pensar que os modelos de IA funcionam como sistemas de compressão muito mais avançados.

Eles pegam tipo petabytes de textos, imagens, códigos, postagens e vai quebrando tudo isso em tokens ou seja pequenas unidade de informação, assim aprendendo relações estatísticas entre eles.

Mais essas relações são representadas em um espaço vetorial, mas não um espaço de três dimensões como no mundo físico, e sim em centenas ou milhares de dimensões matemáticas.

Basicamente em outra palavras, o modelo vai aprender a posicionar cada token dentro desse espaço de forma que os tokens com significados parecidos, fiquem próximos entre eles mesmo.

Sendo essa a base dos chamados Vector Space Models (VSMs) o mesmo conceito que está por trás de ferramentas tipo o Elasticsearch, ou de recursos de Full-Text Search do PostgreSQLm buscando por relevância de texto.

Aquele processo d treinando de I.A que todos fizem, a parte mais demorada e que pode levar meses e meses, basicamente faz o modelo aprender uma nova forma de representar o mundo.

É como se ele criasse um idioma interno, tipo um vocabulário matemático próprio.

Assim quando você vai lá e conversa com um GPT da vida, o texto que você escreve nele, é convertido para essa língua interna em conjunto de vetores conhecidos como o famosos embeddings.

O modelo “raciocina” e por favor, entenda o termo “RACIOCINA” que irei explicar pois não venha aqui comentar e me dizer que a I.A é senciente, não me venha com essa porra aqui.

Então nesse formato vetorial o modelo raciocina e depois traduz o resultado de volta para o nosso idioma, por isso dizemos por exemplo que o GPT entende as palavras em termos de distâncias e direções dentro desse espaço multidimensional. Não é MAGIA.

O mais bacana e interessante é que qualquer tipo de dados, pode ser representado dessa forma, tudo pode ser convertido em dados, o audio pode ser convertido e transformado em texto, texto em embeddings. Vídeos podem ser divididos em quadros de iamgens com informações.

Mais no final das contas tudo pode ser convertido em estruturas numéricas e é isso que os modelos de IA processam. Tudo é matemática não mágica, apenas muita MATEMÁTICA, estatística e poder computacional em vetores.

Para resumir tudo isso, pensamos em modelos de I.A como compressões inteligentes, que ajuda a entender por que eles conseguem gerar, traduzir e relacionar informações tão naturalmente, por esse motivo vem as pessoas e me diz que a I.A pensa sozinha, vai se fude.

Então antes o que era um texto, imagem ou audio, vai virar dados numéricos, em um espaço vetorial gigantesco, e dentro desse “UNIVERSO” de números, a I.A vai “raciocina”.

![explosion.png](/images/explosion.png)

## Workflow - Fluxo de nós (nodes)

No ComfyUI, um workflow é o fluxo de nós (nodes) que via definir como uma imagem vai ser gerada, processada e transformada dentro do sistema.

![workflow002.png](/images/workflow002.png)

Tem caras que montam uns Workflow complexo, ele é tipo um pipeline visual, que via conectar os componentes do modelo, tipo os prompts, difusores, samplers etc. Determinando passo a passo que o ComfyUI vai fazer para produzir o resultado final esperado.

Mais conseguimos montar uma estrutura básica de um Workflow, vou explicar todos calma.

- Checkpoints - Modelo base
    - Arquivos principal do modelo de difusão, com os pesos treinados em milhões de imagens, ele é tipo o cérebro da IA geradora de imagens.
    - Define o estilo, realismo e também a capacidade geral da geração.
- VAE - Autoencoders Variacionais
    - Redes que convertem imagens entre o espaço latente e o espaço visual.
    - Codifica imagens e decodifica elas, ajustando as cores e contrates.
- Text Encoders - Codificadores de Texto
    - Modelo que transforma o texto do prompt em vetores numéricos (expliquei mais a cima sobre os vetores numéricos, ou seja os embeddings).
    - Esse modelo de difusão permite que o modelo compreenda o significado do prompt, basicamente ele relaciona as palavras com conceitos visuais.
- CLIP Vision
    - É uma versão visual do CLIP, usado para entender imagens em vez de texto.
    - Permitindo o modelo analisar as imagens de referência, compara estilos ou extrair os embeddings visuais.
    - Bom para image-to-image.
- Diffusion Models
    - Esse é o núcleo do processo, o modelo que aprendem a remover ruído e gradualmente de uma imagem até formar algo coerente.
    - Vai ser responsável por gerar as imagens durante todo o processo de sampling.
    - Sendo o mecanismo matemático que desenha a imagem.
- Loras
    - Módulos adicionais que vai ajustar o comportamento de um modelo base e sem precisar treinar novamente. Permitindo adicionar novos estilos, personagens, poses, roupas ou temas e etc.
- ControlNet
    - Aqui ele adiciona um controle estrutural tipo pose, bordas, profundidade e etc.
    - Ele garante que a imagem vai seguir uma estrutura ou guia sem perder a criatividade do prompt.
- Upscale Models
    - Especializado em aumentar a resolução e melhorar detalhes de uma imagem sem perder qualidade, tive problemas na minha placa de vídeo (RTX 4050) por causa disso.
- Embeddings
    - Aqui são pequenos vetores de texto treinados para representar conceitos específicos, tipo pessoas, estilos e objetos. Permitindo ensinar o modelo novos conceitos sem treinar um modelo inteiro entende?
    - Básico chamado nos prompts como tokens especiais.
- Save Image
    - O próprio nome já diz, não existe segredo aqui, ele vai salvar a imagem gerada no disco, como eu subi o meu ComfyUI em docker, não tive problemas para salvar a imagem na minha raiz do projeto.
- Preview Image
    - Por ultimo o nó que vai exibir a imagem diretamente na interface do ComfyUI, sem precisar salvar ela, consegue visualizar o resultado em tempo real para ajustes rápidos de params.

Aqui você tem uma **pipeline mínima** para gerar imagens no ComfyUI.

```
[Checkpoint] → [CLIP Text Encode] → [KSampler]
   ↓                                   ↓
 [VAE Decode] → [Preview Image] → [Save Image]
```

Veja o Workflow com os nós

![workflow003.png](/images/workflow003.png)

## Checkpoints SD 1.5

Aqui eu tive que pesquisar um pouco, perguntei para umas I.A, pesquisei alguns vídeos e entendi que é muito importante entender isso, ele é praticamente essencial para dominar o ComfyUI e qualquer pipeline de geração de imagens.

O que são? os checkpoints SD 1.5 é um modelo base da versão 1.5 do Stable Diffusion. Pronto explicado valeu e falou!

Zoeira, vamos lá. eles contêm os pesos e os params do modelo neural que foi treinado para gerar as imagens a partir de texto, ele é o cérebro do Stable Diffusion 1.5, redes de difusão latente treinadas para gerar imagens em resolução 512x512 nativo ok, e a aprtir de embeddings de texto.

Encontrei umas informações que o pessoal chama de características principais do SD 1.5

- Base Architecture
    - Trabalha em espaço latente comprimido.
- Resolução nativa
    - 512x512 sendo possível gerar em outras com qualidade boa.
- Treinamento
    - Treinado com o dataset LAION-5B, basicamente imagens + legendas.
- Tamanho
    - Normalmente encontrado em tamanhos como 2 GB, 4 GB.
- Desempenho
    - Rápido, leve e amplamente compatível com GPUs menores, serviu muito bem na minha RTX 4050 6 GB RAM.

Ótimos para gerar modelos de imagens 2D, estilo artístico, realista ou anime. Uma base para treinar ou aplicar em Loras. Workflows leves como informei a cima, ótimo rápido e leve.

Mais entendeu né, leve, rápido, tem extensa compatibilidade com modelos Loras, ControlNets e embeddings, eu encontrei 2 repositórios GIGANTESCOS de modelos prontos para baixar e usar, não precisa nem procurar muito, os resultados dele é bom, prompts curto, fácil de modificar e treinar.

Como pode perceber, tem suas vantagens, mais também suas limitações. Resolução nativa baixa de 512x512, pode aumentar mais já sabe. Não adianta montar prompts longos, pois são menos precisos, rostos e mãos podem sair deformados sem boas Loras ou refinadores para resolver esse problema, já viu aquelas imagens com vários dedos? Pois é.

## SDXL

Pelo nome é possível entender um pouco, SDCL - Stable Diffusion XL, é uma nova geração de modelo de difusão criado. Basicamente uma evolução do Stable Diffusion 1.5, com arquitetura refinada, melhor pipeline de texto e iamgem, com suporte nativo a resoluções 1024x1024 px, somente tome cuidado, veja qual as limitações da sua placa de vídeo.

Mais em resumo esse cara é um modelo mais inteligente, detalhado e natural, com uma melhor compreensão de linguagem, iluminação e composição visual.

Características desse modelos

- Arquitetura
    - Latent Diffusion 2.1 aprimorada com 2 estágios
- Resolução nativa
    - Melhor claro sendo 1024 x 1024 px
- Tamanho
    - Esse é maior, sendo mais de 6 GB
- Pipeline
    - 2 estágios base e refiner
- Treinamento
    - Dataset e imagens de alta qualidade
- Compatibilidade
    - Nova geração, Loras e ControlNets precisam ser feitos para SDXL

Aqui a pipeline funciona dividindo o processo de geração em duas etapas principais, base e Refiner, a base gera a iamgem bruta, estrutura, cores composição, com resolução que comentei, 1024x1024 e o refiner é como o nome diz, refinador que melhora detalhes finos, iluminação e texturas da imagem, sendo possível utilizar somente a base para gerar mais rápido.

Exemplo de Workflow SDXL

```
[Load Checkpoint: SDXL Base]
→ [CLIP Text Encode (Prompt)]
→ [CLIP Text Encode (Negative Prompt)]
→ [KSampler (steps=20)]
→ [VAE Decode]
→ [Preview Image]
→ [Save Image]

(Base Output Latent)
→ [Load Checkpoint: SDXL Refiner]
→ [KSampler (steps=10, refiner mode)]
→ [VAE Decode]
→ [Preview Image]
→ [Save Image]
```

Veja o workflow com os nós dele, não se assuste

![workflow004.png](/images/workflow004.png)

Aqui você percebeu né que tem vantagens na alta qualidade, compreensão de texto muito superior, melhor anatomia, iluminação, não depende tanto de modelos Loras, pois muitos já estão embutidos nele, ele vai entender os prompts mais complexos e descritivos, sendo exelente na composição, entendo bem as relações dos objetos, pipelines de dois estágios. Somente toma cuidado com a limitações, pois ele é mais pesado, exigindo de 8 a 12 GB de VRAM, sim é pesado, minha RXT 4050 não aguentou esse modelo, principalmente usando Base + Refiner. Nem todos os Loras e ControlNets são compatíveis com eles, prcisa usar  versões feitas quase que especificamente para o SDXL, é claramente um modelo mais lento, processamento muito mais demorado que o SD 1.5, os prompts são longos e necessários, ele entende tranquilamente as frases mais precisa ser detalhado.

Resumo rápido entre os modelos, SD 1.5 resolução nativa 512x512, tamanho do modelo mais ou menos 2 ~ 4 GB, boa compreensão de texto, a qualidade visual é média chuto bem grosseiro ser alta ok, desempenho tranquilo 4~6 GB (VRAM), compatibilidade dele é enorme e ideal para workflows leves e Loras antigos. SDXL resolução nativa de 1024x1024, tamanho do modelo sendo maior que 8 GB não esquecer da base + refiner, compreensão de texto é excelente, qualidade visual dele é alta para profissional, por esse motivo digo grosseiro o outro conseguir uma alta, acho possível com um bom modelo e uma lora bacana ai no meio, desempenho VRAM 8 a 12 GB aqui sem negociação, compatibilidade dele é nova geração e sendo ideal para qualidade máxima, realismo e projetos modernos.

Como comentei existe vários modelos prontos, várias comunidades online inteiramente dedicadas a treinar modelos, encontrando uma infinidade de modelos prontos para uso, segue 1 bacana que eu usei e encontrei vários modelos que eu queria.

[civitai](https://civitai.com)

Quando baixar um modelo, o arquivo tem que ser colocado no diretório corretamente “models/checkpoints” assim todo workflow vai conseguir carregar ele em “Load Checkpoint”