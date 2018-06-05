---
title: Intune Exchange Connector für Exchange Online
titleSuffix: ''
description: Verbinden Sie Intune mit dem Office 365-Exchange-Dienst, um die Verwaltung mobiler Geräte (Mobile Device Management, MDM) mit Exchange ActiveSync zu unterstützen.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 640d1a5cbd785248cb309bc250c95631295955b3
ms.sourcegitcommit: 71497f0215fc8bed454ac318b0548b1281a8fe0f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Konfigurieren des Exchange-Dienstconnectors für Intune und Exchange Online

In diesem Artikel wird beschrieben, wie Sie den Microsoft Intune-Dienst mit Exchange Online oder dem neuen Exchange Online Dedicated-Dienst verbinden. Wenn Sie herausfinden möchten, ob es sich bei Ihrer Exchange Online Dedicated-Umgebung um die **neue** oder die **ältere** Version handelt, wenden Sie sich an Ihren Kundenbetreuer.

## <a name="service-to-service-connector-requirements"></a>Anforderungen an den Service to Service Connector
Der **Service to Service Connector** unterstützt nur Exchange Online oder Exchange Online Dedicated und stellt keine Anforderungen an eine lokale Infrastruktur.


|              Anforderungen               |                                                                                                            Weitere Informationen                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Konfiguration und Ausführung von Exchange Online |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   Autorität für die Verwaltung mobiler Geräte   |                                                       [Festlegen von Microsoft Intune als Autorität für die Verwaltung mobiler Geräte](mdm-authority-set.md)                                                       |
|       Microsoft Exchange-Version       |                                                                                      Exchange Online oder Exchange Online Dedicated (neu)                                                                                      |
|    Active Directory-Synchronisierung    | Bevor Sie den Intune-Connector verwenden können, müssen Sie die [Active Directory-Synchronisierung einrichten](/intune/users-add), damit Ihre lokalen Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden. |

### <a name="exchange-cmdlet-requirements"></a>Anforderungen an Exchange-Cmdlets

Sie müssen auch ein Exchange Online-Benutzerkonto erstellen, das vom Intune Exchange-Dienstconnector verwendet wird. Das Konto muss über die Berechtigung zum Ausführen der folgenden erforderlichen Windows PowerShell-Exchange-Cmdlets verfügen:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Dienst für Service Connector einrichten

1. Melden Sie sich beim [Azure-Portal](http://portal.azure.com) mit einem Benutzerkonto an, das über Exchange-Administratorrechte und entsprechende Berechtigungen für die [zuvor beschriebenen](#exchange-cmdlet-requirements) Cmdlets verfügt. Microsoft Intune verwendet die E-Mail-Adresse des aktuell angemeldeten Benutzers, um die Verbindung einzurichten.

2. Klicken Sie im Menü links auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune**aus, um das Microsoft Intune-Dashboard zu öffnen. Wählen Sie **Bedingter Zugriff** aus, und wählen Sie dann unter **Setup** die Option **Exchange-Dienstconnector** aus.

4.  Wählen Sie auf der Seite **Bedingter Zugriff – Exchange-Dienstconnector** die Option **Service to Service Connector einrichten** aus. 
   
     ![Abbildung mit der Auswahl des Links „Service to Service Connector einrichten“](media/exchange_service_connector.png)

Der Service to Service Connector wird automatisch konfiguriert und mit Ihrer Exchange Online- oder neuen Exchange Online Dedicated-Umgebung synchronisiert.

## <a name="validate-your-exchange-connection"></a>Überprüfen der Exchange-Verbindung

Nachdem Sie den Exchange Service to Service Connector erfolgreich konfiguriert haben, können Sie auf der Seite **Bedingter Zugriff – Exchange-Dienstconnector** die Informationen zum Exchange Connector-Server überprüfen.

Sie können auch den **Verbindungsstatus** sowie die Uhrzeit und das Datum des letzten erfolgreichen Synchronisationsversuchs überprüfen.

## <a name="next-steps"></a>Nächste Schritte
[Überwachen von bedingtem Zugriff auf Exchange in Microsoft Intune](conditional-access-exchange-monitor.md)