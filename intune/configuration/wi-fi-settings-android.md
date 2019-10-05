---
title: Konfigurieren von WLAN-Einstellungen für Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erstellen Sie ein WLAN-Gerätekonfigurationsprofil für Android oder fügen Sie eins hinzu. Erfahren Sie mehr über die verschiedenen Einstellungen, z.B. wie Sie Zertifikate hinzufügen oder einen EAP-Typ bzw. eine Authentifizierungsmethode in Microsoft Intune auswählen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d341aeace950f62ae699aa7760a65c0fd2f74fa
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734036"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Hinzufügen von WLAN-Einstellungen für Android-Geräte in Microsoft Intune

Sie können ein Profil mit bestimmten WLAN-Einstellungen erstellen und dieses dann auf Ihren Android-Geräten bereitstellen. Microsoft Intune bietet viele Funktionen, darunter die Authentifizierung in Ihrem Netzwerk und das Hinzufügen eines PKCS- oder SCEP-Zertifikats.

Diese WLAN-Einstellungen lassen sich in zwei Kategorien unterteilen: grundlegende Einstellungen und Einstellungen für Unternehmen.

Dieser Artikel beschreibt diese Einstellungen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Geräteprofil.](device-profile-create.md)

## <a name="basic"></a>Einfach

- **WLAN-Typ**: Wählen Sie **Grundlegend** aus.
- **SSID**: Geben Sie den **Bezeichner des Dienst Satzes**ein. Dies ist der tatsächliche Name des drahtlos Netzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der **Netzwerkname** angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.

## <a name="enterprise"></a>Enterprise

- **WLAN-Typ**: Wählen Sie **Unternehmen** aus.
- **SSID**: Geben Sie den **Bezeichner des Dienst Satzes**ein. Dies ist der tatsächliche Name des drahtlos Netzwerks, mit dem Geräte eine Verbindung herstellen. Den Benutzern wird beim Auswählen der Verbindung jedoch nur der **Netzwerkname** angezeigt, den Sie konfiguriert haben.
- **Automatisch verbinden**: Wählen Sie **Aktivieren** aus, um automatisch eine Verbindung mit diesem Netzwerk herzustellen, wenn das Gerät in Reichweite ist. Wählen Sie **Deaktivieren** aus, um zu verhindern, dass sich Geräte automatisch verbinden.
- **Ausgeblendetes Netzwerk**: Wählen Sie **Aktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät auszublenden. Die SSID wird nicht übertragen. Wählen Sie **Deaktivieren** aus, um dieses Netzwerk in der Liste der verfügbaren Netzwerke auf dem Gerät anzuzeigen.
- **EAP-Typ**: Wählen Sie den EAP-Typ (Extensible Authentication Protocol) zum Authentifizieren von geschützten Drahtlosverbindungen aus. Folgende Optionen sind verfügbar: 

  - **EAP-TLS**: Machen Sie außerdem die folgenden Angaben:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server angezeigt, wenn der Client eine Verbindung mit dem Netzwerk herstellt. Die Verbindung wird authentifiziert.

    - **Clientauthentifizierung** - **Clientzertifikat zur Clientauthentifizierung (Identitätszertifikat)** : Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

    - **Identitätsschutz (äußere Identität)** : Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet wird. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

  - **EAP-TTLS**: Machen Sie außerdem die folgenden Angaben:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server angezeigt, wenn der Client eine Verbindung mit dem Netzwerk herstellt. Die Verbindung wird authentifiziert.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Methode (innere Identität)** : Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN konfiguriert ist. Folgende Optionen sind verfügbar:

          - **Unverschlüsseltes Kennwort (PAP)**
          - **Challenge Handshake Authentication-Protokoll (CHAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP, Version 2 (MS-CHAP v2)**

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

      - **Identitätsschutz (äußere Identität)** : Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet wird. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

  - **PEAP**: Geben Sie außerdem Folgendes ein:

    - **Serververtrauensstellung** - **Stammzertifikat zur Servervalidierung**: Wählen Sie ein vorhandenes vertrauenswürdiges Stammzertifikatsprofil aus. Dieses Zertifikat wird dem Server angezeigt, wenn der Client eine Verbindung mit dem Netzwerk herstellt. Die Verbindung wird authentifiziert.

    - **Clientauthentifizierung**: Wählen Sie eine **Authentifizierungsmethode** aus. Folgende Optionen sind verfügbar:

      - **Benutzername und Kennwort**: Fordern Sie den Benutzer zur Eingabe des Benutzernamens und Kennworts für die Authentifizierung der Verbindung auf. Geben Sie außerdem Folgendes ein:
        - **Nicht-EAP-Methode zur Authentifizierung (innere Identität)** : Wählen Sie aus, wie Sie die Verbindung authentifizieren möchten. Achten Sie darauf, dass Sie das gleiche Protokoll auswählen, das auch in Ihrem WLAN konfiguriert ist. Folgende Optionen sind verfügbar:

          - **Keine**
          - **Microsoft CHAP, Version 2 (MS-CHAP v2)**

      - **Zertifikate**: Wählen Sie das SCEP- oder PKCS-Clientzertifikatsprofil aus, das auch auf dem Gerät bereitgestellt wird. Dieses Zertifikat ist die Identität, die das Gerät dem Server zur Authentifizierung der Verbindung bereitstellt.

      - **Identitätsschutz (äußere Identität)** : Geben Sie den Text ein, der als Antwort auf eine EAP-Identitätsanforderung gesendet wird. Dieser Text kann einen beliebigen Wert haben, z.B. `anonymous`. Während der Authentifizierung wird zuerst diese anonyme Identität gesendet und anschließend die echte Kennung über einen sicheren Tunnel.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. [Weisen Sie dieses Profil nun zu.](device-profile-assign.md)

## <a name="more-resources"></a>Weitere Ressourcen

- Verschaffen Sie sich eine [Übersicht über WLAN-Einstellungen](wi-fi-settings-configure.md) auf unterschiedlichen Plattformen.

- Verwenden Sie Android Enterprise- oder Android-Kioskgeräte? Wenn ja, sehen Sie sich die [WLAN-Einstellungen für Android Enterprise-Geräte und dedizierte Geräte](wi-fi-settings-android-enterprise.md) an.
