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
ms.openlocfilehash: 63079757ee3610d825601921da1d33aa94f851b6
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794406"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Aktivieren des Mobile Threat Defense-Connector in Intune für nicht registrierte Geräte

Während des Mobile Threat Defense-Setups (MTD) haben Sie eine Richtlinie zum Klassifizieren von Bedrohungen in Ihrer Mobile Threat Defense-Partnerkonsole konfiguriert und die App-Schutzrichtlinie in Intune erstellt. Wenn Sie den Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert haben, können Sie nun die MTD-Verbindung für MTD-Partneranwendungen aktivieren.

> [!NOTE] 
> Dieser Artikel gilt für alle Mobile Threat Defense-Partner, die App-Schutzrichtlinien unterstützen: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

## <a name="to-enable-the-mtd-connector"></a>So aktivieren Sie den MTD-Connector

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

2. Wählen Sie im **Intune-Dashboard** zuerst **Gerätekompatibilität** und dann im Abschnitt **Setup** die Option **Mobile Threat Defense** aus.

3. Klicken Sie im Bereich **Mobile Threat Defense** auf die Option **Hinzufügen**.

4. Wählen Sie Ihre MTD-Lösung in der Dropdownliste unter **Einzurichtenden MTD-Connector (Mobile Threat Defense) auswählen** aus.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Aktivieren Sie die Umschaltoptionen entsprechend den Anforderungen Ihrer Organisation. Die angezeigten Umschaltoptionen variieren je nach MTD-Partner.

## <a name="mtd-toggle-options"></a>MTD-Umschaltoptionen

Sie können entscheiden, welche MTD-Optionen Sie aktivieren müssen, um die Anforderungen Ihrer Organisation zu erfüllen. Nachfolgend finden Sie weitere Details:

**Einstellungen für die App-Schutzrichtlinie**
- **Verbinden von Android-Geräten der Version 4.1 und höher mit *\<MTD-Partnernamen>* zur Auswertung von App-Schutzrichtlinien**: Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.
- **Verbinden von iOS-Geräten der Version 8.0 und höher mit *\<MTD-Partnernamen>* zur Auswertung von App-Schutzrichtlinien**: Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.

**Allgemeine Einstellungen**
- **Anzahl von Tagen, bis Partner als nicht reaktionsfähig gilt:** Anzahl von Tagen mit Inaktivität, bevor Intune den Partner als nicht reaktionsfähig betrachtet, da die Verbindung unterbrochen wurde. Intune ignoriert den Kompatibilitätszustand für nicht reaktionsfähige MTD-Partner.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt, der über die **Letzte Synchronisierung** zwischen Intune und dem MTD-Partner informiert, werden im Bereich „Mobile Threat Defense“ angezeigt.

> [!NOTE] 
> Wenn Sie Mobile Threat Defense mit Intune verbinden, erstellt Intune eine klassische Richtlinie für bedingten Zugriff in Azure Active Directory. Jede MTD-App, die Sie integrieren (einschließlich [Defender ATP](advanced-threat-protection.md) oder jedes unserer zusätzlichen [MTD-Partner](mobile-threat-defense.md#mobile-threat-defense-partners)), erstellt eine neue klassische Richtlinie für bedingten Zugriff. **Diese Richtlinien können ignoriert werden, dürfen jedoch nicht bearbeitet, gelöscht oder deaktiviert werden.**
> 
> Klassische bedingte Zugriffsrichtlinien für MTD-Apps: 
> - Sie werden von Intune MTD verwendet und verlangen, dass Geräte in Azure AD registriert werden, damit sie eine Geräte-ID erhalten, bevor Kommunikation mit MTD-Partnern erfolgt. Die ID ist erforderlich, damit Geräte ihren Status erfolgreich an Intune melden können.  
> - Sie haben keine Auswirkung auf andere Cloud-Apps oder Ressourcen.  
> - Die Zugriffsrichtlinien unterscheiden sich von Richtlinien für bedingten Zugriff, die Sie erstellen können, damit sie Ihnen bei der Verwaltung von MTD helfen oder eine Zertifizierungsstelle für den Schutz von Apps erfordern.
> - Standardmäßig interagieren sie nicht mit anderen Richtlinien für den bedingten Zugriff, die Sie für die Auswertung verwenden.  
>
> Wenn Sie klassische Richtlinien für den bedingten Zugriff in [Azure](https://portal.azure.com/#home) anzeigen möchten, wechseln Sie zu **Azure Active Directory** > **Bedingter Zugriff** > **Klassische Richtlinien**.

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen einer Mobile Threat Defense-App-Schutzrichtlinie (MTD) mit Intune](~/protect/mtd-app-protection-policy.md).