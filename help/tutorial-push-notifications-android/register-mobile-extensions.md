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
source-git-commit: 9be31e056800b806c49a2c5ffbf9f9f42b001d4c
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 14%

---

# Étape 3 - Enregistrement des extensions dans votre application mobile

Dans cette partie, nous ajoutons le code pour enregistrer les extensions Profil utilisateur, Identité, Cycle de vie et Signal. Nous devons également enregistrer l’extension Adobe Campaign Standard comme indiqué dans le code ci-dessous.

Ouvrez votre projet dans [!DNL Android] studio. Supprimez l&#39;intégralité du code dans l&#39;application principale **, à l&#39;exception de la première ligne correspondant à votre instruction de package**.

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

Ligne 32, vous devez fournir l’identifiant de fichier d’environnement de la propriété [!UICONTROL  Launch]. Vous pouvez y accéder à partir de l’onglet [!UICONTROL environnement] de votre propriété [!UICONTROL Launch].

![launch-id](assets/launch-id-property.PNG)
