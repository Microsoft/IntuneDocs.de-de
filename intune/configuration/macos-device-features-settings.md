---
title: macOS-Gerätefunktionseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sehen Sie sich die Einstellungen zur Konfiguration von macOS-Geräten für AirPrint an, und passen Sie das Anmeldefenster so an, dass die Ein-/Ausschaltflächen in Microsoft Intune ein- oder ausgeblendet werden. Beachten Sie die Schritte zum Abrufen der IP-Adresse, des Pfad und der Porteinstellungen eines AirPrint-Servers in Ihrem Netzwerk. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil, um macOS-Gerätefunktionen zu konfigurieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df5b53be159fd082090e61fd736e4c9329644c85
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512737"
---
# <a name="macos-device-feature-settings-in-intune"></a>macOS-Gerätefunktionseinstellungen in Intune

Intune bietet einige integrierte Einstellungen zum Anpassen von Features auf Ihren macOS-Geräten. Administratoren können beispielsweise AirPrint-Drucker hinzufügen, die Art der Benutzeranmeldung auswählen, die Energiesteuerung konfigurieren, die SSO-Authentifizierung verwenden und mehr.

Nutzen Sie diese Features, um macOS-Geräte im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) zu verwalten.

In diesem Artikel werden diese Einstellungen mit ihren Funktionsbeschreibungen aufgeführt. Außerdem werden die Schritte zum Abrufen von IP-Adresse, Pfad und Port von AirPrint-Druckern, die die Terminal-App (Emulator) nutzen, aufgeführt. Weitere Informationen zu Gerätefeatures finden Sie unter [Hinzufügen von Einstellungen für iOS/iPadOS- oder macOS-Gerätefunktionen in Intune](device-features-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein macOS-Gerätekonfigurationsprofil](device-features-configure.md).

