---
template: default.html
title: Grids melhores e mais simples
excerpt: Flexbox nos dá a maior parte dos recursos que queremos de um sistema de grid de forma simples. E tamanho e alinhamento estão apenas uma ou duas propriedades de distância.
---

A maioria dos sistemas de grid hoje utilizam dois métodos de layout: `float` ou `inline-block`. Mas nenhum desses métodos foram realmente planejados para serem usados para layout e, como resultado, trazem alguns problemas e limitações.

Usar floats requer limpá-los periodicamente (NT: como `clear: both`) o que traz toda uma série de problemas de layout, mais notadamente que limpar um elemento muitas vezes o move para uma parte não relacionada da página (veja esse [bug do Bootstrap](https://github.com/twbs/bootstrap/issues/295#issuecomment-2282969) como exemplo). Também, limpar floats geralmente requer utilizar os pseudo-elementos `before` e `after`, impossibilitando assim que você os utilize para outras coisas.

Layouts com `inline-block` precisam lidar com o problema de [espaço em branco entre itens com inline-block](http://css-tricks.com/fighting-the-space-between-inline-block-elements/), e todas as [soluções](http://davidwalsh.name/remove-whitespace-inline-block) para esse problema se utilizam de [hack](https://github.com/suitcss/components-grid/blob/master/lib/grid.css#L30) e são [irritantes](https://twitter.com/thierrykoblentz/status/305152267374428160).

O Flexbox não só elimina esses problemas como também abre um novo mundo de possibilidades.

## Características de um Grid com Flexbox

Sistemas de grid geralmente vêm com uma grande quantidade de opções de dimensionamento dos elementos, mas na maior parte das vezes você vai apenas usar dois ou três elementos lado a lado. Dado isso, por que deveríamos colocar classes de tamanhos em cada célula desse grid?

Listados abaixo estão alguns dos meus critérios para um sistema de grid ideal. Felizmente, com Flexbox nós temos todos esses recursos de graça.

- Por padrão, cada célula do grid tem a mesma largura e altura de qualquer outra célula na mesma linha. Basicamente, todas elas se encaixam automaticamente por padrão.
- Para um controle mais refinado, você pode adicionar classes de tamanho em células individuais. Sem essas classes, elas apenas dividirão o espaço disponível entre si.
- Para grids responsivos, você pode adicionar classes específicas de media query às células.
- Células individuais podem ser alinhadas verticalmente ao topo, à base ou ao meio.
- Quando você quiser que todas as células em um grid tenham o mesmo tamanho ou alinhamento, deveria ser possível adicionar apenas uma classe ao container para evitar repetição desnecessária.
- Grids podem ser aninhados por quantos níveis forem necessários.

### Grids Básicos

As células de grids abaixo não especificam nenhuma largura, elas naturalmente tomam o espaco disponível entre si e se expandem para caber na linha inteira. Elas também tem altura igual por padrão.

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">1/2</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/2</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">1/3</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/3</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/3</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
</div>

<div class="Grid Grid--gutters Grid--flexCells">
  <div class="Grid-cell">
    <div class="Demo">
      Altura total, mesmo quando o conteúdo não preenche todo o espaço.
    </div>
  </div>

  <div class="Grid-cell">
    <div class="Demo">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum mollis velit non gravida venenatis. Praesent consequat lectus purus, ut scelerisque velit condimentum eu. Maecenas sagittis ante ut turpis varius interdum. Quisque tellus ipsum, eleifend non ipsum id, suscipit ultricies neque.
    </div>
  </div>
</div>

### Dimensionamento Individual

Quando você não quiser larguras iguais, você pode adicionar classes de tamanho às células. Células sem classes de tamanho simplesmente dividirão o espaço disponível entre si.

As células abaixo marcadas com "auto" não utilizam classes de tamanho.

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell u-1of2">
    <div class="Demo">1/2</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
  <div class="Grid-cell u-1of3">
    <div class="Demo">1/3</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell u-1of4">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
  <div class="Grid-cell u-1of3">
    <div class="Demo">1/3</div>
  </div>
</div>

### Responsividade

Grids Responsivos funcionam adicionando "media classes" às células ou aos containeres dessas células. Quando os valores definidos por essas classes forem válidos, os grids se ajustarão de acordo com o definido.

As células abaixo devem ter largura total por padrão e devem se encaixar umas com as outras acima de  `48em`. Redimensione seu browser para ver isso em ação.

<div class="Grid Grid--gutters Grid--full large-Grid--fit u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">Total / Metade</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">Total / Metade</div>
  </div>
</div>
<div class="Grid Grid--gutters Grid--full large-Grid--fit u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">Total / Um terço</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">Total / Um terço</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">Total / Um terço</div>
  </div>
</div>

### Grids aninhados

Componentes de grid são aninháveis infinitamente dentro de outros componentes de grid.

<div class="Grid Grid--gutters Grid--flexCells u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">
      <div class="Grid Grid--gutters u-textCenter">
        <div class="Grid-cell u-1of3">
          <div class="Demo">1/3</div>
        </div>
        <div class="Grid-cell">
          <div class="Demo">
            <div class="Grid Grid--gutters u-textCenter">
              <div class="Grid-cell">
                <div class="Demo">1/2</div>
              </div>
              <div class="Grid-cell">
                <div class="Demo">1/2</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="Grid-cell u-1of3">
    <div class="Demo">1/3</div>
  </div>
</div>

## Recursos de Alinhamento

### Células alinhadas ao topo

<div class="Grid Grid--gutters Grid--top">
  <div class="Grid-cell">
    <div class="Demo">
      Essa célula deve ser alinhada ao topo.
    </div>
  </div>
  <div class="Grid-cell u-1of2">
    <div class="Demo">
      Pellentesque sagittis vel erat ac laoreet. Phasellus ac aliquet enim, eu aliquet sem. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed pulvinar porta leo, eu ultricies nunc sollicitudin vitae. Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh.
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Essa célula deve ser alinhada ao topo.
    </div>
  </div>
</div>

### Células alinhadas à base

<div class="Grid Grid--gutters Grid--bottom">
  <div class="Grid-cell">
    <div class="Demo">
      Essa célula deve ser alinhada à base.
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh. Ut interdum ligula id metus hendrerit cursus. Integer eu leo felis. Aenean commodo ultrices nunc, sit amet blandit elit gravida in.
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Essa célula deve ser alinhada à base.
    </div>
  </div>
</div>

### Células alinhadas verticalmente

<div class="Grid Grid--gutters Grid--center">
  <div class="Grid-cell">
    <div class="Demo">
      Essa célula deve ser centralizada verticalmente com a célula à direita.
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh. Ut interdum ligula id metus hendrerit cursus. Integer eu leo felis. Aenean commodo ultrices nunc, sit amet blandit elit gravida in. Sed est ligula, ornare ac nisi adipiscing, iaculis facilisis tellus. Nullam vel facilisis libero. Duis semper lobortis elit, vitae dictum erat.</div>
  </div>
</div>

### Alinhamento Vertical Misto

<div class="Grid Grid--gutters">
  <div class="Grid-cell Grid-cell--top">
    <div class="Demo">
      Essa célula deve ser alinhada ao topo.
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh. Ut interdum ligula id metus hendrerit cursus. Integer eu leo felis. Aenean commodo ultrices nunc, sit amet blandit elit gravida in. Sed est ligula, ornare ac nisi adipiscing, iaculis facilisis tellus.</div>
  </div>
  <div class="Grid-cell Grid-cell--center">
    <div class="Demo">
      Essa célula deve ser centralizada.
    </div>
  </div>
  <div class="Grid-cell Grid-cell--bottom">
    <div class="Demo">
      Essa célula deve ser alinhada à base.
    </div>
  </div>
</div>

## O HTML

```html
<div class="Grid">
  <div class="Grid-cell">…</div>
  <div class="Grid-cell">…</div>
  <div class="Grid-cell">…</div>
</div>
```

## O CSS

### Estilos Básicos do Grid

```css
.Grid {
  display: flex;
}

.Grid-cell {
  flex: 1;
}
```

### Modificadores de Estilo do Grid

```css
/* Com espaçamentos entre as células */
.Grid--gutters {
  margin: -1em 0 0 -1em;
}
.Grid--gutters > .Grid-cell {
  padding: 1em 0 0 1em;
}

/* Alinhamentos por linha */
.Grid--top {
  align-items: flex-start;
}
.Grid--bottom {
  align-items: flex-end;
}
.Grid--center {
  align-items: center;
}

/* Alinhamentos por célula */
.Grid-cell--top {
  align-self: flex-start;
}
.Grid-cell--bottom {
  align-self: flex-end;
}
.Grid-cell--center {
  align-self: center;
}
```

### Modificadores Responsivos (uma abordagem mobile-first)

```css
/* Classes de base para todas as resoluções */
.Grid--fit > .Grid-cell {
  flex: 1;
}
.Grid--full > .Grid-cell {
  flex: 0 0 100%;
}
.Grid--1of2 > .Grid-cell {
  flex: 0 0 50%
}
.Grid--1of3 > .Grid-cell {
  flex: 0 0 33.3333%
}
.Grid--1of4 > .Grid-cell {
  flex: 0 0 25%
}

/* Telas pequenas a médias */
@media (min-width: 24em) {
  .small-Grid--fit > .Grid-cell {
    flex: 1;
  }
  .small-Grid--full > .Grid-cell {
    flex: 0 0 100%;
  }
  .small-Grid--1of2 > .Grid-cell {
    flex: 0 0 50%
  }
  .small-Grid--1of3 > .Grid-cell {
    flex: 0 0 33.3333%
  }
  .small-Grid--1of4 > .Grid-cell {
    flex: 0 0 25%
  }
}

/* Telas grandes */
@media (min-width: 48em) {
  .large-Grid--fit > .Grid-cell {
    flex: 1;
  }
  .large-Grid--full > .Grid-cell {
    flex: 0 0 100%;
  }
  .large-Grid--1of2 > .Grid-cell {
    flex: 0 0 50%
  }
  .large-Grid--1of3 > .Grid-cell {
    flex: 0 0 33.3333%
  }
  .large-Grid--1of4 > .Grid-cell {
    flex: 0 0 25%
  }
}
```

Veja o [código fonte completo](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/grid.css) para o componente `Grid` usado nesse demo no Github.
