---
title: Konfigurieren der WLAN-Einstellungen von Microsoft Intune für Android-Geräte
titleSuffix: ''
description: Erfahren Sie mehr über die Intune-Einstellungen zum Konfigurieren von WLAN-Verbindungen auf Android- und Android for Work-Geräten.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c110121ceb3d7ff871078c39f73b17606e2e7f13
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Konfigurieren von WLAN-Einstellungen in Microsoft Intune für Android- und Android for Work-Geräte  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die WLAN-Einstellungen veranschaulicht, die Sie in Microsoft Intune für Android- und Android for Work-Geräte konfigurieren können.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>WLAN-Einstellungen für Basic und Enterprise-Profile

Die folgenden WLAN-Einstellungen sind für Android- und Android for Work-Geräte verfügbar:

- **Netzwerkname:** Geben Sie einen Namen für diese WLAN-Verbindung ein. Dies ist der Name, der Benutzern in der Liste der verfügbaren WLAN-Verbindungen auf ihren Geräten angezeigt wird.
- **SSID:** Abkürzung für Service Set Identifier. Dies ist der richtige Name des Drahtlosnetzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der Netzwerkname angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden:** Bei Aktivierung kann das Gerät jederzeit eine Verbindung herzustellen, wenn es sich im Bereich des Netzwerks befindet.
- **Ausgeblendetes Netzwerk:** Verhindert, dass dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät angezeigt wird.


## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>WLAN-Einstellungen für Enterprise-Profile

- **EAP-Typ:** Wählen Sie den EAP-Typ (Extensible Authentication-Protokoll) zur Authentifizierung von gesicherten Drahtlosverbindungen aus:
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Weitere Optionen bei der Auswahl eines EAP-Typs

#### <a name="server-trust"></a>Serververtrauensstellung



|Name der Einstellung|Weitere Informationen|Verwendungsgrund|
|-------------|---------------|-----------|
|**Zertifikatservername(n)**|Geben Sie einen oder mehrere allgemeine Namen an, die in den von der vertrauenswürdigen Zertifizierungsstelle (CA) ausgestellten Zertifikaten verwendet werden. Wenn Sie diese Informationen angeben, können Sie den dynamischen Vertrauensstellungsdialog umgehen, der auf Benutzergeräten bei der Herstellung einer Verbindung mit diesem WLAN-Netzwerk angezeigt wird.|Der EAP-Typ ist **EAP-TLS** oder **EAP-TTLS**.|
|**Stammzertifikat zur Servervalidierung**|Wählen Sie das vertrauenswürdige Stammzertifikatprofil zur Authentifizierung der Verbindung aus. |Der EAP-Typ ist **EAP-TLS**, **EAP-TTLS** oder **PEAP**.|
|**Identitätsschutz (äußere Identität)**|Geben Sie den Text ein, der als Antwort auf eine EAP-Identity-Request gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.|Der EAP-Typ ist **PEAP**.|


#### <a name="client-authentication"></a>Clientauthentifizierung


|                                     Name der Einstellung                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Weitere Informationen                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            Verwendungsgrund                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Wählen Sie das SCEP- oder PKCS-Zertifikatprofil zur Authentifizierung der Verbindung aus.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              Der EAP-Typ ist <strong>EAP-TLS</strong>.              |
|                        <strong>Authentifizierungsmethode</strong>                        | Wählen Sie die Authentifizierungsmethode für die Verbindung aus:<br>- <strong>Zertifikate</strong> zur Auswahl von SCEP oder PKCS als Clientzertifikat, das als Identitätszertifikat dem Server vorgelegt wird<br><br>- <strong>Benutzername und Kennwort</strong> zur Angabe einer anderen Authentifizierungsmethode <br><br>Bei Auswahl von <strong>Benutzername und Kennwort</strong>, konfigurieren Sie noch Folgendes:<br><br>-  <strong>Nicht-EAP-Methode (innere Identität):</strong> Wählen Sie anschließend aus, wie Sie die Verbindung authentifizieren möchten:<br>- <strong>Keine</strong><br>- <strong>Unverschlüsseltes Kennwort (PAP)</strong><br>- <strong>Challenge Handshake Authentication-Protokoll (CHAP)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP, Version 2 (MS-CHAP v2)</strong><br>Die verfügbaren Optionen hängen vom ausgewählten EAP-Typ ab.<br><br><strong>und</strong><br><br>- <strong>Identitätsschutz aktivieren (äußere Identität)</strong>. Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dies kann ein beliebiger Text sein. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel. | Der EAP-Typ ist <strong>EAP-TTLS</strong> oder <strong>PEAP</strong>. |

