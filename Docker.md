#O que é um Container?
  Uma emulação de sua aplicação.
Os containers proporcionam uma maneira padrão de empacotar código, configurações e dependências de seu aplicativo em um único
objeto. Eles compartilham um sistema operacional instalado no servidor e são executados como processos isolados de recursos.
Isso permite fazer implantações rápidas, confiáveis e consistentes, independentemente do ambiente. Usualmente roda em uma VM.

#O que É Docker?
  Solomon Hykes em 15 de Março de 2013 na Califórnia. Veja o video de lançamento: https://youtu.be/wW9CAH9nSLs
O objetivo era efetuar um gerenciamento mais simples do PaaS (Platform as a Service) da dotCloud, com deploy similar ao Heroku
(inicialmente só para Ruby), utilizando o conceito de contêineres Linux ao invés de máquinas virtuais.Imagine que você tenha 
que transportar milhões de unidades de um novo smartphone da fabrica que está na China até o mercado americano e europeu 
(lojas). Pense que para transportar em navios, depois trens e caminhões, ficar movendo as caixas (uma unidade ou varias) de 
um meio de transporte para o outro, não é uma maneira otimizada e nem segura de se fazer.
Para essa missão a maneira mais segura e rápida seria utilizar contêineres, iniciando na fábrica que ficaria com a missão de
organizar a mercadoria nos contêineres, onde basta um pau de carga ou um guindaste e alteramos o meio de transporte 
(caminhão -> navio -> trem -> caminhão) que agora seguirá viagem para o seu próximo destino. Mudança de meio de transporte
feito de maneira rápida, eficaz, segura e de baixo custo.
  Docker só roda em processadores 64bits e versão do kernel acima da 3.8.
  
#Camada e o Copy-on-write
  File system = São várias camadas sobrespostas para formar uma imagem. Somente na última camada podemos escrever, se quisermos
ler algo da última camada (read only, o Docker sobe para a última camada).
  Copy-on-write = Você vai escrever algo no livro e aparece uma cópia, então você escreve na cópia preservando o original. Quando
  salvo o arquivo não altera o original, joga na camada de cima e faz uma cópia com as alterações.
  
#Internals
    Namespaces = Permite fazer isolamento de determinados componentes, assim cada container tem suas características sem um 
  interferir no outro.
  PID Namespace = Isola os PID (exclusivo por processo) para que o container tenha sua própria árvore (Process Identification). 
  Net Namespace = Isola a rede para que (ITH 0) seja isolada do host.
  (Existem várias outras Namespaces etc) 
    CGroup = Isola e libera recursos para os containers.
    Netfilter = IP tables 
    
#Intalando Docker
  curl -fsSl https://get.docker.com/ | sh - baixando e instalando
  docker --version - verificar a versão
  
#Administrando
  docker run hello-world - (Consultou na base pra ver se existia essa imagem, SE NÂO, foi na internet fez o dowload da imagem (pull)
e start o container.
  docker images - é um container parado.
  docker ps - ver containers em execução
  docker ps -a - ver todos os containers que foram parados ou finalizados.
  
  docker run -ti ubuntu /bin/bash - (-ti) para ter um terminal interativo, (/bin/bash) para ter um shell
  
  docker-compose up --build ou docker-compose up --build --recreate (rodar)
  
  Ctrl + d - mata meu container saindo do shell
  Ctrl + p + q - sai do container e deixa ele rodando.
  
  docker start id_do_container - para subir o container.
  docker attach id_do_container - para entrar no container.
  
  
  docker create nome_do_container - criar um container.
  docker run -ti nome_do_container - executa o container.
  docker stop id_do_container - parar o container. (Dar o comando fora do container).
  docker pause id_do_container - pausar o container.
  docker unpause id_do_container - despausar o container.
  
  docker stats id_do_container - saber os recursos consumidos. (memória, rede e blocos)
  
  docker top id_do_container - informações de procesos
  docker logs id_do_container - informações de log.docker
  
  docker rm id_do_container - remover o container (O container não pode estar em execução).
  docker rm -f id_do_container  - força a remoção do container
  
 
  
  
  
  
  
  
  
  
  
  
