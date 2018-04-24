---
title: WLAN-Verbindungen
description: Verwenden Sie WLAN-Profile, um Benutzern zu helfen, eine Verbindung mit Ihren WLAN-Netzwerken herzustellen.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5eebe251371d466421bfe936a1f991c988e490b0
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configure-devices-to-connect-to-your-corporate-wi-fi-networks"></a>Konfigurieren von Geräten zur Herstellung einer Verbindung mit Ihren WLAN-Unternehmensnetzwerken

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Verwenden Sie WLAN-Profile in Microsoft Intune, um Benutzern und Geräten in Ihrer Organisation Einstellungen für Drahtlosnetzwerke bereitzustellen. Wenn Sie ein WLAN-Profil bereitstellen, erhalten Ihre Benutzer Zugriff auf Ihr Unternehmens-WLAN, ohne es selbst konfigurieren zu müssen.

Beispiel: Sie installieren ein neues WLAN-Netzwerk mit dem Namen **Contoso Wi-Fi** und möchten alle iOS-Geräte so einrichten, dass sie eine Verbindung mit diesem Netzwerk herstellen können. Gehen Sie dazu folgendermaßen vor:

![Zusammenfassung des WLAN-Profilprozesses](../media/wi-fi-process-diagram.png)

1.   Erstellen Sie ein WLAN-Profil mit den Einstellungen, die zum Verbinden mit dem Drahtlosnetzwerk **Contoso Wi-Fi** erforderlich sind.

2.   Stellen Sie das Profil der Gruppe von Benutzern mit iOS-Geräten bereit.

3.   Auf den Endgeräten der Benutzer erscheint das Netzwerk **Contoso Wi-Fi** in der Liste der Drahtlosnetzwerke, und es kann bequem eine Verbindung zu diesem Netzwerk hergestellt werden.


## <a name="create-a-wi-fi-profile"></a>Erstellen eines WLAN-Profils

Sie können WLAN-Profile auf den folgenden Plattformen bereitstellen:

-   Android 4,0 und höher

-   Android for Work   

-   iOS 8.0 und höher

-   Mac OS X 10.9 und höher

