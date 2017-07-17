# GIT scripts for teams

La branche `master` correspond à la production.

La branche `base` est la racine de tous les développements.

Chaque release a son propre namespace `release/<release_name>`:
* la release est dans `release/<release_name>/base`,
* les features sont dans `release/<release_name>/feature/<feature_name>`.
* les bugfixes sont dans `release/<release_name>/bugfix/<bug_description>`.

Si un ticket est lié à une feature ou un bugfix, le nom est préfixé du numéro du ticket:
* `release/<release_name>/feature/<xxxx_feature_name>`.
* `release/<release_name>/bugfix/<xxxx_bug_description>`.

## Création d'une release

Lorsqu'on démarre une nouvelle release:

* mise à jour de la branche `base`,
* création d'une nouvelle branche `release/<release_name>/base` à partir de `base`.

## Création d'une feature

Lorsqu'on démarre une nouvelle feature:

* mise à jour de la branche `release/<release_name>/base`,
* création d'une nouvelle branche `release/<release_name>/feature/<xxxx_feature_name>` à partir de `release/<release_name>/base`.

## Fin d'une feature

Lorsqu'une feature est considérée comme terminée:

* mise à jour de la branche `release/<release_name>/base`,
* rebase de la branche `release/<release_name>/feature/<xxxx_feature_name>` depuis la branche `release/<release_name>/base`,
* merge de la branche `release/<release_name>/feature/<xxxx_feature_name>` sur la branche `release/<release_name>/base`,
* suppression de la branche `release/<release_name>/feature/<xxxx_feature_name>` en local et en remote.

## Création d'un bugfix

Lorsqu'on démarre un nouveau bugfix:

* mise à jour de la branche `release/<release_name>/base`,
* création d'une nouvelle branche `release/<release_name>/bugfix/<xxxx_bug_description>` à partir de `release/<release_name>/base`.

## Fin d'un bugfix

Lorsqu'un bugfix est considéré comme terminée:

* mise à jour de la branche `release/<release_name>/base`,
* rebase de la branche `release/<release_name>/bugfix/<xxxx_bug_description>` depuis la branche `release/<release_name>/base`,
* merge de la branche `release/<release_name>/bugfix/<xxxx_bug_description>` sur la branche `release/<release_name>/base`,
* suppression de la branche `release/<release_name>/bugfix/<xxxx_bug_description>` en local et en remote.

## Recette / Mise en prod

La recette puis la mise en production se fait à partir de la branche `release/<release_name>/base`.

## Fin d'une release

Une fois la mise en production effectuée :

* merge de la branche `release/<release_name>/base` dans `master` et `base`,
* tag de `master`,
* suppression de la branche `release/<release_name>/base` en local et en remote. 
