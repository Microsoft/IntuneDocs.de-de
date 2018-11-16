---
title: Einrichten des lokalen Microsoft Intune Exchange Connector
titleSuffix: ''
description: Verwenden Sie den lokalen Exchange Connector, um den Zugriff der Geräte auf Exchange-Postfächer basierend auf der Intune-Registrierung und Exchange Active Sync (EAS) zu verwalten.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c24630dd3cc45b35e6313e9e66db74a548bb0851
ms.sourcegitcommit: cfce9318b5b5a3005929be6eab632038a12379c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51298104"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Einrichten des lokalen Intune Exchange Connectors in Microsoft Intune in Azure

In einer lokalen Exchange Server-Umgebung kann der bedingte Zugriff für Intune verwendet werden, um Zugriff auf lokale Exchange-Postfächer zu erlauben oder zu blockieren. Verwenden Sie lokale Exchange Active Sync-Connectors, um Intune mit Ihren Exchange-Organisationen zu verbinden und um den bedingten Zugriff für Intune zusammen mit Richtlinien für die Gerätekonformität einzurichten. Wenn dann ein Gerät versucht, eine Verbindung mit Exchange herzustellen, bestimmt Intune, ob das Gerät in Intune registriert wird und konform ist. Um zu bestimmen, welche Geräte in Intune registriert werden können, ordnet der lokale Exchange Connector die Exchange Active Sync-Datensätze (EAS) in Exchange Server den Intune-Datensätzen zu. Weitere Informationen zu dieser Vorgehensweise finden Sie unter [Welche gängigen Möglichkeiten gibt es für die Verwendung des bedingten Zugriffs in Intune?](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune unterstützt jetzt mehrere lokale Exchange Connectors pro Abonnement. Wenn Sie über mehr als eine lokale Exchange-Organisation verfügen, können Sie einen separaten Connector für jede Exchange-Organisation einrichten.

Folgende Schritte helfen Ihnen, eine Verbindung einzurichten, die Microsoft Intune die Kommunikation mit der lokalen Exchange Server-Instanz ermöglicht:

1.  Laden Sie den lokalen Intune Exchange Connector aus dem Azure-Portal herunter.
2.  Installieren und konfigurieren Sie den Exchange Connector auf einem Computer in der lokalen Exchange-Organisation.
3.  Überprüfen Sie die Exchange-Verbindung.
4. Wiederholen Sie diese Schritte für jede Exchange-Organisation, die Sie mit Intune verbinden möchten.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Anforderungen des lokalen Intune Exchange Connectors
In der folgenden Tabelle finden Sie die Anforderungen an den Computer, auf dem Sie den lokalen Exchange Connector installieren.


|            Anforderungen             |                                                                                                                                                                                                        Weitere Informationen                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Betriebssysteme          |                                                               Intune unterstützt den lokalen Exchange Connector auf Computern, auf denen eine beliebige Edition von Windows Server 2008 SP2 (64 Bit), Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 oder Windows Server 2016 ausgeführt wird.<br /><br />Auf Server Core-Installationen wird der Connector nicht unterstützt.                                                                |
|         Microsoft Exchange         |                                                                           Für lokale Connectors sind Microsoft Exchange 2010 SP3 oder höher oder die veraltete Exchange Online Dedicated-Umgebung erforderlich. Wenn Sie herausfinden möchten, ob es sich bei Ihrer Exchange Online Dedicated-Umgebung um die <strong>neue</strong> oder die <strong>ältere</strong> Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer.                                                                           |
| Autorität für die Verwaltung mobiler Geräte |                                                                                                                              [Festlegen von Intune als Autorität für die Verwaltung mobiler Geräte](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).                                                                                                                               |
|              Hardware              |                                                                                                                                                     Der Computer, auf dem Sie den Connector installieren, erfordert eine CPU mit 1,6 GHz und 2 GB RAM sowie mindestens 10 GB freien Speicherplatz.                                                                                                                                                      |
|  Active Directory-Synchronisierung  |                                                                                      Bevor Sie den Connector für die Verbindung von Intune mit Exchange Server verwenden können, müssen Sie die [Active Directory-Synchronisierung](users-add.md) einrichten, damit Ihre lokalen Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden.                                                                                      |
|        Zusätzliche Software         |                                                                                                                                           Eine vollständige Installation von Microsoft .NET Framework 4.5 und Windows PowerShell 2.0 muss auf dem Computer installiert sein, auf dem der Connector gehostet wird.                                                                                                                                           |
|              Netzwerk               | Der Computer, auf dem Sie den Connector installieren, muss sich in einer Domäne befinden, die sich mit der Domäne, in der Exchange Server gehostet wird, in einer Vertrauensstellung befindet.<br /><br />Der Computer erfordert Konfigurationen, die es ihm ermöglichen, über Firewalls und Proxyserver über Port 80 und 443 auf den Intune-Dienst zuzugreifen. Von Intune verwendete Domänen sind manage.microsoft.com, &#42;manage.microsoft.com und &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Anforderungen an Exchange-Cmdlets

Sie müssen in Active Directory ein Benutzerkonto erstellen, das vom lokalen Exchange Connector verwendet wird. Das Konto muss über die Berechtigung zum Ausführen der folgenden erforderlichen Windows PowerShell-Exchange-Cmdlets verfügen:


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

1. Öffnen Sie auf einem vom lokalen Exchange Connector unterstützten Windows Server-Betriebssystem das [Azure-Portal](http://portal.azure.com) mit einem Administratorkonto in der lokalen Exchange Server-Instanz, für das eine Exchange Server-Lizenz vorhanden ist.

2. Klicken Sie im Menü links auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune** aus. Wenn das Intune-Dashboard geöffnet wird, wählen Sie **Lokaler Zugriff** aus.

4. Klicken Sie unter **Setup** auf **Exchange ActiveSync-Connector** und dann auf **Download the on-premises connector** (Lokalen Connector herunterladen).

5.  Der lokale Exchange Connector ist in einem komprimierten Ordner (ZIP-Archiv) enthalten, der geöffnet oder gespeichert werden kann. Wählen Sie im Dialogfeld **Dateidownload** die Option **Speichern** aus, um den komprimierten Ordner an einem sicheren Speicherort zu speichern.

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

   5. Geben Sie in den Feldern **Benutzer (Domäne\Benutzer)** und **Kennwort** die für die Verbindung mit Ihrem Exchange-Server erforderlichen Anmeldeinformationen an.

   6.  Geben Sie die zum Senden von Benachrichtigungen an das Exchange Server-Postfach eines Benutzers erforderlichen Anmeldeinformationen ein. Dieser Benutzer ist nur für Benachrichtigungen reserviert. Der Benutzer für Benachrichtigungen benötigt ein Exchange-Postfach, um Benachrichtigungen per Mail senden zu können. Sie können diese Benachrichtigungen über Richtlinien für den bedingten Zugriff in Intune konfigurieren.  

       Stellen Sie sicher, dass die AutoErmittlungs- und Exchange-Webdienste auf dem Exchange-Clientzugriffsserver konfiguriert sind. Weitere Informationen finden Sie unter [Clientzugriffsserver](https://technet.microsoft.com/library/dd298114.aspx).

   7.  Geben Sie im Feld **Kennwort** das Kennwort für dieses Konto an, damit Intune auf Exchange Server zugreifen kann.

   8. Wählen Sie **Verbinden** aus.

   > [!NOTE]
   > Das Konfigurieren der Verbindung kann möglicherweise einige Minuten in Anspruch nehmen.

Bei der Konfiguration werden vom Exchange Connector Ihre Proxyeinstellungen gespeichert, um den Zugriff auf das Internet zu ermöglichen. Wenn sich Ihre Proxyeinstellungen ändern, müssen Sie den Exchange Connector neu konfigurieren, damit für ihn die aktualisierten Proxyeinstellungen verwendet werden.

Nach Einrichtung der Verbindung durch den Exchange Connector werden mobile Geräte, die von Exchange verwalteten Benutzern zugeordnet sind, automatisch synchronisiert und dem Exchange Connector hinzugefügt. Diese Synchronisation kann einige Zeit in Anspruch nehmen.

> [!NOTE]
> Wenn Sie den lokalen Exchange Connector installiert haben und zu einem späteren Zeitpunkt die Exchange-Verbindung löschen, müssen Sie den lokalen Exchange Connector von dem Computer löschen, auf dem er installiert wurde.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installieren von Connectors für mehrere Exchange-Organisationen
Intune unterstützt mehrere lokale Exchange Connectors pro Abonnement. Für einen Mandanten mit mehreren Exchange-Organisationen können Sie einen Connector für jede Exchange-Organisation einrichten. Laden Sie den ZIP-Ordner einmal herunter, und befolgen Sie dann für jede Exchange-Organisation die Schritte im vorherigen Abschnitt, um das Setupprogramm auf einem Server in der Organisation zu extrahieren und auszuführen.

Die Features zu Hochverfügbarkeit, Überwachung und manueller Synchronisierung, die in den folgenden Abschnitten beschrieben werden, werden für jede Exchange-Organisation unterstützt, die mit Intune verbunden ist.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Hochverfügbarkeitsunterstützung für lokalen Exchange Connector 
Nachdem der Exchange Connector über den angegebenen CAS eine Verbindung mit Exchange hergestellt hat, kann der Connector andere CAS erkennen. Wenn der primäre CAS nicht mehr verfügbar ist, wird für den Connector ggf. ein Failover auf einen anderen CAS durchgeführt, bis der primäre CAS verfügbar wird. Dieses Feature ist standardmäßig aktiviert. Sie können diese Feature mithilfe des folgenden Verfahrens deaktivieren:
1. Navigieren Sie auf dem Server, auf dem der Exchange Connector installiert ist, zu „%*ProgramData*%\Microsoft\Microsoft Intune Exchange Connector“. 
2. Öffnen Sie mit einem Text-Editor **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Um die Feature zu deaktivieren, ändern Sie &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; in &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt;.    


## <a name="monitor-the-exchange-connector-activity"></a>Überwachen der Exchange-Connectoraktivität

Nachdem Sie Exchange Connectors erfolgreich konfiguriert haben, können Sie den Status der Verbindung und den letzten erfolgreichen Synchronisierungsversuch anzeigen. So überprüfen Sie die Exchange Connector-Verbindung:

1. Wählen Sie auf dem Intune-Dashboard **Lokaler Zugriff** aus.
2. Wählen Sie unter **Setup** **Exchange ActiveSync-Connectors** aus, um den Verbindungsstatus für jeden Exchange Connector zu überprüfen.

Sie können auch die Uhrzeit und das Datum des letzten erfolgreichen Synchronisationsversuchs überprüfen.

### <a name="system-center-operations-manager-scom-management-pack"></a>System Center Operations Manager (SCOM) Management Pack

Ab der Intune-Version 1710 können Sie das [SCOM Management Pack für Exchange-Connector und Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) verwenden. Es bietet Ihnen verschiedene Möglichkeiten zur Überwachung des Exchange-Connectors bei der Problembehandlung.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Manuelle Erzwingung einer schnellen oder vollständigen Synchronisierung
Ein lokaler Exchange Connector synchronisiert regelmäßig automatisch EAS und Datensätze für Intune-Geräte. Wenn sich der Konformitätsstatus eines Geräts verändert, aktualisiert der automatische Synchronisierungsprozess regelmäßig Datensätze, damit der Gerätezugriff entsprechend blockiert und erlaubt werden kann.

   - Die **Schnellsynchronisierung** wird regelmäßig mehrmals täglich ausgeführt. Eine schnelle Synchronisierung ruft Geräteinformationen für die Benutzer ab, die über Intune-Lizenzen und bedingten Zugriff mit lokalem Exchange verfügen, die sich seit der letzten Synchronisierung geändert haben.

   - Die **vollständige Synchronisierung** wird standardmäßig einmal pro Tag durchgeführt. Eine vollständige Synchronisierung ruft Geräteinformationen für alle Benutzer ab, die über Intune-Lizenzen und bedingten Zugriff mit lokalem Exchange verfügen. Eine vollständige Synchronisierung ruft ebenso die Exchange-Serverinformationen ab und stellt sicher, dass die von Intune im Azure-Portal angegebene Konfiguration auf dem Exchange-Server aktualisiert wird. 

Sie können erzwingen, dass ein Connector eine Synchronisierung ausführt, indem Sie die Optionen **Schnellsynchronisierung** oder **Vollständige Synchronisierung** auf dem Intune-Dashboard mit den folgenden Schritten verwenden:

   1. Wählen Sie auf dem Intune-Dashboard **Lokaler Zugriff** aus.
   2. Wählen Sie unter **Setup** die Option **Exchange Active Sync-Connectors** aus.
   3. Wählen Sie den Connector aus, den Sie synchronisieren möchten, wählen Sie anschließend **Schnellsynchronisierung** oder **Vollständige Synchronisierung** aus.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer Richtlinie für bedingten Zugriff für lokales Exchange](conditional-access-exchange-create.md)
