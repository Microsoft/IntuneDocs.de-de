---
title: Was ist die Microsoft Intune App-Verwaltung?
titlesuffix: ''
description: In diesem Thema lernen Sie die Grundlagen der App-Verwaltung mit Microsoft Intune kennen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6d11de1e20f46fb6e13d6d3ef5c9f4a9ee0f98c1
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223780"
---
# <a name="what-is-microsoft-intune-app-management"></a>Was ist die Microsoft Intune App-Verwaltung?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als IT-Administrator können Sie mit Microsoft Intune die mobilen Apps verwalten, die Mitarbeiter Ihres Unternehmens verwenden. Diese Funktion besteht zusätzlich zur Verwaltung von Geräten und dem Schutz von Daten. Eine der Prioritäten eines Administrators ist es, sicherzustellen, dass die Endbenutzer Zugriff auf die Apps haben, die sie für ihre Arbeit benötigen. Dieses Ziel kann aus verschiedenen Gründen eine große Herausforderung darstellen:
- Es gibt eine Vielzahl von Geräteplattformen und App-Typen.
- Sie müssen möglicherweise Apps auf unternehmenseigenen und auf privaten Geräten verwalten.
- Sie müssen sicherstellen, dass Ihr Netzwerk und Ihre Daten weiterhin geschützt sind.

Darüber hinaus sollten Sie Apps auf Geräten, die nicht bei Intune registriert sind, zuweisen und verwalten.

Intune bietet eine Reihe von Funktionen, die die Installation der erforderlichen Apps auf den Geräten unterstützen, auf denen sie ausgeführt werden sollen. Die folgende Tabelle enthält eine Zusammenfassung der App-Verwaltungsfunktionen: 

## <a name="app-management-capabilities-by-platform"></a>App-Verwaltungsfunktionen nach Plattform

||||||
|-|-|-|-|-|
| |Android|iOS|Windows Phone 8.1|Windows 10|
|Hinzufügen und Zuweisen von Apps für Geräte und Benutzer|Ja |Ja |Ja |Ja |
|Zuweisen von Apps für Geräte, die nicht bei Intune registriert sind|Ja |Ja |Nein|Nein|
|Steuern des Startverhaltens von Apps mithilfe von App-Konfigurationsrichtlinien|Nein|Ja |Nein|Nein|
|Verwenden von Richtlinien für die Bereitstellung mobiler Apps zum Verlängern abgelaufener Apps|Nein|Ja |Nein|Nein|
|Schützen von Unternehmensdaten in Apps mit App-Schutzrichtlinien|Ja |Ja |Nein|Nein<sup>1</sup>|
|Entfernen ausschließlich von Unternehmensdaten aus einer installierten App (Selektive App-Zurücksetzung)|Ja |Ja |Ja |Ja |
|Überwachen von App-Zuweisungen|Ja |Ja |Ja |Ja |
|Zuweisen und Nachverfolgen von Per Volumenlizenz in einem App-Store erworbenen Apps|Nein|Nein|Nein|Ja |
|Obligatorische Installation von Apps auf Geräten (erforderlich)<sup>2</sup>|Ja |Ja |Ja |Ja |
|Optionale Installation auf Geräten über das Unternehmensportal (verfügbare Installation)|Ja |Ja |Ja |Ja |
|Installieren von Verknüpfungen zu Apps im Internet (Weblink)|Ja |Ja |Ja |Ja |
|Interne (branchenspezifische) Apps|Ja |Ja |Nein|Ja |
|Apps aus einem Store|Ja |Ja |Ja |Ja |
|Aktualisierung von Apps|Ja |Ja |Ja |Ja |

<sup>1</sup> Erwägen Sie die Verwendung [Windows Information Protection](windows-information-protection-configure.md) für den Schutz von Apps auf Geräten mit Windows 10.

<sup>2</sup> Gilt nur für Geräte, die von Intune verwaltet werden.

## <a name="get-started"></a>Erste Schritte

Sie finden die meisten Informationen zu Apps im Workload **Mobile Apps**, auf die Sie wie folgt zugreifen können:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.  
    Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Microsoft Intune** auf die Option **Mobile Apps**.

    ![Workloadbereich „Mobile Apps“](./media/apps-workload.png)

Die nächsten vier Abschnitte beschreiben die Optionen im Bereich **Mobile Apps**.

### <a name="manage"></a>Verwalten von
- **Apps**: Wählen Sie diese Option aus, um die von Ihren Mitarbeitern verwendeten Apps hinzuzufügen, anzuzeigen, zuzuweisen und zu überwachen. Weitere Informationen finden Sie in folgenden Quellen:
    - [Hinzufügen von Apps](apps-add.md)
    - [Zuweisen von Apps](apps-deploy.md)
    - [Überwachen von Apps](apps-monitor.md)
- **Konfigurationsrichtlinien für Apps**: Wählen Sie diese Option, um Einstellungen anzugeben, die beim Ausführen einer App durch den Benutzer erforderlich sind. Weitere Informationen finden Sie in folgenden Quellen:
    - [App-Konfigurationsrichtlinien für Intune](app-configuration-policies-overview.md)
        - [iOS-App-Konfigurationsrichtlinien](app-configuration-policies-use-ios.md)
        - [Android-App-Konfigurationsrichtlinien](app-configuration-policies-use-android.md)
