gem instal rails

rails new NomeDaApp
SE quiser com o mysql
rails new NomeDaApp --database=mysql

rails server

Documentação Ruby: http://ruby-doc.org

Documentação Ruby: http://apidock.com/ruby

tryruby.org => 15min de Ruby

### Pry é um IRB melhorado com cores de destaque
gem install pry e gem install pry-require_relative
Digita pry pra entrar no console

### Array/Vetor 
=> uma coleção ordenada.
Inicializar: a = [] a = Array.new a = %w(Andressa Dias Tancredi)
Add valores: a.push(valor) Posso colocar diferentes tipos num msm array.
Acessar valores: a[posição]

### Hash 
=> uma coleção de pares chave-valor
Inicializar:  a = {"item1" => "1", "item2" => "2"}
Add valores: a["item3] = 3
Acessar valores: a["item2"]

Para saber todos os métodos a. + tab
a.size.eql?(5) = O tamanho da array é igual a 5? Vai responder true or false

### Bloco 
(tando para array quanto pra hash)
a.each do |elementos|
  puts elementos
end

## Classe 
=> Uma construção que é usada para criar instâncias (cópias) de si msm.
.class para saber o tipo
Criar a classe class Pessoa
Criar método def falar
  puts "Ola!"
 end
end
Instanciar p = Pessoa.new
Chamar o método p.falar
p.class

### Herança 
=> herdar características (<) Ruby NÃO suporta herança múltipla.
Herança múltipla é classe relogio e outra radio e criar uma classe radio relogio herdando das 
duas ao msm tempo.  
class Pessoa
  def falar
    puts "Ola"
  end  
end

require_relative "pessoa"
class Atleta < pessoa
  def correr
    puts "correndo"
  end
end

Além desse atleta poder correr, ele pode falar.

## Módulo 
=> coleção de métodos e constantes

module Configurações
  NOME_DO_SISTEMA = "Sistema da Academia"
  VERSAO =  "1.2.4"

  def calcular
    puts "O resultado é: ..."
  end  
end

Acessar a constante:
no irb require_relative "meu_modulo"
Configuracoes::NOME_DO_SISTEMA
=> "Sistema da Academia"
OU
include Configuracoes (lembrando que é o nome do módulo não do file)
Configuracoes::NOME_DO_SISTEMA
=> "Sistema da Academia"

Diferente das classes, você não pode criar objetos baseados em módulos nem pode criar módulos
que herdam desse módulo; ao invés disso, você especifica qual funcionalidade de um módulo 
específico você deseja adicionar a uma classe ou a um objeto específico. Módulos permanecem 
sozinhos; não há hierarquia de módulos ou herança. eles agem como namespace, permitindo que 
você defina métodos cujos nomes não irão colidir com aqueles definidos em outras partes de um
programa. Permitem que você compartilhe funcionalidade entre classes – se uma classe “mistura”
(mixes in) um módulo (isto é, o inclui), todos os métodos de instância do módulo se tornam 
disponíveis como se tivessem sido definidos na classe.

#### Ruby NÃO suporta herança múltipla. Os módulos eliminam essa necessidade com o mixin.

módulo:
module Configuracoes
  NOME_DO_SISTEMA = "Sistema da Academia"
  VERSAO =  "1.2.4"

  def calcular
    puts "O resultado é: ..."
  end  
end

classe:
module Correio
  def enviar_correio
    puts "enviando..."
  end 
end

mixin:
require_relative "meu_modulo"
require_relative "modulo_correio"

class MeuMixin
  include Configuracoes
  include Correio
end

IRB:
require_relative "meu_mixin"
m = MeuMixin.new
m.calcular (do módulo)
m.enviar_correio (da classe)

Com o mixin consegui acessar os métodos de um módulo e de uma classe.

## Yield 
=> passar um bloco de código dentro de uma função ou outras coisas rs
def ola
  puts "Oi oi oi"
  yield
  puts "helow"
end

Se rodar dá erro: 
LocalJumpError (no block given (yield))

Pq preciso passar o meu yield que pode ser qlq código:
ola {puts "Código no meio"} ou usando um do comum
Oi oi oi
Código no meio (AQUI meu yield)
helow

## DB
Posso mudar o BD indo em config no arquivo database.yml alterando as configs.
Posso setar usuário e senha nesse yml para o sql   username: root ||   password: "saopaulo17"
Para saber em qual ambiente estou usando meu db:
Quando dou um rails s ele mostra.
Se eu quiser mudar o ambiente:
rails s -e production ou test

Como faço para criar os bds que aparecem no databse.yml no MySQL:

mysql -u root

Mostrar dbs do MySQL:
show databases;

+--------------------+

| Database           |

+--------------------+

| information_schema |

| mysql              |

| performance_schema |

| sys                |

+--------------------+

#####Rake

Saber os camandos: rake -T

Criar os bds do dabase.yml sem ter que ir no Workbranch criar na mão: rake db:create
Posso checar rodando: mysql -u root e show databases;

+-----------------------+
| Database              |
+-----------------------+
| information_schema    |
| RubyBasis_development |
| RubyBasis_test        |
| mysql                 |
| performance_schema    |
| sys                   |
+-----------------------+

##### COC Convention Over Configuration
Convenções a serem seguidas para que o dev não se preocupe com configurações. Ex: geradores Scafold, pastas prontas, tabelas no db com campo id.

##### CRUD - create(put/post), read(get), update(put,patch) e delete(delete).

Scaffold = Andaime Vai gerar model, view, controller e uma migrate.

Saber os geradores existentes: rails generate ou rails g
rails g scaffold NomeQVcQuiserParaAModelDoProjeto ex: customer, pet, etc... SEMPRE no singular os modelos no Ruby e as tabelas no BD ficarão no plural, pq possui TODOS os custumers e o modelo representa um só.

rails g scaffold customer name:string email:string birthday:date obs:text 

#### Migrations

Maneira pela qual o Ruby cria e modifica o BD.
Sempre cria automaticamente: t.timestamps = created_at e updated_at

Agora vamos passar essa tabela para o MySql:
rake db:migrate

Para checar:

mysql -u root

use RubyBasis_development;

desc customers

+------------+--------------+------+-----+---------+----------------+
| Field      | Type         | Null | Key | Default | Extra          |
+------------+--------------+------+-----+---------+----------------+
| id         | bigint(20)   | NO   | PRI | NULL    | auto_increment |
| name       | varchar(255) | YES  |     | NULL    |                |
| email      | varchar(255) | YES  |     | NULL    |                |
| birthday   | date         | YES  |     | NULL    |                |
| obs        | text         | YES  |     | NULL    |                |
| created_at | datetime(6)  | NO   |     | NULL    |                |
| updated_at | datetime(6)  | NO   |     | NULL    |                |
+------------+--------------+------+-----+---------+----------------+

Vai na local host e o crud estará pronto!

#### eRuby

erb imbute ruby no html (embedded ruby) <% código ruby %>

Se quiser mostrar no front: <%= %>

Se quiser mostrar no front e tirar a quebra de linha após o código: <%= -%>

Comentário: <%#= %>

#### Interpolação

#{nomeDaVar ou Texto}

### Models
 
ActiveRecord é um framework responsável por relacionar nossas classes com nosso BD.

rails console ou rails c Nesse console tenho um ambiente de todas as classes no projeto

a = Customer.first  ||  a.name  ||  etc

### Controllers

Local para as ações no meu sistema

#### Variaveis de instancia
Com @ na frente para ficar disponível entre a controller e a view, fica no controller.

Ex:

  def index
    @customers = Customer.all
  end

### Rotas
config/routes.rb e localhost:3000/rails/info/routes

1- rails g controller nomeDaController Vai gerar a controller e a pasta na view

2- Add na pasta nomeDaController na view um arq index.html.erb com conteúdo html ou ruby

3- Add   get 'inicio' => 'nomeDaController#index' (Quando bater na rota inicio vai chamar a controller welcome e a ação index)

4- Acesse o localhost com a rota criada: localhost/inicio

Criar uma rota raíz:  root to: 'welcome#index' (Significa o nome do controller + # + ação que eu vou chamar)

resources :customers é um atalho que o rails cria pra gerar todas as rotas com 7 verbos. :customers é a model.

#### Helpers
Métodos prontos/ou criados por vc, que podem ser usados nas views.

1 - Link_to => gera um link

Coloca no html:

<%= link_to "Cadastro", "/customers" %> que é a msm coisa disso: <a href="/customers">Cadastro</a> mas no rails usamos o link_to.
Se vc olhar nesse link localhost:3000/rails/info/routes vai ver todas as rotas e o nomepath que corresponde a ela, então o certo é usar: <%= link_to "Cadastro", customers_path %>

2 - Existem vários, posso pesquiser na APIDOC link na documentação lá em cima.
Campos do html - DOM.

Ex de um helper criado:
module ApplicationHelper
  def data_br(data_us)
    data_us.strftime("#d/%m/%Y")
  end
end
Chama na view: data_br(Data.today)

##### Params

É o que está chegando pela url ou post. é uma var global que o Rails fornece. paramns vem em hash e devemos ajustar o que estamos procurando:     
def customer_params
  params.require(:customer).permit(:name, :email, :birthday, :obs) Por segurança usa o permit.
end
def set_customer
  @customer = Customer.find(params[:id])
end


#### Rest Restful

Rest = Representational State Transfer, Transferência de Estado Representativo que diferente do SOAP que tinha apenas POST e GET usar o CRUD completo. Fala tb que cada recurso é unicamente direcionado através da sua URI.
Sistemas que seguem os princípios REST são chamados de RESTFUL.

#### Symbols

No IRB se vc digitar "oi".object_id vai retornar um id que muda sempre, digita de novo e será outro id para a msm string. Se vc pedir o :oi.object_id vai retornar um id único que nunca vai mudar.

#### Active Record

Perquisando, criando e persistindo no DB.

y = Customer.where(id:1)
z = Customer.create(name: "Maria", email: "maria@gmail.com", birthday: Date.today, obs: "nada")
w = Customer.new cria com tudo nil
w.name = "João" etc...
w.safe w.reload

#### Filtros

before_action x before_filter(não usa mais, mudou o nome para before_action)
São métodos rodados antes ou depois de uma ação do controller.

  before_action :set_customer, only: [:show, :edit, :update, :destroy]

Por isso que na controller nos métodos show e edit não tem nada, pq o set_customer já faz isso.

#### Partials

Vai pra uma pag que vai renderizar em outro lugar, no caso aqui> _sua_partial.html.erb e esse aquivo pode ser compartilhado pq o código repete em vários outros locais.

#### i18n - Internationalization (pq são 18 letras) ou Localizar
controller: I18n.t Traduz texto e I18n.l Traduz data e hora
view: <%= t('hello')%> ou <td><%= l(customer.birthday) %></td>
  
  Pegar yml para locale pronto e criar um arquivo pt-br_rails.yml
  https://raw.githubusercontent.com/AndressaTancredi/rails-i18n/master/rails/locale/pt-BR.yml
  Roda o servidor de novo e o Birthday estará conforme é aqui no BR.

https://guides.rubyonrails.org/i18n.html
Traduzir a página de forma simples.

config/application.rb e add dentro da classe: config.i18n.default_locale = "pt-BR"
____

### Bootstrap
Instalar a gem stylesheet caso queira cores e mais filuras

Add no Genfile : gem "twitter-bootstrap-rails"

Rode: rails g bootstrap:install static

rails g bootstrap:layout application fluid Dá Y e já era

rails g bootstrap:themed NomeDoModuloNoPlural

#### Gerenciar versões do Ruby
https://www.treinaweb.com.br/blog/gerenciar-versoes-do-ruby-com-rvm/




