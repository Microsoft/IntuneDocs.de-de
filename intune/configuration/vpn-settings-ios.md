---
title: Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Fügen Sie ein VPN-Konfigurationsprofil hinzu bzw. erstellen Sie dieses, indem Sie Konfigurationseinstellungen für virtuelle private Netzwerke (VPNs) verwenden, einschließlich der Verbindungsdetails, Authentifizierungsmethoden und dem getrennten Tunneln in den Grundeinstellungen; der benutzerdefinierten VPN-Einstellungen mit dem Bezeichner und den Schlüssel-Wert-Paaren; der App-bezogenen VPN-Einstellungen, die Safari-URLs und bedarfsgesteuerten VPNs mit SSIDs oder DNS-Suchdomänen enthalten; und der Proxyeinstellungen zum Einschließen von einem Konfigurationsskript, einer IP-Adresse oder FQDN-Adresse und einem TCP-Port in Microsoft Intune auf Geräten mit iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6d7b831899a740e722560c509c4b09c31d2a42b
ms.sourcegitcommit: 8c25aeefb7cbc6444a8596af22fccd1c5426877a
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72593785"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Hinzufügen von VPN-Einstellungen auf iOS-Geräten in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune umfasst viele VPN-Einstellungen, die auf iOS-Geräten bereitgestellt werden können. Diese Einstellungen werden zum Erstellen und Konfigurieren von VPN-Verbindungen mit dem Netzwerk Ihrer Organisation verwendet. Dieser Artikel beschreibt diese Einstellungen. Einige Einstellungen sind nur für bestimmte VPN-Clients, z.B. Citrix oder Zscaler, verfügbar.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](vpn-settings-configure.md)

> [!NOTE]
> Diese Einstellungen sind für alle Registrierungs Typen verfügbar. Weitere Informationen zu den Registrierungs Typen finden Sie unter [IOS](../enrollment/ios-enroll.md)-Registrierung.

