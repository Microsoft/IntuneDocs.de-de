---
title: Einrichten eines Microsoft Intune Exchange Connectors
titleSuffix: Microsoft Intune
description: Verwenden Sie den lokalen Intune Exchange-Connector, um den Zugriff von Geräten auf Exchange-Postfächer basierend auf der Intune-Registrierung und Exchange Active Sync (EAS) zu verwalten.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4751b77362567ad18f5b775e5bda9c1081dd181
ms.sourcegitcommit: 78f9750712c254d8b123ef15b74f30ca999aa128
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2019
ms.locfileid: "71911191"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>Einrichten des lokalen Intune Exchange Connectors
Um den Zugriff auf Exchange zu schützen, nutzt Intune eine lokale Komponente, die als Microsoft Intune Exchange Connector bezeichnet wird. Dieser Connector wird auch an einigen Stellen der Intune-Konsole als *lokaler Connector für Exchange ActiveSync* bezeichnet. 

Die Informationen in diesem Artikel helfen Ihnen beim Installieren und Überwachen des Intune Exchange Connectors. Sie können den Connector mit Ihren [Richtlinien für den bedingten Zugriff](conditional-access-exchange-create.md) verwenden, um Zugriff auf Ihre lokalen Exchange-Postfächer zu gewähren oder zu verweigern. 

Der Connector wird auf Ihrer lokalen Hardware installiert und ausgeführt. Er erkennt Geräte, die sich mit Exchange verbinden, und übermittelt Geräteinformationen an den Intune-Dienst. Je nachdem, ob Geräte registriert und konform sind, werden sie vom Connector zugelassen oder blockiert. Für diese Kommunikation wird das Protokoll HTTPS verwendet.

Wenn ein Gerät versucht, auf Ihre lokale Exchange Server-Instanz zuzugreifen, ordnet der Exchange-Connector Exchange ActiveSync-Datensätze (EAS) in Exchange Server Intune-Datensätzen zu, um sicherzustellen, dass das Gerät bei Intune registriert ist und den Richtlinien Ihres Geräts entspricht. Abhängig von Ihren Richtlinien für bedingten Zugriff kann dem Gerät der Zugriff gewährt oder verweigert werden. Weitere Informationen finden Sie im Artikel [Welche gängigen Möglichkeiten gibt es für die Verwendung des bedingten Zugriffs in Intune?](conditional-access-intune-common-ways-use.md).

Die Vorgänge *Ermittlung* und *Zulassen und blockieren* erfolgen mithilfe standardmäßiger PowerShell-Cmdlets für Exchange. Diese Vorgänge verwenden das Dienstkonto, das bei der Erstinstallation des Exchange-Connectors angegeben wird. 

Intune unterstützt pro Abonnement die Installation mehrerer Intune Exchange Connectors. Wenn Sie über mehrere lokale Exchange-Organisationen verfügen, können Sie für jede einen separaten einrichten. Allerdings kann für jede Exchange-Organisation nur ein Connector installiert werden.  

Befolgen Sie diese allgemeinen Anweisungen zum Einrichten einer Verbindung, die es Intune ermöglicht, mit der lokalen Exchange Server-Instanz zu kommunizieren:

1. Laden Sie den lokalen Connector aus dem Intune-Portal herunter.
2. Installieren und konfigurieren Sie den Exchange Connector auf einem Computer in der lokalen Exchange-Organisation.
3. Überprüfen Sie die Exchange-Verbindung.
4. Wiederholen Sie diese Schritte für jede weitere Exchange-Organisation, die Sie mit Intune verbinden möchten.

## <a name="intune-exchange-connector-requirements"></a>Anforderungen an den Intune Exchange Connector

Um eine Verbindung mit Exchange herzustellen, benötigen Sie ein Konto mit einer Intune-Lizenz, die der Connector verwenden kann. Das Konto geben Sie bei der Installation des Connectors an.  

In der folgenden Tabelle finden Sie die Anforderungen an den Computer, auf dem Sie den Intune Exchange Connector installieren.  

