---
path: centrer-element-absolute-fixed
date: 2020-06-29T11:53:51.074Z
title: Centrer un élément en position absolute ou fixed en CSS
description: Nous allons voir comment utiliser translate à notre avantage pour
  centrer un élément positionné en absolute ou fixed.
---
Centrer un élément est devenu trivial avec les outils mis à disposition par CSS, que ce soit Flexbox ou CSS Grid, quelle époque on vie!

Mais il y a un cas de figure où centrer un élément sur la page peut encore être problématique. Dans le cas d’un élément à positionner en `absolute` ou `fixed` et dont on ne connaitrais pas la taille à l’avance, il est possible d’utiliser cette technique:

```css
.wrapper {
  position: relative;
  width: 1000px;
}

.item {
  left: 50%;
}
```

Pour centrer mon élément `.item`, je vais commencer par le placer à 50% de la gauche de `.wrapper` . Le problème, c’est que c’est le pixel le plus en haut à gauche de mon élément `.item`qui va se retrouver aligné à 50% du conteneur.

> La propriété `left` place l’élément relativement au plus proche parent relative ou absolute de l’élément ciblé.   

En revanche, si on écris

```css
.wrapper {
  position: relative;
  width: 1000px;
}

.item {
  left: 50%;
	transform: translateX(-50%);
}
```

La transformation `translate` va se baser sur 50% de l’élément en lui même. On va décaler `.item`  à 50% de la gauche de `.wrapper` avant de le déplacer à nouveau vers la gauche de 50% de la taille de `.item`.  Notre élément est parfaitement centré!