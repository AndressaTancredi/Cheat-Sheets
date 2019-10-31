* Migration

  `docker ps -a` (Pegar o ID do Container)
  
  `docker exec -it IDdoContainer bash`
  
  `bin/rake db:migrate`
  
  `bin/rake db:migrate RAILS_ENV=test`
  
  (No git status vai mostrar o schema com modificações, dar um checkout nele e já era!)
