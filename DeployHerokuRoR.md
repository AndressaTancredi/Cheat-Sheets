# Deploy Heroku

1 - https://www.heroku.com/
   Fazer cadastro no site
  
   Seguir passo a passo do site > https://devcenter.heroku.com/articles/getting-started-with-rails5
   Descrição abaixo:
  
2 - https://devcenter.heroku.com/articles/heroku-cli#download-and-install
   Instalar o heroku conforme link acima e código abaixo:
   $ sudo snap install --classic heroku
  
3 - Fazer login
    $ heroku login
  
4 - O padrão do heroku é o PostgreSQL, por isso é necessário remover a gem sqlite3 da Genfile e add ela na parte
de desenvolvimento:

    group :development, :test do
    # Call...    
    gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
    ## Use sqlite3 as the database for Active Record
    gem 'sqlite3'
    end
    
 5 - Criar novo grupo de produção na Genfile para receber a gem do PostgreSQL:
 
    group :production do
    gem 'pg'
    end
 
 6 - Trazer a gem para o projeto
    $ bundle install
   
 7 - Preparar nossos arquivos para o deploy:
    $ git init
    $ git add .
    $ git commit -m "Meu primeiro deploy"
    
 8 - Dar um nome para sua aplicação (Esse nome será usado na url)
    $ heroku create nomeDaAplicação
  
 9 - Setar o local do deploy
    $ git config --list | grep heroku
    
 10 - Fazer deploy
    $ git push heroku master
    Abaixo estará o link para a aplicação.(vai dar erro se acessar o link, pois falta a migration abaixo)
    
 11 - Gerar as migrações
    $ heroku run rails db:migrate
 
 12 - 
