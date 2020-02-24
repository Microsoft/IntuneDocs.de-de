---
title: Was ist die Microsoft Intune App-Verwaltung?
titleSuffix: ''
description: Erfahren Sie mehr über die plattformspezifischen Client-App-Verwaltungsfunktionen für Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 84d33e0ff6bbe407d9838f97214f37d042a2e261
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414701"
---
# <a name="what-is-microsoft-intune-app-management"></a>Was ist die Microsoft Intune App-Verwaltung?


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Als IT-Administrator können Sie mit Microsoft Intune die Client-Apps verwalten, die Mitarbeiter Ihres Unternehmens verwenden. Diese Funktion besteht zusätzlich zur Verwaltung von Geräten und dem Schutz von Daten. Eine der Prioritäten eines Administrators ist es, sicherzustellen, dass die Endbenutzer Zugriff auf die Apps haben, die sie für ihre Arbeit benötigen. Dieses Ziel kann aus verschiedenen Gründen eine große Herausforderung darstellen:
- Es gibt eine Vielzahl von Geräteplattformen und App-Typen.
- Sie müssen möglicherweise Apps auf unternehmenseigenen und auf privaten Geräten verwalten.
- Sie müssen sicherstellen, dass Ihr Netzwerk und Ihre Daten weiterhin geschützt sind.

Darüber hinaus sollten Sie Apps auf Geräten, die nicht bei Intune registriert sind, zuweisen und verwalten.

## <a name="mobile-application-management-mam-basics"></a>Grundlagen der Verwaltung mobiler Anwendungen (Mobile Application Management, MAM)

Die [mobile Anwendungsverwaltung (Mobile Application Management, MAM) von Intune](app-lifecycle.md) bezeichnet die Intune-Verwaltungsfunktionen, mit denen Sie mobile Apps für Ihre Benutzer veröffentlichen, per Push bereitstellen, konfigurieren, schützen, überwachen und aktualisieren.

