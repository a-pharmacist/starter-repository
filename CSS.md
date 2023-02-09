# Introdução 

## O que significa CSS?

* Cascading Style Sheet
* Código para criar estilos no HTML
* HTML é a estrutura e o CSS é a beleza
* Não é uma linguagem de programação, como o HTML também não
* É uma linaguagem Style Sheet

## Como fazer comentários em CSS

/* Comentário */ -- O comentário também pode ser utilizado para desabilitar partes do código

## Anatomia

* Selector -- p. ex.: h1
* Declaration -- todo o texto entre chaves
* Properties -- p. ex: "color"
* Property Value -- p. ex: "blue"

## Selectors

* Conecta um elemento HTML ao CSS

### Tipos: 

* Global selector '*'
* Element/Type selector 'h1, h2, p, div'
* ID selector '#box, #container'
* Class selector '.red, .m-4'
* Attribute selector, Pseudo-class, Pseudo-element e outros
* É possível realizar o agrupamento de seletores por meio do uso da vírgula: h1, h2 etc.

## Caixas

* (Quase) tudo são caixas do CSS
* Posicionamentos, tamanhos, bordas, cores
* Caixa pode ficar ao lado uma da outra, ou dentro, ou acima
* Elementos HTML são caixas

## Adicionando CSS no documento HTML

### inline

* Atributo "Style"

### <style>

* Tag HTML que irá conter o css

<style>
	h1 {
			color: blue;
			}
	
	strong {
			color: red;
			}
</style>

### link

* Arquivo CSS externo
* <link rel="stylesheet" href="style.css"> Este texto deve ser colocado no "head" do documento HTML. É uma boa prática manter o HTML e CSS juntos na mesma pasta do VSCode. 

### @import

* Arquivo CSS externo
* Não é indicado, porque leva maior tempo para busca de arquivo externo, o link é preferível

## A cascata (cascading)

A escolha do browser de qual regra ele irá aplicar, caso existam muitas regras para o mesmo elemento. 

* O estilo é lido de cima para baixo -- códigos contraditórios podem anular um ao outro

É levado em consideração 3 fatores: 

1. Origem do estilo 
2. Especificidade
3. Importância

### Origem do estilo

inline > tag style > tag link -- o uso do atributo 'style' inline é o mais forte de todos e se sobrepõe aos outros para o mesmo elemento.

### Especificidade

É um cálculo matemático, onde, cada tipo de seletor e origem do estilo, possuem valores a serem considerados. 

0. Universal selector (*), combinators e nagation pseudo-class (:not())
1. Element type selector (h1, h2, p, div) e pseudo-elements (::before, ::after)
10. Classes e attribute selectors ([type="radio"])
100. ID selector
1000. Inline

### A regra !important

* Cuidado, evitar o uso
* Não é considerada uma boa prática
* Quebra o fluxo natural da cascata

## At-rules

* Está relacionado ao comportamento do CSS
* Começa com o sinal de '@' seguido do identificador e valor

- @import               /* incluir um CSS externo */ 
@import "http://local.com/style.css"; ou @import url("http://local.com/style.css");

- @media               /* regras condicionais para dispositivos */
@media (min-width: 500 px) { /* rules here */ }

- @font-face           /* incluir fontes externas */
@font-face { /* rules here */ }

- @keyframes           /* Animações */
@keyframes nameofanimation { /* rules here */ }

## Shorthand

* Junção de propriedades
* Resumido 
* Legível

{
    /* background properties */
    background-color: #000;
    background-image: url(images/bg.gif);
    background-repeat: no-repeat;
    background-position: left top;

    /* background shorthand*/
    background: #000 url(images/bg.gif) no-repeat left top;

    /* font properties */
    font-style: italic;
    font-weight: bold;
    font-size: .8em;
    line-height: 1.2;
    font-family: Arial, sans-serif;

    /* font shorthand */ 
    font: bold italic .8em/1.2 Arial, sans-serif;
}

* Não irá considerar propriedades anteriores;
* Valores não especificados irão assumir o valor padrão;
* Geralmente, a ordem descrita não importa, mas se houver muitas propriedades com valores semelhantes, podemos encontrar problemas;

