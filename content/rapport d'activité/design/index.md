---
title: Design
---

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

MLD
---

Utilisé Oracle Data Modeler