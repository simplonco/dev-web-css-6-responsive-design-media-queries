---
title: "CSS 6 : Responsive Design & Media queries - Solution"
show_toc: false
parent: "CSS 6 : Responsive Design & Media queries"
---


## Solution pas à pas

````stepper
# Démarrage

Je crée les fichiers `index.html` et `style.css` dans un dossier approprié.

# HTML

Je pose l'ensemble des éléments HTML dont je vais avoir besoin pour les trois versions.

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exercise | Responsive</title>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
</head>

<body>
    <nav>
        <a href="#" class="logo">Logo</a>
        <ul>
            <li>
                <a href="#" title="visit home page">
                    <i class="bi bi-house-fill"></i>
                    <span>Home</span>
                </a>
            </li>
            <li>
                <a href="#" title="visit Gallery page">
                    <i class="bi bi-images"></i>
                    <span>Gallery</span>
                </a>
            </li>
            <li>
                <a href="#" title="visit Contact page">
                    <i class="bi bi-envelope-fill"></i>
                    <span>Contact</span>
                </a>
            </li>
        </ul>
    </nav>
</body>

</html>
```


>💡 **À noter**  
>- L'utilisation des icônes bootstrap grâce aux tags `<i>`.  
>- Les textes des liens sont placés à l'intérieur de `<span>` pour pouvoir être manipulés via le CSS.  
>- La présence de l'attribut `title` sur les liens permet d'afficher un texte d'aide au survol de la souris. Il permettra également d'assurer un nom accessible aux liens pour les lecteurs d'écran lorsque le texte du lien est masqué.
{:.alert-info}

# Mobile first

Je réalise l'intégration de la vue mobile.

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    line-height: 1.5;
    background-color: grey;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
}

nav {
    position: fixed;
    inset: auto 0 0 0;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
    background-color: #A306B6;
    color: #fff;
}

nav>a.logo {
    display: none;
    color: inherit;
    text-decoration: none;
}

nav>ul {
    display: flex;
    list-style: none;
    padding: 0;
}

nav>ul>li>a {
    color: inherit;
    text-decoration: none;
    padding: 1rem;
}

nav>ul>li>a>i {
    font-size: 1.5em;
}

nav>ul>li>a>span {
    display: none;
}
```

>💡 **À noter** 
>- La propriété `inset` (ligne 14) sert à définir en une seule ligne les valeurs des propriétés `top`, `right`, `bottom` et `left`.
>- On utilise la propriété `display: none;` pour cacher le logo (ligne 24) et les textes des liens (ligne 46).
{:.alert-info}

# Tablet

J'ajoute les *media queries* pour la vue tablette en mode paysage.

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    line-height: 1.5;
    background-color: grey;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
}

nav {
    position: fixed;
    inset: auto 0 0 0;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
    background-color: #A306B6;
    color: #fff;
}

@media screen and (width >= 1024px) and (orientation: landscape) {
    nav {
        inset: 0 0 0 auto;
    } 
}

nav>a.logo {
    display: none;
    color: inherit;
    text-decoration: none;
}

nav>ul {
    display: flex;
    list-style: none;
    padding: 0;
}

@media screen and (width >= 1024px) and (orientation: landscape) {
    nav>ul  {
        flex-direction: column;
    } 
}

nav>ul>li>a {
    color: inherit;
    text-decoration: none;
    padding: 1rem;
}

nav>ul>li>a>i {
    font-size: 1.5em;
}

nav>ul>li>a>span {
    display: none;
}

@media screen and (width >= 1024px) and (orientation: landscape) {
    nav>ul>li>a>span  {
        display: initial;
    } 
}
```

>💡 **À noter**
>- L'ajout de *media query* n'ayant pas d'impact sur les spécificités, je prends soin de redéfinir les éléments **en-dessous de leur définition initiale** pour que les nouvelles valeurs soient correctement prises en compte par le navigateur.
>- J'ai choisi ici de répéter plusieurs fois, aux endroits les plus pertinents, la déclaration `@media screen and (min-width: 1024px) and (orientation: landscape)` pour faciliter la lecture du code et les mises à jour futures lorsque mon CSS aura beaucoup évolué.

J'aurais pu déclarer une seule fois le `@media screen …` pour l'ensemble des éléments, en fin de fichier par exemple. Mais ce type de placement est difficilement maintenable lorsque mes fichiers CSS contiennent beaucoup de lignes. Le risque étant de passer à côté de certaines spécificités.

Voici ce que j'aurais alors obtenu :
```css
/* ... */
nav>ul>li>a>i {
    font-size: 1.5em;
}

nav>ul>li>a>span {
    display: none;
}

@media screen and (width >= 1024px) and (orientation: landscape) {
    nav {
        inset: 0 0 0 auto;
    }
    nav>ul  {
        flex-direction: column;
    }
    nav>ul>li>a>span  {
        display: initial;
    }
}
```

# Desktop

Enfin, j'ajoute les *media queries* nécessaires à la vue ordinateur en continuant d'écrire en-dessous des points de rupture précédents.

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    line-height: 1.5;
    background-color: grey;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
}

nav {
    position: fixed;
    inset: auto 0 0 0;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
    background-color: #A306B6;
    color: #fff;
}

@media screen and (width >= 1024px) and (orientation: landscape) {
    nav {
        inset: 0 0 0 auto;
    } 
}

@media screen and (width >= 1200px) {
    nav {
        inset: 0 0 auto 0;
        justify-content: space-between;
    } 
}

nav>a.logo {
    display: none;
    color: inherit;
    text-decoration: none;
}

@media screen and (width >= 1200px) {
    nav>a.logo {
        display: initial;
    }
}

nav>ul {
    display: flex;
    list-style: none;
    padding: 0;
}

@media screen and (width >= 1024px) and (orientation: landscape) {
    nav>ul  {
        flex-direction: column;
    } 
}

@media screen and (width >= 1200px) {
    nav>ul {
        flex-direction: row;
    } 
}

nav>ul>li>a {
    color: inherit;
    text-decoration: none;
    padding: 1rem;
}

nav>ul>li>a>i {
    font-size: 1.5em;
}

@media screen and (width >= 1200px) {
    nav>ul>li>a>i  {
        display: none;
    } 
}

nav>ul>li>a>span {
    display: none;
}

@media screen and (width >= 1024px) and (orientation: landscape) {
    nav>ul>li>a>span  {
        display: initial;
    } 
}
```
````

## Conclusion

L'approche _**mobile first**_ permet de concevoir et d'organiser son CSS de manière itérative et structurée. Elle permet aussi de limiter le nombre de lignes nécessaires à l'intégration tout en garantissant le résultat final attendu.

