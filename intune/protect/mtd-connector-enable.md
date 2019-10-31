---
title: Aktivieren Sie den Mobile Threat Defense-Connector in Microsoft Intune.
titleSuffix: Microsoft Intune
description: Aktivieren Sie den Connector zwischen Ihrem Mobile Threat Defense-Partner (MTD) und Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4f917167baecc643e045610e86e582957e535978
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810291"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivieren Sie den Mobile Threat Defense-Connector in Intune.

> [!NOTE] 
> Dieses Thema gilt für alle Mobile Threat Defense-Partner.

Während des Mobile Threat Defense-Setups (MTD) haben Sie eine Richtlinie zum Klassifizieren von Bedrohungen in Ihrer MTD-Partnerkonsole konfiguriert und die Gerätekonformitätsrichtlinie in Intune erstellt. Wenn Sie den Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert haben, können Sie nun die MTD-Verbindung für MTD-Partneranwendungen aktivieren.

Wenn Sie eine neue Anwendung in Intune Mobile Threat Defense integrieren und die Verbindung mit Intune aktivieren, erstellt Intune eine klassische Richtlinie für den bedingten Zugriff in Azure Active Directory. Jede MTD-App, die Sie integrieren (einschließlich [Defender ATP](advanced-threat-protection.md) oder jedes unserer zusätzlichen [MTD-Partner](mobile-threat-defense.md#mobile-threat-defense-partners)), erstellt eine neue klassische Richtlinie für bedingten Zugriff. Diese Richtlinien können ignoriert werden, dürfen jedoch nicht bearbeitet, gelöscht oder deaktiviert werden.

Klassische bedingte Zugriffsrichtlinien für MTD-Apps: 

- Sie werden von Intune MTD verwendet und verlangen, dass Geräte in Azure AD registriert werden, damit sie eine Geräte-ID erhalten, bevor Kommunikation mit MTD-Partnern erfolgt. Die ID ist erforderlich, damit Geräte ihren Status erfolgreich an Intune melden können.  
- Sie haben keine Auswirkung auf andere Cloud-Apps oder Ressourcen.  
- Die Zugriffsrichtlinien unterscheiden sich von Richtlinien für bedingten Zugriff, die Sie möglicherweise erstellen, damit sie Ihnen bei der Verwaltung von MTD helfen.
- Standardmäßig interagieren sie nicht mit anderen Richtlinien für den bedingten Zugriff, die Sie für die Auswertung verwenden.  

Wenn Sie klassische Richtlinien für den bedingten Zugriff in [Azure](https://portal.azure.com/#home) anzeigen möchten, wechseln Sie zu **Azure Active Directory** > **Bedingter Zugriff** > **Klassische Richtlinien**.


## <a name="to-enable-the-mobile-threat-defense-connector"></a>So aktivieren Sie den Mobile Threat Defense-Connector

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

4. Wählen Sie im **Intune-Dashboard** zuerst **Gerätekompatibilität** und dann im Abschnitt **Setup** die Option **Mobile Threat Defense** aus.

5. Klicken Sie im Bereich **Mobile Threat Defense** auf die Option **Hinzufügen**.

6. Wählen Sie Ihre MTD-Lösung in der Dropdownliste unter **Einzurichtenden MTD-Connector (Mobile Threat Defense) auswählen** aus.

    ![MTD-Einrichtung im Intune Azure-Portal](./media/mtd-connector-enable/enable-mtd-connector-1.png)

7. Aktivieren Sie die Umschaltoptionen entsprechend den Anforderungen Ihrer Organisation. Die angezeigten Umschaltoptionen variieren je nach MTD-Partner.

## <a name="mobile-threat-defense-toggle-options"></a>Umschaltoptionen von Mobile Threat Defense

Sie können entsprechend den Anforderungen Ihrer Organisation entscheiden, welche Umschaltoptionen von Mobile Threat Defense Sie aktivieren müssen. Nachfolgend finden Sie weitere Details:

**Einstellungen für die MDM-Konformitätsrichtlinie**
- **Verbinden von Android-Geräten der Version  4.1 und höher mit *\<MTD-Partnername>***: Wenn Sie diese Option aktivieren, können Geräte unter Android 4.1 und höher Sicherheitsrisiken an Intune melden.
- **Verbinden von iOS-Geräten der Version 8.0 und höher mit *\<MTD-Partnername>***: Wenn Sie diese Option aktivieren, können Geräte unter iOS 8.0 und höher Sicherheitsrisiken an Intune melden.
- **Aktivieren der App-Synchronisierung für iOS-Geräte:** Ermöglicht diesem Mobile Threat Defense-Partner, Metadaten zur Bedrohungsanalyse von iOS-Anwendungen aus Intune anzufordern.
- **Nicht unterstützte Betriebssystemversionen blockieren:** Blockieren, wenn auf dem Gerät eine frühere Betriebssystem ausgeführt wird, als die minimal unterstützte Version.

**Einstellungen für die App-Schutzrichtlinie**
- **Verbinden von Android-Geräten der Version 4.1 und höher mit *\<MTD-Partnername>* zur Auswertung von App-Schutzrichtlinien**: Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.
- **Verbinden von iOS-Geräten der Version 8.0 und höher mit *\<MTD-Partnername>* zur Auswertung von App-Schutzrichtlinien**: Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.

Weitere Informationen zur Verwendung von Mobile Threat Defense-Connectors für die Auswertung von Intune-App-Schutzrichtlinien finden Sie unter [Aktivieren des Mobile Threat Defense-Connector in Intune für nicht registrierte Geräte](~/protect/mtd-enable-unenrolled-devices.md).

**Allgemeine Einstellungen**
- **Anzahl von Tagen, bis Partner als nicht reaktionsfähig gilt:** Anzahl von Tagen mit Inaktivität, bevor Intune den Partner als nicht reaktionsfähig betrachtet, da die Verbindung unterbrochen wurde. Intune ignoriert den Kompatibilitätszustand für nicht reaktionsfähige MTD-Partner.

> [!IMPORTANT] 
> Es wird empfohlen, die MTD-Apps nach Möglichkeit hinzuzufügen und zuzuweisen, bevor Sie die Richtlinien für die Gerätekonformität und den bedingten Zugriff erstellen. Dies hilft sicherzustellen, dass die MTD-App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt, der über die **Letzte Synchronisierung** zwischen Intune und dem MTD-Partner informiert, werden im Bereich „Mobile Threat Defense“ angezeigt.
