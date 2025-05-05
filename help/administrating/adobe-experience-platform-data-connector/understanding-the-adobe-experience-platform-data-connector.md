---
title: Présentation du connecteur de données Adobe Experience Platform
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
source-git-commit: 943599bd7ce139ef846f093ebda9084a91550aca
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 16%

---

# Présentation du [!UICONTROL connecteur de données] Adobe Experience Platform

>[!NOTE]
>
>Cette fonctionnalité est en version bêta et sujette à de fréquentes mises à jour et modifications sans préavis.
>
>Contactez le [!UICONTROL service clientèle d’Adobe] si vous envisagez d’implémenter cette fonctionnalité.

## Vue d’ensemble

Adobe Experience Platform [!UICONTROL Connecteur de données] permet aux clients existants de rendre leurs données disponibles sur Adobe Experience Platform en mappant les données XTK (données ingérées dans Adobe Campaign) à des données [!DNL Experience Data Model] (XDM) sur Adobe Experience Platform.

Le connecteur est unidirectionnel et envoie les données de Adobe Campaign Standard vers Adobe Experience Platform. Les données ne sont jamais envoyées de Adobe Experience Platform à Adobe Campaign Standard.

Adobe Experience Platform [!UICONTROL Connecteur de données] est destiné aux ingénieurs de données qui comprennent les [!UICONTROL ressources personnalisées] de Adobe Campaign Standard et connaissent la définition du schéma de données global du client dans Adobe Experience Platform.

>[!VIDEO](https://video.tv.adobe.com/v/34363?learn=on&captions=fre_fr){transcript=true}

*Cette vidéo donne un aperçu du [!UICONTROL connecteur de données] de Adobe Experience Platform (09:35 min)*

>[!NOTE]
>
>Le transfert prêt à l’emploi des [!UICONTROL événements d’abonnement] n’est pas pris en charge. Pour transférer des [!UICONTROL événements d’abonnement], vous pouvez créer le XDM et le jeu de données correspondants sur Adobe Experience Platform, puis configurer un mappage de données personnalisé pour ces données.
>
>Les [!UICONTROL événements d’expérience] existants ne peuvent pas être ingérés dans Adobe Experience Platform, mais les [!UICONTROL événements d’expérience] générés en cours sont diffusés en continu vers Adobe Experience Platform.

## Principales étapes pour effectuer un mapping des données

Les tutoriels suivants décrivent les étapes clés pour effectuer un mapping de données entre Campaign Standard et Adobe Experience Platform :

1. [Mappage de ressources personnalisées](/help/administrating/adobe-experience-platform-data-connector/mapping-custom-resources.md)
2. [Mapping des événements d&#39;expérience](/help/administrating/adobe-experience-platform-data-connector/mapping-experience-events.md)
3. [Mappage des données de tableau de contrôle](/help/administrating/adobe-experience-platform-data-connector/mapping-seed-table-data.md)
4. [Modification du mapping des données](/help/administrating/adobe-experience-platform-data-connector/modifying-data-mapping.md)
5. [Vérification de l&#39;état d’un traitement d&#39;ingestion de données](/help/administrating/adobe-experience-platform-data-connector/checking-status-of-data-ingestion-jobs.md)