### Propriedades que aceitam shorthand

Consultar na documentação do CSS: https://developer.mozilla.org/pt-BR/docs/Web/CSS

## Funções 

* Nome seguido de abre e fecha parentesis
* Recebe argumentos

### Exemplos

color: rgb(255,0,100);
@import url ("http://local.com/style.css");

## DevTools (ferramentas do desenvolvedor)

## Vendor Prefixes

Permite que browsers adicionem 'features' a fim de colocar em uso alguma novidade que vemos no CSS

### Exemplo

p {
	-webkit-background-clip: text; /*Chrome, Safari, iOS e Android*/
	-moz-background-clip: text; /* Mozilla (Firefox) */
	-ms-background-clip: text; /* Internet Explorer ou Edge*/
	-o-background-clip: text; /* Opera */
}

Consultas:

https://ireade.github.io/which-vendor-prefix
https://caniuse.com

# Valores e unidades de medidas

* Cada propriedade possui valores 'property: value'; -- '' = propriedade ex.: 'color' / <> = valor ex.: <color>
* Estudo constante a fim de entender as propriedades e seus valores; 

## Na prática

* Como conhecer e estudar os valores na documentação?
<color> <length>

* Os termos podem variar values ou data types

Documentação MDN: https://developer.mozilla.org/en-US/

## Tipos numéricos

<integer> - número inteiro como -10 ou 223
<number> - número decimal como -2.4, 64 ou 0.234
<dimension> - é um <number> com uma unidade junto: 90deg, 2s, 8px
<percentage> - representa uma fração de outro número: 50%

### Unidades comuns

<length> - é um dos mais usados no CSS e representa um valor de distância: px, em, vw
<angle> - representa um ângulo: deg, rad, turn
<time> - representa um tempo: s, ms
<resolution> - representa resoluções para dispositivos: dpi

## Distâncias absolutas <length>

São fixas e não alteram seu valor.

| Unidade  | Nome                | Equivalência         |
|----------|---------------------|----------------------|
| cm       | Centímetros         | 1cm = 96px/2.54      | 
| in       | Inches (polegadas)  | 1in = 2.54cm = 96px  | 
| px       | Pixels              | 1px = 1/96th of 1in  |

* o mais comum e mais utilizado é o px

* não é recomendado usar cm

## Distâncias relativas

São relativas a um outro valor, pode ser o elemento pai, ou root, ou o tamanho da tela.
Benefício: Maior adaptação aos diferentes tipos de tela.

| Unidade  | Relativo a                                    |
|----------|-----------------------------------------------|
| em       | Tamanho da font do elemento pai               |
| rem      | Tamanho da font do elemento raiz (root/html)  | 
| vw       | 1% da viewport width                          |  
| vh       | 1% da viewport height                         |

Normalmente o tamanho da font padrão do navegador é de 16px e para mudar esse valor temos que fazer a alteração no root ou no elemento html.

:root {
	font-size: 18px;
}

/* OU */

html {
	font-size: 18px;
}

O viewport é a parte da tela que está sendo exibida. No caso dos navegadores web, é o que é exibido na janela/tela do documento. Conteúdos que estão fora do viewport só serão exibidos quando feito um scroll da área de visualização.

## Porcentagens

* As porcentagens são valores bem flexíveis
* Em muitos casos são tratadas da mesma maneira que as distâncias <length>
* Sempre será relativa a algum valor

### Exemplo

Relativo ao elemento pai

<ul>
	<li>One</li>
	<li>Two</li>
	<li>Three
		<ul>
			<li>Three A</li>
			<li>Three B</li>
			<ul>
				<li>Three B 2</li>
			</ul>
		</ul>
	</li>
</ul>

li {
    font-size: 80%; -- relativo ao valor padrão do HTML no browser
}

## Posições

<position>

* Representa um conjunto de coordenadas 2D:
* top, right, bottom, left e center
* Usado para alguns tipos de propriedades como o background-position
* Não confundir com a propriedade position

## Funções

Em programação, funções são reconhecidas por causar um reaproveitamento de código.

Exemplos de funções do CSS:

* rgb()
* hsl()
* url()
* calc()

Dentro dos parêntesis são passados argumentos

