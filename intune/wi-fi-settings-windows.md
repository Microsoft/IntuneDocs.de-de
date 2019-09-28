---
title: WLAN-Einstellungen für Windows 10-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie in Microsoft Intune mithilfe der WLAN-Einstellungen für Geräte mit Windows 10 und höher WLAN-Konfigurationsprofile hinzufügen oder erstellen. Sie können Einstellungen für Basic- oder Enterprise-Profile konfigurieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/8/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 528819452accf4a7f17e54b3c05693dee5cab74f
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71239452"
---
# <a name="add-wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Hinzufügen von WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune

Sie können ein Profil mit bestimmten WLAN-Einstellungen erstellen und dieses dann auf Ihren Geräten mit Windows 10 und höher bereitstellen. Microsoft Intune bietet viele Features, darunter die Authentifizierung bei Ihrem Netzwerk mit einem vorinstallierten Schlüssel.

Dieser Artikel beschreibt diese Einstellungen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Geräteprofil.](device-profile-create.md)

## <a name="basic-profile"></a>Grundlegendes Profil

- **WLAN-Typ**: Wählen Sie **Grundlegend** aus. 

- **WLAN-Name (SSID)** : Abkürzung für Service Set Identifier. Dieser Wert entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der **Verbindungsname** angezeigt, den Sie konfiguriert haben.

- **Verbindungsname**: Geben Sie einen Anzeigenamen für diese WLAN-Verbindung ein. Der eingegebene Text ist der Name, der den Benutzern bei der Suche nach verfügbaren WLAN-Verbindungen auf ihren Geräten angezeigt wird.

- **Automatisch verbinden, wenn in Reichweite**: Wenn **Ja** festgelegt wird, verbinden sich Geräte automatisch, wenn sie sich im Empfangsbereich des Netzwerks befinden. Wenn **Nein** festgelegt wird, verbinden sich Geräte nicht automatisch.

  - **Verbindung mit bevorzugtem Netzwerk herstellen, sofern verfügbar**: Wählen Sie **Ja** aus, wenn sich Geräte im Empfangsbereich das bevorzugten Netzwerks mit diesem verbinden sollen. Wählen Sie **Nein** aus, wenn das WLAN-Netzwerk in diesem Konfigurationsprofil verwendet werden soll.

    Angenommen, Sie erstellen das WLAN-Netzwerk **ContosoCorp** und verwenden **ContosoCorp** im Konfigurationsprofil. Zusätzlich befindet sich das WLAN-Netzwerk **ContosoGuest** im Empfangsbereich des anderen Netzwerks. Wenn Ihre Unternehmensgeräte sich nun im Empfangsbereich befinden, sollen diese sich automatisch mit **ContosoCorp** verbinden. In diesem Szenario legen Sie die Eigenschaft **Verbindung mit bevorzugtem Netzwerk herstellen, sofern verfügbar** auf **Nein** fest.

  - **Verbindung mit diesem Netzwerk herstellen, auch wenn die SSID nicht übertragen wird**: Wählen Sie für das Konfigurationsprofil **Ja** aus, damit auch dann automatisch eine Verbindung zum Netzwerk hergestellt wird, wenn das Netzwerk ausgeblendet ist (d.h., die SSID nicht öffentlich übertragen wird). Wählen Sie **Nein** aus, wenn mit diesem Konfigurationsprofil keine Verbindung mit dem ausgeblendeten Netzwerk hergestellt werden soll.

- **Getaktetes Verbindungslimit:** Administratoren können bestimmen, wie der Datenverkehr des Netzwerks getaktet werden soll. Anwendungen können dann ihr Verhalten für Netzwerkdatenverkehr basierend auf dieser Einstellung anpassen. Folgende Optionen sind verfügbar:

  - **Uneingeschränkt:** Standard. Die Verbindung ist nicht getaktet und der Datenverkehr wird nicht eingeschränkt.
  - **Fest:** Verwenden Sie diese Option, wenn für das Netzwerk ein festes Limit für Datenverkehr festgelegt ist. Wenn dieses Limit erreicht ist, kann nicht mehr auf das Netzwerk zugegriffen werden.
  - **Variabel:** Verwenden Sie diese Option, wenn Netzwerkdatenverkehr pro Byte abgerechnet wird (Kosten pro Byte).

