* Baixa e instala o Docker

  `curl -fsSl https://get.docker.com/ | sh`
  
* Verifica a versão
 
   `docker --version`
  
* Testa (Consultou na base pra ver se existia essa imagem, SE NÂO, foi na internet fez o dowload da imagem (pull))
  
  `docker run hello-world`
  
* Vê container parado

  `docker images`
  
* Vê containers em execução

  `docker ps`
  
* Vê todos os containers que foram parados ou finalizados

  `docker ps -a`
  
*  Abre terminal (-ti) para ter um terminal interative e (/bin/bash) para ter um shell)

  `docker run -ti ubuntu /bin/bash`
  
* Roda o container

  `docker-compose up --build` ou `docker-compose up --build --recreate`
  
* Mata o container saindo do shell
  
  `Ctrl + d`
  
* Sai do container e deixa ele rodando
  
  `Ctrl + p + q`
  
* Sobe o container

  `docker start id_do_container`
  
* Entra no container

  `docker attach id_do_container`
  
* Cria um container

  `docker create nome_do_container`
  
* Executa o container

  `docker run -ti nome_do_container`
  
* Para o container (Dar o comando fora do container)

  `docker stop id_do_container`
  
* Pausa o container

  `docker pause id_do_container`
  
* Despausa o container

  `docker unpause id_do_container` 
  
* Consulta os recursos consumidos (memória, rede e blocos)

  `docker stats id_do_container`
  
* Informa os procesos

  `docker top id_do_container`
  
* Informa o log.docker

  `docker logs id_do_container`
  
* Remove o container (O container não pode estar em execução)

  `docker rm id_do_container`
  
* Força a remoção do container

  `docker rm -f id_do_container`
  
* Roda o Rubocop dentro do container 

  `docker-compose run app rubocop caminhoDoArquivoRb`
 
* Roda console rails

  `docker-compose run app rails c`

* Roda bash

  `docker-compose run app bash`
  
  ## O que é um Container?
  Uma emulação de sua aplicação.
Os containers proporcionam uma maneira padrão de empacotar código, configurações e dependências de seu aplicativo em um único objeto. Eles compartilham um sistema operacional instalado no servidor e são executados como processos isolados de recursos. Isso permite fazer implantações rápidas, confiáveis e consistentes, independentemente do ambiente. Usualmente roda em uma VM.

  ## O que É Docker?
  Solomon Hykes em 15 de Março de 2013 na Califórnia. Veja o video de lançamento: https://youtu.be/wW9CAH9nSLs
O objetivo era efetuar um gerenciamento mais simples do PaaS (Platform as a Service) da dotCloud, com deploy similar ao Heroku (inicialmente só para Ruby), utilizando o conceito de contêineres Linux ao invés de máquinas virtuais.Imagine que você tenha que transportar milhões de unidades de um novo smartphone da fabrica que está na China até o mercado americano e europeu (lojas). Pense que para transportar em navios, depois trens e caminhões, ficar movendo as caixas (uma unidade ou varias) de um meio de transporte para o outro, não é uma maneira otimizada e nem segura de se fazer.
Para essa missão a maneira mais segura e rápida seria utilizar contêineres, iniciando na fábrica que ficaria com a missão de organizar a mercadoria nos contêineres, onde basta um pau de carga ou um guindaste e alteramos o meio de transporte (caminhão -> navio -> trem -> caminhão) que agora seguirá viagem para o seu próximo destino. Mudança de meio de transporte feito de maneira rápida, eficaz, segura e de baixo custo. Docker só roda em processadores 64bits e versão do kernel acima da 3.8.

