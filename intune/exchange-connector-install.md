---
title: Einrichten des lokalen Microsoft Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Verwenden Sie den lokalen Exchange Connector, um den Zugriff der Geräte auf Exchange-Postfächer basierend auf der Intune-Registrierung und Exchange Active Sync (EAS) zu verwalten.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
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
ms.openlocfilehash: 57684a1f5ef94b12c8f0e52a36d8432583391b8a
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045683"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Einrichten des lokalen Exchange Connectors in Microsoft Intune
Die in diesem Artikel enthaltenen Informationen unterstützen Sie beim Installieren und anschließenden Überwachen des lokalen Exchange Active Sync-Connectors für Intune.  Sie verwenden den lokalen Intune Exchange-Connector mit Ihren [Richtlinien für den bedingten Zugriff, um den Zugriff auf Ihre lokalen Exchange-Postfächer zu gewähren oder zu verweigern](conditional-access-exchange-create.md). 

Wenn ein Gerät versucht, auf den lokalen Exchange-Connector zuzugreifen, ordnet der Exchange-Connector EAS-Datensätze (Exchange Active Sync) in Exchange Server Intune-Datensätzen zu, um die Geräteregistrierung bei Intune und die Konformität mit Ihren Gerätekonformitätsrichtlinien zu prüfen. Abhängig von Ihren Richtlinien für bedingten Zugriff kann dem Gerät Zugriff gewährt oder verweigert werden. Weitere Informationen finden Sie im Artikel [Welche gängigen Möglichkeiten gibt es für die Verwendung des bedingten Zugriffs in Intune?](conditional-access-intune-common-ways-use.md)

Intune unterstützt die Installation mehrerer lokaler Exchange-Connectors pro Abonnement. Wenn Sie über mehrere lokale Exchange-Organisationen verfügen, können Sie für jede einen separaten einrichten. Allerdings kann nur ein Connector für die Verwendung jeder einzelnen Exchange-Organisation installiert werden. 

Die folgenden allgemeinen Schritte dienen zum Einrichten einer Verbindung, die es Intune ermöglicht, mit der lokalen Exchange Server-Instanz zu kommunizieren:

1. Laden Sie den lokalen Intune Exchange-Connector aus dem Intune-Portal herunter.
2. Installieren und konfigurieren Sie den Exchange Connector auf einem Computer in der lokalen Exchange-Organisation.
3. Überprüfen Sie die Exchange-Verbindung.
4. Wiederholen Sie diese Schritte für jede weitere Exchange-Organisation, die Sie mit Intune verbinden möchten.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Anforderungen des lokalen Intune Exchange Connectors
Sie benötigen ein Konto mit einer Intune-Lizenz, die vom Connector zum Herstellen einer Verbindung mit Exchange verwendet werden kann. Das Konto wird bei der Installation des Connectors angegeben.  

In der folgenden Tabelle finden Sie die Anforderungen an den Computer, auf dem Sie den lokalen Exchange Connector installieren.  

|  Anforderungen  |   Weitere Informationen     |
|---------------|------------------------|
|  Betriebssysteme        | Intune unterstützt den lokalen Exchange Connector auf Computern, auf denen eine beliebige Edition von Windows Server 2008 SP2 (64 Bit), Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 oder Windows Server 2016 ausgeführt wird.<br /><br />Auf Server Core-Installationen wird der Connector nicht unterstützt.  |
| Microsoft Exchange          | Für lokale Connectors sind Microsoft Exchange 2010 SP3 oder höher oder die veraltete Exchange Online Dedicated-Umgebung erforderlich. Wenn Sie herausfinden möchten, ob es sich bei Ihrer Exchange Online Dedicated-Umgebung um die <strong>neue</strong> oder die <strong>ältere</strong> Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer. |
| Autorität für die Verwaltung mobiler Geräte           | [Festlegen von Intune als Autorität für die Verwaltung mobiler Geräte](mdm-authority-set.md). |
| Hardware              | Der Computer, auf dem Sie den Connector installieren, erfordert eine CPU mit 1,6 GHz und 2 GB RAM sowie mindestens 10 GB freien Speicherplatz. |
|  Active Directory-Synchronisierung             | Bevor Sie den Connector für die Verbindung von Intune mit Exchange Server verwenden können, müssen Sie die [Active Directory-Synchronisierung](users-add.md) einrichten, damit Ihre lokalen Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden. |
| Zusätzliche Software         | Eine vollständige Installation von Microsoft .NET Framework 4.5 und Windows PowerShell 2.0 muss auf dem Computer installiert sein, auf dem der Connector gehostet wird. |
| Netzwerk               | Der Computer, auf dem Sie den Connector installieren, muss sich in einer Domäne befinden, die sich mit der Domäne, in der Exchange Server gehostet wird, in einer Vertrauensstellung befindet.<br /><br />Der Computer erfordert Konfigurationen, die es ihm ermöglichen, über Firewalls und Proxyserver über Port 80 und 443 auf den Intune-Dienst zuzugreifen. Von Intune verwendete Domänen sind manage.microsoft.com, &#42;manage.microsoft.com und &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Anforderungen an Exchange-Cmdlets

