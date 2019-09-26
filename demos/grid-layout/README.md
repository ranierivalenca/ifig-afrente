# Recomendações 
Recomendo forte mente usar o FireFox para trabalhar com Grid, pois a Mozilla adicionou uma feature muito interessante que ao abrir as Ferramenta de Desenvolvedor do FireFox você pode solicitar ao inspetor que sobreponha uma representação do grid.

Quando um elemento da page possui a propriedade `display: grid;` um ícone grid aparece ao seu lado.

<img src="https://1.bp.blogspot.com/-Z5N_3WQ9EHA/XYFfHdiFNtI/AAAAAAAARH8/7mjy-H0Dor8k85oMdzPkfJbnG0bQczR1wCLcBGAsYHQ/s1600/Peek%2B2019-09-17%2B19-27.gif" alt="Banana" />


#  Proprieades

Existem dois tipo de propriedade no grid, as propriedade do grid container e do grid item. Container é o elemento que envolve uma serie de outros elemento logo ele chamamos ele de "elemento pai" e os elementos contido nele de "elementos filho".
```
<div class="container"> // Pai
  <header class="filho">Header</header> //Filho
  <main class="main">Main</main> // Filho
  <aside class="aside">Aside</aside> // Filho
  <footer class="footer">Footer</footer> // Filho
</div>
```


## Container 

> ## *display: grid;*
> Define o elemento como um grid container.

É criado um grid com uma coluna, e suas linhas são geradas automaticamente dia acordo com a quantidade de itens(elementos filhos) do grid.
```
.container {
  display: grid;
}
```

> ## *grid-template-columns*
>  Define o número total de colunas que serão criadas no grid.

Conforme digitamos os valores as colunas são criadas.
```
.container {
  display: grid;
  grid-template-columns: 200px 200px; // criamos duas colunas de 200px
} 
```
Uma novo unidade de medida veio com o Grid Layout o `fr`. fr é uma unidade fracional.
```
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 3fr; 
  //três colunas são criadas sendo que a segunda tem o dobro da primeira e a terceira o triplo
```
Imagina se quisermos criar um grid com 100 colunas teríamos que digitar 100 valores? não, por que ganhamos a função `repeat()`.

```
.container {
  display: grid;
  grid-template-columns: repeat(100, 200px); 
  // o primeiro valor é a quantidade de colunas e o segundo o tamanho. 
}

.container {
  display: grid;
  grid-template-columns: repeat(2, 200px) 100px repeat(5, 1fr); 
  // duas colunas de 200px uma de 100 e uma 5 de 1fr; 
}
```
`ninmax()` essa é outra função muito legal, que permite definir um tamanho mínimo e máximo.

```
.contaier {
  display: grid;
  grid-template-columns: minmax(200px, 400px) minmax(100px, 500px);
  // Primeiro o valor mínimo em seguida o valor máximo.
  // Ou seja a primeira coluna tem no mínimo 200px e consegue se expandir até no máximo 400px;
}
 .container {
   display: grid;
   grid-template-columns: repeat(4, mimax(200, 400));   
 }
```
> ## *grid-template-rows*
> Define a quantidade de linhas no grid. 
> 
Basicamente funciona da mesma forma. E todas as outras funções citadas no `grid-template-columns` funcionam aqui também.

```
.container {
  display: grid;
  grid-template-rows: 200px 200px 200px // cria três linhas de 200px
 }
```

> ## *grid-gap*
> Define o espaçamento  entre os elementos(linhas/colunas) do grid.

`grid-gap` é short cut para as propriedade `grid-column-gap` e `grid-row-gap`. 
```
.container {
  display: grid;
  grid-template-columns: repeat(4, 200px);
  grid-template-rows: repeat(4, 1fr);
  // Se passar apenas um valor o mesmo espaçamento sera aplicado para as linhas e colunas.
  grid-gap: 20px;
 }

.container {
  display: grid;
  grid-template-columns: repeat(4, 200px);
  grid-template-rows: repeat(4, 1fr);
  // Se passar dois o primeiro define os espaçamentos entre as linhas e outra das colunas.
  grid-gap: 10px  30px;
 }

.container {
  display: grid;
  grid-template-columns: repeat(4, 200px);
  grid-template-rows: repeat(4, 1fr);
  grid-column-gap: 20px;
  grid-row-gap: 20px;
 }
```
> ## *grid-template-areas*
> Define áreas específicas no grid. O ponto (.) pode ser utilizado para criar áreas vazias

Essa é cereja do bolo do grid, com essa propriedade  a gente consegue definir um layout base para o nosso grid, especificando onde cada elemento vai ser posicionado.


```
.container {
  dilsplay: grid;
  grid-template-areas: 
  //Isso poderia estar tudo em uma linha eu organizei assim pra ficar mais fácil a leitura.
    "header  header header"
    "aside   aside  main"
    "footer  footer footer
;
```

