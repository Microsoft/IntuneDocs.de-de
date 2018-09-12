---
title: Anzeigen von Gerätedetails mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie Details zu Ihren Geräten an, z.B. Betriebssystem, Speicherplatz, Hersteller und Modell. Mit Microsoft Intune in Azure können Sie eine Liste der installierten Apps abrufen, Konformitätsrichtlinien überprüfen und TeamViewer einrichten. Die Vorgehensweise ähnelt der Anzeige des Bestands der Geräte, die Sie verwalten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a658182800f480f27097e078f28adc95c35aa3ea
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313177"
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
   - Unter **Ermittelte Apps** werden alle auf dem Gerät installierten Apps aufgeführt, die von Intune gefunden wurden. Sie können die App-Liste als eine CSV-Datei **exportieren**.
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

## <a name="hardware-device-details"></a>Details zum Hardwaregerätestatus

### <a name="windows-and-ios-device-details"></a>Details zu Windows- und iOS-Geräten:
|Detail|Beschreibung|  
|--------------|----------------------|  
|Name|Der Name des Geräts.|
|Verwaltungsname|Der Gerätename, der nur in der Konsole verwendet wird. Durch das Ändern dieses Namens wird nicht gleichzeitig der Name des Geräts geändert.|
|UDID|Eindeutige Geräte-ID.|
|Intune-Geräte-ID|Eine Geräte-ID, die das Gerät eindeutig bezeichnet.|
|Seriennummer|Die vom Hersteller für das Gerät vergebene Seriennummer.|
|Freigegebenes Gerät|Wenn **Ja** ausgewählt ist, wird das Gerät für mehr als einen Benutzer freigegeben.|
|Durch den Benutzer genehmigte Registrierung|Wenn **Ja** ausgewählt ist, dann besitzt das Gerät eine vom Benutzer genehmigte Registrierung, mit der Administratoren bestimmte Sicherheitseinstellungen auf dem Gerät verwalten können.|
|Betriebssystem|Das auf dem Gerät verwendete Betriebssystem.|
|Betriebssystemversion|Die Version des Betriebssystems auf dem Gerät.|
|Betriebssystemsprache|Die für das Betriebssystem auf dem Gerät festgelegte Sprache.|
|Gesamtmenge des Speicherplatzes|Der gesamte Speicherplatz auf dem Gerät (in GB).|
|Freier Speicherplatz|Der gesamte freie Speicherplatz auf dem Gerät (in GB).|


### <a name="windows-ios-and-macos-device-details"></a>Details zu Windows-, iOS- und MacOS-Geräten
|Detail|Beschreibung|  
|--------------|----------------------|  
|IMEI|Die International Mobile Equipment Identity des Geräts.|
|MEID|Der Mobile Equipment Identifier des Geräts.|
|Hersteller|Der Hersteller des Geräts.|
|Modell|Das Gerätemodell.|
|Telefonnummer|Die dem Gerät zugewiesene Telefonnummer.|
|Netzbetreiber des Abonnenten|Der Mobilfunkanbieter des Geräts.|
|Mobilfunktechnologie|Das vom Gerät verwendete Funksystem.|
|WiFi-MAC|Die Media Access Control-Adresse des Geräts.|
|ICCID|Der Integrated Circuit Card Identifier, die eindeutige Identifikationsnummer der SIM-Karte.|
|Registrierungsdatum|Datum und Uhrzeit der Registrierung des Gerät bei Intune.|
|Letzter Kontakt|Datum und Uhrzeit der letzten Verbindung des Gerät bei Intune.|
|Code zur Umgehung der Aktivierungssperre|Der Code, mit denen die Aktivierungssperre umgangen werden kann.|
|Registriert bei Azure AD|Wenn **Ja** ausgewählt ist, wurde das Gerät bei Azure Active Directory registriert.|
|Konformität|Der Konformitätszustand des Geräts.|
|EAS aktiviert|Wenn **Ja** ausgewählt ist, ist das Gerät mit einem Exchange-Postfach synchronisiert.|
|EAS-Aktivierungs-ID|Die Exchange ActiveSync-ID des Geräts.|
|Überwacht|Wenn **Ja** ausgewählt ist, haben die Administratoren die Kontrolle über das Gerät verbessert.|
|Verschlüsselt|Wenn **Ja** ausgewählt ist, werden die auf dem Gerät gespeicherten Daten verschlüsselt.|



## <a name="next-steps"></a>Nächste Schritte
Finden Sie heraus, welche Aktionen beim [Verwalten Ihrer Geräte](device-management.md) mit Intune noch möglich sind.