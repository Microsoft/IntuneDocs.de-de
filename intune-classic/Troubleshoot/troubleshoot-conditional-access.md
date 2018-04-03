---
title: Problembehandlung beim bedingten Zugriff
description: Was zu tun ist, wenn Ihre Benutzer durch bedingten Intune-Zugriff nicht auf Ressourcen zugreifen können.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/24/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 67a2891e4c7a6adcd7bd132c5663c9a78426ea07
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-conditional-access"></a>Problembehandlung beim bedingten Zugriff

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In der Regel versucht ein Benutzer, auf E-Mail oder SharePoint zuzugreifen, und wird zur Registrierung aufgefordert. Diese Aufforderung führt den Benutzer zum Unternehmensportal.

In diesem Thema wird beschrieben, was zu tun ist, wenn Ihre Benutzer durch bedingten Intune-Zugriff nicht auf Ressourcen zugreifen können.


## <a name="the-basics-for-success-in-conditional-access"></a>Die Grundlagen für den erfolgreichen bedingten Zugriff

Sie müssen folgende Bedingungen erfüllen, damit der bedingte Zugriff funktioniert:

-   Das Gerät muss von Intune verwaltet werden.
-   Das Gerät muss bei Azure Active Directory (AAD) registriert sein. Unter normalen Umständen erfolgt diese Registrierung automatisch während der Intune-Registrierung.
-   Das Gerät muss mit Ihren Intune-Kompatibilitätsrichtlinien für das Gerät und für den Benutzer des Geräts kompatibel sein.  Wenn keine Kompatibilitätsrichtlinien vorhanden sind, ist die Intune-Registrierung ausreichend.
-   Exchange ActiveSync muss auf dem Gerät aktiviert werden, wenn der Benutzer E-Mails über den nativen E-Mail-Client des Geräts anstatt über Outlook empfängt.     Dies geschieht für iOS,Windows Phone-und Android-/KNOX-Standard-Geräte automatisch.
-   Ihr Intune Exchange Connector muss ordnungsgemäß konfiguriert sein. Weitere Informationen finden Sie unter [Problembehandlung für den Exchange Connector in Microsoft Intune](troubleshoot-exchange-connector.md).

Diese Bedingungen können für jedes Gerät im Azure-Verwaltungsportal und im Geräteinventurbericht angezeigt werden.

## <a name="enrollment-issues"></a>Probleme bei der Registrierung

 -  Das Gerät ist nicht registriert, somit wird das Problem durch die Registrierung gelöst.
 -  Der Benutzer hat das Gerät registriert, bei der Arbeitsplatzeinbindung ist jedoch ein Fehler aufgetreten. Der Benutzer sollte die Registrierung über das Unternehmensportal aktualisieren.

