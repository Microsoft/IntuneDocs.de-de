---
title: 'Windows 10-VPN-Einstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erfahren Sie mehr über die verfügbaren VPN-Einstellungen in Microsoft Intune, erhalten Sie Informationen zu deren Verwendungs- und Funktionsweise, einschließlich Datenverkehrsregeln, bedingtem Zugriff und DNS- sowie Proxyeinstellungen für Windows 10 und Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e38d5e68e79facfd270de64c79708b74aa460189
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838188"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Geräteeinstellungen für Windows 10 und Windows Holographic zum Hinzuzufügen von VPN-Verbindungen mithilfe von Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können VPN-Verbindungen für Geräte mithilfe von Microsoft Intune hinzufügen und konfigurieren. In diesem Artikel werden häufig verwendete Einstellungen und Features für das Erstellen von virtuellen privaten Netzwerken (VPNs) aufgeführt und erläutert. Diese VPN-Einstellungen und Features werden in den Gerätekonfigurationsprofilen in Intune verwendet, die über Push auf Geräte übertragen oder auf Geräten bereitgestellt werden. 

Im Rahmen unserer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) können Sie diese Einstellungen verwenden, um Features zuzulassen oder zu deaktivieren (unter anderem VPN-Anbieter, Always On, DNS und Proxys).

Diese Einstellungen gelten nur für Geräte, auf denen Folgendes ausgeführt wird:

- Windows 10
- Windows Holographic for Business

Abhängig von den ausgewählten Einstellungen können nicht alle der aufgeführten Werte konfiguriert werden.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein VPN-Gerätekonfigurationsprofil.](vpn-settings-configure.md)

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Server:** Fügen Sie mindestens einen VPN-Server hinzu, mit dem Geräte eine Verbindung herstellen können. Wenn Sie einen Server hinzufügen, geben Sie folgende Informationen ein:
  - **Beschreibung**: Geben Sie einen beschreibenden Namen für den Server ein, z. B. **Contoso-VPN-Server**.
  - **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen, z. B. **192.168.1.1** oder **vpn.contoso.com**.
  - **Standardserver:** Aktiviert diesen Server als Standardserver, über den Geräte die Verbindung herstellen. Legen Sie nur einen Server als Standard fest.
  - **Importieren:** Suchen Sie nach einer Datei, die eine durch Trennzeichen getrennte Liste von Servern im Format „Beschreibung, IP-Adresse oder FQDN, Standardserver“ enthält. Wählen Sie **OK** aus, um diese Server in die Liste **Server** zu importieren.
  - **Exportieren:** Exportiert die Liste der Server in eine CSV-Datei (Comma-Separated Values, durch Trennzeichen getrennte Werte).

- **IP-Adressen beim internen DNS registrieren:** Wählen Sie **Aktivieren** aus, um das Windows 10-VPN-Profil zum dynamischen Registrieren der IP-Adressen zu konfigurieren, die der VPN-Schnittstelle mit dem internen DNS zugewiesen sind. Wenn Sie **Deaktivieren** auswählen, werden die IP-Adressen nicht dynamisch registriert.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:

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
    - **Immer aktiv:** **Aktivieren** Sie diese Option, um die VPN-Verbindung automatisch bei folgenden Ereignissen herzustellen: 
      - Benutzer melden sich an ihren Geräten an.
      - Das Netzwerk auf dem Gerät ändert sich.
      - Der Bildschirm wird auf dem Gerät wieder eingeschaltet, nachdem er ausgeschaltet war. 

    - **Authentifizierungsmethode**: Wählen Sie aus, wie Benutzer sich beim VPN-Server authentifizieren sollen. Die Verwendung von **Zertifikaten** bietet erweiterte Features, z.B. Authentifizierung ohne Benutzereingriff, bedarfsgesteuertes VPN und Pro-App-VPN.
    - **Anmeldeinformationen bei jeder Anmeldung speichern:** Wählen Sie diese Option aus, wenn die Anmeldeinformationen für die Authentifizierung zwischengespeichert werden sollen.
    - **Benutzerdefiniertes XML:** Geben Sie benutzerdefinierte XML-Befehle zum Konfigurieren der VPN-Verbindung an.
    - **EAP-XML:** Geben Sie EAP-XML-Befehle zum Konfigurieren der VPN-Verbindung ein.

#### <a name="pulse-secure-example"></a>Pulse Secure-Beispiel

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>F5 Edge Client-Beispiel

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>SonicWall Mobile Connect-Beispiel
**Anmeldegruppe oder -domäne:** Diese Eigenschaft kann nicht im VPN-Profil festgelegt werden. Stattdessen analysiert Mobile Connect diesen Wert, wenn der Benutzername und die Domäne im Format `username@domain` oder `DOMAIN\username` eingegeben werden.

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

