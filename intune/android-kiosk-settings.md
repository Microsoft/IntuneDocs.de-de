---
title: 'Kioskeinstellungen für Android in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Konfigurieren Sie Ihre Android-Kioskgeräte als Kiosks für einzelne und mehrere Apps.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cef98527ee2c281547f8046f3c6f08275d8f0807
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329382"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Kiosk-Einstellungen für Android-Geräte in Intune

Sie können ein Gerät in den Kioskmodus für einzelne oder mehrere Apps konfigurieren, indem Sie die Gerätekonfigurationseinstellungen verwenden. Wenn ein Gerät im Kioskmodus ist, ist die Nutzung des Geräts auf die Apps oder Weblinks beschränkt, die vom Einschränkungsprofil definiert werden. 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Einschränken eines Android-Kioskgeräts auf eine einzelne App

Wenn das Einschränkungsprofil eines Kioskgeräts auf **Kioskmodus** = **Kiosk mit einzelner App** festgelegt ist, können Benutzer nur auf eine einzelne App zugreifen. Wenn ein in diesem Modus konfiguriertes Gerät gestartet wird, wird die spezifische App gestartet. Benutzer können keine neuen Apps öffnen oder die ausgeführte App ändern.

1. Stellen Sie sicher, dass die App, die auf dem Kioskgerät ausgeführt werden soll, [auf dem Gerät bereitgestellt wurde](apps-deploy.md), und dass Sie die App der Gerätegruppe zugewiesen haben, die Sie für Ihre Kioskgeräte erstellt haben.
2. Navigieren Sie zum [Intune-Portal](https://portal.azure.com), und klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie auf dem Blatt **Profil erstellen** die folgenden Felder fest:
     - **Name**
     - **Plattform:** Android Enterprise
     - **Profiltyp:** Nur Gerätebesitzer > Geräteeinschränkungen
4. Klicken Sie auf **Einstellungen** > **Kiosk**.
5. Wählen Sie **Kiosk mit einzelner App** für den **Kioskmodus** aus.
6. Klicken Sie auf **Verwaltete App auswählen**, und wählen Sie anschließend die verwaltete Google Play-App aus, die Sie als einzige verfügbare App auf Geräten mit diesem Profil festlegen wollen.
7. Klicken Sie auf **OK** > **OK** > **OK** > **Erstellen**.
8. Wählen Sie das Profil aus, das Sie soeben erstellt haben, und klicken Sie dann auf **Zuweisungen**.
9. Wählen Sie **Ausgewählte Gruppen** unter **Zuweisen zu** aus.
10. Klicken Sie auf **Select groups to include** (Einzuschließende Gruppen auswählen), wählen Sie die Gerätegruppe aus, die Sie für Ihre Kioskgeräte erstellt haben, und klicken Sie anschließend auf **Auswählen**.

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>Einschränken eines Kioskgeräts auf mehrere Apps oder Weblinks

Wenn das Einschränkungsprofil eines Kioskgeräts auf **Kioskmodus** = **Multi-App-Kiosk** festgelegt ist, können Benutzer nur auf eine beschränkte Anzahl von Apps zugreifen, die Sie konfigurieren. Außerdem können Sie eine Reihe von Weblinks definieren, die Benutzer besuchen können. Wenn die Richtlinie angewendet wird, können Benutzer die Symbole für die zulässigen Apps auf dem Startbildschirm sehen.

Führen Sie die folgenden Hauptschritte aus, um ein Android-Kioskgerät für mehrere Apps festzulegen:

1. [Importieren und Bereitstellen der Managed Home Screen-App über Managed Google Play](#import-and -deploy-the-managed-home-screen-app)
2. [Hinzufügen und Zuweisen von Apps, die im Kioskmodus verwendet werden können](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. [Hinzufügen von Weblinks, die im Kioskmodus verwendet werden können](#add-web-links-that-can-be-used-in-kiosk-mode) (optional)

### <a name="import-and-deply-the-managed-home-screen-app"></a>Importieren und Bereitstellen der Managed Home Screen-App

1. Navigieren Sie zur [Seite der Managed Home Screen-App in Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise), und melden Sie sich mit dem gleichen Konto an, das Sie für andere Managed Google Play-Apps verwenden.
2. Klicken Sie auf **Genehmigen**.
3. Wechseln Sie zum [Intune-Portal](https://portal.azure.com), und wählen Sie **Client-Apps** > **Verwaltetes Google Play** > **Synchronisieren** aus.
4. Klicken Sie auf **Apps** > **Managed Home Screen** > **Zuweisungen** > **Gruppe hinzufügen**.
5. Klicken Sie unter **Zuweisungstyp** auf **Erforderlich**.
6. Klicken Sie auf **Included groups** > **Select groups to include** (Eingeschlossene Gruppen > Einzuschließende Gruppen auswählen), wählen Sie die Gerätegruppe aus, die Sie für Ihre Kioskgeräte erstellt haben, und klicken Sie anschließend auf **Auswählen** > **OK** > **OK** > **Speichern**.

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>Hinzufügen und Zuweisen von Apps, die im Kioskmodus verwendet werden können

Führen Sie die folgenden Schritte für jede App aus, die Sie auf Ihren Kioskgeräten zur Verfügung stellen möchten:

1. [Fügen Sie die App in Intune hinzu](store-apps-android.md).
2. Wählen Sie **Client-Apps** > **Apps** und dann die App aus, und klicken Sie anschließend auf **Zuweisungen** > **Gruppe hinzufügen**.
3. Klicken Sie unter **Zuweisungstyp** auf **Erforderlich**.
4. Klicken Sie auf **Included groups** > **Select groups to include** (Eingeschlossene Gruppen > Einzuschließende Gruppen auswählen), wählen Sie die Gerätegruppe aus, die Sie für Ihre Kioskgeräte erstellt haben, und klicken Sie anschließend auf **Auswählen** > **OK** > **OK** > **Speichern**.

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>Hinzufügen von Weblinks, die im Kioskmodus verwendet werden können

1. Wechseln Sie zum [Intune-Portal](https://portal.azure.com), und wählen Sie **Client-Apps** > **Apps** > **Hinzufügen** aus.
2. Wählen Sie **Weblink** unter **App-Typ** aus.
3. Klicken Sie auf **Konfigurieren**, und geben Sie die erforderlichen Informationen an. Sie müssen kein Bild für das Logo hinzufügen, da es automatisch aus der Datei „favicon.ico“ der Website abgerufen wird.
4. Klicken Sie auf **OK** > **Hinzufügen**.

Achten Sie darauf, dass Sie eine Webbrowser-App mit [Mobile Apps](apps-add.md) auf dem Kiosk-Gerät bereitstellen.

### <a name="create-a-multi-app-kiosk-profile"></a>Erstellen Sie ein Multi-App-Kioskprofil

1. Navigieren Sie zum [Intune-Portal](https://portal.azure.com), und klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie auf dem Blatt **Profil erstellen** die folgenden Felder fest:
     - **Name:** Geben Sie einen aussagekräftigen Namen ein
     - **Plattform:** Android Enterprise
     - **Profiltyp:** Nur Gerätebesitzer > Geräteeinschränkungen
4. Klicken Sie auf **Einstellungen** > **Kiosk**.
5. Wählen Sie **Multi-App-Kiosk** für den **Kioskmodus** aus.
6. Klicken Sie auf **Hinzufügen**, und wählen Sie dann die Apps oder Weblinks aus, die Sie auf den Geräten mit diesem Profil zur Verfügung stellen möchten.
7. Klicken Sie auf **OK** > **OK** > **OK** > **Erstellen**.
8. Wählen Sie das Profil aus, das Sie soeben erstellt haben, und klicken Sie dann auf **Zuweisungen**.
9. Wählen Sie **Ausgewählte Gruppen** unter **Zuweisen zu** aus.
10. Klicken Sie auf **Select groups to include** (Einzuschließende Gruppen auswählen), wählen Sie die Gerätegruppe aus, die Sie für Ihre Kioskgeräte erstellt haben, und klicken Sie anschließend auf **Auswählen** > **Speichern**.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
