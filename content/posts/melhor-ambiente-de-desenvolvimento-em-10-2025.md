---
title: "Melhor Ambiente De Desenvolvimento Em 10/2025"
date: 2025-10-02T13:00:25-03:00
lastmod: 2025-10-16T13:00:25-03:00
draft: false
status: "in_progress"
status_label: "> ⚠️ Este artigo está em desenvolvimento. Atualizações serão adicionadas em breve."
---

Eu queria começar a escrever esse assunto mais para frente, pois tinha outras coisas que eu gostaria de colocar antes, mais puta que pariu durante essa semana eu ouvi novamente “Libera um servidor para o dev desenvolver direto lá” sério mesmo? estamos em 2025 e você quer liberar para o seu desenvolvedor trabalhar diretamente no servidor, subindo arquivos via SFTP. WHATTT?

Esse assunto vai ser um pouco longo, pois eu quero fechar esse assunto de uma vez por todas, vamos ACABAR COM ESSA PORRA DE DESENVOLVER DIRETAMENTE NO SERVER, vamos aprender as boas práticas, e olha que vamos falar sobre DESENVOLVER LOCALMENTE, por que uma aplicação real, existe muitas coisas por trás, não é somente subir um server, colocar seu apache, configurar banco e pronto acabou, pensou como escalar isso? O artigo de hoje não é o foco, porém eu vou separar um somente para falar sobre isso.

Olá pessoal tudo bem? Eu espero que sim!

Eu vou escrever nesse artigo um tutorial completo para montar um ambiente bacana de desenvolvimento, a questão aqui não será “Qual o melhor sistema operacional?” ou “Eu somente desenvolvo em Windows”, onde você desenvolve e o que gosta de usar, é problema seu, não vou falar qual sistema operacional é melhor, use da maneira que você preferir, eu em particular, gosto e desenvolvo em Linux, sim tenho um Windows que utilizo, porém faço WSL2 e rodo um Ubuntu nele.

 Eu estou cansado de precisar explicar ou esbarrar com alguém subindo arquivos diretamente via SFTP  e ainda coloca a equipe para desenvolver dessa maneira. Estamos atualmente em 2025 e a equipe não está usando GIT, não tem boas práticas nada nada nada nada, realmente é algo frustrante, o que me deixa mais puto ainda, é quando você pega uma equipe de estagiários e coloca junto com o “MESTRE” onde o mesmo vai gerenciar essa equipe e começa a ensinar da maneira errada, sobe os arquivos ou desenvolve diretamente via SFTP no server, SIM é exatamente isso que você está LENDO AQUI!!! Vou explicar, baixa o arquivo, edita e sobe. Por incrível que aprece eu já vi um “dev” de 10 anos, sim “DEZ ANOS” que atua na área e se diz “DESENVOLVEDOR” da onde eu não sei mais, baixar o arquivo do servidor, editar, e em seguida sobe o arquivo para ver se as mudanças tinham ocorrido, isso chega ser uma tortura infinita, você fica tão incomodado que não sabe o que fazer, nem o que dizer, mais não adianta pegar e reclamar dizendo que a culpa foi do seu mestre, ele ensinou assim e nunca mudou, para meu, se você depender do seu mestre para aprender, você só vai chegar até onde o seu mestre chegou, você precisa evoluir sozinho, aprender a aprender.

Aprenda e seja autodidata, aprenda a aprender coisas novas, esteja atualizado, coloque na sua cabeça, o você de hoje é a sua versão melhor de ontem, ou seja, o cara que eu sou hoje é o meu passado de ontem, que será o novo eu de amanhã, os japoneses têm uma filosofia denominada KAIZEN, que significa melhora contínua “hoje, melhor do que ontem, amanhã, melhor do que hoje!”

Em particular eu uso um ambiente Linux, tenho um ambiente Windows com WSL2 conversa para outro momento, mais o que eu vou te ensinar aqui, você pode aplicar isso em qualquer ambiente, ou seja poderá compartilhar com seu amigo e ambos desenvolver o mesmo projeto sem grandes problemas.

## Windows e WSL2

