---
title: Exchange Connector für lokales EAS
description: Verwenden Sie den Connector, um die Kommunikation zwischen der Intune-Verwaltungskonsole und der lokalen Exchange Server-Instanz für Exchange ActiveSync-MDM zu ermöglichen.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 41ff4212-a6f5-4374-8731-631f7560cff1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f5976b76f839a973355ed2c0b157f8c72733bf64
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="install-the-intune-on-premises-exchange-connector"></a>Installieren des lokalen Exchange Connectors für Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Zum Einrichten einer Verbindung, über die Microsoft Intune mit dem Exchange-Server kommunizieren kann, auf dem die Postfächer für die mobilen Geräte gehostet werden, müssen Sie den lokalen Exchange Connector von der Intune-Administratorkonsole herunterladen und konfigurieren. Intune unterstützt pro Abonnement nur eine Exchange Connector-Verbindung eines beliebigen Typs.

## <a name="on-premises-exchange-connector-requirements"></a>Anforderungen des lokalen Exchange Connectors
In der folgenden Tabelle finden Sie die Anforderungen an den Computer, auf dem Sie den lokalen Exchange Connector installieren.


|            Anforderungen             |                                                                                                                                                                                                        Weitere Informationen                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Betriebssysteme          |                                                                          Intune unterstützt den lokalen Exchange Connector auf Computern, auf denen eine beliebige Edition von Windows Server 2008 SP2 (64 Bit), Windows Server 2008 R2, Windows Server 2012 oder Windows Server 2012 R2 ausgeführt wird.<br /><br />Auf Server Core-Installationen wird der Connector nicht unterstützt.                                                                          |
|         Microsoft Exchange         |                                                                           Für lokale Connectors ist Microsoft Exchange 2010 SP1 oder höher oder die Exchange Online Dedicated-Legacyumgebung erforderlich. Wenn Sie herausfinden möchten, ob es sich bei Ihrer Exchange Online Dedicated-Umgebung um die <strong>neue</strong> oder die <strong>ältere</strong> Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer.                                                                           |
| Autorität für die Verwaltung mobiler Geräte |                                                                                                                                                       [Festlegen von Intune als Autorität für die Verwaltung mobiler Geräte](prerequisites-for-enrollment.md#step-2-set-mdm-authority).                                                                                                                                                        |
|              Hardware              |                                                                                                                                                     Der Computer, auf dem Sie den Connector installieren, erfordert eine CPU mit 1,6 GHz und 2 GB RAM sowie mindestens 10 GB freien Speicherplatz.                                                                                                                                                      |
|  Active Directory-Synchronisierung  |                                                                             Bevor Sie einen Connector für die Verbindung von Intune mit Exchange Server verwenden können, müssen Sie die [Active Directory-Synchronisierung](/intune/users-permissions-add) einrichten, damit Ihre lokalen Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden.                                                                              |
|        Zusätzliche Software         |                                                                                                                                           Eine vollständige Installation von Microsoft .NET Framework 4.5 und Windows PowerShell 2.0 muss auf dem Computer installiert sein, auf dem der Connector gehostet wird.                                                                                                                                           |
|              Netzwerk               | Der Computer, auf dem Sie den Connector installieren, muss sich in einer Domäne befinden, die sich mit der Domäne, in der Exchange Server gehostet wird, in einer Vertrauensstellung befindet.<br /><br />Der Computer erfordert Konfigurationen, die es ihm ermöglichen, über Firewalls und Proxyserver über Port 80 und 443 auf den Intune-Dienst zuzugreifen. Von Intune verwendete Domänen sind manage.microsoft.com, &#42;manage.microsoft.com und &#42;.manage.microsoft.com. |

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

1. Öffnen Sie auf einem vom lokalen Exchange Connector unterstützten Windows Server-Betriebssystem die [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) (https://manage.microsoft.com)) mit einem Benutzerkonto, das ein Administrator im Exchange-Mandanten ist und über eine Lizenz zum Verwenden von Exchange Server verfügt.
![Öffnen und Einrichten der Exchange-Verbindung](../media/ExchangeConnector.gif)

2.  Wählen Sie im Bereich mit den Arbeitsbereichsverknüpfungen **Admin**>**Verwaltung mobiler Geräte** > **Microsoft Exchange**>**Exchange-Verbindung einrichten** aus.

3.  Wählen Sie auf der Seite **Exchange-Verbindung einrichten** die Option **Lokalen Connector herunterladen** aus.

4.  Der lokale Exchange Connector ist in einem komprimierten Ordner (ZIP-Archiv) enthalten, der geöffnet oder gespeichert werden kann. Wählen Sie im Dialogfeld **Dateidownload** die Option **Speichern** aus, um den komprimierten Ordner an einem sicheren Speicherort zu speichern.

> [!IMPORTANT]
> Die Dateien im Ordner des lokalen Exchange Connectors dürfen nicht umbenannt oder verschoben werden. Bei Verschieben oder Umbenennen der Inhalte des Ordners ist die Installation nicht mehr funktionsfähig.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installieren und Konfigurieren des lokalen Exchange Connectors für Intune
Führen Sie die folgenden Schritte aus, um den lokalen Exchange Connector für Intune zu installieren. Der lokale Connector kann nur einmal pro Intune-Abonnement und nur auf einem Computer installiert werden. Wenn Sie versuchen, einen weiteren lokalen Exchange Connector zu konfigurieren, wird die ursprüngliche Verbindung durch die neue ersetzt.

1. Extrahieren Sie unter einem für den lokalen Connector unterstützten Betriebssystem die Dateien in **Exchange_Connector_Setup.zip** an einen sicheren Speicherort.

2. Nachdem die Dateien extrahiert wurden, öffnen Sie den extrahierten Ordner, und doppelklicken Sie auf **Exchange_Connector_Setup.exe**, um den lokalen Exchange Connector zu installieren.

   > [!IMPORTANT]
   > Wenn der Speicherort nicht sicher ist, sollten Sie die Zertifikatdatei **WindowsIntune.accountcert** nach der Installation des lokalen Connectors unbedingt löschen.

3. Wählen Sie im Dialogfeld **Microsoft Intune Exchange Connector** entweder **Lokaler Microsoft Exchange-Server** oder **Gehosteter Microsoft Exchange-Server** aus.

   ![Wählen des Exchange-Servertyps](../media/IntuneSA1dconfigureExchConnector.png)

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

   6.  Geben Sie die zum Senden von Benachrichtigungen an das Exchange Server-Postfach des Benutzers erforderlichen administrativen Anmeldeinformationen ein. Sie können diese Benachrichtigungen über Richtlinien für den bedingten Zugriff in Intune konfigurieren.

       Stellen Sie sicher, dass die AutoErmittlungs- und Exchange-Webdienste auf dem Exchange-Clientzugriffsserver konfiguriert sind. Weitere Informationen finden Sie unter [Clientzugriffsserver](https://technet.microsoft.com/library/dd298114.aspx).

   7.  Geben Sie im Feld **Kennwort** das Kennwort für dieses Konto an, damit Intune auf Exchange Server zugreifen kann.

   8. Wählen Sie **Verbinden** aus.

Das Konfigurieren der Verbindung kann möglicherweise einige Minuten in Anspruch nehmen.

Bei der Konfiguration werden vom Exchange-Connector Ihre Proxyeinstellungen gespeichert, um den Zugriff auf das Internet zu ermöglichen. Wenn sich Ihre Proxyeinstellungen ändern, müssen Sie den Exchange Connector neu konfigurieren, damit für ihn die aktualisierten Proxyeinstellungen verwendet werden.

Nach Einrichtung der Verbindung durch den Exchange Connector werden mobile Geräte, die vom Exchange Connector verwalteten Benutzern zugeordnet sind, automatisch synchronisiert und dem Exchange Connector hinzugefügt. Diese Synchronisation kann einige Zeit in Anspruch nehmen.

> [!NOTE]
> Wenn Sie den lokalen Exchange Connector installiert haben und zu einem späteren Zeitpunkt die Exchange-Verbindung löschen, müssen Sie den lokalen Exchange Connector von dem Computer löschen, auf dem er installiert wurde.

## <a name="validate-the-exchange-connection"></a>Überprüfen der Exchange-Verbindung

Nachdem Sie den Exchange-Connector erfolgreich konfiguriert haben, können Sie den Status der Verbindung und den letzten erfolgreichen Synchronisationsversuch anzeigen. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) den Arbeitsbereich **ADMIN** aus. Wählen Sie unter **Verwaltung mobiler Geräte** die Option **Microsoft Exchange** aus, und überprüfen Sie die unter **Exchange-Verbindungsinformationen** angezeigten Details.


Sie können auch die Uhrzeit und das Datum des letzten erfolgreichen Synchronisationsversuchs überprüfen.