- **Sicherheitstyp für Drahtlosverbindung**: Geben Sie das Sicherheitsprotokoll an, mit dem Geräte in Ihrem Netzwerk authentifiziert werden. Folgende Optionen sind verfügbar:
  - **Offen (keine Authentifizierung):** Verwenden Sie diese Option nur, wenn das Netzwerk nicht gesichert ist.
  - **WPA/WPA2-Personal:** eine sicherere Option, die häufig für WLAN-Verbindungen verwendet wird. Wenn Sie mehr Sicherheit wünschen, können Sie auch ein Kennwort für einen vorinstallierten Schlüssel oder einen Netzwerkschlüssel angeben. 

    - **Vorinstallierter Schlüssel:** Optional. Diese Option wird angezeigt, wenn Sie **WPA/WPA2-Personal** als Sicherheitstyp auswählen. Wenn das Netzwerk Ihrer Organisation eingerichtet oder konfiguriert wird, wird auch ein Kennwort oder ein Netzwerkschlüssel konfiguriert. Geben Sie dieses Kennwort oder den Netzwerkschlüssel für den Wert des vorinstallierten Schlüssels ein. Geben Sie eine Zeichenfolge ein, die zwischen 8 und 64 Zeichen umfasst. Wenn Ihr Kennwort oder Netzwerkschlüssel 64 Zeichen umfasst, geben Sie Hexadezimalzeichen an.
    
      > [!NOTE]
      > Wenn Sie das WLAN-Profil speichern, wird der von Ihnen angegebene PSK-Wert aus Sicherheitsgründen nicht angezeigt. Als Grenzwert für den vorinstallierten Schlüssel wird weiterhin **Nicht konfiguriert** angezeigt, obwohl der PSK-Wert in dem Profil gespeichert ist. Wenn Sie den PSK-Wert ändern möchten, geben Sie einen neuen Schlüssel ein, und speichern Sie das Profil. Wenn Sie einen PSK-Wert speichern, bearbeiten Sie die Richtlinie, und lassen Sie das PSK-Feld leer. Dann wird der bereits vorhandene PSK-Wert weiter verwendet.
      
      > [!IMPORTANT]
      > Das PSK ist für alle Geräte, für die Sie das profule als Ziel haben, identisch. Wenn der Schlüssel kompromittiert ist, kann er von jedem Gerät zum Herstellen einer Verbindung mit dem WLAN-Netzwerk verwendet werden. Sorgen Sie für eine sichere Sicherheit Ihrer PSS.

- **Proxyeinstellungen für Unternehmen**: Wählen Sie die Proxyeinstellungen aus, die innerhalb Ihrer Organisation verwendet werden sollen. Folgende Optionen sind verfügbar:
  - **Keine**: Es sind keine Proxyeinstellungen konfiguriert.
  - **Manuell konfigurieren**: Geben Sie die **IP-Adresse des Proxyservers** and die zugehörige **Portnummer** ein.
  - **Automatisch konfigurieren**: Geben Sie die URL ein, die auf ein PAC-Skript (Proxy auto-configuration = automatische Proxykonfiguration) verweist. Geben Sie beispielsweise `http://proxy.contoso.com/proxy.pac` ein.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="enterprise-profile"></a>Unternehmensprofil

- **WLAN-Typ**: Wählen Sie **Unternehmen** aus. 

- **WLAN-Name (SSID)** : Abkürzung für Service Set Identifier. Dieser Wert entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der **Verbindungsname** angezeigt, den Sie konfiguriert haben.

- **Verbindungsname**: Geben Sie einen Anzeigenamen für diese WLAN-Verbindung ein. Der eingegebene Text ist der Name, der den Benutzern bei der Suche nach verfügbaren WLAN-Verbindungen auf ihren Geräten angezeigt wird.

- **Automatisch verbinden, wenn in Reichweite**: Wenn **Ja** festgelegt wird, verbinden sich Geräte automatisch, wenn sie sich im Empfangsbereich des Netzwerks befinden. Wenn **Nein** festgelegt wird, verbinden sich Geräte nicht automatisch.
  - **Verbindung mit bevorzugtem Netzwerk herstellen, sofern verfügbar**: Wählen Sie **Ja** aus, wenn sich Geräte im Empfangsbereich das bevorzugten Netzwerks mit diesem verbinden sollen. Wählen Sie **Nein** aus, wenn das WLAN-Netzwerk in diesem Konfigurationsprofil verwendet werden soll.

    Angenommen, Sie erstellen das WLAN-Netzwerk **ContosoCorp** und verwenden **ContosoCorp** im Konfigurationsprofil. Zusätzlich befindet sich das WLAN-Netzwerk **ContosoGuest** im Empfangsbereich des anderen Netzwerks. Wenn Ihre Unternehmensgeräte sich nun im Empfangsbereich befinden, sollen diese sich automatisch mit **ContosoCorp** verbinden. In diesem Szenario legen Sie die Eigenschaft **Verbindung mit bevorzugtem Netzwerk herstellen, sofern verfügbar** auf **Nein** fest.

  - **Verbindung mit diesem Netzwerk herstellen, auch wenn die SSID nicht übertragen wird**: Wählen Sie für das Konfigurationsprofil **Ja** aus, damit auch dann automatisch eine Verbindung zum Netzwerk hergestellt wird, wenn das Netzwerk ausgeblendet ist (d.h., die SSID nicht öffentlich übertragen wird). Wählen Sie **Nein** aus, wenn mit diesem Konfigurationsprofil keine Verbindung mit dem ausgeblendeten Netzwerk hergestellt werden soll.

