---
title: VPN-Verbindungen
description: "Verwenden Sie VPN-Profile zur Bereitstellung von VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7c63c817ccddd0abc6c5c6b0ae2f2a7d1cb2d9bf
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="vpn-connections-in-microsoft-intune"></a>VPN-Verbindungen in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Virtuelle private Netzwerke (virtual private networks, VPNs) bieten Ihren Benutzern sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. Geräte verwenden ein *VPN-Verbindungsprofil*, um eine Verbindung mit dem VPN-Server zu initiieren. *VPN-Profile* in Microsoft Intune ermöglichen Ihnen die Bereitstellung von VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation, damit diese leicht eine sichere Verbindung zum Netzwerk herstellen können.

Nehmen Sie z. B. an, Sie möchten allen iOS-Geräten die Einstellungen zur Verfügung stellen, die zum Verbinden mit einer Dateifreigabe im Unternehmensnetzwerk erforderlich sind. Sie erstellen ein VPN-Profil mit den Einstellungen, die zum Herstellen einer Verbindung mit dem Unternehmensnetzwerk erforderlich sind, und stellen dieses Profil dann für alle Benutzer mit iOS-Geräten bereit. Die Benutzer sehen die VPN-Verbindung in der Liste der verfügbaren Netzwerke und können mit geringem Aufwand eine Verbindung herstellen.

Sie können die folgenden Gerätetypen mit VPN-Profilen konfigurieren:

* Geräte unter Android 4 und höher
* Android for Work-Geräte
* Geräte unter iOS 8.0 und höher
* Geräte unter Mac OS X 10.9 und höher
* Registrierte Geräte unter Windows 8.1 und höher
* Geräte unter Windows Phone 8.1 und höher
* Geräte unter Windows 10 Desktop und Mobile

Die Konfigurationsoptionen für VPN-Profile variieren je nach gewähltem Gerätetyp.

## <a name="vpn-connection-types"></a>VPN-Verbindungstypen

Intune unterstützt die Erstellung von VPN-Profilen mit den folgenden Verbindungstypen:


Verbindungstyp |iOS und Mac OS X  |Android und Android for Work|Windows 8.1|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop und Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Ja  |Ja    |Nein    |Nein  |Nein    | Ja (OMA-URI, nur mobil)|     
Cisco (IPsec)|Ja  |Ja    |Nein  |Nein  |Nein | Nein|
Citrix|Ja  |Ja (nur Android)   |Nein  |Nein  |Nein | Nein|
Pulse Secure|Ja   |Ja  |Ja    |Ja   |Ja | Ja |        
F5 Edge Client|Ja  |Ja  |Ja  |Ja   |   Ja  |  Ja |   
SonicWall Mobile Connect|Ja  |Ja  |Ja  |Ja  |Ja  |Ja |         
CheckPoint Mobile VPN|Ja  |Ja  |Ja  |Ja |Ja |Ja |
Microsoft SSL (SSTP)|Nein |Nein |Nein |Nein|Nein|VPN v1 OMA-URI*|
Microsoft Automatic|Nein |Nein |Nein |Nein|Ja (OMA-URI)|Ja |
IKEv2|Benutzerdefiniertes Profil für iOS|Nein |Nein |Nein|Ja (OMA-URI)|Ja |
PPTP|Benutzerdefiniertes Profil für iOS|Nein |Nein |Nein|Nein|Ja |
L2TP|Benutzerdefiniertes Profil für iOS|Nein |Nein |Nein|Ja (OMA-URI)|Ja |

\* Ohne zusätzliche Einstellungen, die andernfalls für Windows 10 verfügbar sind.

> [!IMPORTANT]
> Vor der Verwendung von VPN-Profilen, die auf einem Gerät bereitgestellt werden, müssen Sie die entsprechende VPN-App für das Profil installieren. Sie können die Informationen im Thema [Bereitstellen von Apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) verwenden, um Unterstützung beim Bereitstellen der entsprechenden Anwendung mit Intune zu erhalten.  

 Informationen zum Erstellen benutzerdefinierter VPN-Profile mithilfe von URI-Einstellungen finden Sie unter [Benutzerdefinierte Konfigurationen für VPN-Profile](create-custom-vpn-profiles.md).     

