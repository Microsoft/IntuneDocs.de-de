---
title: Überwachen von bedingtem Zugriff auf Exchange in Microsoft Intune
titlesuffix: ''
description: Überwachen der Konformität mit bedingtem Zugriff bei einer lokalen Installation von Exchange und Exchange Online durch das Azure-Portal für Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 932dfe32c6df5741615d9db9f303aaee7785d3a3
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
ms.locfileid: "29775357"
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Überwachen der Konformität mit bedingtem Zugriff für Exchange lokal und Exchange Online in Intune

Ab Version Intune 1704 können Administratoren Berichtsinformationen in Zusammenhang mit Exchange ActiveSync-Gerät-Geräteeinträgen sehen, die entweder über den lokalen Exchange-Connector oder dem Intune Service to Service Connector (Exchange Online-Connector) mit Intune synchronisiert werden. Berichte zur Kompatibilität mit bedingtem Zugriff enthalten eine Zusammenfassung der Geräte mit unterschiedlichen Synchronisierungsstatus:

-   **Zulassen**

-   **Blockieren**

-   **Quarantäne**

## <a name="to-monitor-conditional-access-compliance"></a>Überwachen der Kompatibilität mit bedingtem Zugriff

1.  Melden Sie sich im [Azure-Portal](https://portal.azure.com/) mit Ihren Intune-Anmeldeinformationen an.

2.  Sobald Sie erfolgreich angemeldet sind, wird das **Azure-Dashboard** angezeigt.

3.  Klicken Sie im Menü links auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

4.  Wählen Sie **Intune** aus. Das **Intune-Dashboard** wird angezeigt.

5.  Klicken Sie auf **Bedingter Zugriff** > **Übersicht**.

6.  Wählen Sie im Diagramm einen der drei Bereiche (**Zugelassen**, **Blockiert** oder **Quarantäne**) aus, um Ihre Berichte zur Konformität mit bedingtem Zugriff anzuzeigen.

    ![Bild des Dashboards für den bedingten Zugriff](./media/CA-reporting-intune-1.png)

Nachdem Sie einen der drei Bereiche ausgewählt haben, können Sie weitere Details über zugelassene, blockierte oder unter Quarantäne gestellte Geräte sehen.

Sie können auch ein Drilldown auf bestimmte Geräte ausführen, um weitere Details anzuzeigen. Beispielsweise ist das in der nachfolgenden Abbildung ausgewählte Gerät blockiert. Intune bietet Ihnen die Möglichkeit, Unternehmensdaten aus dem Bereich zum Bericht zur Konformität mit bedingtem Zugriff zu entfernen.

![Bild des Berichts mit Informationen zu den Gerätedetails mit bedingtem Zugriff](./media/CA-reporting-intune-3.png)

Im Bereich mit den Gerätedetails finden Sie weitere Informationen:

-   **Übersicht:** Folgende Eigenschaften des Geräts werden angezeigt: Betriebssystemversion, Gerätemodell, Besitz, Seriennummer, Gerätehersteller, Telefonnummer und Zeitpunkt, an dem das Gerät zuletzt eingecheckt wurde.

-   **Eigenschaften:** Sie können den Gerätebesitz (privat oder Unternehmen) festlegen.

-   **Hardware:** Dieser Abschnitt enthält Informationen, die Sie in der Übersicht sehen, sowie Speicherdetails (gesamter und freier Speicherplatz), Systemgehäuse, Netzwerkdetails, Netzwerkdienst und weitere Details über Sperrungen des bedingten Zugriffs.

-   **Ermittelte Apps:** In diesem Abschnitt werden alle Programme angezeigt, die auf Ihrem Gerät installiert sind. Sie können die Liste der installierten Apps auch im .CSV-Format exportieren.

-   **Kompatibilität:** In diesem Abschnitt werden alle Details zu Richtlinien für die Gerätekompatibilität angezeigt.

-   **Gerätekonfiguration:** In diesem Abschnitt werden alle Details zur Gerätekonfiguration angezeigt.

-   **Exchange-Zugriff:** Hier finden Sie weitere Informationen über den Gerätestatus nach der Anwendung von Richtlinien für den bedingten Zugriff.
