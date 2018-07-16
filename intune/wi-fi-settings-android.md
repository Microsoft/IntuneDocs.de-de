---
title: Konfigurieren der WLAN-Einstellungen von Microsoft Intune für Android-Geräte
titleSuffix: ''
description: Erfahren Sie mehr über das Konfigurieren der WLAN-Einstellungen von Intune auf Android-Geräten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0157815322488525a4ce7a3d6d2c90cbb8d3ff2a
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905664"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-android-work-profiles-and-android-kiosk-devices"></a>Konfigurieren von WLAN-Einstellungen in Microsoft Intune für Android-, Android-Kiosk- und Android-Arbeitsprofilgeräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die WLAN-Einstellungen veranschaulicht, die Sie in Microsoft Intune für Android- und Android-Arbeitsprofilgeräte konfigurieren können.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>WLAN-Einstellungen für Basic und Enterprise-Profile

Die folgenden WLAN-Einstellungen sind für Android- und Android-Arbeitsprofilgeräte verfügbar:

- **Netzwerkname:** Geben Sie einen Namen für diese WLAN-Verbindung ein. Dies ist der Name, der Benutzern in der Liste der verfügbaren WLAN-Verbindungen auf ihren Geräten angezeigt wird.
- **SSID:** Abkürzung für Service Set Identifier. Dies ist der richtige Name des Drahtlosnetzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der Netzwerkname angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden:** Bei Aktivierung kann das Gerät jederzeit eine Verbindung herzustellen, wenn es sich im Bereich des Netzwerks befindet.
- **Ausgeblendetes Netzwerk:** Verhindert, dass dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät angezeigt wird.

## <a name="wi-fi-settings-available-for-enterprise-kiosk-profiles"></a>WLAN-Einstellungen, die für Enterprise-Kioskgeräte verfügbar sind
- **WLAN-Typ:** Die Einstellungen des WLAN-Typs sind nur verfügbar, wenn Sie **Profiltyp** > **Nur Gerätebesitzer** > **WLAN** auswählen.
    - **Offen (keine Authentifizierung)**
    - **Vorinstallierter WEP-Schlüssel:** Sie müssen im Feld **Vorinstallierter Schlüssel** ein Kennwort eingeben.
    - **Vorinstallierter WPA-Schlüssel:** Sie müssen im Feld **Vorinstallierter Schlüssel** ein Kennwort eingeben.

## <a name="wi-fi-settings-for-android-legacy-and-android-work-profiles-only"></a>WLAN-Einstellungen für Android-Legacy- und Android-Arbeitsprofile

- **EAP-Typ:** Wählen Sie den EAP-Typ (Extensible Authentication-Protokoll) zur Authentifizierung von gesicherten Drahtlosverbindungen aus:
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Weitere Optionen bei der Auswahl eines EAP-Typs

#### <a name="server-trust"></a>Serververtrauensstellung



|Einstellungsname|Weitere Informationen|Verwendungsgrund|
|-------------|---------------|-----------|
|**Zertifikatservername(n)**|Geben Sie einen oder mehrere allgemeine Namen an, die in den von der vertrauenswürdigen Zertifizierungsstelle (CA) ausgestellten Zertifikaten verwendet werden. Wenn Sie diese Informationen angeben, können Sie den dynamischen Vertrauensstellungsdialog umgehen, der auf Benutzergeräten bei der Herstellung einer Verbindung mit diesem WLAN-Netzwerk angezeigt wird.|Der EAP-Typ ist **EAP-TLS** oder **EAP-TTLS**.|
|**Stammzertifikat zur Servervalidierung**|Wählen Sie das vertrauenswürdige Stammzertifikatprofil zur Authentifizierung der Verbindung aus. |Der EAP-Typ ist **EAP-TLS**, **EAP-TTLS** oder **PEAP**.|
|**Identitätsschutz (äußere Identität)**|Geben Sie den Text ein, der als Antwort auf eine EAP-Identity-Request gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.|Der EAP-Typ ist **PEAP**.|


#### <a name="client-authentication"></a>Clientauthentifizierung


|                                     Einstellungsname                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Weitere Informationen                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            Verwendungsgrund                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Wählen Sie das SCEP- oder PKCS-Zertifikatprofil zur Authentifizierung der Verbindung aus.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              Der EAP-Typ ist <strong>EAP-TLS</strong>.              |
|                        <strong>Authentifizierungsmethode</strong>                        | Wählen Sie die Authentifizierungsmethode für die Verbindung aus:<br>- <strong>Zertifikate</strong> zur Auswahl von SCEP oder PKCS als Clientzertifikat, das als Identitätszertifikat dem Server vorgelegt wird<br><br>- <strong>Benutzername und Kennwort</strong> zur Angabe einer anderen Authentifizierungsmethode <br><br>Bei Auswahl von <strong>Benutzername und Kennwort</strong>, konfigurieren Sie noch Folgendes:<br><br>-  <strong>Nicht-EAP-Methode (innere Identität):</strong> Wählen Sie anschließend aus, wie Sie die Verbindung authentifizieren möchten:<br>- <strong>Keine</strong><br>- <strong>Unverschlüsseltes Kennwort (PAP)</strong><br>- <strong>Challenge Handshake Authentication-Protokoll (CHAP)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP, Version 2 (MS-CHAP v2)</strong><br>Die verfügbaren Optionen hängen vom ausgewählten EAP-Typ ab.<br><br><strong>und</strong><br><br>- <strong>Identitätsschutz aktivieren (äußere Identität)</strong>. Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel. | Der EAP-Typ ist <strong>EAP-TTLS</strong> oder <strong>PEAP</strong>. |

