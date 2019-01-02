---
title: Zuweisen von Apps zu Android-Arbeitsprofilgeräten
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Apps mit Android-Arbeitsprofilgeräten synchronisieren und sie diesen über den Managed Google Play Store zuweisen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 5495addba30e8a958d2a49f2c04ee5af70d62712
ms.sourcegitcommit: a0db74934433226e28ffdf5d92930dafd2feceae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305929"
---
# <a name="assign-apps-to-android-work-profile-devices-with-intune"></a>Zuweisen von Apps zu Android-Arbeitsprofilgeräten mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android Enterprise ist ein Programm für Android-Geräte mit Arbeitsprofilen und für Android-Kioskgeräte. Für Android-Geräte mit Arbeitsprofilen stellt Android Enterprise eine Reihe von Features und Diensten bereit, die Ihre privaten Apps und Daten von Ihrem Arbeitsprofil von Geschäfts-Apps und -daten trennt. Android Enterprise bietet zusätzliche Verwaltungsoptionen und zusätzlichen Datenschutz, wenn Benutzer ihre Android-Geräte für die Arbeit verwenden. Intune unterstützt Sie bei der Bereitstellung von Apps und Einstellungen auf Android-Arbeitsprofilgeräten und stellt so sicher, dass geschäftliche und private Informationen immer getrennt bleiben. Alle Apps, die für Android-Geräte mit Arbeitsprofilen installiert werden, stammen aus dem Managed Google Play Store. Das Zuweisen von Apps zu Android-Arbeitsprofilgeräten unterscheidet sich von deren Zuweisung zu „normalen“ Android-Geräten. Melden Sie sich beim Store an, suchen Sie nach den gewünschten Apps, und genehmigen Sie diese. Die App wird dann im Knoten **Lizenzierte Apps** des Azure-Portals angezeigt, und Sie können die Zuweisung der App wie bei jeder anderen App verwalten.

Wenn Sie eigene branchenspezifische Apps erstellt haben, können Sie diese ebenfalls wie folgt zuweisen:
- Registrieren Sie sich für ein Google Developer-Konto, über das Sie Apps in einem privaten Bereich im Google Play Store veröffentlichen können.
- Synchronisieren Sie die Apps mit Intune.

## <a name="before-you-start"></a>Vorbereitung

Stellen Sie sicher, dass Sie Intune und Android-Arbeitsprofile für die **Geräteregistrierungsworkload** des Azure-Portals so konfiguriert haben, dass beide zusammen funktionieren. Weitere Informationen finden Sie unter [Registrieren von Android-Geräten](android-work-profile-enroll.md).

## <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Synchronisieren einer App aus dem Managed Google Play Store

