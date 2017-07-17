# GIT scripts for teams

La branche `master` correspond à la production.

La branche `base` est la racine de tous les développements.

Chaque release a sa propre branche `release/<release_name>`.

Enfin, chaque feature d'une release a sa branche `release/<release_name>/feature/<feature_name>`.

Si un ticket est lié à cette feature, le nom de la feature est de la forme `release/<release_name>/feature/<xxxx_feature_name>`.

## Création d'une release

Lorsqu'on démarre une nouvelle release:

* on créé une nouvelle branche `release/<release_name>` à partir de `base`.

## Création d'une feature

Lorsqu'on démarre une nouvelle feature:

* on se place sur la branche `release/<release_name>`,
* on créé une nouvelle branche `release/<release_name>/feature/<xxxx_feature_name>`.

## Fin d'une feature

Lorsqu'une feature est considérée comme terminée:

* on fait un rebase depuis la branche release parente,
* on merge la branche feature sur la branche release,
* on supprime la branche feature en local et en remote.

## Création d'un bugfix

Lorsqu'on démarre un nouveau bugfix:

* on se place sur la branche `release/<release_name>`,
* on créé une nouvelle branche `release/<release_name>/bugfix/<bugfix_name>`.

## Fin d'un bugfix

Lorsqu'un bugfix est considéré comme terminée:

* on fait un rebase depuis la branche release parente,
* on merge la branche bugfix sur la branche release,
* on supprime la branche bugfix en local et en remote.

## Recette / Mise en prod

La recette puis la mise en production se fait à partir de cette branche release.

## Fin d'une release

Une fois la mise en production effectuée :

* on merge la branche release dans `master` et `base`,
* on supprime la branche release en local et en remote. 
