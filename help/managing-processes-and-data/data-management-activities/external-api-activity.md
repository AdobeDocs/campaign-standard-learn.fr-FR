---
title: Configuration et exécution d’un workflow avec l’activité API externe
description: Découvrez comment appeler un point d’entrée externe de l’API REST pour extraire des données de personnalisation d’un système tiers dans votre campagne.
feature: Data Management Activity
jira: KT-2764
thumbnail: 28200.jpg
doc-type: feature video
activity: use
team: TM
exl-id: bce6fa2e-a684-43af-a41e-dfec54dd453a
role: User, Developer
level: Experienced
TQID: 'https://experienceleague.adobe.com/XTIqOfVTs-cE00YQM955S-7G1jwAU-W4pg1J8bNm-HE'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: f5407121-8933-4ac3-8e06-a9b692a4e88a
    internal-label: Campaign Standard
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: 97f7b899-98c8-5133-9446-bfaf99a51b9f
    internal-label: Data Management Activity
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
source-git-commit: 9d73ba976848e452ee9529a2f3799e1c6ed3fa83
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 49%
---
# Configuration et exécution d’un workflow avec l’[!UICONTROL activité API externe]

L’[!UICONTROL activité API externe] est une [!UICONTROL activité de Data Management]. Elle permet d’appeler un point d’entrée externe de l’API REST. L’objectif de cette activité est d’obtenir des données de personnalisation d’un système tiers dans votre campagne.

Voici quelques cas pratiques :

* Obtention du dernier programme d’un événement sportif afin d’en personnaliser le contenu
* Obtention du dernier ensemble d’offres
* Connexion à un système de génération de bons
* Vérification des conditions météorologiques par région et utilisation de ces données pour personnaliser le contenu

Cette vidéo présente l’utilisation de l’[!UICONTROL activité API externe].

>[!VIDEO](https://video.tv.adobe.com/v/33117/?captions=fre_fr&learn=on){transcript=true}

*[!UICONTROL Activité API externe] (06:48 min)*

>[!NOTE]
>
>L’activité est destinée à récupérer des données à l’échelle de la campagne, et non à récupérer des informations spécifiques à chaque profil, car cela peut entraîner le transfert de grandes quantités de données. Si le cas d’utilisation nécessite des informations spécifiques au profil, la recommandation consiste à utiliser l’activité Transfert de fichier .
