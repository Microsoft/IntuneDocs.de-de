---
title: 'Anzeigen der VPN-Einstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: "Erfahren Sie mehr über die verfügbaren VPN-Einstellungen in Microsoft Intune, erhalten Sie Informationen zu deren Verwendungs- und Funktionsweise, einschließlich Datenverkehrsregeln, bedingtem Zugriff und DNS- sowie Proxyeinstellungen für Windows 10- und Windows Holographic for Business-Geräte."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 1c1ed2946782f92313aacec05a65a80b2704ddaa
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>Informationen zu VPN-Einstellungen in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Sie können VPN-Verbindungen mit Intune konfigurieren. In diesem Artikel werden diese Einstellungen, die Datenverkehrsregeln, der bedingte Zugriff und DNS- sowie Proxyeinstellungen erläutert.

Diese Einstellungen gelten für:

- Windows 10-Geräte
- Windows Holographic for Business-Geräte

Abhängig von den ausgewählten Einstellungen können nicht alle der aufgeführten Werte konfiguriert werden.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

- **Verbindungsname**: Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Server**: Fügen Sie mindestens einen VPN-Server hinzu, mit dem Geräte eine Verbindung herstellen.
  - **Hinzufügen**: Öffnet die Option **Zeile hinzufügen**, in die Sie folgende Informationen eingeben:
    - **Beschreibung**: Geben Sie einen beschreibenden Namen für den Server ein, z.B. **Contoso-VPN-Server**.
    - **IP-Adresse oder FQDN**: Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen, z.B. **192.168.1.1** oder **vpn.contoso.com**.
    - **Standardserver**: Aktiviert diesen Server als Standardserver, über den Geräte die Verbindung herstellen. Legen Sie nur einen Server als Standard fest.
  - **Importieren**: Suchen Sie nach einer Datei, die eine durch Trennzeichen getrennte Liste von Servern im Format „Beschreibung, IP-Adresse oder FQDN, Standardserver“ enthält. Klicken Sie auf **OK**, um diese Server in die Liste **Server** zu importieren.
  - **Exportieren**: Exportiert die Liste der Server in eine CSV-Datei (Comma-Separated Values, durch Trennzeichen getrennte Werte).

**Verbindungstyp**: Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:

- **Automatisch**
- **Check Point Capsule VPN**
- **Citrix-VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**Anmeldegruppe oder Domäne** (nur SonicWall Mobile Connect): Diese Eigenschaft kann nicht im VPN-Profil festgelegt werden. Stattdessen analysiert Mobile Connect diesen Wert, wenn der Benutzername und die Domäne im Format `username@domain` oder `DOMAIN\username` eingegeben werden.

