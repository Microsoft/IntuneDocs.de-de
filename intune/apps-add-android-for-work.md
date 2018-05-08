---
title: Zuweisen von Apps zu Android for Work-Geräten
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Apps über den Managed Google Play Store synchronisieren und Android for Work-Geräten zuweisen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1742c33642667a9e7b8ca2f780094345959cd86c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="assign-apps-to-android-for-work-devices-with-intune"></a>Zuweisen von Apps für Android for Work-Geräte mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work ist ein Programm für Android-Geräte. Alle Apps, die Sie auf Android for Work-Geräten installieren, stammen aus dem Google Play for Work Store. Wie sich das Zuweisen von Apps zu Android for Work-Geräten von deren Zuweisung zu standardmäßigen Android-Geräten unterscheidet. Melden Sie sich beim Store an, suchen Sie nach den gewünschten Apps, und genehmigen Sie diese. Die App wird dann im Knoten **Lizenzierte Apps** des Azure-Portals angezeigt, und Sie können die Zuweisung der App wie bei jeder anderen App verwalten.

Wenn Sie eigene branchenspezifische Apps erstellt haben, können Sie diese ebenfalls wie folgt zuweisen:
- Registrieren Sie sich für ein Google Developer-Konto, über das Sie Apps in einem privaten Bereich im Google Play Store veröffentlichen können.
- Synchronisieren Sie die Apps mit Intune.

## <a name="before-you-start"></a>Vorbereitung

Stellen Sie sicher, dass Sie Intune und Android for Work für die **Geräteregistrierung** des Azure-Portals so konfiguriert haben, dass beide zusammen funktionieren.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Synchronisieren einer App aus dem Google Play for Work Store