- **App-Schutzrichtlinien:** Wählen Sie diese Option, um Einstellungen für eine App zum Schutz der Unternehmensdaten, die diese verwendet, hinzuzufügen. Sie können z.B. die Funktionen einer App zur Kommunikation mit anderen Apps einschränken oder erzwingen, dass der Benutzer eine PIN eingeben muss, um auf eine Unternehmens-App zuzugreifen. Weitere Informationen finden Sie in folgenden Quellen:
    - [App-Schutzrichtlinien](app-protection-policies.md)
- **Selektive App-Zurücksetzung**: Wählen Sie diese Option, um nur Unternehmensdaten vom Gerät eines ausgewählten Benutzers zu entfernen. Weitere Informationen finden Sie in folgenden Quellen:
    - [Selektive App-Zurücksetzung](apps-selective-wipe.md)
- **iOS-App-Bereitstellungsprofile**: iOS-Apps enthalten ein Bereitstellungsprofil und Code, der von einem Zertifikat signiert ist. Wenn das Zertifikat abläuft, kann die App nicht mehr ausgeführt werden. Intune stellt Ihnen die Tools zum proaktiven Zuweisen einer neuen Richtlinie für Bereitstellungsprofile auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen. Weitere Informationen finden Sie in folgenden Quellen:
    - [iOS-App-Bereitstellungsprofile](app-provisioning-profile-ios.md)

Weitere Informationen zu diesem Abschnitt finden Sie unter [Verwalten von Apps](app-management.md).

### <a name="monitor"></a>Überwachen
- **App-Lizenzen**: Ermöglicht das Anzeigen, Zuweisen und Überwachen von per Volumenlizenz erworbenen Apps aus App Stores. Weitere Informationen finden Sie in folgenden Quellen:
    - [Per Volumenlizenzprogramm erworbene iOS-Apps (VPP-Apps)](vpp-apps-ios.md)
    - [Per Volumenlizenz erworbene Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md)
- **Ermittelte Apps**: Zeigt alle Apps an, die von Intune zugewiesen und auf einem Gerät installiert wurden.
- **App-Installationsstatus:** Zeigt den Status einer App-Zuweisung, die Sie erstellt haben.
- **App-Schutzstatus:** Zeigt den Status einer App-Schutzrichtlinie für einen ausgewählten Benutzer an.
- **Überwachungsprotokolle**: Zeigt die Aktivität aller IT-Administratoren in Bezug auf die Intune-App an.

Weitere Informationen zu diesem Abschnitt finden Sie unter [Überwachen von Apps](apps-monitor.md).

### <a name="set-up"></a>Einrichten
- **iOS-VPP-Token**: Wendet iOS-VPP-Lizenzen (Volume Purchase Program) an, und zeigt diese an. Weitere Informationen finden Sie in folgenden Quellen:
    - [Per Volumenlizenz erworbene Apps](vpp-apps-ios.md)
- **Windows Enterprise-Zertifikat**: Wendet den Status eines codesignierenden Zertifikats an, das zur Verteilung von branchenspezifischen Apps an Ihre verwalteten Windows-Geräte verwendet wird, oder zeigt diesen an.
- **Windows-Symantec-Zertifikat**: Wendet den Status eines codesignierenden Symantec-Zertifikats an, das zur Verteilung von XAP- und WP8.x-APPX-Dateien an Windows 10 Mobile-Geräten erforderlich ist, oder zeigt diesen an.
- **Microsoft Store für Unternehmen**: Richten Sie die Integration in den Microsoft Store für Unternehmen ein. Anschließend können Sie erworbene Anwendungen mit Intune synchronisieren, sie zuweisen und Ihre Lizenznutzung verfolgen. Weitere Informationen finden Sie in folgenden Quellen:
    - [Per Volumenlizenz erworbene Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md)
- **Windows-Schlüssel zum Querladen**: Fügen Sie einen Windows-Schlüssel zum Querladen hinzu, mit dem Sie eine App direkt auf Geräten installieren können, anstatt die App im Microsoft Store zu veröffentlichen und von diesem herunterzuladen. Weitere Informationen finden Sie in folgenden Quellen:
    - [Querladen einer Windows-App](app-sideload-windows.md)
- **Unternehmensportalbranding:** Passen Sie das Unternehmensportal mit Ihrem Unternehmensbranding an. Weitere Informationen finden Sie in folgenden Quellen:
    - [Konfiguration des Unternehmensportals](company-portal-app.md)
- **App-Kategorien**: Ermöglicht das Hinzufügen, Anheften und Löschen von App-Kategorienamen.
- **Android for Work**: Genehmigt und synchronisiert die Apps, die Sie für Ihr Unternehmen genehmigt haben. Weitere Informationen finden Sie in folgenden Quellen:
    - [Android for Work-Apps](apps-add-android-for-work.md)

### <a name="help-and-support"></a>Hilfe und Support
- **Hilfe und Support**: Ermöglicht das Behandeln von Problemen, das Anfordern von Unterstützung oder das Anzeigen des Intune-Status. Weitere Informationen finden Sie in folgenden Quellen:
    - [Problembehandlung](help-desk-operators.md)

## <a name="next-steps"></a>Nächste Schritte

- [So fügen Sie eine App zu Microsoft Intune hinzu](apps-add.md)