## <a name="methods-of-securing-vpn-profiles"></a>Methoden zum Schützen von VPN-Profilen

VPN-Profile können eine Reihe verschiedener Verbindungstypen und Protokolle von unterschiedlichen Herstellern verwenden. Diese Verbindungen werden in der Regel mit einer von zwei Methoden gesichert.

### <a name="certificates"></a>Zertifikate

Beim Erstellen des VPN-Profils wählen Sie ein SCEP- oder PFX-Zertifikatprofil aus, das Sie zuvor in Intune erstellt haben. Dies wird als Identitätszertifikat bezeichnet. Es dient zur Authentifizierung anhand eines von Ihnen erstellten vertrauenswürdigen Zertifikatprofils (oder eines *Stammzertifikats*), mit dem überprüft wird, ob das Gerät des Benutzers eine Verbindung herstellen darf. Das vertrauenswürdige Zertifikat wird auf dem Computer bereitgestellt, der die VPN-Verbindung authentifiziert, in der Regel ist dies der VPN-Server.

Weitere Informationen zum Erstellen und Verwenden von Zertifikatprofilen in Intune finden Sie unter [Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen](secure-resource-access-with-certificate-profiles.md).

### <a name="user-name-and-password"></a>Benutzername und Kennwort

Der Benutzer authentifiziert sich beim VPN-Server durch Angabe seines Benutzernamens und Kennworts.

## <a name="create-a-vpn-profile"></a>Erstellen eines VPN-Profils

1. Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** > **Richtlinie hinzufügen**.
2. Wählen Sie eine Vorlage für die neue Richtlinie aus, indem Sie den entsprechenden Gerätetyp erweitern, und wählen Sie dann das VPN-Profil für dieses Gerät aus:
    * **VPN-Profil (Android 4 und höher)**
    * **VPN-Profil (Android for Work)**
    * **VPN-Profil (iOS 8.0 und höher)**
    * **VPN-Profil (Mac OS X 10.9 und höher)**
    * **VPN-Profil (Windows 8.1 und höher)**
    * **VPN-Profil (Windows Phone 8.1 und höher)**
    * **VPN-Profil (Windows 10 Desktop und Mobile und höher)**

 Sie können nur benutzerdefinierte VPN-Profilrichtlinien erstellen und bereitstellen. Empfohlene Einstellungen sind nicht verfügbar.

> [!Note]
> Ein VPN-Profil für Android for Work-Geräte lässt nur für solche Apps eine VPN-Verbindung zu, die auf dem Arbeitsprofil des Geräts installiert sind.
>
> Einige VPN-Verbindungstypen unterstützen VPN pro App für Android for Work-Geräte und für die Aktivierung von VPN pro App auf Apps, die durch Intune verteilt werden.  

3. Orientieren Sie sich bei der Konfiguration der Einstellungen für das VPN-Profil an der folgenden Tabelle:

