---
title: Design
---

Organisation
---
On s'est créé un salon discord où on a crée des channel 
 discuter de chaque partie du projet.

On a créé un channel github pour avoir les notifications 
d'activité de git.

On a créé un channel de notifications de l'activité sur taïga.

On a utilisé taiga.io pour planifier le projet en sprints.

On a essayé de faire des daily standups.

Architecture
---

En terme d'architecture on a décidé de mettre
la persistance sur firebase car une des contraintes
qu'on veut suivre est de pouvoir déployer gratuitement
sur render.com, et avoir un docker image qui contient
mongodb dépasse le quota de ce qui est autorisé sur render.

On veut également que le multiplexage se passe sur le
serveur node, de sorte que cette operation lourde
en electricité n'impacte pas le client ipad.

Le diagrammew de use cases a été fait avec umlet.

{{<figure src="usecases.png" caption="Use cases" >}}

Le stockage des medias se fait avec Firebase storage
https://firebase.google.com/docs/storage qui est un 
CDN qui permet des conversions en webp, le 
redimensionnement automatique des images via une 
url du type image.jpg?width=50, etc.

Un bon tutorial a ce sujet 
https://dev.to/dbanisimov/building-image-cdn-with-firebase-15ef

Le stockage des images se fait sur le google cloud
https://firebase.google.com/docs/storage/admin/start

On utilise Firebase authentification pour 
identifier les utilisateurs.

Design
---

Utilisé figma. Pour l'inspiration des fontes on 
s'est inspiré d'autres apps existantes, et demandé
conseil a chatgpt. Le choix des couleurs s'est
fait pour être cohérent avec une application sociale
de cuisine.

Inspiration:
- awwwards
- dribble
- https://www.happyhues.co/palettes/12
- https://www.supercook.com/#/desktop

Quelques ressources pour les fontes :
- https://fontsinuse.com

Ces formations, en plus des cours nous ont été utiles :
- https://www.linkedin.com/learning/figma-creer-une-interface-mobile
- https://www.linkedin.com/learning/figma-creer-la-maquette-d-un-site-pour-une-marque-eco-responsable

Les plugins Figma qu'on a utilisé sont ceux les plus
populaires sur la marketplace
- iconify
- content reel
- unsplash

Premiere version du Figma

{{<figure src="figma.png" caption="Use cases" >}}


MLD
---

Utilisé Oracle Data Modeler