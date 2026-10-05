---
title: Comprendre le connecteur de données Adobe Experience Platform
description: Adobe Experience Platform Data Connector permet aux clients existants de rendre leurs données disponibles sur Adobe Experience Platform en mappant les données XTK (données ingérées dans Campaign) avec les données XDM (Experience Data Model) sur Adobe Experience Platform.
feature: People Core Service Integration
jira: KT-2826
thumbnail: 27304.jpg
role: User
level: Experienced
doc-type: feature video
activity: understand
team: TM
exl-id: 686961f9-5374-4cc6-8b36-7ee0584ea720
TQID: 'https://experienceleague.adobe.com/8z32-bArYoMN41QFSi19bXUFc617UqZvdzxaam0Xr-E'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: f5407121-8933-4ac3-8e06-a9b692a4e88a
    internal-label: Campaign Standard
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: a8512b64-d668-4084-b4f0-34baa899e306
    internal-label: People Core Service integration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 508c3590ce956401ccfba3a256000cbc5849a684
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 15%
---
# Comprendre le Adobe Experience Platform [!UICONTROL Connecteur de données]

>[!NOTE]
>
>Cette fonctionnalité est en version bêta et est sujette à de fréquentes mises à jour et modifications sans préavis.
>
>Contactez le [!UICONTROL service clientèle d’] si vous envisagez de mettre en œuvre cette fonctionnalité.

## Vue d&#39;ensemble

Adobe Experience Platform [!UICONTROL Data Connector] permet aux clients existants de rendre leurs données disponibles sur Adobe Experience Platform en mappant les données XTK (données ingérées dans Adobe Campaign) aux données [!DNL Experience Data Model] (XDM) sur Adobe Experience Platform.

Le connecteur est unidirectionnel et envoie les données de Adobe Campaign Standard vers Adobe Experience Platform. Les données ne sont jamais envoyées du Adobe Experience Platform vers Adobe Campaign Standard.

Adobe Experience Platform [!UICONTROL Data Connector] est destiné aux ingénieurs de données qui connaissent Adobe Campaign Standard [!UICONTROL ressources personnalisées] et savent comment le schéma de données global du client doit se trouver dans Adobe Experience Platform.

>[!VIDEO](https://video.tv.adobe.com/v/27304?learn=on){transcript=true}

*Cette vidéo donne un aperçu de Adobe Experience Platform [!UICONTROL Connecteur de données] (09:35 min)*

>[!NOTE]
>
>Le transfert prêt à l’emploi des [!UICONTROL événements d’abonnement] n’est pas pris en charge. Pour transférer des [!UICONTROL événements d’abonnement], vous pouvez créer le XDM et le jeu de données correspondants sur Adobe Experience Platform, puis configurer un mappage de données personnalisé pour ces données.
>
>Les [!UICONTROL événements d’expérience] existants ne peuvent pas être ingérés dans Adobe Experience Platform, mais les [!UICONTROL événements d’expérience] générés en cours sont diffusés en continu vers Adobe Experience Platform.

## Étapes clés de la réalisation d’un mapping des données

Les tutoriels suivants décrivent les étapes essentielles pour effectuer un mappage de données entre Campaign Standard et Adobe Experience Platform :

1. [Mappage de ressources personnalisées](/help/administrating/adobe-experience-platform-data-connector/mapping-custom-resources.md)
2. [Mapping des événements d&#39;expérience](/help/administrating/adobe-experience-platform-data-connector/mapping-experience-events.md)
3. [Mappage des données du tableau de contrôle](/help/administrating/adobe-experience-platform-data-connector/mapping-seed-table-data.md)
4. [Modification du mappage de données](/help/administrating/adobe-experience-platform-data-connector/modifying-data-mapping.md)
5. [Vérification de l&#39;état d’un traitement d&#39;ingestion de données](/help/administrating/adobe-experience-platform-data-connector/checking-status-of-data-ingestion-jobs.md)

