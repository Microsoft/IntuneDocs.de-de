---
title: Aktivieren Sie den Mobile Threat Defense-Connector in Microsoft Intune.
titleSuffix: ''
description: Aktivieren Sie den Connector zwischen Ihrem Mobile Threat Defense-Partner (MTD) und Microsoft Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6fccfcbceecc9aa0667aa9fd6656c2fcc524d363
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34569356"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivieren Sie den Mobile Threat Defense-Connector in Intune.

> [!NOTE] 
> Dieses Thema gilt für alle Mobile Threat Defense-Partner.

Während des Mobile Threat Defense-Setups (MTD) haben Sie eine Richtlinie zum Klassifizieren von Bedrohungen in Ihrer MTD-Partnerkonsole konfiguriert und die Gerätekonformitätsrichtlinie in Intune erstellt. Wenn Sie den Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert haben, können Sie nun die MTD-Verbindung in Intune aktivieren.

## <a name="to-enable-the-mtd-connector"></a>So aktivieren Sie den MTD-Connector

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) mit Ihren Intune-Anmeldeinformationen an. Sobald Sie erfolgreich angemeldet sind, wird das **Azure-Dashboard** angezeigt.

2. Klicken Sie im **Azure-Dashboard** im linken Menü auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Klicken Sie auf **Intune**. Das **Intune-Dashboard** wird geöffnet.

4. Wählen Sie im **Intune-Dashboard** zuerst **Gerätekompatibilität** und dann im Abschnitt **Setup** die Option **Mobile Threat Defense** aus.

5. Klicken Sie im Bereich **Mobile Threat Defense** auf die Option **Hinzufügen**.

6. Wählen Sie Ihre MTD-Lösung in der Dropdownliste unter **Einzurichtenden MTD-Connector (Mobile Threat Defense) auswählen** aus.

    ![MTD-Einrichtung im Intune Azure-Portal](./media/enable-mtd-connector-1.png)

7. Aktivieren Sie die Umschaltoptionen entsprechend den Anforderungen Ihrer Organisation.

## <a name="mtd-toggle-options"></a>MTD-Umschaltoptionen

Sie können entscheiden, welche MTD-Umschaltoptionen Sie entsprechend den Anforderungen Ihrer Organisation aktivieren müssen. Nachfolgend finden Sie weitere Details:

- **Herstellen einer Verbindung zwischen Geräten unter Android 4.1 und höher und MTD von [MTD-Partnername] for Work**: Wenn Sie diese Option aktivieren, können Geräte unter Android 4.1 und höher Sicherheitsrisiken an Intune melden.
    - **Als nicht kompatibel markieren, wenn keine Daten erhalten werden**: Wenn Intune keine Daten über ein Gerät auf dieser Plattform vom MTD-Partner empfängt, betrachten Sie das Gerät als nicht kompatibel.
<br></br>
- **Herstellen einer Verbindung zwischen Geräten unter iOS 8.0 und höher und MTD von [MTD-Partnername] for Work:** Wenn Sie diese Option aktivieren, können Geräte unter iOS 8.0 und höher Sicherheitsrisiken an Intune melden.
    - **Als nicht kompatibel markieren, wenn keine Daten erhalten werden**: Wenn Intune keine Daten über ein Gerät auf dieser Plattform vom MTD-Partner empfängt, betrachten Sie das Gerät als nicht kompatibel.
<br></br>
- **App-Synchronisierung für iOS-Geräte aktivieren**: Ermöglicht diesem Mobile Threat Defense-Partner, Metadaten von iOS-Anwendungen aus Intune zur Bedrohungsanalyse anzufordern.

- **Nicht unterstützte Betriebssystemversionen blockieren**: Blockieren, wenn auf dem Gerät eine frühere Betriebssystem ausgeführt wird, als die minimal unterstützte Version.

- **Anzahl von Tagen, bis Partner als nicht reaktionsfähig gilt**: Anzahl von Tagen mit Inaktivität, bevor Intune den Partner als nicht reaktionsfähig betrachtet, da die Verbindung unterbrochen wurde. Intune ignoriert den Kompatibilitätszustand für nicht reaktionsfähige MTD-Partner.

> [!IMPORTANT] 
> Sie müssen die MTD-Apps hinzufügen und zuweisen, bevor Sie die Richtlinienregeln für Kompatibilität und bedingten Zugriff erstellen. Dadurch wird sichergestellt, dass die MTD-App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt, der über die **Letzte Synchronisierung** zwischen Intune und dem MTD-Partner informiert, werden im Bereich „Mobile Threat Defense“ angezeigt.