## <a name="compliance-issues"></a>Kompatibilitätsprobleme

 -  Das Gerät ist mit der Intune-Richtlinie nicht kompatibel. Häufige Probleme sind Verschlüsselungs- und Kennwortanforderungen. Der Benutzer wird auf das Unternehmensportal umgeleitet, wo er sein Gerät dahingehend konfigurieren kann, dass es kompatibel ist.
 -  Die Registrierung der Konformitätsinformationen für ein Gerät kann einige Zeit in Anspruch nehmen. Warten Sie einige Minuten, und versuchen Sie es erneut.
 -  Geräte unter iOS:
     -   Ein vom Benutzer erstelltes, vorhandenes E-Mail-Profil blockiert die Bereitstellung eines Profils, das vom Intune-Administrator erstellt wurde. Das ist ein häufig auftretendes Problem, da iOS-Benutzer in der Regel ein E-Mail-Profil erstellen und anschließend die Registrierung vornehmen. Das Unternehmensportal informiert den Benutzer darüber, dass es aufgrund seines manuell konfigurierten E-Mail-Profils nicht kompatibel ist, und fordert ihn dazu auf, dieses Profil zu entfernen. Der Benutzer sollte sein E-Mail-Profil entfernen, damit das Intune-Profil bereitgestellt werden kann. Weisen Sie Ihre Benutzer an, die Registrierung ohne das Installieren eines E-Mail-Profils vorzunehmen und Intune die Bereitstellung des Profils zu erlauben, um das Problem zu vermeiden.
     -   Ein iOS-Gerät kann beim Überprüfen der Kompatibilität hängen bleiben, wodurch verhindert wird, dass der Benutzer einen weiteren Eincheckvorgang initiiert. Dieses Problem kann durch einen Neustart des Unternehmensportals behoben werden und der Kompatibilitätsstatus spiegelt den Gerätestatus in Intune wider. Nachdem alle Daten von einer Gerätesynchronisierung erfasst wurden, erfolgt die Kompatibilitätsprüfung sehr schnell und sie benötigt im Durchschnitt weniger als eine halbe Sekunde.

        In der Regel verbleiben Geräte in diesem Zustand, weil sie Probleme beim Herstellen einer Verbindung mit dem Dienst haben oder die Synchronisierung lange dauert.  Tritt das Problem für verschiedene Netzwerkkonfigurationen (Mobilfunk, WLAN, VPN), nach Geräteneustarts und nach der Überprüfung, dass der SSP auf dem Gerät aktuell ist, weiterhin auf, wenden Sie sich gemäß der Beschreibung in [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) an den Microsoft-Support.

 - Für Android-Geräte:
    - Bestimmte Android-Geräte mögen verschlüsselt zu sein scheinen, aber die Unternehmensportal-App erkennt diese Geräte als nicht verschlüsselt. 
    
        -   Für Geräte in diesem Status muss der Benutzer eine sichere Startkennung festlegen. Für den Benutzer erscheint eine Benachrichtigung über die Geräte von der Unternehmensportal-App, die ihn auffordert, eine Startkennung für das Gerät festzulegen. Tippen Sie auf die Benachrichtigung über die Geräte und bestätigen Sie die vorhandene PIN oder das Kennwort, und wählen Sie dann auf dem Bildschirm **Secure start-up** (Sicherer Start) die Option **Require PIN to start device** (PIN für Start des Geräts anfordern). Tippen Sie dann auf die Schaltfläche **Check Compliance** (Kompatibilität prüfen) für das Gerät aus der Unternehmensportal-App. Das Gerät sollte nun als verschlüsselt erkannt werden.
    
        -   Einige Gerätehersteller verschlüsseln ihre Geräte mithilfe einer Standard-PIN anstelle der geheimen PIN, die vom Benutzer festgelegt wird. Intune erkennt die Verschlüsselung über die Standard-PIN als unsicher, da diese Methode der Verschlüsselung die Daten auf dem Gerät durch böswillige Benutzer mit physischem Zugriff auf das Gerät gefährden kann. Wenn dies das Problem ist, ziehen Sie die [App-Schutzrichtlinien](/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies) in Betracht.

## <a name="policy-issues"></a>Probleme mit Richtlinien

Wenn Sie eine Kompatibilitätsrichtlinie erstellen und mit einer E-Mail-Richtlinie verknüpfen, müssen beide Richtlinien für denselben Benutzer bereitgestellt werden. Gehen Sie daher bei der Planung der Bereitstellung der verschiedenen Richtlinien für die verschiedenen Gruppen sorgfältig vor. Benutzer, die nur eine Richtlinie angewendet haben, werden wahrscheinlich feststellen, dass ihre Geräte nicht kompatibel sind.


## <a name="exchange-activesync-issues"></a>Exchange ActiveSync-Probleme

### <a name="compliant-android-device-gets-quarantine-notice"></a>Kompatibles Android-Gerät erhält Quarantänehinweis
- Bei einem Android-Gerät, das registriert und kompatibel ist, kann dennoch ein Quarantänehinweis erscheinen, wenn versucht wird, auf Unternehmensressourcen zuzugreifen. Bevor sie den Link **Starten** auswählen, sollte sich der Benutzer vergewissern, dass das Unternehmensportal nicht offen war, als er versuchte, auf die Ressourcen zuzugreifen. Der Benutzer sollte das Unternehmensportal schließen, erneut versuchen, auf die Ressourcen zuzugreifen, und anschließend den Link **Starten** auswählen.

### <a name="retired-device-continues-to-have-access"></a>Abgekoppeltes Gerät hat weiterhin Zugriff.
- Ein abgekoppeltes Gerät hat bei der Verwendung von Exchange Online nach der Abkopplung möglicherweise noch für mehrere Stunden Zugriff. Dies liegt daran, dass Exchange die Zugriffsrechte 6 Stunden lang zwischenspeichert. Ziehen Sie in diesem Szenario andere Möglichkeiten zum Datenschutz auf abgekoppelten Geräten in Betracht.

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>Gerät ist kompatibel und bei AAD registriert, aber wird weiterhin blockiert
- In manchen Fällen kann sich die Bereitstellung der Exchange ActiveSync-ID (EASID) für AAD verzögern. Eine häufige Ursache für dieses Problem ist die Drosselung. Warten Sie daher einige Minuten, und versuchen Sie es erneut.

