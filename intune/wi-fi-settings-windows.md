---
title: WLAN-Einstellungen für Windows 10-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie in Microsoft Intune mithilfe der WLAN-Einstellungen für Geräte mit Windows 10 und höher WLAN-Konfigurationsprofile hinzufügen oder erstellen. Sie können Einstellungen für Basic- oder Enterprise-Profile konfigurieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6532c63612b806f9824f5b9ca98f1ebbbc943f
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321662"
---
## <a name="wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune

WLAN-Einstellungen werden in einem Konfigurationsprofil verwendet, das auf Geräte mit Windows 10 und höher angewendet wird. Diese Optionen umfassen Folgendes:

- Einfach
- Enterprise

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Geräteprofil.](device-profile-create.md)

## <a name="settings-for-basic-and-enterprise-profiles"></a>Einstellungen für Basic- und Enterprise-Profile

- **WLAN-Name (SSID)**: Abkürzung für Service Set Identifier. Dieser Wert entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der **Verbindungsname** angezeigt, den Sie konfiguriert haben.
- **Verbindungsname**: Geben Sie einen Anzeigenamen für diese WLAN-Verbindung ein. Der eingegebene Text ist der Name, der den Benutzern bei der Suche nach verfügbaren WLAN-Verbindungen auf ihren Geräten angezeigt wird.
- **Automatisch verbinden, wenn in Reichweite**: Wenn **Ja** festgelegt wird, verbinden sich Geräte automatisch, wenn sie sich im Empfangsbereich des Netzwerks befinden. Wenn **Nein** festgelegt wird, verbinden sich Geräte nicht automatisch.
  - **Verbindung mit bevorzugtem Netzwerk herstellen, sofern verfügbar**: Wählen Sie **Ja** aus, wenn sich Geräte im Empfangsbereich das bevorzugten Netzwerks mit diesem verbinden sollen. Wählen Sie **Nein** aus, wenn das WLAN-Netzwerk in diesem Konfigurationsprofil verwendet werden soll.

    Angenommen, Sie erstellen das WLAN-Netzwerk **ContosoCorp** und verwenden **ContosoCorp** im Konfigurationsprofil. Zusätzlich befindet sich das WLAN-Netzwerk **ContosoGuest** im Empfangsbereich des anderen Netzwerks. Wenn Ihre Unternehmensgeräte sich nun im Empfangsbereich befinden, sollen diese sich automatisch mit **ContosoCorp** verbinden. In diesem Szenario legen Sie die Eigenschaft **Verbindung mit bevorzugtem Netzwerk herstellen, sofern verfügbar** auf **Nein** fest.

  - **Verbindung mit diesem Netzwerk herstellen, auch wenn die SSID nicht übertragen wird**: Wählen Sie für das Konfigurationsprofil **Ja** aus, damit auch dann automatisch eine Verbindung zum Netzwerk hergestellt wird, wenn das Netzwerk ausgeblendet ist (d.h., die SSID nicht öffentlich übertragen wird). Wählen Sie **Nein** aus, wenn mit diesem Konfigurationsprofil keine Verbindung mit dem ausgeblendeten Netzwerk hergestellt werden soll.

- **Proxyeinstellungen für Unternehmen**: Wählen Sie die Proxyeinstellungen aus, die innerhalb Ihrer Organisation verwendet werden sollen. Folgende Optionen sind verfügbar:
  - **Keine**: Es sind keine Proxyeinstellungen konfiguriert.
  - **Manuell konfigurieren**: Geben Sie die **IP-Adresse des Proxyservers** and die zugehörige **Portnummer** ein.
  - **Automatisch konfigurieren**: Geben Sie die URL ein, die auf ein PAC-Skript (Proxy auto-configuration; automatische Proxykonfiguration) verweist. Geben Sie beispielsweise `http://proxy.contoso.com/proxy.pac` ein.

## <a name="settings-for-basic-profiles-only"></a>Einstellungen für Basic-Profile