Como eu disse, eu tenho um Windows rodando Ubuntu com WSL2, sendo uma compatibilidade que roda o Linux dentro do Windows. WSL2 roda uma máquina virtual leve rodando um kernel de Linux real, recursos como memória RAM, GPU, CPU serão compartilhados entre os dois sistemas operacionais, então por isso é mais pesado, não recomendo rodar se tiver menos de 4 CPU e menos de 8GB RAM, vai rodar se tiver menos mais via ficar muuuuuuito lento. Recomendo 8 CPU e 16 GB RAM. Não pergunte se “Aaah minha máquina tem 4 de RAM vai rodar?” Faça a conta, 4 é menor do que 8 recomendado, me diga você Sherlock Homes?

Ele usa o Hyper-V como tecnologia de virtualização,  que permite criar e gerenciar máquinas virtuais em sistemas Windows, funciona virtualizando o hardware para rodar vários sistemas operacionais no mesmo computador físico.

Nessa integração ele vai montar o /mnt/c/ para os arquivos windows e \\wsl$\ para os arquivos do Linux. Tem suporte com o Docker e outras ferramentas, até mesmo o próprio VSCode consegue reconhecer o WSL rodando, sobe uma notificação de uso e etc…

Ou seja em resumo é um kernel de Linux completo rodando em uma VM otimizada que está integrada no Windows.

Não vou estivar muito o assunto, pois se realmente fossemos falar de VMs, WSL2 e etc.. esse artigo ficaria muito longo, mais posso depois escrever sobre o assunto separado.

## Linux

Caso queira replicar um ambiente igual o que estou usando atualmente siga esse tutorial [Omarchy](https://andersonteala.com.br/posts/install-arch-and-omarchy-2-0-in-acer-nitro-v15/).

Atualmente estou utilizando o Omarchy baseado em Arch Linux, ele configura grande parte do que eu uso para meu ambiente de desenvolvimento, e também como comentei  eu tenho em outro notebook o Windows instalado, faço WSL2 utilizando o Ubuntu, como eu disse o sistema operacional que você vai utilizar não interessa tanto faz, vai mudar as coisas nas instalações, mais eu vou ensinar a instalar tudo no Ubuntu e se você estiver em outro sistema operacional, pode replicar isso pegando a documentação oficial e se virar para montar dentro do seu ambiente, lembra do se virar sozinho? bicicleta sem rodinhas? Aprendendo a aprender? Vou dar um caminho bacana e completo no Ubuntu, sendo possível replicar em outro ambiente no caso do Windows.

Se caso tenha seguido o tutorial a cima e instalou o Omarchy, sugiro pular diretamente para a sessão [].

Se você continua lendo a partir daqui, presumo que não instalou o Omarchy e seguiu instalando o Ubuntu diretamente, show de bola vamos configurar o ambiente agora.

## Docker

Sim muito dev não utiliza hoje, e deveria fazer parte do seu ambiente de desenvolvimento, lembra do cara que edita arquivo local, sobe via SFTP e valida se as alterações surtiram efeitos no server? Vamos eliminar essa porra!!!

Docker é uma plataforma que permite criar, distribuir e executar as suas aplicações em containers, basicamente um container é uma unidade leve que empacota uma aplicação com todas as suas dependências, bibliotecas e configurações separadas. Preste atenção isso é totalmente diferente de uma máquina virtual, containers não são máquinas virtuais, por que o container compartilham o kernel do sistema e isola apenas o necessário, e isso torna mais leve e super rápido.

A arquitetura do Docker é simples entenda o Docker Daemon que é o processo que gerencia os containers, imagens e redes. Docker CLI Interface de linha de comando para interagir com o deamon. API REST sendo usada para comunicar entre o cliente e daemon. Temos as images que são modelos imutáveis que servem para base da criação de containers, sendo construídas a partir do Dockerfile. Os próprios containers que são instancias executáveis das imagens docker. Repositório do docker Hub público para compartilhar e baixas as images. Volumes usado para persistência dos dados fora do ciclo de vida do container. Permitem comunicação de redes entre os containers e com o próprio host.

Isso é um básico simples sobre a arquitetura do Docker, caso não entenda de Docker, recomendo pegar qualquer curso para aprender e claro, devorar a documentação deles que é muito boa.

O fluxo do docker é básico e simples, você cria um arquivo Dockerfile descrito como montar a imagem, ele vai construir a imagem e executar um container.

```bash
# CONSTRUIR A IMAGEM
docker build

# EXECUTAR O CONTAINER
docker run minha-imagem

# LISTAR OS CONTAINERS
docker ps

# PARAR UM CONTAINER
docker stop minha-imagem
```