---
title: Exchange Connector für Exchange Online
description: Verbinden Sie Intune mit dem Office 365-Exchange-Dienst, um die Verwaltung mobiler Geräte (Mobile Device Management, MDM) mit Exchange ActiveSync zu unterstützen.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 78b4e91fd61bb79c2a3a6d86d5a79c39b320cc5e
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>Konfigurieren des Microsoft Intune Service to Service Connector für Hosted Exchange

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Anhand dieser Informationen können Sie Microsoft Intune und Exchange Online oder den neuen Exchange Online Dedicated-Dienst verbinden. Wenn Sie herausfinden möchten, ob es sich bei Ihrer Exchange Online Dedicated-Umgebung um die **neue** oder die **ältere** Version handelt, wenden Sie sich an Ihren Kundenbetreuer. Intune unterstützt pro Abonnement nur eine Exchange Connector-Verbindung eines beliebigen Typs.

## <a name="service-to-service-connector-requirements"></a>Anforderungen an den Service to Service Connector
Der **Service to Service Connector** unterstützt nur Exchange Online oder Exchange Online Dedicated und stellt keine Anforderungen an die lokale Infrastruktur.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Konfiguration und Ausführung von Exchange Online|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autorität für die Verwaltung mobiler Geräte| [Festlegen von Microsoft Intune als Autorität für die Verwaltung mobiler Geräte](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Microsoft Exchange-Version|Exchange Online oder Exchange Online Dedicated (neu)|/intune/users-permissions-add
|Active Directory-Synchronisierung|Bevor Sie den Intune-Connector verwenden können, müssen Sie die [Active Directory-Synchronisierung einrichten](/intune/users-permissions-add), damit Ihre lokalen Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden.|

### <a name="exchange-cmdlet-requirements"></a>Anforderungen an Exchange-Cmdlets

Sie müssen in Exchange Online ein Benutzerkonto erstellen, das vom Intune Exchange Connector verwendet wird. Das Konto muss über die Berechtigung zum Verwenden der Intune-Verwaltungskonsole und zum Ausführen der folgenden erforderlichen Windows PowerShell-Exchange-Cmdlets verfügen:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Dienst für Service Connector einrichten

1. Öffnen Sie die [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) mit einem Benutzerkonto, das über Administratorrechten für Exchange und Berechtigungen für die [zuvor genannten](#exchange-cmdlet-requirements) Cmdlets verfügt. Microsoft Intune verwendet die E-Mail-Adresse des aktuell angemeldeten Benutzers, um die Verbindung einzurichten.

2.  Wählen Sie im Bereich mit den Arbeitsbereichsverknüpfungen **ADMIN**>**Verwaltung mobiler Geräte** > **Microsoft Exchange** > **Exchange-Verbindung einrichten** aus.
![Seite „Service to Service Connector einrichten“](../media/intunesa5cservicetoserviceconnector.png)

3.  Wählen Sie auf der Seite **Exchange-Verbindung einrichten** die Option **Dienst für Service Connector einrichten** aus.


Der Service to Service Connector wird automatisch konfiguriert und mit Ihrer Exchange Online- oder neuen Exchange Online Dedicated-Umgebung synchronisiert.

## <a name="validate-your-exchange-connection"></a>Überprüfen der Exchange-Verbindung

Nachdem Sie den Exchange Connector erfolgreich konfiguriert haben, fahren Sie mit der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) fort. Wählen Sie **Admin**> **Verwaltung mobiler Geräte** > **Microsoft Exchange** aus. Überprüfen Sie, ob die von Ihnen bereitgestellten Angaben unter **Exchange-Verbindungsinformationen** angezeigt werden.

Sie können auch die Uhrzeit und das Datum des letzten erfolgreichen Synchronisationsversuchs überprüfen.