- **Sicherheitstyp für Drahtlosverbindung**: Geben Sie das Sicherheitsprotokoll an, mit dem Geräte in Ihrem Netzwerk authentifiziert werden. Folgende Optionen sind verfügbar:
  - **Offen (keine Authentifizierung):** Verwenden Sie diese Option nur, wenn das Netzwerk nicht gesichert ist.
  - **WPA/WPA2-Personal**

## <a name="settings-for-enterprise-profiles-only"></a>Einstellungen für Enterprise-Profile

- **Einmaliges Anmelden (SSO)**: Mit dieser Einstellung können Sie SSO konfigurieren. Dabei werden Anmeldeinformationen sowohl für Anmeldungen an einem Computer als auch bei Anmeldungen bei einem WLAN-Netzwerk verwendet. Folgende Optionen sind verfügbar:
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

### <a name="more-options-when-you-choose-the-eap-type"></a>Weitere Optionen beim Auswählen des EAP-Typs

> [!NOTE]
> Aktuell werden beim Verwenden des EAP-Typs nur SCEP-Zertifikatprofile unterstützt. PKCS-Zertifikatprofile werden nicht unterstützt. Wenn der Benutzer zur Angabe des Zertifikats aufgefordert wird, muss sichergestellt werden, dass das SCEP-Zertifikat ausgewählt wird.

#### <a name="server-trust"></a>Serververtrauensstellung

|Name der Einstellung|Weitere Informationen|Verwendungsgrund|
|--------------|-------------|----------|
|**Zertifikatservername(n)**|Geben Sie mindestens einen allgemeinen Namen ein, der in den von der vertrauenswürdigen Zertifizierungsstelle ausgestellten Zertifikaten verwendet wird. Wenn Sie diese Informationen eingeben, können Sie das Dialogfeld für dynamische Vertrauensstellungen umgehen, das auf Benutzergeräten bei der Verbindungsherstellung mit diesem WLAN angezeigt wird.|Der EAP-Typ ist **EAP-TLS**, **EAP-TTLS** oder **PEAP**.|
|**Stammzertifikat zur Servervalidierung**|Wählen Sie das vertrauenswürdige Stammzertifikatprofil zur Authentifizierung der Verbindung aus. |Der EAP-Typ ist **EAP-TLS**, **EAP-TTLS** oder **PEAP**.|
|**Identitätsschutz (äußere Identität)**|Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.|Der EAP-Typ ist **PEAP**.|

#### <a name="client-authentication"></a>Clientauthentifizierung

| Name der Einstellung | Weitere Informationen | Verwendungsgrund |
|---|---|---|
| **Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)** |  Wählen Sie das SCEP-Zertifikatprofil zur Authentifizierung der Verbindung aus. | Der EAP-Typ ist **EAP-TLS**. |
| **Authentifizierungsmethode** | Wählen Sie die Authentifizierungsmethode für die Verbindung aus:<br><br>- **Zertifikate**: Wählen Sie das SCEP-Clientzertifikat aus, das dem Server als Identitätszertifikat vorgelegt wird.<br><br>- **Benutzername und Kennwort**: Geben Sie als Authentifizierungsmethode eine **Nicht-EAP-Methode (innere Identität)** an. Folgende Optionen sind verfügbar:<br><br>- **Unverschlüsseltes Kennwort (PAP)**<br>- **Challenge Handshake (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP, Version 2 (MS-CHAP v2)**<br><br>- **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel. | Der EAP-Typ ist **EAP-TTLS**. |

## <a name="use-an-imported-settings-file"></a>Verwenden einer importierten Einstellungsdatei

Falls bestimmte Einstellungen nicht in Intune verfügbar sind, können Sie WLAN-Einstellungen eines anderen Windows-Geräts exportieren. Bei diesem Export wird eine XML-Datei mit allen Einstellungen erstellt. Importieren Sie diese Datei anschließend in Intune, und verwenden Sie sie als WLAN-Profil. Weitere Informationen finden Sie unter [Exportieren und Importieren von WLAN-Einstellungen für Windows-Geräte](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von WLAN-Einstellungen in Intune](wi-fi-settings-configure.md)
