---
title: "Montando meu novo ambiente Arch com Omarchy 2.0 / Acer Nitro V15"
date: 2025-08-31T21:31:09+00:00
# weight: 4998
# aliases: ["/first"]
tags: ["arch", "linux", "omarchy", "acer", "nitro", "v15"]
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

## Montando meu novo ambiente Arch com Omarchy 2.0 / Acer Nitro V15

Fiz um upgrade no meu setup, e troquei meu Notebook, eu precisava de um para conseguir desenvolver mais tranquilamente, uso para o dia a dia e de vez em quando jogar, porém não sou muito de jogar em Notebook, prefiro jogar em console, de vez em quando jogo alguns como por exemplo um lolzinho.

Começei a fazer várias buscas pela internet por alguns meses, até que encontrei finalmente depois de tempos e tempos buscando, eu não tenho pressa, gosto de procurar, pesquisar e entender antes de realizar qualquer compra, mesmo que dure meses, eu vou esperar para não comprar no desespero e me fuder lá na frente.

# 1 - Notebook e novo ambiente

Depois de longas pesquisar e frescuras, decidi então comprar um Notebook Gamer Acer Nitro V, Intel Core i5-13ªGen, 8GB, SSD 512GB, RTX4050, Tela 15.6" Full HD, 144Hz. Ainda vou fazer um post falando sobre minhas expectativas e frustrações com o Notebook. Logo de cara decidi fazer um upgrade de memória RAM e coloquei mais um SSD de 1TB.

Comprei uma memória RAM de 16GB (**Memória RAM para Notebook Kingston Fury Impact, 16GB, 5600MHz, DDR5, CL40, Preto - KF556S40IB-16**) que ainda não chegou e vai totalizar 24GB para mim ficou perfeito pois eu programava em um com 16GB de RAM.

Sim a memória que eu comprei é de **5600MHz** porém o Notebook vai usar somente até **5200MHz**, então foda-se.

Enfim, comprei o Notebook chegou fiz os primeiros passo a passo do Windows, eu não curto muito Windows para desenvolver, comecei e aprendi direto no Linux, tudo o que eu quero fazer tenho minhas frescuras e facilidades com o Linux, desenvolvendo em 6 anos diretos em um Ubuntu, e usando Windows apenas para jogar.

Depois que realizei infinitos passos para configurar, realizei as configurações de drivers download e pronto, não fiz mais nada, não instalei mais porra nenhuma, e fiquei louco para montar meu ambiente de desenvolvimento pois eu quero testar essa RTX 4050.

Baixei o Ubuntu normalmente, usei o rufus para montar o meu pendrive bootável e ai quando eu fui instalar o Ubuntu minha cabeça como sempre falou pra mim: **“Cara, durante 6 anos diretos você desenvolveu utilizando o Ubuntu, por que não passa a usar um diferente, por que não usar um Arch?”** Pronto, isso bastou para eu travar minhas instalação do Ubuntu e partir em busca de instalar um Arch.

Eu já usei um pouco o Arch nos meus estudos, para instalar ele hoje é realmente um pouco complicado, mais para quem é iniciante pode se frustrar a primeira vez, porém nunca deve deixar isso tomar conta é aquela velha história que ensino para o meu filho, não conseguiu? Ok agradeça e tente novamente.

Eu sei que hoje em dia tem o **archinstall** que ajuda muito na instalação, mais eu recomendo usar o passo a passo do Arch para instalar do absoluto zero pelo menos uma vez na vida.

Decidi! vou instalar o **Arch** e sair um pouco da caixinha, eu gosto, é bom sair da zona de conforto, quando percebo que estou muito confortável com algo, eu começo a fazer mudanças para não entrar nessa rotina. Logo em seguida eu vi que muitos usando o Arch com Hyprland, porra adorei quando eu vi isso, deixando o desktop muito moderno e de uma maneira que eu curti muito, quando pesquisei  sobre o Hyprland , vi que um desenvolvedor que eu sigo tinha acabado de fazer uma postagem sobre o assunto e ai ganhei na loteria.

# 2 - Upgrade no Notebook

Como eu comprei a memória RAM e ainda não chegou coloquei somente o SDD no Notebook inicialmente, assim que chegar a memória eu faço um edit: e coloco ela.

