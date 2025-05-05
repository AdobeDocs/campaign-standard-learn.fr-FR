---
title: Résolution de problèmes pour les spécialistes du marketing
description: Connaître les erreurs les plus courantes peut vous aider à résoudre plus rapidement les problèmes et à accroître votre productivité. Ces conseils de dépannage vous aident à résoudre efficacement des erreurs similaires lorsqu’elles se produisent.
feature: Workflows
role: User
level: Beginner, Intermediate, Experienced
doc-type: Article
last-substantial-update: 2023-05-18T00:00:00Z
jira: KT-13256
thumbnail: KT-13256.jpeg
exl-id: 24a6815b-52d1-4bd6-9d27-522720a91f83
source-git-commit: 83b1b0c98d74d4555269a7d90051146d21824dc0
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Dépannage pour les professionnels du marketing : 5 erreurs courantes de workflow et de diffusion

Par : [Suraj Patra](https://www.linkedin.com/in/suraj-p-51612053/){target="_blank"}, Consultant principal, Meijer

En tant qu’ingénieur senior et expert client sur les produits Adobe Experience Cloud depuis cinq ans, j’ai permis aux utilisateurs professionnels de [Meijer](https://www.meijer.com/){target="_blank"}, une chaîne américaine de supercentres fondée en 1934, d’exécuter des campagnes marketing et transactionnelles complexes avec ACS. J’ai travaillé sur quelques projets, notamment des campagnes personnalisées pour stocker les offres et les détails de commande pour la personnalisation, l’intégration à Adobe Audience Manager, ainsi que des informations sur les clients pour l’ingestion de segments.


Pendant que j&#39;utilisais ACS, j&#39;ai rencontré des erreurs, qui peuvent prendre du temps et être frustrantes à résoudre. Connaître les erreurs les plus courantes peut vous aider à résoudre plus rapidement les problèmes et à accroître votre productivité. Vous trouverez ci-dessous mes conseils de dépannage pour vous aider à résoudre efficacement des erreurs similaires lorsqu’elles se produisent.

## Erreur de correspondance du type de données

**Code d’erreur :**
`PGS-220000 PostgreSQL error: ERROR: operator does not exist: character varying = bigint`

**Cause :**
Ces types d’erreurs apparaissent dans un workflow lorsque vous essayez de réconcilier à l’aide de champs de différents types de données. Par exemple, lorsque vous chargez un fichier à l’aide de l’option Charger le fichier , qui comporte un champ de chaîne, et que vous essayez de réconcilier le champ de chaîne avec un champ de profil dont le type de données est int.

![data-type-mismatch-error](/help/assets/kt-13256/data-type-mismatch.png)

**Solution :**
Remplacez le type de données du champ de l&#39;activité « Chargement de fichier » par celui avec lequel vous effectuez la correspondance. Ouvrez l’activité « Chargement de fichier ». Accédez à l’onglet « DÉFINITION DE COLONNE » et modifiez le type de données du champ souhaité.


![data-type-mismatch-solution](/help/assets/kt-13256/data-type-mismatch-solution.png)

## Erreur de Personalization de diffusion

**Code d’erreur :**
`The schema for profiles specified in the transition ('') is not compatible with the schema defined in the delivery template ('nms:recipient'). They should be identical.`

**Cause :**
Cette erreur s’affiche lorsque vous envoyez un e-mail à une adresse, mais que l’e-mail ou tout autre identifiant n’est pas réconcilié avec un profil. Pour envoyer une communication par e-mail, l’e-mail ou l’identifiant doit toujours être lié à un profil.

![workflow avec activité de réconciliation](/help/assets/kt-13256/del-persn-error-wf.png)

**Solution :**
Un identifiant commun doit exister à partir du fichier chargé avec la table des destinataires. Cette clé commune joint le fichier de chargement à la table des destinataires au sein de l&#39;activité de réconciliation. Les e-mails ne peuvent pas être envoyés aux enregistrements qui n’existent pas dans la table des destinataires, ce qui nécessite cette étape de réconciliation dans le workflow. Ce faisant, vous réconciliez l’activité de chargement de fichier entrant avec un identifiant tel que l’ID d’e-mail du profil. Le schéma `nms:recipient` fait référence à la table des profils et la réconciliation des enregistrements entrants avec le profil la rend disponible lors de la préparation de l&#39;email.

Consultez la capture d&#39;écran de l&#39;activité de réconciliation comme illustré ci-dessous.

![workflow avec détails de réconciliation](/help/assets/kt-13256/del-persn-error-wf-solution.png)

En savoir plus sur la [ réconciliation ](https://experienceleague.adobe.com/fr/docs/campaign-standard/using/managing-processes-and-data/data-management-activities/reconciliation).

## Erreur de jeu de données de champ commun

**Code d’erreur :**
`The document types of inbound events (''and'') are incompatible (step 'Exclusion'). Unable to perform the operation. `

**Cause :**
Ce problème se produit lors de l’utilisation de l’activité **exclusion** dans les workflows ACS, lors de l’exécution d’une exclusion en fonction de l’identifiant, lorsque le jeu de Principal et l’ensemble exclu n’ont pas les mêmes noms de champ.


![Erreur de jeu de données de champ commun](/help/assets/kt-13256/dataset-error.png)

**Solution :**

Il existe deux manières de résoudre cette erreur :

1. Utilisez le même nom de champ dans les champs principal et exclu et utilisez ce champ comme ID

   OU

2. Utilisez la méthode d&#39;exclusion JOINS pour sélectionner le champ en fonction duquel vous souhaitez exclure les enregistrements.

![Erreur de jeu de données de champ commun - ](/help/assets/kt-13256/dataset-error-solution.png) de solution

## Erreur de suppression du nom du champ

**Code d’erreur :**
`XTK-170036 Unable to parse expression 'i__name'`

**Cause :**

Des points d’échec peuvent se produire dans une **activité d’enrichissement**. L’une des plus courantes est affichée ci-dessous.

![Erreur de suppression du nom du champ](/help/assets/kt-13256/field-name-dropped-error.png)

Cela se produit lorsque vous modifiez manuellement le nom d’une expression dans l’activité. L’image indique que l’expression a été modifiée de `name `en `i__name`.

**Solution :**

Vous pouvez résoudre cette erreur de trois façons :

1. Remplacez le nom par l’expression qui était présente à l’origine.

2. Si vous souhaitez utiliser un nouveau nom, modifiez les valeurs dans l’activité **enrichissement**.

3. Si vous ne vous souvenez pas de ce qui a changé, il est recommandé de recréer l’activité.

## Erreur de suppression de la table temporaire 

**Code d’erreur :**
`XTK-170024 The temporary schema "temp:deliveryEmail1" is not defined in the current context.`

**Cause :**
Il s’agit d’une erreur courante dans les workflows complexes impliquant un enrichissement ou une autre activité. Cela signifie probablement que certains workflows d’activité ne sont pas correctement enregistrés lors de plusieurs modifications apportées au workflow.

![Erreur de table temporaire ](/help/assets/kt-13256/temp-table-dropped-error.png)

**Solution :**
Cette erreur peut se produire de nombreuses façons. Il n’existe donc pas de solution simple. S’il s’agit d’un workflow simple, il est préférable de reconfigurer l’activité. Dans un workflow complexe, il est préférable de copier les activités de workflow dans un nouveau workflow, de les enregistrer et de les réexécuter.
