---
title: Einrichten des lokalen Microsoft Intune Exchange Connector
titleSuffix: 
description: "Verwenden Sie den lokalen Exchange Connector, um den Zugriff der Geräte auf Exchange-Postfächer basierend auf der Intune-Registrierung und Exchange Active Sync (EAS) zu verwalten."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0caea2e8b7704fe2dfcbec937b59000ac2a12ae5
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Einrichten des lokalen Intune Exchange Connectors in Microsoft Intune in Azure

Lokale Exchange Server-Umgebungen können den lokalen Intune Exchange Connector zum Verwalten des Gerätezugriffs auf lokale Exchange-Postfächer abhängig davon nutzen, ob die Geräte bei Intune registriert und mit Intune-Richtlinien zur Gerätekonformität konform sind. Der lokale Exchange Connector ist auch für die Ermittlung mobiler Geräte zuständig, die sich mit lokalen Exchange Server-Instanzen verbinden, indem der vorhandene EAS-Datensatz (Exchange Active Sync) mit Intune synchronisiert wird.

> [!IMPORTANT]
> Intune unterstützt pro Abonnement nur eine lokale Exchange Connector-Verbindung eines beliebigen Typs.

Um eine Verbindung einzurichten, die Microsoft Intune die Kommunikation mit der lokalen Exchange Server-Instanz ermöglicht, müssen Sie die folgenden Schritte ausführen:

1.  Laden Sie den lokalen Intune Exchange Connector aus dem Azure-Portal herunter.
2.  Installieren und konfigurieren Sie den lokalen Intune Exchange Connector.
3.  Überprüfen Sie die Exchange-Verbindung.

## <a name="on-premises-exchange-connector-requirements"></a>Anforderungen des lokalen Exchange Connectors
In der folgenden Tabelle finden Sie die Anforderungen an den Computer, auf dem Sie den lokalen Exchange Connector installieren.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Betriebssysteme|Intune unterstützt den lokalen Exchange Connector auf Computern, auf denen eine beliebige Edition von Windows Server 2008 SP2 (64 Bit), Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 oder Windows Server 2016 ausgeführt wird.<br /><br />Auf Server Core-Installationen wird der Connector nicht unterstützt.|
|Microsoft Exchange|Für lokale Connectors ist Microsoft Exchange 2010 SP1 oder höher oder die Exchange Online Dedicated-Legacyumgebung erforderlich. Wenn Sie herausfinden möchten, ob es sich bei Ihrer Exchange Online Dedicated-Umgebung um die **neue** oder die **ältere** Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer.|
|Autorität für die Verwaltung mobiler Geräte| [Festlegen von Intune als Autorität für die Verwaltung mobiler Geräte](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).|
|Hardware|Der Computer, auf dem Sie den Connector installieren, erfordert eine CPU mit 1,6 GHz und 2 GB RAM sowie mindestens 10 GB freien Speicherplatz.|users-add.md
|Active Directory-Synchronisierung|Bevor Sie einen Connector für die Verbindung von Intune mit Exchange Server verwenden können, müssen Sie die [Active Directory-Synchronisierung](users-add.md) einrichten, damit Ihre lokalen Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden.|
|Zusätzliche Software|Eine vollständige Installation von Microsoft .NET Framework 4.5 und Windows PowerShell 2.0 muss auf dem Computer installiert sein, auf dem der Connector gehostet wird.|
|Netzwerk|Der Computer, auf dem Sie den Connector installieren, muss sich in einer Domäne befinden, die sich mit der Domäne, in der Exchange Server gehostet wird, in einer Vertrauensstellung befindet.<br /><br />Der Computer erfordert Konfigurationen, die es ihm ermöglichen, über Firewalls und Proxyserver über Port 80 und 443 auf den Intune-Dienst zuzugreifen. Von Intune verwendete Domänen sind manage.microsoft.com, &#42;manage.microsoft.com und &#42;.manage.microsoft.com.|


### <a name="exchange-cmdlet-requirements"></a>Anforderungen an Exchange-Cmdlets

Sie müssen in Active Directory ein Benutzerkonto erstellen, das vom Intune Exchange Connector verwendet wird. Das Konto muss über die Berechtigung zum Ausführen der folgenden erforderlichen Windows PowerShell-Exchange-Cmdlets verfügen:


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

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Herunterladen des Softwareinstallationspaket für den lokalen Exchange Connector

