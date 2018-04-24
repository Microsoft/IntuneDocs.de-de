---
title: Exchange Connector-Problembehandlung
description: Behandeln von Problemen, die sich auf den Intune Exchange Connector beziehen.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/26/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0eef4e2ae3792c601bd4a32cd041d7d041091cca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshoot-the-exchange-connector"></a>Exchange Connector-Problembehandlung

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

In diesem Thema wird die Behandlung von Problemen beschrieben, die sich möglicherweise auf den Intune Exchange Connector beziehen.

## <a name="steps-for-checking-the-connector-configuration"></a>Schritte zum Überprüfen der Exchange Connector-Konfiguration 

Überprüfen Sie die Exchange Connector-Konfiguration, und prüfen Sie dann, ob das Problem behoben wurde.

- Achten Sie darauf, dass Sie beim anfänglichen Exchange Connector-Setup ein Benachrichtigungskonto angeben.
- Das Exchange Connector-Dienstkonto muss über die entsprechenden Berechtigungen zum Ausführen von PowerShell-Cmdlets verfügen, die vom Exchange Connector verwendet werden.
- Geben Sie bei der Exchange Connector-Konfiguration einen Clientzugriffsserver (CAS) an, der sich so nah wie möglich beim Server befindet, der den Exchange Connector hostet. Die Latenz bei der Kommunikation zwischen dem Clientzugriffsserver und dem Exchange Connector kann zu Verzögerungen bei der Geräteerkennung führen, insbesondere bei der dedizierten Verwendung von Office 365.
- Denken Sie daran, dass zwischen Exchange Connector-Synchronisierungen mit dem Exchange-Clientzugriffsserver eine zeitliche Verzögerung auftritt. Eine vollständige Synchronisierung erfolgt einmal täglich, während eine schnelle Synchronisierung (Delta) alle zwei Stunden durchgeführt wird. Es besteht die Wahrscheinlichkeit, dass bei einem Benutzer mit einem neu registrierten Gerät Verzögerungen beim Zugriff auftreten.
- 
  ## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync-Gerät wurde von Exchange nicht erkannt
  Überprüfen Sie, ob das Exchange Connector mit dem Exchange-Server synchronisiert wird. Suchen Sie dazu Protokolle für eine vollständige Synchronisierung oder eine Deltasynchronisierung. Weitere Informationen finden Sie unter „Exchange Connector-Protokolle“. Wenn seit der Einbindung des Geräts eine vollständige Synchronisierung oder Deltasynchronisierung erfolgreich abgeschlossen wurde, haben Sie dies als Quelle des Problems beseitigt. Wenn keine Synchronisierung stattgefunden hat, sammeln Sie die Synchronisierungsprotokolle, und fügen Sie sie an Ihre Supportanforderung an.

- Wenn ein Benutzer keine Intune-Lizenz besitzt, erkennt der Exchange Connector seine Geräte nicht.
- Wenn sich die primäre SMTP-Adresse eines Benutzers vom UPN in AAD unterscheidet, erkennt der Exchange Connector keine Geräte für diesen Intune-/AAD-Benutzer. Beheben Sie die primäre SMTP-Adresse.
- Wenn der Clientzugriffsserver, mit dem der Exchange Connector während eines Ermittlungszyklusses kommuniziert, ein Exchange 2010-Clientzugriffsserver ist und Sie sowohl über Exchange 2010- als auch Exchange 2013-Postfachserver verfügen, erkennt der Exchange Connector keine Geräte von Exchange 2013-Benutzern. Um dies zu beheben, konfigurieren Sie den Exchange Connector entsprechend, dass dieser auf einen Exchange 2013-Clientzugriffsserver verweist.  Obwohl dieses Problem in erster Linie dedizierte Office 365-Topologien betrifft, wird dennoch als bewährte Methode empfohlen, auch in anderen Topologien auf einen Exchange 2013-Clientzugriffsserver zu verweisen.
- Für dedizierte Exchange-Umgebungen (Office 365 dediziert) müssen Sie den Exchange Connector während des anfänglichen Setups auf einen Exchange 2013-Clientzugriffsserver (nicht 2010) in der dedizierten Umgebung verweisen, da dieser bei der Ausführung von PowerShell-Cmdlets nur mit diesem Clientzugriffsserver kommuniziert.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Verwenden von PowerShell zum Abrufen weiterer Daten bei Exchange Connector-Problemen
- Verwenden Sie „Get-ActiveSyncDeviceStatistics -mailbox mbx“, um eine Liste aller mobilen Geräte für ein Postfach abzurufen.
- Verwenden Sie „Get-Mailbox -Identity user | select emailaddresses | fl“, um eine Liste von SMTP-Adressen für ein Postfach abzurufen.
- Verwenden Sie „Get-CASMailbox <upn> | fl“, um ausführliche Informationen zum Zugriffsstatus eines Geräts abzurufen.

### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) beschrieben an den Microsoft Support.