### <a name="device-blocked"></a>Gerät blockiert

Der bedingte Zugriff ist für ein Gerät möglicherweise blockiert, ohne eine E-Mail zur Aktivierung zu erhalten.

- Gibt es eine Exchange-Standardregel, über die Geräte in Quarantäne gestellt oder blockiert werden? Wenn eine Standardregel Geräte blockiert oder in Quarantäne stellt, können die Geräte die E-Mail zur Aktivierung vom Exchange Connector nicht empfangen. Dieser Fehler ist entwurfsbedingt.
- Ist das Benachrichtigungskonto gemäß der Beschreibung in der Standardkonfiguration ordnungsgemäß konfiguriert?
- Ist das Gerät in der Intune-Verwaltungskonsole als Exchange ActiveSync-Gerät verfügbar? Ist dies nicht der Fall, ist es wahrscheinlich, dass bei der Geräteermittlung ein Fehler aufgetreten ist, da voraussichtlich ein Exchange Connector-Synchronisierungsproblem aufgetreten ist. Weitere Informationen finden Sie unter „Exchange ActiveSync-Gerät wurde von Exchange nicht erkannt“.
- Überprüfen Sie die Exchange Connector-Protokolle für die Sendemail-Aktivität, und suchen Sie nach Fehlern. Ein Beispiel für den zu suchenden Befehl ist „SendEmail from notification account to useremail“.
- Bevor das Gerät vom Exchange Connector blockiert wird, sendet er die Aktivierungs-E-Mail. Wenn das Gerät offline ist, erhält es die Aktivierungs-E-Mail möglicherweise nicht. Überprüfen Sie, ob für den E-Mail-Client des Geräts der E-Mail-Abruf per Push (anstelle von „Abrufen“) aktiviert ist, da der Benutzer dadurch ebenfalls die E-Mail verpassen könnte. Wechseln Sie zu „Abrufen“ und überprüfen Sie, ob das Gerät die E-Mail empfängt.

## <a name="noncompliant-device-not-blocked"></a>Nicht kompatibles Gerät wird nicht blockiert

Wenn Sie ein Gerät ermitteln, das nicht kompatibel ist, aber weiterhin Zugriff hat, gehen Sie folgendermaßen vor.

- Überprüfen Sie die Ziel- und Ausschlussgruppen. Wenn sich ein Benutzer nicht in der richtigen Zielgruppe oder in der Ausschlussgruppe befindet, wird er nicht blockiert. Nur die Geräte der Benutzer in einer Zielgruppe werden hinsichtlich der Kompatibilität überprüft.
- Stellen Sie sicher, dass das Gerät ermittelt wird. Verweist der Exchange Connector auf einen Exchange 2010-Clientzugriffsserver, obwohl sich der Benutzer auf einem Exchange 2013-Server befindet? In diesem Fall kann Intune die Verbindung des Geräts mit Exchange nicht erkennen, wenn die Exchange-Standardregel „Zulassen“ lautet, auch wenn sich der Benutzer in der Zielgruppe befindet.
- Überprüfen Sie die Existenz und den Zugriffsstatus des Geräts in Exchange:
    - Verwenden Sie dieses PowerShell-Cmdlet, um eine Liste aller mobilen Geräte für ein Postfach abzurufen: „Get-ActiveSyncDeviceStatistics -mailbox mbx“. Wenn das Gerät nicht aufgeführt ist, greift es nicht auf Exchange zu.
    - Wenn das Gerät aufgeführt ist, verwenden Sie das Cmdlet „Get-CASmailbox -identity:’upn’ | fl“, um ausführliche Informationen zum Zugriffsstatus zu erhalten und diese Informationen dem Microsoft-Support bereitzustellen.

## <a name="before-you-open-a-support-ticket"></a>Vor dem Öffnen eines Supporttickets
Wenn diese Verfahren zur Problembehandlung das Problem nicht beheben, gibt es einige Informationen, die Sie möglicherweise dem Microsoft-Support bereitstellen müssen, z. B. die OWA-Postfachprotokolle oder Exchange Connector-Protokolle.

### <a name="collecting-owa-mailbox-logs"></a>Sammeln von OWA-Postfachprotokollen

