---
title: Aktivieren des Mobile Threat Defense-Connector für nicht registrierte Geräte
titleSuffix: Microsoft Intune
description: Aktivieren des Mobile Threat Defense-Connector in Microsoft Intune für nicht registrierte Geräte.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 84f82cf2fde7d400e5531bac219b6cbb4877032f
ms.sourcegitcommit: 960ffb2214c35d75ad219fa2571a999529a0abd4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74478926"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Aktivieren des Mobile Threat Defense-Connector in Intune für nicht registrierte Geräte

Während des Mobile Threat Defense-Setups (MTD) haben Sie eine Richtlinie zum Klassifizieren von Bedrohungen in Ihrer Mobile Threat Defense-Partnerkonsole konfiguriert und die App-Schutzrichtlinie in Intune erstellt. Wenn Sie den Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert haben, können Sie nun die MTD-Verbindung für MTD-Partneranwendungen aktivieren.

> [!NOTE]
> Dieser Artikel gilt für alle Mobile Threat Defense-Partner, die App-Schutzrichtlinien unterstützen: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Klassische Richtlinien für bedingten Zugriff für MTD-Apps

Wenn Sie eine neue Anwendung in Intune Mobile Threat Defense integrieren und die Verbindung mit Intune aktivieren, erstellt Intune eine klassische Richtlinie für den bedingten Zugriff in Azure Active Directory. Jede MTD-App, die Sie integrieren (einschließlich [Defender ATP](advanced-threat-protection.md) oder jedes unserer zusätzlichen [MTD-Partner](mobile-threat-defense.md#mobile-threat-defense-partners)), erstellt eine neue klassische Richtlinie für bedingten Zugriff. Diese Richtlinien können ignoriert werden, dürfen jedoch nicht bearbeitet, gelöscht oder deaktiviert werden.

Wenn die klassische Richtlinie gelöscht wird, müssen Sie die für die Erstellung dieser Richtlinie verantwortliche Verbindung mit Intune löschen und anschließend erneut einrichten. Durch diesen Prozess wird die klassische Richtlinie neu erstellt. Es wird keine Unterstützung für die Migration klassischer Richtlinien für MTD-Apps zum neuen Richtlinientyp für bedingten Zugriff bereitgestellt.

Klassische bedingte Zugriffsrichtlinien für MTD-Apps:

- Sie werden von Intune MTD verwendet und verlangen, dass Geräte in Azure AD registriert werden, damit sie eine Geräte-ID erhalten, bevor Kommunikation mit MTD-Partnern erfolgt. Die ID ist erforderlich, damit Geräte ihren Status erfolgreich an Intune melden können.

- Sie haben keine Auswirkung auf andere Cloud-Apps oder Ressourcen.

- Die Zugriffsrichtlinien unterscheiden sich von Richtlinien für bedingten Zugriff, die Sie möglicherweise erstellen, damit sie Ihnen bei der Verwaltung von MTD helfen.

- Standardmäßig interagieren sie nicht mit anderen Richtlinien für den bedingten Zugriff, die Sie für die Auswertung verwenden.

Wenn Sie klassische Richtlinien für den bedingten Zugriff in [Azure](https://portal.azure.com/#home) anzeigen möchten, wechseln Sie zu **Azure Active Directory** > **Bedingter Zugriff** > **Klassische Richtlinien**.

## <a name="to-enable-the-mtd-connector"></a>So aktivieren Sie den MTD-Connector

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Klicken Sie auf **Mandantenverwaltung** > **Connectors und Token** > **Mobile Threat Defense**.

3. Klicken Sie im Bereich **Mobile Threat Defense** auf die Option **Hinzufügen**.

4. Wählen Sie Ihre MTD-Lösung in der Dropdownliste unter **Einzurichtenden MTD-Connector (Mobile Threat Defense) auswählen** aus.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Aktivieren Sie die Umschaltoptionen entsprechend den Anforderungen Ihrer Organisation. Die angezeigten Umschaltoptionen variieren je nach MTD-Partner.

## <a name="mobile-threat-defense-toggle-options"></a>Umschaltoptionen von Mobile Threat Defense

Sie können entscheiden, welche MTD-Umschaltoptionen Sie entsprechend den Anforderungen Ihrer Organisation aktivieren müssen. Nachfolgend finden Sie weitere Details:

**Einstellungen für die App-Schutzrichtlinie**

- **Verbinden von Android-Geräten der Version 4.4 und höher mit *\<MTD-Partnername>* zur Auswertung von App-Schutzrichtlinien**: Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.

- **Verbinden von iOS-Geräten der Version 11 und höher mit *\<MTD-Partnername>* zur Auswertung von App-Schutzrichtlinien**: Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.

**Allgemeine Einstellungen**

- **Anzahl von Tagen, bis Partner als nicht reaktionsfähig gilt:** Anzahl von Tagen mit Inaktivität, bevor Intune den Partner als nicht reaktionsfähig betrachtet, da die Verbindung unterbrochen wurde. Intune ignoriert den Kompatibilitätszustand für nicht reaktionsfähige MTD-Partner.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt, der über die **Letzte Synchronisierung** zwischen Intune und dem MTD-Partner informiert, werden im Bereich „Mobile Threat Defense“ angezeigt.

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen einer Mobile Threat Defense-App-Schutzrichtlinie (MTD) mit Intune](~/protect/mtd-app-protection-policy.md).