|  Anforderungen  |   Weitere Informationen     |
|---------------|------------------------|
|  Betriebssysteme        | Intune unterstützt den Intune Exchange Connector auf Computern, auf denen eine beliebige Edition von Windows Server 2008 SP2 (64 Bit), Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 oder Windows Server 2016 ausgeführt wird.<br /><br />Auf Server Core-Installationen wird der Connector nicht unterstützt.  |
| Microsoft Exchange          | Für lokale Connectors sind Microsoft Exchange 2010 SP3 oder höher oder die veraltete Exchange Online Dedicated-Umgebung erforderlich. Wenn Sie herausfinden möchten, ob es sich bei Ihrer Exchange Online Dedicated-Umgebung um die *neue* oder die *ältere* Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer. |
| Autorität für die Verwaltung mobiler Geräte           | [Festlegen von Intune als Autorität für die Verwaltung mobiler Geräte](../fundamentals/mdm-authority-set.md). |
| Hardware              | Der Computer, auf dem Sie den Connector installieren, erfordert eine CPU mit 1,6 GHz und 2 GB RAM sowie mindestens 10 GB freien Speicherplatz. |
|  Active Directory-Synchronisierung             | Bevor Sie den Connector verwenden, um Intune mit Ihrer Exchange Server-Instanz zu verbinden, richten Sie [die Active Directory-Synchronisierung](../fundamentals/users-add.md) ein. Ihre lokalen Benutzer und Sicherheitsgruppen müssen mit Ihrer Instanz von Azure Active Directory synchronisiert werden. |
| Zusätzliche Software         | Auf dem Computer, auf dem der Connector gehostet wird, muss eine vollständige Installation von Microsoft.NET Framework 4.5 und Windows PowerShell 2.0 vorhanden sein. |
| Netzwerk               | Der Computer, auf dem Sie den Connector installieren, muss sich in einer Domäne befinden, die sich mit der Domäne, in der Ihre Exchange Server-Instanz gehostet wird, in einer Vertrauensstellung befindet.<br /><br />Konfigurieren Sie den Computer so, dass er über Firewalls und Proxyserver an den Ports 80 und 443 auf den Intune-Dienst zugreifen kann. Intune verwendet diese Domänen: <br> manage.microsoft.com <br> manage.microsoft.com<br> .manage.microsoft.com <br><br> Der Intune Exchange Connector kommuniziert mit den folgenden Diensten: <br> Intune-Dienst: HTTPS-Port 443 <br> Exchange-Clientzugriffsserver: WinRM-Dienstport 443<br> Exchange-AutoErmittlung 443<br> Exchange-Webdienste 443  |

### <a name="exchange-cmdlet-requirements"></a>Anforderungen an Exchange-Cmdlets

Erstellen Sie für den Intune Exchange Connector ein Active Directory-Benutzerkonto. Das Konto muss über die Berechtigung zum Ausführen der folgenden Windows PowerShell-Cmdlets für Exchange verfügen:  