- **Getaktetes Verbindungslimit:** Administratoren können bestimmen, wie der Datenverkehr des Netzwerks getaktet werden soll. Anwendungen können dann ihr Verhalten für Netzwerkdatenverkehr basierend auf dieser Einstellung anpassen. Folgende Optionen sind verfügbar:

  - **Uneingeschränkt:** Standard. Die Verbindung ist nicht getaktet und der Datenverkehr wird nicht eingeschränkt.
  - **Fest:** Verwenden Sie diese Option, wenn für das Netzwerk ein festes Limit für Datenverkehr festgelegt ist. Wenn dieses Limit erreicht ist, kann nicht mehr auf das Netzwerk zugegriffen werden.
  - **Variabel:** Verwenden Sie diese Option, wenn Netzwerkdatenverkehr pro Byte abgerechnet wird.

- **Einmaliges Anmelden (SSO):** Mit dieser Einstellung können Sie SSO konfigurieren. Dabei werden Anmeldeinformationen sowohl für Anmeldungen an einem Computer als auch bei Anmeldungen bei einem WLAN-Netzwerk verwendet. Folgende Optionen sind verfügbar:
  - **Deaktivieren**: Deaktiviert SSO. Der Benutzer muss sich in einem zusätzlichen Schritt beim Netzwerk authentifizieren.
  - **Enable before user signs into device** (Aktivieren, bevor sich Benutzer beim Gerät anmeldet): Verwenden Sie SSO, um eine Authentifizierung beim Netzwerk durchzuführen, bevor der Benutzer sich anmeldet.
  - **Enable after user signs into device** (Aktivieren, nachdem Benutzer sich beim Gerät angemeldet hat): Verwenden Sie SSO, um eine Authentifizierung beim Netzwerk durchzuführen, nachdem der Benutzer sich angemeldet hat.
  - **Maximale Zeit zur Authentifizierung vor einem Timeout**: Geben Sie die maximale Zeit in Sekunden zur Authentifizierung beim Netzwerk an. Der Wert muss zwischen 1 und 120 liegen.
  - **Windows das Anfordern zusätzlicher Anmeldeinformationen zur Authentifizierung des Benutzers erlauben**: Wenn Sie **Ja** auswählen, fordert das Windows-System den Benutzer dazu auf, zusätzliche Anmeldeinformationen einzugeben, wenn diese von der Authentifizierungsmethode benötigt werden. Wählen Sie **Nein** aus, um die Aufforderungen auszublenden.

- **PMK-Zwischenspeicherung aktivieren**: Wählen Sie **Ja** aus, um den bei der Authentifizierung verwendeten PMK zwischenzuspeichern. Dadurch wird die Authentifizierung beim Netzwerk üblicherweise schneller abgeschlossen. Wählen Sie **Nein** aus, damit bei jeder Verbindung mit dem WLAN-Netzwerk der Authentifizierungshandshake erzwungen wird.

  - **Maximal zulässige Zeit der Speicherung eines PMK im Cache**: Geben Sie die maximale Zeit in Minuten zur Zwischenspeicherung des PMK ein. Der Wert muss zwischen 5 und 1440 liegen.
  - **Maximum number of PMKs stored in cache** (Maximal zulässige Anzahl zwischengespeicherter PMKs): Geben Sie die Höchstzahl der Schlüssel ein, die zwischengespeichert werden können. Der Wert muss zwischen 1 und 255 liegen.

- **Vorauthentifizierung aktivieren**: Durch die Vorauthentifizierung kann das Profil sich bei allen Zugriffspunkten für das im Profil angegebene Netzwerk authentifizieren, bevor eine Verbindung hergestellt wird. Beim Wechseln zwischen Zugriffspunkten wird durch die Vorauthentifizierung die Neuverbindung von Benutzern oder Geräten beschleunigt. Wählen Sie **Ja** für das Profil aus, damit eine Authentifizierung bei allen Netzwerk-Zugriffspunkten durchgeführt wird, die sich innerhalb des Empfangsbereichs befinden. Wählen Sie **Nein** aus, wenn sich die Benutzer oder Geräte bei jedem Zugriffspunkt neu authentifizieren müssen.

  - **Max. Vorauthentifizierungsversuche**: Geben Sie die Höchstzahl der Vorauthentifizierungsversuche ein. Der Wert muss zwischen 1 und 16 liegen.