1. Melden Sie sich über OWA an, und wählen Sie das Symbol „Einstellungen“ (Zahnrad) neben Ihrem Namen in der oberen rechten Ecke aus.
2. Wählen Sie **Optionen** aus
3. Wählen Sie in der Spalte auf der linken Seite **Telefon** (oder **Mobiltelefone**) aus.
4. Wählen Sie im oberen Menü **Mobiltelefone** aus.
5. Wählen Sie Ihr Gerät aus der Liste aus, und wählen Sie anschließend **Protokollierung starten** aus.
6. Wenn Sie dazu aufgefordert werden, wählen Sie im Popupdialogfenster **Ja** aus.
7. Führen Sie die Aktion aus, die das Problem verursacht hat, damit Sie es reproduzieren können.
8. Warten Sie ein bis zwei Minuten, und kehren Sie dann zur Telefonliste in OWA zurück. Vergewissern Sie sich, dass Ihr Telefon in der Liste ausgewählt ist, und wählen Sie aus dem oberen Menü **Protokoll abrufen** aus.
9. Sie sollten jetzt eine E-Mail von sich selbst mit einem Anhang erhalten. Stellen Sie Microsoft Support beim Öffnen eines Supporttickets den Inhalt der E-Mail zur Verfügung.

### <a name="exchange-connector-logs"></a>Exchange Connector-Protokolle

#### <a name="general-log-information"></a>Allgemeine Protokollinformationen
Verwenden Sie zum Anzeigen der Exchange Connector-Protokolle das [Server Trace Viewer-Tool](Server Trace Viewer-Tool (https://msdn.microsoft.com/library/ms732023(v=vs.110).aspx')). Dieses Tool erfordert, dass Sie das Windows Server-SDK herunterladen.

>[!NOTE]
>Die Protokolle befinden sich unter „C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs“. Die Protokolle befinden sich in einer Folge von 30 Protokolldateien, die mit *Connector0.log* beginnen und mit *Connector29.log* enden. Protokolliert Rollover von einer Datei zu einer anderen, nachdem sich 10 MB an Daten in einem Protokoll angesammelt haben. Nachdem die Protokolle zu „Connector29“ gelangt sind, wird wieder bei „Connector0“ begonnen, wobei die vorherigen Protokolldateien überschrieben werden.

#### <a name="locating-sync-logs"></a>Suchen von Synchronisierungsprotokollen

-    Suchen Sie eine vollständige Synchronisierung in den Protokollen, indem Sie nach **full sync** suchen. Der Anfang einer vollständigen Synchronisierung wird durch den folgenden Text gekennzeichnet:

    „Handling command: Getting the mobile device list without a time filter (full sync) for <number> users“

    Das Ende des Protokolls für eine vollständige Synchronisierung sieht folgendermaßen aus:

    „Getting the mobile device list without a time filter (full sync) for 4 users completed successfully.“ Details: Inventory command result - Devices synced: 0 Commmand ID: commandIDGUID' Exchange health: 'Server health 'Name: 'PowerShellExchangeServer: <Name=mymailservername>' Status: Connected','

-   Suchen Sie eine schnelle Synchronisierung (Delta) in den Protokollen, indem Sie nach **quick sync** suchen.

##### <a name="exceptions-in-get-next-command"></a>Ausnahmen im Befehl „Get next“
Überprüfen Sie die Exchange Connector-Protokolle auf Ausnahmen im **Befehl „Get next“**, und stellen Sie diese dem Microsoft-Support bereit.

#### <a name="verbose-logging"></a>Ausführliche Protokollierung

So aktivieren Sie die ausführliche Protokollierung

1.  Öffnen Sie die Konfigurationsdatei für die Exchange Connector-Ablaufverfolgung. Die Datei befindet sich unter: %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml.
2.  Suchen Sie nach „TraceSourceLine“ mit dem folgenden Schlüssel: „OnPremisesExchangeConnectorService“
3.  Ändern Sie den Knotenwert für **SourceLevel** von **Warning ActivityTracing** (Standardeinstellung) in **Verbose ActivityTracing**, wie nachfolgend veranschaulicht.

    <TraceSourceLine> <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key> <Value xsi:type="TraceSource"> <SourceLevel>All</SourceLevel> <Listeners> <Listener> <ListenerType>CircularTraceListener</ListenerType> <SourceLevel>Verbose ActivityTracing</SourceLevel> <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes> <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName> <FileQuota>30</FileQuota> </Listener> </Listeners> </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) beschrieben an den Microsoft Support.
