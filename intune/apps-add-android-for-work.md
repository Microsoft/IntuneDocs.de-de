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
ms.openlocfilehash: 4168f78bff8937ca403cdb75b1028954cbbebd6f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Zuweisen von Apps für Android for Work-Geräte mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work ist ein Programm für Android-Geräte. Alle Apps, die Sie auf Android for Work-Geräten installieren, stammen aus dem Google Play for Work Store. Apps werden zu Android for Work-Geräten anders zugewiesen als zu normalen Android-Geräten. Melden Sie sich beim Store an, suchen Sie nach den gewünschten Apps, und genehmigen Sie diese. Anschließend wird die App im Knoten **Lizenzierte Apps** des Azure-Portals angezeigt. Ab dann können Sie die Zuweisung der App auf dieselbe Weise wie bei jeder anderen App durchführen.

Wenn Sie eigene branchenspezifische Apps erstellt haben, können Sie diese ebenfalls wie folgt zuweisen:
- Registrieren Sie sich für ein Google Developer-Konto, über das Sie Apps in einem privaten Bereich im Google Play Store veröffentlichen können.
- Synchronisieren Sie die Apps mit Intune.

## <a name="before-you-start"></a>Vorbereitung

Stellen Sie sicher, dass Sie Intune und Android for Work für die **Geräteregistrierung** des Azure-Portals so konfiguriert haben, dass beide zusammen funktionieren.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Synchronisieren einer App aus dem Google Play for Work Store