**Benutzerdefiniertes XML**/**EAP-XML**: Geben Sie benutzerdefinierte XML-Befehle zum Konfigurieren der VPN-Verbindung ein.

**Beispiel für Pulse Secure:**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Beispiel für CheckPoint Mobile VPN:**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Beispiel für SonicWall Mobile Connect:**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Beispiel für F5 Edge Client:**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Weitere Informationen zum Erstellen von benutzerdefinierten XML-Befehlen finden Sie in der VPN-Dokumentation des jeweiligen Herstellers.

Weitere Informationen zum Erstellen von benutzerdefinierten EAP-XML finden Sie unter [EAP configuration (EAP-Konfiguration)](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

**Tunneling teilen**: **Aktivieren** oder **deaktivieren** Sie diese Option, damit die Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Zum Beispiel verwendet ein Benutzer in einem Hotel die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, das Standardnetzwerk des Hotels jedoch für normales Webbrowsen.
- **Tunnelingrouten für diese VPN-Verbindung teilen**: Fügen Sie optionale Routen für VPN-Drittanbieter hinzu. Geben Sie ein Zielpräfix und eine Präfixgröße für jede Route ein.

## <a name="apps-and-traffic-rules"></a>Regeln für Apps und Datenverkehr

**VPN-Verbindung auf diese Apps beschränken**: Aktivieren Sie diese Einstellung, wenn nur die angegebenen Apps die VPN-Verbindung verwenden sollen.
**Zugeordnete Apps:** Geben Sie eine Liste von Apps ein, die automatisch die VPN-Verbindung verwenden. Der Typ der App bestimmt den App-Bezeichner. Geben Sie für eine universelle App den Paketfamiliennamen ein. Geben Sie für eine Desktop-App den Dateipfad der App ein.

>[!IMPORTANT]
>Es wird empfohlen, alle App-Listen schützen, die für Pro-App-VPNs erstellt sind. Wenn ein nicht autorisierter Benutzer die Liste ändert, und Sie sie in die Liste der Apps für Pro-App-VPNs importieren, autorisieren Sie damit möglicherweise den VPN-Zugriff auf Apps, auf die nicht zugegriffen werden soll. Eine Möglichkeit, App-Listen zu sichern, ist die Verwendung einer Zugriffssteuerungsliste (Access Control List, ACL).

**Regeln für den Netzwerkdatenverkehr für diese VPN-Verbindung**: Wählen Sie die Protokolle, die lokalen Ports und die Remoteports sowie die Adressbereiche aus, die für die VPN-Verbindung aktiviert werden sollen. Wenn Sie keine Regel für den Netzwerkdatenverkehr erstellen, werden alle Protokolle, Ports und Adressbereiche aktiviert. Nachdem Sie eine Regel erstellt haben, werden nur die in dieser Regel festgelegten Protokolle, Ports und Adressbereiche von der VPN-Verbindung verwendet.

## <a name="conditional-access"></a>Bedingter Zugriff

**Bedingter Zugriff für diese VPN-Verbindung**: Aktiviert den Gerätekonformitätsflow vom Client. Wenn aktiviert, versucht der VPN-Client, mit Azure AD zu kommunizieren, um ein Zertifikat für die Authentifizierung abzurufen. Der VPN sollte für die Zertifikatauthentifizierung eingerichtet sein, und der VPN-Server muss dem Server vertrauen, der von Azure Active Directory zurückgegeben wird.

**Einmaliges Anmelden (Single Sign-On, SSO) mit alternativem Zertifikat**: Verwenden Sie aus Gründen der Gerätekonformität ein anderes Zertifikat als das VPN-Authentifizierungszertifikat für die Kerberos-Authentifizierung. Geben Sie das Zertifikat mit den folgenden Einstellungen ein:

- **Erweiterte Schlüsselverwendung**: Name der erweiterten Schlüsselverwendung (Extended Key Usage, EKU)
- **Objektbezeichner**: Objektbezeichner für die EKU
- **Ausstellerhash**: Fingerabdruck des SSO-Zertifikats

## <a name="dns-settings"></a>DNS-Einstellungen

**DNS-Namen und -Server für diese VPN-Verbindung**: Wählen Sie die DNS-Server aus, die von der VPN-Verbindung verwendet werden, nachdem die Verbindung hergestellt wurde.
Geben Sie für jeden Server Folgendes an:
- **DNS-Name**
- **DNS-Server**
- **Proxy**

## <a name="proxy-settings"></a>Proxyeinstellungen

- **Proxyeinstellungen automatisch erkennen**: Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, wählen Sie aus, ob Geräte die in der Lage sein sollen, Verbindungseinstellungen automatisch zu erkennen.
- **Automatisches Konfigurationsskript**: Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** ein, die die Konfigurationsdatei enthält, z.B. `http://proxy.contoso.com`.
- **Proxyserver verwenden**: Aktivieren Sie diese Option, um die Einstellungen des Proxyservers manuell einzugeben.
  - **Adresse**: Geben Sie die Adresse des Proxyservers (als IP-Adresse) ein.
  - **Portnummer**: Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.
- **Proxy für lokale Adressen umgehen**: Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, aktivieren Sie diese Option, wenn der Proxyserver nicht für von Ihnen angegebene lokale Adressen verwendet werden soll.