Für Geräte mit Windows 8.1, Windows 10 Desktop oder mobilen Betriebssystemen können Sie ein WLAN-Konfigurationsprofil importieren, das zuvor in eine Datei exportiert wurde. Ausführliche Informationen finden Sie unter [Exportieren oder Importieren eines WLAN-Konfigurationsprofils für Windows-Geräte](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

1.  Wählen Sie in der [Microsoft Intune-Administratorkonsole](https://manage.microsoft.com) **Richtlinie** &gt; **Richtlinie hinzufügen** aus.

2.  Wählen Sie einen der folgenden Richtlinientypen aus, und wählen Sie dann die Option **Richtlinie erstellen**:

    -   WLAN-Profil (Android 4 und höher)

    -   WLAN-Profil (Android for Work)

    -   WLAN-Profil (iOS 8.0 und höher)

    -   WLAN-Profil (Mac OS X 10.9 und höher)


Es gibt keine empfohlenen Einstellungen für diesen Richtlinientyp. Sie müssen eine benutzerdefinierte Richtlinie erstellen.

3. Geben Sie den Namen und die Beschreibung für das Profil an.

4. Geben Sie die Werte der **Netzwerkverbindungen** an.
   - **SSID (Service Set Identifier)**: Wählen Sie diese Option aus, wenn für die Benutzer anstelle der SSID der Netzwerkname angezeigt werden soll.
   - **Verbinden, wenn das Netzwerk nicht seinen Namen überträgt (SSID)**: Wählen Sie diese Option aus, um Geräte mit dem Netzwerk zu verbinden, wenn es nicht in der Liste der Netzwerke angezeigt wird (weil es ausgeblendet ist und seinen Namen nicht sendet).

5. Konfigurieren Sie die **Sicherheitseinstellungen** für die ausgewählte Plattform. Die verfügbaren Einstellungen hängen von den Typen der Drahtlossicherheit ab, die Sie auswählen. Sie werden unter [Sicherheitseinstellungen](#security-settings) beschrieben.

6. Konfigurieren Sie **Proxyeinstellungen** (nur iOS und Mac OS X).


   |                              Name der Einstellung                              |                                                                                                                                Weitere Informationen                                                                                                                                 |                                            Verwendung                                            |
   |------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
   |       <strong>Proxyeinstellungen für diese WLAN-Verbindung</strong>        | Wählen Sie die Art der Proxyeinstellungen aus:<br /><br />-   <strong>Keine</strong> (Standard)<br />-   <strong>Manuell</strong>: Sie möchten die URL und die Portnummer des Proxyservers manuell angeben.<br />-   <strong>Automatisch</strong>: Sie möchten eine Konfigurationsdatei verwenden, um den Proxyserver zu konfigurieren. |                                              Immer                                               |
   | <strong>Proxyserveradresse</strong> und <strong>Portnummer</strong> |                                                                                                              Geben Sie die URL und die Portnummer des Proxyservers an.                                                                                                               |  Wenn <strong>Proxyeinstellungen für diese WLAN-Verbindung</strong> auf <strong>Manuell</strong> festgelegt wurde.   |
   |                   <strong>Proxyserver-URL</strong>                    |                                                                                                      Geben Sie die URL der Datei an, die die Proxyservereinstellungen enthält.                                                                                                       | Wenn <strong>Proxyeinstellungen für diese WLAN-Verbindung</strong> auf <strong>Automatisch</strong> festgelegt wurde. |


7. Speichern des WLAN-Profils

Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt. Informationen zur Bereitstellung des Profils finden Sie unter **Nächste Schritte**.

## <a name="export-or-import-a-wi-fi-configuration-profile-for-windows-devices"></a>Exportieren oder Importieren eines WLAN-Konfigurationsprofils für Windows-Geräte

Für Geräte mit Windows 8.1, Windows 10 Desktop oder mobilen Betriebssystemen können Sie ein WLAN-Konfigurationsprofil importieren, das zuvor in eine Datei exportiert wurde.

### <a name="export-a-wi-fi-profile"></a>Exportieren eines WLAN-Profils
In Windows können Sie mit dem Hilfsprogramm **netsh wlan** ein vorhandenes WLAN-Profil in eine XML-Datei exportieren, die von Intune gelesen werden kann. Führen Sie auf einem Windows-Computer, auf dem das erforderliche WLAN-Profil bereits installiert ist, die folgenden Schritte aus:

1.  Erstellen Sie einen lokalen Ordner für die exportierten WLAN-Profile. Erstellen Sie beispielsweise einen Ordner namens **C:\WiFi**.

2.  Öffnen Sie eine Eingabeaufforderung als Administrator.

3.  Führen Sie den Befehl `netsh wlan show profiles` aus, und notieren Sie den Namen des Profils, das Sie exportieren möchten.  In diesem Beispiel lautet der Profilname **WiFiName**.

4.  Führen Sie diesen Befehl aus: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Dadurch wird ein WLAN-Profil namens **Wi-Fi-WiFiName.xml** im Zielordner erstellt.

### <a name="import-a-wi-fi-profile"></a>Importieren eines WLAN-Profils
Verwenden Sie zum Importieren von WLAN-Einstellungen für die Bereitstellung an die benötigten Benutzer- und Gerätegruppen **WLAN-Importrichtlinie für Windows**.


1.  Klicken Sie in der [Microsoft Intune-Administratorkonsole](https://manage.microsoft.com) auf **Richtlinie** &gt; **Richtlinie hinzufügen**.

2.  Konfigurieren Sie eine Richtlinie vom Typ **Windows** &gt; **WLAN-Import (Windows 8.1 und später)**.

    Diese Richtlinie kann auf Geräte mit Windows 8.1, Windows 10 Desktop und mobile Betriebssysteme angewendet werden.

    Sie können nur eine *benutzerdefinierte* WLAN-Importrichtlinie für Windows erstellen und bereitstellen. Empfohlene Einstellungen sind nicht verfügbar.

3.  Geben Sie die folgenden allgemeinen Informationen für die WLAN-Importrichtlinie an:

    |Name der Einstellung|Weitere Informationen|
    |----------------|--------------------|
    |**Name**|Geben Sie einen eindeutigen Namen für das WLAN-Profil ein, um es in der Intune-Konsole identifizieren zu können.|
    |**Beschreibung**|Geben Sie eine Beschreibung des WLAN-Profils sowie weitere relevante Informationen ein, um es besser zuordnen zu können.|

4.  Geben Sie unter der Überschrift **Benutzerdefiniertes WLAN-Profil** die folgenden Werte ein:

    |Name der Einstellung|Weitere Informationen|
    |----------------|--------------------|
    |**Konfigurationsprofildatei**|Wählen Sie **Importieren**, um die XML-Datei mit den WLAN-Profileinstellungen auszuwählen, die Sie in Intune importieren möchten.|
    |**Name des benutzerdefinierten Konfigurationsprofils (wird Benutzern angezeigt)**|Wählen Sie aus, wie der Name des WLAN-Profils auf dem Gerät der Benutzer angezeigt werden soll.|
    |**Details zum Konfigurationsprofil**|Wählen Sie aus, wie der XML-Code für das ausgewählte Konfigurationsprofil angezeigt werden soll.|

5.  Wählen Sie anschließend die Option **Richtlinie speichern**.

6.  Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt.

## <a name="deploy-the-profile"></a>Bereitstellen des Profils

Ein Profil ist eine Art Richtlinie, verwenden Sie also den Arbeitsbereich **Richtlinien**, um sie bereitzustellen.

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und wählen Sie dann **Bereitstellung verwalten** aus.

2.  Führen Sie im Dialogfeld **Bereitstellung verwalten** folgende Schritte aus:

    -   **Bereitstellen der Richtlinie**: Wählen Sie mindestens eine Gruppe aus, für die Sie die Richtlinie bereitstellen möchten. Wählen Sie anschließend **Hinzufügen** &gt; **OK**.

    -   **Dialogfeld schließen, ohne die Richtlinie bereitzustellen:** Klicken Sie auf **Abbrechen**.


Die Seite **Übersicht** des Arbeitsbereichs **Richtlinie** zeigt Probleme mit der Richtlinie an, die Ihre Aufmerksamkeit erfordern. Darüber hinaus wird eine Statusübersicht im Arbeitsbereich „Dashboard“ angezeigt.

## <a name="security-settings"></a>Sicherheitseinstellungen
Diese Tabellen enthalten die Details für die Sicherheitseinstellungen, die für Android-, iOS- und Mac OS X-WLAN-Profile verfügbar sind.

### <a name="security-settings-for-android-devices"></a>Sicherheitseinstellungen für Android-Geräte

  |Name der Einstellung|Weitere Informationen|Verwendung|
|----------------|--------------------|-------------|
|**Sicherheitstyp**|Wählen Sie das Sicherheitsprotokoll für das Drahtlosnetzwerk:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Keine Authentifizierung (Offen)**, wenn das Netzwerk nicht gesichert ist.|Immer|
|**EAP-Typ**|Wählen Sie die den EAP-Typ (Extensible Authentication-Protokoll) zur Authentifizierung von gesicherten Drahtlosverbindungen:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Bei Auswahl des Sicherheitstyp **WPA-Enterprise/WPA2-Enterprise**.|
|**Stammzertifikate für die Serverüberprüfung auswählen**|Klicken Sie auf **Auswählen**, und wählen Sie dann das vertrauenswürdige Stammzertifikatprofil aus, das Sie zur Authentifizierung der Verbindung verwendet haben. Weitere Informationen zum Verwenden eines vertrauenswürdigen Stammzertifikatprofils in Intune finden Sie unter [Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen](secure-resource-access-with-certificate-profiles.md).|Bei Auswahl einer beliebigen Einstellung für **EAP-Typs**.|
|**Authentifizierungsmethode**|Wählen Sie die Authentifizierungsmethode für die Verbindung aus:<br /><br />-   **Zertifikate** zur Angabe des Clientzertifikats<br />-   **Benutzername und Kennwort** zur Angabe einer anderen Authentifizierungsmethode|Bei **PEAP** oder **EAP-TTLS** als **EAP-Typ**.|
|**EAP-fremde Authentifizierungsmethode auswählen (innere Identität)**|Wählen Sie, wie Sie die Verbindung authentifizieren möchten:<br /><br />-   **Keine**<br />-   **Unverschlüsseltes Kennwort (PAP)**<br />-   **Challenge Handshake Authentication-Protokoll (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP, Version 2 (MS-CHAP v2)**<br /><br />Die verfügbaren Optionen richten sich nach dem ausgewählten EAP-Typ.|Die **Authentifizierungsmethode** ist **Benutzername und Kennwort**.|
|**Identitätsschutz aktivieren (äußere Identität)**|Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird anfänglich diese anonyme Identität gesendet. Die tatsächliche Identifizierung wird in einem sicheren Tunnel gesendet.|Bei Auswahl von **PEAP** oder **EAP-TTLS** als **EAP-Typ**.|
|**Clientzertifikat für die Clientauthentifizierung (Identitätszertifikat) auswählen**|Klicken Sie auf **Auswählen**, und wählen Sie dann das SCEP-Zertifikatprofil aus, das Sie zur Authentifizierung der Verbindung verwendet haben. Weitere Informationen zum Verwenden eines SCEP-Zertifikatprofils in Intune finden Sie unter [Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen](secure-resource-access-with-certificate-profiles.md).|Bei Auswahl des Sicherheitstyps **WPA-Enterprise/WPA2-Enterprise** und einer beliebigen Einstellung für **EAP-Typ**.|

### <a name="security-settings-for-ios-and-mac-os-x-devices"></a>Sicherheitseinstellungen für iOS und Mac OS X-Geräte

  |Name der Einstellung|Weitere Informationen|Verwendung|
|----------------|--------------------|-------------|
|**Sicherheitstyp**|Wählen Sie das Sicherheitsprotokoll für das Drahtlosnetzwerk:<br /><br />-   **WPA-Personal/WPA2-Personal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Keine Authentifizierung (Offen)**, wenn das Netzwerk nicht gesichert ist.|Immer|
|**EAP-Typ**|Wählen Sie die den EAP-Typ (Extensible Authentication-Protokoll) zur Authentifizierung von gesicherten Drahtlosverbindungen:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|Bei Auswahl des Sicherheitstyps **WPA-Enterprise/WPA2-Enterprise**.|
|**Namen der vertrauenswürdigen Serverzertifikate**|Wählen Sie das vertrauenswürdige Stammzertifikatprofil, das Sie zur Authentifizierung der Verbindung verwendet haben. Weitere Informationen zum Verwenden eines vertrauenswürdigen Stammzertifikatprofils in Intune finden Sie unter [Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen](secure-resource-access-with-certificate-profiles.md).|Bei Auswahl von **EAP-TLS**, **PEAP**, **EAP-TTLS** oder **EAP-FAST** als EAP-Typ.|
|**Protected Access Credential (PAC) verwenden**|Wählen Sie die Verwendung von geschützten Zugriffsanmeldeinformationen zum Herstellen eines authentifizierten Tunnels zwischen dem Client und dem Authentifizierungsserver. Eine vorhandene PAC-Datei wird ggf. verwendet.|Der **EAP-Typ** lautet **EAP-FAST**.|
|**PAC bereitstellen**|Richten Sie die PAC-Datei auf Ihren Geräten ein.<br /><br />Bei Verwendung dieser Option können Sie auch **PAC anonym bereitstellen** auswählen, damit die PAC-Datei ohne Authentifizierung des Servers bereitgestellt wird.|Bei Auswahl von **Geschützte Zugriffsanmeldeinformationen (PAC) verwenden**.|
|**Authentifizierungsmethode**|Wählen Sie die Authentifizierungsmethode für die Verbindung aus:<br /><br /><ul><li>**Zertifikate** zur Angabe des Clientzertifikats</li><li>**Benutzername und Kennwort** für eine der folgenden EAP-fremden Methoden zur Authentifizierung (auch als innere Identität bekannt):<br /><br /><ul><li>**Keine**</li><li>**Unverschlüsseltes Kennwort (PAP)**</li><li>**Challenge Handshake Authentication-Protokoll (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP, Version 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|Bei Auswahl von **PEAP** oder **EAP-TTLS** als **EAP-Typ**.|
|**Clientzertifikat für die Clientauthentifizierung (Identitätszertifikat) auswählen**|Wählen Sie das SCEP-Zertifikatprofil, dass Sie zur Authentifizierung der Verbindung verwendet haben. Weitere Informationen zum Verwenden eines SCEP-Zertifikatprofils in Intune finden Sie unter [Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen](secure-resource-access-with-certificate-profiles.md).|Bei Auswahl des Sicherheitstyps **WPA-Enterprise/WPA2-Enterprise** und Festlegung von **EAP-TLS**, **PEAP** oder **EAP-TTLS** als **EAP-Typ**.|
|**Identitätsschutz aktivieren (äußere Identität)**|Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein.<br /><br />Während der Authentifizierung wird anfänglich diese anonyme Identität gesendet. Die tatsächliche Identifizierung wird in einem sicheren Tunnel gesendet.|Bei Festlegung von **PEAP**, **EAP-TTLS** oder **EAP-FAST** als **EAP-Typ**.|


### <a name="see-also"></a>Siehe auch
Unter [WLAN-Profil mit vorinstalliertem Schlüssel](pre-shared-key-wi-fi-profile.md) erfahren Sie, wie Sie ein WLAN-Profil mit einem vorinstallierten Schlüssel erstellen.
