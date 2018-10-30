---
title: Konfigurieren von WLAN-Einstellungen für macOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erstellen Sie ein WLAN-Gerätekonfigurationsprofil für macOS-Geräte, oder fügen Sie eines hinzu. Erfahren Sie mehr über die verschiedenen Einstellungen, z.B., wie Sie Zertifikate hinzufügen oder einen EAP-Typ bzw. eine Authentifizierungsmethode in Microsoft Intune auswählen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e094ec72f7db6c25bcb306518df47dd5938681bf
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425341"
---
# <a name="add-wi-fi-settings-for-macos-devices-in-microsoft-intune"></a>Hinzufügen von WLAN-Einstellungen für macOS-Geräte in Microsoft Intune

Sie können ein Profil mit bestimmten WLAN-Einstellungen erstellen und dieses dann auf Ihren macOS-Geräten bereitstellen. Microsoft Intune bietet viele Features, darunter die Authentifizierung bei Ihrem Netzwerk und das Hinzufügen eines PKCS- oder SCEP-Zertifikats.

Diese WLAN-Einstellungen lassen sich in zwei Kategorien unterteilen: grundlegende Einstellungen und Einstellungen für Unternehmen.

Dieser Artikel beschreibt diese Einstellungen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Geräteprofil.](device-profile-create.md)

## <a name="basic-profiles"></a>Grundlegende Profile

- **WLAN-Typ**: Wählen Sie **Grundlegend** aus.
- **Netzwerkname**: Geben Sie einen Namen für diese WLAN-Verbindung ein. Dieser Wert ist der Name, der Benutzern in der Liste der verfügbaren Verbindungen auf ihren Geräten angezeigt wird.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Eigenschaft entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der Netzwerkname angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.
- **Sicherheitstyp**: Wählen Sie das Sicherheitsprotokoll zur Authentifizierung beim WLAN-Netzwerk aus: Folgende Optionen sind verfügbar:

  - **Offen (keine Authentifizierung):** Verwenden Sie diese Option nur, wenn das Netzwerk nicht gesichert ist.
  - **WPA/WPA2 – Persönlich**: Geben Sie das Kennwort unter **Vorinstallierter Schlüssel** ein. Wenn das Netzwerk Ihrer Organisation eingerichtet oder konfiguriert wird, wird auch ein Kennwort oder ein Netzwerkschlüssel konfiguriert. Geben Sie dieses Kennwort oder den Netzwerkschlüssel für den Wert des vorinstallierten Schlüssels ein.
  - **Datenverschlüsselung**

- **Proxyeinstellungen**: Ihre Optionen:
  - **Keine**: Es sind keine Proxyeinstellungen konfiguriert.
  - **Manuell**: Geben Sie die **Proxyserveradresse** (als IP-Adresse) und die **Portnummer** ein.
  - **Automatisch**: Verwenden Sie eine Konfigurationsdatei, um den Proxyserver zu konfigurieren. Geben Sie die **Proxyserver-URL** ein (z.B. `http://proxy.contoso.com`), unter der die Konfigurationsdatei zu finden ist.

## <a name="enterprise-profiles"></a>Enterprise-Profile

- **WLAN-Typ**: Wählen Sie **Unternehmen** aus.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Eigenschaft entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der Netzwerkname angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.

- **EAP-Typ**: Wählen Sie den EAP-Typ (Extensible Authentication Protocol) zum Authentifizieren von geschützten Drahtlosverbindungen aus. Folgende Optionen sind verfügbar:

  - **EAP-FAST**: Geben Sie die **PAC-Einstellungen (Protected Access Credential)** ein. Bei dieser Option werden geschützte Zugriffsanmeldeinformationen verwendet, um einen authentifizierten Tunnel zwischen dem Client und dem Authentifizierungsserver zu erstellen. Folgende Optionen sind verfügbar:
    - **Nicht (PAC) verwenden**
    - **(PAC) verwenden**: Wenn eine PAC-Datei vorhanden ist, verwenden Sie diese.
    - **PAC verwenden und bereitstellen**: Erstellen Sie die PAC-Datei, und fügen Sie sie auf Ihren Geräten hinzu.
    - **PAC anonym verwenden und bereitstellen**: Erstellen Sie die PAC-Datei, und fügen Sie sie Ihren Geräte ohne Authentifizierung beim Server hinzu.

  - **EAP-SIM**

  - **EAP-TLS**: Machen Sie außerdem die folgenden Angaben:

    - **Serververtrauensstellung** - **Zertifikatservernamen**: **Fügen Sie mindestens einen allgemeinen Namen hinzu**, der in den von der vertrauenswürdigen Zertifizierungsstelle ausgestellten Zertifikaten verwendet wird. Wenn Sie diese Informationen eingeben, können Sie das Fenster für dynamische Vertrauensstellungen umgehen, das auf Benutzergeräten bei der Verbindungsherstellung mit diesem WLAN angezeigt wird.
    - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung** - **Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

  - **EAP-TTLS**: Machen Sie außerdem die folgenden Angaben:

    - **Serververtrauensstellung** - **Zertifikatservernamen**: **Fügen Sie mindestens einen allgemeinen Namen hinzu**, der in den von der vertrauenswürdigen Zertifizierungsstelle ausgestellten Zertifikaten verwendet wird. Wenn Sie diese Informationen eingeben, können Sie das Fenster für dynamische Vertrauensstellungen umgehen, das auf Benutzergeräten bei der Verbindungsherstellung mit diesem WLAN angezeigt wird.
    - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Methode (innere Identität)**: Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN-Netzwerk konfiguriert ist.

          Ihre Optionen sind **Unverschlüsseltes Kennwort (PAP)**, **Challenge Handshake Authentication-Protokoll (CHAP)**, **Microsoft CHAP (MS-CHAP)** oder **Microsoft CHAP Version 2 (MS-CHAP v2)**.

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

        Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet wird. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

  - **LEAP**

  - **PEAP**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Zertifikatservernamen**: **Fügen Sie mindestens einen allgemeinen Namen hinzu**, der in den von der vertrauenswürdigen Zertifizierungsstelle ausgestellten Zertifikaten verwendet wird. Wenn Sie diese Informationen eingeben, können Sie das Fenster für dynamische Vertrauensstellungen umgehen, das auf Benutzergeräten bei der Verbindungsherstellung mit diesem WLAN angezeigt wird.
    - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. 

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

        Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet wird. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

- **Proxyeinstellungen**: Ihre Optionen:
  - **Keine**: Es sind keine Proxyeinstellungen konfiguriert.
  - **Manuell**: Geben Sie die **Proxyserveradresse** (als IP-Adresse) und die **Portnummer** ein.
  - **Automatisch**: Verwenden Sie eine Konfigurationsdatei, um den Proxyserver zu konfigurieren. Geben Sie die **Proxyserver-URL** ein (z.B. `http://proxy.contoso.com`), unter der die Konfigurationsdatei zu finden ist.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. [Weisen Sie dieses Profil nun zu.](device-profile-assign.md)

## <a name="more-resources"></a>Weitere Ressourcen

[Übersicht über WLAN-Einstellungen](wi-fi-settings-configure.md) auf unterschiedlichen Plattformen