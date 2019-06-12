---
title: Aktivieren Sie den Mobile Threat Defense-Connector in Microsoft Intune.
titleSuffix: Microsoft Intune
description: Aktivieren Sie den Connector zwischen Ihrem Mobile Threat Defense-Partner (MTD) und Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1929b811a5a5320bc0ceefcef4f05ed2443ac070
ms.sourcegitcommit: cc5d757018d05fc03ac9ea3d30f563df9bfd61ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66819646"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivieren Sie den Mobile Threat Defense-Connector in Intune.

> [!NOTE] 
> Dieses Thema gilt für alle Mobile Threat Defense-Partner.

Während des Mobile Threat Defense-Setups (MTD) haben Sie eine Richtlinie zum Klassifizieren von Bedrohungen in Ihrer MTD-Partnerkonsole konfiguriert und die Gerätekonformitätsrichtlinie in Intune erstellt. Wenn Sie den Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert haben, können Sie nun die MTD-Verbindung in Intune aktivieren.

## <a name="to-enable-the-mtd-connector"></a>So aktivieren Sie den MTD-Connector

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

4. Wählen Sie im **Intune-Dashboard** zuerst **Gerätekompatibilität** und dann im Abschnitt **Setup** die Option **Mobile Threat Defense** aus.

5. Klicken Sie im Bereich **Mobile Threat Defense** auf die Option **Hinzufügen**.

6. Wählen Sie Ihre MTD-Lösung in der Dropdownliste unter **Einzurichtenden MTD-Connector (Mobile Threat Defense) auswählen** aus.

    ![MTD-Einrichtung im Intune Azure-Portal](./media/enable-mtd-connector-1.png)

7. Aktivieren Sie die Umschaltoptionen entsprechend den Anforderungen Ihrer Organisation. Die angezeigten Umschaltoptionen variieren je nach MTD-Partner.

## <a name="mtd-toggle-options"></a>MTD-Umschaltoptionen

Sie können entscheiden, welche MTD-Optionen Sie aktivieren müssen, um die Anforderungen Ihrer Organisation zu erfüllen. Nachfolgend finden Sie weitere Details:

- **Herstellen einer Verbindung zwischen Android-Geräten ab Version 4.1 mit [MTD-Partnername] for Work MTD:** Wenn Sie diese Option aktivieren, können Geräte unter Android 4.1 und höher Sicherheitsrisiken an Intune melden.
    - **Als nicht konform markieren, wenn keine Daten empfangen werden:** Wenn Intune keine Daten über ein Gerät auf dieser Plattform vom MTD-Partner empfängt, wird das Gerät als nicht konform betrachtet.
<br></br>
- **Herstellen einer Verbindung zwischen iOS-Geräten ab Version 8.0 mit [MTD-Partnername] for Work MTD:** Wenn Sie diese Option aktivieren, können Geräte unter iOS 8.0 und höher Sicherheitsrisiken an Intune melden.
    - **Als nicht konform markieren, wenn keine Daten empfangen werden:** Wenn Intune keine Daten über ein Gerät auf dieser Plattform vom MTD-Partner empfängt, wird das Gerät als nicht konform betrachtet.
<br></br>
- **Aktivieren der App-Synchronisierung für iOS-Geräte:** Ermöglicht diesem Mobile Threat Defense-Partner, Metadaten zur Bedrohungsanalyse von iOS-Anwendungen aus Intune anzufordern.

- **Nicht unterstützte Betriebssystemversionen blockieren:** Blockieren, wenn auf dem Gerät eine frühere Betriebssystem ausgeführt wird, als die minimal unterstützte Version.

- **Anzahl von Tagen, bis Partner als nicht reaktionsfähig gilt:** Anzahl von Tagen mit Inaktivität, bevor Intune den Partner als nicht reaktionsfähig betrachtet, da die Verbindung unterbrochen wurde. Intune ignoriert den Kompatibilitätszustand für nicht reaktionsfähige MTD-Partner.

> [!IMPORTANT] 
> Wenn möglich, empfehlen wir, dass Sie die MTD-Apps hinzufügen und zuweisen, bevor Sie die Richtlinienregeln für Gerätekonformität und bedingten Zugriff erstellen. Dies hilft sicherzustellen, dass die MTD-App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt, der über die **Letzte Synchronisierung** zwischen Intune und dem MTD-Partner informiert, werden im Bereich „Mobile Threat Defense“ angezeigt.
