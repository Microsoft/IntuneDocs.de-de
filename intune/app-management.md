---
title: Was ist die Microsoft Intune App-Verwaltung?
titlesuffix: ''
description: Erfahren Sie mehr über die plattformspezifischen Client-App-Verwaltungsfunktionen für Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f2c5da7772ff137e44fead66f00fe34004bb1f4
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850902"
---
# <a name="what-is-microsoft-intune-app-management"></a>Was ist die Microsoft Intune App-Verwaltung?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als IT-Administrator können Sie mit Microsoft Intune die Client-Apps verwalten, die Mitarbeiter Ihres Unternehmens verwenden. Diese Funktion besteht zusätzlich zur Verwaltung von Geräten und dem Schutz von Daten. Eine der Prioritäten eines Administrators ist es, sicherzustellen, dass die Endbenutzer Zugriff auf die Apps haben, die sie für ihre Arbeit benötigen. Dieses Ziel kann aus verschiedenen Gründen eine große Herausforderung darstellen:
- Es gibt eine Vielzahl von Geräteplattformen und App-Typen.
- Sie müssen möglicherweise Apps auf unternehmenseigenen und auf privaten Geräten verwalten.
- Sie müssen sicherstellen, dass Ihr Netzwerk und Ihre Daten weiterhin geschützt sind.

Darüber hinaus sollten Sie Apps auf Geräten, die nicht bei Intune registriert sind, zuweisen und verwalten.

Intune bietet eine Reihe von Funktionen, die die Installation der erforderlichen Apps auf den Geräten unterstützen, auf denen sie ausgeführt werden sollen. Die folgende Tabelle enthält eine Zusammenfassung der App-Verwaltungsfunktionen: 

## <a name="app-management-capabilities-by-platform"></a>App-Verwaltungsfunktionen nach Plattform

|  | Android | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Hinzufügen und Zuweisen von Apps für Geräte und Benutzer | Ja | Ja | Ja | Ja | Ja |
| Zuweisen von Apps für Geräte, die nicht bei Intune registriert sind | Ja | Ja | Nein | Nein | Nein |
| Steuern des Startverhaltens von Apps mithilfe von App-Konfigurationsrichtlinien | Nein | Ja | Nein | Nein | Nein |
| Verwenden von Richtlinien für die Bereitstellung mobiler Apps zum Verlängern abgelaufener Apps | Nein | Ja | Nein | Nein | Nein |
| Schützen von Unternehmensdaten in Apps mit App-Schutzrichtlinien | Ja | Ja | Nein | Nein | Nein |
| Entfernen ausschließlich von Unternehmensdaten aus einer installierten App (Selektive App-Zurücksetzung) | Ja | Ja | Nein | Ja | Ja |
| Überwachen von App-Zuweisungen | Ja | Ja | Ja | Ja | Ja |
| Zuweisen und Nachverfolgen von per Volumenlizenz in einem App-Store erworbenen Apps | Nein | Nein | Nein | Ja | Nein |
| Obligatorische Installation von Apps auf Geräten (erforderlich)2 | Ja | Ja | Ja | Ja | Ja |
| Optionale Installation auf Geräten über das Unternehmensportal (verfügbare Installation) | Ja | Ja | Ja | Ja | Ja |
| Installieren von Verknüpfungen zu Apps im Internet (Weblink) | Ja | Ja | Ja | Ja | Ja |
| Interne (branchenspezifische) Apps | Ja | Ja | Ja | Ja | Nein |
| Apps aus einem Store | Ja | Ja | Nein | Ja | Ja |
| Aktualisierung von Apps | Ja | Ja | Nein | Ja | Ja |

<sup>1</sup> Erwägen Sie die Verwendung [Windows Information Protection](windows-information-protection-configure.md) für den Schutz von Apps auf Geräten mit Windows 10.

<sup>2</sup> Gilt nur für Geräte, die von Intune verwaltet werden.

## <a name="get-started"></a>Erste Schritte

Sie finden die meisten Informationen zu Apps in der Workload **Client-Apps**, auf die Sie wie folgt zugreifen können:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.  
    Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Microsoft Intune** auf die Option **Client-Apps**.

    ![Der Workloadbereich „Client-Apps“](./media/apps-workload.png)

Die nächsten vier Abschnitte beschreiben die Optionen im Bereich **Client-Apps**.

### <a name="manage"></a>Verwalten von
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
- **iOS-App-Bereitstellungsprofile**: iOS-Apps enthalten ein Bereitstellungsprofil und Code, der von einem Zertifikat signiert ist. Wenn das Zertifikat abläuft, kann die App nicht mehr ausgeführt werden. Intune stellt Ihnen die Tools zum proaktiven Zuweisen einer neuen Richtlinie für Bereitstellungsprofile auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen. Weitere Informationen finden Sie in folgenden Quellen:
    - [iOS-App-Bereitstellungsprofile](app-provisioning-profile-ios.md)

Weitere Informationen zu diesem Abschnitt finden Sie unter [Verwalten von Apps](app-management.md).

### <a name="monitor"></a>Überwachen
- **App-Lizenzen**: Hiermit können Sie per Volumenlizenz erworbene Apps aus App-Stores anzeigen, zuweisen und überwachen. Weitere Informationen finden Sie in folgenden Quellen:
    - [Per Volumenlizenzprogramm erworbene iOS-Apps (VPP-Apps)](vpp-apps-ios.md)
    - [Per Volumenlizenz erworbene Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md)
- **Ermittelte Apps**: Zeigen Sie Apps an, die von Intune zugewiesen oder auf einem Gerät installiert wurden. Weitere Informationen finden Sie unter [Anzeigen von Gerätedetails in Microsoft Intune](device-inventory.md).
- **App-Installationsstatus**: Zeigen Sie den Status einer von Ihnen erstellten App-Zuweisung an. Weitere Informationen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Status des App-Schutzes**: Zeigen Sie den Status einer App-Schutzrichtlinie für einen ausgewählten Benutzer an.
- **Überwachungsprotokolle**: Zeigen Sie die App-bezogenen Aktivitäten aller IT-Administratoren in Intune an.

Weitere Informationen zu diesem Abschnitt finden Sie unter [Überwachen von Apps](apps-monitor.md).

### <a name="set-up"></a>Einrichten
- **iOS-VPP-Token**: Hiermit können Sie Ihre iOS-VPP-Lizenzen (Volume Purchase Program) anzeigen und anwenden. Weitere Informationen finden Sie in folgenden Quellen:
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
    - [Problembehandlung](help-desk-operators.md)

## <a name="next-steps"></a>Nächste Schritte

- [So fügen Sie eine App zu Microsoft Intune hinzu](apps-add.md)
