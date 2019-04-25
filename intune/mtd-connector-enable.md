---
title: Aktivieren Sie den Mobile Threat Defense-Connector in Microsoft Intune.
titleSuffix: Microsoft Intune
description: Aktivieren Sie den Connector zwischen Ihrem Mobile Threat Defense-Partner (MTD) und Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ab9fef5a577783ebbdd512de6d00ab98483e754c
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513352"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivieren Sie den Mobile Threat Defense-Connector in Intune.

> [!NOTE] 
> Dieses Thema gilt für alle Mobile Threat Defense-Partner.

Während des Mobile Threat Defense-Setups (MTD) haben Sie eine Richtlinie zum Klassifizieren von Bedrohungen in Ihrer MTD-Partnerkonsole konfiguriert und die Gerätekonformitätsrichtlinie in Intune erstellt. Wenn Sie den Intune-Connector in der MTD-Partnerkonsole bereits konfiguriert haben, können Sie nun die MTD-Verbindung in Intune aktivieren.

## <a name="to-enable-the-mtd-connector"></a>So aktivieren Sie den MTD-Connector

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com) mit Ihren Intune-Anmeldeinformationen an. Nachdem Sie sich erfolgreich angemeldet haben, wird das **Azure-Dashboard** angezeigt.

2. Klicken Sie auf dem **Azure-Dashboard** im linken Menü auf **Alle Dienste**, und geben Sie dann **Intune** in das Filtertextfeld ein.

3. Wählen Sie **Intune** aus. Daraufhin wird das **Intune-Dashboard** geöffnet.

4. Klicken Sie auf dem **Intune-Dashboard** auf **Gerätekonformität**, und wählen Sie dann **Mobile Threat Defense** im Abschnitt **Setup** aus.

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
> Sie müssen die MTD-Apps hinzufügen und zuweisen, bevor Sie die Richtlinienregeln für Kompatibilität und bedingten Zugriff erstellen. Dadurch wird sichergestellt, dass die MTD-App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

> [!TIP]
> Der **Verbindungsstatus** und der Zeitpunkt, der über die **Letzte Synchronisierung** zwischen Intune und dem MTD-Partner informiert, werden im Bereich „Mobile Threat Defense“ angezeigt.