1. Wechseln Sie zum [Google Play for Work Store](https://play.google.com/work). Melden Sie sich mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android for Work verwendet haben.
2. Suchen Sie im Store nach der App, die Sie mithilfe von Intune zuweisen möchten, und wählen Sie die App aus.
3. Wählen Sie auf der Seite, die die App anzeigt, **Genehmigen** aus.  
    Im folgenden Beispiel wurde die Microsoft Excel-App ausgewählt.

    ![Die Schaltfläche „Genehmigen“ im Google Play for Work-Store](media/approve.png)
    
   Ein Fenster für die App wird geöffnet, und Sie werden gebeten, der App Berechtigungen zum Durchführen verschiedener Vorgänge zu erteilen. 

4. Klicken Sie auf **Genehmigen**, um die App-Berechtigungen zu akzeptieren und fortzufahren.

    ![Die Schaltfläche „Genehmigen“ für App-Berechtigungen](media/approve-app-permissions.png)

5. Wählen Sie eine Option für die Behandlung neuer App-Berechtigungsanforderungen und dann **Speichern** aus.

    ![Optionen für die Behandlung neuer App-Berechtigungsanforderungen](media/approve-app-settings.png)

    Die App wird genehmigt und in Ihrer IT-Verwaltungskonsole angezeigt. Jetzt können Sie [die Android for Work-App mit Intune synchronisieren](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Synchronisieren einer Android for Work-App mit Intune

Wenn Sie eine App aus dem Store genehmigt haben und diese im Knoten **Lizenzierte Apps** der Workload **Mobile Apps** nicht angezeigt wird, erzwingen Sie wie folgt eine sofortige Synchronisierung:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Mobile Apps**.
4. Wählen Sie im Workloadbereich **Mobile Apps** unter **Setup** die Option **Android for Work** aus.
5. Klicken Sie im Bereich **Android for Work** auf **Synchronisieren**.  
    Auf der Seite werden Uhrzeit und Status der letzten Synchronisierung aktualisiert.
6. Wählen Sie im Workloadbereich **Mobile Apps** die Option **Apps** aus.  
    Die neu verfügbare Android for Work-App wird angezeigt.

Wenn die App im Knoten **App-Lizenzen** des Workloadbereichs **Mobile Apps** angezeigt wird, können Sie sie [wie jede andere App zuweisen](/intune-azure/manage-apps/deploy-apps). Die App kann nur zu Benutzergruppen zugewiesen werden.

Nachdem Sie die App zugewiesen haben, wird sie auf den vorgesehenen Geräten installiert. Der Benutzer des Geräts wird nicht zur Genehmigung der Installation aufgefordert.

## <a name="manage-android-for-work-app-permissions"></a>Verwalten von Android for Work-App-Berechtigungen
Android for Work erfordert, dass Sie Apps in der verwalteten Google Play-Webkonsole genehmigen, bevor Sie sie mit Intune synchronisieren und Ihren Benutzern zuweisen. Da Sie diese Apps mit Android for Work im Hintergrund und automatisch auf die Geräte der Benutzer übertragen können, müssen Sie die App-Berechtigungen im Interesse aller Ihrer Benutzer akzeptieren. Benutzern werden bei der Installation der Apps keine App-Berechtigungen angezeigt, daher ist es wichtig, dass Sie diese Berechtigungen lesen und verstehen.

Wenn ein App-Entwickler eine neue Version der App mit aktualisierten Berechtigungen veröffentlicht, werden diese Berechtigungen auch dann nicht automatisch akzeptiert, wenn Sie die vorherigen Berechtigungen genehmigt haben. Geräte, auf denen die vorherige Version der App ausgeführt wird, können diese weiterhin verwenden. Die App wird jedoch erst dann aktualisiert, wenn die neuen Berechtigungen genehmigt wurden. Geräte, auf denen die App nicht installiert ist, können die App nicht installieren, solange Sie die neuen Berechtigungen der App nicht genehmigt haben.

### <a name="update-app-permissions"></a>Aktualisieren von App-Berechtigungen

Besuchen Sie regelmäßig die verwaltete Google Play-Konsole, um zu prüfen, ob neue Berechtigungen vorliegen. Sie können Google Play so konfigurieren, dass eine E-Mail an Sie oder andere Personen gesendet wird, wenn neue Berechtigungen für eine genehmigte App erforderlich sind. Wenn Sie eine App zuweisen und feststellen, dass sie nicht auf Geräten installiert ist, überprüfen Sie folgendermaßen, ob neue Berechtigungen vorliegen:

1. Wechseln Sie zu [Google Play](http://play.google.com/work).
2. Melden Sie sich mit dem Google-Konto an, das Sie zum Veröffentlichen und Genehmigen der Apps verwendet haben.
3. Wählen Sie die Registerkarte **Updates** aus, und überprüfen Sie, ob andere Apps ein Update erfordern.  
    Alle aufgelisteten Apps erfordern neue Berechtigungen und werden erst zugewiesen, wenn diese Berechtigungen angewendet wurden.

Alternativ können Sie Google Play so konfigurieren, dass App-Berechtigungen auf App-Basis automatisch erneut genehmigt werden. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Arbeiten mit einer branchenspezifischen App aus dem Managed Google Play Store

1. Melden Sie sich bei der [Google Play Developer Console](https://play.google.com/apps/publish) mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android for Work verwendet haben.  
    Wenn Sie sich zum ersten Mal anmelden, müssen Sie sich registrieren und eine Gebühr bezahlen, um Mitglied im Google Developer-Programm zu werden.
2. Wählen Sie in der Konsole **Neue Anwendung hinzufügen** aus.
3. Informationen über Ihre App laden Sie auf dieselbe Weise hoch wie Sie Apps im Google Play Store veröffentlichen. Sie müssen jedoch **Only make this application available to my organization (<*organization name*>)** (Diese Anwendung nur für meine Organisation [<Name der Organisation>] verfügbar machen) auswählen.

    ![Verfügbarmachen der App nur für Ihre Organisation](media/restrict.png)

    Durch diesen Vorgang wird sichergestellt, dass die App nur für Ihre Organisation und nicht im öffentlichen Google Play-Store verfügbar ist.

    Weitere Informationen zum Hochladen und Veröffentlichen von Android-Apps finden Sie in der [Google Developer Console-Hilfe](https://support.google.com/googleplay/android-developer/answer/113469).
4. Nachdem Sie Ihre App veröffentlicht haben, melden Sie sich beim [Google Play for Work-Store](https://play.google.com/work) mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android for Work verwendet haben.
5. Prüfen Sie im Knoten **Apps** im Store, ob die veröffentlichte App angezeigt wird.  
    Die App ist automatisch für die Synchronisierung mit Intune genehmigt.

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md) 

