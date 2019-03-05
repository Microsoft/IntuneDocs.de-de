---
title: WLAN-Einstellungen für Android Enterprise- und Kioskgeräte – Microsoft Intune | Microsoft-Dokumentation
description: Erstellen Sie ein WLAN-Gerätekonfigurationsprofils für Android Enterprise- und Android-Kioskgeräte, oder fügen Sie eines hinzu. Erfahren Sie mehr über die verschiedenen Einstellungen, z.B., wie Sie Zertifikate hinzufügen oder einen EAP-Typ bzw. eine Authentifizierungsmethode in Microsoft Intune auswählen. Geben Sie für Kioskgeräte außerdem den vorinstallierten Schlüssel Ihres Netzwerks ein.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c750178efe18c16796253ad542157466f7ba57f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238641"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Festlegen von WLAN-Einstellungen für Geräte mit Android Enterprise und Android-Kioskgeräte in Microsoft Intune

Sie können ein Profil mit bestimmten WLAN-Einstellungen erstellen und dieses dann auf Ihren Android Enterprise- und Android-Kioskgeräten bereitstellen. Microsoft Intune bietet viele Features, darunter die Authentifizierung bei Ihrem Netzwerk mit einem vorinstallierten Schlüssel.

Dieser Artikel beschreibt diese Einstellungen. [Hinzufügen und Verwenden von WLAN-Einstellungen auf Microsoft Intune-Geräten](wi-fi-settings-configure.md) enthält weitere Informationen über die WLAN-Funktion in Microsoft Intune.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Geräteprofil.](wi-fi-settings-configure.md#create-a-device-profile)

## <a name="device-owner-only---kiosk"></a>Nur Gerätebesitzer – Kiosk

Wählen Sie diese Option aus, wenn Sie ein Android Enterprise-Gerät als Kiosk verwenden.

- **Netzwerkname**: Geben Sie einen Namen für diese WLAN-Verbindung ein. Dieser Wert ist der Name, der Benutzern in der Liste der verfügbaren Verbindungen auf ihren Geräten angezeigt wird.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Einstellung entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem sich die Geräte verbinden. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der **Netzwerkname** angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.
- **WLAN-Typ**: Wählen Sie das Sicherheitsprotokoll zur Authentifizierung beim WLAN-Netzwerk aus. Folgende Optionen sind verfügbar:

  - **Offen (keine Authentifizierung)**: Verwenden Sie diese Option nur, wenn das Netzwerk nicht gesichert ist.
  - **Vorinstallierter WEP-Schlüssel**: Geben Sie das Kennwort unter **Vorinstallierter Schlüssel** ein. Wenn das Netzwerk Ihrer Organisation eingerichtet oder konfiguriert wird, wird auch ein Kennwort oder ein Netzwerkschlüssel konfiguriert. Geben Sie dieses Kennwort oder den Netzwerkschlüssel für den Wert des vorinstallierten Schlüssels ein.
  - **Vorinstallierter WPA-Schlüssel**: Geben Sie das Kennwort unter **Vorinstallierter Schlüssel** ein. Wenn das Netzwerk Ihrer Organisation eingerichtet oder konfiguriert wird, wird auch ein Kennwort oder ein Netzwerkschlüssel konfiguriert. Geben Sie dieses Kennwort oder den Netzwerkschlüssel für den Wert des vorinstallierten Schlüssels ein.

Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="work-profile-only"></a>Nur Arbeitsprofil

### <a name="basic-settings"></a>Grundlegende Einstellungen

- **WLAN-Typ**: Wählen Sie **Standard**.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Einstellung entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem sich die Geräte verbinden.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.

## <a name="enterprise-profile"></a>Unternehmensprofil

- **WLAN-Typ**: Wählen Sie **Unternehmen** aus.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Einstellung entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem sich die Geräte verbinden.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.
- **EAP-Typ**: Wählen Sie die den EAP-Typ (Extensible Authentication-Protokoll) zur Authentifizierung von gesicherten Drahtlosverbindungen aus. Folgende Optionen sind verfügbar: 

  - **EAP-TLS**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes, vertrauenswürdiges Stammzertifikatprofil aus. Wenn sich der Client mit dem Netzwerk verbindet, wird dieses Zertifikat dem Server bereitgestellt und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung** - **Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

  - **EAP-TTLS**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes, vertrauenswürdiges Stammzertifikatprofil aus. Wenn sich der Client mit dem Netzwerk verbindet, wird dieses Zertifikat dem Server bereitgestellt und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Methode (innere Identität)**: Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN konfiguriert ist.

          Folgende Optionen sind verfügbar: **Unverschlüsseltes Kennwort (PAP)**, **Challenge Handshake Authentication-Protokoll (CHAP)**, **Microsoft CHAP (MS-CHAP)** oder **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

        Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

  - **PEAP**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes, vertrauenswürdiges Stammzertifikatprofil aus. Wenn sich der Client mit dem Netzwerk verbindet, wird dieses Zertifikat dem Server bereitgestellt und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Authentifizierungsmethode (innere Identität)**: Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN konfiguriert ist.

          Folgende Optionen sind verfügbar: **Keine** oder **Microsoft CHAP, Version 2 (MS-CHAP v2)**

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

        Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. Die nächsten Schritte sind das [Zuweisen dieses Profils](device-profile-assign.md) und das [Überwachen seines Status](device-profile-monitor.md).

Sie können WLAN-Profile auch für [Android](wi-fi-settings-android.md)-, [iOS](wi-fi-settings-ios.md)-, [macOS](wi-fi-settings-macos.md)-, [Windows 10](wi-fi-settings-windows.md)- und [Windows 8.1](wi-fi-settings-import-windows-8-1.md)-Geräte erstellen.