1. Öffnen Sie auf einem vom lokalen Exchange Connector unterstützten Windows Server-Betriebssystem das [Azure-Portal](http://portal.azure.com) mit einem Benutzerkonto, das ein Administrator in der lokalen Exchange Server-Instanz ist und über eine Exchange Server-Lizenz verfügt.

2. Klicken Sie im Menü links auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune** aus. Das Intune-Dashboard wird geöffnet, auf dem Sie **Lokaler Zugriff** auswählen.

4. Klicken Sie auf **Exchange ActiveSync-Connector** und dann auf **Download the on-premises connector** (Lokalen Connector herunterladen).

5.  Der lokale Exchange Connector ist in einem komprimierten Ordner (ZIP-Archiv) enthalten, der geöffnet oder gespeichert werden kann. Wählen Sie im Dialogfeld **Dateidownload** die Option **Speichern** aus, um den komprimierten Ordner an einem sicheren Speicherort zu speichern.

    > [!IMPORTANT]
    > Die Dateien im Ordner des lokalen Exchange Connectors dürfen nicht umbenannt oder verschoben werden. Bei Verschieben oder Umbenennen der Inhalte des Ordners ist die Exchange Connector-Installation nicht mehr funktionsfähig.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installieren und Konfigurieren des lokalen Exchange Connectors für Intune
Führen Sie die folgenden Schritte aus, um den lokalen Exchange Connector für Intune zu installieren. Der lokale Connector kann nur einmal pro Intune-Abonnement und nur auf einem Computer installiert werden. Wenn Sie versuchen, einen weiteren lokalen Exchange Connector zu konfigurieren, wird die ursprüngliche Verbindung durch die neue ersetzt.

1.  Extrahieren Sie unter einem für den lokalen Connector unterstützten Betriebssystem die Dateien in **Exchange_Connector_Setup.zip** an einen sicheren Speicherort.

2.  Nachdem die Dateien extrahiert wurden, öffnen Sie den extrahierten Ordner, und doppelklicken Sie auf **Exchange_Connector_Setup.exe**, um den lokalen Exchange Connector zu installieren.

    > [!IMPORTANT]
    > Wenn der Speicherort nicht sicher ist, sollten Sie die Zertifikatdatei **WindowsIntune.accountcert** nach der Installation des lokalen Connectors unbedingt löschen.

3.  Wählen Sie im Dialogfeld **Microsoft Intune Exchange Connector** entweder **Lokaler Microsoft Exchange-Server** oder **Gehosteter Microsoft Exchange-Server** aus.

  ![Abbildung, die darstellt, wo der Exchange Server-Typ ausgewählt wird](./media/intune-sa-exchange-connector-config.png)

  Geben Sie bei einem lokalen Exchange-Server entweder den Servernamen oder den vollqualifizierten Domänennamen des Exchange-Servers an, auf dem die Rolle **Clientzugriffsserver** gehostet wird.

  Bei einem gehosteten Exchange-Server geben Sie die Adresse des Exchange-Servers an. So ermitteln Sie die URL des gehosteten Exchange-Servers:

    1. Öffnen Sie die Outlook Web-App für Office 365.

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

Bei der Konfiguration werden vom Exchange-Connector Ihre Proxyeinstellungen gespeichert, um den Zugriff auf das Internet zu ermöglichen. Wenn sich Ihre Proxyeinstellungen ändern, müssen Sie den Exchange Connector neu konfigurieren, damit für ihn die aktualisierten Proxyeinstellungen verwendet werden.

Nach Einrichtung der Verbindung durch den Exchange Connector werden mobile Geräte, die vom Exchange Connector verwalteten Benutzern zugeordnet sind, automatisch synchronisiert und dem Exchange Connector hinzugefügt. Diese Synchronisation kann einige Zeit in Anspruch nehmen.

> [!NOTE]
> Wenn Sie den lokalen Exchange Connector installiert haben und zu einem späteren Zeitpunkt die Exchange-Verbindung löschen, müssen Sie den lokalen Exchange Connector von dem Computer löschen, auf dem er installiert wurde.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Hochverfügbarkeitsunterstützung für lokalen Exchange Connector 
Nachdem der Exchange Connector über den angegebenen CAS eine Verbindung mit Exchange hergestellt hat, kann der Connector andere CAS erkennen. Wenn der primäre CAS nicht mehr verfügbar ist, wird für den Connector ggf. ein Failover auf einen anderen CAS durchgeführt, bis der primäre CAS verfügbar wird. Dieses Feature ist standardmäßig aktiviert. Sie können diese Feature mithilfe des folgenden Verfahrens deaktivieren:
1. Navigieren Sie auf dem Server, auf dem der Exchange Connector installiert ist, zu „%*ProgramData*%\Microsoft\Microsoft Intune Exchange Connector“. 
2. Öffnen Sie mit einem Text-Editor **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Um die Feature zu deaktivieren, ändern Sie &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; in &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt;.    


## <a name="monitor-the-exchange-connector-activity"></a>Überwachen der Exchange-Connectoraktivität

Nachdem Sie den Exchange-Connector erfolgreich konfiguriert haben, können Sie den Status der Verbindung und den letzten erfolgreichen Synchronisationsversuch anzeigen. So überprüfen Sie die Exchange Connector-Verbindung

1. Wählen Sie auf dem Intune-Dashboard **Lokaler Zugriff** aus.
2. Wählen Sie unter **Verwalten** die Option **Lokaler Exchange-Zugriff** zum Überprüfen des Verbindungsstatus aus.

Sie können auch die Uhrzeit und das Datum des letzten erfolgreichen Synchronisationsversuchs überprüfen.

### <a name="system-center-operations-manager-scom-management-pack"></a>System Center Operations Manager (SCOM) Management Pack

Ab der Intune-Version 1710 können Sie das [SCOM Management Pack für Exchange-Connector und Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True) verwenden. Es bietet Ihnen verschiedene Möglichkeiten zur Überwachung des Exchange-Connectors bei der Problembehandlung.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer Richtlinie für bedingten Zugriff für lokales Exchange](conditional-access-exchange-create.md)
