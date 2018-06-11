---
title: 'Konfigurieren der Windows 10-VPN-Einstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erfahren Sie mehr über die verfügbaren VPN-Einstellungen in Microsoft Intune, erhalten Sie Informationen zu deren Verwendungs- und Funktionsweise, einschließlich Datenverkehrsregeln, bedingtem Zugriff und DNS- sowie Proxyeinstellungen für Windows 10- und Windows Holographic for Business-Geräte.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 61310f5baa64c43d2e818df6c61a36d232922c1c
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744736"
---
# <a name="windows-10-vpn-settings-in-intune"></a>Windows 10-VPN-Einstellungen in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können VPN-Verbindungen mit Intune konfigurieren. In diesem Artikel werden diese Einstellungen, die Datenverkehrsregeln, der bedingte Zugriff und DNS- sowie Proxyeinstellungen erläutert.

Diese Einstellungen gelten für:

- Windows 10-Geräte
- Windows Holographic for Business-Geräte

Abhängig von den ausgewählten Einstellungen können nicht alle der aufgeführten Werte konfiguriert werden.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

- **Verbindungsname**: Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Server**: Fügen Sie mindestens einen VPN-Server hinzu, mit dem Geräte eine Verbindung herstellen. Wenn Sie einen Server hinzufügen, geben Sie folgende Informationen ein:
  - **Beschreibung**: Geben Sie einen beschreibenden Namen für den Server ein, z.B. **Contoso-VPN-Server**.
  - **IP-Adresse oder FQDN**: Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen, z.B. **192.168.1.1** oder **vpn.contoso.com**.
  - **Standardserver**: Aktiviert diesen Server als Standardserver, über den Geräte die Verbindung herstellen. Legen Sie nur einen Server als Standard fest.
  - **Importieren**: Suchen Sie nach einer Datei, die eine durch Trennzeichen getrennte Liste von Servern im Format „Beschreibung, IP-Adresse oder FQDN, Standardserver“ enthält. Wählen Sie **OK** aus, um diese Server in die Liste **Server** zu importieren.
  - **Exportieren**: Exportiert die Liste der Server in eine CSV-Datei (Comma-Separated Values, durch Trennzeichen getrennte Werte).

- **Verbindungstyp**: Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automatisch**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Wenn Sie einen VPN-Verbindungstyp auswählen, werden Sie möglicherweise aufgefordert, folgende Einstellungen vorzunehmen:  
    - **Always On**: Aktivieren, um automatisch die VPN-Verbindung herzustellen, wenn Folgendes geschieht: 
      - Benutzer melden sich an ihren Geräten an.
      - Das Netzwerk auf dem Gerät ändert sich.
      - Der Bildschirm wird auf dem Gerät wieder eingeschaltet, nachdem er ausgeschaltet war. 

    - **Authentifizierungsmethode**: Wählen Sie aus, wie Benutzer sich bei dem VPN-Server authentifizieren sollen. Die Verwendung von **Zertifikaten** bietet erweiterte Funktionen, z.B. berührungslose Authentifizierung, bedarfsgesteuertes VPN und Pro-App-VPN.
    - **Anmeldeinformationen bei jeder Anmeldung speichern**: Wählen Sie das Zwischenspeichern von Anmeldeinformationen für die Authentifizierung aus.
    - **Benutzerdefiniertes XML**: Geben Sie benutzerdefinierte XML-Befehle zum Konfigurieren der VPN-Verbindung ein.
    - **EAP-XML**: Geben Sie EAP-XML-Befehle zum Konfigurieren der VPN-Verbindung ein.

#### <a name="pulse-secure-example"></a>Pulse Secure-Beispiel

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>F5 Edge Client-Beispiel

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>SonicWall Mobile Connect-Beispiel
**Anmeldegruppe oder Domäne**: Diese Eigenschaft kann nicht im VPN-Profil festgelegt werden. Stattdessen analysiert Mobile Connect diesen Wert, wenn der Benutzername und die Domäne im Format `username@domain` oder `DOMAIN\username` eingegeben werden.

Beispiel:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>CheckPoint Mobile VPN-Beispiel

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>Schreiben von benutzerdefiniertem XML-Code
Weitere Informationen zum Erstellen von benutzerdefinierten XML-Befehlen finden Sie in der VPN-Dokumentation des jeweiligen Herstellers.