Sempre recomendo SEMPRE, use proteção, tenho a pulseira e luvas antiestáticas muita gente acha besteira, tudo bem siga sua maneira de viver, eu prefiro não arriscar e danificar parcialmente peças do Notebook, porém eu sempre recomendo usar proteção, é como camisinha, se não usar uma hora vai dar MERDA, comprei uma bem simples foram incríveis R$ 30,00 lules que uso sempre que necessário.

Abri o Notebook com maior cuidado, desativei a bateria, coloquei o SSD, conectei a bateria, fechei o Notebook, e para minha surpresa vem aquele mini infarto que sentimos ao fazer isso, ligo e a porra do Notebook não ligou.

Claro fiquei preocupado pois havia acabado de chegar, não testei nem um game nele, mais beleza abri os parafusos novamente maior trampo da porra, tirei bateria, tirei o SSD e apertei o botão POWER para eliminar as energias etc.. coloquei o SSD novamente, conectei a bateria, coloquei a tampa do Notebook, mais dessa vez não coloquei os malditos parafusos infernais, assim que liguei, pronto o miserável ligou, fiquei feliz novamente e coloquei a porra dos parafusos kkkkkkkk.

Nesse SSD eu usava em outro Notebook, então eu tinha um Ubuntu instalado nele, nesse momento entrei no Ubuntu, vi minhas coisas que estavam lá, pois eu havia feito Backup de tudo, e pensei porra acho que vou usar o Ubuntu, novamente minha cabeça me disse **“Cara, lembra da zona de conforto, vamos sair dela, não compensa, vamos mudar isso”**.

Decido novamente vou apagar o Ubuntu e instalar o Arch + Omarchy.

# 3 - Instalando Omarchy

Aqui! todos dizem que instalar um Arch é a coisa mais complicado do mundo, concordo e discordo, é complicado para quem ainda é um iniciante e nunca mexeu em um Linux, mais nunca deve deixar de tentar pelo menos uma vez, como comentei mais a cima, atualmente temos o archinstall que facilita muito a instalação.

Mesmo assim eu decidi baixar a iso do Omarchy primeiro e testar a instalação direta nela. Primeiro de cara não gostei de instalar com a iso do Omarchy, pois ela não permitiu eu fazer o particionamento do disco, eu sei que teria outras maneira mais estava contando com essa parte da instalação.

Primeiro toda vez que estava realizando o download dos pacotes, começava a ficar lento e não conseguia concluir e não tentava novamente apenas dava erro e solicitava para instalar novamente, sim eu estava utilizando pelo Wi-Fi, decidi diversas vezes deixar pra lá e instalar o Arch primeiro, mais eu pensei porra que sacanagem vamos instalar isso de qualquer maneira agora.

Passei algumas horas pesquisando e olhando o forum e não encontrei ninguém que estava com a mesma situação, pensei que poderia até ser um problema na minha placa de rede pois tinha acabado de comprar o Notebook, mais creio que não pois eu estava utilizando o Windows com ele antes e não tive problemas, pois eu gosto sempre de testar tudo antes para garantir que não tem problema e assim solicitar a troca dentro dos 7 dias na lei, caso contrário eles não trocam e enviam para a assistência técnica um Notebook novo que você acabou de comprar em poucos dias. Bem vindo ao Bostil.

Bom, seguindo firme, montei o pendrive novamente para garantir que não corrompeu, mesmo assim não dava certo com o WiFi, refiz esse processo umas 3 vezes, por algum motivo ele tem algum bug que quando a internet oscila ele para e não tenta novamente, e apenas da erro, mais eu não quis perder tempo com isso, então precisei levantar deixar a preguiça, pegar um cabo, enfiei no Notebook e bora lá novamente, e para a minha surpresa deu certo.

Deixei instalar somente para testar e show de bola deu certo, de cara Omarchy instalado, fiz alguns testes, e adorei muito bom era realmente o que eu buscava para sair da minha zona de conforto.

## 3.1 - O que o Omarchy tem de bacana?
O Omarchy é uma camada personalizada em cima do Arch Linux, no sentido de **"Arch Way"**, que é possível agilizar a instalação e configuração do sistema, com isso sendo simples, e controle total que adiciona conveniência e praticidade.

