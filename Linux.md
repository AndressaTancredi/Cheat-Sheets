Saber o diretório
pwd

Escreve e guarda essa msg dentro de um novo arquivo
echo "Bem Vindo" > bemvindo.txt

Adcionar num arquivo já existente
echo "Bem Vindo de Novo"  >> bemvindo.txt

Copiar msg de um arquivo para outro
cp bemvindo.txt bemvindo2.txt

Renomear arquivos
mv bemvindo.txt mensagem.txt
pode mudar dir tb
mv bemvindo.txt workspace/mensagem.txt

Ler o que tem no arquivo
cat

Limpar a tela
clear

Mostra arquivos ocultos
ls -a ou ls -la (para ver detalhes tb)

Mostra detalhes dos arquivos no diretório
ls -l

Ajuda
man e a letra q para sair da ajuda

Ver o nome do usuário no Linux
whoami

Ver dir atual
ls .

Ver dir anterior
ls ..

Novo dir
mkdir nomeDoDir

Apagar dir vazio
rmdir nomeDoDir

Apagar dir cheio
rm -r nomeDoDir

Apagar arquivo
rm nomeDoArquivo

Copiar dir
cp -r projetos-java projetos-c#

Compactar dir
zip -r work.zip workspace/
zip (nomeDoArquivo.zip) dir
Ou
tar -cz workspace > work.tar.gz

Descompactar dir
rm -r workspace/
unzip work.zip
Ou
tar -xz < work.tar.gz

Ler todos arquivos txt
cat *.txt
Ou somente as linhas com California cat google.txt | grep California

Houve uma modificação
touch nomeDoArq

Ver primeiras 10 linhas do arq
head nomeDoArq.txt
Ou
head -n 3 nomeDoArq.txt
Ou
tail nomeDoArq.txt ou tail -n 3 nomeDoArq.txt

Entrar no arq
vi nomeDoArq.txt
para inserir algo
i e digita algo
esc para sair da edição
x para remover ou apagar caracteres
:w enter salva
:q enter sai
Ou
:wq enter salva e sai
:q! sai sem salvar
/ nomeDaBusca busca a palavra e n navega nas ocorrencias
p para colar
y copiar Ou 6yy pra copiar 6 linhas


Linux 2

Saber os processos que estão rodando
ps 
OU ps -e (para todos os processos na máquina)
Ou ps -ef (para mais detalhes)
Ou ps -ef | grep firefox (para pegar todos os processos firefox)

Para saber a situação dos processos (memórias...)
top
Ou pstree

Parar um processo
kill numeroDoProcesso
Ou kill -9 numeroDoProcesso (MATA MESMO RS)
Ou killall -9 top (Mata todos os processos com TOP)

Mostrar apenas os processos de um determinado usuário
top -u lucas

Acompanhar as informações de um processo específico
top -p passando como argumento o PID do processo

Parar temporariamente um processo no terminal
Ctrl + z

Ver os processos
jobs

Jogar processo para o background
bg 1 (Fica com o $ depois do nome do processo)

Trazer para o forground
fg 1

Abrir direto no backgorund
firefox &

Para executar um script
sh nomeDoArq
OU ./nomeDoArq

X Execução W Escrita R Leitura
Permissões
chmod +x nomeDorArq (Permitir q o user execute o arq)
chmod -x nomeDorArq (Não permitir q o user execute o arq)

Saber as permissões
ls -l
ls -l /usr (de cada user)

Ver se há dados desatualizados
locale

Atualizar o DB
sudo updatedb

Saber onde o programa está instalado
which nomeDoProg

Mudar a senha do usuario
passwd
Ou passwd root 

Logar como root
su root

Ver quantos usuários tem no sistema
Vai na /home e dá ls

Criar outros usuarios
adduser mariana

Contar o número de palavras, caracteres e linhas que um arquivo possui. Junto com o wc podemos utilizar a opção -w para indicar que desejamos contar apenas o número de palavras que existem no arquivo. O *.txt indica que desejamos realizar a contagem em todos os arquivos .txt do nosso diretório atual.
wc -w *.txt

