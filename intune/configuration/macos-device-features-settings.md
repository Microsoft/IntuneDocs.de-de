---
title: macOS-Gerätefunktionseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sehen Sie sich die Einstellungen zur Konfiguration von macOS-Geräten für AirPrint an, und passen Sie das Anmeldefenster so an, dass die Ein-/Ausschaltflächen in Microsoft Intune ein- oder ausgeblendet werden. Beachten Sie die Schritte zum Abrufen der IP-Adresse, des Pfad und der Porteinstellungen eines AirPrint-Servers in Ihrem Netzwerk. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil, um macOS-Gerätefunktionen zu konfigurieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2019
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
ms.openlocfilehash: 48cca2c894067439943bdfff33b953463e513490
ms.sourcegitcommit: e9cf372711ff186ed468b01a9204631a139bd8e5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776888"
---
# <a name="macos-device-feature-settings-in-intune"></a>macOS-Gerätefunktionseinstellungen in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune bietet einige integrierte Einstellungen zum Anpassen von Features auf Ihren macOS-Geräten. Administratoren können z. b. airprint-Drucker hinzufügen, auswählen, wie sich Benutzer anmelden, die Energiesteuerung konfigurieren, Single Sign-on Authentifizierung verwenden und vieles mehr.

Nutzen Sie diese Features, um macOS-Geräte im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) zu verwalten.

In diesem Artikel werden diese Einstellungen mit ihren Funktionsbeschreibungen aufgeführt. Außerdem werden die Schritte zum Abrufen von IP-Adresse, Pfad und Port von AirPrint-Druckern, die die Terminal-App (Emulator) nutzen, aufgeführt. Weitere Informationen zu Gerätefunktionen finden [Sie unter Hinzufügen von IOS-oder macOS-Geräte Funktionseinstellungen](device-features-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein macOS-Gerätekonfigurationsprofil](device-features-configure.md).

> [!NOTE]
> Diese Einstellungen gelten für verschiedene Registrierungs Typen, wobei einige Einstellungen auf alle Registrierungs Optionen angewendet werden. Weitere Informationen zu den verschiedenen Registrierungs Typen finden Sie unter [macOS](../enrollment/macos-enroll.md)-Registrierung.

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung und automatisierte Geräteregistrierung 

