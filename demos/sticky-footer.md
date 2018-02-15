---
template: default.html
title: Footer Fixo
excerpt: Deixar seu footer fixado no final de sua página com conteúdo variável sempre foi algo trabalhoso. E se a altura do footer não for fixa, era basicamente impossível. Não é mais assim. 
---

<div class="Demo Demo--spaced">

Clique no botão abaixo para esconder o conteúdo desta página. Perceba como o footer gruda no final da janela mesmo quando não há conteúdo suficiente para preencher toda a página.

<button id="collapse-trigger" class="Button"><span class="icon-refresh u-spaceRS"></span> Alterar Conteúdo </button>

</div>

<div id="collapsable-content">

Deixar o footer fixado no final da página com conteúdo espalhado é algo que praticamente todo desenvolvedor web já tentou fazer em algum ponto de sua carreira. E, na maioria das dos casos, já é um problema resolvido. Ainda assim, todas as [soluções existentes](http://ryanfait.com/resources/footer-stick-to-bottom-of-page/) tem uma deficiência significativa &mdash; elas não funcionam se a altura do seu footer for desconhecida.

O Flexbox se encaixa perfeitamente nesse tipo de problema. Embora seja mais conhecido por alinhar conteúdo na direção horizontal, o Flexbox também funciona muito bem para problemas de layout na vertical. Tudo o que você precisa fazer é envolver as seções verticais em um container flex e escolher quais você quer expandir. Eles irão automaticamente tomar todo o espaço disponível no container.

No exemplo abaixo, o container tem como altura a altura total da janela, e a área de conteúdo irá se expandir conforme necessário. *(Nota: na direção vertical, você precisa especificar uma altura para o container, diferente da horizontal, que expande automaticamente para caber no espaço disponível.)*

## O HTML

```xml
<body class="Site">
  <header>…</header>
  <main class="Site-content">…</main>
  <footer>…</footer>
</body>
```

## O CSS

```css
.Site {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.Site-content {
  flex: 1;
}
```

Veja o [código fonte completo](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/site.css) para o componente `Site` usado nesse demo no Github.

<aside class="Notice"><strong>Nota:</strong>&nbsp; o CSS necessário para fazer esse demo funcionar em todos os browsers é levemente diferente do CSS mostrado no exemplo acima, que leva em consideração apenas browsers com suporte total à especificação Flexbox. Veja os  <a href="https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/site.css">comentários no código fonte</a> para mais detalhes.</aside>

</div>

<script class="js-allow-before-footer">
  (function() {
    var collapseTrigger = document.getElementById("collapse-trigger");
    var collapseableContent = document.getElementById("collapsable-content");
    var isCollapsed = false;
    collapseTrigger.addEventListener("click", function() {
      if (isCollapsed) {
        collapseableContent.classList.remove("u-hidden");
      } else {
        collapseableContent.classList.add("u-hidden");
      }
      isCollapsed = !isCollapsed;
    }, false);
  }());
</script>
