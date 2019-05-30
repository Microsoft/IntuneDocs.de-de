---
title: Konfigurieren der Geräte- und App-Konformität während einer Intune-Migration
titleSuffix: Microsoft Intune
description: Dieser Artikel stellt die für das Konfigurieren der Richtlinien für die Gerätekompatibilität und die App-Verwaltung notwendigen Schritte während einer Migration zu Microsoft Intune bereit.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d3e36dbeb1fb7c90dfc5cc4c18fb30140c761db
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046495"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>Konfigurieren der Richtlinien für die Gerätekompatibilität und die App-Verwaltung während einer Migration zu Microsoft Intune

Das Hauptziel der Migration zu Intune ist die Registrierung aller Geräte in Intune und die Kompatibilität aller Geräte mit ihren Richtlinien. Geräterichtlinien helfen Ihnen nicht nur dabei, firmeneigene Geräte mit nur einem Benutzer zu verwalten, sondern auch bei der Verwaltung persönlicher (Bring-Your-Own-Device, BYOD) und freigegebener Geräte, wie z.B. Kiosks, Verkaufsortcomputer, Tablets, die von mehreren Schülern in einem Klassenzimmer verwendet werden, oder Geräte ohne Benutzer (nur iOS).

Jede Geräteplattform hat möglicherweise unterschiedliche Einstellungen, aber Geräterichtlinien von Intune funktionieren durch folgende MDM-Funktionen mit jeder Geräteplattform:

-   Regulierung der Zahl von Geräten, die jeder Benutzer registriert

-   Verwalten der Geräteeinstellungen (z.B Verschlüsselung auf Geräteebene, Länge des Kennworts, Kameragebrauch)

-   Bereitstellen von Apps, E-Mail-Profilen, VPN-Profilen, etc.

-   Auswerten der Kriterien für Sicherheitskompatibilitätsrichtlinien auf der Geräteebene

> [!IMPORTANT]
> Geräteverwaltungsrichtlinien werden einzelnen Geräten oder Benutzern nicht direkt zugewiesen, sondern ganzen Benutzergruppen. Die Richtlinien können direkt auf Benutzergruppen und somit auch auf das Geräte des Benutzers angewendet werden; die Richtlinien können auch auf eine Gerätegruppe und somit auch auf Gruppenmitglieder angewendet werden.

## <a name="task-list-for-device-compliance-policies"></a>Aufgabenliste für Gerätekompatibilitätsrichtlinien

### <a name="task-1-add-device-groups-optional"></a>Aufgabe 1: Hinzufügen von Gerätegruppen (optional)

Sie können Gerätegruppen erstellen, wenn Sie Verwaltungsaufgaben basierend auf Geräteidentität statt auf Benutzeridentität durchführen müssen.

Benutzergruppen sind nützlich bei der Verwaltung von Geräten ohne dedizierte Benutzer, wie z.B Kioskgeräte, oder von Geräten, die für Schichtarbeiter freigegeben oder einem bestimmtem Standort zugewiesen wurden.

Wenn Sie Gerätegruppen schon vor der Geräteregistrierung konfigurieren, können Sie Gerätekategorien nutzen, um Geräte automatisch mit Gruppen vor der Registrierung zu verknüpfen. Dann erhalten Sie automatisch die Geräterichtlinien ihrer Gruppe. [Erste Schritte mit Gruppen](groups-get-started.md).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Aufgabe 2: Verwenden von Profilen für den Ressourcenzugriff (WLAN, VPN und E-Mail-Zertifikate)

Profile für den Ressourcenzugriff stellen Zertifikate und Zugriffskonfigurationen für die Geräteregistrierung bereit. Wenn Sie eine zertifikatbasierte Authentifizierung nutzen, [konfigurieren Sie Zertifikate](certificates-configure.md).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Aufgabe 3: Erstellen und Bereitstellen von Gerätekonfigurationsprofilen

Sie müssen ein Gerätekonfigurationsprofil erstellen, um Einstellungen auf der Geräteebene zu erzwingen, wie z.B. Deaktivieren der Kamera, App Store, Konfigurieren des Einzelanwendungsmodus, Startbildschirm, etc. Erfahren Sie mehr über [Geräteprofile](device-profiles.md).

####  <a name="directly-import-ios-configuration-profiles-optional"></a>Direkter Import von iOS-Konfigurationsprofilen (optional)

-   **iOS-Profile von Apple Configurator (iOS 7.1 und höher)**: Wenn Ihre vorhandene MDM-Lösung Apple Configurator-Profile verwendet (MOBILECONFIG-Dateien), kann Intune diese direkt als benutzerdefinierte Konfigurationsrichtlinien importieren.

-   **Richtlinien für die Konfiguration von mobilen iOS-Anwendungen**: Wenn Ihre vorhandene MDM-Lösung Richtlinien für die Konfiguration von mobilen iOS-Anwendungen verwendet, kann Intune diese direkt importieren, sofern sie dem XML-Format entsprechen, das von Apple für Eigenschaftenlisten festgelegt wurde.

- Erfahren Sie, wie Sie eine benutzerdefinierte Richtlinie für [iOS](custom-settings-ios.md) hinzufügen können.

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Aufgabe 4: Erstellen und Bereitstellen einer Gerätekonformitätsrichtlinie (optional)

Gerätekonformitätsrichtlinien werten sicherheitsorientierte Einstellungen aus und bieten eine Berichterstattung, die anzeigt, ob die Geräte den Unternehmensansprüchen entsprechen. Dazu zählen die folgenden Einstellungen:

-   PIN-Länge

-   Status „Jail-broken“ (Nutzungsbeschränkungen entfernt)

-   BS-Version

Hier finden Sie weitere Ressourcen für die Einstellungen der Gerätekompatibilität:

-   Erfahren Sie mehr über [Gerätekompatibilitätsrichtlinien](device-compliance.md).

-   Erfahren Sie, wie Sie eine [Gerätekompatibilitätsrichtlinie erstellen](device-compliance-get-started.md) können.

### <a name="task-5-publish-and-deploy-apps"></a>Aufgabe 5: Veröffentlichen und Bereitstellen von Apps

Wenn Sie MDM mit Intune verwenden, können Sie Apps bereitstellen, indem Sie entweder deren automatische Installation verlangen oder sie über das Unternehmensportal zur Verfügung stellen.

-   [So fügen Sie Apps hinzu](apps-add.md)

-   [Bereitstellen von Apps](apps-deploy.md)

### <a name="task-6-enable-device-enrollment"></a>Aufgabe 6: Aktivieren der Geräteregistrierung

Die Geräteregistrierung ist nötig, um das Gerät zu verwalten. Erfahren Sie, wie Sie sich [auf die Registrierung von firmeneigenen und persönlichen Geräten vorbereiten](device-enrollment.md) können.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von App-Schutzrichtlinien (optional)](migration-guide-app-protection-policies.md)