- **Diesem VPN WIP oder Apps zuordnen:** Aktivieren Sie diese Einstellung, wenn nur die angegebenen Apps die VPN-Verbindung verwenden sollen. Folgende Optionen sind verfügbar:

  - **Dieser Verbindung WIP zuordnen:** Geben Sie eine **WIP-Domäne für diese Verbindung** ein.
  - **Apps dieser Verbindung zuordnen:** Sie können die **VPN-Verbindung auf diese Apps beschränken** und dann **Zugeordnete Apps** hinzufügen. Die von Ihnen eingegebenen Apps verwenden automatisch die VPN-Verbindung. Der Typ der App bestimmt den App-Bezeichner. Geben Sie für eine universelle App den Paketfamiliennamen ein. Geben Sie für eine Desktop-App den Dateipfad der App ein.
  >[!IMPORTANT]
  >Es wird empfohlen, alle App-Listen schützen, die für Pro-App-VPNs erstellt sind. Wenn ein nicht autorisierter Benutzer die Liste ändert, und Sie sie in die Liste der Apps für Pro-App-VPNs importieren, autorisieren Sie damit möglicherweise den VPN-Zugriff auf Apps, auf die nicht zugegriffen werden soll. Eine Möglichkeit, App-Listen zu sichern, ist die Verwendung einer Zugriffssteuerungsliste (Access Control List, ACL).

- **Regeln für den Netzwerkdatenverkehr für diese VPN-Verbindung:** Wählen Sie die Protokolle, die lokalen und Remoteports sowie die Adressbereiche aus, die für die VPN-Verbindung aktiviert werden sollen. Wenn Sie keine Regel für den Netzwerkdatenverkehr erstellen, werden alle Protokolle, Ports und Adressbereiche aktiviert. Nachdem Sie eine Regel erstellt haben, werden nur die in dieser Regel festgelegten Protokolle, Ports und Adressbereiche von der VPN-Verbindung verwendet.

## <a name="conditional-access"></a>Bedingter Zugriff

- **Bedingter Zugriff für diese VPN-Verbindung:** Über diese Option wird der Gerätekonformitätsflow über den Client aktiviert. Wenn aktiviert, kommuniziert der VPN-Client mit Azure Active Directory (AD), um ein Zertifikat für die Authentifizierung abzurufen. Der VPN sollte für die Zertifikatauthentifizierung eingerichtet sein, und der VPN-Server muss dem Server vertrauen, der von Azure AD zurückgegeben wird.

- **Einmaliges Anmelden (SSO) mit alternativem Zertifikat:** Verwenden Sie aus Gründen der Gerätekonformität ein anderes Zertifikat als das VPN-Authentifizierungszertifikat für die Kerberos-Authentifizierung. Geben Sie das Zertifikat mit den folgenden Einstellungen ein:

  - **Name**: Der Name für die erweiterte Schlüsselverwendung (Extended Key Usage, EKU)
  - **Objektbezeichner:** Der Objektbezeichner für die erweiterte Schlüsselverwendung
  - **Ausstellerhash:** Fingerabdruck des SSO-Zertifikats

## <a name="dns-settings"></a>DNS-Einstellungen

- **DNS-Suffixsuchliste:** Geben Sie unter **DNS-Suffixe** ein DNS-Suffix ein, und klicken Sie auf **Hinzufügen**. Sie können mehrere Suffixe hinzufügen.

  Wenn Sie DNS-Suffixe verwenden, können Sie nach einer Netzwerkressource mithilfe ihres Kurznamens anstelle des vollqualifizierten Domänennamens (Fully Qualified Domain Name, FQDN) suchen. Bei der Suche über den Kurznamen wird das Suffix automatisch vom DNS-Server ermittelt. Beispielsweise befindet sich `utah.contoso.com` in der DNS-Suffixliste. Pingen Sie `DEV-comp`. In diesem Szenario wird es in `DEV-comp.utah.contoso.com` aufgelöst.

  DNS-Suffixe werden in der aufgeführten Reihenfolge aufgelöst, wobei die Reihenfolge geändert werden kann. Zum Beispiel sind `colorado.contoso.com` und `utah.contoso.com` in der DNS-Suffixliste enthalten, und beide weisen eine Ressource namens `DEV-comp` auf. Da `colorado.contoso.com` an erster Stelle in der Liste steht, wird es als `DEV-comp.colorado.contoso.com` aufgelöst.
  
  Um die Reihenfolge zu ändern, klicken Sie auf die Punkte links neben dem DNS-Suffix, und ziehen Sie das Suffix dann nach oben:

  ![Auswählen der drei Punkte, Klicken und Ziehen zum Verschieben des DNS-Suffixes](./media/vpn-settings-windows10-move-dns-suffix.png)

