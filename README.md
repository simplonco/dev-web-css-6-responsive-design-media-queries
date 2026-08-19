---
title: "CSS 6 : Responsive Design & Media queries"
description: "Des mises en pages adaptées à tous les supports. Découvre les objectifs et la pratique du responsive design."
show_toc: true
---

## Objectifs

* Comprendre ce que sont les *media queries*
* Découvrir comment tu peux les utiliser pour modifier ta mise en page
* Comprendre le concept du **mobile first**

## Introduction

Aux débuts d'Internet, les pages web étaient conçues pour des tailles d'écran très spécifiques.
Aujourd'hui, **nous avons tous des tailles d'écran différentes**, même nos **smartphones sont tous de tailles différentes**.

C'est pour résoudre ce problème spécifique que le *responsive web design* (design web réactif) a été inventé.
Le *responsive web design* **est un ensemble de pratiques** qui **permet aux pages web de changer leur mise en page pour s'adapter à des tailles d'écran différentes**.

Dans cette ressource, nous parlerons de ce qu'est le *responsive web design* et **de la façon dont tu peux appliquer ces pratiques à tes sites web**.

![](images/desk-responsive.png)

## L'histoire des différentes mise en page des sites web

Avant que le concept de sites web réactifs n'existe, il n'y avait que deux façons de concevoir un site web.

* Créer une mise en page fixe (les sites web ont une taille fixe)

![](images/fixed-layout.gif)

* Créer une mise en page **liquide** (les sites web ont une taille en % qui s'adapte à la largeur de l'écran)