Ele vai automatizar o processo de instalação inicial do Arch, o problema é somente aquele que comentei, não consegui particionar o disco com o instalador dele.

Traz uma base organizada de pacotes, dotfiles e ajustes que deixa o sistema bem bacana e funcional.

O mais bacana é que ele inclui pacotes para desenvolvimento e produtividade, sem aquelas porcarias de outras distros que se dizem **"prontas"**.

Fácil para personalizar, permite alterar e ajustar tudo que necessário, o céu é o limite aqui.

# 4 - Instalando Arch + Omarchy

Agora voltei para o windows e busquei a iso do Arch para fazer um pendrive boot e começar o processo tudo novamente. Eu gosto muito de usar o Rufus, ele é meu parceiro para fazer os pendrive boot, eu já usei o Balena Etcher para fazer alguns com o MacOS.

Utilizei no Rufus a seguinte maneira:

- **Dispositivo**: Selecionei o meu pendrive (Usei um de 64 GB) recomendo de 8GB.
- **Selecionar boot**: Escolhi a ISO do Arch.
- **Esquema de partição**: **GPT**.
- **Sistema de destino**: **UEFI (não CSM)**.
- **Sistema de arquivos**: **FAT32**.
- **Iniciar:** Perguntou sobre a gravação, escolhi **DD mode**.

Pendrive pronto, agora feliz da vida vou eu começar a instalar meu Arch, padrão reiniciei o Notebook, F12 (meu caso), escolhi o pendrive e abriu o terminal para instalar o Arch.

Aqui é o seguinte estava na mesa do lado do meu roteador WiFi, preguiça da porra de pegar um cabo e conectar no Notebook (Já era outro dia do anterior que fiz a instalação do Omarchy, então eu já havia guardado o outro cabo), sim seria a melhor maneira, download mais rápido etc.. mais não, preferi conectar o WiFi, como estamos somente com um terminal, linha de comando na nossa frente, precisei conectar o Wi-Fi da seguinte maneira. Siga meu passo a passo que não terá erro:

**1** - Você vai acessar o gerenciamento de rede sem fio com o comando:

```bash
iwctl
```

**2** - Feito isso, vamos listar os dispositivos Wi-Fi:

```bash
device list
```

**3** - Agora você vai usar o device que listou a cima e escanear as redes Wi-Fi disponíveis:

```bash
station <device> scan
```

**4** - Liste agora as redes disponíveis SSID digite:

```bash
station <device> get-networks
```

**5** - Pronto, agora somente precisa conectar a rede:

```bash
station <device> connect <SSID>
```

**6** - Aqui você pode verificar a conexão com a rede:

```bash
station <device> show
```

Feito tudo isso, agora você acha que acabou? Calma pequeno gafanhoto, ainda tem mais vamos lá.

Você está conectado na rede, porém agora precisa atribuir um endereço de IP, vamos usar um DHCP (Dynamic Host Configuration Protocol) e obter um automaticamente. Mais antes precisamos sair do gerenciamento de rede, pois nele iremos atribuir o IP e realizar um ping para validar.

**1** - Agora faça o seguinte para sair do gerenciamento de rede:

```bash
exit
```

**2** - Feito isso, obtenha um endereço de IP:

```bash
dhcpcd
```

**3** - Teste a conexão com a internet:

```bash
ping google.com
```

Agora você vai receber respostas da conexão ativa, e pronto estamos conectados e pronto para continuar.

Como eu já havia realizado backup do que eu realmente queria, e também estava com o Omarchy instalado no SSD, não ligo de apagar 100%, mais não esqueça de fazer backup pois agora iremos apagar 100% do disco.

No terminal digite:

```bash
archinstall
```

Pronto, vai abrir um menu no terminal para seguirmos, vou listar o que eu fiz pois pra mim funcionou e isso não quer dizer que vai funcionar para você, caso queira faça assim:

