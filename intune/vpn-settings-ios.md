---
title: 'Hinzufügen von VPN-Einstellungen für iOS-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Fügen Sie ein VPN-Konfigurationsprofil hinzu bzw. erstellen Sie dieses, indem Sie Konfigurationseinstellungen für virtuelle private Netzwerke (VPNs) verwenden, einschließlich der Verbindungsdetails, Authentifizierungsmethoden und dem getrennten Tunneln in den Grundeinstellungen; der benutzerdefinierten VPN-Einstellungen mit dem Bezeichner und den Schlüssel-Wert-Paaren; der App-bezogenen VPN-Einstellungen, die Safari-URLs und bedarfsgesteuerten VPNs mit SSIDs oder DNS-Suchdomänen enthalten; und der Proxyeinstellungen zum Einschließen von einem Konfigurationsskript, einer IP-Adresse oder FQDN-Adresse und einem TCP-Port in Microsoft Intune auf Geräten mit iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b794ec40d05358ddd1aa3179c2f4060b2cd6fe1d
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236508"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Konfigurieren von VPN-Einstellungen auf iOS-Geräten in Microsoft Intune

Microsoft Intune umfasst viele VPN-Einstellungen, die auf iOS-Geräten bereitgestellt werden können. Diese Einstellungen werden zum Erstellen und Konfigurieren von VPN-Verbindungen mit dem Netzwerk Ihrer Organisation verwendet. Dieser Artikel beschreibt diese Einstellungen. Einige Einstellungen sind nur für bestimmte VPN-Clients, z.B. Citrix oder Zscaler, verfügbar.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

Die in der folgenden Liste gezeigten Einstellungen hängen vom ausgewählten VPN-Verbindungstyp ab.  

- **Verbindungsname**: Endbenutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät eine Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Benutzerdefinierter Domänennamen** (nur für Zscaler): Füllen Sie das Anmeldefeld der Zscaler-App mit der Domäne, zu der Ihre Benutzer gehören. Wenn beispielsweise ein Benutzername `Joe@contoso.net` lautet, würde die Domäne `contoso.net` beim Öffnen der App statisch im Feld erscheinen. Wenn Sie keinen Domänennamen eingeben, wird der Domänenteil des UPN in Azure Active Directory (AD) verwendet.
- **IP-Adresse oder FQDN**: Die IP-Adresse oder der vollqualifizierte Domänenname (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise `192.168.1.1` oder `vpn.contoso.com` ein.
- **Cloudname der Organisation** (nur für Zscaler): Geben Sie den Namen der Cloud ein, in der Ihre Organisation bereitgestellt wird. In der von Ihnen verwendeten URL, die Sie für die Anmeldung bei Zscaler verwenden, ist der Name enthalten.  
- **Authentifizierungsmethode:** Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. 
  - **Zertifikate:** Wählen Sie unter **Authentifizierungszertifikat** ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten](certificates-configure.md).
  - **Benutzername und Kennwort:** Benutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server eingeben.  

    > [!NOTE]
    > Wenn Benutzername und Kennwort als Authentifizierungsmethode für Cisco IPsec VPN verwendet werden, müssen sie das SharedSecret über ein benutzerdefiniertes Apple Configurator-Profil bereitstellen.
  