1. Wechseln Sie zum [Google Play for Work Store](https://play.google.com/work). Melden Sie sich mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android for Work verwendet haben.
2. Suchen Sie im Store nach der App, die Sie mithilfe von Intune zuweisen möchten, und wählen Sie die App aus.
3. Klicken Sie auf der Seite, auf der die App angezeigt wird, auf **Genehmigen**. Die folgenden Beispiele zeigen die Microsoft Excel-App.</br>

    ![Beispiel: Genehmigen einer App im Managed Google Play Store](media/approve.png)</br>
    
   Ein Fenster für die App wird geöffnet, und Sie werden gebeten, der App Berechtigungen zum Durchführen verschiedener Vorgänge zu erteilen. 

4. Klicken Sie auf **Genehmigen**, um die App-Berechtigungen zu akzeptieren und fortzufahren.</br>

    ![Beispiel: Genehmigen von App-Berechtigungen](media/approve-app-permissions.png)

5. Wählen Sie aus, wie neue Anforderungen für App-Berechtigungen behandelt werden sollen. Klicken Sie dann auf **Speichern**, um die Behandlung neuer Anforderungen für App-Berechtigungen zu speichern.</br>

    ![Beispiel: Speichern der Behandlung neuer Anforderungen für App-Berechtigungen](media/approve-app-settings.png)</br>

    Die App wird genehmigt und in Ihrer IT-Verwaltungskonsole angezeigt. Jetzt können Sie [die Android for Work-App mit Intune synchronisieren](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Synchronisieren einer Android for Work-App mit Intune

Wenn Sie eine App aus dem Store genehmigt haben und diese im Knoten **Lizenzierte Apps** der Workload **Mobile Apps** nicht angezeigt wird, erzwingen Sie wie folgt eine sofortige Synchronisierung:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Mobile Apps**.
4. Wählen Sie in der Workload **Mobile Apps** im Abschnitt **Setup** die Option **Android for Work** aus.
5. Klicken Sie im Bereich „Android for Work“ auf **Synchronisieren**. Auf der Seite werden Uhrzeit und Status der letzten Synchronisierung aktualisiert.
6. Wählen Sie in der Workload **Mobile Apps** die Option **Apps** aus, um die neu verfügbare Android for Work-App anzuzeigen.

Wenn die App im Knoten **App-Lizenzen** der Workload **Mobile Apps** angezeigt wird, können Sie sie [wie jede andere App zuweisen](/intune-azure/manage-apps/deploy-apps). Die App kann nur zu Benutzergruppen zugewiesen werden.

Nachdem Sie die App zugewiesen haben, wird sie auf den vorgesehenen Geräten installiert. Der Benutzer des Geräts wird nicht zur Genehmigung der Installation aufgefordert.

## <a name="manage-android-for-work-app-permissions"></a>Verwalten von Android for Work-App-Berechtigungen
Android for Work erfordert, dass Sie Apps in der verwalteten Play-Webkonsole von Google genehmigen, bevor Sie sie mit Intune synchronisieren und Ihren Benutzern zuweisen.  Da Sie diese Apps mit Android for Work im Hintergrund und automatisch auf die Geräte der Benutzer übertragen können, müssen Sie die App-Berechtigungen im Interesse aller Ihrer Benutzer akzeptieren.  Endbenutzern werden bei der Installation keine App-Berechtigungen angezeigt, daher ist es wichtig, dass Sie diese Berechtigungen lesen und verstehen.

Wenn ein App-Entwickler eine neue Version der App mit aktualisierten Berechtigungen veröffentlicht, werden diese Berechtigungen auch dann nicht automatisch akzeptiert, wenn Sie die vorherigen Berechtigungen genehmigt haben. Geräte, auf denen die alte Version der App ausgeführt wird, können diese weiterhin verwenden. Die App wird jedoch erst dann aktualisiert, wenn die neuen Berechtigungen genehmigt wurden. Geräte, auf denen die App nicht installiert ist, können die App nicht installieren, solange Sie die neuen Berechtigungen der App nicht genehmigt haben.

### <a name="how-to-update-app-permissions"></a>Aktualisieren von Berechtigungen für die App

Besuchen Sie regelmäßig die verwaltete Google Play-Konsole, um zu prüfen, ob neue Berechtigungen vorliegen. Sie können Google Play so konfigurieren, dass eine E-Mail an Sie oder andere Personen gesendet wird, wenn neue Berechtigungen für eine genehmigte App erforderlich sind. Wenn Sie eine App zuweisen und feststellen, dass sie nicht auf Geräten installiert ist, überprüfen Sie mit den folgenden Schritten, ob neue Berechtigungen vorliegen:

1. Besuchen Sie http://play.google.com/work.
2. Melden Sie sich mit dem Google-Konto an, das Sie zum Veröffentlichen und Genehmigen der Apps verwendet haben.
3. Rufen Sie die Registerkarte **Aktualisierungen** auf, um festzustellen, ob Apps vorhanden sind, die ein Update erfordern.  Alle aufgelisteten Apps erfordern neue Berechtigungen und werden erst zugewiesen, wenn diese Berechtigungen angewendet wurden.  

Alternativ können Sie Google Play so konfigurieren, dass App-Berechtigungen auf App-Basis automatisch erneut genehmigt werden. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Arbeiten mit einer branchenspezifischen App aus dem Managed Google Play Store

1. Wechseln Sie zur Google Play Developer Console unter [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Melden Sie sich mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android for Work verwendet haben. Wenn Sie sich zum ersten Mal anmelden, müssen Sie sich registrieren und eine Gebühr bezahlen, um Mitglied im Google Developer-Programm zu werden.
3. Wählen Sie in der Konsole **Neue Anwendung hinzufügen**.
4. Informationen über Ihre App laden Sie auf dieselbe Weise hoch wie Sie Apps im Google Play Store veröffentlichen. Sie müssen jedoch die Einstellung **Only make this application available to my organization (<*organization name*>)** (Diese Anwendung nur für meine Organisation (<Name der Organisation>) verfügbar machen) auswählen:</br>

    ![Option, um eine Anwendung nur für die eigene Organisation verfügbar zu machen](media/restrict.png)</br>

Durch diesen Vorgang wird sichergestellt, dass die App nur für Ihre Organisation und nicht im öffentlichen Google Play Store verfügbar ist.
Weitere Informationen zum Hochladen und Veröffentlichen von Android-Apps finden Sie in der [Google Developer Console-Hilfe](https://support.google.com/googleplay/android-developer/answer/113469).
5. Wechseln Sie nach dem Veröffentlichen Ihrer App zum [Google Play for Work Store](https://play.google.com/work). Melden Sie sich mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android for Work verwendet haben.
6. Prüfen Sie im Knoten **Apps** im Store, ob die veröffentlichte App angezeigt wird. Die App ist automatisch für die Synchronisierung mit Intune genehmigt.

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Apps zu Gruppen](apps-deploy.md)

