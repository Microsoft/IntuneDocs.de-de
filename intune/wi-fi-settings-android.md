---
title: Konfigurieren von WLAN-Einstellungen für Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erstellen Sie ein WLAN-Gerätekonfigurationsprofil für Android oder fügen Sie eins hinzu. Erfahren Sie mehr über die verschiedenen Einstellungen, z.B. wie Sie Zertifikate hinzufügen oder einen EAP-Typ bzw. eine Authentifizierungsmethode in Microsoft Intune auswählen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d199256d77f19655d8d3e78c545ab1f236021d0
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236856"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Hinzufügen von WLAN-Einstellungen für Android-Geräte in Microsoft Intune

Sie können ein Profil mit bestimmten WLAN-Einstellungen erstellen und dieses dann auf Ihren Android-Geräten bereitstellen. Microsoft Intune bietet viele Features, darunter die Authentifizierung bei Ihrem Netzwerk und das Hinzufügen eines PKCS- oder SCEP-Zertifikats.

Diese WLAN-Einstellungen werden in zwei Kategorien unterteilt: Grundeinstellungen und Einstellungen für Unternehmen.

Dieser Artikel beschreibt diese Einstellungen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Geräteprofil.](device-profile-create.md)

## <a name="basic-profile"></a>Grundlegendes Profil

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

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes, vertrauenswürdiges Stammzertifikatprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung** - **Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

  - **EAP-TTLS**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes, vertrauenswürdiges Stammzertifikatprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

      Klicken Sie auf **OK**, um die Änderungen zu speichern.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Methode (innere Identität)**: Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN konfiguriert ist.

          Folgende Optionen sind verfügbar: **Unverschlüsseltes Kennwort (PAP)**, **Challenge Handshake Authentication-Protokoll (CHAP)**, **Microsoft CHAP (MS-CHAP)** oder **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

        Klicken Sie auf **OK**, um die Änderungen zu speichern.

      - **Identitätsschutz (äußere Identität)**: Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet werden soll. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

  - **PEAP**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes, vertrauenswürdiges Stammzertifikatprofil aus. Dieses Zertifikat wird dem Server bereitgestellt, wenn sich der Client mit dem Netzwerk verbindet, und zur Authentifizierung der Verbindung verwendet.

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

Das Profil ist nun erstellt. [Weisen Sie dieses Profil nun zu.](device-profile-assign.md)

## <a name="more-resources"></a>Weitere Ressourcen

- Verschaffen Sie sich eine [Übersicht über WLAN-Einstellungen](wi-fi-settings-configure.md) auf unterschiedlichen Plattformen.

- Verwenden Sie Android Enterprise- oder Android-Kioskgeräte? Wenn ja, sehen Sie sich die [WLAN-Einstellungen für Geräte mit Android Enterprise und Android-Kiosk](wi-fi-settings-android-enterprise.md) an.