Link da documentação do MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions

## Strings e identificadores

* Strings: texto envolto em aspas

.box::after {
	content: "Isso é uma string"
}

* Identificadores: podemos ter nomes de cores como red, black, gold

# Box model

O Box Model é fundamental para fazer layouts para web porque ele vai te dar maior facilidade na hora de aplicar o CSS. Ao entender os conceitos do Box Model muitas questões do CSS começam a fazer sentido.

## O que é o Box Model?

* Cada elemento é representado como uma caixa retangular

* Essa caixa possui propriedades de uma caixa em 2 dimensões (largura x altura)

* Propriedades da caixa

    Tamanho (largura x altura) → width | height
    Conteúdo → content
    Bordas → border
    Preenchimento interno → padding
    Espaços fora da caixa → margin

## box-sizing: border-box

Propriedade e valor que mantêm a largura da caixa de acordo com o tamanho (width) determinado, independentemente do espaço ocupado pelo conteúdo (padding). Por padrão, o valor da propriedade 'box-sizing' é <content-box>, sendo necessário alterar isso. 

* <border-box> -- distância de uma borda a outra;
* <content-box> -- espaço ocupado pelo conteúdo da caixa;

## display: block; vs display: inline;

* Como as caixas se comportam em relação as outras caixas
* Comportamento externo das caixas

* Display block: 

* Ocupa toda a linha, colocando o próximo elemento abaixo desse
* width e height são respeitados
* padding, margin, border irão funcionar normalmente
* <p> <div> <section>, todos os headings

* Display inline: 

* Os elementos ficam ao lado do outro e não empurram outros elementos para baixo
* width e height não funcionam
* Somente valores horizontais de margin
* <a> <span> etc.

## Margin

* Margin, é o espaço (margem) entre os elementos

* Podemos dividir o margin em 4 valores:

/* margin-top | margin-right | margin-bottom | margin-left */
values: <length> | <percentage> | auto -- realiza cálculos somente nas laterais

Geralmente usamos uma forma abreviada (shorthand) para escrever o margin. Esse formato segue o sentido horário iniciando pelo top, seguindo para right, bottom e left.

    margin: 12px 16px 10px 4px; /* TOP = 12px | RIGHT = 16px | BOTTOM = 10px | LEFT = 4px */
    margin: 12px 16px 0; /* TOP = 12px | RIGHT = 16px | BOTTOM = 0px | LEFT = 16px */
    margin: 8px 16px; /* TOP = 8px | RIGHT = 16px | BOTTOM = 8px | LEFT = 16px */
    margin: 8px; /* TOP = 8px | RIGHT = 8px | BOTTOM = 8px | LEFT = 8px */

* O margin é aplicado em elementos com display block

* Cuidado com o margin collapsing que é quando o top se junta ao bottom (ocorre apenas em display block)

## Padding

* O padding é o preenchimento interno da caixa.

* A propriedade padding pode ser escrita como nos formatos apresentados abaixo:

    padding-top | padding-right | padding-bottom | padding-left

* Geralmente usamos uma forma abreviada (shorthand) para escrever o padding. Esse formato segue o sentido horário iniciando pelo top, seguindo para right, bottom e left.

    padding: 12px 16px 10px 4px; /* TOP = 12px | RIGHT = 16px | BOTTOM = 10px | LEFT = 4px */
    padding: 12px 16px 0; /* TOP = 12px | RIGHT = 16px | BOTTOM = 0px | LEFT = 16px */
    padding: 8px 16px; /* TOP = 8px | RIGHT = 16px | BOTTOM = 8px | LEFT = 16px */
    padding: 8px; /* TOP = 8px | RIGHT = 8px | BOTTOM = 8px | LEFT = 8px */

* O padding pode ter valores (values) de comprimento (px, em, rem) ou de porcentagem (%)

* O padding poderá causar diferença na largura de um elemento

- obs.: Na aula sobre box-sizing aprendemos como resolver essa diferença na largura do elemento

## Border-outline

São as bordas da caixa

Documentação do MDN: https://developer.mozilla.org/en-US/docs/Web/CSS/border

value: <border-style> | <border-width> | <border-color>

