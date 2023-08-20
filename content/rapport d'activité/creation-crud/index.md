---
title: "Creation Crud"
date: 2023-08-19T13:15:49+02:00
draft: false
---

La persistence se passe sur firebase, donc pour simplifier
l'interface avec firebase, tout dialogue avec firebase
passe par le bckend NestJS. Donc pour discuter avec
les CRUD on nutilise une app flutter, qui elle
même s'interface avec NestJS.

On commence donc a creer un CRUD sur NestJS en suivant
cette procédure. https://docs.nestjs.com/recipes/crud-generator

On veut egalement que notre API soit documentee donc
on utilise OpenAPI de la facon expliquée ici
https://docs.nestjs.com/openapi/introduction

Concretement `npx nest g resource MediaCategory`

Sur Flutter c'est compliqué car on a pas trouvé d'outil
clé en main pour les CRUDS, donc c'est plus long et fastidieux,
mais en factorisant on peut esperer réduire le code nécessaire.

Notamment pour gerer les donnes relationelles << OneToMany >>,
etc, une solution
existe pour typeORM et mongoose, mais pas firebase.
https://docs.nestjs.com/techniques/database

Ceci est utile https://ricardoromanj.com/posts/firestore-with-nestjs

On a commencé sur Flutter un crud << simple >> pour les types de
media, qui contient une seule proriteté de type texte: << name >>

Cela a pris deux jours.

Pour un crud media il faut egalement gerer le relation 
ManyToMany entre les types media et le media en lui
meme, ainsi que l'upload d'image, l'envoi sur firestore
et sa suppression, qui vont au dela de firestore, mais
emploie Firebase Storage. On essaye de refactoriser
le code de CRUD qu'on a developpé pour le MediaType
afin d'avoir le minimum de code qui se répète.

Un defi pour le CRUD a été d'avoir un FutureBuilder qui 
se combine avec un ChangeNotifierProvider, pour garder le 
CRUD à jour quand on ajoute ou supprime des elements depuis
un sous-écran.

Pour le image picker on utilise https://pub.dev/packages/image_picker

Pour le deuxieme CRUD on a essayé d'voir quelque chose de 
generique afin d'avoir le minimum de code qui se repete.