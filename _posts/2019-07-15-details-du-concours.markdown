---
layout: post
title:  "Détails du concours 2019"
ref: welcome
date:   2019-07-15 09:48:44 +0100
categories: competition
lang: fr
---

Le thème du défi de cette année est le rendu distribué, c'est-à-dire la visualisation de très grands jeux
de données nécessitant un rendu parallèle sur un supercalculateur. Pour participer au défi, veuillez vous
inscrire.

### Option 1: utilisez vos propres données

Nous vous encourageons à utiliser vos propres données de recherche si vous disposez d'un jeu de données
suffisamment volumineux. Tout jeu de données trop volumineux pour être rendu sur un poste de travail sera
qualifié pour ce concours. Un exemple classique est une simulation en fonction du temps dans laquelle
l'espace disque requis pour stocker chaque pas de temps est comparable ou supérieur à la RAM de la
station de travail.

### Option 2: utilisez les données que nous vous fournissons

Si vous n'avez pas accès à de telles données, vous pouvez utiliser le jeu de données de mécanique des
fluides numérique (MFN) gracieusement fourni par Joshua Brinkerhoff (UBC Okanagan) pour ce concours. Cet
ensemble de données provient d'une simulation numérique OpenFOAM d'un flux d'air de transition
incompressible sur une section d'éolienne. Le fluide est considéré incompressible en raison nombre de
Mach peu élevé. Le profil aérodynamique est NACA0018, communément utilisé pour étudier l’aérodynamique
des éoliennes.

Pour réduire la taille du jeu de données, nous considérons une courte période de temps
$$t=14.88308-15.01908$$ et nous ne sauvegardons qu’à chaque 3eme pas de temps (pour un total de 86) et 5
variables:

- *p* est la pression statique de jauge (en fait, la pression statique est divisée par la densité, mais
  la densité est constante dans un flux incompressible, de sorte qu'elle fonctionne comme une pression
  statique);
- *U* est le vecteur de vélocité;
- *vorticity* est le vecteur du tourbillon (courbure de la vitesse);
- *Lambda2* est la deuxième valeur propre du tenseur symétrique $$ S ^ 2 + \ Omega ^ 2 $$, où $$ S $$ et
  $$ \ Omega $$ sont les composantes symétriques et antisymétriques du tenseur à gradient de vitesse;
- *Q* est le deuxième invariant du tenseur de gradient de vitesse.

Veuillez noter que bien que les trois premières variables (p, U, Vorticity) soient disponibles pour les
86 pas de temps, les deux dernières (Lambda2, Q) ne sont disponibles que pour les 50 premiers. Notez
également que, autour de $$ t = 14.92308 $$, le pas de temps augmente.

Ci-dessous, nous fournissons un rendu simple de la magnitude de la vitesse effectuée avec ParaView sur le
supercalculateur Cedar. La visualisation intégrale avec 286 images a nécessité environ 20 minutes de
rendu sur 64 cœurs, la majeure partie du temps étant consacrée à la partie dépendante du temps, vers la
fin de la vidéo où nous devions lire chaque pas de temps directement à partir du disque.

<div class="flex-video">
	<iframe width="650" height="350" src="https://player.vimeo.com/video/353444320" frameborder="0"
	allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
	allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>
</div>

<sup>(Ou cliquez <a href="https://vimeo.com/353444320" target="_blank">ici</a> pour regarder cette vidéo
directement sur Vimeo.)</sup>

Vous trouverez ci-dessous un aperçu plus détaillé de la séparation de la couche limite laminaire de la
surface du profil et de son passage à la turbulence. Ce rendu plus complexe montrant l’isosurface de la
vitesse constante de l’air colorée selon la composante Y du tourbillon a pris 17 minutes sur 128 cœurs
sur Cedar.

<div class="flex-video">
	<iframe width="650" height="350" src="https://player.vimeo.com/video/354038712" frameborder="0"
	allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
	allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>
</div>

<sup>(Ou cliquez<a href="https://vimeo.com/354038712" target="_blank">ici</a> pour regarder cette vidéo
directement sur Vimeo.)</sup>

Le jeu de données lui-même
[est disponible]( {{ site.baseurl }}/competition/2019/09/30/dataset.html)
sur les grappes Cedar, Graham,
Niagara et Béluga. Vous aurez besoin d'un compte Calcul Canada (gratuit pour tous les chercheurs
canadiens) pour accéder aux données. Étant donné que la taille du jeu de données est d'environ 1,04 To,
nous vous conseillons vivement de ne pas le copier ou le télécharger sur votre ordinateur. Veuillez
plutôt le lire directement dans votre programme de visualisation à partir de son emplacement d'origine.

Les soumissions doivent être envoyées avant minuit, heure du Pacifique, le 30 novembre 2019.
