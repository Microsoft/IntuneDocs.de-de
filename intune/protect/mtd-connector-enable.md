---
title: Aktivieren Sie den Mobile Threat Defense-Connector in Microsoft Intune.
titleSuffix: Microsoft Intune
description: Aktivieren Sie den Connector zwischen Ihrem Mobile Threat Defense-Partner (MTD) und Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
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
ms.openlocfilehash: b8243ae4014660a76c6327afd9c970ce8a9eae58
ms.sourcegitcommit: 960ffb2214c35d75ad219fa2571a999529a0abd4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74478833"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivieren Sie den Mobile Threat Defense-Connector in Intune.

Während des Mobile Threat Defense-Setups (MTD) haben Sie eine Richtlinie zum Klassifizieren von Bedrohungen in Ihrer Mobile Threat Defense-Partnerkonsole konfiguriert und die App-Konformitätsrichtlinie in Intune erstellt. Wenn Sie den Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert haben, können Sie nun die MTD-Verbindung für MTD-Partneranwendungen aktivieren.

> [!NOTE]
> Dieses Thema gilt für alle Mobile Threat Defense-Partner.

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Klassische Richtlinien für bedingten Zugriff für MTD-Apps

Wenn Sie eine neue Anwendung in Intune Mobile Threat Defense integrieren und die Verbindung mit Intune aktivieren, erstellt Intune eine klassische Richtlinie für den bedingten Zugriff in Azure Active Directory. Jede MTD-App, die Sie integrieren (einschließlich [Defender ATP](advanced-threat-protection.md) oder jedes unserer zusätzlichen [MTD-Partner](mobile-threat-defense.md#mobile-threat-defense-partners)), erstellt eine neue klassische Richtlinie für bedingten Zugriff. Diese Richtlinien können ignoriert werden, dürfen jedoch nicht bearbeitet, gelöscht oder deaktiviert werden.

Wenn die klassische Richtlinie gelöscht wird, müssen Sie die zur Erstellung dieser Richtlinie verantwortliche Verbindung mit Intune löschen und anschließend erneut einrichten. Durch diesen Prozess wird die klassische Richtlinie neu erstellt. Es wird keine Unterstützung für die Migration klassischer Richtlinien für MTD-Apps zum neuen Richtlinientyp für bedingten Zugriff bereitgestellt.

Klassische bedingte Zugriffsrichtlinien für MTD-Apps:

- Sie werden von Intune MTD verwendet und verlangen, dass Geräte in Azure AD registriert werden, damit sie eine Geräte-ID erhalten, bevor Kommunikation mit MTD-Partnern erfolgt. Die ID ist erforderlich, damit Geräte ihren Status erfolgreich an Intune melden können.

- Sie haben keine Auswirkung auf andere Cloud-Apps oder Ressourcen.

- Die Zugriffsrichtlinien unterscheiden sich von Richtlinien für bedingten Zugriff, die Sie möglicherweise erstellen, damit sie Ihnen bei der Verwaltung von MTD helfen.

- Standardmäßig interagieren sie nicht mit anderen Richtlinien für den bedingten Zugriff, die Sie für die Auswertung verwenden.

Wenn Sie klassische Richtlinien für den bedingten Zugriff in [Azure](https://portal.azure.com/#home) anzeigen möchten, wechseln Sie zu **Azure Active Directory** > **Bedingter Zugriff** > **Klassische Richtlinien**.

## <a name="to-enable-the-mobile-threat-defense-connector"></a>So aktivieren Sie den Mobile Threat Defense-Connector

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Klicken Sie auf **Tenant administration** > **Connectors and tokens** > **Mobile Threat Defense** (Mandantenverwaltung > Connectors und Token).

3. Klicken Sie im Bereich **Mobile Threat Defense** auf die Option **Hinzufügen**.

4. Wählen Sie für **Mobile Threat Defense connector to setup** (Einzurichtender Mobile Threat Defense-Connector) Ihre MTD-Lösung aus der Dropdownliste aus.

5. Aktivieren Sie die Umschaltoptionen entsprechend den Anforderungen Ihrer Organisation. Die angezeigten Umschaltoptionen variieren je nach MTD-Partner.  Die folgende Abbildung zeigt beispielsweise die für Symantec Endpoint Protection verfügbaren Optionen:

   ![MTD-Einrichtung im Intune Azure-Portal](./media/mtd-connector-enable/enable-mtd-connector-1.png)

## <a name="mobile-threat-defense-toggle-options"></a>Umschaltoptionen von Mobile Threat Defense

Sie können entscheiden, welche MTD-Umschaltoptionen Sie entsprechend den Anforderungen Ihrer Organisation aktivieren müssen. Nicht alle der folgenden Optionen werden von allen Mobile Thread Defense-Partnern unterstützt:

**Einstellungen für die MDM-Konformitätsrichtlinie**

- **Connect Android devices of version _\<supported versions>_ to _\<MTD partner name>_** (Verbinden von Android-Geräten der Version <unterstützte Versionen> mit <Name von MTD-Partner>): Wenn Sie diese Option aktivieren, können Geräte unter Android 4.1 und höher Sicherheitsrisiken an Intune melden.

- **Connect iOS devices of version _\<supported versions>_ to _\<MTD partner name>_** (Verbinden von iOS-Geräten der Version <unterstützte Versionen> mit <Name von MTD-Partner>): Wenn Sie diese Option aktivieren, können Geräte unter iOS 8.0 und höher Sicherheitsrisiken an Intune melden.

- **Aktivieren der App-Synchronisierung für iOS-Geräte:** Ermöglicht diesem Mobile Threat Defense-Partner, Metadaten zur Bedrohungsanalyse von iOS-Anwendungen aus Intune anzufordern.

- **Nicht unterstützte Betriebssystemversionen blockieren:** Blockieren, wenn auf dem Gerät eine frühere Betriebssystem ausgeführt wird, als die minimal unterstützte Version.

**Einstellungen für die App-Schutzrichtlinie**

- **Connect Android devices of version *\<supported versions>* to *\<MTD partner name>* for app protection policy evaluation** (Verbinden von Android-Geräten der Version <unterstützte Versionen> mit <Name von MTD-Partner> zur Auswertung von App-Schutzrichtlinien): Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.

- **Connect iOS devices of version *\<supported versions>* to *\<MTD partner name>* for app protection policy evaluation** (Verbinden von iOS-Geräten der Version <unterstützte Versionen> mit <Name von MTD-Partner> zur Auswertung von App-Schutzrichtlinien): Wenn Sie diese Option aktivieren, werten App-Schutzrichtlinien mit der Regel „Gerätebedrohungsstufe“ Geräte aus, die Daten von diesem Connector enthalten.

Weitere Informationen zur Verwendung von Mobile Threat Defense-Connectors für die Auswertung von Intune-App-Schutzrichtlinien finden Sie unter [Aktivieren des Mobile Threat Defense-Connector in Intune für nicht registrierte Geräte](~/protect/mtd-enable-unenrolled-devices.md).

**Allgemeine Einstellungen**

- **Anzahl von Tagen, bis Partner als nicht reaktionsfähig gilt:** Anzahl von Tagen mit Inaktivität, bevor Intune den Partner als nicht reaktionsfähig betrachtet, da die Verbindung unterbrochen wurde. Intune ignoriert den Kompatibilitätszustand für nicht reaktionsfähige MTD-Partner.

> [!IMPORTANT]
> Es wird empfohlen, die MTD-Apps nach Möglichkeit hinzuzufügen und zuzuweisen, bevor Sie die Richtlinien für die Gerätekonformität und den bedingten Zugriff erstellen. Dies hilft sicherzustellen, dass die MTD-App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt, der über die **Letzte Synchronisierung** zwischen Intune und dem MTD-Partner informiert, werden im Bereich „Mobile Threat Defense“ angezeigt.

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen einer Mobile Threat Defense-App-Schutzrichtlinie (MTD) mit Intune](~/protect/mtd-app-protection-policy.md).