Weitere Informationen zum Erstellen von benutzerdefinierten EAP-XML finden Sie unter [EAP configuration (EAP-Konfiguration)](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Regeln für Apps und Datenverkehr

- **Diesem VPN WIP oder Apps zuordnen**: Aktivieren Sie diese Einstellung, wenn nur die angegebenen Apps die VPN-Verbindung verwenden sollen. Folgende Optionen sind verfügbar:

  - **Dieser Verbindung WIP zuordnen**: Geben Sie eine **WIP-Domäne für diese Verbindung** ein.
  - **Apps dieser Verbindung zuordnen**: Sie können die **VPN-Verbindung auf diese Apps beschränken** und dann **Zugeordnete Apps** hinzufügen. Die von Ihnen eingegebenen Apps verwenden automatisch die VPN-Verbindung. Der Typ der App bestimmt den App-Bezeichner. Geben Sie für eine universelle App den Paketfamiliennamen ein. Geben Sie für eine Desktop-App den Dateipfad der App ein.
  >[!IMPORTANT]
  >Es wird empfohlen, alle App-Listen schützen, die für Pro-App-VPNs erstellt sind. Wenn ein nicht autorisierter Benutzer die Liste ändert, und Sie sie in die Liste der Apps für Pro-App-VPNs importieren, autorisieren Sie damit möglicherweise den VPN-Zugriff auf Apps, auf die nicht zugegriffen werden soll. Eine Möglichkeit, App-Listen zu sichern, ist die Verwendung einer Zugriffssteuerungsliste (Access Control List, ACL).

- **Regeln für den Netzwerkdatenverkehr für diese VPN-Verbindung**: Wählen Sie die Protokolle, die lokalen Ports und die Remoteports sowie die Adressbereiche aus, die für die VPN-Verbindung aktiviert werden sollen. Wenn Sie keine Regel für den Netzwerkdatenverkehr erstellen, werden alle Protokolle, Ports und Adressbereiche aktiviert. Nachdem Sie eine Regel erstellt haben, werden nur die in dieser Regel festgelegten Protokolle, Ports und Adressbereiche von der VPN-Verbindung verwendet.

## <a name="conditional-access"></a>Bedingter Zugriff

- **Bedingter Zugriff für diese VPN-Verbindung**: Aktiviert den Gerätekonformitätsflow vom Client. Wenn aktiviert, versucht der VPN-Client, mit Azure Active Directory (AD) zu kommunizieren, um ein Zertifikat für die Authentifizierung abzurufen. Der VPN sollte für die Zertifikatauthentifizierung eingerichtet sein, und der VPN-Server muss dem Server vertrauen, der von Azure AD zurückgegeben wird.

- **Einmaliges Anmelden (Single Sign-On, SSO) mit alternativem Zertifikat**: Verwenden Sie aus Gründen der Gerätekonformität ein anderes Zertifikat als das VPN-Authentifizierungszertifikat für die Kerberos-Authentifizierung. Geben Sie das Zertifikat mit den folgenden Einstellungen ein:

  - **Name**: Name für erweiterte Schlüsselverwendung (Extended Key Usage, EKU)
  - **Objektbezeichner**: Objektbezeichner für die EKU
  - **Ausstellerhash**: Fingerabdruck des SSO-Zertifikats

## <a name="dns-settings"></a>DNS-Einstellungen

**Domäne und Server für diese VPN-Verbindung**: Fügen Sie Domäne und DNS-Server für das zu verwendende VPN hinzu. Sie können die DNS-Server auswählen, die die VPN-Verbindung nach dem Herstellen der Verbindung verwendet. Geben Sie für jeden Server Folgendes an:
- **Domäne**
- **DNS-Server**
- **Proxy**

## <a name="proxy-settings"></a>Proxyeinstellungen

- **Automatisches Konfigurationsskript**: Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** ein, die die Konfigurationsdatei enthält, z.B. `http://proxy.contoso.com`.
- **Adresse**: Geben Sie die Adresse des Proxyservers ein, etwa eine IP-Adresse oder `vpn.contoso.com`.
- **Portnummer**: Geben Sie die von Ihrem Proxyserver verwendete TCP-Portnummer ein.
- **Proxy für lokale Adressen umgehen**: Wenn Sie keinen Proxyserver für lokale Adressen verwenden möchten, wählen Sie „Aktivieren“ aus. Diese Einstellung gilt, wenn der VPN-Server für die Verbindung einen Proxyserver benötigt.

## <a name="split-tunneling"></a>Getrenntes Tunneln

- **Tunneling teilen**: **Aktivieren** oder **deaktivieren** Sie diese Option, damit die Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Zum Beispiel verwendet ein Benutzer in einem Hotel die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, das Standardnetzwerk des Hotels jedoch für normales Webbrowsen.
- **Tunnelingrouten für diese VPN-Verbindung teilen**: Fügen Sie optionale Routen für VPN-Drittanbieter hinzu. Geben Sie ein Zielpräfix und eine Präfixgröße für jede Verbindung ein.