- **Language/Locale**: en_US (como preferir ou pt_BR).
- **Mirrors**: Brazil + United States (costuma ser mais rápido).
- **Kernel**: linux (padrão) ou linux-zen (opcional).
- **Bootloader**: GRUB (Vou explicar daqui a pouco o motivo, principalmente por causa do Btrfs que vou escolher daqui a pouco).
- **Profile**: Desktop → Hyprland ou “Minimal” (Aqui realmente não importa por o Omarchy vai embelezar e configurar pra gente depois)
- **Network**: NetworkManager.
- **Usuário**: crie seu usuário e senha, defina senha do root.

Agora sim chegamos onde eu realmente queria e não encontrei no instalador do Omarchy, vamos particionar o disco aqui, muito cuidado caso tenha mais de um instalado na sua máquina, eu vou apenas usar o meu NVMe de 1 TB, o meu SSD que já estava no Notebook com o WIndows vai ficar intacto, não vou mexer nele. Então CUIDADO tenha máxima atenção aqui caso não queria perder nada e formatar o disco errado, se formatar e não tiver backup infelizmente você se fudeo!

Escolhi o customizado e coloquei da seguinte maneira (Isso pra mim Ok, caso queira pode usar o recomendado)

- **450GiB** → btrfs (Daqui a pouco explico sobre o motivo)
- **3GiB** → swap
- **1GiB** → fat32
- Restante deixe free para formatar no Windows  (ele adota sem frescura a partição formatada por ele mesmo) eu vou utilizar como storage para jogos e lixos de downloads.

Pronto, aqui sigo e coloco para instalar. Mais como sempre a vida nunca é bela o bastante sempre pode nos surpreender, começo a ter diversos problemas.

Por algum fucking motivo não estava instalando o Arch, no meio do processo causava um erro, já era mais de 1 da manhã, eu estava cansado demais não queria mais perder tempo com isso, instalar o Omarchy direto, me fez perder um bom tempo com a questão do Wi-Fi, decidi refazer meu pendrive novamente e depois de diversas tentativas, sim eu refiz o processo todo novamente algumas vezes, sendo eles: conectar Wi-Fi, configurar partições, mirros, etc...

Tá aqui te juro, eu estava muito cansado, mais decidi entender o motivo do problema, eu estava montando o disco do tipo Btrfs somente com o mountopoint: (/) percebi que isso estava causando um problema, e não conseguia montar o disco, finalizava a instalação e aparecia o erro com a mensagem:

[COLOCAR A FOTO DO ERRO]

Tentei usar o pendrive novamente para arrumar isso, mais percebi que reparar seria muito custoso, estava quebrado de tentas tentativas e erros, mais não abandonei a situação.

Beleza vamos lá novamente, depois de tentar diversas vezes e nada, fui atrás e vi que o correto seria subs dentro do Btrfs, novamente refiz todo o processo e coloquei o seguinte:

@ /

@home /home

@log /var/log

@pkg /var/cache/pacman/pkg

Cansado para um caralho, deu certo, arch instalado finalmente!!! Aaaaaaaaaaaaahh!!!

Lembrando eu escolhi o profile do Hyprland, ou seja se você também escolheu, não fique preocupado, aqui verá que ele realmente é cru, não tem nada é virgem, mais não se preocupe vamos configurar e embelezar.

Antes atualize o sistema não esqueça pois eu esqueci e tive alguns problemas pois não encontrava os pacotes necessários para realizar o download, pois o Omarchy usa o pacman para instalar vários pacotes de uma vez, e eu estava usando um mirror ruim, e ainda pacotes não tinham então atualizei o meu:

```bash
sudo pacman -Syyu
```

Cuidado, o Arch quebra facilmente quando instala pacotes com o mirror ruim, por esse motivo utilize backups, falo sobre daqui a pouco.

Agora somente faça isso no seu terminal:

```bash
curl -fsSL https://omarchy.org/install | bash
```

Pronto, somente seguir as instruções e deixar ele fazer o restante. Aqui acabou temos o Omarchy instalado e pronto para uso.

# 4 - Omarchy instalado e configurando

Eu acostumado a usar o Ubuntu, aqui foi realmente sair fora da caixinha, em quanto escrevo esse artigo, estou usando o meu Arch Linux + Omarchy, e realmente foi uma escolha nota 10.

