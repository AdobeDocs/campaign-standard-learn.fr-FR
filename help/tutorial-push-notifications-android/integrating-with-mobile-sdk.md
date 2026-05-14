---
title: Étape 2 - Intégration du SDK Mobile
description: 'Dans cette partie, nous allons intégrer l’application Android à Mobile SDK. Pour intégrer Mobile SDK à l’application Android :'
feature: Push
user: Admin
level: Experienced
jira: KT-4826
doc-type: tutorial
activity: use
team: TM
recommendations: noDisplay
exl-id: 0fa53536-8330-4e96-be2f-afc078609bcd
TQID: https://experienceleague.adobe.com/6WL8yj7aMoS9C6l-HwQZZ3Hg0B2jmNtlmaFnsAi0Ohw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 7d15c0a5dc01907ff529b3684eaddaca5321facc
workflow-type: tm+mt
source-wordcount: 170
ht-degree: 3%

---

# ÉTAPE 2 - Intégrer [!UICONTROL Mobile SDK] à l&#39;application Android

Dans cette partie, nous allons intégrer l’application [!DNL Android] à [!UICONTROL Mobile SDK]. Pour intégrer [!UICONTROL mobile SDK] à l’application [!DNL Android], procédez comme suit :

* Ouvrez le projet *ACSPushTutorial* dans [!DNL Android Studio]
* Créez une classe Java appelée *MainApp* qui étend [!DNL android.app.Application]
* À ce stade, la structure de votre projet doit se présenter comme suit :

![main-app](assets/android-main-app.PNG)

* Développez le dossier [!DNL Gradle Scripts] . Double-cliquez sur le [!DNL build.gradle] du module . Collez les dépendances suivantes dans la section des dépendances du fichier [!DNL build.gradle]. Votre fichier [!DNL build.gradle] doit maintenant se présenter comme suit :

<!--
Removed `{.line-numbers}` below
-->

```java
implementation 'com.adobe.marketing.mobile:campaign:1.+'
implementation 'com.adobe.marketing.mobile:userprofile:1.+'
implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
```

![module-gradle](assets/module-build-gradle.PNG)

* Synchronisez votre projet [!DNL Android] en cliquant sur le bouton Synchroniser maintenant pour synchroniser votre projet

## Modifier le [!DNL AndroidManifest.xml]{#modify-android-manifest}

Ouvrez *AndroidManifest.xml* et collez les 2 lignes suivantes après l’élément de manifeste et avant l’élément d’application. Votre application peut ainsi communiquer avec le monde extérieur

<!--
Removed `{.line-numbers}` below
-->

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Copiez la ligne suivante dans l&#39;élément d&#39;application
[!DNL android:name= ».MainApp »]
Enregistrez votre [!DNL AndroidManifest.xml]
Votre [!DNL AndroidManifest.xml] doit ressembler à ceci

<!--
Removed `{.line-numbers}` below
-->

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.acspushtutorial">
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

<application
    android:name=".MainApp"
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/AppTheme">

<activity android:name=".MainActivity">
<intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER" />
</intent-filter>
</activity>
</application>

</manifest>
```
