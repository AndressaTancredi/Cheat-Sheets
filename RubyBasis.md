gem instal rails

rails new NomeDaApp

rails server

Documentação Ruby: http://ruby-doc.org

Documentação Ruby: http://apidock.com/ruby

tryruby.org => 15min de Ruby

### Pry é um IRB melhorado com cores de destaque
gem install pry e gem install pry-require_relative
Digita pry pra entrar no console

### Array/Vetor => uma coleção ordenada.
Inicializar: a = [] a = Array.new a = %w(Andressa Dias Tancredi)
Add valores: a.push(valor) Posso colocar diferentes tipos num msm array.
Acessar valores: a[posição]

### Hash => uma coleção de pares chave-valor
Inicializar:  a = {"item1" => "1", "item2" => "2"}
Add valores: a["item3] = 3
Acessar valores: a["item2"]

Para saber todos os métodos a. + tab
a.size.eql?(5) = O tamanho da array é igual a 5? Vai responder true or false

### Bloco (tando para array quanto pra hash)
a.each do |elementos|
  puts elementos
end

## Classe => Uma construção que é usada para criar instâncias (cópias) de si msm.
.class para saber o tipo
Criar a classe class Pessoa
Criar método def falar
  puts "Ola!"
 end
end
Instanciar p = Pessoa.new
Chamar o método p.falar
p.class

### Herança => herdar características (<) Ruby NÃO suporta herança múltipla.
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

## Módulo => coleção de métodos e constantes

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
Ruby NÃO suporta herança múltipla. Os módulos eliminam essa necessidade com o mixin.

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

## Yield => passar um bloco de código dentro de uma função ou outras coisas rs
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
