# Guia de código HTML e CSS
Padrões para o desenvolvimento de um HTML e CSS flexível, durável e sustentável.



----------



## Índice

* [Regra de Ouro](#regra-de-oruo)
* [HTML](#html)
  * [Sintaxe](#sintaxe-do-html)
  * [Doctype HTML5](#doctype-html5)
  * [Pragmatismo sobre semântica](#pragmatismo-sobre-semantica)
  * [Ordem dos atributos](#ordem-dos-atributos)
  * [Marcação gerada via JavaScript](#marcacao-gerada-via-javascript)
* [CSS](#css)
  * [Sintaxe do CSS](#sintaxe-do-css)
  * [Ordem de declaração](#ordem-de-declaracao)
  * [Excessões de formatação](#excessoes-de-formatacao)
    * [Propriedades com prefixo](#propriedades-com-prefixo)
    * [Regras com declarações únicas](#regras-com-declaracoes-unicas)
  * [Legibilidade](#legibilidade)
    * [Comentários](#comentarios)
    * [Classes](#classes)
    * [Seletores](#seletores)
  * [Organização](#organizacao)
* [Writing copy](#copy)
  * [Sentence case](#sentence-case)



----------



## Regra de ouro

> Todo código em qualquer base de código deve parecer como se uma única pessoa o digitou, não importando quantas pessoas contribuiram.

Isso significa sempre respeitar rigorosamente estas diretrizes. Para adições ou contribuições, por favor [registre uma issue no GitHub](https://github.com/mdo/code-guide).



----------



## HTML


### Sintaxe do HTML

* Use tabs com dois espaços
* Elementos inseridos dentro de outros elementos devem ser indentados uma vez (2 espaços)
* Sempre use aspas dupla, nuca aspas simples
* Não inclua uma barra invertida de fechamento em elementos de fechamento automático

**Exemplo incorreto:**

````html
<!DOCTYPE html>
<html>
<head>
<title>Título da Página</title>
</head>
<body>
<img src='images/company-logo.png' alt='Company' />
<h1 class='hello-world'>Hello, world!</h1>
</body>
</html>
````

**Exemplo correto:**

````html
<!DOCTYPE html>
<html>
  <head>
    <title>Título da Página</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
````


### Doctype HTML5

Obriga o modelo padrão em todos navegadores possíveis com esse simples doctype no início de cada página HTML.


````html
<!DOCTYPE html>
````


### Pragmatismo acima da semântica

Empenhe-se para manter os padrões HTML e a semântica, mas não sacrifique o pragmatismo. Use a quantidade mínima de marcação com a menor complexidade quando possível.


### Ordem dos Atributos

Atributos HTML devem vir nessa ordem particular para uma leitura mais fácil do código.

* classe
* id
* data-*
* for|type|href

De tal forma que a sua marcação se parecerá com:

````html
<a class="" id="" data-modal="" href="">Example link</a>
````

### Marcação gerada via JavaScript

Escrever marcação em um arquivo javascript faz com que o conteúdo seja mais difícil de encontrar, mais difícil de editar e menos eficaz. Não faça isso. 



----------



## CSS

### Sintaxe do CSS

* Use tabs com dois espaços
* Ao agrupar seletores, mantenha cada um em uma única linha
* Inclua um espaço antes da chave de abertura dos blocos de declaração
* Coloque a chave de fechamento dos blocos de declaração em uma nova linha
* Inclua um espaço depois de <code>:</code> em cada propriedade
* Cada declaração deve aparecer em sua própria linha
* Termine todas as declaraçoes com um ponto e vírgula
* Valores separados por vírgula devem ter um espaço depois de cada vírgula
* Não inclua espaços depois das vírgulas em cores RGB ou RGBa, e não preceda valores com um zero à esquerda
* Coloque em caixa baixa todos os valores hexadecimais, e.g., <code>#fff</code> ao invés de <code>#FFF</code>
* Use valores hexadecimais abreviados quando possível, e.g., <code>#fff</code> ao invés de <code>#ffffff</code>
* Indique os atributos de valores no seletores, e.g., <code>input[type="text"]</code>
* Evite especificar unidade para valores zero, e.g., <code>margin: 0;</code> ao invés de <code>margin: 0px;</code>

**Exemplo incorrecto:**

````css
.seletor, .seletor-secundario, .seletor[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}
````

**Exemplo correto:**

````css
.seletor,
.seletor-secundario,
.seletor[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
````

Dúvidas sobre os termos usados aqui? Consulte a [seção sobre sintaxe no artigo de Cascading Style Sheets](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax) na Wikipedia.


### Ordem de Declaração

Declarações relacionadas devem ser agrupadas juntas, colocando as propriedades de posicionamento e box-model próximas do topo, seguidas por tipografia e propriedades visuais.

````css
.ordem-de-declaracao {
  /* Posicionamento */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Tipografia */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Diversos */
  opacity: 1;
}
````

Para uma completa lista de propriedades e sua ordem, por favor veja [Recess](http://twitter.github.com/recess).


### Excessões de dormatação

Em alguns casos, faz sentido desviar-se ligeiramente da [sintaxe](#sintaxe-do-css) padrão.

#### Propriedades com Prefixo

Ao usar propriedades com prefixos, indente cada propriedade de tal forma que o valor se alinhe verticalmente para uma fácil edição multi-linha.

````css
.seletor {
  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
          border-radius: 3px;
}
````

No Textmate, use **Text &rarr; Edit Each Line in Selection** (&#8963;&#8984;A). No Sublime Text 2, use **Selection &rarr; Add Previous Line** (&#8963;&#8679;&uarr;) and **Selection &rarr;  Add Next Line** (&#8963;&#8679;&darr;).

#### Regras com decalarações únicas

No casos em que várias regras apresentarem apenas uma declaração cada, considere remover as quebras de linha para facilitar a leitura e agilizar a edição.

````css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
````


### Legibilidade

Código é escrito e mantido por pessoas. Garanta que seu código seja descritivo, bem comentado e acessível por outros.

#### Comentários

Bons comentários de código transmitem contexto ou propósito e não devem apenas reiterar um compenente ou nome da classe.

**Exemplo ruim:**

````css
/* Modal header */
.modal-header {
  ...
}
````

**Exemplo bom:**

````css
/* Elemento que envolve .modal-title e .modal-close */
.modal-header {
  ...
}
````

#### Classes

* Manter classes em caixa baixa e usar traços (não usar underline ou camelCase)
* Evite notação abreviada arbitrária
* Mantenha as classes o mais curto e sucinta possíveis
* Use nomes significativos; use nomes estruturais ou com propósito para apresentações
* Prefixo das classes baseado na classe do componente pai mais próximo

**Exemplo ruim:**

````css
.t { ... }
.red { ... }
.header { ... }
````

**Exemplo bom:**

````css
.tweet { ... }
.important { ... }
.tweet-header { ... }
````

#### Seletores

* Use classes ao invés de tags de elementos genéricos
* Mantenha-os curtos e limite o número de elementos em cada seletor para três
* Classes de escopo para os pais mais próximos quando necessário (e.g.,quando não estiver usando classes com prefixo)

**Exemplo ruim:**

````css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
````

**Exemplo bom:**

````css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
````

### Organização

* Organize seções de código por componente
* Desenvolva uma consistente hierarquia de comentários
* Se estiver usando vários arquivos CSS, discriminá-los por componente



----------



## Cópia

### Sentence case

Sempre escreva, incluindo cabeçalhos e comentários de código em [sentence case](http://en.wikipedia.org/wiki/Letter_case#Usage). Em outras palavras, com exceção de títulos e nomes próprios, apenas a primeira letra deve ser em maiúscula.



----------



### Agradecimentos

Profundamente inspirado por [Idiomatic CSS](https://github.com/necolas/idiomatic-css) e o [GitHub Styleguide](http://github.com/styleguide). Feito com todo o amor do mundo por [@mdo](http://twitter.com/mdo).