Cada `""` representa uma linha, e os nomes dentro delas representa as colunas que são separados por espaços, e claro você pode definir qualquer nome.

Mas e agora como faço pra usar esse esquema feito acima? Precisamos falar com os grid itens.

 ## *Alinhamento*
Essas propriedades só funciona se o container tiver espaço sobrando.

>## *justify-content*
> Justifica os itens do grid em relação ao eixo X.

```
.container {   
  display: grid;
  justify-content: start // Justifica os itens ao início.
  justify-content: end // Justifica os itens ao final.
  justify-content: stretch // Estica os itens.
  justify-content: space-around // Distribui espaço entre os elementos.
  justify-content: space-between // Cria um espaço entre os elementos, ignorando o início e  final.
  justify-content: space-evenly // Cria um espaço igual entre as colunas.
  justify-content: center // Centraliza o conteúdo.
}
```
>## *align-content*
> Alinha os itens do grid em relação ao eixo y

```
.container {
  display: grid;
  align-content: start // Justifica os itens ao início.
  align-content: end // Justifica os itens ao final.
  align-content: stretch // Estica os itens.
  align-content: space-around // Distribui espaço entre os elementos.
  justify-content: space-between // Cria um espaço entre os elementos, ignorando o início e  final.
  align-content: space-evenly // Cria um espaço igual entre as colunas.
  align-content: center // Centraliza o conteúdo.
 }
```
> ## *justify-items*
> Justifica o conteúdo dos itens do grid em relação ao eixo X. Justifica em relação a célula.

```
.container {
  display: gird;
  justify-items:  start // Justifica os itens ao início.
  justify-items:  end // Justifica os itens ao final.
  justify-items:  center // Centraliza o conteúdo.
  justify-items:  stretch // Estica os itens.
 }
```

>## *align-items*
> Alinha o conteúdo dos itens do grid em relação ao eixo Y. Alinha em relação a célula.

```
.container {
 align-items: start// Alinha os itens ao início.
 align-items: end // Alinha os itens ao final.
 align-items: center // Centraliza o conteúdo.
 align-items: stretch // Estica os itens.
}
```

## Grid itens

> ## *grid-area*
> Define a área do item do grid. 
> 
Lembra do grid-template-areas lá em cima? bom é com essa propriedade que definimos a área onde queremos posicionar um grid item.

```
.main {
  grid-area: header;
}
```

> ## *grid-column* 
> Define quais colunas serão ocupadas pelo grid item. 
> 
Uma boa hora pra ativar a opção **Diplay line numbers** do firefox FireFox.
<img src="https://1.bp.blogspot.com/-zOQUTytNQ50/XYqNJ-OQUUI/AAAAAAAARI4/qvbspPRCPZoA9fiwOuCZc39SREbrC1lxwCLcBGAsYHQ/s1600/Screenshot_2019-09-24%2BGRID%2BLayout.png">

Com isso podemos viabilizar as colunas e fica bem mais fácil posicionar.

```
.header {
  grid-column: 1 / 3 // O primeiro valor indica a coluna de onde o item vai começar e o segundo a coluna onde ele vai terminar.
  grid-column: 1; // item vai ocupar a coluna 1;
  grid-column: span 2 // apartir da coluna que item estiver ele vai se espadir para mais duas colunas
```
Se prefirir pode setar esses valores individualmente usando as propriedades grid `grid-column-start` e 
`grid-column-end`.

```
.main {
  grid-column-start: 1; // vai começar na coluna 1
  grid-column-end: 2; // termina na coluna 2
}
```

> ## *grid-row*
> Define quais linhas serão ocupadas pelo grid item.

Tem as mesma propriedade.

```
.header {
  grid-row: 1 / 3 // O primeiro valor indica a linha de onde o item vai começar e o segundo a linha onde ele vai terminar.
  grid-row: 1; // item vai ocupar a linha 1;
  grid-row: span 2 // apartir da linha que item estiver ele vai se espadir para mais duas linhas
```

```
.main {
  grid-column-start: 1; // vai começar na linha 1
  grid-column-end: 2; // termina na linha 2
}
```

  ## Alinhamento
 
 >## *justify-self*
>Justifica o item do grid em relação ao eixo X. Justifica em relação a célula.
 
```
.main {
 justify-self: start // Justifica o item ao início.
 justify-self: end // Justifica o item ao final.
 justify-self: center // Centraliza o conteúdo.
 justify-self: stretch // Estica o item.
}
```

>## *align-self*
> Justifica o item do grid em relação ao eixo y (vertical). Alinha em relação a célula.

```
.main {
 align-self: start // Alinha o item ao início.
 align-self: end // Alinha o item ao final.
 align-self: center // Centraliza o conteúdo.
 align-self: stretch // Estica o item.
}
```

## Fontes
<a href="https://www.origamid.com/projetos/css-grid-layout-guia-completo/">Origamid</a>
<a href="https://css-tricks.com/snippets/css/complete-guide-grid/">CSS Tricks</a>
