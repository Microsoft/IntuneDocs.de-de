---
title: Verstehen Sie Ihre Geräte mithilfe des Inventars
description: Verwenden Sie Intune zum Anzeigen von Informationen zur Hardware der Geräte, die Sie verwalten.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/05/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e50a7329512e6b57eb5486792669b7cd102eebdb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>Verstehen Sie Ihre Geräte mithilfe des Inventars in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Mit Microsoft Intune können Sie das Inventar an registrierten Geräten und Windows-PCs anzeigen, auf denen die Intune-Clientsoftware ausgeführt wird.
Intune sammelt normalerweise alle 7 Tage den Bestand von verwalteten Geräten. Aus diesem Grund entsteht möglicherweise eine Verzögerung, bevor Berichte die Ergebnisse von kürzlich durchgeführten Änderungen an Geräten anzeigen, z.B. eine Änderung am Gerätenamen oder am freien Speicherplatz.

## <a name="whats-collected-from-enrolled-devices"></a>Welche Daten registrierter Geräte werden gesammelt?
Um das von den mobilen Geräten gesammelte Inventar anzuzeigen, führen Sie die [Inventurberichte für mobile Geräte](understand-microsoft-intune-operations-by-using-reports.md) aus. Intune sammelt das folgende Inventar von den mobilen Geräten:

|Eigenschaft|Gesammelt von|
|------------|-----------------------|
|**Name**|Alle Geräte|
|**Betriebssystem**|Alle Geräte|
|**Hersteller**|Alle Geräte|
|**Modell**|Alle Geräte|
|**Verwaltungskanal**|Alle Geräte|
|**Bei AAD registriert**|Alle Geräte mit Ausnahme von Mac OS X|
|**Kompatibel**|Alle Geräte|
|**EAS-aktiviert**|Alle Geräte mit Ausnahme von Mac OS X|
|**EAS-Aktivierungs-ID**|Alle Geräte mit Ausnahme von Mac OS X|
|**EAS-Aktivierungszeitpunkt**|Alle Geräte mit Ausnahme von Mac OS X|
|**Verwaltungsstatus**|Alle Geräte|
|**E-Mail-Adresse**|Alle Geräte|
|**Exchange ActiveSync-ID**|Alle Geräte|
|**Jailbreak oder Rooting**|Nur iOS- und Android-Geräte|
|**Eindeutige Geräte-ID**|Alle Geräte mit Ausnahme von Exchange ActiveSync|
|**Seriennummer**|iOS-, Mac OS X-, Android-, Windows 8.1- und Windows 10-Desktopgeräte|
|**Gesamtmenge des Speicherplatzes**|iOS-, Mac OS X-, Android-, Windows 8.1- und Windows 10-Desktopgeräte und -mobile Geräte|
|**Freier Speicherplatz**|iOS-, Mac OS X-, Windows 8.1- und Windows 10-Desktopgeräte|
|**Telefonnummer**<br>Telefone, die als geschäftlich eingestuft sind, werden jetzt mit der vollständigen Telefonnummer identifiziert, wenn Sie beispielsweise einen Inventurbericht für mobile Geräte ausführen. BYOD-Telefonnummern werden mit &#42; maskiert, und nur die letzten vier Ziffern werden angezeigt.|iOS-, Android- und Windows Phone-Geräte|
|**IMEI**|Exchange ActiveSync-, iOS-, Android- und Windows Phone-Geräte|
|**MEID**<br>Mobile Equipment Identifier|Nur iOS-Geräte|
|**WiFi-MAC**|Alle Geräte mit Ausnahme von Exchange ActiveSync|
|**Netzbetreiber des Abonnenten**|Nur iOS- und Android-Geräte|
|**Mobilfunktechnologie**|Nur iOS- und Android-Geräte|
|**Überwacht**|Nur iOS-Geräte|
|**Aktivierungssperrenstatus**|Nur iOS-Geräte|
|**Registrierungsdatum**|Alle Geräte|
|**Zuletzt aktualisiert**|Alle Geräte|
|**Ethernet MAC**|Nur Mac OS X-Geräte|
|**Aktivierungssperre aktiviert**|Nur iOS-Geräte|
|**Verschlüsselung aktiviert**|Alle Geräte|

>[!NOTE]
>Je nachdem, welchen Netzbetreiber Sie mit dem Gerät verwenden, werden einige der oben aufgeführten Elemente vielleicht nicht erfasst.

## <a name="whats-collected-from-windows-pcs"></a>Was wird von Windows-PCs gesammelt?
> [!IMPORTANT]
> Dieser Abschnitt gilt nur für Windows-PCs, auf denen die Intune-Windows-PC-Clientsoftware ausgeführt wird.

Um das von den Windows-PCs gesammelte Inventar anzuzeigen, führen Sie die [Computerinventurberichte](understand-microsoft-intune-operations-by-using-reports.md) aus. Intune sammelt das folgende Inventar von den Windows-PCs:

-   **Name**

-   **Chassistyp**

-   **Hersteller**

-   **Modell**

-   **Betriebssystem**

-   **TPM-Version**

-   **Gesamter Speicherplatz**

-   **Verwendeter Speicherplatz**

-   **Freier Speicherplatz**

-   **Name des Betriebssystem-Datenträgers**

-   **Speicherplatz des Betriebssystem-Datenträgers**

-   **Freier Speicherplatz des Betriebssystem-Datenträgers**

-   **Physischer Speicher**

-   **Name des Prozessors**

-   **Prozessorarchitektur**

-   **CPU-Geschwindigkeit**

-   **IP-Adresse**

-   **Seriennummer**

-   **Letzter Benutzer, der sich angemeldet hat**

-   **Zugewiesener Benutzer**

-   **Zuletzt aktualisiert**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->