Como ele usa o Hyprland é totalmente customizado, sendo possível editar o que quisermos diretamente em ~/.config/hypr.

Percebi que ele deixou pronto 90% da maneira que eu gosto de usar, sim não é puxando saco, mais ele realmente vem completo, docker, git e etc…

Primeiro eu ajustei a minha tela eu tenho 1 monitor somente. Para configurar isso no Hyprland é editando arquivos mais podemos facilitar esse processo, sendo assim somente precisa instalar com o comando:

```bash
yay -S nwg-displays
```

Instalei o vscode pelo AUR

```bash
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
yay -S visual-studio-code-bin
```

Vai instalar o AUR com yay e depois o VS Code

Você vai perceber que está sem som, mais fique tranquilo apenas atualize os drivers:

```bash
sudo pacman -S sof-firmware
```

Depois reinicie o sistema

Adoro e sempre recomendo utilizar o asdf, para conseguir gerenciar versões de linguagens no mesmo sistema de forma unificada, ele resolve problemas que um projeto utilizar PHP 7.4, outro PHP 8.2, com isso pose utilizar as duas versões no sistema, sendo uma global ou pode utilizar a versão na pasta do projeto, lindo e maravilhoso, vou explicar um exemplo como você pode fazer com ele. Sendo assim você pode gerenciar várias linguagens no mesmo lugar, você pode ter Node, Python, Go, PHP, Java, Elixir, Rust, etc…. tudo sob controle do asdf.

Ele cria arquivos .tool-versions, em cada projeto, você pode salvar quais versões usar, e quem clonar o repositório pode simplesmente rodar asdf install para ter o mesmo ambiente.

Primeiro vamos instalar o asdf:

```bash
yay -S asdf-vm
```

Exemplo para instalar nodejs:

```bash
# instalar plugin para Node.js
asdf plugin-add nodejs

# instalar Node.js 20
asdf install nodejs 20.5.1

# usar globalmente
asdf global nodejs 20.5.1

# checar versão em uso
node -v
```

Exemplo: Node 18 para um projeto e Node 20 global ou para outro local.

```bash
asdf global nodejs 20.5.1   # Define versão global
asdf local nodejs 18.17.1   # Define versão só para o projeto
```

Como pode ver o asdf é como um "gerente de RH" das suas linguagens e ferramentas, mantendo várias versões organizadas e fáceis de trocar.

Como de costume, instalei o zsh e defini como padrão:

```bash
sudo pacman -S zsh
```

Agora instalei o Oh My Zsh, é um framework para gerenciar as configurações do zsh:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Depois instalei 2 plugins que eu uso muito:

Zsh-syntax-highlighting: Adiciona um destaque de sintaxe em quanto você digita no terminal, ou seja ele vai destacar comandos válidos como verdes, comandos inválidos vermelho e strings, opções de paths ficam coloridos.

```bash
# Zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Zsh-autosuggestions: mostra sugestões de comandos com base no seu histórico, em quanto você digita aparece cinza claro e o restante do comando sugerido, se a sugestão acertar pastar apertar tab para aceitar, ajuda muito a reconomizar tempo repetindo comandos que você usa com frequência.

```bash
# Zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Depois de instalado apenas edita o arquivo:

```bash
nano ~/.zshrc
```

Procure a linha de plugins e adicione:

```bash
plugins=(
...
zsh-syntax-highlighting
zsh-autosuggestions
)
```

Recomendo usar também o Atuin, muito bom para realizar backup do seu histórico de comandos utilizados até hoje, caso você utiliza mais de um ambiente de desenvolvimento como é o meu caso: https://atuin.sh/

Bem simples para usar recomendo ver a documentação e seguir no site oficial deles, veja um exemplo como é simples a configuração:

```bash
bash <(curl --proto '=https' --tlsv1.2 -sSf https://setup.atuin.sh)

atuin register -u <USERNAME> -e <EMAIL>
atuin import auto
atuin sync
```

# 5 - Por que escolhi instalar meu Arch Linux com Btrfs e usar o GRUB como bootloader

Lembra quando comentei no particionamento sobre o Btrfs e Bootloader usar o GRUB, bom agora vou te explicar o motivo.