- **Verbindungstyp**: Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:
  - **Check Point Capsule VPN**
  - **Cisco Legacy AnyConnect**: Gilt für die [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)-App-Version 4.0.5x und ältere Versionen.
  - **Cisco AnyConnect**: Gilt für die [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)-App-Version 4.0.7x und höhere Versionen.
  - **SonicWall Mobile Connect**
  - **F5 Access Legacy**: Gilt für die F5 Access-App-Version 2.1 und ältere Versionen.
  - **F5 Access**: Gilt für die F5 Access-App-Version 3.0 und höhere Versionen.
  - **Palo Alto Networks GlobalProtect (Legacy)**: Gilt für Palo Alto Networks GlobalProtect-App-Version 4.1 und ältere Versionen.
  - **Palo Alto Networks GlobalProtect**: Gilt für Palo Alto Networks GlobalProtect-App-Version 5.0 und höhere Versionen.
  - **Pulse Secure**
  - **Cisco (IPsec)**
  - **Citrix-VPN**
  - **Citrix SSO**
  - **Zscaler**: Erfordert die Integration von Zscaler Private Access (ZPA) in Ihr Azure AD-Konto. Ausführliche Schritte finden Sie in der [Zscaler-Dokumentation](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
  - **Benutzerdefiniertes VPN**    

    > [!NOTE]
    > Cisco, Citrix, F5 und Palo Alto haben angekündigt, dass ihre Legacy-Clients mit iOS 12 nicht funktionieren. Sie sollten so schnell wie möglich auf die neuen Apps umsteigen. Weitere Informationen finden Sie im [Microsoft Intune-Blog des Supportteams](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

* **Ausgeschlossene URLs** (nur für Zscaler): Wenn Sie mit dem Zscaler-VPN verbunden sind, sind die aufgeführten URLs außerhalb der Zscaler-Cloud erreichbar. 

- **Getrenntes Tunneln**: **Aktivieren** oder **deaktivieren** Sie diese Option, damit die Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Zum Beispiel verwendet ein Benutzer in einem Hotel die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, das Standardnetzwerk des Hotels jedoch für normales Webbrowsen.

- **Netzwerkzugriffssteuerung (NAC) aktivieren**: Bei dieser Einstellung handelt es sich um einen Platzhalter für VPN-Clients wie Citrix, damit eine Geräte-ID in das VPN-Profil eingefügt werden kann, um diese für die Netzwerkzugriffssteuerung (NAC) zu verwenden. Wenn Sie **Ich stimme zu** auswählen, ist diese Geräte-ID im VPN-Profil enthalten. Derzeit gibt es keine VPN-Clients oder NAC-Partnerlösungen, die diese neue ID unterstützen, sodass Geräte unabhängig vom Konformitätsstatus eine Verbindung zum VPN herstellen können. Dieses Dokument wird aktualisiert, sobald unsere Partner ihre Unterstützung für die ID hinzufügen.

  Wichtige Details:  

  - Wenn diese Einstellung aktiviert ist, wird die VPN-Verbindung alle 24 Stunden getrennt.
  - Die Geräte-ID ist Teil des Profils, kann in Intune oder im Profil aber nicht angezeigt werden. Diese ID wird nicht von Microsoft gespeichert oder weitergegeben. Sobald dies von VPN-Partnern unterstützt wird, kann der VPN-Client, z.B. Citrix SSO, die ID abrufen. Außerdem kann er Intune abfragen, um zu bestätigen, dass das Gerät registriert ist und ob das VPN-Profil kompatibel ist.
  - Zum Entfernen dieser Einstellung erstellen Sie das Profil neu und wählen **Ich stimme zu** nicht aus. Anschließend weisen Sie das Profil neu zu.

## <a name="custom-vpn-settings"></a>Benutzerdefinierte VPN-Einstellungen

Wenn Sie **Benutzerdefiniertes VPN** als Verbindungstyp ausgewählt haben, konfigurieren Sie die folgenden Einstellungen. Diese Einstellungen sind auch für Zscaler- und Citrix-Verbindungen sichtbar.

- **VPN-Bezeichner:** Ein Bezeichner für die verwendete VPN-App, die von Ihrem VPN-Anbieter bereitgestellt wird.
- **Geben Sie Schlüssel-Wert-Paare für die benutzerdefinierten VPN-Attribute Ihrer Organisation ein:** Fügen Sie **Schlüssel** und **Werte** zum Anpassen der VPN-Verbindung hinzu, oder importieren Sie sie. Denken Sie daran, dass diese Werte in der Regel von Ihrem VPN-Anbieter bereitgestellt werden.

## <a name="automatic-vpn-settings"></a>Automatische VPN-Einstellungen

- **Pro-App-VPN**: Ermöglicht ein VPN pro App. VPN-Verbindungen können automatisch ausgelöst werden, wenn bestimmte Apps geöffnet sind. Apps lassen sich auch diesem VPN-Profil zuweisen. Weitere Informationen finden Sie in den [Anweisungen zum Einrichten des Pro-App-VPN für iOS-Geräte](vpn-setting-configure-per-app.md).
  - **Anbietertyp**: Nur für „Pulse Secure“ und „Benutzerdefiniertes VPN“ verfügbar.
  - Wenn Sie **Pro-App-VPN**-Profile für iOS mit Pulse Secure oder einem benutzerdefinierten VPN verwenden, können Sie das Tunneln entweder auf App-Ebene (app-proxy) oder auf Paketebene (packet-tunnel) nutzen. Legen Sie für Tunneln auf App-Ebene den Wert **ProviderType** auf **app-proxy** oder für Tunneln auf Paketebene auf **packet-tunnel** fest. Wenn Sie sich nicht sicher sind, welcher Wert benutzt werden soll, lesen Sie dies in der Dokumentation Ihres VPN-Anbieters nach.
  - **Safari URLs, die dieses VPN auslösen**: Fügen Sie mindestens eine Website-URL hinzu. Wenn diese URLs mit dem Safari-Browser auf dem Gerät aufgerufen werden, wird die VPN-Verbindung automatisch aufgebaut.

- **Bedarfsgesteuertes VPN:** Konfigurieren Sie bedingte Regeln, die steuern, wann die VPN-Verbindung gestartet wird. Erstellen Sie beispielsweise eine Bedingung, in der die VPN-Verbindung nur verwendet wird, wenn ein Gerät nicht mit einem WLAN des Unternehmens verbunden ist. Erstellen Sie alternativ eine Bedingung, in der die VPN-Verbindung nicht initiiert wird, wenn ein Gerät nicht auf eine eingegebene DNS-Suchdomäne zugreifen kann.

  - **SSIDs oder DNS-Suchdomänen:** Wählen Sie aus, ob diese Bedingung **SSIDs** des Drahtlosnetzwerks oder **DNS-Suchdomänen** verwenden soll. Klicken Sie auf **Hinzufügen**, um SSIDs oder Suchdomänen zu konfigurieren.
  - **URL-Zeichenfolgentest:** Optional. Geben Sie eine URL ein, die die Regel als Test verwenden soll. Wenn das Gerät mit diesem Profil auf diese URL ohne Umleitung zugreift, wird die VPN-Verbindung initiiert. Und das Gerät wird mit der Ziel-URL verbunden. Der Standort des URL-Zeichenfolgentests wird dem Benutzer nicht angezeigt. Ein Beispiel für einen URL-Zeichenfolgentest ist die Adresse eines Überwachungswebservers, der die Gerätekonformität prüft, bevor die VPN-Verbindung hergestellt wird. Eine andere Möglichkeit besteht darin, mit der URL zu testen, ob das VPN eine Verbindung mit einem Standort herstellen kann, bevor das Gerät über das VPN mit der Ziel-URL verbunden wird.
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

## <a name="next-step"></a>Nächster Schritt
[Erstellen von VPN-Profilen in Intune](vpn-settings-configure.md)  