style: solid | dotted | dashed | double | groove | ridge | inset | outset
width: <length>
color: <color>

div {
	/* shorthand */
	border-top: solid 2px; /* top | right | bottom | left */

	/* style */
	border: solid;

	/* width <length> | style */
	border: 2px dotted;

	/* style | color */
	border: outset #f33;

	/* width | style | color */
	border: medium dashed green;

}

## Outline

O outline é muito semelhante ao border, mas difere em 4 sentidos:

* Não modifica o tamanho da caixa, pois não é parte do Box Model
* Poderá ser diferente de retangular
* Não permite ajuste individuais
* Mais usado pelo user agent para acessibilidade

# Cores

Usamos CSS para alterar cores do nosso documento.

* Tipos
- background-color (para caixas)
- color (para textos)
- border-color (para caixas)
- outros

* Valores

Podemos definir valores por:

- palavra-chave (blue, transparent, currentcolor)
- hexadecimal (#990011) (#009910) (#000099)
- funções: rgb, rgba, hsl, hsla

## Hexadecimal 

/*<hex-color> values 0-9 e A-F*/

	color: #090; /* RED, GREEN, BLUE */
	color: #009900;
	color: #090a;
	color:#009900aa;


## RGB

RGB → Red, Green e Blue

O alpha representa a transparência da cor

/*<rgb()> values */
	color: rgb(34, 12, 64) /* 0-255 */
	color: rgba(34, 12, 64, 0.6)

## HSL

HSL → Hue - Saturation - Lightness

	color: hsl(180, 100%, 50%, 60%)
	color: hsla(180, 100%, 50%, 60%)

## Valores globais

/* Global values */
	color: inheritr; /* Herda a cor do elemento anterior */
	color: initial; /* Volta a sua cor inicial */
	color: unset; /* Pega a cor do contexto */

Referência: https://developer.mozilla.org/en-US/docs/Web/CSS/color_value

## Background

* Define um fundo para nosso elemento
* Sua área de atuação é a caixa toda
* Por padrão, é transparente

Exemplos: 

* Usar cores solidas
* Usar imagens

Controlar:

* a posição das imagens
* se elas se repetem ou não
* o tamanho delas na caixa
* Usar cor e imagem juntas
* Usar cor gradiente

## Background-color

A propriedade background-color define a cor de fundo do elemento selecionado.

HTML

<header>

</header>
<main>
    <h1>Evolua rápido com a tecnologia</h1>
    <p>Junte-se a milhares de devs e acelere
    na direção dos seus objetivos</p>
</main>

CSS

* {
    margin: 0;
}

header {
    height: 100px;
    border: 7px dashed red;
    background-color: rgb(55, 100, 50);
}

## Background-image-repeat

Para adicionar uma imagem como background podemos usar a propriedade background-image
Por padrão a imagem vai se repetir e podemos modificar essa opção usando a propriedade background-repeat

/* Values */
	background-repeat: repeat-x;
	background-repeat: repeat-y;
	background-repeat: repeat;
	background-repeat: space;
	background-repeat: round;
	background-repeat: no-repeat;

/* Podedmos usar 2 valores: horizontal | vertical */
	background-repeat: repeat space;
	background-repeat: repeat repeat;
	background-repeat: round space;
	background-repeat: no-repeat round;

## Background-position

Com a propriedade background-position podemos mudar a posição da imagem do background.

/* Pricipais valores */
	background-position: top;
	background-position: bottom;
	background-position: left;
	background-position: right;
	background-position: center;

## Background-size

Para mudar o tamanho da imagem do background usamos a propriedade background-size.

/* Values */
	background-size: cover;
	background-size: contain;

/* Podemos usar 2 valores, o primeiro é para a largura da imagem e o segundo é para a altura */
	background-size: 40% auto;
	background-size: 2em 25%;
	background-size: auto 8px;
	background-size: auto auto;

## Background-origin-clip

A propriedade background-origin é quem define o ponto de origem de uma imagem específica.

/* Principais valores */
background-origin: border-box;
background-origin: padding-box;
background-origin: content-box;

O background-clip define se a cor ou imagem do background iniciam debaixo de sua área de borda, preenchimento ou conteúdo.

/* Principais valores */
background-clip: border-box;
background-clip: padding-box;
background-clip: content-box;
background-clip: text;

## Background-attachment

A propriedade background-attachment determina se a posição da imagem vai ser fixa ou se vai rolar junto com o conteúdo.

/* Principais valores */
	background-attachment: scroll;
	background-attachment: fixed;
	background-attachment: local;

Podemos usar o *shorthand* background para definir todos os valores do background

## Gradient

linear-gradient() é a função usada para criar gradient linear com o CSS.

	background: linear-gradient(45deg, red, yellow)

radial-gradient() é a função usada para criar gradient circular.

	background: radial-gradient(green, red, yellow)
	background: radial-gradient(rgba(255, 255, 255, 0), rgba(255, 0, 0, 0.2))

## Múltiplos valores

Podemos aplicar múltiplos backgrounds em um mesmo elemento, podendo ter cor sólida, gradiente ou imagem. Para isso basta separar por vírgula cada background.

# Page Layouts

Nessa aula vamos ver alguns dos métodos usados para posicionar os elementos na tela.

* Tables
* Floats e clear
* Frameworks e Grid Systems
* Flexbox
* Grid

## Position 

Controla onde, na página, o elemento irá ficar, alterando o fluxo normal dos elementos.

Name: position
Value: static | relative | absolute | fixed

Lembrando que o fluxo normal dos elementos é ficar um abaixo do outro, a não ser no caso de elementos inline, que ficam um ao lado do outro.

## Static 

Por padrão os elementos são static. Isso significa que os elementos irão seguir o fluxo normal do HTML.

## Relative

O position indica onde o elemento vai ser posicionado na página. Ao usar o position podemos adicionar outras propriedades como top, right, bottom, left e z-index, que vão determinar o posicionamento final do elemento.

Quando o position é relative os elementos são deslocados do seu posicionamento normal, mas sem afetar o posicionamento de outros elementos da página.


HTML

<div class="box box1"></div>
<div class="box box2"></div>
<div class="box box3"></div>


CSS

.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.box1 {
  background-color: red;
  position: relative;
  left: 100px;
  top: 80px
}

.box2 {
  background-color: green;
}

.box3 {
  background-color: blue;
}

## Absolute

Quando o position é absolute o elemento é deslocado saindo do fluxo normal. O elemento de position absolute é posicionado em relação ao seu parent element mais próximo. Se esse elemento "pai" não existir, ele será posicionando em relação ao bloco contendo a raiz do elemento.


HTML

<div class="box box1"></div>
<div class="box box2"></div>
<div class="box box3"></div>


CSS

.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.box1 {
  background-color: red;
  position: absolute;
  left: 100px;
  top: 80px
}

.box2 {
  background-color: green;
}

.box3 {
  background-color: blue;
}

## Fixed

Quando aplicado o position fixed é como se criasse um elemento flutuante que fica fixo na página, independente do scrolling feito.

## Element Stacking

É o empilhamento de elementos. Podemos usar o z-index para determinar a ordem da posição do elemento. Quanto maior o z-index, mais "acima" vai aparecer o elemento.


HTML

<div class="box box1"></div>
<div class="box box2"></div>
<div class="box box3"></div>


CSS

.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.box1 {
  background-color: red;
  position: absolute;
  left: 5px;
  top: 5px;
  z-index: 3;
}

.box2 {
  background-color: green;
  position: absolute;
  left: 10px;
  top: 10px
}

.box3 {
  background-color: blue;
  position: absolute;
  left: 15px;
  top: 15px
}

## Display Flex

* Nos permite posicionar os elementos dentro da caixa
* Controle em uma dimensão (horizontal ou vertical)
* Alinhamento, direcionamento, ordenar e tamanhos

div.parent {
	display: flex;
}

* Flex-direction
Qual a direção do flex: horizontal ou vertical
row | column

* Alinhamento
justify-content
align-items

HTML

<div class="container">
  <div class="box blue"></div>
  <div class="box red"></div>
  <div class="box green"></div>
</div>


CSS

.container {
    display: flex;
    justify-content: space-between;
}

.box {
  width: 50px;
  height: 50px;
  margin-bottom: 8px;
}

.blue {
  background-color: blue;
}

.red {
    background-color: red;
}

.green {
    background-color: green;
}

# font-properties

A tipografia transmite uma mensagem, por exemplo, quando queremos dar uma ênfase no texto nós podemos escrever o mesmo em negrito.

Nós podemos transmitir uma mensagem diferente dependendo do estilo que escrevemos o texto.

Algumas das propriedades de fonts do CSS que podem nos ajudar a transmitir uma mensagem através dos textos da página são:

* font-family
* font-weight
* font-style
* font-size

## font-family

Tipo de fonte de um elemento
Lista de fontes e ordem de prioridade
inclui *fallback* font

p {
  font-family: "Times New Roman", Times, serif;
}
Alguns tipos de fonts:

serif (com serifa)
sans-serif (sem serifa)

## font-weight

Peso da fonte
Valores: normal | bold | bolder | lighter | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900
Dependendo da família da fonte não conseguimos utilizar todos os pesos de fonte

p {
	font-weight: bold;
}

Referência
https://www.w3.org/TR/css-fonts-3/

## font-style

É o estilo da fonte
Valores: normal | italic | oblique
Os valores que podem ser aplicados dependem da fonte usada

span {
	font-style: italic;
}

## font-size

Tamanho da fonte

p {
	font-size: 18px;
}

## Web fonts

Fontes do sistema x Fontes da web

Fontes do sistema são as fontes que estão instaladas na máquina do usuário e nem sempre o cliente vai ter instalado as fontes usadas no projeto e isso pode fazer com que os estilos dos textos não sejam aplicados corretamente, mas para resolver esses casos podemos preparar nossas fonts para web ou usar fontes da web.

Como usar fontes para web?

@font-face
@import
link

Referência
https://fonts.google.com/ https://css-tricks.com/snippets/css/using-font-face-in-css/

## Font Variant

Faz variações na apresentação da fonte

p {
	font-variant: small-caps;
}

https://developer.mozilla.org/en-US/docs/Web/CSS/font-variant

## Font Stretch

Alargamento ou encolhimento da fonte
Aceita palavras-chaves como: expanded, condensed, normal
Aceita porcentagens de 50% a 200%
Essa propriedade não vai funcionar em todas as fontes
+
p {
	font-stretch: expanded;
}

https://developer.mozilla.org/en-US/docs/Web/CSS/font-stretch

https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals

## Letter spacing

Define o espaçamento entre os caracteres
p {
	letter-spacing: 4px;
}

https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing

## Word spacing

Define o espaçamento entre palavras

p {
	word-spacing: 1em;
}

https://developer.mozilla.org/en-US/docs/Web/CSS/word-spacing

## Line height

Define os espaços entre linhas
Pode ser com unidades ou sem unidades de medida
Valores comuns: 1.5 ou 2

p {
	line-height: 1.5;
}

https://developer.mozilla.org/en-US/docs/Web/CSS/line-height

## Text transform

Transformação do texto
Valores podem ser: none | capitalize | uppercase | lowercase | full-width | full-size-kana

p {
	text-transform: uppercase;
}

https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform

## Text decoration

Aparência decorativa de um texto

line: underline | overline | line-through

podemos aplicar mais de 1 valor

style: wavy | dotted | double | dashed | solid

color: <color> values

h1 {
	text-decoration: underline; /* shorthand */
}

p {
  text-decoration: wavy overline blue; /* shorthand */
}

https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration

## Text align

Alinhamento de um texto

Valores: start | end | left | right | center | justify | match-parent

p {
	text-align: center;
}

https://developer.mozilla.org/en-US/docs/Web/CSS/text-align

## Text shadow

Sombra aplicada a um texto
Permite múltiplos valores

p {
  text-shadow: 1px 1px 1px red,
	       2px 2px 1px green; /* offset-x | offset-y | blur-radius | color */
}

https://developer.mozilla.org/en-US/docs/Web/CSS/text-shadow

## Shorthand

Podemos usar o shorthand font para determinar os seguintes valores: font-style, font-variant, font-weight, font-stretch, font-size, line-height e font-family

p {
  font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif;
}