- `Get-ActiveSyncOrganizationSettings`, `Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`, `Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`, `Set-ActiveSyncMailboxPolicy`, `New-ActiveSyncMailboxPolicy`, `Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`, `Set-ActiveSyncDeviceAccessRule`, `New-ActiveSyncDeviceAccessRule`, `Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`, `Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>Herunterladen des Installationspakets

1. Melden Sie sich auf einem Windows-Server mit Unterstützung des Intune Exchange Connectors bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an. Verwenden Sie ein Administratorkonto für die lokale Exchange Server-Instanz, das über eine Nutzungslizenz für Exchange Server verfügt.

2. Wechseln Sie zu **Intune** > **Exchange-Zugriff**.  

3. Wählen Sie **Lokaler Connector für Exchange ActiveSync** unter **Setup** aus, und klicken Sie dann auf **Hinzufügen**.

4. Klicken Sie auf der Seite **Connector hinzufügen** auf **Lokalen Connector herunterladen**. Der Intune Exchange Connector befindet sich in einem komprimierten Ordner (.zip), der geöffnet oder gespeichert werden kann. Wählen Sie im Dialogfeld **Dateidownload** die Option **Speichern** aus, um den komprimierten Ordner an einem sicheren Speicherort zu speichern.


## <a name="install-and-configure-the-intune-exchange-connector"></a>Installieren und Konfigurieren des Intune Exchange Connectors

Führen Sie die folgenden Schritte aus, um den Intune Exchange Connectors zu installieren. Wenn Sie über mehrere Exchange-Organisationen verfügen, wiederholen Sie die Schritte für jeden Exchange-Connector, den Sie einrichten möchten.

1. Extrahieren Sie unter einem vom Intune Exchange Connector unterstützten Betriebssystem die Dateien in **Exchange_Connector_Setup.zip** an einen sicheren Speicherort.
   > [!IMPORTANT]
   > Die Dateien im Ordner *Exchange_Connector_Setup* dürfen nicht umbenannt oder verschoben werden. Etwaige Änderungen führen dazu, dass die Installation des Connectors fehlschlägt.

2. Nachdem die Dateien extrahiert wurden, öffnen Sie den extrahierten Ordner. Doppelklicken Sie auf **Exchange_Connector_Setup.exe**, um den Connector zu installieren.

   > [!IMPORTANT]
   > Wenn der Zielordner kein sicherer Speicherort ist, löschen Sie nach Abschluss der Installation des lokalen Connectors die Zertifikatdatei *MicrosoftIntune.accountcert*.

3. Wählen Sie im Dialogfeld **Microsoft Intune Exchange Connector** entweder **Lokaler Microsoft Exchange-Server** oder **Gehosteter Microsoft Exchange-Server** aus.

   ![Abbildung, die darstellt, wo der Exchange Server-Typ ausgewählt wird](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Geben Sie bei einem lokalen Exchange-Server entweder den Servernamen oder den vollqualifizierten Domänennamen des Exchange-Servers an, auf dem die Rolle **Clientzugriffsserver** gehostet wird.

   Bei einem gehosteten Exchange-Server geben Sie die Adresse des Exchange-Servers an. So ermitteln Sie die URL des gehosteten Exchange-Servers:

   1. Öffnen Sie Outlook für Office 365.

   2. Wählen Sie das **?** links oben und anschließend **Info** aus.

   3. Suchen Sie den Wert **Externer POP-Server**.

   4. Wählen Sie **Proxyserver** aus, um die Proxyservereinstellungen für Ihren gehosteten Exchange-Server anzugeben.

       1. Wählen Sie **Beim Synchronisieren von Informationen für mobile Geräte einen Proxyserver verwenden**aus.

       1. Geben Sie den **Proxyservernamen** und die für den Zugriff auf den Server zu verwendende **Portnummer** ein.

       1. Wenn für den Zugriff auf den Proxyserver Benutzeranmeldeinformationen erforderlich sind, wählen Sie **Mithilfe von Anmeldeinformationen eine Verbindung mit dem Proxyserver herstellen** aus. Geben Sie dann **Domäne\Benutzer** und das **Kennwort** ein.

       1. Wählen Sie **OK** aus.

4. Geben Sie in den Feldern **Benutzer (Domäne\Benutzer)** und **Kennwort** die Anmeldeinformationen für die Verbindung mit Ihrer Exchange Server-Instanz an. Das Konto, das Sie festlegen, muss über eine Lizenz für die Verwendung von Intune verfügen. 

5. Geben Sie die Anmeldeinformationen zum Senden von Benachrichtigungen an das Exchange Server-Postfach eines Benutzers ein. Dieser Benutzer ist nur für Benachrichtigungen reserviert. Der Benutzer für Benachrichtigungen benötigt ein Exchange-Postfach, um Benachrichtigungen per Mail zu senden. Sie können diese Benachrichtigungen in Intune über Richtlinien für den bedingten Zugriff konfigurieren.  

   Stellen Sie sicher, dass der Dienst „AutoErmittlung“ und die Exchange-Webdienste auf dem Exchange-Clientzugriffsserver konfiguriert sind. Weitere Informationen finden Sie unter [Clientzugriffsserver](https://technet.microsoft.com/library/dd298114.aspx).

6. Geben Sie im Feld **Kennwort** das Kennwort für dieses Konto an, damit Intune auf die Exchange Server-Instanz zugreifen kann.

   > [!NOTE]
   > Das Konto, mit dem Sie sich beim Mandanten anmelden, muss mindestens ein Intune-Dienstadministratorkonto sein. Ohne dieses Administratorkonto tritt ein Verbindungsfehler mit folgender Fehlermeldung auf: „Der Remoteserver hat einen Fehler zurückgegeben: (400) Ungültige Anforderung“.

7. Wählen Sie **Verbinden** aus.

   > [!NOTE]
   > Das Konfigurieren der Verbindung kann möglicherweise einige Minuten dauern.

Bei der Konfiguration werden vom Exchange-Connector Ihre Proxyeinstellungen gespeichert, um den Zugriff auf das Internet zu ermöglichen. Wenn sich Ihre Proxyeinstellungen ändern, müssen Sie den Exchange-Connector neu konfigurieren, damit er die aktualisierten Proxyeinstellungen übernimmt.

Nach Einrichtung der Verbindung durch den Exchange-Connector werden mobile Geräte, die von Exchange verwalteten Benutzern zugeordnet sind, automatisch synchronisiert und dem Exchange-Connector hinzugefügt. Diese Synchronisierung kann einige Zeit dauern.

> [!NOTE]
> Wenn Sie den Intune Exchange Connector installieren und später die Exchange-Verbindung löschen müssen, müssen Sie den Connector vom Computer deinstallieren, auf dem er installiert wurde.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installieren von Connectors für mehrere Exchange-Organisationen

Intune unterstützt pro Abonnement mehrere Intune Exchange Connectors. Für einen Mandanten mit mehreren Exchange-Organisationen können Sie pro Exchange-Organisation nur einen Connector einrichten. 

Um Connectors für das Herstellen einer Verbindung mit mehreren Exchange-Organisationen zu installieren, laden Sie den ZIP-Ordner einmal herunter. Verwenden Sie für jeden Connector, den Sie installieren, denselben Download. Führen Sie die Schritte aus dem vorherigen Abschnitt für jeden weiteren Connector aus, um das Setupprogramm zu extrahieren und auf einem Server in der Exchange-Organisation auszuführen.

Jede Exchange-Organisation, die sich mit Intune verbindet, unterstützt Hochverfügbarkeit, Überwachung und manuelle Synchronisierung. Diese Features werden in den folgenden Abschnitten beschrieben.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>Unterstützung von Hochverfügbarkeit durch den Intune Exchange Connector  

Hochverfügbarkeit bedeutet für den lokalen Connector Folgendes: Wenn der Exchange-Clientzugriffsserver, den der Connector verwendet, nicht mehr verfügbar ist, kann der Connector zu einem anderen Clientzugriffsserver der betreffenden Exchange-Organisation wechseln. Der Exchange-Connector selbst unterstützt Hochverfügbarkeit nicht. Wenn der Connector ausfällt, erfolgt kein automatisches Failover. Sie müssen [einen neuen Connector installieren](#reinstall-the-intune-exchange-connector), um den ausgefallenen Connector zu ersetzen. 

Zum Failover verwendet der Connector den angegebenen Clientzugriffsserver, um eine erfolgreiche Verbindung mit Exchange herzustellen. Anschließend ermittelt er zusätzliche Clientzugriffsserver für die betreffende Exchange-Organisation. Dank dieser Ermittlung kann der Connector ein Failover auf einen anderen verfügbaren Clientzugriffsserver durchführen, bis der primäre Clientzugriffsserver wieder verfügbar ist. 

Die Ermittlung weiterer Clientzugriffsserver ist standardmäßig aktiviert. Wenn Sie das Failover deaktivieren müssen:  
1. Navigieren Sie auf dem Server, auf dem der Exchange-Connector installiert ist, zu **% *%ProgramData*%\Microsoft\Microsoft Intune Exchange Connector**. 
2. Öffnen Sie mit einem Text-Editor **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Ändern Sie **\<IsCasFailoverEnabled>*true*\</IsCasFailoverEnabled>** in **\<IsCasFailoverEnabled>*false*\</IsCasFailoverEnabled>** .  
 
## <a name="performance-tune-the-exchange-connector-optional"></a>Optimieren der Leistung des Exchange-Connectors (optional)

Wenn Exchange ActiveSync über 5.000 Geräte unterstützt, können Sie eine optionale Einstellung konfigurieren, um die Leistung des Connectors zu verbessern. Sie verbessern die Leistung, indem Sie für Exchange die Verwendung mehrerer Instanzen des Ausführungsbereichs eines PowerShell-Befehls ermöglichen. 

Bevor Sie diese Änderung vornehmen, sollten Sie sich vergewissern, dass das Konto, das Sie zum Ausführen des Exchange Connectors verwenden, nicht für andere Verwaltungszwecke für Exchange verwendet wird. Ein Exchange-Konto verfügt über eine begrenzte Anzahl von Ausführungsbereichen, von denen die meisten vom Connector verwendet werden. 

Diese Leistungsoptimierung eignet sich nicht für Connectors, die auf älterer oder langsamerer Hardware ausgeführt werden.  

So verbessern Sie die Leistung des Exchange-Connectors 

1. Öffnen Sie auf dem Server, auf dem der Connector installiert ist, dessen Installationsverzeichnis.  Der Standardpfad lautet *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Bearbeiten Sie die Datei *OnPremisesExchangeConnectorServiceConfiguration.xml*.
3. Suchen Sie nach **EnableParallelCommandSupport**, und legen Sie den Wert auf **TRUE** fest:  
     
   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>
4. Speichern Sie die Datei, und starten Sie dann den Microsoft Intune Exchange Connector neu.

## <a name="reinstall-the-intune-exchange-connector"></a>Neuinstallieren des Intune Exchange Connector

Möglicherweise müssen Sie den Intune Exchange Connector neu installieren. Da sich nur ein einzelner Connector mit einer Exchange-Organisation verbinden kann, ersetzt der neue Connector, den Sie installieren, den ursprünglichen Connector, sobald Sie einen zweiten Connector für die Organisation installieren.

1. Um den neuen Connector zu installieren, führen Sie die Schritte im Abschnitt [Installieren und Konfigurieren des Exchange-Connectors](#install-and-configure-the-intune-exchange-connector) aus. 
2. Klicken Sie auf **Ersetzen**, wenn Sie bei der Installation des neuen Connectors dazu aufgefordert werden.  
   ![Konfigurationswarnung bei Ersetzen eines Connectors](./media/exchange-connector-install/prompt-to-replace.png)

3. Setzen Sie die Schritte im Abschnitt [Installieren und Konfigurieren des Intune Exchange Connectors](#install-and-configure-the-intune-exchange-connector) fort, und melden Sie sich erneut bei Intune an.
4. Klicken Sie im letzten Fenster auf **Schließen**, um die Installation abzuschließen.  
   ![Abschließen des Setups](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-an-exchange-connector"></a>Überwachen eines Exchange-Connectors

Nachdem Sie den Exchange-Connector erfolgreich konfiguriert haben, können Sie den Status der Verbindungen und den letzten erfolgreichen Synchronisierungsversuch anzeigen. 

So überprüfen Sie die Verbindung des Exchange-Connectors:

1. Klicken Sie auf dem Intune-Dashboard auf **Exchange-Zugriff**.
2. Klicken Sie auf **Zugriff auf Exchange lokal**, um den Verbindungsstatus der Exchange-Connectors zu überprüfen.

Sie können auch die Uhrzeit und das Datum des letzten erfolgreichen Synchronisationsversuchs überprüfen.

Ab Intune-Version 1710 können Sie das [System Center Operations Manager Management Pack für Exchange-Connector und Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) verwenden. Das Management Pack bietet Ihnen für die Problembehandlung verschiedene Möglichkeiten zur Überwachung des Exchange-Connectors.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Manuelle Erzwingung einer schnellen oder vollständigen Synchronisierung

Ein Intune Exchange Connector synchronisiert EAS- und Intune-Gerätedatensätze automatisch regelmäßig. Wenn sich der Konformitätsstatus eines Geräts verändert, aktualisiert der automatische Synchronisierungsprozess regelmäßig Datensätze, damit der Gerätezugriff entsprechend blockiert und erlaubt werden kann.

- Die **Schnellsynchronisierung** erfolgt regelmäßig mehrmals täglich. Eine Schnellsynchronisierung ruft Geräteinformationen für von Intune lizenzierte und lokale Exchange-Benutzer ab, die bedingtem Zugriff unterliegen und sich seit der letzten Synchronisierung geändert haben.

- Die **vollständige Synchronisierung** erfolgt standardmäßig einmal pro Tag. Eine vollständige Synchronisierung ruft Geräteinformationen für alle für Intune lizenzierten und lokalen Exchange-Benutzer ab, die bedingtem Zugriff unterliegen. Eine vollständige Synchronisierung ruft ebenfalls Exchange Server-Informationen ab und stellt sicher, dass die von Intune im Azure-Portal angegebene Konfiguration für die Exchange Server-Instanz aktualisiert wird. 


Sie können erzwingen, dass ein Connector eine Synchronisierung ausführt, indem Sie im Intune-Dashboard die Optionen **Schnellsynchronisierung** oder **Vollständige Synchronisierung** verwenden:

   1. Klicken Sie auf dem Intune-Dashboard auf **Exchange-Zugriff**.
   2. Klicken Sie auf **Zugriff auf Exchange lokal**.
   3. Wählen Sie den Connector aus, den Sie synchronisieren möchten, wählen Sie anschließend **Schnellsynchronisierung** oder **Vollständige Synchronisierung** aus.

## <a name="next-steps"></a>Nächste Schritte

Erstellen einer [Richtlinie für bedingten Zugriff für lokale Exchange Server-Instanzen](conditional-access-exchange-create.md)