- **EAP-Typ**: Wählen Sie den EAP-Typ (Extensible Authentication-Protokoll) zur Authentifizierung von gesicherten Drahtlosverbindungen aus. Folgende Optionen sind verfügbar:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **Geschütztes EAP** (PEAP)

    **Weitere Einstellungen für EAP-TLS, EAP-TTLS und PEAP:**
    
    > [!NOTE]
    > Aktuell werden beim Verwenden des EAP-Typs nur SCEP-Zertifikatprofile unterstützt. PKCS-Zertifikatprofile werden nicht unterstützt. Wenn der Benutzer zur Angabe des Zertifikats aufgefordert wird, muss sichergestellt werden, dass das SCEP-Zertifikat ausgewählt wird.

    - **Serververtrauensstellung**  

      **Zertifikatservernamen:** Verwenden Sie diese Option mit den EAP-Typen **EAP-TLS**, **EAP-TTLS** oder **PEAP**. Geben Sie mindestens einen allgemeinen Namen ein, der in den von der vertrauenswürdigen Zertifizierungsstelle ausgestellten Zertifikaten verwendet wird. Wenn Sie diese Informationen eingeben, können Sie das Dialogfeld für dynamische Vertrauensstellungen umgehen, das auf Benutzergeräten bei der Verbindungsherstellung mit diesem WLAN angezeigt wird.  

      **Stammzertifikat zur Servervalidierung:** Verwenden Sie diese Option mit den EAP-Typen **EAP-TLS**, **EAP-TTLS** oder **PEAP**. Wählen Sie das vertrauenswürdige Stammzertifikatprofil zur Authentifizierung der Verbindung aus.  

      **Identitätsschutz (äußere Identität):** Verwenden Sie diese Option mit dem EAP-Typ **PEAP**. Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.  

    - **Clientauthentifizierung**

      **Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat):** Verwenden Sie diese Option mit dem EAP-Typ **EAP-TLS**. Wählen Sie das Zertifikatprofil zur Authentifizierung der Verbindung aus.

      **Authentifizierungsmethode:** Verwenden Sie diese Option mit dem EAP-Typ **EAP-TTLS**. Wählen Sie die Authentifizierungsmethode für die Verbindung aus:  

      - **Zertifikate:** Wählen Sie das Clientzertifikat aus, das dem Server als Identitätszertifikat übermittelt wird.
      - **Benutzername und Kennwort:** Geben Sie als Authentifizierungsmethode eine **Nicht-EAP-Methode (innere Identität)** an. Folgende Optionen sind verfügbar:

        - **Unverschlüsseltes Kennwort (PAP)**
        - **Challenge Handshake (CHAP)**
        - **Microsoft CHAP (MS-CHAP)**
        - **Microsoft CHAP, Version 2 (MS-CHAP v2)**

      **Identitätsschutz (äußere Identität):** Verwenden Sie diese Option mit dem EAP-Typ **EAP-TTLS**. Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

- **Proxyeinstellungen für Unternehmen**: Wählen Sie die Proxyeinstellungen aus, die innerhalb Ihrer Organisation verwendet werden sollen. Folgende Optionen sind verfügbar:
  - **Keine**: Es sind keine Proxyeinstellungen konfiguriert.
  - **Manuell konfigurieren**: Geben Sie die **IP-Adresse des Proxyservers** and die zugehörige **Portnummer** ein.
  - **Automatisch konfigurieren**: Geben Sie die URL ein, die auf ein PAC-Skript (Proxy auto-configuration; automatische Proxykonfiguration) verweist. Geben Sie beispielsweise `http://proxy.contoso.com/proxy.pac` ein.

- **FIPS-konformes (Federal Information Processing Standard) WLAN-Profil erzwingen:** Wählen Sie bei der Validierung des FIPS 140-2-Standards **Ja** aus. Dieser Standard ist für alle US-Bundesbehörden erforderlich, die Sicherheitssysteme verwenden, die auf Kryptografie basieren, um vertrauliche aber nicht klassifizierte Informationen digital zu speichern. Wählen Sie **Nein** aus, um nicht FIPS-konform zu sein.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="use-an-imported-settings-file"></a>Verwenden einer importierten Einstellungsdatei

Falls bestimmte Einstellungen nicht in Intune verfügbar sind, können Sie WLAN-Einstellungen eines anderen Windows-Geräts exportieren. Bei diesem Export wird eine XML-Datei mit allen Einstellungen erstellt. Importieren Sie diese Datei anschließend in Intune, und verwenden Sie sie als WLAN-Profil. Weitere Informationen finden Sie unter [Exportieren und Importieren von WLAN-Einstellungen für Windows-Geräte](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. [Weisen Sie dieses Profil nun zu.](device-profile-assign.md)

## <a name="more-resources"></a>Weitere Ressourcen

- Weitere Informationen zu den verfügbaren Einstellungen finden Sie unter [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
- Weitere Informationen, z.B. zu anderen Plattformen, finden Sie in der [Übersicht zu WLAN-Einstellungen](wi-fi-settings-configure.md).
