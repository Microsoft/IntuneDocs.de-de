---
title: Konfigurieren von Google Chrome für Android-Geräte mit Intune
titleSuffix: Microsoft Intune
description: Verwenden Sie Intune-Konfigurationsrichtlinien mit Google Chrome für Android-Geräte.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35f52e80f83426c076ac7925d308daacf4595f88
ms.sourcegitcommit: b1e97211db7cb949eb39be6776b3a11d434fdab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251509"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Konfigurieren von Google Chrome für Android-Geräte mit Intune 

Sie können Intune-App-Konfigurationsrichtlinien zum Konfigurieren von Google Chrome für Android-Geräte verwenden. Die Einstellungen für die App können automatisch angewendet werden. Beispielsweise können Sie explizit die Lesezeichen und URLs festlegen, die Sie blockieren oder zulassen möchten.

## <a name="prerequisites"></a>Voraussetzungen

- Das Android Enterprise-Gerät muss bei Intune registriert sein. Weitere Informationen finden Sie unter [Einrichten der Registrierung von Android Enterprise-Arbeitsprofilgeräten](~/enrollment/android-work-profile-enroll.md).
- Google Chrome wird als verwaltete Google Play-App hinzugefügt. Weitere Informationen zu verwaltetem Google Play finden Sie unter [Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>Hinzufügen der Google Chrome-App zu Intune

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie im Bereich **Intune** die Option **Client-Apps** > **Apps** > **Hinzufügen** aus, und fügen Sie dann die **Verwaltete Google Play**-App hinzu.
3. Wechseln Sie zu verwaltetem Google Play, suchen Sie **Google Chrome**, und erteilen Sie die Genehmigung.

    ![Suchen und Genehmigen von Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Weisen Sie Google Chrome einer Benutzergruppe als erforderlicher App-Typ zu. Google Chrome wird automatisch bereitgestellt, wenn das Gerät bei Intune registriert wird.

Weitere Informationen zum Hinzufügen einer verwalteten Google Play-App zu Intune finden Sie unter [Apps im verwalteten Google Play Store](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-an-app-configuration-policy-for-managed-android-enterprise-devices"></a>Hinzufügen einer App-Konfigurationsrichtlinie für verwaltete Android Enterprise-Geräte

1. Wählen Sie im Bereich [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) die Option **App-Konfigurationsrichtlinien** > **Hinzufügen** aus.
2. Fügen Sie den Richtliniennamen hinzu, und wählen Sie **Verwaltete Geräte** unter „Geräteregistrierungstyp“ und **Android** unter „Plattform“ aus.

    ![Hinzufügen einer Google Chrome-Konfigurationsrichtlinie](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Klicken Sie auf **Zugeordnete App**, und wählen Sie **Google Chrome**  aus.

    ![Auswählen von Google Chrome unter „Zugeordnete App“](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Klicken Sie auf **Konfigurationseinstellungen**, wählen Sie **Konfigurations-Designer verwenden** aus, und klicken Sie dann auf **Hinzufügen**, um die Konfigurationsschlüssel auszuwählen.

    ![Hinzufügen von „Konfigurations-Designer verwenden“](~/apps/media/apps-configure-chrome-android/configuration.png)

    Im Folgenden finden Sie ein Beispiel für die allgemeinen Einstellungen:
    - **Zugriff auf eine Liste von URLs blockieren**: `["*"]`
    - **Zugriff auf eine Liste von URLs zulassen**: `["baidu.com", "yahoo.com", "chrome://*"]`
    - **Verwaltete Lesezeichen**: `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Verfügbarkeit des Inkognito-Modus**: `Incognito mode disabled`

    Nachdem die Konfigurationseinstellungen mit dem Konfigurations-Designer hinzugefügt wurden, werden sie in einer Tabelle aufgelistet. 

    ![Allgemeine Einstellungen](~/apps/media/apps-configure-chrome-android/common-settings.png)

    Mit den obigen Einstellungen werden Lesezeichen erstellt und der Zugriff auf alle Websites mit Ausnahme von `baidu.com`, `yahoo.com` und `chrome://` ermöglicht.

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