Se utilizarmos o comando ps -e, que lista todos os processos, podemos passar o retorno do ps para o wc -l contar quantas linhas o retorno possui. A quantidade de linhas representa a quantidade de processos existentes no nosso sistema.
ps -e | wc -l

Atualizar programas
sudo apt-get update

Pesquisar quais programas estão disponíveis para instalação
apt-cache search nomeDoProg

Duas maneiras de instalar um programa no Linux:

    Via apt: quando o programa já está disponibilizado na central de programas do Ubuntu.

    Via dpkg: quando baixamos pelo navegador um pacote do programa com a extensão .deb.


Podemos instalar programas que não estão disponibilizados na central de programas do Ubuntu, ou seja, sem o uso do apt. Para isso nós baixamos um pacote desse programa em um site e depois o instalamos. O formato desse pacote é dpkg, que é um arquivo com a extensão .deb.
amos instalar novamente o servidor de FTP, porém, usando o pacote .deb. Procuramos na internet e baixamos via navegador o vsftpd no endereço: http://ftp.br.debian.org/debian/pool/main/v/vsftpd/vsftpd_3.0.2-17+deb8u1_i386.deb. Ele estará salvo no diretório de Downloads. Para instalar entramos nesse diretório com o comando cd e utilizando o comando dpkg fazemos:
sudo dpkg -i vsftpd_3.0.2-17+deb8u1_i386.deb
O -i indica que estamos instalando o programa. 

Desinstalar um programa pelo dpkg
sudo dpkg -r nomeDoPacote

É possível que um programa não esteja disponível em nenhuma das duas formas (APT-GET ou DPKG). Nesse caso vamos ter que baixar seu código fonte, compilá-lo e instalá-lo. 

Acessar um servidor remoto no Linux. Para isso, teremos que fazer uma comunicação com o outro servidor. Já vimos o FTP, mas o FTP é para troca de arquivos. O que queremos é nos logar como um usuário. Para isso iremos usar o SSH. O primeiro passo é instalá-lo:
sudo apt-get install ssh
Desta forma instala-se tanto o cliente SSH (ssh-client), quando o servidor (ssh-server). Para testarmos se o programa instalou corretamente, logaremos na nossa própria máquina utilizando o comando ssh, fornecendo o nome de um usuário já criado anteriormente e o ip da máquina(localhost)
ssh jose@localhost
Poderemos executar uma série de comandos, porém não temos acesso às ferramentas e programas gráficos. Não podemos, por exemplo, abrir um navegador.
Para termos essa permissão, precisamos nos conectar usando um modificador que permita o uso de ferramentas gráficas. O -X é esse modificador:
ssh -X jose@localhost
Para encerrar a conexão, usamos o comando exit
Lembrando que tudo o que estamos fazendo está sendo executado lá no servidor e não em nossa máquina. Somente o gráfico é mostrado em nossa máquina, as ações são todas remotas.
Agora vamos ver como copiar um arquivo da nossa máquina local para a máquina remota. Fazemos por meio do comando scp, indicando para ele qual é o arquivo e qual é o destino do arquivo:
scp work.zip jose@localhost:/home/jose
/home/jose é a home do usuário jose e pode ser substituído por "~":
scp work.zip jose@localhost:~/
Com isso jogamos o arquivo work.zip no nosso servidor remoto. Se o buscarmos dentro da outra máquina, nos conectando novamente com o ssh e listarmos os arquivos com o comando ls iremos perceber que realmente ele foi copiado.
Agora nós iremos transferir um arquivo para uma máquina remota utilizando o comando scp.
Você pode escolher um arquivo de sua preferência para transferir. Caso queira, pode transferir o diretório workspace, criado anteriormente, ou o diretório scripts (não se esqueça de utilizar a opção -r caso escolha transferir um diretório). Para transferir um arquivo, vamos compactar um dos diretórios (lembre-se de alterar o nome do diretório caso seja necessário):
$ zip -r work.zip workspace/
Utilize o comando scp para copiar o arquivo para a pasta do usuário jose, que é um usuário de sua máquina. Se logue com o usuário jose e verifique se o arquivo foi copiado.
