---
title: Der Legacy-Intune-PC-Client und Intune in Azure
description: Überlegungen bei der Verwaltung der Windows-Geräte Ihrer Organisation mit Intune in Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 717f85737ac7db4bd7c0401eb7e763e4fc691406
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238165"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune in der Azure-Konsole und der Legacy-Intune-PC-Client

Intune verwendet eine Azure-basierte SaaS-Anwendungsdienstarchitektur. Azure bietet erhebliche Verbesserungen in den Bereichen Skalierung, Kapazität und Leistung. Dies bietet erweiterte Funktionen für Intune-Administratoren sowie optimierte Workflows im Azure-Portal. 

Ziehen Sie bei der Verwaltung der Windows-Geräte Ihrer Organisation mit Intune in Azure die folgenden Punkte in Betracht:

## <a name="manage-windows-10-devices-by-using-mdm"></a>Verwalten von Windows 10-Geräten mithilfe von MDM

Wir empfehlen die Verwendung der [mobilen Geräteverwaltung (Mobile Device Management, MDM) zum Verwalten Ihrer Windows 10-Geräte](https://docs.microsoft.com/intune/device-restrictions-windows-10) anstelle des Legacy-Intune-PC-Clients. Die Möglichkeit zum Verwalten von Windows 10 über MDM steht in Intune über das Azure-Portal zur Verfügung. MDM für Windows 10 bietet viele neue Verwaltungs- und Sicherheitsfunktionen, die über den Legacy-Intune-PC-Client nicht verfügbar sind.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Legacy-PC-Client-Funktionen sind nur in der Silverlight-Konsole verfügbar.

Für die Intune-PC-Client-Verwaltungsworkflows wird die [Silverlight-basierte Intune-Verwaltungskonsole](https://manage.microsoft.com/) verwendet. Das hat folgende Konsequenzen:

- Für alle Verwaltungsaufgaben ohne Gruppierung, die mithilfe des Intune-PC-Clients durchgeführt werden, müssen Sie die Silverlight-Konsole verwenden.
- Wenn Sie Gruppen verwalten, müssen Sie [Intune im Azure-Portal](https://portal.azure.com/) verwenden. Diese Anforderung gilt, weil Intune jetzt Azure AD-Gruppen anstelle der Legacy-Intune-Gruppen verwendet. 

Aufgrund der Umstellung auf Azure AD-Gruppen hat sich die „gruppenbasierte“ Filterung in den Dashboardansichten der Silverlight-Konsole leicht verändert. Gehen Sie folgendermaßen vor, um in der aktualisierten Silverlight-Benutzeroberfläche zu filtern:

1. Wählen Sie eine Ansicht aus.
2. Geben Sie im Feld **Filter** den Namen der Gruppe ein, nach der Sie filtern möchten, und drücken Sie die EINGABETASTE. Dadurch wird die Listenansicht auf die Geräte in dieser jeweiligen Gruppe gefiltert.

   ![](media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Weiteres Verwalten von Windows 7 mit dem Intune-PC-Client

Da Windows 7 nicht über MDM verwaltet werden kann, stellen wir nur in der Silverlight-Konsole weiterhin Unterstützung für vorhandene Intune-PC-Client-Funktionen zur Verfügung. Erwägen Sie bei einem Upgrade auf Windows 10 eine Migration zur MDM-Verwaltung.

## <a name="mdm-capabilities"></a>MDM-Funktionen

Einen ausführlichen Vergleich zwischen PC-Client und MDM-Funktionen finden Sie unter [Vergleichen der Verwaltung von Windows-PCs als Computer oder mobile Geräte](pc-management-comparison.md). Über MDM-Updates werden weiterhin neue Verwaltungsfunktionen für in MDM registrierte Windows 10-Geräte bereitgestellt, einschließlich Auswertungsoptionen für Win32-Apps. Unter [Neuerungen](https://docs.microsoft.com/intune/whats-new) finden Sie die neuesten Features, die dem Dienst hinzugefügt wurden.

## <a name="switch-from-pc-client-to-mdm"></a>Umstellen vom PC-Client auf MDM

Um die Verwaltung von Windows 10-Geräten mit dem Intune-PC-Client auf die Verwaltung mit MDM umzustellen, gehen Sie folgendermaßen vor:

1. Führen Sie in der Silverlight-Konsole eine **selektive Zurücksetzung** durch, um die Registrierung des Geräts beim PC-Client aufzuheben.
  ![](media/intune-legacy-pc-client/image02.png)
2. Registrieren Sie das Gerät neu bei [MDM (und/oder Azure AD Join)](https://docs.microsoft.com/intune/windows-enroll). 

## <a name="next-steps"></a>Nächste Schritte
[Registrieren von Windows-Geräten](https://docs.microsoft.com/intune/windows-enroll)

 