MAM ermöglicht es Ihnen, die Daten Ihres Unternehmens innerhalb einer Anwendung zu verwalten und zu schützen. Mit **MAM ohne Geräteregistrierung** (MAM-WE) kann eine Geschäfts-, Schul- oder Uni-App, die vertrauliche Daten enthält, auf nahezu jedem [Gerät](app-management.md#app-management-capabilities-by-platform) verwaltet werden, auch auf persönlichen Geräten in **BYOD-Szenarios (Bring Your Own Device)** . Viele Produktivitäts-Apps, wie z. B. die Microsoft Office-Apps, können über Intune MAM verwaltet werden. Weitere Informationen finden Sie in der Liste von in [Microsoft Intune verwalteten Apps](apps-supported-intune-apps.md), die für die Öffentlichkeit verfügbar ist.

Intune MAM unterstützt zwei Konfigurationen:
- **Intune MDM und MAM**: IT-Administratoren können Apps mithilfe von MAM und App-Schutzrichtlinien nur auf Geräten verwalten, die bei der Intune-Verwaltung mobiler Geräte (Mobile Device Management, MDM) registriert sind. Um Apps mithilfe von MDM und MAM zu verwalten, sollten Kunden die Intune-Konsole im Azure-Portal unter https://portal.azure.com verwenden.
- **MAM ohne Geräteregistrierung**: Mit MAM ohne Geräteregistrierung (MAM without enrollment, MAM-WE) können IT-Administratoren Apps mithilfe von MAM und App-Schutzrichtlinien auf Geräten verwalten, die nicht bei Intune MDM registriert sind. Dies bedeutet, dass Apps über Intune auf Geräten verwaltet werden können, die bei EMM-Drittanbietern registriert sind. Um Apps mithilfe von MAM-WE zu verwalten, sollten Kunden unter https://portal.azure.com die Intune-Konsole im Azure-Portal verwenden. Darüber hinaus können Apps auf Geräten, die entweder bei EMM-Drittanbietern (Enterprise Mobility Management, EMM) oder überhaupt nicht bei einer MDM registriert sind, von Intune verwaltet werden. Weitere Informationen über BYOD und EMS von Microsoft finden Sie unter [ Technologieentscheidungen zur Ermöglichung von BYOD mit Microsoft Enterprise Mobility + Security (EMS)](../fundamentals/byod-technology-decisions.md).

## <a name="app-management-capabilities-by-platform"></a>App-Verwaltungsfunktionen nach Plattform

Intune bietet eine Reihe von Funktionen, die die Installation der erforderlichen Apps auf den Geräten unterstützen, auf denen sie ausgeführt werden sollen. Die folgende Tabelle enthält eine Zusammenfassung der App-Verwaltungsfunktionen.

|  | Android/Android Enterprise | iOS/iPadOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Hinzufügen und Zuweisen von Apps für Geräte und Benutzer | Ja | Ja | Ja | Ja | Ja |
| Zuweisen von Apps für Geräte, die nicht bei Intune registriert sind | Ja | Ja | Nein | Nein | Nein |
| Steuern des Startverhaltens von Apps mithilfe von App-Konfigurationsrichtlinien | Ja | Ja | Nein | Nein | Nein |
| Verwenden von Richtlinien für die Bereitstellung mobiler Apps zum Verlängern abgelaufener Apps | Nein | Ja | Nein | Nein | Nein |
| Schützen von Unternehmensdaten in Apps mit App-Schutzrichtlinien | Ja | Ja | Nein | Nein <sup>1</sup> | Nein |
| Entfernen ausschließlich von Unternehmensdaten aus einer installierten App (Selektive App-Zurücksetzung) | Ja | Ja | Nein | Ja | Ja |
| Überwachen von App-Zuweisungen | Ja | Ja | Ja | Ja | Ja |
| Zuweisen und Nachverfolgen von per Volumenlizenz in einem App-Store erworbenen Apps | Nein | Nein | Nein | Ja | Nein |
| Obligatorische Installation von Apps auf Geräten (erforderlich) <sup>2</sup> | Ja | Ja | Ja | Ja | Ja |
| Optionale Installation auf Geräten über das Unternehmensportal (verfügbare Installation) | Ja <sup>3</sup> | Ja | Ja | Ja | Ja |
| Installieren von Verknüpfungen zu Apps im Internet (Weblink) | Ja <sup>4</sup> | Ja | Ja | Ja | Ja |
| Interne (branchenspezifische) Apps | Ja | Ja | Ja | Ja | Nein |
| Apps aus einem Store | Ja | Ja | Nein | Ja | Ja |
| Aktualisierung von Apps | Ja | Ja | Nein | Ja | Ja |

<sup>1</sup> Erwägen Sie die Verwendung [Windows Information Protection](../protect/windows-information-protection-configure.md) für den Schutz von Apps auf Geräten mit Windows 10.<br>
<sup>2</sup> Gilt nur für Geräte, die von Intune verwaltet werden.<br>
<sup>3</sup> Intune unterstützt verfügbare Apps aus dem verwalteten Google Play Store auf Android Enterprise-Geräten.<br>
<sup>4</sup> Intune bietet keine Möglichkeit, eine Verknüpfung zu einer App als Weblink auf Standard Android Enterprise-Geräten zu installieren. Jedoch wird die Unterstützung von Weblinks für [dedizierte Android Enterprise-Geräte mit mehreren Apps](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings) bereitgestellt. 


## <a name="get-started"></a>Erste Schritte

Sie finden die meisten Informationen zu Apps im Workload **Apps**, auf die Sie wie folgt zugreifen können:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Klicken Sie auf **Apps**.

    ![Apps-Workloadbereich](./media/app-management/apps-workload.png)

Die nächsten vier Abschnitte beschreiben die Optionen im Bereich **Apps**.

### <a name="manage"></a>Verwalten
- **Apps**: Wählen Sie diese Option aus, um die von Ihren Mitarbeitern verwendeten Apps hinzuzufügen, anzuzeigen, zuzuweisen und zu überwachen. Weitere Informationen finden Sie in folgenden Quellen:
  - [Hinzufügen von Apps](apps-add.md)
  - [Zuweisen von Apps](apps-deploy.md)
  - [Überwachen von Apps](apps-monitor.md)
- **App-Konfigurationsrichtlinien**: Wählen Sie diese Option aus, um Einstellungen anzugeben, die beim Ausführen einer App durch einen Benutzer möglicherweise erforderlich sind. Weitere Informationen finden Sie in folgenden Quellen:
  - [App-Konfigurationsrichtlinien für Intune](app-configuration-policies-overview.md)
    - [iOS-App-Konfigurationsrichtlinien](app-configuration-policies-use-ios.md)
    - [Android-App-Konfigurationsrichtlinien](app-configuration-policies-use-android.md)
- **App-Schutzrichtlinien**: Wählen Sie diese Option aus, um einer App Einstellungen zuzuweisen und so die Unternehmensdaten zu schützen, die diese App verwendet. Sie können z.B. die Funktionen einer App zur Kommunikation mit anderen Apps einschränken oder erzwingen, dass der Benutzer eine PIN eingeben muss, um auf eine Unternehmens-App zuzugreifen. Weitere Informationen finden Sie in folgenden Quellen:
  - [App-Schutzrichtlinien](app-protection-policies.md)
- **Selektive App-Zurücksetzung**: Wählen Sie diese Option aus, um nur Unternehmensdaten vom Gerät eines ausgewählten Benutzers zu entfernen. Weitere Informationen finden Sie in folgenden Quellen:
  - [Selektive App-Zurücksetzung](apps-selective-wipe.md)
- **iOS-App-Bereitstellungsprofile**: iOS-/iPadOS-Apps enthalten ein Bereitstellungsprofil und Code, der von einem Zertifikat signiert ist. Wenn das Zertifikat abläuft, kann die App nicht mehr ausgeführt werden. Intune stellt Ihnen die Tools zum proaktiven Zuweisen einer neuen Richtlinie für Bereitstellungsprofile auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen. Weitere Informationen finden Sie in folgenden Quellen:
  - [iOS-App-Bereitstellungsprofile](app-provisioning-profile-ios.md)

Weitere Informationen zu diesem Abschnitt finden Sie unter [Verwalten von Apps](app-management.md).

### <a name="monitor"></a>Überwachen
- **App-Lizenzen**: Hiermit können Sie per Volumenlizenz erworbene Apps aus App-Stores anzeigen, zuweisen und überwachen. Weitere Informationen finden Sie in folgenden Quellen:
  - [Per Volumenlizenzprogramm erworbene iOS-Apps (VPP-Apps)](vpp-apps-ios.md)
  - [Per Volumenlizenz erworbene Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md)
- **Ermittelte Apps**: Zeigen Sie Apps an, die von Intune zugewiesen oder auf einem Gerät installiert wurden. Weitere Informationen finden Sie unter [Von Intune ermittelte Apps](app-discovered-apps.md).
- **App-Installationsstatus**: Zeigen Sie den Status einer von Ihnen erstellten App-Zuweisung an. Weitere Informationen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Status des App-Schutzes**: Zeigen Sie den Status einer App-Schutzrichtlinie für einen ausgewählten Benutzer an.
- **Überwachungsprotokolle**: Zeigen Sie die App-bezogenen Aktivitäten aller IT-Administratoren in Intune an.

Weitere Informationen zu diesem Abschnitt finden Sie unter [Überwachen von Apps](apps-monitor.md).

### <a name="set-up"></a>Einrichtung
- **iOS-VPP-Token**: Hiermit können Sie Ihre iOS-/iPadOS-VPP-Lizenzen (Volume Purchase Program) anzeigen und anwenden. Weitere Informationen finden Sie in folgenden Quellen:
  - [Per Volumenlizenz erworbene Apps](vpp-apps-ios.md)
- **Windows Enterprise-Zertifikat**: Hiermit können Sie den Status eines codesignierenden Zertifikats anwenden oder anzeigen, das zur Verteilung von branchenspezifischen Apps an Ihre verwalteten Windows-Geräte verwendet wird.
- **Windows-Symantec-Zertifikat**: Hiermit können Sie den Status eines codesignierenden Symantec-Zertifikats anwenden oder anzeigen, das zur Verteilung von XAP- und WP8.x-APPX-Dateien an Windows 10 Mobile-Geräten erforderlich ist.
- **Microsoft Store für Unternehmen**: Richten Sie die Integration in den Microsoft Store für Unternehmen ein. Anschließend können Sie erworbene Anwendungen mit Intune synchronisieren, sie zuweisen und Ihre Lizenznutzung verfolgen. Weitere Informationen finden Sie in folgenden Quellen:
  - [Per Volumenlizenz erworbene Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md)
- **Windows-Schlüssel zum Querladen**: Fügen Sie einen Windows-Schlüssel zum Querladen hinzu, mit dem Sie eine App direkt auf Geräten installieren können, anstatt die App im Microsoft Store zu veröffentlichen und aus diesem herunterzuladen. Weitere Informationen finden Sie in folgenden Quellen:
  - [Querladen einer Windows-App](app-sideload-windows.md)
- **Branding des Unternehmensportals**: Passen Sie das Unternehmensportal mit Ihrem Unternehmensbranding an. Weitere Informationen finden Sie in folgenden Quellen:
  - [Konfiguration des Unternehmensportals](company-portal-app.md)
- **App-Kategorien**: Hiermit können Sie App-Kategorienamen hinzufügen, anheften und löschen.
- **Android-Arbeitsprofil**: Genehmigen und synchronisieren Sie die Apps, die Sie für Ihr Unternehmen genehmigt haben. Weitere Informationen finden Sie in folgenden Quellen:
  - [Android-Arbeitsprofil-Apps](apps-add-android-for-work.md)

### <a name="help-and-support"></a>Hilfe und Support
- **Hilfe und Support**: Hiermit können Sie Probleme behandeln, Unterstützung anfordern oder den Intune-Status anzeigen. Weitere Informationen finden Sie in folgenden Quellen:
  - [Problembehandlung](../fundamentals/help-desk-operators.md)

## <a name="next-steps"></a>Nächste Schritte

- [So fügen Sie eine App zu Microsoft Intune hinzu](apps-add.md)
