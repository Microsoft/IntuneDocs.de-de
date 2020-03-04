---
title: Konfigurieren von Google Chrome für Android-Geräte mit Intune
titleSuffix: Microsoft Intune
description: Verwenden Sie Intune-Konfigurationsrichtlinien mit Google Chrome für Android-Geräte.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78e0e8560c64a1d6be4fa5e01aa9ce32b8a4c613
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181771"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Konfigurieren von Google Chrome für Android-Geräte mit Intune 

Sie können Intune-App-Konfigurationsrichtlinien zum Konfigurieren von Google Chrome für Android-Geräte verwenden. Die Einstellungen für die App können automatisch angewendet werden. Beispielsweise können Sie explizit die Lesezeichen und URLs festlegen, die Sie blockieren oder zulassen möchten.

## <a name="prerequisites"></a>Voraussetzungen

- Das Android Enterprise-Gerät muss bei Intune registriert sein. Weitere Informationen finden Sie unter [Einrichten der Registrierung von Android Enterprise-Arbeitsprofilgeräten](~/enrollment/android-work-profile-enroll.md).
- Google Chrome wird als verwaltete Google Play-App hinzugefügt. Weitere Informationen zu verwaltetem Google Play finden Sie unter [Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>Hinzufügen der Google Chrome-App zu Intune

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus, und fügen Sie dann die App **Verwaltetes Google Play** hinzu.
3. Wechseln Sie zu verwaltetem Google Play, suchen Sie **Google Chrome**, und erteilen Sie die Genehmigung.

    ![Suchen und Genehmigen von Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Weisen Sie Google Chrome einer Benutzergruppe als erforderlicher App-Typ zu. Google Chrome wird automatisch bereitgestellt, wenn das Gerät bei Intune registriert wird.

Weitere Informationen zum Hinzufügen einer verwalteten Google Play-App zu Intune finden Sie unter [Apps im verwalteten Google Play Store](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-app-configuration-for-managed-ae-devices"></a>Hinzufügen der App-Konfiguration für verwaltete AE-Geräte

1. Navigieren Sie zum [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), und wählen Sie **Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen** > **Verwaltete Geräte** aus.
2. Legen Sie die folgenden Details fest:
    - **Name:** Der Name des Profils, das im Azure-Portal angezeigt wird.
    - **Beschreibung:** Die Beschreibung des Profils, das im Azure-Portal angezeigt wird.
    - **Geräteregistrierungstyp:** Diese Einstellung ist auf **Verwaltete Geräte** festgelegt.
    - **Plattform:** Wählen Sie **Android** aus.

    ![Hinzufügen einer Google Chrome-Konfigurationsrichtlinie](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Klicken Sie auf **Zugeordnete App**, um den Bereich **Zugeordnete App** anzuzeigen. Suchen Sie nach **Google Chrome**. Diese Liste enthält [verwaltete Google Play-Apps aus, die Sie genehmigt und mit Intune synchronisiert haben](~/apps/apps-add-android-for-work.md).

    ![Auswählen von Google Chrome unter „Zugeordnete App“](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Klicken Sie auf **Konfigurationseinstellungen**, wählen Sie **Konfigurations-Designer verwenden** aus, und klicken Sie dann auf **Hinzufügen**, um die Konfigurationsschlüssel auszuwählen.

    ![Hinzufügen von „Konfigurations-Designer verwenden“](~/apps/media/apps-configure-chrome-android/configuration.png)

    Im Folgenden finden Sie ein Beispiel für die allgemeinen Einstellungen:
    - **Zugriff auf eine Liste von URLs blockieren**: `["*"]`
    - **Zugriff auf eine Liste von URLs zulassen**: `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **Verwaltete Lesezeichen**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Verfügbarkeit des Inkognito-Modus**: `Incognito mode disabled`

    Nachdem die Konfigurationseinstellungen mit dem Konfigurations-Designer hinzugefügt wurden, werden sie in einer Tabelle aufgelistet. 

    ![Allgemeine Einstellungen](~/apps/media/apps-configure-chrome-android/common-settings.png)

    Mit den obigen Einstellungen werden Lesezeichen erstellt und der Zugriff auf alle URLs mit Ausnahme von `baidu.com`, `yahoo.com`, `chromium.org` und `chrome://` blockiert.

5. Klicken Sie auf **OK** und **Hinzufügen**, um Intune die Konfigurationsrichtlinie hinzuzufügen.
6. Weisen Sie diese Konfigurationsrichtlinie einer Benutzergruppe zu. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Überprüfen der Geräteeinstellungen

Sobald das Android-Gerät bei Android Enterprise registriert ist, wird die verwaltete Google Chrome-App mit dem Portfoliosymbol automatisch bereitgestellt.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Sobald Sie Google Chrome starten, werden die Einstellungen angewendet.

   Lesezeichen:<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   Blockierte URL:<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   Zugelassene URL:<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Registerkarte „Inkognito“:<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Problembehandlung

1. Überwachen Sie im Intune-Portal den Bereitstellungsstatus der Richtlinie.

    ![Überwachen des Bereitstellungsstatus der Richtlinie](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Starten Sie Google Chrome, und besuchen Sie **chrome://policy**. Wir können überprüfen, ob die Einstellungen erfolgreich angewendet werden.

    ![Überprüfen der erfolgreichen Anwendung der Einstellungen](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>Zusätzliche Informationen

- [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android Enterprise-Geräte](~/app-configuration-policies-use-android.md)
- [Chrome Enterprise-Richtlinienliste](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu vollständig verwalteten Android Enterprise-Geräten finden Sie unter [Einrichten der Intune-Registrierung für vollständig verwaltete Android Enterprise-Geräte](~/enrollment/android-fully-managed-enroll.md).
