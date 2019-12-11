---
title: Behandeln von häufigen Fehlern für den InTune Exchange Connector
titleSuffix: Microsoft Intune
description: Beheben und Beheben allgemeiner Fehler für die lokale Microsoft InTune Exchange Connector
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b30a7e843850d6918abc2e76f84397a1f197516f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508861"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Beheben von häufigen Fehlern für den InTune Exchange Connector

Dieser Artikel hilft dem InTune-Administrator dabei, bestimmte Fehler und Meldungen zum Betrieb von InTune Exchange Connector zu beheben.  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>Fehler bei der Konfiguration. Fehlercode 0x0000001

**Problem:**  
Wenn Sie versuchen, die Microsoft InTune Exchange Connector zu konfigurieren, erhalten Sie die folgende Fehlermeldung:

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

Dieses Problem kann auftreten, wenn die Internet Proxy Einstellungen falsch konfiguriert sind.

**Lösung**:  
Konfigurieren von Proxyeinstellungen:
1. Wenden Sie sich an den Administrator des lokalen Netzwerks, um sicherzustellen, dass die Proxy Einstellungen ordnungsgemäß konfiguriert sind. 
2. Verwenden Sie den Befehl **netsh WinHTTP** , um den Proxy Server zu konfigurieren und die erforderliche Ausschlussliste hinzuzufügen. Beispiel:  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>Fehler bei der Konfiguration. Fehlercode 0x000000b   

**Problem:**  
Wenn Sie versuchen, die Microsoft InTune Exchange Connector zu konfigurieren, erhalten Sie die folgende Fehlermeldung:  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Dieses Problem kann auftreten, wenn das Konto, das Sie für die Anmeldung bei InTune verwendet haben, kein globales InTune-Administrator Konto ist.

**Lösung**:  
Melden Sie sich bei InTune mit einem Konto an, das ein globaler Administrator ist, oder fügen Sie Ihr Konto der globalen Administrator Gruppe hinzu. Weitere Informationen finden Sie unter [Rollenbasierte Zugriffssteuerung (RBAC) mit Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>Fehler bei der Konfiguration. Fehlercode 0x0000006

**Problem:**  
Wenn Sie versuchen, die Microsoft InTune Exchange Connector zu konfigurieren, erhalten Sie die folgende Fehlermeldung:  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
Dieser Fehler kann auftreten, wenn ein Proxy Server verwendet wird, um eine Verbindung mit dem Internet herzustellen, und den Datenverkehr an den InTune-Dienst blockiert. Um zu ermitteln, ob ein Proxy verwendet wird, wechseln Sie zu **Systemsteuerung** > **Internet Optionen**, wählen Sie die Registerkarte **Verbindung** aus, und klicken Sie dann auf **LAN-Einstellungen**.

**Lösung**:  

- **Option 1** : Entfernen Sie die Proxy Einstellungen, damit der Computer eine Verbindung mit dem Internet herstellen kann, ohne den Proxy zu durchlaufen.  

- **Option 2** : Konfigurieren Sie den Proxy Server so, dass die Kommunikation mit dem InTune-Dienst zulässig ist, wie in den [Anforderungen von InTune Exchange Connector](exchange-connector-install.md#intune-exchange-connector-requirements)beschrieben.



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>Ereignis 7000 oder 7041: Microsoft InTune Exchange Connector Dienst wird nicht gestartet.

**Problem:**  
Ein IOS-Gerät kann nicht bei InTune registriert werden und generiert eine der folgenden Fehlermeldungen:  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
Dieses Problem kann auftreten, wenn das **WIEC_User** Konto nicht über das Benutzerrecht " **Anmelden als Dienst** " in der lokalen Richtlinie verfügt.

**Lösung**:  
Weisen Sie auf dem Computer, auf dem InTune Exchange Connector ausgeführt wird, das Benutzerrecht **Anmelden als Dienst** dem **WIEC_User** -Dienst Konto zu. Wenn es sich bei dem Computer um einen Knoten in einem Cluster handelt, stellen Sie sicher, dass Sie dem Cluster Dienst Konto auf allen Knoten im Cluster das Benutzerrecht *Anmelden als Dienst* zuweisen.  

Gehen Sie folgendermaßen vor, um das Benutzerrecht " **Anmelden als Dienst** " dem **WIEC_User** -Dienst Konto auf dem Computer zuzuweisen:

1. Melden Sie sich beim Computer als Administrator oder als Mitglied der Gruppe "Administratoren" an.
2. Führen Sie **secpol. msc** aus, um die lokale Sicherheitsrichtlinie zu öffnen.
3. Wechseln Sie zu **Sicherheitseinstellungen** > **lokale Richtlinien**, und wählen Sie dann zuweisen von **Benutzerrechten**aus.
4. Doppelklicken Sie auf den rechten Bereich **Anmelden als Dienst**.
5. Wählen Sie **Benutzer oder Gruppe hinzufügen**aus, fügen Sie der Richtlinie **WIEC_USER** hinzu, und wählen Sie dann zweimal **OK** aus.

Wenn das Benutzerrecht " **Anmelden als Dienst** " **WIEC_User** zugewiesen wurde, aber später entfernt wurde, wenden Sie sich an den Domänen Administrator, um zu bestimmen, ob er von einer Gruppenrichtlinie Einstellung überschrieben wird.  

## <a name="next-steps"></a>Nächste Schritte  

Der folgende Artikel hilft Ihnen dabei, bestimmte Fehler zu beheben:
- [Beheben allgemeiner Probleme mit dem InTune Exchange Connector](troubleshoot-exchange-connector-common-problems.md). git 

Suchen Sie Unterstützung durch Support oder InTune-Community.
- Weitere Informationen finden Sie [unter Support](../fundamentals/get-support.md) zur Verwendung der InTune-Konsole, um das Problem zu beheben, oder um eine Support Anfrage bei Microsoft zu eröffnen. 
- Veröffentlichen Sie Ihr Problem in den [Microsoft InTune-Foren](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