## <a name="connection-type"></a>Verbindungstyp

Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**: Gilt für die [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)-App-Version 4.0.5x und ältere Versionen.
- **Cisco AnyConnect**: Gilt für die [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)-App-Version 4.0.7x und höhere Versionen.
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: Gilt für die F5 Access-App-Version 2.1 und ältere Versionen.
- **F5 Access**: Gilt für die F5 Access-App-Version 3.0 und höhere Versionen.
- **Palo Alto Networks GlobalProtect (Legacy)** : Gilt für Palo Alto Networks GlobalProtect-App-Version 4.1 und ältere Versionen.
- **Palo Alto Networks GlobalProtect**: Gilt für Palo Alto Networks GlobalProtect-App-Version 5.0 und höhere Versionen.
- **Pulse Secure**
- **Cisco (IPsec)**
- **Citrix-VPN**
- **Citrix SSO**
- **Zscaler**: Um den bedingten Zugriff zu nutzen oder Benutzern zu ermöglichen, den Zscaler-Anmeldebildschirm zu umgehen, müssen Sie Zscaler Private Access (ZPA) in Ihr Azure AD-Konto integrieren. Ausführliche Schritte finden Sie in der [Zscaler-Dokumentation](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad). 
- **IKEv2**: [IKEv2 Settings](#ikev2-settings) (in diesem Artikel) beschreibt die Eigenschaften.
- **Benutzerdefiniertes VPN**

> [!NOTE]
> Cisco, Citrix, F5 und Palo Alto haben angekündigt, dass ihre Legacy-Clients mit iOS 12 nicht funktionieren. Sie sollten so schnell wie möglich auf die neuen Apps umsteigen. Weitere Informationen finden Sie im [Microsoft Intune-Blog des Supportteams](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

Die in der folgenden Liste gezeigten Einstellungen hängen vom ausgewählten VPN-Verbindungstyp ab.  

- **Verbindungsname**: Endbenutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät eine Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Benutzerdefinierter Domänennamen** (nur für Zscaler): Füllen Sie das Anmeldefeld der Zscaler-App vorab mit der Domäne auf, zu der Ihre Benutzer gehören. Wenn beispielsweise ein Benutzername `Joe@contoso.net` lautet, würde die Domäne `contoso.net` beim Öffnen der App statisch im Feld erscheinen. Wenn Sie keinen Domänennamen eingeben, wird der Domänenteil des UPN in Azure Active Directory (AD) verwendet.
- **IP-Adresse oder FQDN**: Die IP-Adresse oder der vollqualifizierte Domänenname (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise `192.168.1.1` oder `vpn.contoso.com` ein.
- **Cloudname der Organisation** (nur für Zscaler): Geben Sie den Namen der Cloud ein, in der Ihre Organisation bereitgestellt wird. In der von Ihnen verwendeten URL, die Sie für die Anmeldung bei Zscaler verwenden, ist der Name enthalten.  
- **Authentifizierungsmethode:** Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. 
  - **Zertifikate:** Wählen Sie unter **Authentifizierungszertifikat** ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten](../protect/certificates-configure.md).
  - **Benutzername und Kennwort:** Benutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server eingeben.  

    > [!NOTE]
    > Wenn Benutzername und Kennwort als Authentifizierungsmethode für Cisco IPsec VPN verwendet werden, müssen sie das SharedSecret über ein benutzerdefiniertes Apple Configurator-Profil bereitstellen.

  - **Abgeleitete**Anmelde Informationen: Wenn kein abgeleiteter Anmelde Informations Aussteller konfiguriert wurde, werden Sie von InTune dazu aufgefordert.

- **Ausgeschlossene URLs** (nur für Zscaler): Wenn Sie mit dem Zscaler-VPN verbunden sind, sind die aufgeführten URLs außerhalb der Zscaler-Cloud erreichbar. 

- **Getrenntes Tunneln**: **Aktivieren** oder **deaktivieren** Sie diese Option, damit die Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Zum Beispiel verwendet ein Benutzer in einem Hotel die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, das Standardnetzwerk des Hotels jedoch für normales Webbrowsen.

- **VPN-Bezeichner** (benutzerdefiniertes VPN, Zscaler und Citrix): Ein Bezeichner für die verwendete VPN-App, der von Ihrem VPN-Anbieter bereitgestellt wird.
  - **Geben Sie Schlüssel-Wert-Paare für die benutzerdefinierten VPN-Attribute Ihrer Organisation ein:** Fügen Sie **Schlüssel** und **Werte** zum Anpassen der VPN-Verbindung hinzu, oder importieren Sie sie. Denken Sie daran, dass diese Werte in der Regel von Ihrem VPN-Anbieter bereitgestellt werden.

- **Netzwerkzugriffssteuerung (NAC) aktivieren** (nur Citrix SSO, F5 Access): Wenn Sie auf **Ich stimme zu** klicken, wird die Geräte-ID in das VPN-Profil eingeschlossen. Diese ID kann für die Authentifizierung beim VPN verwendet werden, um Zugriff auf das Netzwerk zu ermöglichen oder zu verhindern.

  Achten Sie bei **Verwenden von F5 Access** auf Folgendes:

  - Vergewissern Sie sich, dass Sie F5 BIG-IP 13.1.1.5 nutzen. BIG-IP 14 wird nicht unterstützt.
  - Integrieren Sie BIG-IP für NAC in Intune. Siehe die F5-Anleitung [Konfigurieren von APM für Gerätestatusüberprüfungen mit Endpunktverwaltungssystemen](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89).
  - Aktivieren Sie die NAC im VPN-Profil.

  **Wenn Sie Citrix SSO mit Gateway verwenden**, führen Sie Folgendes durch:

  - Vergewissern Sie sich, dass Sie Citrix Gateway 12.0.59 oder höher verwenden.
  - Vergewissern Sie sich, dass Ihre Benutzer Citrix SSO 1.1.6 oder höher auf ihren Geräten installiert haben.
  - Integrieren Sie Citrix Gateway für NAC in Intune. Siehe den Citrix-Bereitstellungsleitfaden [Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) (Integration von Microsoft Intune/Enterprise Mobility + Security E3 in NetScaler [Szenario mit LDAP+OTP]).
  - Aktivieren Sie die NAC im VPN-Profil.

  **Wichtige Details**:  

  - Wenn die NAC aktiviert ist, wird die VPN-Verbindung alle 24 Stunden getrennt. Die VPN-Verbindung kann sofort wiederhergestellt werden.
  - Die Geräte-ID ist Teil des Profils, wird aber in Intune nicht angezeigt. Diese ID wird nicht von Microsoft gespeichert oder weitergegeben.

  Wenn die Geräte-ID von VPN-Partnern unterstützt wird, kann der VPN-Client, z.B. Citrix SSO, die ID abrufen. Anschließend kann Intune abgefragt werden, um zu bestätigen, dass das Gerät registriert ist und ob das VPN-Profil konform ist oder nicht.

  - Zum Entfernen dieser Einstellung erstellen Sie das Profil neu und wählen **Ich stimme zu** nicht aus. Anschließend weisen Sie das Profil neu zu.

## <a name="ikev2-settings"></a>IKEv2 Einstellungen

Diese Einstellungen gelten, wenn Sie **Verbindungstyp**  > **IKEv2**auswählen.

- **Remote**-ID: Geben Sie die Netzwerk-IP-Adresse, den voll qualifizierten Namen, den Benutzernamen oder den ASN1DN des IKEv2-Servers ein. Geben Sie beispielsweise `10.0.0.3` oder `vpn.contoso.com` ein. In der Regel geben Sie den gleichen Wert wie für den [**Verbindungs Namen**](#base-vpn-settings) ein (in diesem Artikel). Es hängt jedoch von den IKEv2-Servereinstellungen ab.

- **Client Authentifizierungstyp**: Wählen Sie aus, wie der VPN-Client beim VPN authentifiziert werden soll. Folgende Optionen sind verfügbar:
  - **Benutzerauthentifizierung** (Standard): authentifizieren sich Benutzer Anmelde Informationen beim VPN.
  - **Computer Authentifizierung**: die Geräte Anmelde Informationen werden beim VPN authentifiziert.

- **Authentifizierungsmethode**: Wählen Sie den Typ der Client Anmelde Informationen aus, die an den Server gesendet werden sollen. Folgende Optionen sind verfügbar:
  - **Zertifikate**: verwendet ein vorhandenes Zertifikat Profil, um sich beim VPN zu authentifizieren. Stellen Sie sicher, dass dieses Zertifikat Profil dem Benutzer oder Gerät bereits zugewiesen ist. Andernfalls tritt bei der VPN-Verbindung ein Fehler auf.
    - **Zertifikattyp**: Wählen Sie den Verschlüsselungstyp aus, der vom Zertifikat verwendet wird. Stellen Sie sicher, dass der VPN-Server für die Annahme dieser Art von Zertifikat konfiguriert ist. Folgende Optionen sind verfügbar:
      - **RSA** (Standard)
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - **Benutzername und Kennwort** (nur Benutzerauthentifizierung): Wenn Benutzer eine Verbindung mit dem VPN herstellen, werden Sie aufgefordert, Ihren Benutzernamen und Ihr Kennwort einzugeben.
  - **Gemeinsamer geheimer** Schlüssel (nur Computer Authentifizierung): Hiermit können Sie einen gemeinsamen geheimen Schlüssel eingeben, der an den VPN-Server gesendet werden soll.
    - **Gemeinsamer geheimer**Schlüssel: Geben Sie den gemeinsamen geheimen Schlüssel ein, der auch als vorinstaltzter Schlüssel (PSK) bezeichnet wird. Stellen Sie sicher, dass der Wert dem auf dem VPN-Server konfigurierten gemeinsamen geheimen Schlüssel entspricht

- Allgemeiner **Name des Server Zertifikats Ausstellers**: ermöglicht es dem VPN-Server, sich beim VPN-Client zu authentifizieren. Geben Sie den allgemeinen Namen des Zertifikat Ausstellers (CN) des VPN-Serverzertifikats ein, das an den VPN-Client auf dem Gerät gesendet wird. Stellen Sie sicher, dass der CN-Wert mit der Konfiguration des VPN-Servers übereinstimmt. Andernfalls tritt bei der VPN-Verbindung ein Fehler auf.
- Allgemeiner **Name des Server Zertifikats**: Geben Sie den CN für das Zertifikat selbst ein. Wenn das Feld leer gelassen wird, wird der Remote-Bezeichnerwert verwendet.

- **Erkennung**von unzustellbaren Peers: Wählen Sie aus, wie oft der VPN-Client prüft, ob der VPN-Tunnel aktiv ist. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: verwendet den Standardwert des IOS-Systems, der mit der Auswahl des **Mediums**identisch sein kann.
  - **None**: deaktiviert die Erkennung von unzustellbaren Peers.
  - **Niedrig**: sendet eine KeepAlive-Nachricht alle 30 Minuten.
  - **Mittel** (Standard): sendet eine KeepAlive-Nachricht alle 10 Minuten.
  - **Hoch**: sendet eine KeepAlive-Nachricht alle 60 Sekunden.

- **Mindestens TLS-Versions Bereich**: Geben Sie die minimale zu verwendende TLS-Version ein. Geben Sie `1.0`, `1.1` oder `1.2` ein. Wenn das Feld leer gelassen wird, wird der Standardwert `1.0` verwendet.
- **Maximal TLS-Versions Bereich**: Geben Sie die maximale zu verwendende TLS-Version ein. Geben Sie `1.0`, `1.1` oder `1.2` ein. Wenn das Feld leer gelassen wird, wird der Standardwert `1.2` verwendet.
- **Perfektes vorwärts Geheimnis**: Wählen Sie aktivieren aus, um das perfekte vorwärts Geheimnis (PFS) zu **aktivieren** . PFS ist ein IP-Sicherheits Feature, das die Auswirkung verringert, wenn ein Sitzungsschlüssel kompromittiert wird. **Deaktivieren** (Standard) verwendet keine PFS.
- **Zertifikat Sperr Überprüfung**: Wählen Sie **aktivieren** aus, um sicherzustellen, dass die Zertifikate nicht widerrufen werden, bevor die VPN-Verbindung erfolgreich ist Diese Überprüfung ist der beste Aufwand. Wenn für den VPN-Server ein Timeout auftritt, bevor Sie ermitteln, ob das Zertifikat gesperrt wird, wird der Zugriff gewährt. **Deaktivieren** (Standard) überprüft nicht auf gesperrte Zertifikate.

- **Sicherheits Zuordnungs Parameter konfigurieren**: **nicht konfiguriert** (Standard) verwendet das IOS-System Standard. Wählen Sie **aktivieren** aus, um die beim Erstellen von Sicherheits Zuordnungen mit dem VPN-Server verwendeten Parameter einzugeben:
  - **Verschlüsselungsalgorithmus**: Wählen Sie den gewünschten Algorithmus aus:
    - DES
    - 3DES
    - AES-128
    - AES-256 (Standard)
    - AES-128-GCM
    - AES-256-GCM
  - **Integritäts Algorithmus**: Wählen Sie den gewünschten Algorithmus aus:
    - SHA1-96
    - SHA1-160
    - SHA2-256 (Standard)
    - SHA2-384
    - SHA2-512
  - **Diffie-Hellman-Gruppe**: Wählen Sie die gewünschte Gruppe aus. Der Standardwert ist Group `2`.
  - **Lebensdauer** (Minuten): Wählen Sie aus, wie lange die Sicherheits Zuordnung aktiv bleibt, bis die Schlüssel gedreht wurden. Geben Sie einen ganzzahligen Wert zwischen `10` und `1440` ein (1440 Minuten sind 24 Stunden). Der Standardwert ist `1440`.

- **Konfigurieren Sie einen separaten Satz von Parametern für untergeordnete Sicherheits Zuordnungen**: IOS ermöglicht Ihnen, separate Parameter für die IKE-Verbindung und alle untergeordneten Verbindungen zu konfigurieren. 

  **Nicht konfiguriert** (Standardeinstellung) verwendet die Werte, die Sie in der vorherigen Einstellung Sicherheits Zuordnungs **Parameter konfigurieren** eingegeben haben. Wählen Sie **aktivieren** aus, um die *beim Erstellen von* untergeordneten Sicherheits Zuordnungen für den VPN-Server verwendeten Parameter einzugeben:
  - **Verschlüsselungsalgorithmus**: Wählen Sie den gewünschten Algorithmus aus:
    - DES
    - 3DES
    - AES-128
    - AES-256 (Standard)
    - AES-128-GCM
    - AES-256-GCM
  - **Integritäts Algorithmus**: Wählen Sie den gewünschten Algorithmus aus:
    - SHA1-96
    - SHA1-160
    - SHA2-256 (Standard)
    - SHA2-384
    - SHA2-512
  - **Diffie-Hellman-Gruppe**: Wählen Sie die gewünschte Gruppe aus. Der Standardwert ist Group `2`.
  - **Lebensdauer** (Minuten): Wählen Sie aus, wie lange die Sicherheits Zuordnung aktiv bleibt, bis die Schlüssel gedreht wurden. Geben Sie einen ganzzahligen Wert zwischen `10` und `1440` ein (1440 Minuten sind 24 Stunden). Der Standardwert ist `1440`.

## <a name="automatic-vpn-settings"></a>Automatische VPN-Einstellungen

- **Pro-App-VPN**: Ermöglicht ein VPN pro App. VPN-Verbindungen können automatisch ausgelöst werden, wenn bestimmte Apps geöffnet sind. Apps lassen sich auch diesem VPN-Profil zuweisen. Weitere Informationen finden Sie in den [Anweisungen zum Einrichten des Pro-App-VPN für iOS-Geräte](vpn-setting-configure-per-app.md).
  - **Anbietertyp**: Nur für „Pulse Secure“ und „Benutzerdefiniertes VPN“ verfügbar.
  - Wenn Sie **Pro-App-VPN**-Profile für iOS mit Pulse Secure oder einem benutzerdefinierten VPN verwenden, können Sie das Tunneln entweder auf App-Ebene (app-proxy) oder auf Paketebene (packet-tunnel) nutzen. Legen Sie für Tunneln auf App-Ebene den Wert **ProviderType** auf **app-proxy** oder für Tunneln auf Paketebene auf **packet-tunnel** fest. Wenn Sie sich nicht sicher sind, welcher Wert benutzt werden soll, lesen Sie dies in der Dokumentation Ihres VPN-Anbieters nach.
  - **Safari URLs, die dieses VPN auslösen**: Fügen Sie mindestens eine Website-URL hinzu. Wenn diese URLs mit dem Safari-Browser auf dem Gerät aufgerufen werden, wird die VPN-Verbindung automatisch aufgebaut.

- **Bedarfsgesteuertes VPN:** Konfigurieren Sie bedingte Regeln, die steuern, wann die VPN-Verbindung gestartet wird. Erstellen Sie beispielsweise eine Bedingung, in der die VPN-Verbindung nur verwendet wird, wenn ein Gerät nicht mit einem WLAN des Unternehmens verbunden ist. Oder erstellen Sie eine Bedingung. Wenn beispielsweise ein Gerät nicht auf eine von Ihnen angegebene DNS-Suchdomäne zugreifen kann, wird die VPN-Verbindung nicht gestartet.

  - **SSIDs oder DNS-Suchdomänen:** Wählen Sie aus, ob diese Bedingung **SSIDs** des Drahtlosnetzwerks oder **DNS-Suchdomänen** verwenden soll. Klicken Sie auf **Hinzufügen**, um SSIDs oder Suchdomänen zu konfigurieren.
  - **URL-Zeichenfolgentest:** Optional. Geben Sie eine URL ein, die die Regel als Test verwenden soll. Wenn das Gerät mit diesem Profil auf diese URL ohne Umleitung zugreift, wird die VPN-Verbindung gestartet. Und das Gerät wird mit der Ziel-URL verbunden. Der Standort des URL-Zeichenfolgentests wird dem Benutzer nicht angezeigt. Ein Beispiel für einen URL-Zeichenfolgentest ist die Adresse eines Überwachungswebservers, der die Gerätekonformität prüft, bevor die VPN-Verbindung hergestellt wird. Eine andere Möglichkeit besteht darin, mit der URL zu testen, ob das VPN eine Verbindung mit einem Standort herstellen kann, bevor das Gerät über das VPN mit der Ziel-URL verbunden wird.
  - **Domänenaktion:** Wählen Sie eine der folgenden Optionen aus:
    - Bei Bedarf verbinden
    - Nie verbinden
  - **Aktion:** Wählen Sie eine der folgenden Optionen aus:
    - Verbinden
    - Verbindung auswerten
    - Ignorieren
    - Trennen

## <a name="proxy-settings"></a>Proxyeinstellungen

Wenn Sie einen Proxy verwenden, konfigurieren Sie die folgenden Einstellungen. Proxyeinstellungen sind nicht für Zscaler-VPN-Verbindungen verfügbar.  

- **Automatisches Konfigurationsskript**: Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** (z.B. `http://proxy.contoso.com`) ein, unter der die Konfigurationsdatei zu finden ist.
- **Adresse:** Geben Sie die IP-Adresse des vollständig qualifizierten Hostnamens des Proxyservers ein.
- **Portnummer:** Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Konfigurieren Sie VPN-Einstellungen auf [Android](vpn-settings-android.md)-, [Android Enterprise](vpn-settings-android-enterprise.md)-, [macOS](vpn-settings-macos.md)-und [Windows 10](vpn-settings-windows-10.md) -Geräten.