Erstellen Sie ein Active Directory-Benutzerkonto, das vom lokalen Exchange-Connector verwendet wird. Das Konto muss über die Berechtigung zum Ausführen der folgenden erforderlichen Windows PowerShell-Exchange-Cmdlets verfügen:


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Herunterladen des Softwareinstallationspakets für den lokalen Exchange Connector

1. Öffnen Sie auf einem vom lokalen Exchange Connector unterstützten Windows Server-Betriebssystem das [Azure-Portal](https://portal.azure.com) mit einem Administratorkonto in der lokalen Exchange Server-Instanz, für das eine Exchange Server-Lizenz vorhanden ist.

2. Wechseln Sie zu **Intune** > **Exchange-Zugriff**  

3. Wählen Sie **Lokaler Connector für Exchange ActiveSync** unter **Setup** aus, und klicken Sie dann auf **Hinzufügen**.

4. Klicken Sie auf der Seite **Connector hinzufügen** auf **Lokalen Connector herunterladen**. Der lokale Exchange Connector befindet sich in einem komprimierten Ordner (.zip), der geöffnet oder gespeichert werden kann. Wählen Sie im Dialogfeld **Dateidownload** die Option **Speichern** aus, um den komprimierten Ordner an einem sicheren Speicherort zu speichern.

    > [!IMPORTANT]
    > Die Dateien im Ordner des lokalen Exchange Connectors dürfen nicht umbenannt oder verschoben werden. Bei Verschieben oder Umbenennen der Inhalte des Ordners ist die Exchange Connector-Installation nicht mehr funktionsfähig.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installieren und Konfigurieren des lokalen Intune Exchange Connectors
Führen Sie die folgenden Schritte aus, um den lokalen Intune Exchange Connector zu installieren. Wenn Sie über mehrere Exchange-Organisationen verfügen, wiederholen Sie diese Schritte für jeden zusätzlichen Exchange Connector, den Sie einrichten möchten.

1. Extrahieren Sie unter einem für den lokalen Exchange Connector unterstützten Betriebssystem die Dateien in **Exchange_Connector_Setup.zip** an einen sicheren Speicherort.

2. Nachdem die Dateien extrahiert wurden, öffnen Sie den extrahierten Ordner, und doppelklicken Sie auf **Exchange_Connector_Setup.exe**, um den lokalen Exchange Connector zu installieren.

   > [!IMPORTANT]
   > Wenn der Speicherort nicht sicher ist, sollten Sie die Zertifikatdatei **MicrosoftIntune.accountcert** nach Abschluss der Installation des lokalen Connectors unbedingt löschen.

3. Wählen Sie im Dialogfeld **Microsoft Intune Exchange Connector** entweder **Lokaler Microsoft Exchange-Server** oder **Gehosteter Microsoft Exchange-Server** aus.

   ![Abbildung, die darstellt, wo der Exchange Server-Typ ausgewählt wird](./media/intune-sa-exchange-connector-config.png)

   Geben Sie bei einem lokalen Exchange-Server entweder den Servernamen oder den vollqualifizierten Domänennamen des Exchange-Servers an, auf dem die Rolle **Clientzugriffsserver** gehostet wird.

   Bei einem gehosteten Exchange-Server geben Sie die Adresse des Exchange-Servers an. So ermitteln Sie die URL des gehosteten Exchange-Servers:

   1. Öffnen Sie Outlook im Web für Office 365.

   2. Wählen Sie das **?** links oben und anschließend **Info** aus.

   3. Suchen Sie den Wert **Externer POP-Server**.

   4. Wählen Sie **Proxyserver** aus, um die Proxyservereinstellungen für Ihren gehosteten Exchange-Server anzugeben.
       1. Wählen Sie **Beim Synchronisieren von Informationen für mobile Geräte einen Proxyserver verwenden**aus.

       2. Geben Sie den **Proxyservernamen** und die für den Zugriff auf den Server zu verwendende **Portnummer** ein.

       3. Ist für den Zugriff auf den Proxyserver die Angabe von Benutzeranmeldeinformationen erforderlich, wählen Sie **Mithilfe von Anmeldeinformationen eine Verbindung mit dem Proxyserver herstellen** aus. Geben Sie dann **Domäne\Benutzer** und das **Kennwort** ein.

       4. Wählen Sie **OK** aus.

4. Geben Sie in den Feldern **Benutzer (Domäne\Benutzer)** und **Kennwort** die für die Verbindung mit Ihrem Exchange-Server erforderlichen Anmeldeinformationen an. Das Konto, das Sie festlegen, muss über eine Lizenz für die Verwendung von Intune verfügen. 

5. Geben Sie die zum Senden von Benachrichtigungen an das Exchange Server-Postfach eines Benutzers erforderlichen Anmeldeinformationen ein. Dieser Benutzer ist nur für Benachrichtigungen reserviert. Der Benutzer für Benachrichtigungen benötigt ein Exchange-Postfach, um Benachrichtigungen per Mail zu senden. Sie können diese Benachrichtigungen über Richtlinien für den bedingten Zugriff in Intune konfigurieren.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. Geben Sie im Feld **Kennwort** das Kennwort für dieses Konto an, damit Intune auf Exchange Server zugreifen kann.

7. Wählen Sie **Verbinden** aus.

   > [!NOTE]
   > Das Konfigurieren der Verbindung kann möglicherweise einige Minuten in Anspruch nehmen.

Bei der Konfiguration werden vom Exchange Connector Ihre Proxyeinstellungen gespeichert, um den Zugriff auf das Internet zu ermöglichen. Wenn sich Ihre Proxyeinstellungen ändern, müssen Sie den Exchange Connector neu konfigurieren, damit für ihn die aktualisierten Proxyeinstellungen verwendet werden.

Nach Einrichtung der Verbindung durch den Exchange Connector werden mobile Geräte, die von Exchange verwalteten Benutzern zugeordnet sind, automatisch synchronisiert und dem Exchange Connector hinzugefügt. Diese Synchronisation kann einige Zeit in Anspruch nehmen.

> [!NOTE]
> Wenn Sie den lokalen Exchange Connector installiert haben und zu einem späteren Zeitpunkt die Exchange-Verbindung löschen, müssen Sie den lokalen Exchange Connector von dem Computer löschen, auf dem er installiert wurde.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installieren von Connectors für mehrere Exchange-Organisationen
Intune unterstützt mehrere lokale Exchange Connectors pro Abonnement. Für einen Mandanten mit mehreren Exchange-Organisationen können Sie einen Connector für jede Exchange-Organisation einrichten, aber nur einen Connector pro Organisation. 

Wenn Sie Connectors installieren, um mehrere Exchange-Organisationen zu verbinden, laden Sie den ZIP-Ordner einmal herunter, und verwenden Sie den Ordner für jeden installierten Connector wieder. Führen Sie die Schritte aus dem vorherigen Abschnitt für jeden weiteren Connector aus, um das Setupprogramm zu extrahieren und auf einem Server in der Exchange-Organisation auszuführen.

Die Features zu Hochverfügbarkeit, Überwachung und manueller Synchronisierung, die in den folgenden Abschnitten beschrieben werden, werden für jede Exchange-Organisation unterstützt, die mit Intune verbunden wird.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Hochverfügbarkeitsunterstützung für lokalen Exchange Connector 
Wenn der Exchange-Clientzugriffsserver, den der Connector verwendet, nicht verfügbar ist, sorgt die Hochverfügbarkeit für lokale Exchange-Connectors dafür, dass der Connector einen anderen Clientzugriffsserver für die jeweilige Exchange-Organisation verwenden kann. Der Exchange-Connector selbst unterstützt die Hochverfügbarkeit nicht. Wenn der Connector ausfällt, wird kein automatisches Failover ausgeführt, und Sie müssen den Connector ersetzen, indem Sie [einen neuen Connector installieren](#reinstall-the-on-premises-exchange-connector). 

Nachdem der Connector mithilfe des angegebenen Clientzugriffsservers erfolgreich eine Verbindung mit Exchange hergestellt hat, ermittelt der Connector weitere Clientzugriffsserver für diese Exchange-Organisation, die für Failovers verwendet werden können. Mithilfe des Wissens über weitere Clientzugriffsserver kann der Connector ein Failover auf einen anderen verfügbaren Clientzugriffsserver durchführen, bis der primäre Clientzugriffsserver wieder verfügbar ist. Die Ermittlung weiterer Clientzugriffsserver ist standardmäßig aktiviert. Sie können das Failover mithilfe des folgenden Verfahrens deaktivieren:  
1. Navigieren Sie auf dem Server, auf dem der Exchange-Connector installiert ist, zu „%*ProgramData*%\Microsoft\Microsoft Intune Exchange Connector“. 
2. Öffnen Sie mit einem Text-Editor **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Um die Feature zu deaktivieren, ändern Sie &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; in &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt;.    
 

## <a name="reinstall-the-on-premises-exchange-connector"></a>Erneutes Installieren des lokalen Exchange-Connectors
Möglicherweise müssen Sie Exchange-Connector neu installieren. Da für die Herstellung einer Verbindung mit jeder Exchange-Organisation ein einzelner Connector unterstützt wird, ersetzt ein neu installierter Connector den ursprünglichen, wenn Sie versuchen einen zweiten Connector für eine Organisation zu installieren.

1. Führen Sie die Schritte unter [Installieren und Konfigurieren des lokalen Intune Exchange Connectors](#install-and-configure-the-intune-on-premises-exchange-connector) aus, um die Installation des neuen Connectors zu starten. 
2. Klicken Sie auf **Ersetzen**, wenn Sie bei der Installation des neuen Connectors dazu aufgefordert werden.  
   ![Konfigurationsaufforderung beim Ersetzen eines Connectors](./media/exchange-connector-install/prompt-to-replace.png)

3. Fahren Sie mit den Schritten aus dem vorherigen Verfahren fort, und melden Sie sich erneut bei Intune an.
4. Klicken Sie auf der letzten Anzeige auf **Schließen**, um die Installation abzuschließen.  
   ![Setup abschließen](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Überwachen der Exchange-Connectoraktivität

Nachdem Sie den Exchange-Connector erfolgreich konfiguriert haben, können Sie den Status der Verbindungen und den letzten erfolgreichen Synchronisationsversuch anzeigen. So überprüfen Sie die Verbindung des Exchange-Connectors:

1. Klicken Sie auf dem Intune-Dashboard auf **Exchange-Zugriff**.
2. Klicken Sie auf **Zugriff auf Exchange lokal**, um den Verbindungsstatus der Exchange-Connectors zu überprüfen.

Sie können auch die Uhrzeit und das Datum des letzten erfolgreichen Synchronisationsversuchs überprüfen.
--> 

### <a name="system-center-operations-manager-management-pack"></a>System Center Operations Manager Management Pack

Ab Intune-Release 1710 können Sie das [Operations Manager Management Pack für Exchange Connector und Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) verwenden. Das Management Pack bietet Ihnen verschiedene Möglichkeiten zur Überwachung des Exchange-Connectors für die Problembehandlung.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Manuelle Erzwingung einer schnellen oder vollständigen Synchronisierung
Ein lokaler Exchange Connector synchronisiert regelmäßig EAS und Datensätze für Intune-Geräte. Wenn sich der Konformitätsstatus eines Geräts verändert, aktualisiert der automatische Synchronisierungsprozess regelmäßig Datensätze, damit der Gerätezugriff entsprechend blockiert und erlaubt werden kann.

   - Die **Schnellsynchronisierung** wird regelmäßig mehrmals täglich ausgeführt. Eine Schnellsynchronisierung ruft Geräteinformationen für Benutzer ab, die über Intune-Lizenzen und bedingten Zugriff auf lokales Exchange verfügen und bei denen seit der letzten Synchronisierung Änderungen aufgetreten sind.

   - Die **vollständige Synchronisierung** wird standardmäßig einmal pro Tag durchgeführt. Eine vollständige Synchronisierung ruft Geräteinformationen für alle Benutzer ab, die über Intune-Lizenzen und bedingten Zugriff auf lokales Exchange verfügen. Eine vollständige Synchronisierung ruft ebenso die Exchange-Serverinformationen ab und stellt sicher, dass die von Intune im Azure-Portal angegebene Konfiguration auf dem Exchange-Server aktualisiert wird. 


Sie können erzwingen, dass ein Connector eine Synchronisierung ausführt, indem Sie die Optionen **Schnellsynchronisierung** oder **Vollständige Synchronisierung** auf dem Intune-Dashboard mit den folgenden Schritten verwenden:

   1. Klicken Sie auf dem Intune-Dashboard auf **Exchange-Zugriff**.
   2. Klicken Sie auf **Zugriff auf Exchange lokal**.
   3. Wählen Sie den Connector aus, den Sie synchronisieren möchten, wählen Sie anschließend **Schnellsynchronisierung** oder **Vollständige Synchronisierung** aus.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer Richtlinie für bedingten Zugriff für Exchange lokal](conditional-access-exchange-create.md)