![](images/fluid-layout.gif)
Source : [https://medium.com/@space.alpaca/so-what-exactly-is-the-difference-between-fixed-fluid-adaptive-and-responsive-layouts-and-why-3773272d8481](https://medium.com/@space.alpaca/so-what-exactly-is-the-difference-between-fixed-fluid-adaptive-and-responsive-layouts-and-why-3773272d8481)

Le *responsive design* a été créé pour résoudre les problèmes des dispositions fixes et liquides.

## Responsive Design

Le terme "*responsive design*" (conception réactive ou adaptative) **ne se réfère pas à une technologie spécifique**. Il fait plutôt référence à un **ensemble d'outils et de pratiques pour créer des mises en page** qui "s'adaptent" à la **taille des écrans**.
Le terme "*responsive design*" a été apposé par [Ethan Matcotte](https://ethanmarcotte.com/) en 2010.

![](images/responsive.jpeg)

## Mobile-first

Un concept qui est également apparu avec le *responsive design* (et surtout à la "révolution mobile") est le concept de **mobile-first.**

La philosophie du *mobile-first* est de toujours commencer à travailler sur la version **mobile avant de construire la version de bureau.**

Non seulement les utilisateurs **auront une meilleure expérience sur mobile**, mais **il est également plus facile de commencer à travailler sur une version mobile.**

>💡 **Illustrons ce concept**.  
>Imagine que tu vives dans une petite pièce (quelques mètres carrés). Si tu dois déménager dans un appartement plus grand, il te sera bien plus facile de déplacer toutes tes affaires depuis un espace plus petit vers un espace plus grand que l'inverse.

C'est la même chose pour le **design réactif.**

La plupart des utilisations d'Internet se font à partir d'un appareil mobile, il est donc crucial d'avoir une excellente version mobile de ton site web !

![](images/mobile-internet-usage.jpg)
*source :* [https://www.broadbandsearch.net/blog/mobile-desktop-internet-usage-statistics](https://www.broadbandsearch.net/blog/mobile-desktop-internet-usage-statistics)

Aujourd'hui, avoir une **bonne version mobile** peut **améliorer considérablement la visibilité sur les moteurs de recherche.**
Par exemple, **Google donnera un rang à ton site web** en vérifiant si celui-ci est **mobile-friendly** et lui attribuant si c'est le cas **une meilleure visibilité sur le moteur de recherche.**

👉 [Adaptabilité au téléphone portable](https://developer.mozilla.org/en-US/docs/Web/Guide/Mobile/Mobile-friendliness)  
Un bel article de MDN sur l'adaptabilité des sites aux téléphones portables
{:.alert-info}

## Comment coder une page web responsive

### La balise meta viewport

Pour indiquer au navigateur que ta page s'adapte à tous les appareils, tu dois ajouter une balise *meta* dans le `<head>` de ton document :

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

Ici, nous indiquons au navigateur d'utiliser 100% de la largeur disponible de l'écran et d'appliquer un niveau de grossissement à 1 (c'est-à-dire aucun zoom avant ni arrière au chargement).


👉 [Utilisation de la balise meta viewport](https://developer.mozilla.org/fr/docs/Web/HTML/Viewport_meta_tag)
{:.alert-info}

![](images/viewport-meta.png)
*Source :* [https://developers.google.com/search/mobile-sites/mobile-seo/responsive-design](https://developers.google.com/search/mobile-sites/mobile-seo/responsive-design)

### Media queries

Les *media queries* permettent de modifier la mise en page en fonction de la taille du **viewport**.
Ce que nous appelons viewport est **la taille de la fenêtre**.

En utilisant les *media queries*, tu peux décider de réorganiser certains éléments de ta page web en fonction de la taille de la fenêtre.

![](images/media-queries.png)
*Source :* [https://hackernoon.com/introduction-to-css-media-queries-xu3t3vxc](https://hackernoon.com/introduction-to-css-media-queries-xu3t3vxc)

La syntaxe d'une *media query* ressemble à ceci :

```css
@media <media_type> and (<media_features>) {

/* put your CSS here */

}
```

### Types de *media*

Le `<media_type>` décrit la catégorie d'appareil. Voici une liste des différents **types de media** que tu peux utiliser :

* `all` : appliquer la règle à tous les types d'appareils.

* `print` : utilisé pour un document destiné à être imprimé (papier)

* `screen` : utilisé pour tous les types d'écran.

* `speech` : pour les synthétiseurs de parole

Le **plus utilisé** est généralement `screen`.

### Caractéristiques media

Ensuite, à la place de `<media_features>`, tu peux écrire des règles pour lesquelles la media query sera appliquée.
Les *features* les plus courantes sont la largeur minimale `min-width` et la largeur maximale `max-width`.


👉 [CSS @media Rule](https://www.w3schools.com/cssref/css3_pr_mediaquery.asp)  
Tu trouveras ici la définition et les règles d'utilisation des *media queries*
{:.alert-info}

Voici un exemple de *media queries* avec toutes les propriétés :

```css
@media screen and (max-width: 600px) { 
  .menu { 
    display: none; 
  } 
}

//écriture alternative 
@media screen and (width <= 600px) { 
  .menu { 
    display: none; 
  } 
}
```

Cette *media query* vérifie si la page web est affichée sur un écran, et si la largeur de la fenêtre de visualisation est inférieure à **600px.**
Si la condition est vraie, alors la règle CSS est appliquée et l'élément `.menu` change en `display : none.`

Ouvre la démo sur Codesandbox et déplace la taille de l'écran ; le menu devrait disparaître lorsque la taille de l'écran est inférieure à **600px**.

[Codesandbox - Media query demo](https://codesandbox.io/s/restless-waterfall-do0wo?file=/style.css:192-195)

Il existe plein d'autres options possibles pour spécifier certaines situations telles que l'**orientation portrait ou paysage** du média (orientation), **la résolution**, si le type d'**affichage est monochrome**, etc. Consulte la page suivante pour des explications détaillées.

👉 [Les media features](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_media_queries/Using_media_queries#caract%C3%A9ristiques_m%C3%A9dia_media_features)
{:.alert-info}

### 🔬 Expérience

Maintenant, essaie de réarranger ces trois blocs en utilisant les *media queries*. Lorsque la taille de l'écran est inférieure à 600px, les blocs doivent être en `display:block` et prendre toute la largeur (100%).

[Codesandbox - Exercice media queries](https://codesandbox.io/s/zen-keldysh-ol0g9?file=/style.css)

<details markdown="1">
<summary>Voir la solution</summary>

```css
@media screen and (max-width: 600px) {
  .boxes {
    display: block;
    width: 100%;
  }
}
```

</details>

## Points de rupture

Dans la *responsive design*, un point de rupture (ou *breakpoint*) est un point auquel la *media query* se déclenche (et la mise en page s'adapte). Dans l'exemple précédent, tu as utilisé 600px comme point de rupture.

Nous ne voulons pas que les éléments changent tout le temps pour un grand nombre d'écrans différents.
Ton site web ne devrait changer que sur les **points d'arrêt** principaux (ex : lorsque le site passe d'un écran de bureau à la tablette, *etc.*)

Voici les tailles d'écran les plus utilisées :

* **Mobile en portrait** (320px à 414px) - Pour les appareils avec des écrans de 4" à 6,9".
* **Mobile en paysage** (568px à 812px) - Idem, mais en paysage.
* **Tablette en portrait** (768px à 834px) - Pour les appareils de 7" à 10".
* **Tablette en paysage** (1024px à 1112px) - Idem, mais aussi tablettes 12" en portrait.
* **Ecrans d'ordinateurs portables et de bureau** (>1200px) - Varie beaucoup, mais généralement de 1200px et plus.

![](images/breakpoints.jpg)
*Source : Pinterest* [https://in.pinterest.com/pin/370421138093022328/](https://in.pinterest.com/pin/370421138093022328/)

## Images

Un autre concept important en *responsive design* est celui des **images**.
Nous voulons aussi que les images s'adaptent à la taille de l'écran.

Nous pouvons utiliser ce code pour nous assurer que l'élément image ne prend pas plus de 100% de la taille du parent :

```css
max-width: 100%;
height: auto;
```

### 🔬 Expérience

Cette image de chat est trop grande : utilise la technique que nous venons d'apprendre pour l'adapter à la taille de la fenêtre de visualisation.

[Codesandbox - Exercice images](https://codesandbox.io/s/agitated-vaughan-75xsr)

{% capture my_html %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Static Template</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1>
      Make the cat fit the viewport
    </h1>
    <img
      src="/images/cat.jpg"
      alt=""
      class="img-cat"
    />
  </body>
</html>

{% endcapture %}

{% capture my_css %}

{% endcapture %}

{% include playground.html
  id="demo_cat"
  initial_html=my_html
  initial_css=my_css
%}

<details markdown="1">
<summary>Voir le code</summary>

Des problèmes pour trouver la solution ?

```css
.img-cat {
  max-width: 100%;
  height: auto;
}
```

</details>

## Résumé

* Le *responsive design* est un **ensemble de pratiques** utilisées pour **créer une mise en page qui "répond" (s'adapte) aux contraintes de l'appareil**
* Le principe du ***mobile-first*** est un principe important lié au *responsive design*. Ce principe signifie que tu dois toujours **démarrer la construction de la version mobile** de ton site web **avant la version pour bureau**
* Tu peux écrire des *media queries* pour appliquer des **règles CSS spécifiques** à certaines **tailles d'écran**

## Ressources

<div class="alert-info" markdown="1">
[Responsive design - Meilleures pratiques et considérations](https://www.toptal.com/designers/responsive/responsive-design-best-practices)
Un bel article sur les meilleures pratiques en matière de *responsive design*.
</div>

## Challenge

En utilisant les *media queries*, essaie de reproduire l'intégration de la barre de navigation représentée ci-dessous.

![Challenge responsive](images/challenge-responsive.png)

### Consignes

- L'intégration doit être faite pour trois tailles d'écran, soit deux points de ruptures (1024 et 1200px), comme suit :
  - **Mobile portrait ou paysage** pour une largeur inférieure à 1024px. Servira aussi pour les tablettes en orientation portrait.
  - **Tablette en orientation paysage** et une largeur d'écran supérieure à 1024px
  - **Ordinateur** et une largeur supérieure à 1200px
- Pour les trois versions, la barre de navigation est fixe.
- Version **mobile** : seules les icônes sont visibles. La barre est fixée en pied de fenêtre
- Version **tablette** : les icônes ainsi que les textes des liens sont visibles. La barre est fixée à droite de l'écran
- Version **ordinateur** : les icônes sont cachées mais les textes des liens sont visibles ainsi que le logo. La barre de navigation est fixée en haut de la fenêtre.

### Tips
- Essaie de réaliser ton CSS dans une approche _**mobile first**_
- Code pour le violet : #A306B6.
- Icônes : tu peux utiliser la [bibliothèque d'icônes Bootstrap Icons](https://icons.getbootstrap.com/) qui s'intègre en ajoutant ce code dans la partie `<head>` de la page :

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
```

---

[Voir la solution](solution){:.alert-info}