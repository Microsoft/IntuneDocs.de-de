---
title: macOS-Gerätefunktionseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie alle Einstellungen zum Konfigurieren von macOS-Geräten für AirPrint in Microsoft Intune. Beachten Sie auch die Schritte zum Abrufen der IP-Adresse, des Pfad und der Porteinstellungen eines AirPrint-Servers in Ihrem Netzwerk. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil, um macOS-Geräte zur Verwendung von AirPrint-Servern in Ihrem Netzwerk zu konfigurieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.openlocfilehash: cdc5f5fe2c94dee2349cab777c7671c2673f52b2
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54832321"
---
# <a name="macos-device-feature-settings-in-intune"></a>macOS-Gerätefunktionseinstellungen in Intune

Intune umfasst einige integrierte Einstellungen, um macOS-Benutzern das Drucken auf AirPrint-Druckern in Ihrem Netzwerk zu ermöglichen. In diesem Artikel werden diese Einstellungen mit ihren Funktionsbeschreibungen aufgeführt. Außerdem werden die Schritte zum Abrufen von IP-Adresse, Pfad und Port von AirPrint-Druckern, die die Terminal-App (Emulator) nutzen, aufgeführt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein macOS-Gerätekonfigurationsprofil](device-features-configure.md).

## <a name="airprint-settings"></a>AirPrint-Einstellungen

1. Wählen Sie in **Einstellungen** die Option **AirPrint** aus. Geben Sie die folgenden Eigenschaften des AirPrint-Servers ein:

    - **IP-Adresse**: Geben Sie die IPv4- oder IPv6-Adresse des Druckers ein. Wenn Sie den Hostnamen verwenden, um Drucker zu identifizieren, erhalten Sie die IP-Adresse, indem Sie den Drucker in der Terminal-App pingen. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
    - **Pfad:** Geben Sie den Pfad des Druckers ein. Der Pfad ist für Drucker in Ihrem Netzwerk in der Regel `ipp/print`. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
    - **Port**: Geben Sie den Lauschport des AirPrint-Ziels ein. Wenn Sie diese Eigenschaft leer lassen, verwendet AirPrint den Standardport. In iOS 11.0 und höher verfügbar.
    - **TLS**: Wählen Sie **Aktivieren**, um AirPrint-Verbindungen mit Transport Layer Security (TLS) zu sichern. In iOS 11.0 und höher verfügbar.

2. Wählen Sie **Hinzufügen** aus. Der AirPrint-Server wird der Liste hinzugefügt. Sie können viele AirPrint-Server hinzufügen.

    Sie können auch eine durch Trennzeichen getrennte Datei (CSV) **Importieren**, die eine Liste der AirPrint-Drucker enthält. Nachdem Sie AirPrint-Drucker in Intune hinzugefügt haben, können Sie diese Liste **Exportieren**.

3. Klicken Sie zum Speichern Ihrer Liste auf **OK**.

## <a name="get-the-ip-address-and-path"></a>Abrufen von IP-Adresse und Pfad

Um AirPrinter-Server hinzuzufügen, benötigen Sie die IP-Adresse des Druckers, den Ressourcenpfad und den Port. Die folgenden Schritte zeigen Ihnen, wie Sie diese Informationen abrufen.

1. Öffnen Sie das **Terminal** auf einem Mac, der mit dem gleichen lokalen Netzwerk (Subnetz) verbunden ist wie die AirPrint-Drucker (über **/Anwendungen/Hilfsprogramme**).
2. Geben Sie in der Terminal-App `ippfind` ein, und wählen Sie „Eingabe“ aus.

    Beachten Sie die Druckerinformationen. Es könnte z.B. `ipp://myprinter.local.:631/ipp/port1` zurückgegeben werden. Der erste Teil ist der Name des Druckers. Der letzte Teil (`ipp/port1`) ist der Pfad der Ressource.

3. Geben Sie im Terminal `ping myprinter.local` ein, und wählen Sie „Eingabe“ aus.

   Beachten Sie die IP-Adresse. Es könnte z.B. `PING myprinter.local (10.50.25.21)` zurückgegeben werden.

4. Verwenden Sie die Werte von IP-Adresse und Ressourcenpfad. In diesem Beispiel ist die IP-Adresse `10.50.25.21` und der Ressourcenpfad `/ipp/port1`.

## <a name="next-steps"></a>Nächste Schritte

- Zeigen Sie alle Einstellungen für [iOS](ios-device-features-settings.md)-Geräte an.
- Weisen Sie dieses Profil Gruppen zu; siehe [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md).