* Migration
Recurso do framework Rails para escrever o código no banco de dados usando Ruby ao invés de SQL. Serão classes que estemdem de ActiveRecord::Migration, devem estar no db/migration e podem ser gerada automaticamente usando:
`rails generate migration NomeDaMigration`

  `docker ps -a` (Pegar o ID do Container)
  
  `docker exec -it IDdoContainer bash`
  
  `bin/rake db:migrate`
  
  `bin/rake db:migrate RAILS_ENV=test`
  
  (No git status vai mostrar o schema com modificações, dar um checkout nele e já era!)
