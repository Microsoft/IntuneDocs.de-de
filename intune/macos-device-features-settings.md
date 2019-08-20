---
title: macOS-Gerätefunktionseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sehen Sie sich die Einstellungen zur Konfiguration von macOS-Geräten für AirPrint an, und passen Sie das Anmeldefenster so an, dass die Ein-/Ausschaltflächen in Microsoft Intune ein- oder ausgeblendet werden. Beachten Sie die Schritte zum Abrufen der IP-Adresse, des Pfad und der Porteinstellungen eines AirPrint-Servers in Ihrem Netzwerk. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil, um macOS-Gerätefunktionen zu konfigurieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63f2832dd321425efe8092f1bb12dd0d479ef71b
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69549932"
---
# <a name="macos-device-feature-settings-in-intune"></a>macOS-Gerätefunktionseinstellungen in Intune

Intune bietet einige integrierte Einstellungen zum Anpassen von Features auf Ihren macOS-Geräten. In diesem Artikel werden diese Einstellungen mit ihren Funktionsbeschreibungen aufgeführt. Außerdem werden die Schritte zum Abrufen von IP-Adresse, Pfad und Port von AirPrint-Druckern, die die Terminal-App (Emulator) nutzen, aufgeführt.

Diese Funktion gilt für:

- macOS

Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) können Sie mit diesen Einstellungen ein Banner erstellen, wählen, wie sich Benutzer anmelden, einen AirPrint-Server hinzufügen und vieles mehr.

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren macOS-Geräten zugewiesen oder bereitgestellt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein macOS-Gerätekonfigurationsprofil](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **IP-Adresse**: Geben Sie die IPv4- oder IPv6-Adresse des Druckers ein. Wenn Sie den Hostnamen verwenden, um Drucker zu identifizieren, erhalten Sie die IP-Adresse, indem Sie den Drucker in der Terminal-App pingen. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
- **Pfad**: Geben Sie den Pfad des Druckers ein. Der Pfad ist für Drucker in Ihrem Netzwerk in der Regel `ipp/print`. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
- **Port** (iOS 11.0 und höher): Geben Sie den Lauschport des AirPrint-Ziels ein. Wenn Sie diese Eigenschaft leer lassen, verwendet AirPrint den Standardport.
- **TLS** (iOS 11.0 und höher): Klicken Sie auf **Aktivieren**, um AirPrint-Verbindungen mit Transport Layer Security (TLS) zu schützen.

**Fügen** Sie den AirPrint-Server hinzu. Sie können viele AirPrint-Server hinzufügen.

- **Importieren** (optional): Sie können auch eine durch Trennzeichen getrennte Datei (CSV) **importieren**, die eine Liste mit AirPrint-Druckern enthält. Nachdem Sie AirPrint-Drucker in Intune hinzugefügt haben, können Sie diese Liste **Exportieren**.

Klicken Sie auf **OK**, um die Einstellungen zu speichern.

### <a name="get-the-ip-address-and-path"></a>Abrufen von IP-Adresse und Pfad

Um AirPrinter-Server hinzuzufügen, benötigen Sie die IP-Adresse des Druckers, den Ressourcenpfad und den Port. Die folgenden Schritte zeigen Ihnen, wie Sie diese Informationen abrufen.

1. Öffnen Sie das **Terminal** auf einem Mac, der mit dem gleichen lokalen Netzwerk (Subnetz) verbunden ist wie die AirPrint-Drucker (über **/Anwendungen/Hilfsprogramme**).
2. Geben Sie in der Terminal-App `ippfind` ein, und wählen Sie „Eingabe“ aus.

    Beachten Sie die Druckerinformationen. Es könnte z.B. `ipp://myprinter.local.:631/ipp/port1` zurückgegeben werden. Der erste Teil ist der Name des Druckers. Der letzte Teil (`ipp/port1`) ist der Pfad der Ressource.

3. Geben Sie im Terminal `ping myprinter.local` ein, und wählen Sie „Eingabe“ aus.

   Beachten Sie die IP-Adresse. Es könnte z.B. `PING myprinter.local (10.50.25.21)` zurückgegeben werden.

4. Verwenden Sie die Werte von IP-Adresse und Ressourcenpfad. In diesem Beispiel ist die IP-Adresse `10.50.25.21` und der Ressourcenpfad `/ipp/port1`.

## <a name="login-items"></a>Anmelde Elemente

- **Dateien, Ordner und benutzerdefinierte apps**: **fügen** Sie den Pfad einer Datei, eines Ordners, einer benutzerdefinierten APP oder einer System-App hinzu, die Sie öffnen möchten, wenn sich ein Benutzer am Gerät anmeldet. System-Apps oder apps, die für Ihre Organisation erstellt oder angepasst wurden, `Applications` befinden sich in der Regel im Ordner `/Applications/AppName.app`mit einem Pfad, der ähnelt. 

  Sie können viele Dateien, Ordner und apps hinzufügen. Geben Sie beispielsweise Folgendes ein:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Wenn Sie eine APP, einen Ordner oder eine Datei hinzufügen, geben Sie den richtigen Pfad ein. Nicht alle Elemente befinden sich im `Applications` Ordner. Wenn ein Benutzer ein Element von einem Speicherort an einen anderen verschiebt, ändert sich der Pfad. Dieses verschoderte Element wird nicht geöffnet, wenn sich der Benutzer anmeldet.

## <a name="login-window"></a>Fenster „Anmeldung“

### <a name="window-layout"></a>Fensterlayout

- **Zusätzliche Informationen in der Menüleiste anzeigen**: Wenn der Zeitbereich auf der Menüleiste ausgewählt ist, zeigt **Zulassen** den Hostnamen und die macOS-Version. Bei Wahl der Standardeinstellung **Nicht konfiguriert** werden diese Informationen nicht auf der Menüleiste angezeigt.
- **Banner**: Geben Sie eine Meldung ein, die auf dem Anmeldebildschirm des Geräts gezeigt wird. Geben Sie beispielsweise Ihre Unternehmensinformationen, eine Begrüßungsmeldung, Informationen bei Verlust eines Geräts usw. ein.
- **Anmeldeformat wählen**: Wählen Sie, wie sich Benutzer am Gerät anmelden. Folgende Optionen sind verfügbar:
  - **Nach Benutzernamen und Kennwort fragen** (Standard): Erfordert, dass Benutzer einen Benutzernamen und ein Kennwort eingeben.
  - **Alle Benutzer auflisten und Kennwort anfordern**: Erfordert, dass Benutzer ihren Benutzernamen in einer Benutzerliste auswählen und dann ihr Kennwort eingeben. Konfigurieren Sie auch Folgendes:

    - **Lokale Benutzer**: Bei Wahl von **Ausblenden** werden die lokalen Benutzerkonten nicht in der Benutzerliste angezeigt, wozu auch die Standard- und die Administratorkonten gehören können. Nur die Netzwerk- und Systembenutzerkonten werden gezeigt. **Nicht konfiguriert** (Standard): Zeigt die lokalen Benutzerkonten in der Benutzerliste.
    - **Mobile Konten**: Bei Wahl von **Ausblenden** werden mobile Konten nicht in der Benutzerliste angezeigt. **Nicht konfiguriert** (Standard): Zeigt die mobilen Konten in der Benutzerliste. Einige mobile Konten werden möglicherweise als Netzwerkbenutzer angezeigt.
    - **Netzwerkbenutzer**: Klicken Sie auf **Anzeigen**, um die Netzwerkbenutzer in der Benutzerliste aufzulisten. **Nicht konfiguriert** (Standard): Zeigt die Konten von Netzwerkbenutzern nicht in der Benutzerliste an.
    - **Administratorbenutzer**: Bei Wahl von **Ausblenden** werden Administratorbenutzerkonten nicht in der Benutzerliste angezeigt. **Nicht konfiguriert** (Standard): Zeigt die Administratorbenutzerkonten in der Benutzerliste an.
    - **Andere Benutzer**: Klicken Sie auf **Anzeigen**, um **andere** Benutzer in der Benutzerliste aufzulisten. **Nicht konfiguriert** (Standard): Zeigt andere Benutzerkonten nicht in der Benutzerliste an.

### <a name="login-screen-power-settings"></a>Energieeinstellungen auf dem Anmeldebildschirm

- **Schaltfläche „Herunterfahren“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Herunterfahren“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Herunterfahren“ gezeigt.
- **Schaltfläche „Neu starten“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Neu starten“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Neu starten“ gezeigt.
- **Schaltfläche „Standby“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Standby“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Standby“ gezeigt.

### <a name="other"></a>Andere

- **Benutzeranmeldung über Konsole deaktivieren**: Bei Wahl von **Deaktivieren** wird die macOS-Befehlszeile zum Anmelden ausgeblendet. **Deaktivieren** Sie diese Einstellung für typische Benutzer. Die Standardeinstellung **Nicht konfiguriert** ermöglicht fortgeschrittenen Benutzern die Anmeldung über die macOS-Befehlszeile. Um in den Konsolenmodus zu wechseln, müssen Benutzer `>console` in das Feld „Benutzername“ eingeben und sich im Konsolenfenster authentifizieren.

### <a name="apple-menu"></a>Apple-Menü

Nachdem sich Benutzer bei den Geräten angemeldet haben, beeinflussen die folgenden Einstellungen ihre Möglichkeiten.

- **Herunterfahren deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Herunterfahren** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Herunterfahren** auf dem Gerät.
- **Neustart deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Neu starten** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Neu starten** auf dem Gerät.
- **Ausschalten deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Ausschalten** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Ausschalten** auf dem Gerät.
- **Abmelden deaktivieren** (macOS 10.13 und höher): Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Abmelden** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Abmelden** auf dem Gerät.
- **Sperrbildschirm deaktivieren** (macOS 10.13 und höher): Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Sperrbildschirm** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Sperrbildschirm** auf dem Gerät.

Klicken Sie auf **OK**, um die Einstellungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte

- Zeigen Sie alle Einstellungen für [iOS](ios-device-features-settings.md)-Geräte an.
- [Zuweisen dieses Profils](device-profile-assign.md) zu Ihren Gruppen und das [Überwachen seines Status](device-profile-monitor.md).
