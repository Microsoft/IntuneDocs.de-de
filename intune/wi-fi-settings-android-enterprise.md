---
title: Konfigurieren von WLAN-Einstellungen für Android Enterprise- und Kioskgeräte – Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erstellen Sie ein WLAN-Gerätekonfigurationsprofils für Android Enterprise- und Android-Kioskgeräte, oder fügen Sie eines hinzu. Erfahren Sie mehr über die verschiedenen Einstellungen, z.B., wie Sie Zertifikate hinzufügen oder einen EAP-Typ bzw. eine Authentifizierungsmethode in Microsoft Intune auswählen. Geben Sie für Kioskgeräte außerdem den vorinstallierten Schlüssel Ihres Netzwerks ein.
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
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: be26522555766c6a3661857ba7722c2425cc984e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180441"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Festlegen von WLAN-Einstellungen für Geräte mit Android Enterprise und Android-Kioskgeräte in Microsoft Intune

Sie können ein Profil mit bestimmten WLAN-Einstellungen erstellen und dieses dann auf Ihren Android Enterprise- und Android-Kioskgeräten bereitstellen. Microsoft Intune bietet viele Features, darunter die Authentifizierung bei Ihrem Netzwerk mit einem vorinstallierten Schlüssel.

Dieser Artikel beschreibt diese Einstellungen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Geräteprofil.](device-profile-create.md)

## <a name="device-owner-only---kiosk"></a>Nur Gerätebesitzer – Kiosk

Wählen Sie diese Option aus, wenn Sie ein Android Enterprise-Gerät als Kiosk verwenden.

- **Netzwerkname**: Geben Sie einen Namen für diese WLAN-Verbindung ein. Dieser Wert ist der Name, der Benutzern in der Liste der verfügbaren Verbindungen auf ihren Geräten angezeigt wird.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Einstellung entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem sich die Geräte verbinden. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der **Netzwerkname** angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.
- **WLAN-Typ**: Wählen Sie das Sicherheitsprotokoll zur Authentifizierung beim WLAN-Netzwerk aus. Folgende Optionen sind verfügbar:

  - **Offen (keine Authentifizierung):** Verwenden Sie diese Option nur, wenn das Netzwerk nicht gesichert ist.
  - **Vorinstallierter WEP-Schlüssel**: Geben Sie das Kennwort unter **Vorinstallierter Schlüssel** ein. Wenn das Netzwerk Ihrer Organisation eingerichtet oder konfiguriert wird, wird auch ein Kennwort oder ein Netzwerkschlüssel konfiguriert. Geben Sie dieses Kennwort oder den Netzwerkschlüssel für den Wert des vorinstallierten Schlüssels ein.
  - **Vorinstallierter WPA-Schlüssel**: Geben Sie das Kennwort unter **Vorinstallierter Schlüssel** ein. Wenn das Netzwerk Ihrer Organisation eingerichtet oder konfiguriert wird, wird auch ein Kennwort oder ein Netzwerkschlüssel konfiguriert. Geben Sie dieses Kennwort oder den Netzwerkschlüssel für den Wert des vorinstallierten Schlüssels ein.

Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="work-profile-only"></a>Nur Arbeitsprofil

### <a name="basic-settings"></a>Grundlegende Einstellungen

- **WLAN-Typ**: Wählen Sie **Grundlegend** aus.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Einstellung entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem sich die Geräte verbinden.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.

## <a name="enterprise-profile"></a>Unternehmensprofil

- **WLAN-Typ**: Wählen Sie **Unternehmen** aus.
- **SSID**: Abkürzung für **Service Set Identifier**. Diese Einstellung entspricht dem tatsächlichen Namen des Drahtlosnetzwerks, mit dem sich die Geräte verbinden.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.
- **EAP-Typ**: Wählen Sie den EAP-Typ (Extensible Authentication Protocol) zum Authentifizieren von geschützten Drahtlosverbindungen aus. Folgende Optionen sind verfügbar: 

  - **EAP-TLS**: Machen Sie außerdem die folgenden Angaben:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung** - **Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

  - **EAP-TTLS**: Machen Sie außerdem die folgenden Angaben:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Methode (innere Identität)**: Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN konfiguriert ist.

          Ihre Optionen sind **Unverschlüsseltes Kennwort (PAP)**, **Challenge Handshake Authentication-Protokoll (CHAP)**, **Microsoft CHAP (MS-CHAP)** oder **Microsoft CHAP Version 2 (MS-CHAP v2)**.

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

        Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet wird. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

  - **PEAP**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Methode zur Authentifizierung (innere Identität)**: Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN konfiguriert ist.

          Ihre Optionen lauten **Keine** oder **Microsoft CHAP, Version 2 (MS-CHAP v2)**.

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

        Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet wird. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. [Weisen Sie dieses Profil nun zu.](device-profile-assign.md)

## <a name="more-resources"></a>Weitere Ressourcen

- Die verfügbaren Einstellungen für Android-Geräte finden Sie unter [Festlegen von WLAN-Einstellungen für Android-Geräte in Microsoft Intune](wi-fi-settings-android.md).
- Verschaffen Sie sich eine [Übersicht über WLAN-Einstellungen](wi-fi-settings-configure.md) auf unterschiedlichen Plattformen.