- **IP-Adresse**: Geben Sie die IPv4- oder IPv6-Adresse des Druckers ein. Wenn Sie den Hostnamen verwenden, um Drucker zu identifizieren, erhalten Sie die IP-Adresse, indem Sie den Drucker in der Terminal-App pingen. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
- **Pfad**: Geben Sie den Pfad des Druckers ein. Der Pfad ist für Drucker in Ihrem Netzwerk in der Regel `ipp/print`. Der Abschnitt [Abrufen von IP-Adresse und Pfad](#get-the-ip-address-and-path) (in diesem Artikel) enthält weitere Details.
- **Port** (iOS 11.0 und höher): Geben Sie den Lauschport des AirPrint-Ziels ein. Wenn Sie diese Eigenschaft leer lassen, verwendet AirPrint den Standardport.
- **TLS** (iOS 11.0 und höher): Klicken Sie auf **Aktivieren**, um AirPrint-Verbindungen mit Transport Layer Security (TLS) zu schützen.

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

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Dateien, Ordner und benutzerdefinierte apps**: **fügen** Sie den Pfad einer Datei, eines Ordners, einer benutzerdefinierten APP oder einer System-App hinzu, die Sie öffnen möchten, wenn sich ein Benutzer am Gerät anmeldet. System-Apps oder apps, die für Ihre Organisation erstellt oder angepasst wurden, befinden sich in der Regel im Ordner "`Applications`" mit einem ähnlichen Pfad wie `/Applications/AppName.app`. 

  Sie können viele Dateien, Ordner und apps hinzufügen. Geben Sie beispielsweise Folgendes ein:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Wenn Sie eine APP, einen Ordner oder eine Datei hinzufügen, geben Sie den richtigen Pfad ein. Nicht alle Elemente befinden sich im Ordner "`Applications`". Wenn ein Benutzer ein Element von einem Speicherort an einen anderen verschiebt, ändert sich der Pfad. Dieses verschoderte Element wird nicht geöffnet, wenn sich der Benutzer anmeldet.

## <a name="login-window"></a>Fenster „Anmeldung“

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung und automatisierte Geräteregistrierung 

#### <a name="window-layout"></a>Fensterlayout

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

#### <a name="login-screen-power-settings"></a>Energieeinstellungen auf dem Anmeldebildschirm

- **Schaltfläche „Herunterfahren“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Herunterfahren“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Herunterfahren“ gezeigt.
- **Schaltfläche „Neu starten“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Neu starten“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Neu starten“ gezeigt.
- **Schaltfläche „Standby“** : Bei Wahl von **Ausblenden** wird die Schaltfläche „Standby“ nicht auf dem Anmeldebildschirm angezeigt. Bei Wahl der Standardeinstellung **Nicht konfiguriert** wird die Schaltfläche „Standby“ gezeigt.

#### <a name="other"></a>Andere

- **Benutzeranmeldung über Konsole deaktivieren**: Bei Wahl von **Deaktivieren** wird die macOS-Befehlszeile zum Anmelden ausgeblendet. **Deaktivieren** Sie diese Einstellung für typische Benutzer. Die Standardeinstellung **Nicht konfiguriert** ermöglicht fortgeschrittenen Benutzern die Anmeldung über die macOS-Befehlszeile. Um in den Konsolenmodus zu wechseln, müssen Benutzer `>console` in das Feld „Benutzername“ eingeben und sich im Konsolenfenster authentifizieren.

#### <a name="apple-menu"></a>Apple-Menü

Nachdem sich Benutzer bei den Geräten angemeldet haben, beeinflussen die folgenden Einstellungen ihre Möglichkeiten.

- **Herunterfahren deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Herunterfahren** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Herunterfahren** auf dem Gerät.
- **Neustart deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Neu starten** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Neu starten** auf dem Gerät.
- **Ausschalten deaktivieren**: Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Ausschalten** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Ausschalten** auf dem Gerät.
- **Abmelden deaktivieren** (macOS 10.13 und höher): Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Abmelden** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Abmelden** auf dem Gerät.
- **Sperrbildschirm deaktivieren** (macOS 10.13 und höher): Bei Wahl von **Deaktivieren** werden Benutzer am Auswählen der Option **Sperrbildschirm** gehindert, nachdem sich der Benutzer angemeldet hat. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern das Auswählen des Menüelements **Sperrbildschirm** auf dem Gerät.

## <a name="single-sign-on-app-extension"></a>App-Erweiterung für einmaliges Anmelden

Diese Funktion gilt für:

- macOS 10.15 und neuer

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen 

- **SSO-App-Erweiterungstyp**: Wählen Sie den Typ der Anmelde Informationen-SSO-App-Erweiterung. Wenn Sie das SSO-App-Erweiterungs Profil speichern, können Sie den SSO-App-Erweiterungstyp nicht ändern. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert**: App-Erweiterungen werden nicht verwendet. Um eine SSO-App-Erweiterung zu deaktivieren, ändern Sie den SSO-App-Erweiterungstyp von **Kerberos** oder **Credential** in **nicht konfiguriert**.
  - **Anmelde Informationen**: Verwenden Sie eine generische, anpassbare App-Erweiterung für Anmelde Informationen, um SSO zu verwenden. Stellen Sie sicher, dass Sie die Erweiterungs-ID und Team-ID für die SSO-App-Erweiterung Ihrer Organisation kennen.  
  - **Kerberos**: Verwenden Sie die integrierte Kerberos-Erweiterung von Apple, die unter macOS Catalina 10,15 und höher enthalten ist. Bei dieser Option handelt es sich um eine Kerberos-spezifische **Version der Anmelde Informationen-App-** Erweiterung.

  > [!TIP]
  > Mit dem Anmelde Informationstyp fügen Sie eigene Konfigurationswerte zum durch **laufen der Erweiterung** hinzu. Verwenden Sie stattdessen die von Apple bereitgestellten integrierten Konfigurationseinstellungen im **Kerberos** -Typ.

- **Erweiterungs-ID** (nur Anmelde Informationen): Geben Sie die Bündel-ID ein, die Ihre SSO-App-Erweiterung identifiziert, z. b. `com.apple.ssoexample`.
- **Team-ID** (nur Anmelde Informationen): Geben Sie die Team Kennung Ihrer SSO-App-Erweiterung ein. Eine Team-ID ist eine Zeichenfolge mit einer alphanumerischen Zeichenfolge (Ziffern und Buchstaben) mit 10 Zeichen, die von Apple generiert wird, z. b. `ABCDE12345`. 

  [Suchen Sie nach Ihrer Team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öffnet die Website von Apple), die weitere Informationen enthält.

- **Bereich**: Geben Sie den Namen des Kerberos-Bereichs ein. Der Bereichs Name sollte groß geschrieben werden, z. b. `CONTOSO.COM`. In der Regel ist Ihr Bereichs Name mit dem DNS-Domänen Namen identisch, aber in Großbuchstaben.
- **Domänen**: Geben Sie die Domänen-oder Hostnamen der Standorte ein, die über SSO authentifiziert werden können. Wenn Ihre Website beispielsweise `mysite.contoso.com` ist, ist `mysite` der Hostname, und `contoso.com` ist der Domänen Name. Wenn Benutzer eine Verbindung mit einer dieser Websites herstellen, wird die Authentifizierungs Aufforderung von der APP-Erweiterung behandelt. Diese Authentifizierung ermöglicht es Benutzern, die Gesichts-ID, die Fingereingabe-ID oder Apple Pincode/Passcode für die Anmeldung zu verwenden.

  - Alle Domänen in der Single Sign-on App-Erweiterung InTune-Profile müssen eindeutig sein. Sie können eine Domäne in Anmelde-App-Erweiterungs Profilen nicht wiederholen, auch wenn Sie unterschiedliche Typen von SSO-App-Erweiterungen verwenden.
  - Diese Domänen beachten nicht die Groß-/Kleinschreibung.

- **Zusätzliche Konfiguration** (nur Anmelde Informationen): Geben Sie zusätzliche Erweiterungs spezifische Daten ein, die an die SSO-App-Erweiterung übergeben werden sollen:
  - **Konfigurationsschlüssel**: Geben Sie den Namen des Elements ein, das Sie hinzufügen möchten, z. b. `user name`.
  - **Werttyp**: Geben Sie den Typ der Daten ein. Folgende Optionen sind verfügbar:

    - Zeichenfolge
    - Boolescher Wert: Geben Sie unter **Konfigurations Wert den Wert**`True` oder `False` ein.
    - Integer: Geben Sie unter **Konfigurations Wert**eine Zahl ein.
    
  - **Konfigurations Wert**: Geben Sie die Daten ein.
  
  - **Add**: Wählen Sie diese Option aus, um die Konfigurationsschlüssel hinzuzufügen

- **Verwendung von Keychain** (nur Kerberos): Wählen Sie **Block** aus, um zu verhindern, dass Kenn Wörter in der Keychain gespeichert und gespeichert werden. **Nicht konfiguriert** (Standardeinstellung): ermöglicht das Speichern und Speichern von Kenn Wörtern in der Keychain.  
- **Gesichts-ID, Fingereingabe-ID oder Kennung** (nur Kerberos) **: erzwingen** Sie, dass Benutzer ihre Gesichts-ID, Fingereingabe-ID oder Apple-Kennung eingeben, um sich bei den hinzugefügten Domänen anzumelden. **Nicht konfiguriert** (Standardeinstellung) erfordert nicht, dass Benutzer Biometrie oder Kennung für die Anmeldung verwenden.
- **Standardbereich** (nur Kerberos): Wählen Sie **aktivieren** aus, um den von Ihnen eingegebenen **Bereichs** Wert als Standardbereich festzulegen. **Nicht konfiguriert** (Standard) legt keinen Standardbereich fest.

  > [!TIP]
  > - **Aktivieren** Sie diese Einstellung, wenn Sie mehrere Kerberos-SSO-App-Erweiterungen in Ihrer Organisation konfigurieren.
  > - **Aktivieren** Sie diese Einstellung, wenn Sie mehrere Bereiche verwenden. Der von Ihnen eingegebene **Bereichs** Wert wird als Standardbereich festgelegt.
  > - Wenn Sie nur über einen Bereich verfügen, lassen Sie ihn **nicht konfiguriert** (Standard).

- **Autodiscover** (nur Kerberos): bei Festlegung auf **blockieren**verwendet die Kerberos-Erweiterung nicht automatisch LDAP und DNS, um den Namen der Active Directory Site zu ermitteln. **Nicht konfiguriert** (Standardeinstellung): ermöglicht der Erweiterung, den Namen der Active Directory Site automatisch zu finden.
- Kenn **Wort Änderungen** (nur Kerberos) **: verhindert** , dass Benutzer die Kenn Wörter ändern, die Sie zum Anmelden bei den eingegebenen Domänen verwenden. **Nicht konfiguriert** (Standardeinstellung): erlaubt Kenn Wort Änderungen.  
- Kenn **Wort Synchronisierung** (nur Kerberos): Wählen Sie **aktivieren** aus, um die lokalen Kenn Wörter Ihrer Benutzer mit Azure AD zu synchronisieren. **Nicht konfiguriert** (Standard) deaktiviert die Kenn Wort Synchronisierung für die Azure AD. Verwenden Sie diese Einstellung als Alternative oder Sicherung für einmaliges Anmelden (SSO). Diese Einstellung funktioniert nicht, wenn Benutzer mit einem Apple Mobile-Konto angemeldet sind.
- **Komplexität von Windows Server Active Directory** -Kenn Wörtern (nur Kerberos): Wählen Sie **erforderlich** aus, um die Kenn Wort Komplexitäts Anforderungen Active Directory zu erzwingen. Weitere Informationen finden Sie unter [Kennwort muss Komplexitäts Anforderungen entsprechen](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **Nicht konfiguriert** (Standard) erfordert nicht, dass Benutzer die Kenn Wort Anforderung Active Directory erfüllen.
- **Minimale Kenn Wort Länge** (nur Kerberos): Geben Sie die Mindestanzahl von Zeichen ein, die das Kennwort eines Benutzers bilden kann. **Nicht konfiguriert** (Standard) erzwingt keine minimale Kenn Wort Länge für die Benutzer.
- Limit für die Kenn **Wort Wiederverwendung** (nur Kerberos): Geben Sie die Anzahl neuer Kenn Wörter (von 1-24) ein, die verwendet werden müssen, bis ein vorheriges Kennwort für die Domäne wieder verwendet werden kann. **Nicht konfiguriert** (Standard) erzwingt keine Kenn Wort Wiederverwendungs Beschränkung.
- **Minimal Kennwort** (nur Kerberos): Geben Sie die Anzahl von Tagen ein, die ein Kennwort für die Domäne verwendet werden muss, bevor ein Benutzer es ändern kann. **Nicht konfiguriert** (Standard) erzwingt kein minimal Alter von Kenn Wörtern, bevor Sie geändert werden können.
- **Benachrichtigung über Kenn Wort Ablauf** (nur Kerberos): Geben Sie die Anzahl von Tagen ein, bevor ein Kennwort abläuft, damit Benutzer benachrichtigt werden, dass Ihr Kennwort abläuft. **Nicht konfiguriert** (Standard) verwendet `15` Tage.
- **Kennwortablauf** (nur Kerberos): Geben Sie die Anzahl der Tage an, nach denen das Gerätekennwort geändert werden muss. **Nicht konfiguriert** (Standard) bedeutet, dass Benutzer Kennwörter nie ablaufen.
- **Prinzipal Name** (nur Kerberos): Geben Sie den Benutzernamen des Kerberos-Prinzipals ein. Sie müssen den Bereichs Namen nicht einschließen. In `user@contoso.com` ist `user` z. b. der Prinzipal Name, und `contoso.com` ist der Bereichs Name.
- **Active Directory Standortcode** (nur Kerberos): Geben Sie den Namen des Active Directory Standorts ein, der von der Kerberos-Erweiterung verwendet werden soll. Möglicherweise müssen Sie diesen Wert nicht ändern, da die Kerberos-Erweiterung möglicherweise automatisch den Active Directory Standort Codes findet.
- **Cache Name** (nur Kerberos): Geben Sie den Namen des generischen Sicherheits Diensts (GSS) des Kerberos-Caches ein. Dieser Wert muss höchstwahrscheinlich nicht festgelegt werden.  
- **Meldung zu Kenn Wort Anforderungen** (nur Kerberos): Geben Sie eine Textversion der Kenn Wort Anforderungen Ihres Unternehmens ein, die den Benutzern angezeigt wird. Die Meldung wird angezeigt, wenn Sie keine Anforderungen an die Kenn Wort Komplexität Active Directory müssen, oder geben Sie eine minimale Kenn Wort Länge ein.  
- **App-Bündel-IDs** (nur Kerberos): **fügen Sie** die APP Bundle Bezeichner hinzu, die Single Sign-on auf Ihren Geräten verwenden sollen. Diesen apps wird Zugriff auf das Kerberos-Ticket zum Erteilen von Tickets, das Authentifizierungs Ticket und das Authentifizieren von Benutzern für Dienste gewährt, auf die Sie Zugriff haben.
- **Domänen Bereichs Zuordnung** (nur Kerberos): **fügen Sie** die Domänen-DNS-Suffixe hinzu, die dem Bereich zugeordnet werden sollen. Verwenden Sie diese Einstellung, wenn die DNS-Namen der Hosts nicht mit dem Bereichs Namen identisch sind. Wahrscheinlich ist es nicht erforderlich, diese benutzerdefinierte Domäne-zu-Bereich-Zuordnung zu erstellen.

## <a name="associated-domains"></a>Zugeordnete Domänen

In Intune können Sie folgende Aktionen ausführen:

- Fügen Sie viele Zuordnungen zwischen apps und Domänen hinzu.
- Ordnen Sie der gleichen App viele Domänen zu.

Diese Funktion gilt für:

- macOS 10.15 und neuer

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **App-ID**: Geben Sie den App-Bezeichner der APP ein, die mit einer Website verknüpft werden soll. Der APP-Bezeichner enthält die Team-ID und eine Bündel-ID: `TeamID.BundleID`.

  Die Team-ID ist eine Zeichenfolge mit einer alphanumerischen Zeichenfolge (Buchstaben und Zahlen) aus 10 Zeichen, die von Apple für Ihre APP-Entwickler generiert wird, wie `ABCDE12345`. [Suchen Sie die Team-ID](https://help.apple.com/developer-account/#/dev55c3c710c)   (öffnet die Website von Apple) Weitere Informationen.

  Die Bündel-ID identifiziert die APP eindeutig und wird in der Regel in umgekehrter Domänen Namen Notation formatiert. Beispielsweise ist die Bündel-ID des Finders `com.apple.finder`. Um die Bündel-ID zu finden, verwenden Sie das AppleScript-Skript im Terminal:

  `osascript -e 'id of app "ExampleApp"'`

- **Domäne**: Geben Sie die Website Domäne ein, die einer APP zugeordnet werden soll. Die Domäne enthält einen Diensttyp und einen voll qualifizierten Hostnamen, z. b. `webcredentials:www.contoso.com`.

  Sie können alle Unterdomänen einer zugeordneten Domäne vergleichen, indem Sie `*.` (ein Sternchen-Platzhalter und einen Zeitraum) vor dem Anfang der Domäne eingeben. Der Zeitraum ist erforderlich. Exakte Domänen haben eine höhere Priorität als Platzhalter Domänen. Daher werden Muster aus übergeordneten Domänen abgeglichen, *Wenn* in der voll qualifizierten Unterdomäne keine Übereinstimmung gefunden wird.

  Der Diensttyp kann wie folgt lauten:

  - **authsrv**: App-Erweiterung für einmaliges Anmelden
  - **applink**: Universal Link
  - **webanmelde**Informationen: Kenn Wort Auto Ausfüllen

- **Add**: Wählen Sie diese Option aus, um Ihre apps und zugeordneten Domänen

> [!TIP]
> Öffnen Sie zum Beheben von Problemen auf Ihrem macOS-Gerät die **System Einstellungen**  > **profile**. Vergewissern Sie sich, dass das erstellte Profil in der Liste Geräteprofile aufgeführt ist. Wenn die Liste aufgeführt ist, stellen Sie sicher, dass sich die **Konfiguration der zugeordneten Domänen** im Profil befindet und die richtige APP-ID und die richtigen Domänen enthält.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch Geräte Features unter [IOS](ios-device-features-settings.md)konfigurieren.