Name der Einstellung  |Weitere Informationen  
---------|---------
**Name**     |Geben Sie einen eindeutigen Namen für das VPN-Profil ein, damit Sie es leichter in der Intune-Konsole identifizieren können.         
**Beschreibung**     |Geben Sie eine Beschreibung mit einem Überblick über das VPN-Profil und anderen relevanten Informationen ein, die Ihnen bei der Suche danach helfen.         
**VPN-Verbindungsname (wird Benutzern angezeigt)**     |Geben Sie einen Namen für das VPN-Profil ein. Dies ist der Name, der Benutzern in der Liste der verfügbaren VPN-Verbindungen auf ihren Geräten angezeigt wird.         
**Verbindungstyp**     |  Wählen Sie einen der folgenden Verbindungstypen zur Verwendung im VPN-Profil aus: **Cisco AnyConnect** (nicht verfügbar für Windows 8.1 oder Windows Phone 8.1), **Pulse Secure**, **Citrix**, **F5 Edge Client**, **SonicWall Mobile Connect**, **CheckPoint Mobile VPN**.
**VPN-Serverbeschreibung**     | Geben Sie eine Beschreibung für den VPN-Server an, mit dem Geräte eine Verbindung herstellen. Beispiel: **Contoso-VPN-Server**. Wenn der Verbindungstyp **F5 Edge Client** ist, geben Sie im Feld **Serverliste** eine Liste der Serverbeschreibungen und IP-Adressen an.
**IP-Adresse oder FQDN des Servers**    |Geben Sie die IP-Adresse oder den vollständig qualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.  Wenn der Verbindungstyp **F5 Edge Client** ist, geben Sie im Feld **Serverliste** eine Liste der Serverbeschreibungen und IP-Adressen an.         |         
**Serverliste**     |Klicken Sie auf **Hinzufügen**, um einen neuen VPN-Server zur Verwendung für die VPN-Verbindung hinzuzufügen. Sie können auch angeben, welcher Server als Standardserver für die Verbindung dienen soll. Diese Option wird nur für den Verbindungstyp **F5 Edge Client** angezeigt.         
**Gesamten Netzwerkdatenverkehr über die VPN-Verbindung senden**     |Wenn Sie diese Option aktivieren, wird der gesamte Netzwerkdatenverkehr über die VPN-Verbindung gesendet. Wenn Sie diese Option nicht auswählen, verhandelt der Client dynamisch die Routen für getrenntes Tunneln beim Herstellen einer Verbindung mit dem VPN-Server eines Drittanbieters. Nur Verbindungen mit dem Unternehmensnetzwerk werden über einen VPN-Tunnel gesendet. Beim Verbinden mit Ressourcen im Internet wird VPN-Tunneln nicht verwendet.
**Authentifizierungsmethode**| Wählen Sie die von der VPN-Verbindung verwendete Authentifizierungsmethode aus: **Zertifikate** oder **Benutzername und Kennwort**. (Die Einstellung **Benutzername und Kennwort** ist für den Verbindungstyp „Cisco AnyConnect“ nicht verfügbar.) Die Option **Authentifizierungsmethode** ist für Windows 8.1 nicht verfügbar.
**Benutzeranmeldeinformationen bei jeder Anmeldung speichern**|Aktivieren Sie diese Option, um sicherzustellen, dass die Benutzeranmeldeinformationen gespeichert werden, sodass der Benutzer die Anmeldeinformationen nicht bei jeder Verbindungsherstellung erneut eingeben muss.
**Clientzertifikat für die Clientauthentifizierung (Identitätszertifikat) auswählen**|Wählen Sie das SCEP-Clientzertifikat aus, das Sie zuvor erstellt haben und das zur Authentifizierung der VPN-Verbindung verwendet wird. Weitere Informationen zum Verwenden von Zertifikatprofilen in Intune finden Sie unter [Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen](secure-resource-access-with-certificate-profiles.md). Diese Option wird nur für die Authentifizierungsmethode **Zertifikate** angezeigt.
**Rolle**| Geben Sie den Namen der Benutzerrolle an, die Zugriff auf diese Verbindung hat. Eine Benutzerrolle definiert persönliche Einstellungen und Optionen und aktiviert oder deaktiviert bestimmte Zugriffsfeatures. Diese Option wird nur für den Verbindungstyp **Pulse Secure** oder **Citrix** angezeigt.
**Bereich**|Geben Sie den Namen des gewünschten Authentifizierungsbereichs an. Ein Authentifizierungsbereich ist eine Gruppe von Authentifizierungsressourcen, die vom Verbindungstyp „Pulse Secure“ oder „Citrix“ verwendet werden. Diese Option wird nur für den Verbindungstyp **Pulse Secure** oder **Citrix** angezeigt.
**Anmeldegruppe oder Domäne**|Geben Sie den Namen der Anmeldegruppe oder Domäne an, mit der Sie eine Verbindung herstellen möchten. Diese Option wird nur für den Verbindungstyp **SonicWall Mobile Connect** angezeigt.
**Fingerabdruck**|Geben Sie eine Zeichenfolge (z. B. „Contoso-Fingerabdruckcode“) an, anhand der überprüft wird, ob der VPN-Server vertrauenswürdig ist. Ein Fingerabdruck kann an den Client gesendet werden, damit dieser weiß, dass alle Server vertrauenswürdig sind, die beim Verbinden den betreffenden Fingerabdruck vorweisen. Wenn das Gerät nicht über den Fingerabdruck verfügt, wird der Benutzer aufgefordert, dem VPN-Server zu vertrauen, mit dem Verbindung hergestellt wird, während der Fingerabdruck angezeigt wird. (Der Benutzer überprüft den Fingerabdruck manuell und wählt **Vertrauen** aus, um die Verbindung herzustellen.) Diese Option wird nur für den Verbindungstyp **CheckPoint Mobile VPN** angezeigt.
**VPN für App**|Mit dieser Option können Sie diese VPN-Verbindung einer iOS- oder Mac OS X-App zuzuordnen, sodass die Verbindung geöffnet wird, wenn die Anwendung ausgeführt wird. Die Zuordnung des VPN-Profils zu einer App kann bei der Bereitstellung der Software erfolgen. Weitere Informationen finden Sie unter [Bereitstellen von Apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
**Bedarfsgesteuertes VPN**|Sie können für Geräte mit iOS 8.0 und höher ein bedarfsgesteuertes VPN einrichten. Eine Anleitung zum Einrichten eines bedarfsgesteuerten VPN finden Sie unter [Bedarfsgesteuertes VPN für iOS-Geräte](#on-demand-vpn-for-ios-devices).
**Proxyeinstellungen automatisch erkennen** (nur iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1)|Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, geben Sie an, ob Geräte die Verbindungseinstellungen automatisch erkennen können sollen. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
**Automatisches Konfigurationsskript verwenden** (nur iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1)|Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, geben Sie an, ob Sie die Einstellungen mit einem automatischen Konfigurationsskript definieren und dann eine URL zur Datei mit den Einstellungen angeben möchten. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
**Proxyserver verwenden** (nur iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1)|Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, aktivieren Sie diese Option, und geben Sie dann die Adresse und die Portnummer des Proxyservers an. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
**Proxyeinstellungen für lokale Adressen umgehen** (nur iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1)|Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, aktivieren Sie diese Option, wenn der Proxyserver für von Ihnen angegebene lokale Adressen nicht verwendet werden soll. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
**Benutzerdefiniertes XML** (Windows 8.1 und höher sowie Windows Phone 8.1 und höher)|Geben Sie benutzerdefinierte XML-Befehle zum Konfigurieren der VPN-Verbindung an. Beispiel für **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Beispiel für **CheckPoint Mobile VPN**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Beispiel für **SonicWall Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Beispiel für **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Weitere Informationen zum Erstellen von benutzerdefinierten XML-Befehlen finden Sie in der VPN-Dokumentation des jeweiligen Herstellers.
**DNS-Suffix-Suchliste** (nur Windows Phone 8.1)|Geben Sie in jeder Zeile ein DNS-Suffix an. Jedes angegebene DNS-Suffix wird beim Verbinden mit einer Website unter Verwendung eines Kurznamens gesucht. Geben Sie z. B. die DNS-Suffixe **domain1.contoso.com** und **domain2.contoso.com** ein, rufen Sie die URL **http://mywebsite** auf, und die URLs **http://mywebsite.domain1.contoso.com** und **http://mywebsite.domain2.contoso.com** werden durchsucht.
**Bei Verbindung mit dem Unternehmens-WLAN VPN umgehen** (nur Windows Phone 8.1)|Wählen Sie diese Option aus, um anzugeben, dass die VPN-Verbindung nicht verwendet wird, wenn das Gerät mit dem Unternehmens-WLAN verbunden ist.
**VPN umgehen, wenn mit Heimat-WLAN-Netzwerk verbunden** (nur Windows Phone 8.1)|Wählen Sie diese Option aus, um anzugeben, dass die VPN-Verbindung nicht verwendet wird, wenn das Gerät mit einem privaten WLAN verbunden ist.

Die folgenden zusätzlichen Einstellungen sind für Geräte mit Windows 10 Desktop und Mobile verfügbar.

Name der Einstellung  |Weitere Informationen  
---------|---------
**Regeln für den Netzwerkdatenverkehr**|Wählen Sie die Protokolle, die lokalen und Remoteports sowie die Adressbereiche aus, die für die VPN-Verbindung aktiviert werden sollen. Wenn Sie keine Regel für den Netzwerkdatenverkehr erstellen, werden alle Protokolle, Ports und Adressbereiche aktiviert. Nachdem Sie eine Regel erstellt haben, werden nur die in dieser Regel festgelegten Protokolle, Ports und Adressbereiche von der VPN-Verbindung verwendet.
**Routen**|Wählen Sie die Routen aus, welche die VPN-Verbindung verwenden.
**DNS-Server**| Wählen Sie die DNS-Server aus, die von der VPN-Verbindung verwendet werden, nachdem die Verbindung hergestellt wurde.         
**Zugeordnete Apps**|Stellen Sie eine Liste von Apps bereit, die automatisch die VPN-Verbindung verwenden. Der Typ der App bestimmt den App-Bezeichner. Stellen Sie für eine universelle App den Paketfamiliennamen bereit. Stellen Sie für eine Desktop-App den Dateipfad der App bereit.          


> [!IMPORTANT]
> Es wird empfohlen, alle Listen mit Apps zu schützen, die Sie für die Verwendung in der Konfiguration eines App-bezogenen VPN zusammenstellen. Wenn ein nicht autorisierter Benutzer die Liste ändert und Sie sie in die Liste der Apps für App-bezogenes VPN importieren, autorisieren Sie möglicherweise den VPN-Zugriff auf Apps, auf die nicht zugegriffen werden soll. Eine Möglichkeit, App-Listen zu schützen, ist die Verwendung einer Zugriffssteuerungsliste (Access Control List, ACL).

Im Folgenden finden Sie ein Beispiel für die Verwendung von Einstellungen für Unternehmensgrenzen. Wenn Sie das VPN nur für Remotedesktops aktivieren möchten, erstellen Sie eine Regel für den Netzwerkdatenverkehr, die Datenverkehr für Protokoll 27 am externen Port 3996 zulässt. Kein anderer Datenverkehr verwendet das VPN.

Das Definieren von Routen innerhalb von Unternehmensgrenzen ist nützlich, wenn Sie für Ihren VPN-Verbindungstyp nicht definieren können, wie Datenverkehr bei getrenntem Tunneln behandelt wird. Verwenden Sie in diesem Fall **Routen**, um die Routen aufzulisten, die das VPN verwenden.

Sie können die VPN-Nutzung für Windows 10-Geräte auf bestimmte Apps beschränken, indem Sie eine benutzerdefinierte OMA-URI-Einstellung erstellen.

Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt.

### <a name="on-demand-vpn-for-ios-devices"></a>Bedarfsgesteuertes VPN für iOS-Geräte
Sie können für Geräte mit iOS 8.0 und höher ein bedarfsgesteuertes VPN konfigurieren.

> [!NOTE]
>  
> Sie können keine VPNs pro App und bedarfsgesteuerten VPNs in derselben Richtlinie verwenden.

1. Suchen Sie auf der Seite der Richtlinienkonfiguration die Option **Bedarfsgesteuerte Regeln für diese VPN-Verbindung**. Die Spalten heißen **Übereinstimmung**, die Bedingung, deren Einhaltung die Regeln überprüfen, und **Aktion**, die Aktion, die durch die Richtlinie ausgelöst wird, wenn die Bedingung erfüllt ist.
2. Wählen Sie **Hinzufügen** aus, um eine Regel zu erstellen. Es gibt zwei Arten von Übereinstimmungen, die Sie in der Regel einrichten können. Sie können pro Regel jeweils nur eine Art konfigurieren.
  - **SSIDs**: beziehen sich auf drahtlose Netzwerke.
  - **DNS-Suchdomänen**: Sie können vollständig qualifizierte Domänennamen wie z.B. *team.corp.contoso.com* oder Domänen wie *contoso.com* verwenden (dies entspricht der Verwendung von **.contoso.com*).
3. Optional: Geben Sie eine URL-Zeichenfolgetest an, d. h. eine URL, die von der Regel als Test verwendet wird. Wenn das Gerät, auf dem dieses Profil installiert wird, auf diese URL ohne Umleitung zugreifen kann, wird das VPN eingerichtet, und das Gerät stellt eine Verbindung mit der Ziel-URL her. Der URL-Zeichenfolgentest-Standort wird dem Benutzer nicht angezeigt. Ein Beispiel für einen URL-Zeichenfolgentest ist die Adresse eines Überwachungswebservers, der die Gerätekompatibilität prüft, bevor die VPN-Verbindung hergestellt wird. Eine andere Möglichkeit besteht darin, mit der URL zu testen, ob das VPN eine Verbindung mit einem Standort herstellen kann, bevor das Gerät über das VPN mit der Ziel-URL verbunden wird.
4. Wählen Sie eine der folgenden Aktionen aus:
  - **Verbinden**
  - **Verbindung auswerten** verfügt über drei Einstellungen: a. **Domänenaktion**: Wählen Sie **Bei Bedarf verbinden** oder **Nie verbinden** aus: b. **Durch Trennzeichen getrennte Liste der Domänen**: Diese Option konfigurieren Sie nur, wenn Sie **Bei Bedarf verbinden** als **Domänenaktion** auswählen: c. **Test der erforderlichen URL-Zeichenfolge** – eine HTTP- oder HTTPS-URL (bevorzugt), z. B. *https://vpntestprobe.contoso.com*. Mit der Regel wird überprüft, ob diese Adresse eine Antwort sendet. Wenn dies nicht der Fall ist, und **Bei Bedarf verbinden** die **Domänenaktion** ist, wird das VPN ausgelöst.
      
     > [!TIP]
     >
     >Ein Beispiel für die Verwendung dieser Aktion: Für einige Standorte im Unternehmensnetzwerk ist eine direkte oder VPN-Unternehmensnetzwerkverbindung erforderlich, für andere jedoch nicht. Wenn Sie in **Durch Trennzeichen getrennte Liste von DNS-Suchdomänen** *corp.contoso.com* gelistet sind, können Sie **Bei Bedarf verbinden** auswählen und dann bestimmte Standorte innerhalb dieses Netzwerks auflisten, die möglicherweise VPN benötigen, z. B. *sharepoint.corp.contoso.com*. Die Regel überprüft daraufhin, ob *vpntestprobe.contoso.com* erreicht werden kann. Wenn dies nicht möglich ist, wird das VPN für die Sharepoint-Website ausgelöst.
  - **Ignorieren** – Die VPN-Konnektivität wird nicht geändert. Wenn das VPN verbunden ist, lassen Sie die Verbindung bestehen, wenn es nicht verbunden ist, stellen Sie keine Verbindung her. Angenommen, Sie verfügen über eine Regel, die für alle Ihre internen Unternehmenswebsites eine VPN-Verbindung herstellt, möchten eine dieser internen Websites aber nur verfügbar machen, wenn das Gerät tatsächlich mit dem Unternehmensnetzwerk verbunden ist. In diesem Fall würden Sie eine Ignorieren-Regel für diese eine Website erstellen.
  - **Trennen** – Trennt Geräte vom VPN, wenn die Bedingung erfüllt sind. Sie könnten Ihre Unternehmens-WLANs beispielsweise im Feld **SSIDs** auflisten und eine Regel erstellen, welche die Geräte vom VPN trennt, wenn sie eine Verbindung mit einem dieser Netzwerke herstellen.

Domänenspezifische Regeln werden vor Regeln ausgewertet, die für alle Domänen gelten.


## <a name="deploy-the-policy"></a>Bereitstellen der Richtlinie

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und wählen Sie dann **Bereitstellung verwalten** aus.

2.  Führen Sie im Dialogfeld **Bereitstellung verwalten** folgende Schritte aus:

    -   Um die Richtlinie bereitzustellen, wählen Sie mindestens eine Gruppe aus, für die Sie die Richtlinie bereitstellen möchten, und klicken Sie auf **Hinzufügen** &gt; **OK**.

    -   Klicken Sie zum Schließen des Dialogfelds auf **Abbrechen**, ohne die Richtlinie bereitzustellen.


Nach der erfolgreichen Bereitstellung sehen Benutzer den von Ihnen angegebenen VPN-Verbindungsnamen in der Liste der VPN-Verbindungen auf ihren Geräten.

Eine Statuszusammenfassung und Warnungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie** identifiziert Probleme mit der Richtlinie, die Ihre Aufmerksamkeit erfordern. Darüber hinaus wird eine Statusübersicht im Arbeitsbereich „Dashboard“ angezeigt.