1. Besuchen Sie den [Managed Google Play Store](https://play.google.com/work). Melden Sie sich mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android Enterprise verwendet haben.
2. Suchen Sie im Store nach der App, die Sie mithilfe von Intune zuweisen möchten, und wählen Sie die App aus.
3. Wählen Sie auf der Seite, die die App anzeigt, **Genehmigen** aus.  
    Im folgenden Beispiel wurde die Microsoft Excel-App ausgewählt.

    ![Die Schaltfläche „Genehmigen“ im Managed Google Play-Store](media/approve.png)
    
   Ein Fenster für die App wird geöffnet, und Sie werden gebeten, der App Berechtigungen zum Durchführen verschiedener Vorgänge zu erteilen. 

4. Klicken Sie auf **Genehmigen**, um die App-Berechtigungen zu akzeptieren und fortzufahren.

    ![Die Schaltfläche „Genehmigen“ für App-Berechtigungen](media/approve-app-permissions.png)

5. Wählen Sie eine Option für die Behandlung neuer App-Berechtigungsanforderungen und dann **Speichern** aus.

    ![Optionen für die Behandlung neuer App-Berechtigungsanforderungen](media/approve-app-settings.png)

    Die App wird genehmigt und in Ihrer IT-Verwaltungskonsole angezeigt. Als Nächstes können Sie [die Android-Arbeitsprofil-App mit Intune synchronisieren](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune). 

## <a name="sync-a-managed-google-play-app-with-intune"></a>Synchronisieren einer App aus dem Managed Google Play Store mit Intune

Wenn Sie eine App aus dem Store genehmigt haben und diese nicht im Knoten **Lizenzierte Apps** der Workload **Client-Apps** angezeigt wird, erzwingen Sie wie folgt eine sofortige Synchronisierung:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Setup** die Option **Managed Google Play** aus.
5. Klicken Sie im Bereich **Managed Google Play** auf **Aktualisieren**.  
    Auf der Seite werden Uhrzeit und Status der letzten Synchronisierung aktualisiert.
6. Wählen Sie im Workloadbereich **Client-Apps** die Option **Apps** aus.  
    Die neu verfügbare Managed Google Play-App wird angezeigt.

Wenn die App im Knoten **App-Lizenzen** des Workloadbereichs **Client-Apps** angezeigt wird, können Sie sie [wie jede andere App zuweisen](/intune-azure/manage-apps/deploy-apps). Die App kann nur zu Benutzergruppen zugewiesen werden.

Nachdem Sie die App zugewiesen haben, wird sie auf den vorgesehenen Geräten installiert. Der Benutzer des Geräts wird nicht zur Genehmigung der Installation aufgefordert.

## <a name="manage-android-enterprise-app-permissions"></a>Berechtigungen für Managed Android Enterprise-Apps
Android Enterprise erfordert, dass Sie Apps in der Managed Google Play-Webkonsole genehmigen, bevor Sie sie mit Intune synchronisieren und Ihren Benutzern zuweisen. Da Sie diese Apps mit Android Enterprise im Hintergrund und automatisch auf die Geräte der Benutzer übertragen können, müssen Sie die App-Berechtigungen im Interesse aller Ihrer Benutzer akzeptieren. Benutzern werden bei der Installation der Apps keine App-Berechtigungen angezeigt. Daher ist es wichtig, dass Sie diese Berechtigungen verstehen.

Wenn ein App-Entwickler eine neue Version der App mit aktualisierten Berechtigungen veröffentlicht, werden diese Berechtigungen auch dann nicht automatisch akzeptiert, wenn Sie die vorherigen Berechtigungen genehmigt haben. Geräte, auf denen die vorherige Version der App ausgeführt wird, können diese weiterhin verwenden. Die App wird jedoch erst dann aktualisiert, wenn die neuen Berechtigungen genehmigt wurden. Geräte, auf denen die App nicht installiert ist, können die App nicht installieren, solange Sie die neuen Berechtigungen der App nicht genehmigt haben.

### <a name="update-app-permissions"></a>Aktualisieren von App-Berechtigungen

Besuchen Sie regelmäßig die verwaltete Google Play-Konsole, um zu prüfen, ob neue Berechtigungen vorliegen. Sie können Google Play so konfigurieren, dass eine E-Mail an Sie oder andere Personen gesendet wird, wenn neue Berechtigungen für eine genehmigte App erforderlich sind. Wenn Sie eine App zuweisen und feststellen, dass sie nicht auf Geräten installiert ist, überprüfen Sie folgendermaßen, ob neue Berechtigungen vorliegen:

1. Wechseln Sie zu [Google Play](https://play.google.com/work).
2. Melden Sie sich mit dem Google-Konto an, das Sie zum Veröffentlichen und Genehmigen der Apps verwendet haben.
3. Wählen Sie die Registerkarte **Updates** aus, und überprüfen Sie, ob andere Apps ein Update erfordern.  
    Alle aufgelisteten Apps erfordern neue Berechtigungen und werden erst zugewiesen, wenn diese Berechtigungen angewendet wurden.

Alternativ können Sie Google Play so konfigurieren, dass App-Berechtigungen auf App-Basis automatisch erneut genehmigt werden. 

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Arbeiten mit einer branchenspezifischen App aus dem Managed Google Play Store

1. Melden Sie sich bei der [Google Play Developer Console](https://play.google.com/apps/publish) mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android Enterprise verwendet haben.  
    Wenn Sie sich zum ersten Mal anmelden, müssen Sie sich registrieren und eine Gebühr bezahlen, um Mitglied im Google Developer-Programm zu werden.
2. Wählen Sie in der Konsole **Neue Anwendung hinzufügen** aus.
3. Informationen über Ihre App laden Sie auf dieselbe Weise hoch wie Sie Apps im Google Play Store veröffentlichen. Sie müssen jedoch **Only make this application available to my organization (<*organization name*>)** (Diese Anwendung nur für meine Organisation [<Name der Organisation>] verfügbar machen) auswählen.

    ![Verfügbarmachen der App nur für Ihre Organisation](media/restrict.png)

    Durch diese Aktion wir die App nur für Ihre Organisation verfügbar gemacht. Sie wird nicht im öffentlichen Google Play Store verfügbar gemacht.

    Weitere Informationen zum Hochladen und Veröffentlichen von Android-Apps finden Sie in der [Google Developer Console-Hilfe](https://support.google.com/googleplay/android-developer/answer/113469).
4. Nachdem Sie Ihre App veröffentlicht haben, melden Sie sich beim [Managed Google Play Store](https://play.google.com/work) mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android Enterprise verwendet haben.
5. Prüfen Sie im Knoten **Apps** im Store, ob die veröffentlichte App angezeigt wird.  
    Die App ist automatisch für die Synchronisierung mit Intune genehmigt.

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md) 

