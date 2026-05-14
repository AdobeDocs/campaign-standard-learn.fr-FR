---
title: Étape 3 - Enregistrement des extensions dans votre application mobile
description: Dans cette partie, nous ajoutons le code pour enregistrer les extensions UserProfile, Identity, Lifecycle et Signal.
feature: Push
user: Admin
level: Experienced
jira: KT-4827
doc-type: tutorial
activity: use
team: TM
exl-id: d8c0d8c6-2e04-4c27-b27a-d0de79dd953b
TQID: https://experienceleague.adobe.com/WjKV0qe9zi7cV37Wn54BJdI91n92i302t4k-yMIenZ4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 7d15c0a5dc01907ff529b3684eaddaca5321facc
workflow-type: tm+mt
source-wordcount: 115
ht-degree: 13%

---

# Étape 3 - Enregistrement des extensions dans votre application mobile

Dans cette partie, nous ajoutons le code pour enregistrer les extensions Profil utilisateur, Identité, Cycle de vie et Signal. Nous devons également enregistrer l’extension Adobe Campaign Standard, comme indiqué dans le code ci-dessous.

Ouvrez votre projet dans [!DNL Android] studio. Supprimez l’intégralité du code dans MainApp **à l’exception de la première ligne qui correspond à l’instruction de votre package**.

Collez le code suivant dans MainApp

<!--
Removed `{.line-numbers}` below
-->

```java
import [!DNL android].app.Application;
import android.util.Log;

import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.Campaign;
import com.adobe.marketing.mobile.Identity;
import com.adobe.marketing.mobile.InvalidInitException;
import com.adobe.marketing.mobile.Lifecycle;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Signal;
import com.adobe.marketing.mobile.UserProfile;

public class MainApp extends Application {

@Override
public void onCreate() {
super.onCreate();

MobileCore.setApplication(this);
MobileCore.setLogLevel(LoggingMode.DEBUG);

try{
    Campaign.registerExtension();
    UserProfile.registerExtension();
    Identity.registerExtension();
    Lifecycle.registerExtension();
    Signal.registerExtension();
    MobileCore.start(new AdobeCallback () {
        @Override
        public void call(Object o) {
            MobileCore.configureWithAppID("copy your launch property id here");
        }
    });
} catch (InvalidInitException e) {
    Log.d("ACS Exception", "exception");
}
}
}
```

Ligne 32 : vous devez fournir l’identifiant du fichier d’environnement de votre propriété [!UICONTROL  Launch]. Vous pouvez y accéder à partir de l’onglet [!UICONTROL environnement] de votre propriété [!UICONTROL Launch].

![launch-id](assets/launch-id-property.PNG)
