# Todolist avec VueJS 3

## Objectif

L'objectif est de créer un petit système de tâche à faire:

* On affiche un message s'il n'y a pas de tâche à faire
* Un champs texte accompagné d'un bouton "Ajouter" sera présent au dessus de la liste et permettra d'ajouter une nouvelle tâche.
* Pour chaque tâche, une case à cocher permettra de marquer la tâche comme faite.
* Une tâche terminée sera barrée (à l'aide de CSS).
* Les tâches à faire seront toujours affichées en premier
* Une case, en bas de la liste, permettra de masquer les tâches terminées

```javascript
[
    { "title": "Acheter la propriété 'Rue de la Paix'", "completed": false, "date": 20240730 },
    { "title": "Construire un hôtel sur 'Avenue Foch'", "completed": false, "date": 20240730 },
    { "title": "Éviter la case prison", "completed": false, "date": 20240730 }
]
```

## Project Setup

```sh
yarn
```

### Compile and Hot-Reload for Development

```sh
yarn dev
```

### Compile and Minify for Production

```sh
yarn build
```
