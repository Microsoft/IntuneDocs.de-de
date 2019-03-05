---
title: Anzeigen von Gerätedetails mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie Details zu Ihren Geräten an, z.B. Betriebssystem, Speicherplatz, Hersteller und Modell. Mit Microsoft Intune in Azure können Sie eine Liste der installierten Apps abrufen, Konformitätsrichtlinien überprüfen und TeamViewer einrichten. Die Vorgehensweise ähnelt der Anzeige des Bestands der Geräte, die Sie verwalten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76b125c216cd3767df0cb6a374d0fcbeeade794a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232589"
---
# <a name="see-device-details-in-intune"></a>Anzeigen von Gerätedetails in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Das Feature **Geräte** bietet zusätzliche Informationen zu den von Ihnen verwalteten Geräten, z.B. zur Hardware und zu installierten Apps.

Dieser Artikel erläutert, wie Sie all Ihre Geräte und deren Eigenschaften im Azure-Portal anzeigen.

## <a name="view-the-device-details"></a>Anzeigen der Gerätedetails

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** > **Alle Geräte**, und wählen Sie anschließend eins der aufgeführten Geräte aus, damit dessen Gerätedetails geöffnet werden:

   - In der **Übersicht** wird der Gerätename angezeigt, und es sind einige der Schlüsseleigenschaften des Geräts aufgeführt. Sie erfahren also z.B., ob es sich um ein Bring Your Own Device-Gerät (BYOD) handelt, wann es eingecheckt hat usw. Sie können folgende Aktionen auf dem Gerät ausführen:
      - [Außerkraftsetzen](devices-wipe.md#retire)
        - [Zurücksetzen](devices-wipe.md#wipe)
        - [Remotesperre](device-remote-lock.md)
        - [Synchronisieren von Geräten](device-sync.md)
        - [Kennung zurücksetzen](device-passcode-reset.md)
        - [Neu starten](device-restart.md) (nur Windows)
        - [Sauberer Start](device-fresh-start.md) (nur Windows)
     - Starten einer Remoteunterstützungssitzung
   - Verwenden Sie die **Eigenschaften**, um eine [von Ihnen erstellte Gerätekategorie](device-group-mapping.md) zuzuweisen, und ändern Sie den Besitz des Geräts in ein privates oder ein unternehmenseigenes Gerät.
   - Der Bereich **Hardware** umfasst einige Details zu dem Gerät, einschließlich der Geräte-ID, dem Betriebssystem und der Betriebssystemversion, dem Speicherplatz, dem Modell und dem Hersteller, Einstellungen für bedingten Zugriff etc.
   - Unter **Ermittelte Apps** werden alle auf dem Gerät installierten Apps aufgeführt, die von Intune gefunden wurden. Sie können die App-Liste als eine CSV-Datei **exportieren**. Diese Liste wird alle 7 Tage aktualisiert.
   - Unter **Gerätekonformität** werden alle zugewiesenen Konformitätsrichtlinien aufgeführt, und es wird angezeigt, ob das Gerät mit diesen Richtlinien konform ist.
   - Unter **Gerätekonfiguration** werden alle Gerätekonfigurationsrichtlinien angezeigt, die dem Gerät zugewiesen sind, und Sie können erkennen, ob die Richtlinie erfolgreich war oder fehlgeschlagen ist.

Intune erfasst nur auf unternehmenseigenen Geräten eine App-Liste. Auf persönlichen Geräten werden keine Apps überprüft. Bei unternehmenseigenen Windows 10 PCs werden nur moderne Apps aufgeführt. Intune sammelt keine Informationen über Win32-Apps auf dem Gerät. Je nach Netzbetreiber der Geräte werden möglicherweise nicht alle Apps erfasst.

|Plattform|Geräte, die einem Benutzer gehören|Geräte, die dem Unternehmen gehören|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (ohne Configuration Manager-Client)|Nur verwaltete Apps|Nur verwaltete Apps|
|Windows 8.1 (ohne Configuration Manager-Client)|Nur verwaltete Apps|Nur verwaltete Apps|  
|Windows Phone 8|Nur verwaltete Apps|Nur verwaltete Apps|  
|Windows RT|Nur verwaltete Apps|Nur verwaltete Apps|  
|iOS|Nur verwaltete Apps|Alle auf dem Gerät installierten Apps|
|macOS|Alle auf dem Gerät installierten Apps|Alle auf dem Gerät installierten Apps|  
|Android|Nur verwaltete Apps|Alle auf dem Gerät installierten Apps|  
|Android Enterprise|Nur verwaltete Apps|Nur im Arbeitsprofil installierte Apps|  

## <a name="hardware-device-details"></a>Details zum Hardwaregerätestatus
Je nach Netzbetreiber der Geräte werden möglicherweise nicht alle Details erfasst.

|Detail|Beschreibung|Plattform| 
|--------------|----------------------|----|  
|Name|Der Name des Geräts.|Windows, iOS|
|Verwaltungsname|Der Gerätename, der nur in der Konsole verwendet wird. Durch das Ändern dieses Namens wird nicht gleichzeitig der Name des Geräts geändert.|Windows, iOS|
|UDID|Eindeutige Geräte-ID.|Windows, iOS|
|Intune-Geräte-ID|Eine Geräte-ID, die das Gerät eindeutig bezeichnet.|Windows, iOS|
|Seriennummer|Die vom Hersteller für das Gerät vergebene Seriennummer.|Windows, iOS|
|Freigegebenes Gerät|Wenn **Ja** ausgewählt ist, wird das Gerät für mehr als einen Benutzer freigegeben.|Windows, iOS|
|Durch den Benutzer genehmigte Registrierung|Wenn **Ja** ausgewählt ist, dann besitzt das Gerät eine vom Benutzer genehmigte Registrierung, mit der Administratoren bestimmte Sicherheitseinstellungen auf dem Gerät verwalten können.|Windows, iOS|
|Betriebssystem|Das auf dem Gerät verwendete Betriebssystem.|Windows, iOS|
|Betriebssystemversion|Die Version des Betriebssystems auf dem Gerät.|Windows, iOS|
|Betriebssystemsprache|Die für das Betriebssystem auf dem Gerät festgelegte Sprache.|Windows, iOS|
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
|Konformität|Der Konformitätszustand des Geräts.|Windows, iOS, Android|
|EAS aktiviert|Wenn **Ja** ausgewählt ist, ist das Gerät mit einem Exchange-Postfach synchronisiert.|Windows, iOS, Android|
|EAS-Aktivierungs-ID|Die Exchange ActiveSync-ID des Geräts.|Windows, iOS, Android|
|Überwacht|Wenn **Ja** ausgewählt ist, haben die Administratoren die Kontrolle über das Gerät verbessert.|Windows, iOS, Android|
|Verschlüsselt|Wenn **Ja** ausgewählt ist, werden die auf dem Gerät gespeicherten Daten verschlüsselt.|Windows, iOS, Android|



## <a name="next-steps"></a>Nächste Schritte
Finden Sie heraus, welche Aktionen beim [Verwalten Ihrer Geräte](device-management.md) mit Intune noch möglich sind.