> [!NOTE]
> Diese Einstellungen gelten für verschiedene Registrierungstypen, wobei einige Einstellungen für alle Registrierungsoptionen gelten. Weitere Informationen zu den verschiedenen Registrierungstypen finden Sie unter [macOS-Registrierung](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und automatische Geräteregistrierung 

- **IP-Adresse**: Geben Sie die IPv4- oder IPv6-Adresse des Druckers ein. Wenn Sie den Hostnamen verwenden, um Drucker zu identifizieren, erhalten Sie die IP-Adresse, indem Sie den Drucker in der Terminal-App pingen. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
- **Pfad:** Geben Sie den Pfad des Druckers ein. Der Pfad ist für Drucker in Ihrem Netzwerk in der Regel `ipp/print`. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
- **Port** (iOS 11.0+, iPadOS 13.0+): Geben Sie den Lauschport des AirPrint-Ziels ein. Wenn Sie diese Eigenschaft leer lassen, verwendet AirPrint den Standardport.
- **TLS** (iOS 11.0+, iPadOS 13.0+): Wählen Sie **Aktivieren** aus, um AirPrint-Verbindungen mit Transport Layer Security (TLS) zu sichern.

- **Fügen** Sie den AirPrint-Server hinzu. Sie können viele AirPrint-Server hinzufügen.

Sie können auch eine durch Trennzeichen getrennte Datei (CSV) **Importieren**, die eine Liste der AirPrint-Drucker enthält. Nachdem Sie AirPrint-Drucker in Intune hinzugefügt haben, können Sie diese Liste **Exportieren**.

### <a name="get-the-ip-address-and-path"></a>Abrufen von IP-Adresse und Pfad

Um AirPrinter-Server hinzuzufügen, benötigen Sie die IP-Adresse des Druckers, den Ressourcenpfad und den Port. Die folgenden Schritte zeigen Ihnen, wie Sie diese Informationen abrufen.

1. Öffnen Sie das **Terminal** auf einem Mac, der mit dem gleichen lokalen Netzwerk (Subnetz) verbunden ist wie die AirPrint-Drucker (über **/Anwendungen/Hilfsprogramme**).
2. Geben Sie in der Terminal-App `ippfind` ein, und wählen Sie „Eingabe“ aus.

    Beachten Sie die Druckerinformationen. Es könnte z.B. `ipp://myprinter.local.:631/ipp/port1` zurückgegeben werden. Der erste Teil ist der Name des Druckers. Der letzte Teil (`ipp/port1`) ist der Pfad der Ressource.

3. Geben Sie im Terminal `ping myprinter.local` ein, und wählen Sie „Eingabe“ aus.

   Beachten Sie die IP-Adresse. Es könnte z.B. `PING myprinter.local (10.50.25.21)` zurückgegeben werden.

4. Verwenden Sie die Werte von IP-Adresse und Ressourcenpfad. In diesem Beispiel ist die IP-Adresse `10.50.25.21` und der Ressourcenpfad `/ipp/port1`.

## <a name="login-items"></a>Anmeldeelemente

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Dateien, Ordner und benutzerdefinierte Apps**: **Hinzufügen**: Fügen sie den Pfad zu einer Datei oder einem Ordner, eine benutzerdefinierte App oder eine System-App hinzu, die Sie öffnen möchten, wenn sich ein Benutzer beim Gerät anmeldet. System-Apps oder Apps, die für Ihre Organisation entwickelt oder angepasst wurden, befinden sich üblicherweise im Ordner `Applications` und weisen einen Pfad ähnlich wie `/Applications/AppName.app` auf. 

  Sie können zahlreiche Dateien, Ordner und Apps hinzufügen. Geben Sie beispielsweise Folgendes ein:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Wenn Sie eine App, einen Ordner oder eine Datei hinzufügen, stellen Sie sicher, dass Sie den richtigen Pfad eingeben. Nicht alle Elemente befinden sich im Ordner `Applications`. Wenn ein Benutzer ein Element von einem Speicherort an einen anderen verschiebt, ändert sich der Pfad. Dieses verschobene Element wird nicht geöffnet, wenn sich der Benutzer anmeldet.

## <a name="login-window"></a>Fenster „Anmeldung“

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und automatische Geräteregistrierung

#### <a name="window-layout"></a>Fensterlayout

- **Zusätzliche Informationen in der Menüleiste anzeigen**: Wenn der Zeitbereich auf der Menüleiste ausgewählt ist, zeigt **Zulassen** den Hostnamen und die macOS-Version an. Bei Wahl der Standardeinstellung **Nicht konfiguriert** werden diese Informationen nicht auf der Menüleiste angezeigt.
- **Banner**: Geben Sie eine Meldung ein, die auf dem Anmeldebildschirm des Geräts angezeigt wird. Geben Sie beispielsweise Ihre Unternehmensinformationen, eine Begrüßungsmeldung, Informationen bei Verlust eines Geräts usw. ein.
- **Anmeldeformat auswählen**: Wählen Sie aus, wie Benutzer sich beim Gerät anmelden können. Folgende Optionen sind verfügbar:
  - **Nach Benutzernamen und Kennwort fragen** (Standard): Erfordert, dass Benutzer einen Benutzernamen und ein Kennwort eingeben.
  - **Alle Benutzer auflisten und Kennwort anfordern**: Erfordert, dass Benutzer ihren Benutzernamen in einer Benutzerliste auswählen und dann ihr Kennwort eingeben. Konfigurieren Sie auch Folgendes:

    - **Lokale Benutzer**: Bei Wahl von **Ausblenden** werden die lokalen Benutzerkonten nicht in der Benutzerliste angezeigt, wozu auch die Standard- und die Administratorkonten gehören können. Nur die Netzwerk- und Systembenutzerkonten werden gezeigt. **Nicht konfiguriert** (Standard): Zeigt die lokalen Benutzerkonten in der Benutzerliste.
    - **Mobile Konten**: Bei Wahl von **Ausblenden** werden mobile Konten nicht in der Benutzerliste angezeigt. **Nicht konfiguriert** (Standard): Zeigt die mobilen Konten in der Benutzerliste. Einige mobile Konten werden möglicherweise als Netzwerkbenutzer angezeigt.
    - **Netzwerkbenutzer**: Klicken Sie auf **Anzeigen**, um die Netzwerkbenutzer in der Benutzerliste aufzulisten. **Nicht konfiguriert** (Standard): Zeigt die Konten von Netzwerkbenutzern nicht in der Benutzerliste an.
    - **Administratorbenutzer**: Bei Wahl von **Ausblenden** werden Administratorbenutzerkonten nicht in der Benutzerliste angezeigt. **Nicht konfiguriert** (Standard): Zeigt die Administratorbenutzerkonten in der Benutzerliste an.
    - **Andere Benutzer**: Wählen Sie **Anzeigen** aus, um **Weitere...** Benutzer in der Benutzerliste aufzulisten. **Nicht konfiguriert** (Standard): Zeigt andere Benutzerkonten nicht in der Benutzerliste an.

#### <a name="login-screen-power-settings"></a>Energieeinstellungen auf dem Anmeldebildschirm

- **Schaltfläche „Herunterfahren“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Herunterfahren“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Herunterfahren“ gezeigt.
- **Schaltfläche „Neu starten“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Neu starten“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Neu starten“ gezeigt.
- **Standbytaste**: Bei Wahl von **Ausblenden** wird die Schaltfläche „Standby“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Standby“ gezeigt.

#### <a name="other"></a>Andere

- **Benutzeranmeldung über Konsole deaktivieren**: Bei Wahl von **Deaktivieren** wird die macOS-Befehlszeile zum Anmelden ausgeblendet. **Deaktivieren** Sie diese Einstellung für typische Benutzer. Die Standardeinstellung **Nicht konfiguriert** ermöglicht fortgeschrittenen Benutzern die Anmeldung über die macOS-Befehlszeile. Um in den Konsolenmodus zu wechseln, müssen Benutzer `>console` in das Feld „Benutzername“ eingeben und sich im Konsolenfenster authentifizieren.

#### <a name="apple-menu"></a>Apple-Menü

Nachdem sich Benutzer bei den Geräten angemeldet haben, beeinflussen die folgenden Einstellungen ihre Möglichkeiten.

- **Herunterfahren deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Herunterfahren** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Herunterfahren** auf dem Gerät.
- **Neustart deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Neu starten** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Neu starten** auf dem Gerät.
- **Ausschalten deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Ausschalten** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Ausschalten** auf dem Gerät.
- **Abmelden deaktivieren** (macOS 10.13 und höher): Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Abmelden** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Abmelden** auf dem Gerät.
- **Sperrbildschirm deaktivieren** (macOS 10.13 und höher): Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Bildschirm sperren** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Sperrbildschirm** auf dem Gerät.

## <a name="single-sign-on-app-extension"></a>App-Erweiterung für einmaliges Anmelden

Diese Funktion gilt für:

- macOS 10.15 und neuer

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen 

- **Typ der SSO-App-Erweiterung**: Wählen Sie den Typ der SSO-App-Erweiterung aus. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert**: Es werden keine App-Erweiterungen verwendet. Um eine App-Erweiterung zu deaktivieren, ändern Sie den Typ der SSO-App-Erweiterung in **Nicht konfiguriert**.
  - **Umleitung**: Verwenden Sie eine generische, anpassbare App-Erweiterung für die Umleitung, um einmaliges Anmelden (SSO) mit modernen Authentifizierungsflows zu unterstützen. Stellen Sie sicher, dass Sie die Erweiterung und die Team-ID für die App-Erweiterung Ihrer Organisation kennen.
  - **Anmeldeinformationen**: Verwenden Sie eine generische, anpassbare App-Erweiterung für Anmeldeinformationen, um einmaliges Anmelden (SSO) mit Challenge-Response-Authentifizierungsflows zu unterstützen. Stellen Sie sicher, dass Sie die Erweiterungs-ID und die Team-ID für die SSO-App-Erweiterung Ihrer Organisation kennen.  
  - **Kerberos**: Verwenden Sie die integrierte Kerberos-Erweiterung von Apple, die in macOS Catalina 10.15 und höher enthalten ist. Bei dieser Option handelt es sich um eine Kerberos-spezifische Version der App-Erweiterung vom Typ **Anmeldeinformationen**.

  > [!TIP]
  > Mit den Typen **Umleitung** und **Anmeldeinformationen** fügen Sie eigene Konfigurationswerte hinzu, die über die Erweiterung übergeben werden. Erwägen Sie bei Auswahl von **Anmeldeinformationen** die Verwendung integrierter Konfigurationseinstellungen, die von Apple für den Typ **Kerberos** bereitgestellt werden.

- **Erweiterungs-ID** (Umleitung und Anmeldeinformationen): Geben Sie den Bundlebezeichner ein, der Ihre SSO-App-Erweiterung identifiziert, z. B. `com.apple.ssoexample`.
- **Team-ID** (Umleitung und Anmeldeinformationen): Geben Sie die Team-ID Ihrer SSO-App-Erweiterung ein. Eine Team-ID ist eine aus 10 Zeichen bestehende alphanumerische (Ziffern und Buchstaben) Zeichenfolge, die von Apple generiert wird, z. B. `ABCDE12345`. 

  Auf der [Seite zur Team-ID-Ermittlung](https://help.apple.com/developer-account/#/dev55c3c710c) (öffnet die Website von Apple) finden Sie weitere Informationen.

- **Bereich** (Anmeldeinformationen und Kerberos): Geben Sie den Namen Ihres Authentifizierungsbereichs ein. Der Bereichsname sollte groß geschrieben werden, z. B. `CONTOSO.COM`. In der Regel ist Ihr Bereichsname mit dem DNS-Domänennamen identisch, besteht aber nur aus Großbuchstaben.

- **Domänen** (Anmeldeinformationen und Kerberos): Geben Sie die Domänen- oder Hostnamen der Standorte ein, die über SSO authentifiziert werden können. Wenn Ihre Website beispielsweise `mysite.contoso.com` lautet, ist `mysite` der Hostname und `contoso.com` der Domänenname. Wenn Benutzer eine Verbindung mit einer dieser Websites herstellen, verarbeitet die App-Erweiterung die Authentifizierung. Diese Authentifizierung ermöglicht es Benutzern Face ID, Touch ID oder eine PIN/einen Passcode von Apple für die Anmeldung zu verwenden.

  - Alle Domänen in den Intune-Profilen für Ihre SSO-App-Erweiterung müssen eindeutig sein. Sie können eine Domäne nicht mehrfach in einem SSO-App-Erweiterungsprofil verwenden – selbst dann nicht, wenn Sie verschiedene Arten von SSO-App-Erweiterungen verwenden.
  - Für diese Domänen erfolgt keine Beachtung der Groß-/Kleinschreibung.

- **URLs** (nur Umleitung): Geben Sie die URL-Präfixe der Identitätsanbieter an, in deren Namen die Umleitungs-App-Erweiterung die SSO-Authentifizierung durchführt. Wenn ein Benutzer an diese URLs umgeleitet wird, greift die SSO-App-Erweiterung und fordert eine SSO-Authentifizierung an.

  - Alle URLs in Ihren Intune-SSO-Erweiterungsprofilen müssen eindeutig sein. Sie können eine Domäne nicht mehrfach in einem SSO-App-Erweiterungsprofil verwenden – selbst dann nicht, wenn Sie verschiedene Arten von SSO-App-Erweiterungen verwenden.
  - Die URLs müssen mit „http://“ oder „https://“ beginnen.

- **Zusätzliche Konfiguration** (Umleitung und Anmeldeinformationen): Geben Sie zusätzliche erweiterungsspezifische Daten ein, die an die SSO-App-Erweiterung übergeben werden sollen:
  - **Schlüssel**: Geben Sie den Namen des Elements ein, das Sie hinzufügen möchten, z. B. `user name`.
  - **Typ**: Geben Sie den Typ der Daten ein. Folgende Optionen sind verfügbar:

    - Zeichenfolge
    - Boolescher Wert: Geben Sie in **Konfigurationswert** entweder `True` oder `False` ein.
    - Ganzzahl: Geben Sie in **Konfigurationswert** eine Zahl ein.
    
  - **Wert**: Geben Sie die Daten ein.
  
  - **Hinzufügen**: Wählen Sie diese Option aus, um Ihre Konfigurationsschlüssel hinzuzufügen.

- **Verwendung des Schlüsselbunds** (nur Kerberos): Wählen Sie **Blockieren** aus, um zu verhindern, dass Kennwörter im Schlüsselbund gespeichert werden. **Nicht konfiguriert** (Standardeinstellung): Ermöglicht das Speichern von Kennwörtern im Schlüsselbund.  
- **Face ID, Touch ID oder Passcode** (nur Kerberos): Durch Festlegung auf **Erzwingen** müssen die Benutzer sich über Face ID, Touch ID oder mit ihrem Apple-Passcode bei den von Ihnen hinzugefügten Domänen anmelden. **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellung müssen sich Benutzer nicht mit biometrischen Daten oder einem Passcode anmelden.
- **Standardbereich** (nur Kerberos): Wählen Sie **Aktivieren** aus, um den von Ihnen eingegebenen **Bereich** als Standardbereich festzulegen. **Nicht konfiguriert** (Standardeinstellung): Es ist kein Standardbereich festgelegt.

  > [!TIP]
  > - **Aktivieren** Sie diese Einstellung, wenn Sie mehrere Kerberos-SSO-App-Erweiterungen in Ihrer Organisation konfigurieren.
  > - **Aktivieren** Sie diese Einstellung, wenn Sie mehrere Bereiche verwenden. Der von Ihnen eingegebene **Bereich** wird als Standardbereich festgelegt.
  > - Wenn Sie nur über einen Bereich verfügen, behalten Sie die Einstellung **Nicht konfiguriert** (Standardeinstellung) bei.

- **AutoErmittlung** (nur Kerberos): Bei Festlegung auf **Blockieren** verwendet die Kerberos-Erweiterung nicht automatisch LDAP und DNS, um den Namen des zugehörigen Active Directory-Standorts zu bestimmen. **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellung kann die Erweiterung den Namen des Active Directory-Standorts automatisch ermitteln.
- **Kennwortänderungen** (nur Kerberos): Mit **Blockieren** werden Benutzer daran gehindert, die zur Anmeldung bei den von Ihnen eingegebenen Domänen verwendeten Kennwörter zu ändern. **Nicht konfiguriert** (Standardeinstellung): Das Ändern von Kennwörtern ist gestattet.  
- **Kennwortsynchronisierung** (nur Kerberos): Wählen Sie **Aktivieren** aus, um die lokalen Kennwörter Ihrer Benutzer mit Azure AD zu synchronisieren. **Nicht konfiguriert** (Standardeinstellung): Deaktiviert die Kennwortsynchronisierung mit Azure AD. Verwenden Sie diese Einstellung als Alternative oder Backuplösung für das einmalige Anmelden (SSO). Diese Einstellung funktioniert nicht, wenn Benutzer mit einem mobilen Apple-Konto angemeldet sind.
- **Windows Server Active Directory-Kennwortkomplexität** (nur Kerberos): Durch Auswahl von **Erzwingen** müssen Benutzerkennwörter die Kennwortkomplexitätsanforderungen von Active Directory erfüllen. Weitere Informationen finden Sie unter [Kennwort muss Komplexitätsvoraussetzungen entsprechen](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements). **Nicht konfiguriert** (Standardeinstellung): Die Benutzer müssen nicht die Active Directory-Kennwortanforderungen erfüllen.
- **Mindestkennwortlänge** (nur Kerberos): Geben Sie die Mindestanzahl von Zeichen ein, aus denen ein Benutzerkennwort bestehen muss. **Nicht konfiguriert** (Standardeinstellung): Es wird keine Mindestlänge für Benutzerkennwörter erzwungen.
- **Limit für die Wiederverwendung von Kennwörtern** (nur Kerberos): Geben Sie die Anzahl neuer Kennwörter ein (1–24), die verwendet werden müssen, bis ein vorheriges Kennwort erneut für die Domäne verwendet werden kann. **Nicht konfiguriert** (Standardeinstellung): Es wird kein Limit für die Wiederverwendung von Kennwörtern erzwungen.
- **Mindestkennwortalter** (nur Kerberos): Geben Sie die Anzahl von Tagen ein, die ein Kennwort für die Domäne verwendet werden muss, bevor ein Benutzer es ändern kann. **Nicht konfiguriert** (Standardeinstellung): Es wird kein Mindestkennwortalter erzwungen, bevor ein Kennwort geändert werden kann.
- **Benachrichtigung über Kennwortablauf** (nur Kerberos): Geben Sie an, wie viele Tage vor Ablauf eines Kennworts Benutzer über den bevorstehenden Ablauf ihres Kennworts benachrichtigt werden. **Nicht konfiguriert** (Standardeinstellung): `15` Tage.
- **Kennwortablauf** (nur Kerberos): Geben Sie die Anzahl der Tage an, bis das Gerätekennwort geändert werden muss. **Nicht konfiguriert** (Standardeinstellung): Benutzerkennwörter laufen nie ab.
- **URL für Kennwortänderung** (nur Kerberos): Geben Sie die URL ein, die gestartet wird, wenn der Benutzer eine Kerberos-Kennwortänderung einleitet.
- **Prinzipalname** (nur Kerberos): Geben Sie den Benutzernamen des Kerberos-Prinzipals ein. Sie müssen den Bereichsnamen nicht einschließen. In `user@contoso.com` lautet der Prinzipalname beispielsweise `user`, und `contoso.com` ist der Bereichsname.

  > [!TIP]
  > - Sie können auch Variablen im Prinzipalnamen verwenden, indem Sie geschweifte Klammern `{{ }}` eingeben. Geben Sie z. B. `Username: {{username}}` ein, um den Benutzernamen anzuzeigen. 
  > - Verwenden Sie die Variablenersetzung jedoch mit Bedacht, da die Variablen in der Benutzeroberfläche nicht validiert werden und die Groß- und Kleinschreibung berücksichtigt wird. Stellen Sie sicher, dass die eingegebenen Informationen korrekt sind.
  
- **Active Directory-Standortcode** (nur Kerberos): Geben Sie den Namen des Active Directory-Standorts ein, der von der Kerberos-Erweiterung verwendet werden soll. Möglicherweise müssen Sie diesen Wert nicht ändern, weil die Kerberos-Erweiterung den Active Directory-Standortcode ggf. automatisch ermittelt.
- **Cachename** (nur Kerberos): Geben Sie den GSS-Namen (Generic Security Services) für den Kerberos-Cache ein. Dieser Wert muss höchstwahrscheinlich nicht festgelegt werden.  
- **Meldung zu Kennwortanforderungen** (nur Kerberos): Geben Sie eine Textversion der Kennwortanforderungen Ihrer Organisation ein, die den Benutzern angezeigt wird. Die Meldung wird angezeigt, wenn Sie keine Active Directory-Kennwortkomplexitätsanforderungen erzwingen oder keine Mindestkennwortlänge eingeben.  
- **App-Bundle-IDs** (nur Kerberos): Mit **Hinzufügen** werden die App-Bundle-IDs hinzugefügt, für die auf Ihren Geräten SSO verwendet werden soll. Diese Apps erhalten Zugriff auf das Kerberos-TGT (Ticket Granting Ticket) sowie das Authentifizierungsticket und authentifizieren Benutzer für Dienste, für die sie autorisiert sind.
- **Domänenbereichszuordnung** (nur Kerberos): Mit **Hinzufügen** werden die Domänen-DNS-Suffixe hinzugefügt, die Ihrem Bereich zugeordnet werden sollen. Verwenden Sie diese Einstellung, wenn die DNS-Namen der Hosts nicht mit dem Bereichsnamen identisch sind. Wahrscheinlich ist es nicht erforderlich, diese Zuordnung zwischen benutzerdefinierter Domäne und Bereich zu erstellen.
- **PKINIT-Zertifikat** (nur Kerberos): Durch **Auswählen** legen Sie das PKINIT-Zertifikat (Public Key Cryptography for Initial Authentication) fest, das für die Kerberos-Authentifizierung verwendet werden kann. Sie können aus [PKCS](../protect/certficates-pfx-configure.md)- oder [SCEP](../protect/certificates-scep-configure.md)-Zertifikaten auswählen, die Sie in Intune hinzugefügt haben. Weitere Informationen zu Zertifikaten finden Sie unter [Verwenden von Zertifikaten zur Authentifizierung in Microsoft Intune](../protect/certificates-configure.md).

## <a name="associated-domains"></a>Zugeordnete Domänen

In Intune können Sie folgende Aktionen ausführen:

- Hinzufügen von mehreren Zuordnungen zwischen Apps und Domänen
- Zuordnen von mehreren Domänen zur selben App

Diese Funktion gilt für:

- macOS 10.15 und neuer

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **App-ID**: Geben Sie den App-Bezeichner der App ein, die einer Website zugeordnet werden soll. Der App-Bezeichner enthält die Team-ID und eine Bundle-ID: `TeamID.BundleID`.

  Die Team-ID ist eine aus 10 Zeichen bestehende alphanumerische (Ziffern und Buchstaben) Zeichenfolge, die von Apple für Ihre App-Entwickler generiert wird, z. B. `ABCDE12345`. Auf der [Seite zur Team-ID-Ermittlung](https://help.apple.com/developer-account/#/dev55c3c710c)  (öffnet die Website von Apple) finden Sie weitere Informationen.

  Die Bundle-ID identifiziert die App eindeutig und ist üblicherweise in umgekehrter Domänennamennotation formatiert. Beispielsweise lautet die Bundle-ID des Finders `com.apple.finder`. Um die Bundle-ID zu finden, verwenden Sie das AppleScript-Skript im Terminal:

  `osascript -e 'id of app "ExampleApp"'`

- **Domäne**: Geben Sie die Websitedomäne ein, die einer App zugeordnet werden soll. Die Domäne enthält einen Diensttyp und einen vollqualifizierten Hostnamen, beispielsweise `webcredentials:www.contoso.com`.

  Sie können alle Unterdomänen einer zugeordneten Domäne einschließen, indem Sie vor dem Domänennamen `*.` (Sternchen-Platzhalter und Punkt) eingeben. Der Punkt ist erforderlich. Exakte Domänen haben eine höhere Priorität als Platzhalterdomänen. Daher werden Muster aus übergeordneten Domänen abgeglichen, *wenn* in der vollqualifizierten Unterdomäne keine Übereinstimmung gefunden wird.

  Der Diensttyp kann wie folgt lauten:

  - **authsrv**: App-Erweiterung für einmaliges Anmelden
  - **applink**: Universeller Link
  - **webcredentials**: AutoAusfüllen von Kennwörtern

- **Hinzufügen**: Wählen Sie diese Option aus, um Ihre Apps und zugeordneten Domänen hinzuzufügen.

> [!TIP]
> Wechseln Sie zur Problembehandlung auf Ihrem macOS-Gerät zu **Systemeinstellungen** > **Profile**. Vergewissern Sie sich, dass das erstellte Profil in der Liste der Geräteprofile aufgeführt ist. Wenn das Profil aufgelistet wird, stellen Sie sicher, dass **Konfiguration der zugeordneten Domänen** im Profil enthalten ist und die richtige App-ID und die richtigen Domänen aufweist.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können außerdem Gerätefeatures für [iOS/iPadOS](ios-device-features-settings.md) konfigurieren.
