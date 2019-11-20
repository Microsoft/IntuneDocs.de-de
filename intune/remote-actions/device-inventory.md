---
title: Anzeigen von Gerätedetails mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie Details zu Ihren Geräten an, z.B. Betriebssystem, Speicherplatz, Hersteller und Modell. Mit Microsoft Intune in Azure können Sie eine Liste der installierten Apps abrufen, Konformitätsrichtlinien überprüfen und TeamViewer einrichten. Die Vorgehensweise ähnelt der Anzeige des Bestands der Geräte, die Sie verwalten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 918468bf8948ce54082f3fccc0325db07e116966
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713204"
---
# <a name="see-device-details-in-intune"></a>Anzeigen von Gerätedetails in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Das Feature **Geräte** bietet zusätzliche Informationen zu den von Ihnen verwalteten Geräten, z.B. zur Hardware und zu installierten Apps.

Dieser Artikel erläutert, wie Sie all Ihre Geräte und deren Eigenschaften im Azure-Portal anzeigen.

## <a name="view-the-device-details"></a>Anzeigen der Gerätedetails

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Klicken Sie auf **Geräte** > **Alle Geräte**, und wählen Sie anschließend eins der aufgeführten Geräte aus, damit dessen Gerätedetails geöffnet werden:

   - In der **Übersicht** werden der Gerätename und einige wichtige Eigenschaften des Geräts aufgeführt, z. B. ob es sich um ein BYOD-Gerät (Bring-Your-Own-Device), die Einckeckzeit und mehr. Auf diesem Gerät können Sie die folgenden Aktionen ausführen:
      - [Außerkraftsetzen](devices-wipe.md#retire)
      - [Zurücksetzen](devices-wipe.md#wipe)
      - [Remotesperre](device-remote-lock.md)
      - [Synchronisieren von Geräten](device-sync.md)
      - [Kennung zurücksetzen](device-passcode-reset.md)
      - [Neu starten](device-restart.md) (nur Windows)
      - [Sauberer Start](device-fresh-start.md) (nur Windows)
      - Starten einer Remoteunterstützungssitzung
   - Verwenden Sie die **Eigenschaften**, um eine [von Ihnen erstellte Gerätekategorie](../enrollment/device-group-mapping.md) zuzuweisen, und ändern Sie den Besitz des Geräts in ein privates oder ein unternehmenseigenes Gerät.
   - Unter **Hardware** werden viele Details über das Gerät aufgeführt, z. B. die Geräte-ID, das Betriebssystem und die Version, der Speicherplatz und weitere Details.
   - Unter **Ermittelte Apps** werden alle auf dem Gerät installierten Apps aufgeführt, die von Intune gefunden wurden. Weitere Informationen finden Sie unter [Von Intune ermittelte Apps](../apps/app-discovered-apps.md).
   - Unter **Gerätekonformität** werden alle zugewiesenen Konformitätsrichtlinien aufgeführt, und es wird angezeigt, ob das Gerät mit diesen Richtlinien konform ist.
   - Unter **Gerätekonfiguration** werden alle Gerätekonfigurationsrichtlinien angezeigt, die dem Gerät zugewiesen sind, und Sie können erkennen, ob die Richtlinie erfolgreich war oder fehlgeschlagen ist.

## <a name="hardware-device-details"></a>Details zum Hardwaregerätestatus
Je nach Netzbetreiber der Geräte werden möglicherweise nicht alle Details erfasst.

> [!Note]  
> Der Hardware- und Softwarebestand wird im Intune-Dienst alle 7 Tage aktualisiert.

|Detail|Beschreibung|Plattform| 
|--------------|----------------------|----|  
|Name|Der Name des Geräts.|Windows, iOS|
|Verwaltungsname|Der Gerätename, der nur in der Konsole verwendet wird. Durch das Ändern dieses Namens wird nicht gleichzeitig der Name des Geräts geändert.|Windows, iOS|
|UDID|Eindeutige Geräte-ID.|Windows, iOS|
|Intune-Geräte-ID|Eine Geräte-ID, die das Gerät eindeutig bezeichnet.|Windows, iOS|
|Seriennummer|Die vom Hersteller für das Gerät vergebene Seriennummer.|Windows, iOS|
|Freigegebenes Gerät|Wenn **Ja** ausgewählt ist, wird das Gerät für mehr als einen Benutzer freigegeben.|Windows, iOS|
|Durch den Benutzer genehmigte Registrierung|Wenn **Ja** angegeben wird, besitzt das Gerät eine vom Benutzer genehmigte Registrierung, mit der Administratoren bestimmte Sicherheitseinstellungen auf dem Gerät verwalten können.|Windows, iOS|
|Betriebssystem|Das auf dem Gerät verwendete Betriebssystem.|Windows, iOS|
|Betriebssystemversion|Die Version des Betriebssystems auf dem Gerät.|Windows, iOS|
|Betriebssystemsprache|Die für das Betriebssystem auf dem Gerät festgelegte Sprache.|Windows, iOS|
|Buildnummer|Gibt die Buildnummer des Betriebssystems an.|Android|
|Sicherheitspatchebene|Die Sicherheitspatchebene für das Gerät|Android|
|Gesamtmenge des Speicherplatzes|Der gesamte Speicherplatz auf dem Gerät (in GB).|Windows, iOS|
|Freier Speicherplatz|Der gesamte freie Speicherplatz auf dem Gerät (in GB).|Windows, iOS|
|IMEI|Die International Mobile Equipment Identity des Geräts.|Windows, iOS, Android|
|MEID|Der Mobile Equipment Identifier des Geräts.|Windows, iOS, Android|
|Hersteller|Der Hersteller des Geräts.|Windows, iOS, Android|
|Modell|Das Gerätemodell.|Windows, iOS, Android|
|Telefonnummer|Die dem Gerät zugewiesene Telefonnummer.|Windows, iOS, Android|
|Netzbetreiber des Abonnenten|Der Mobilfunkanbieter des Geräts.|Windows, iOS, Android|
|Mobilfunktechnologie|Das vom Gerät verwendete Funksystem.|Windows, iOS, Android|
|WiFi-MAC|Die Media Access Control-Adresse des Geräts.|Windows, iOS, Android|
|ICCID|Der Integrated Circuit Card Identifier, die eindeutige Identifikationsnummer der SIM-Karte.|Windows, iOS, Android|
|Registrierungsdatum|Datum und Uhrzeit der Registrierung des Gerät bei Intune.|Windows, iOS, Android|
|Letzter Kontakt|Datum und Uhrzeit der letzten Verbindung des Gerät bei Intune.|Windows, iOS, Android|
|Code zur Umgehung der Aktivierungssperre|Der Code, mit denen die Aktivierungssperre umgangen werden kann.|Windows, iOS, Android|
|Registriert bei Azure AD|Wenn **Ja** ausgewählt ist, wurde das Gerät bei Azure Active Directory registriert.|Windows, iOS, Android|
|Für Intune registriert|Wenn **Ja** angegeben wird, wurde das Gerät bei Intune registriert.|Windows, iOS, Android|
|Konformität|Der Konformitätszustand des Geräts.|Windows, iOS, Android|
|EAS aktiviert|Wenn **Ja** ausgewählt ist, ist das Gerät mit einem Exchange-Postfach synchronisiert.|Windows, iOS, Android|
|EAS-Aktivierungs-ID|Die Exchange ActiveSync-ID des Geräts.|Windows, iOS, Android|
|Überwacht|Wenn **Ja** ausgewählt ist, haben die Administratoren die Kontrolle über das Gerät verbessert.|Windows, iOS, Android|
|Verschlüsselt|Wenn **Ja** ausgewählt ist, werden die auf dem Gerät gespeicherten Daten verschlüsselt.|Windows, iOS, Android|



## <a name="next-steps"></a>Nächste Schritte
Finden Sie heraus, welche Aktionen beim [Verwalten Ihrer Geräte](device-management.md) mit Intune noch möglich sind.
