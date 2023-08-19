---
title: "Gestion Projet"
date: 2023-08-19T12:37:44+02:00
draft: false
---

La coordination du projet s'est fait sur Discord

https://discord.gg/GCbSMXh7f

La bas on a crée un chan pour chaque partie du projet.

On a aussi crée un chan pour les daily standups en mode 
SCRUM, on a laissé tomber apres quelque temps.

On a ajouté des webhooks pour recevoir les notifications
de github sur un chan specifique. Il suffit pour ca
de creer un webhook dans les integrations dans les
setting du serveur discord, puis dans les webhooks du repo 
github ajouter le lien donné par discord, en ajoutant << /github >>
à la fin (ou n'importe quel nom qui correspond au salon où
on veut vois les notifications apparaitre)

Pour la gestion de projet en mode kanban (trello) on utilise taiga.
L'integration discord de taiga n'est pas officiellement 
existante mais on a reussi a obtrenir cette integration en 
suivant cette combine https://github.com/taigaio/taiga-back/issues/888#issuecomment-411227921

On a donc le suivi de l'activité du projet sur discord ainsi.

Sur taiga on a découpé l'avancement en sprints en utilisant
la methodologie SCRUM et Kanban, ainsi que des Epics.

Lien du taiga https://tree.taiga.io/project/meithal-projet-annuel-3moc-esgi-ivo-elie-pierre-elie/timeline