---
title: Étape 3 - Enregistrement des extensions dans votre application mobile
description: Dans cette partie, nous allons ajouter le code pour enregistrer les extensions UserProfile, Identity, Lifecycle et Signal.
feature: Push
kt: 4827
doc-type: tutorial
activity: use
team: TM
exl-id: d8c0d8c6-2e04-4c27-b27a-d0de79dd953b
source-git-commit: ada0b029245190f53d58fa93c79c161719bfe9fd
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 14%

---

# Étape 3 - Enregistrement des extensions dans votre application mobile

Dans cette partie, nous allons ajouter le code pour enregistrer les extensions Profil utilisateur, Identité, Cycle de vie et Signal. Ces extensions font partie de [[!UICONTROL Extensions principales mobiles]](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core). Nous devrons également enregistrer l’extension Adobe Campaign Standard comme indiqué dans le code ci-dessous.

Ouvrez votre projet dans [!DNL Android] studio. Suppression du code entier dans MainApp **à l’exception de la première ligne qui correspond à votre instruction de package.**.

Collez le code suivant dans MainApp.

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

Ligne 32, vous devez fournir[!UICONTROL  Launch] ID du fichier d’environnement de la propriété. Vous pouvez y accéder à partir du [!UICONTROL onglet environnement] de votre [!UICONTROL Launch] .

![launch-id](assets/launch-id-property.PNG)