O Btrfs é um sistema de arquivos modeno, cheio de recursos que trazem muitas vantagens para quem gosta de ter o controle com o Linux, o principal motivo é pelos Snapshots, ele permite criar Snapshots (cópias instantâneas do estado do sistema de arquivos), pois o Arch pode acabar quebrando como comentei mais a cima na instalação, então isso é extremamente útil quando preciso voltar no tempo e fico tranquilo para realizar testes, atualizações e recuperar falhas.

Lembra do meu problema na instalação? Foda… então ele realmente precisa criar subvolumes para particionar o disco rigidamente, eu criei os subvolumes como necessário, isso ajuda a organizar os snapshots do sistema.

Com o Btrfs temos a verificação de checksums, garantindo que os arquivos não sejam corrompidos silenciosamente.

Agora a melhor parte pelo motivo que escolhi ele é que os snapshots são feitos de forma “copy-on-write”, significa que eles não ocupam espaço extra no disco, até que algum arquivo seja modificado.

O Timeshift será nosso amigo aqui, pois funciona como um ponto de restauração do sistema, aproveitando o poder dos snapshots do Btrfs. Podemos criar snapshots automáticos no sistema até mesmo antes de atualizar. Restaurar um estado anterior em caso de falhas, e sim se atualmente você não utiliza backup você vai se fuder um dia, é igual camisinha, não quer usar? uma hora vai dar merda.

O GRUB, é classico né, nada relevante com ele, mais com ele conseguimos no momento do boot, escolher no menu o Timeshift, ou seja posso configurar o GRUB para listar e inicializar diretamente os snapshots Btrfs que foram feitos.

È bem simples para usar, não tem segredo, vou deixar um print aqui para as configurações que eu escolhi no meu, escolha as suas conforme combina melhor.

Lembrando que esses snapshots ainda estão local, então ainda não estão seguros, mesmo assim compre um HD Externo (Compre de um lugar com referencia e nome, não compre de um china qualquer)

Vamos iniciar a configuração então abra o Timeshift com o comando:

```bash
sudo -E timeshift-gtk
```

- **Tipo**: selecione **Btrfs**.
- **Local do snapshot**: a mesma partição Btrfs do `/` (ele identifica).
- **Agendamento**: Eu coloquei da maneira que funciona pra mim, escolha a sua.
- **Usuários**: Por padrão o Timeshift NÂO INCLUI seus arquivos pessoais ele é focado no **sistema**. Mais eu vou incluir a Home isso é opcional e lembre que restaurar também pode **voltar arquivos pessoais** para versões antigas.

Segue um CLI para validar/criar/deletar seu snapshots:

```bash
# listar snapshots
sudo timeshift --list

# criar snapshot sob demanda (tag O=On-demand; D=Daily; etc.)
sudo timeshift --create --comments "test snapshot"

# restaurar (interativo)
sudo timeshift --restore

# deletar um snapshot específico
sudo timeshift --delete --snapshot "2025-08-31_12-00-00"

# apagar todos (cuidado!)
sudo timeshift --delete-all

```

Verifique se o cron está rodando, caso não ative:

```bash
# verifique se está rodando
systemctl status cronie

# ative o cronie caso não esteja
systemctl start cronie
```

Pronto, agora você já pode criar seu primeiro snapshot com seu Arch Linux + Omarchy configurado:

```bash
sudo timeshift --create --comments "first snapshot"
```

Verifique se foi criado:

```bash
sudo timeshift --list
```

Vou fornecer algumas dicas que eu já tive problemas no passado com o timeshit, se assim como eu você utiliza docker nos seus projetos, quando iniciamos um container, ou aquele maldito docker compose up, ele vai baixar diversas imagens e criar logs dos estados, então olha só que maravilha se você hoje tem 1GB de imagens docker, e amanhã 5GB, sim é o que você pensou, vai ser contado no seus snapshots, então vamos remover isso.

Faça o comando:

```bash
sudo chattr +C /var/lib/docker
```

Isso vai eliminar os arquivos do docker, e toda aquela porcaria de imagens etc.. dos seus snapshots pois isso não é necessário.

Também recomendo eliminar os arquivos de logs:

```bash
sudo chattr +C /var/log
```

