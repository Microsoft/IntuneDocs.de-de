---
title: Aktivieren des Mobile Threat Defense-Connectors mit Intune
titlesuffix: Azure portal
description: Aktivieren Sie den Mobile Threat Defense-Connector in Intune.
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 99b73cb0885c4d93cf91ea219ca98a8a81d67b39
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="enable-mobile-threat-defense-in-intune"></a>Aktivieren von Mobile Threat Defense in Intune

> [!NOTE] 
> Dieses Thema gilt für alle Mobile Threat Defense-Partner.

Um die Verbindung mit Mobile Threat Defense (MTD) in Intune zu aktivieren, muss der Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert sein.

## <a name="to-enable-the-mtd-connector"></a>So aktivieren Sie den MTD-Connector

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) mit Ihren Intune-Anmeldeinformationen an. Sobald Sie erfolgreich angemeldet sind, wird das **Azure-Dashboard** angezeigt.

2. Wählen Sie im **Azure-Dashboard** im linken Menü **Weitere Dienste** aus, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune** aus. Das **Intune-Dashboard** wird geöffnet.

4. Wählen Sie im **Intune-Dashboard** zuerst **Gerätekompatibilität** und dann im Abschnitt **Setup** die Option **Mobile Threat Defense** aus.

5. Wählen Sie auf dem Blatt **Mobile Threat Defense** die Option **Hinzufügen** aus.

6. Wählen Sie Ihre MTD-Lösung in der Dropdownliste unter **Einzurichtenden MTD-Connector (Mobile Threat Defense) auswählen** aus.

    ![MTD-Einrichtung im Intune Azure-Portal](./media/enable-mtd-connector-1.png)

7. Aktivieren Sie die Umschaltoptionen entsprechend den Anforderungen Ihrer Organisation.

## <a name="mtd-toggle-options"></a>MTD-Umschaltoptionen

Sie können entscheiden, welche MTD-Umschaltoptionen Sie entsprechend den Anforderungen Ihrer Organisation aktivieren müssen. Ausführlichere Informationen:

- **Herstellen einer Verbindung zwischen Geräten unter Android 4.1 und höher und MTD von [MTD-Partnername] for Work**: Wenn Sie diese Option aktivieren, können Geräte unter Android 4.1 und höher Sicherheitsrisiken an Intune melden.
    - **Als nicht kompatibel markieren, wenn keine Daten erhalten werden**: Wenn Intune keine Daten über ein Gerät auf dieser Plattform vom MTD-Partner empfängt, betrachten Sie das Gerät als nicht kompatibel.
<br></br>
- **Herstellen einer Verbindung zwischen Geräten unter iOS 8.0 und höher und MTD von [MTD-Partnername] for Work**: Wenn Sie diese Option aktivieren, können Geräte unter Android 4.1 und höher Sicherheitsrisiken an Intune melden.
    - **Als nicht kompatibel markieren, wenn keine Daten erhalten werden**: Wenn Intune keine Daten über ein Gerät auf dieser Plattform vom MTD-Partner empfängt, betrachten Sie das Gerät als nicht kompatibel.
<br></br>
- **Nicht unterstützte Betriebssystemversionen blockieren**: Blockieren, wenn auf dem Gerät eine frühere Betriebssystem ausgeführt wird, als die minimal unterstützte Version.

- **Anzahl von Tagen, bis Partner als nicht reaktionsfähig gilt**: Anzahl von Tagen mit Inaktivität, bevor Intune den Partner als nicht reaktionsfähig betrachtet, da die Verbindung unterbrochen wurde. Intune ignoriert den Kompatibilitätszustand für nicht reaktionsfähige MTD-Partner.

> [!IMPORTANT] 
> Sie müssen die MTD-Apps hinzufügen und zuweisen, bevor Sie die Richtlinienregeln für Kompatibilität und bedingten Zugriff erstellen. Dadurch wird sichergestellt, dass die MTD-App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt **der letzten Synchronisierung** zwischen Intune und dem MTD-Partner werden auf dem Blatt „Mobile Threat Defense“ angezeigt.
