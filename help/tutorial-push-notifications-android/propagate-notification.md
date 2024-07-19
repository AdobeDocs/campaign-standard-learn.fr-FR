---
title: Étape 5 - Propagation des notifications
description: Dans cette partie, nous allons propager le message reçu d’Adobe Campaign à l’aide d’Android Notification Manager.Firebase
feature: Push
jira: KT-4829
user: Admin
level: Experienced
doc-type: tutorial
activity: use
team: TM
exl-id: b0e01224-4ddc-4999-b8c6-794e49245428
source-git-commit: 200dcb4d6698c174f7fde508779609b11043d031
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 2%

---

# Ajouter un service pour envoyer la notification

Dans cette partie, nous allons propager le message reçu d’Adobe Campaign à l’aide de [!DNL Android Notification Manager]. [!DNL Notification manager] est utilisé pour avertir l’utilisateur des événements qui se produisent.
Voici comment vous dites à l’utilisateur que quelque chose s’est produit en arrière-plan :

* Lancement [!DNL Android Studio]
* Ouvrir le projet *[!DNL ACSPushTutorial]*
* Développer la structure du projet
* Cliquez avec le bouton droit sur le dossier de package ([!DNL com.example.acspushtutorial]) et [!DNL New ->Java Class]
* Nommez cette classe *[!DNL MyService]* et assurez-vous qu’elle étend [!DNL FirebaseMessagingService]
* Créez la méthode *[!DNL sendNotification]* dans cette classe. Dans cette méthode, vous devez définir le contenu et le canal de la notification à l’aide d’un objet [!DNL NotificationCompat.Builder]. Pour faire apparaître la notification, appelez [!DNL NotificationManagerCompat.notify()], lui transmettant un identifiant unique pour la notification et le résultat de [!DNL NotificationCompat.Builder.build()].

<!--
Removed `{.line-numbers}` below
-->

```java
package com.example.pushmessaging;
import android.app.NotificationChannel;
import android.app.NotificationManager;
import android.app.PendingIntent;
import android.content.Context;
import android.content.Intent;
import android.media.RingtoneManager;
import android.net.Uri;
import android.os.Build;
import android.util.Log;

import androidx.core.app.NotificationCompat;

import com.google.firebase.messaging.FirebaseMessagingService;
import com.google.firebase.messaging.RemoteMessage;

import java.util.Map;

public class MyService extends FirebaseMessagingService {
@Override
public void onMessageReceived(RemoteMessage remoteMessage)
{
Map<String,String> data  = remoteMessage.getData();
Log.d("data payload: ", data.toString());
sendNotification(remoteMessage);
}


private void sendNotification(RemoteMessage message) {
Intent intent = new Intent(this, MainActivity.class);
intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

String channelId = "0";
Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
NotificationCompat.Builder notificationBuilder =
        new NotificationCompat.Builder(this, channelId)
                .setSmallIcon(R.drawable.ic_launcher_background)
                .setContentTitle("Message from AEM")
                .setContentText(message.getData().get("body"))
                .setAutoCancel(true)
                .setSound(defaultSoundUri)
                .setContentIntent(pendingIntent);

NotificationManager notificationManager =
        (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

// Since android Oreo notification channel is needed.
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    NotificationChannel channel = new NotificationChannel(channelId,
            "Channel human readable title",
            NotificationManager.IMPORTANCE_DEFAULT);
    notificationManager.createNotificationChannel(channel);
}

notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
}
}
```

## Modifier [!DNL AndroidManifest.xml]

Ajoutez le service qui a été créé à votre [!DNL AndroidManifest.xml]. Le dernier [!DNL AndroidManifest.xml] doit ressembler à ce qui suit :

<!--
Removed `{.line-numbers}` below
-->

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.pushmessaging">

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
        <service
            android:name=".MyService"
            android:exported="false">
            <intent-filter>
                <action android:name="com.google.firebase.MESSAGING_EVENT" />
            </intent-filter>
        </service>

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## Exécution de l’application

Exécutez l’application en cliquant sur la **flèche verte** dans la barre d’outils ou dans le menu [!DNL Run].
