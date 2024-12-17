# Checklist Accessibilité

## Pour des applications riches et accessibles

#### 1. Taille du texte

Préférez les tailles relatives, en `rem` plutôt qu'en `px`

#### 2. Vérifier le ratio

- Est-ce que le site respecte le contraste avec ratio de 3:1  
  -> https://contrast-ratio.com/
- Sinon, générer une palette accessible  
  -> http://colorsafe.co/

#### 3. Libélés explicites des liens

- Les `title` des `<a>` -> Ex un bouton avec écrit "accès à votre suivi de commande"
- Les logiciels de revue d'écran lisent le `aria-label` ou le `title` et parfois les 2 selon la configuration du logiciel. Mettre le title seulement s'il apporte une information complémentaire et non redondante avec le libellé

#### 4. Text alternatif

- `alt="" des images`

#### 5. Alternative aux éléments sonores

- Utilisez <track> pour intégrer des sous-titres synchronisés aux vidéo via des fichiers [WebVTT](http://edutechwiki.unige.ch/fr/WebVTT) -> supportent plusieurs langues
- Appliquez des styles via CSS externe

#### 6. Ouverture dans une nouvelle fenetre

Rendre explicite l'ouverture dans le title

```html
<a href="#" target="_blank" title="Ouverture dans une nouvelle fenêtre">Mon lien</a>
```

#### 7. Langue

Indiquer la langue du site dans le head `<htlm lang="fr>` 
et s'il y a un mot en anglais ajouter un `<span lang="en">Hello World !</span>`

#### 8. Roles

Définir les rôles des pages pour les lecteurs d'écran, plus spécifiquement les Blocks sémantiques, en limitant le nombre de découpage en DIV inutiles

```txt
role="banner" - dans header
role="main" - dans main
role="content-info" - dans footer
role="search"
role="navigation" - dans chaque nav
role="form" - pour les formulaire
```

#### 9. Rendre accessible les formulaires

Pour que le lecteur d'écran puisse lire le label, on a besoin du `for` associé à un champs

```html
Ex1 :
<label for="txtIdentifiant">Identifiant</label>
<input type="text" id="txtIdentifiant" name="identifiant" />

-> Le lecteur lira "identifiant, édition" Ex2 :
<label for="txtMotDePasse">Mot de passe</label>
<input type="password" id="txtMotDePasse" name="motdepasse" />

-> Le lecteur lira : "Mot de passe, édition protégée"
```

#### 10. Gérer les éléments non pertinents avec aria-hidden

`aria-hidden="true"` évite de vocaliser éléments décoratifs

Ex : L'icône `&times;` (une croix) est uniquement décorative. Si elle était vocalisée, elle ajouterait une redondance : "Croix Fermer, bouton", ce qui peut prêter à confusion

```html
<button aria-label="Fermer">
  <i aria-hidden="true">&times;</i>
</button>
```

#### 11. Les aria-label des éléments interactifs

- Description plus précise de l'action
- les `alt=""` des images sont vides, car les logos (Visa, MasterCard, PayPal) sont purement décoratifs

```html
<button aria-label="payer avec Visa">
  <img src="visa.png" alt="" />
</button>
<button aria-label="payer avec MasterCard">
  <img src="mastercard.png" alt="" />
</button>
<button aria-label="payer avec Paypal">
  <img src="paypal.png" alt="" />
</button>
---
<a href="https://example.com" aria-label="Télécharger le rapport PDF">
  <i class="icon-download"></i>
</a>
```

#### 12. Rendre accessible un message d'alerte

`aria-live="polite"` = Le lecteur va attendre la fin de l'action  
Ici, le lecteur va restituer :  
"Alert, Attention le formulaire n'est pas validé, Fermer la notification, buton"

```html
<div id="notification" role="alert" aria-live="polite">
  <button onclick="close()" aria-label="fermer la notification">
    <i aria-hidden="true">&times;</i>
  </button>
  <span>Attention le formulaire n'est pas validé</span>
</div>
```

#### 13. Autres attributs ARIA

```txt
- aria-labelledby : indiquer les id des éléments qui titrent l'objet
- aria-describedby : indiquer les id des éléments qui décrivent l'objet
- aria-required : élément obligatoire
- aria-checked : élément coché
- aria-invalid : element invalide
- aria-live : restituer le contenu à la suite d'un nouvel évènement déclanché
- aria-expanded : élément déplié / replié
- aria-hidden : visible visuellement mais caché au lecteur d'écran
```

#### 14. Prévoyez la navigation au clavier :

- `touche Tab` : possibilité de pouvoir passer d'un élément à un autre
- `touche entrée` : la validation d'un lien fonctionne bien
- `flèches` : se déplacer de page en page
- Des accès rapide grâce à l'attribut `accesskey`  
  Ex: `<a href="contact.html" accesskey="t">Contact</a>`

#### 15. Zoom à 200%

Garder le contenu sans l'altérer avec un zoom jusqu'à 200%

#### 16. Black & White

Vérifier que si on passe le site en noir et blanc ça n'altère pas l'information

#### 17. Politique d'accessibilité 
Permet d'expliquer toutes les spécificités d'utilisation du site.
Pour ce point beaucoup de sites prévoient des fichiers audios permettant d'expliquer la disposition et la navigation. Et résumer tout ou partie du contenu.

#### 18. Passer le site dans des validateurs
-> https://achecker.ca/checker/index.php

#### 19. Tester son site

Avec des logiciels de revue d'écrans, il en existe des gratuits comme le narrateur nativement présent dans Windows 10 ou NVDA petit logiciel a télécharger ou des alternatives payantes.

#### 20. Moteurs de recherches spécialisés ? Inscription sur des sites annuaires ?

#### 21. Attentions aux animations et aux éléments cachés

Un menu déroulant par exemple n'est pas du tout une solution d'accessibilité adaptée

### Sources

#### Accessibilité mal voyants
- [Logiciels de revue d'écrans](https://www.ionos.fr/digitalguide/sites-internet/developpement-web/lecteurs-decran-logiciels-pour-malvoyants-et-non-voyants/)

- [NVDA](https://www.nvda-fr.org/)

- [Accessibilité recommandation WCAG](https://www.ionos.fr/digitalguide/sites-internet/developpement-web/accessibilite-sur-le-web-wcag-les-lignes-directrices/)

- [Aria](https://developer.mozilla.org/fr/docs/Accessibilit%C3%A9/ARIA)
- [Utilisation de l'aria](https://developer.paciellogroup.com/blog/2013/02/using-wai-aria-landmarks-2013/)


#### Accessibilité mal entendants

- [Sous titrage html avec `<track>`](https://developer.mozilla.org/fr/docs/Web/HTML/Element/track)
