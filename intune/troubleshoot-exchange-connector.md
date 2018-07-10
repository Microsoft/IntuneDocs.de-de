---
title: Exchange Connector-Problembehandlung
description: Erfahren Sie, wie Sie Problemen mit dem lokalen Intune Exchange Connector behandeln.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 70428cae999d91e83af43a0be0249ee3554c7dde
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238169"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Behandeln von Problemen mit dem lokalen Intune Exchange Connector

In diesem Artikel wird beschrieben, wie Sie Problemen mit dem lokalen Intune Exchange Connector behandeln.

## <a name="steps-for-checking-the-connector-configuration"></a>Schritte zum Überprüfen der Exchange Connector-Konfiguration 

Überprüfen Sie das [Setup des lokalen Intune Exchange Connectors](exchange-connector-install.md), um sicherzustellen, dass der Connector ordnungsgemäß konfiguriert ist. Im Folgenden werden häufige Probleme aufgeführt. Wenn Sie alle Korrekturen vorgenommen haben, sollten Sie überprüfen, ob das Problem behoben wurde.

 - Stellen Sie im Dialogfeld „Microsoft Intune Exchange Connector“ sicher, dass Sie ein Benutzerkonto angegeben haben, das die richtigen Berechtigungen besitzt, um die erforderlichen [Windows PowerShell-Exchange-Cmdlets](exchange-connector-install.md#exchange-cmdlet-requirements) auszuführen.
- Aktivieren Sie Benachrichtigungen, und geben Sie ein Benachrichtigungskonto an.
 - Geben Sie bei der Exchange Connector-Konfiguration einen Clientzugriffsserver (CAS) an, der sich so nah wie möglich beim Server befindet, der den Exchange Connector hostet. Die Latenz bei der Kommunikation zwischen dem Clientzugriffsserver und dem Exchange Connector kann zu Verzögerungen bei der Geräteerkennung führen, insbesondere bei der dedizierten Verwendung von Exchange Online.
 - Bei einem Benutzer mit einem neu registrierten Gerät kann es beim Zugriff zu Verzögerungen kommen, bis der Exchange Connector mit dem Exchange-Clientzugriffsserver synchronisiert wurde. Eine vollständige Synchronisierung erfolgt einmal täglich, während eine schnelle Synchronisierung (Delta) mehrmals täglich durchgeführt wird.  Sie können eine [schnelle oder vollständige Synchronisierung manuell erzwingen](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync), um Verzögerungen zu minimieren.
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync-Gerät wurde von Exchange nicht erkannt
[Überwachen Sie die Aktivitäten des Exchange Connectors](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support), um festzustellen, ob der Exchange Connector mit dem Exchange-Server synchronisiert wird. Wenn eine vollständige oder schnelle Synchronisierung erfolgreich abgeschlossen wurde, seit das Gerät verknüpft wurde, können Sie es auf andere mögliche Probleme überprüfen, die im Folgenden aufgeführt sind. Wenn keine Synchronisierung stattgefunden hat, sammeln Sie die Synchronisierungsprotokolle, und fügen Sie sie an eine Supportanfrage an.

 - Stellen Sie sicher, dass der Benutzer eine Intune-Lizenz besitzt, andernfalls erkennt der Exchange Connector dessen Geräte nicht.
 - Wenn die primäre SMTP-Adresse eines Benutzers sich von seinem Benutzerprinzipalnamen in Azure Active Directory (Azure AD) unterscheidet, erkennt der Exchange Connector keine Geräte für diesen Benutzer. Korrigieren Sie die primäre SMTP-Adresse, um das Problem zu beheben.
 - Wenn in Ihrer Umgebung Exchange 2010- und Exchange 2013-Postfachserver vorhanden sind, wird empfohlen, den Exchange Connector auf einen Exchange 2013-Clientzugriffsserver zu verweisen. Wenn der Exchange Connector für die Kommunikation mit einem Exchange 2010-Clientzugriffsserver eingerichtet ist, erkennt dieser keine Exchange 2013-Geräte von Benutzern. 
- Für dedizierte Exchange Online-Umgebungen müssen Sie den Exchange Connector während des anfänglichen Setups auf einen Exchange 2013-Clientzugriffsserver (nicht auf einen Exchange 2010-Clientzugriffsserver) in der dedizierten Umgebung verweisen, da dieser bei der Ausführung von PowerShell-Cmdlets nur mit diesem Clientzugriffsserver kommuniziert.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Verwenden von PowerShell zum Abrufen weiterer Daten bei Exchange Connector-Problemen
- Verwenden Sie den Befehl „Get-ActiveSyncDeviceStatistics -mailbox mbx“, um eine Liste aller mobilen Geräte für ein Postfach abzurufen.
- Verwenden Sie den Befehl „Get-Mailbox -Identity user | select emailaddresses | fl“, um eine Liste von SMTP-Adressen für ein Postfach abzurufen.
- Verwenden Sie „Get-CASMailbox <upn> | fl“, um ausführliche Informationen zum Zugriffsstatus eines Geräts abzurufen.

### <a name="next-steps"></a>Nächste Schritte
Wenn Sie weitere Hilfe benötigen, können Sie ebenfalls [Support für Microsoft Intune](get-support.md) anfordern.
