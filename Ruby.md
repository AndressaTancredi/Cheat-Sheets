## Migration

Recurso do framework Rails para escrever o código no banco de dados usando Ruby ao invés de SQL. São classes que estendem de ActiveRecord::Migration, devem estar no db/migration e podem ser geradas automaticamente usando:
`rails generate migration NomeDaMigration`

Rodar Migration para atualizar seu Schema e deixa-lo pareado com o banco de dados geral.

  `docker ps -a` (Pegar o ID do Container)
  
  `docker exec -it IDdoContainer bash`
  
  `bin/rake db:migrate`
  
  `bin/rake db:migrate RAILS_ENV=test`
  
  (No git status vai mostrar o schema com modificações, dar um checkout nele e já era!)
  
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