Apenas uma dica já que estamos falando de docker, as vezes é sempre bom limpar um pouco os arquivos de docker da sua máquina, mais cuidado ele realmente vai limpar e apagar tudo, imagens etc… recomendo fazer isso de vez em quando:

```bash
# Limpa tudo
docker system prune

# Remove imagens etc...
docker compose down —rmi all
```

De tempos em tempos caso você limpe os seus snapshots, vai perceber que o timeshift ainda reservou aquele espaço, vamos dar um exemplo que você vacilou e não removeu o docker e os logs, seus snapshots foi a cada dia mais crescendo e você começou a ter erros para escrever no disco pois ele ficou lotado, sim isso pode acontecer e tem uma saída, se você fizer:

```bash
sudo Btrfs filesystem df /
```

Vai ver a quantidade em uso, sendo assim você vai no timeshift e exclui a metade dos logs, e não vê espaço liberado, novamente faz o comando:

```bash
sudo Btrfs filesystem df /
```

Percebe que nada mudou, é como se nada tivesse acontecido, isso por que o timeshift deixa aquele espaço reservado, mais para isso, precisamos fazer um comando que demora um pouco dependendo do tamanho, faça o comando e vai tomar um café:

```bash
sudo Btrfs filesystem balance start /
```

Após isso percebe que liberou espaço e novamente realizando o comando vai ver que o espaço mudou:

```bash
sudo Btrfs filesystem df /
```

Por fim e por ultimo eu instalei o Keepass para gerenciamento de senhas, vou escrever depois sobre os motivos pelos quais você nunca deve utilizar a mesma senha para tudo, mais um breve resumo sobre o assunto, nossas senhas precisam se manter seguras, isso é fundamental, é o básico, muito cometem o erro de utilizar a mesma senha para várias contas ou anotar as senhas no drive do e-mail, burrice total.

Bom aqui entra o Keepass, existem outros muito bom também, até mesmo 1Password que é pago, grandes empresas usam e tem nome, até mesmo eles não tem acesso aos dados, o Keepass gerencia as senhas é confiável e eficiente.

Ele utiliza criptografia (AES e Twofish) para proteger o seu banco de dados e as senhas nele, mesmo que alguém consiga acesso ao arquivo do Keepass, sem a senha mestre, suas informações estão praticamente inacessíveis.

Ele tem código aberto pode validar se existe falhas de seguranças ou backdoors, existe uma camada extra de confiança em comparação a outros.

O armazenamento para gerenciar as senhas não é na nuvem, e sim ele salva tudo localmente no seu computador, pendrive, algum serviço de nuvem da sua escolha e etc…

Você pode usar ele em diversas plataformas como Windows, Linux macOS e até mesmo no seu celular que você anota as senhas em um grupo seu do WhatsApp.

Vamos instalar o maldito:

```bash
sudo pacman -S keepassxc
```

E pronto, só abrir e configurar, seja feliz.

# Conclusão

Esse jornada foi longa, muita coisa eu precisei parar, buscar e entender como os erros que tive na instalação. Não precisei configurar quase nada pois o Omarchy deixou quase tudo pronto pra mim, apenas fiz algumas alterações para deixar meu ambiente mais confortável o possível para usar, e sim ficou perfeito.

De cara pensei que era loucura sair do meu Ubuntu para essa mudança totalmente radical, mais como eu disse eu gosto de sair da caixinha, gosto de sair da zona de conforto, isso é bom pois se você utiliza esse modelo na sua vida, verá grandes novidades. O problema é nossos melhores amigos, eles que nos mantém de pé, pois se você gosta de resolver problema, por trás de cada problema existe uma oportunidade te esperando.

Passei meu domingo inteiro utilizando essa nova configuração, estou escrevendo este post a partir do meu novo ambiente.

Sim recomendo 100% você trocar seu ambiente e sair da caixinha como eu fiz.

Obrigado pelo seu tempo, espero de coração que novos caminhos se abram a sua frente, que o vento sopre levemente na suas costas, que o sol brilhe suave e morno no seu rosto, que a chuva caia de mansinho em seus campos, e, até que nos encontremos, de novo… Que Deus lhe guarde nas palmas de suas mãos!