- **Name Resolution Policy table (NRPT) rules** (Regeln der Richtlinientabelle für die Namensauflösung (NRPT)): Über die Regeln der Richtlinientabelle für die Namensauflösung (Name Resolution Policy Table, NRPT) wird definiert, wie ein DNS Namen auflöst, wenn eine Verbindung mit dem VPN hergestellt wird. Wenn eine VPN-Verbindung hergestellt wurde, können Sie festlegen, welche DNS-Server von der VPN-Verbindung verwendet werden sollen.

  Sie können Regeln zur Tabelle hinzufügen, die die Domäne, den DNS-Server, den Proxy oder andere Komponenten betreffen, um die eingegebene Domäne aufzulösen. Diese Regeln werden von der VPN-Verbindung verwendet, wenn Benutzer eine Verbindung mit den eingegebenen Domänen herstellen.

  Klicken Sie auf **Hinzufügen**, um eine neue Regel hinzuzufügen. Geben Sie für jeden Server Folgendes an:

  - **Domäne:** Geben Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) oder ein DNS-Suffix ein, um die Regel anzuwenden. Sie können die Eingabe mit einem Punkt beginnen, um ein DNS-Suffix festzulegen. Geben Sie beispielsweise `contoso.com` oder `.allcontososubdomains.com` ein.
  - **DNS-Server:** Geben Sie die IP-Adresse oder den DNS-Server ein, die bzw. der die Domäne auflöst. Geben Sie beispielsweise `10.0.0.3` oder `vpn.contoso.com` ein.
  - **Proxy:** Geben Sie den Webproxyserver ein, der die Domäne auflöst. Geben Sie beispielsweise `http://proxy.com` ein.
  - **Automatisch verbinden:** Wenn diese Option auf **Aktiviert** festgelegt ist, stellt das Gerät automatisch eine Verbindung mit dem VPN her, wenn ein Gerät eine Verbindung mit einer von Ihnen eingegebenen Domäne (z. B. `contoso.com`) herstellt. Wenn diese Option auf **Nicht konfiguriert** (Standardeinstellung) festgelegt ist, stellt das Gerät keine automatische Verbindung mit dem VPN her.
  - **Persistent:** Wenn diese Option auf **Aktiviert** festgelegt ist, verbleibt die Regel in der Richtlinientabelle für die Namensauflösung, bis sie manuell vom Gerät entfernt wird (auch wenn die Verbindung mit dem VPN getrennt wird). Wenn diese Option auf **Nicht konfiguriert** (Standardeinstellung) festgelegt ist, werden die NRPT-Regeln im VPN-Profil vom Gerät entfernt, wenn die Verbindung mit dem VPN getrennt wird.

## <a name="proxy-settings"></a>Proxyeinstellungen

- **Automatisches Konfigurationsskript:** Verwenden Sie eine Datei, um den Proxyserver zu konfigurieren. Geben Sie die **Proxyserver-URL** ein, die die Konfigurationsdatei enthält, z.B. `http://proxy.contoso.com`.
- **Adresse:** Geben Sie die Adresse des Proxyservers ein, z. B. eine IP-Adresse oder `vpn.contoso.com`.
- **Portnummer:** Geben Sie die von Ihrem Proxyserver verwendete TCP-Portnummer ein.
- **Proxy für lokale Adressen umgehen:** Wenn Sie keinen Proxyserver für lokale Adressen verwenden möchten, wählen Sie „Aktivieren“ aus. Diese Einstellung gilt, wenn der VPN-Server für die Verbindung einen Proxyserver benötigt.

## <a name="split-tunneling"></a>Getrenntes Tunneln

- **Getrenntes Tunneln:** Wählen Sie **Aktivieren** oder **Deaktivieren** für diese Option aus, damit die Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Zum Beispiel verwendet ein Benutzer in einem Hotel die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, das Standardnetzwerk des Hotels jedoch für normales Webbrowsen.
- **Tunnelingrouten für diese VPN-Verbindung teilen:** Mit dieser Option können Sie optionale Routen für VPN-Drittanbieter hinzufügen. Geben Sie ein Zielpräfix und eine Präfixgröße für jede Verbindung ein.

## <a name="trusted-network-detection"></a>Ermitteln von vertrauenswürdigen Netzwerken

**DNS-Suffixe für vertrauenswürdige Netzwerke:** Wenn der Benutzer bereits eine Verbindung mit einem vertrauenswürdigen Netzwerk hergestellt hat, können Sie verhindern, dass Geräte automatisch eine Verbindung mit einem anderen VPN herstellen.

Geben Sie unter **DNS-Suffixe** ein DNS-Suffix ein, das sie als vertrauenswürdig einstufen (z. B. contoso.com), und klicken Sie auf **Hinzufügen**. Sie können beliebig viele Suffixe hinzufügen.

Wenn ein Benutzer mit einem DNS-Suffix in der Liste verbunden ist, wird für diesen Benutzer keine automatische Verbindung mit einem anderen VPN hergestellt. Für den Benutzer wird weiterhin die von Ihnen eingegebene Liste der vertrauenswürdigen DNS-Suffixe verwendet. Das vertrauenswürdige Netzwerk wird weiter verwendet, auch wenn automatische Trigger festgelegt wurden.

Wenn der Benutzer beispielsweise bereits mit einem vertrauenswürdigen DNS-Suffix verbunden ist, werden folgende automatische Trigger ignoriert. Die DNS-Suffixe in der Liste setzen alle automatischen Trigger für Verbindungen außer Kraft, insbesondere die folgenden:

- Immer aktiv
- App-basierte Trigger
- Automatische DNS-Trigger

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Konfigurieren Sie die VPN-Einstellungen für [Android-](vpn-settings-android.md), [iOS-](vpn-settings-ios.md) und [macOS-Geräte](vpn-settings-macos.md).
