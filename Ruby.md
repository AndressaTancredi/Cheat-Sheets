## Migration

Recurso do framework Rails para escrever o código no banco de dados usando Ruby ao invés de SQL. São classes que estendem de ActiveRecord::Migration, devem estar no db/migration e podem ser geradas automaticamente usando:
`rails generate migration NomeDaMigration`

Rodar Migration para atualizar seu Schema e deixa-lo pareado com o banco de dados geral.

  `docker ps` (Pegar o ID do Container)
  
  `docker exec -it IDdoContainer bash`
  
  `bin/rake db:migrate RAILS_ENV=test`
  
  (No git status vai mostrar o schema com modificações, dar um checkout nele e já era!)
  
  Gerenciar conflitos: Ir para a branch e dar:
  
    `bin/rake db:rollback RAILS_ENV=test` `bin/rake db:rollback RAILS_ENV=development`
    
    `bin/rake db:migration RAILS_ENV=test` `bin/rake db:migration RAILS_ENV=development`
  
  `git merge staging`
  
  `git add .`
  
  `git commit -m "Merge with master"`
  
  `git push origin NomeDaBranch`
  
Rodar Migration para criar campos no Schema:

Cria a classe:

  
Referências: 

1- https://www.devmedia.com.br/introducao-a-migrations-no-ruby-on-rails/33820

2- https://guides.rubyonrails.org/v3.2/migrations.html

## YAML

Um padrão de serialização de dados amigável para qualquer linguagem de programação. Usado para arquivos de configuração.

“ O YAML foi criado especificamente para funcionar bem em casos de uso comum, como: arquivos de configuração, arquivos 
de log, mensagens entre processos, compartilhamento de dados entre linguagens, persistência de objetos e depuração de estruturas de dados complexas. Quando os dados são fáceis de visualizar e entender, a programação se torna uma tarefa 
mais simples.”

* A identação é muito importante no .yaml.
* Não deixar uma linha adicional no final do arquivo como usual em outros tipos.
* Evitar quebrar linhas.

## VSCode

ERRO: The content on disk is newer. Click on Compare to compare your version with the one on disk

VS Code will show you an error message when you try to save a file that cannot be saved because it has changed on disk. VS Code blocks saving the file to prevent overwriting changes that have been made outside of the editor.

In order to resolve this issue, click the Compare action in the error message to open a diff editor that will show you the contents of the file on disk (to the left) compared to the contents in VS Code (on the right): {Refer an Image}

enter image description here

You must either accept the changes or revert the changes. Without taking any of the mentioned actions, you cant save the file.

P.S Above answer has been referred from visual studio code official documentation.

##  Console Rails

Pegar o id do pod:

`kubectl get pods` 

Entrar no conscole:

`kubectl exec -it scooby-development-5cc7854884-c62x5 bin/rails c`

## Deploy Staging

1- Entra no Jenkins

2- Entra em Scooby 

3- Entra em Build with parameters

4- Acha sua branch

5- Aperta build
