---
title: "Umschließen von iOS-Apps mit dem Intune App Wrapping Tool"
description: "Lernen Sie, Ihre iOS-Apps zu umschließen, ohne den Code der App selbst zu ändern. Bereiten Sie die Apps vor, damit Sie Verwaltungsrichtlinien für mobile Apps anwenden können."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c9329c25d6211149102c06b44fdb6d6222b13550
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Vorbereiten von iOS-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Verwenden Sie das Microsoft Intune App Wrapping Tool für iOS zum Aktivieren von Intune-App-Schutzrichtlinien für interne iOS-Apps, ohne den Code der App selbst zu ändern.

Das Tool ist eine macOS-Befehlszeilenanwendung, die einen Wrapper um eine App erstellt. Sobald eine App verarbeitet wurde, können Sie die App-Funktionen ändern, indem Sie [App-Schutzrichtlinien](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) für diese bereitstellen.

Das Tools können Sie unter [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) in GitHub herunterladen.



## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>Allgemeine Voraussetzungen für das App Wrapping Tool

Bevor Sie das App Wrapping Tool ausführen, müssen Sie einige allgemeine Voraussetzungen erfüllen:

* Laden Sie das [Microsoft Intune App Wrapping Tool für iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) von GitHub herunter.

* Mac OS-Computer mit OS X 10.8.5 oder höher und installierter Xcode-Toolsetversion 5 oder höher.

* Die Ausgangs-iOS-App muss von Ihrem Unternehmen oder einem unabhängigen Softwareanbieter (ISV) entwickelt und signiert werden.

  * Die Ausgangs-App-Datei muss die Erweiterung **.ipa** oder **.app** haben.

  * Die Ausgangs-App muss für iOS 8.0 kompiliert sein. oder höher kompiliert werden.

  * Die Ausgangs-App darf nicht verschlüsselt werden.

  * Die Ausgangs-App darf keine erweiterten Dateiattribute haben.

  * Die Ausgangs-App benötigt festgelegte Berechtigungen, bevor sie vom Intune App Wrapping Tool verarbeitet wird. Diese [Berechtigungen](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html) gehen über die üblicherweise erteilten hinaus und ermöglichen zusätzliche Funktionen. Anleitungen finden Sie unter [Festlegen von App-Berechtigungen](#setting-app-entitlements).

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>Apple Developer-Voraussetzungen für das App Wrapping Tool

Um mit dem Wrapping Tool bearbeitete Apps exklusiv an Benutzer in Ihrer Organisation zu verteilen, benötigen Sie ein [Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/)-Konto und mehrere Entitäten für die App-Signierung, die mit Ihrem Apple Developer-Konto verknüpft sind.

Weitere Informationen zum internen Verteilen von iOS-Apps an die Benutzer in Ihrer Organisation finden Sie im offiziellen Handbuch zum [Verteilen von Apple Developer Enterprise Program-Apps](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1).

Sie benötigen Folgendes zum Verteilen von Apps, die von Intune mit einem Wrapper versehen werden:

* Ein Entwicklerkonto im Apple Developer Enterprise Program.

* Internes und Ad-hoc-Signaturzertifikat für die Verteilung mit gültigem Teambezeichner.

  * Sie benötigen den SHA1-Hash des Signaturzertifikats als Parameter für das Intune App Wrapping Tool.


* Bereitstellungsprofil für die interne Verteilung.

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Schritte zum Erstellen eines Apple Developer Enterprise-Kontos
1. Wechseln Sie zur Website [Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/).

2. Klicken Sie links oben auf **Enroll**.

3. Lesen Sie die Checkliste unter „What You Need to Enroll“ durch. Klicken Sie auf unten auf der Seite auf **Start Your Enrollment**.

4. **Melden Sie sich** mit der Apple ID Ihres Unternehmens an. Wenn Sie keine haben, klicken Sie auf **Create Apple ID**.

5. Wählen Sie Ihren **Entitätstyp** aus, und klicken Sie auf **Continue**.

6. Füllen Sie das Formular mit den Informationen Ihrer Organisation aus. Klicken Sie auf **Continue**(Weiter). An dieser Stelle kontaktiert Apple Sie, um zu prüfen, ob Sie zum Registrieren Ihrer Organisation berechtigt sind.

8. Klicken Sie nach der Bestätigung auf **Agree to License**.

9. Beenden Sie nach Zustimmen zu den Lizenzbedingungen den Vorgang durch **Erwerben und Aktivieren des Programms**.

10. Wenn Sie sind der Team-Agent (die Person, die im Auftrag Ihres Unternehmens am Apple Developer Enterprise Program teilnimmt) sind, erstellen Sie zunächst Ihr Team, indem Sie Teammitglieder einladen und Rollen zuweisen. Informationen zum Verwalten Ihres Teams finden Sie in der Apple-Dokumentation unter [Managing Your Developer Account Team](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1).

### <a name="steps-to-create-an-apple-signing-certificate"></a>Schritte zum Erstellen eines Apple-Signaturzertifikats

1. Wechseln Sie zum [Apple Developer-Portal](https://developer.apple.com/).

2. Klicken Sie rechts oben auf der Seite auf **Account**.

3. **Melden Sie sich** mit der Apple ID Ihrer Organisation an.

4. Klicken Sie auf **Certificates, IDs & Profiles**.

  ![Apple Developer-Portal](./media/iOS-signing-cert-1.png)

5. Klicken Sie auf ![das Pluszeichen im Apple Developer-Portal](./media/iOS-signing-cert-2.png) (rechts oben), um ein iOS-Zertifikat hinzuzufügen.

6. Wählen Sie unter **Production** das Erstellen eines Zertifikats des Typs **In-House and Ad Hoc** aus.

  ![Wählen Sie das „In-House and Ad Hoc“-Zertifikat aus.](./media/iOS-signing-cert-3.png)

  >[!NOTE]
  >Wenn Sie nicht planen, die App zu verteilen und sie nur intern testen möchten, können Sie ein iOS App-Entwicklungszertifikat anstelle eines Produktionszertifikats verwenden. Wenn Sie ein Entwicklungszertifikat verwenden, stellen Sie sicher, dass das mobile Bereitstellungsprofil auf Geräte verweist, auf denen die App installiert wird.

7. Klicken Sie unten auf der Seite auf **Next**.

8. Lesen Sie die Anweisungen zum Erstellen einer **Zertifikatsignieranforderung (Certificate Signing Request, CSR)** mithilfe der Anwendung „Schlüsselbundverwaltung“ auf Ihrem macOS-Computer.

  ![Lesen der Anweisungen zum Erstellen einer CSR](./media/iOS-signing-cert-4.png)

9. Befolgen Sie die Anweisungen zum Erstellen einer Zertifikatsignieranforderung. Starten Sie auf dem macOS-Computer die Anwendung **Schlüsselbundverwaltung**.

10. Wechseln Sie im macOS-Menü oben auf dem Bildschirm zu **Schlüsselbundverwaltung > Zertifikatsassistent > Zertifikat einer Zertifizierungsinstanz anfordern**.  

  ![Anfordern eines Zertifikats von einer Zertifizierungsinstanz in Schlüsselbundverwaltung](./media/iOS-signing-cert-5.png)

11. Befolgen Sie die obigen Anweisungen auf der Apple Developer-Website zum Erstellen einer CSR-Datei. Speichern Sie die CSR-Datei auf Ihrem macOS-Computer.

  ![Anfordern eines Zertifikats von einer Zertifizierungsinstanz in Schlüsselbundverwaltung](./media/iOS-signing-cert-6.png)

12. Kehren Sie zur Apple Developer-Website zurück. Klicken Sie auf **Continue**(Weiter). Laden Sie dann die CSR-Datei hoch.

13. Apple generiert Ihr Signaturzertifikat. Laden Sie es herunter, und speichern Sie es an einem einprägsamen Speicherort auf Ihrem macOS-Computer.

  ![Herunterladen Ihres Signaturzertifikats](./media/iOS-signing-cert-7.png)

14. Doppelklicken Sie auf die Zertifikatsdatei, die Sie gerade heruntergeladen haben, um das Zertifikat einem Schlüsselbund hinzuzufügen.

15. Öffnen Sie **Schlüsselbundverwaltung** erneut. Suchen Sie Ihr Zertifikat, indem Sie rechts oben in der Suchleiste nach ihrem Namen suchen. Klicken Sie mit der rechten Maustaste auf das Element, um das Menü einzublenden, und klicken Sie auf **Informationen**. In den Beispielbildschirmen verwenden wir ein Entwicklungszertifikat anstelle eines Produktionszertifikats.

  ![Hinzufügen Ihres Zertifikats zu einem Schlüsselbund](./media/iOS-signing-cert-8.png)

16. Ein Informationsfenster wird angezeigt. Scrollen Sie nach unten, und sehen Sie unter der Bezeichnung **Fingerabdrücke** nach. Kopieren Sie die **SHA1**-Zeichenfolge (unscharf), die Sie als Parameter „-c“ für das App Wrapping Tool verwenden.

  ![Hinzufügen Ihres Zertifikats zu einem Schlüsselbund](./media/iOS-signing-cert-9.png)



### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>Schritte zum Erstellen eines Bereitstellungsprofils für die interne Verteilung

1. Wechseln Sie zurück zum [Apple Developer-Kontoportal](https://developer.apple.com/account/), und **melden Sie sich** mit der Apple ID Ihrer Organisation an.

2. Klicken Sie auf **Certificates, IDs & Profiles**.

3. Klicken Sie auf ![das Pluszeichen im Apple Developer-Portal](./media/iOS-signing-cert-2.png) (rechts oben), um ein iOS-Bereitstellungsprofil hinzuzufügen.

4. Wählen Sie unter **Distribution** das Erstellen eines Bereitstellungsprofils des Typs **In House** aus.

  ![Auswählen des Bereitstellungsprofils „In House“](./media/iOS-provisioning-profile-1.png)

5. Klicken Sie auf **Continue**(Weiter). Verknüpfen Sie unbedingt das zuvor generierte Signaturzertifikat mit dem Bereitstellungsprofil.

6. Befolgen Sie die Anweisungen zum Herunterladen Ihres Profils (mit der Erweiterung „.mobileprovision“) auf Ihren macOS-Computer.

7. Speichern Sie die Datei an einem einprägsamen Speicherort. Diese Datei wird mit im App Wrapping Tool für den Parameter „-p“ verwendet.



## <a name="download-the-app-wrapping-tool"></a>Herunterladen des App Wrapping Tools

1.  Laden Sie die Dateien für das App Wrapping Tool aus [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) auf einen macOS-Computer herunter.

2.  Doppelklicken Sie auf **Microsoft Intune App Wrapping Tool for iOS.dmg**. Ein Fenster mit den Lizenzbedingungen wird angezeigt. Lesen Sie das Dokument sorgfältig durch.

3. Wählen Sie **Agree** (Zustimmen) aus, um die Lizenzbedingungen zu akzeptieren, wodurch das Paket auf Ihrem Computer eingelegt wird.

4.  Öffnen Sie den Ordner **IntuneMAMPackager**, und speichern Sie seinen Inhalt auf Ihrem macOS-Computer. Sie können nun das App Wrapping Tool ausführen.

> [!NOTE]
> Der Intune MAM Packager kann auf macOS Computern separat eingebunden werden, was möglicherweise zu dem Fehler „Datei nicht gefunden.“ führt, wenn Sie die Wrapping-Befehle ausführen. Dadurch, dass die Inhalte des Ordners „IntuneMAMPackager“ verschoben werden, kann der Pfad zum Packager während des Umschließungsvorgangs gefunden werden.

## <a name="run-the-app-wrapping-tool"></a>Ausführen des App Wrapping Tools

### <a name="use-terminal"></a>Verwenden des Terminals

Öffnen Sie das macOS-Terminalprogramm, und navigieren Sie zu dem Ordner, in dem Sie die App Wrapping Tool-Dateien gespeichert haben. Das ausführbare Tool heißt „IntuneMAMPackager“ und befindet sich in „IntuneMAMPackager/Contents/MacOS“. Führen Sie den Befehl wie folgt aus:

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Einige Parameter sind optional, wie in der folgenden Tabelle dargestellt.

**Beispiel**: Der Befehl im folgenden Beispiel führt das App Wrapping Tool für eine App mit dem Namen „MyApp.ipa“ aus. Es werden ein Bereitstellungsprofil und ein SHA-1-Hash des Signaturzertifikats angegeben und zum Signieren der umschlossenen App verwendet. Die Ausgabe-App („MyApp_Wrapped.ipa“) wird erstellt und in Ihrem Desktopordner gespeichert.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>Befehlszeilenparameter
Sie können die folgenden Befehlszeilenparameter mit dem App Wrapping Tool verwenden:

|Eigenschaft|Verwendung|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. Der Dateiname muss auf APP oder IPA enden. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**|Zeigt detaillierte Verwendungsinformationen zu den verfügbaren Befehlszeileneigenschaften für das App Wrapping Tool an.|
|**-v**|(Optional) Gibt ausführliche Meldungen in die Konsole aus. Sie sollten dieses Flag verwenden, um Fehler zu debuggen.|
|**-e**| (Optional) Verwenden Sie dieses Flag, damit das App Wrapping Tool fehlende Berechtigungen bei der Verarbeitung der App entfernt. Weitere Details finden Sie unter [Setting app entitlements (Festlegen von App-Berechtigungen)](#setting-app-entitlements).|
|**-xe**| (Optional) Gibt Informationen über die iOS-Erweiterungen in der App und die Berechtigungen aus, die für deren Verwendung erforderlich sind. Weitere Details finden Sie unter [Setting app entitlements (Festlegen von App-Berechtigungen)](#setting-app-entitlements). |
|**-x**| (Optional) `<An array of paths to extension provisioning profiles>`. Verwenden Sie diese Option, wenn Ihre Anwendung Bereitstellungsprofile für Erweiterungen benötigt.|
|**-f**|(Optional) `<Path to a plist file specifying arguments.>` Verwenden Sie dieses Flag vor der [PLIST](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-Datei, wenn Sie die PLIST-Vorlage verwenden, um die restlichen IntuneMAMPackager-Eigenschaften wie „-i“, „-o“ und „-p“ anzugeben. Informationen finden Sie unter „Verwenden einer PLIST-Datei für die Eingabe von Argumenten“. |
|**-b**|(Optional) Verwenden Sie „-b“ ohne ein Argument, wenn die umschlossene Ausgabe-App über die gleiche Bundleversion wie die Eingabe-App verfügen soll (nicht empfohlen). <br/><br/> Verwenden Sie `-b <custom bundle version>`, wenn die umschlossene App über eine benutzerdefinierte CFBundleVersion verfügen soll. Wenn Sie eine benutzerdefinierte CFBundleVersion angeben möchten, empfiehlt es sich, die CFBundleVersion der nativen App um die unwichtigste Komponente zu erhöhen, z.B. 1.0.0 -> 1.0.1. |

### <a name="use-a-plist-to-input-arguments"></a>Verwenden einer PLIST-Datei für die Eingabe von Argumenten
Eine einfache Möglichkeit, das App Wrapping Tool auszuführen, besteht darin, alle Befehlsargumente in einer [PLIST](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html)-Datei zu platzieren. PLIST ist ein Dateiformat, das XML ähnelt und das für die Eingabe von Befehlszeilenargumenten mithilfe einer Formularschnittstelle verwenden werden kann.

Öffnen Sie im Ordner „IntuneMAMPackager/Contents/MacOS“ `Parameters.plist` (eine leere PLIST-Vorlage) mit einem Text-Editor oder Xcode. Geben Sie Ihre Argumente für die folgenden Schlüssel:

| PLIST-Schlüssel |  Standardwert| Hinweise |
|------------------|--------------|-----|
| Input Application Package Path  |empty| Identisch mit „-i“|
| Output Application Package Path |empty| Identisch mit „-o“|
| Provisioning Profile Path |empty| Identisch mit „-p“|
| SHA-1 Certificate Hash |empty| Identisch mit „-c“|
| Verbose Enabled |false| Identisch mit „-v“|
| Remove Missing Entitlements | false| Identisch mit „-c“|
| Prevent Default Build |false | Entspricht der Verwendung von „-b“ ohne Argumente|
|Build String Override | empty| Die benutzerdefinierte CFBundleVersion der umschlossenen Ausgabe-App |
|Extension Provisioning Profile Paths | empty| Profile für die Erweiterungsbereitstellung für Apps


Führen Sie IntuneMAMPackager mit „plist“ als einziges Argument aus:

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>Nach dem Umschließen

Wenn der Prozess zum Umschließen abgeschlossen wurde, wird die Nachricht „The application was successfully wrapped“ (Die Anwendung wurde erfolgreich umschlossen) angezeigt. Falls ein Fehler auftritt, finden Sie unter [Fehlermeldungen](#error-messages-and-log-files) hilfreiche Informationen.

Die per Wrapping umschlossene Anwendung wird im Ausgabeordner gespeichert, den Sie zuvor angegeben haben. Sie können die App in die Intune-Administratorkonsole hochladen und der App eine Richtlinie für die mobile Anwendungsverwaltung zuordnen.

> [!IMPORTANT]
> Wenn Sie eine umschlossene App hochladen, können Sie versuchen, eine ältere Version der Anwendung zu aktualisieren, wenn eine ältere (umschlossene oder native) Version bereits in Intune bereitgestellt wurde. Wenn einen Fehler auftritt, laden Sie die App als neue App hoch, und löschen Sie die ältere Version.

Sie können die App jetzt für Ihre Benutzergruppen bereitstellen und der App Richtlinien zum App-Schutz zuweisen. Die App wird auf dem Gerät mit den von Ihnen angegebenen App-Schutzrichtlinien ausgeführt.

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>Wie häufig sollten iOS-Anwendungen mithilfe des App Wrapping Tools von Intune erneut umschlossen werden?
In den folgenden Hauptszenarios besteht die Notwendigkeit, Anwendungen erneut zu umschließen:
* Die Anwendung hat eine neue Version veröffentlicht. Die Vorgängerversion der App wurde umschlossen und in die Intune-Konsole hochgeladen.
* Das App Wrapping Tool von Intune für iOS hat eine neue Version veröffentlicht, mit der wichtige Fehler behoben oder neue Intune-spezifische Richtlinienfeatures zum Schutz von Anwendungen eingeführt werden. Dies geschieht nach sechs bis acht Wochen über das GitHub-Repository für das [App Wrapping Tool von Microsoft Intune für iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

Für iOS ist es zwar möglich, Umschließungsvorgänge mit anderen Zertifizierungs- bzw. Bereitstellungsprofilen als dem ursprünglich zum Signieren der App verwendete Profil durchzuführen, allerdings schlagen die Vorgänge fehl, wenn die in der App angegebenen Berechtigungen nicht in dem neuen Bereitstellungsprofil enthalten sind. Wenn Sie die Befehlszeilenoption „-e“ verwenden, über die fehlende Berechtigungen aus der App entfernt werden, um zu erzwingen, dass der Umschließungsvorgang in diesem Szenario nicht fehlschlägt, können die Funktionen in der App eingeschränkt sein.

Im Folgenden werden bewährte Methoden für das erneute Umschließen aufgeführt:
* Gewährleisten, dass ein anderes Bereitstellungsprofil über dieselben erforderlichen Berechtigungen verfügt wie die Vorgängerversion des Bereitstellungsprofils. 

## <a name="error-messages-and-log-files"></a>Fehlermeldungen und Protokolldateien
Verwenden Sie die folgende Informationen, um Problemen mit dem App Wrapping Tool zu behandeln.

### <a name="error-messages"></a>Fehlermeldungen
Wenn das App Wrapping Tool nicht erfolgreich abgeschlossen wurde, wird eine der folgenden Fehlermeldungen in der Konsole angezeigt:

|Fehlermeldung|Weitere Informationen|
|-----------------|--------------------|
|Sie müssen ein gültiges iOS-Bereitstellungsprofil angeben.|Ihr Bereitstellungsprofil ist möglicherweise nicht gültig. Stellen Sie sicher, dass Sie die richtigen Berechtigungen für die Geräte haben und dass Ihr Profil korrekt auf Entwicklung oder Verteilung abzielt. Ihr Bereitstellungsprofil ist möglicherweise auch abgelaufen.|
|Geben Sie einen gültigen Eingabe-Anwendungsnamen an.|Stellen Sie sicher, dass der angegebene Eingabe-App-Name richtig ist.|
|Geben Sie einen gültigen Pfad für die Ausgabeanwendung an.|Stellen Sie sicher, dass der Pfad zur Ausgabe-App, den Sie angeben, vorhanden und korrekt ist.|
|Geben Sie ein gültiges Eingabe-Bereitstellungsprofil an.|Stellen Sie sicher, dass Sie einen gültigen Bereitstellungs-Profilnamen und die Erweiterung angegeben haben. In Ihrem Bereitstellungsprofil fehlen Berechtigungen, oder Sie haben möglicherweise nicht die Befehlszeilenoption „–p“ hinzugefügt.|
|Die angegebene Eingabeanwendung wurde nicht gefunden. Geben Sie einen gültigen Eingabe-App-Namen und -Pfad an.|Stellen Sie sicher, dass der Pfad Ihrer Eingabe-App gültig und vorhanden ist. Stellen Sie sicher, dass die Eingabe-App an diesem Speicherort vorhanden ist.|
|Die angegebene Eingabe-Bereitstellungsprofildatei wurde nicht gefunden. Geben Sie eine gültige Eingabe-Bereitstellungsprofildatei an.|Stellen Sie sicher, dass der Pfad der Eingabe-Bereitstellungsprofildatei gültig ist und die angegebene Datei vorhanden ist.|
|Der angegebene Ausgabeordner für die Anwendung wurde nicht gefunden. Geben Sie einen gültigen Pfad für die Ausgabeanwendung an.|Stellen Sie sicher, dass der von Ihnen angegebene Ausgabepfad gültig und vorhanden ist.|
|Die Ausgabe-App hat keine **IPA**-Erweiterung.|Nur Apps mit den Erweiterungen **APP** und **IPA** werden vom App Wrapping Tool akzeptiert. Stellen Sie sicher, dass die Ausgabedatei eine gültige Erweiterung hat.|
|Es wurde ein ungültiges Signaturzertifikat angegeben. Geben Sie ein gültiges Signaturzertifikat von Apple an.|Stellen Sie sicher, dass Sie das richtige Signaturzertifikat aus dem Apple-Entwicklerportal heruntergeladen haben. Ihr Zertifikat ist möglicherweise abgelaufen oder verfügt über keinen öffentlichen oder privaten Schlüssel. Wenn Ihr Apple-Zertifikat und das Bereitstellungsprofil verwendet werden können, um eine App in Xcode ordnungsgemäß zu signieren, sind sie für das App Wrapping Tool gültig.|
|Die angegebene Eingabeanwendung ist ungültig. Geben Sie eine gültige Anwendung an.|Stellen Sie sicher, dass Sie über eine gültige iOS-Anwendung verfügen, die als APP- oder IPA-Datei kompiliert wurde.|
|Die angegebene Eingabeanwendung ist verschlüsselt. Geben Sie eine gültige unverschlüsselte Anwendung an.|Das App Wrapping Tool unterstützt keine verschlüsselten Apps. Stellen Sie eine unverschlüsselte App bereit.|
|Die angegebene Eingabeanwendung liegt nicht im PIE-Format (Positionsunabhängige ausführbare Datei) vor. Geben Sie eine gültige Anwendung im PIE-Format an.|PIE-Apps können beim Ausführen an einer zufälligen Speicheradresse geladen werden. Dies kann Sicherheitsvorteile haben. Weitere Informationen zu Sicherheitsvorteilen finden Sie in Ihrer Apple-Entwicklerdokumentation.|
|Die angegebene Eingabe-App wurde bereits umschlossen. Geben Sie eine App ohne Wrapping an.|Sie können eine App, die vom Tool bereits verarbeitet wurde, nicht erneut verarbeiten. Wenn Sie eine App erneut verarbeiten möchten, führen Sie das Tool mit der ursprünglichen Version der App aus.|
|Die angegebene Eingabeanwendung ist nicht signiert. Geben Sie eine gültige signierte Anwendung an.|Das App Wrapping Tool erfordert, dass Apps signiert sind. Lesen Sie in der Entwicklerdokumentation, wie Sie eine umschlossene App signieren.|
|Die angegebene Eingabeanwendung muss im IPA- oder APP-Format vorliegen.|Nur APP- und IPA-Erweiterungen werden vom App Wrapping Tool akzeptiert. Stellen Sie sicher, dass Ihre Eingabedatei eine gültige Erweiterung hat und als APP- oder IPA-Datei kompiliert wurde.|
|Die angegebene Eingabe-App wurde bereits umschlossen und verwendet die neueste Version der Richtlinienvorlage.|Das App Wrapping Tool umschließt eine vorhandene umschlossene App mit der neuesten Version der Richtlinienvorlage nicht erneut.|
|WARNUNG: Sie haben kein SHA1-Zertifikathash angegeben. Stellen Sie sicher, dass die umschlossene Anwendung vor der Bereitstellung signiert wird.|Stellen Sie sicher, dass Sie ein gültiges SHA1-Hash gefolgt vom Befehlszeilenflag „–c“ angeben. |

### <a name="log-files-for-the-app-wrapping-tool"></a>Protokolldateien für das App Wrapping Tool
Apps, die mit dem App Wrapping Tool umschlossen wurden, generieren Protokolle, die in die iOS-Clientgerätekonsole geschrieben werden. Diese Informationen sind hilfreich, wenn Sie Probleme mit der Anwendung haben und ermitteln möchten, ob das Problem mit dem App Wrapping Tool zusammenhängt. Führen Sie die folgenden Schritte aus, um die Informationen abzurufen:

1.  Reproduzieren Sie das Problem durch Ausführen der App.

2.  Sammeln Sie die Konsolenausgabe mit den folgenden Apple-Anweisungen für das [Debuggen bereitgestellter iOS-Apps](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3.  Filtern Sie die gespeicherten Protokolle nach der Ausgabe von App-Einschränkungen, indem Sie das folgende Skript in die Konsole eingeben:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Sie können die gefilterten Protokolle an Microsoft senden.

    > [!NOTE]
    > In der Protokolldatei stellt das Element "Buildversion" die Version von Xcode dar.

    Umschlossene Apps geben auch Benutzern die Möglichkeit, die Protokolle direkt vom Gerät per E-Mail zu versenden, falls die App abstürzt. Benutzer können Ihnen das Protokoll zusenden, damit Sie es überprüfen und ggf. an Microsoft weiterleiten.


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>Anforderungen an Zertifikat, Bereitstellungsprofil und Authentifizierung

Damit eine vollständige Funktionalität gewährleistet werden kann, müssen die Voraussetzungen für das App Wrapping Tool für iOS erfüllt sein.

|Anforderungen|Details|
|---------------|-----------|
|iOS-Bereitstellungsprofil|Stellen Sie sicher, dass das Bereitstellungsprofil gültig ist, bevor Sie es einfügen. Das App Wrapping Tool überprüft bei der Verarbeitung einer iOS-App nicht, ob das Bereitstellungsprofil abgelaufen ist. Wenn ein abgelaufenes Bereitstellungsprofil angegeben wird, umfasst das App Wrapping Tool das abgelaufene Bereitstellungsprofil; Sie wissen erst dann, dass ein Problem vorliegt, wenn die Anwendung nicht mehr auf einem iOS-Gerät installiert werden kann.|
|iOS-Signaturzertifikat|Stellen Sie sicher, dass das Signaturzertifikat gültig ist, bevor Sie es angeben. Das App Wrapping Tool überprüft bei der Verarbeitung einer iOS-App nicht, ob das Zertifikat abgelaufen ist. Wenn ein Hash für ein abgelaufenes Zertifikat bereitgestellt wird, kann das Tool die App verarbeiten und signieren, jedoch die Installation auf Geräten schlägt fehl.<br /><br />Stellen Sie sicher, dass das für die Signierung der umschlossenen App bereitgestellte Zertifikat im Bereitstellungsprofil enthalten ist. Das Tool überprüft nicht, ob das Bereitstellungsprofil über eine Übereinstimmung für das Zertifikat zum Signieren der umschlossenen Anwendung verfügt.|
|Authentifizierung|Ein Gerät muss eine PIN haben, damit die Verschlüsselung funktioniert. Auf Geräten, auf denen Sie eine umschlossene App bereitgestellt haben, muss sich der Benutzer beim Berühren der Statusleiste auf dem Gerät erneut mit einem Geschäfts-, Schul- oder Unikonto anmelden. Die Standardrichtlinie in einer umschlossenen Anwendung lautet *authentication on re-launch* (Authentifizierung bei Neustart). iOS verarbeitet externe Benachrichtigungen (wie einen Anruf), indem die App beendet und erneut gestartet wird.


## <a name="setting-app-entitlements"></a>Festlegen von App-Berechtigungen
Vor dem Umschließen Ihrer App können Sie *Berechtigungen* erteilen, um der App zusätzliche Berechtigungen und Funktionen zu gewähren, die über das hinaus gehen, was einer App typischerweise gestattet ist. Eine *Berechtigungsdatei* wird während der Codesignatur verwendet, um spezielle Berechtigungen innerhalb Ihrer App anzugeben (z. B. Zugriff auf einen freigegebenen Schlüsselbund). Bestimmte App-Dienste (*Funktionen*) werden während der App-Entwicklung innerhalb von Xcode aktiviert. Nach ihrer Aktivierung werden die Funktionen in Ihrer Berechtigungsdatei wiedergegeben. Weitere Informationen zu Berechtigungen und Funktionen finden Sie unter [Hinzufügen von Funktionen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) in der iOS-Entwicklerbibliothek. Eine vollständige Liste der unterstützten Funktionen finden Sie unter [Unterstützte Funktionen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>Unterstützte Funktionen für das App Wrapping Tool für iOS

|Funktion|Beschreibung|Empfohlene Vorgehensweise|
|--------------|---------------|------------------------|
|App-Gruppen|Verwenden Sie App-Gruppen, um mehreren Apps den Zugriff auf freigegebene Container zu gestatten und um die zusätzliche, prozessübergreifende Kommunikation zwischen Apps zu ermöglichen.<br /><br />Um App-Gruppen zu aktivieren, öffnen Sie den Bereich **Funktionen**, und klicken Sie unter **App-Gruppen** auf **EIN**. Sie können App-Gruppen hinzufügen oder vorhandene auswählen.|Bei Verwendung von App-Gruppen verwenden Sie Reverse-DNS-Notation:<br /><br />*group.com.companyName.AppGroup*|
|Hintergrundmodi|Durch das Aktivieren von Hintergrundmodi kann Ihre iOS-App weiter im Hintergrund ausgeführt werden.||
|Datenschutz|Der Schutz von Daten erhöht die Sicherheit der von Ihrer iOS-App auf einem Datenträger gespeicherten Dateien. Der Schutz von Daten verwendet die integrierte Verschlüsselungshardware, die auf bestimmten Geräten vorhanden ist, um Dateien in einem verschlüsselten Format auf dem Datenträger zu speichern. Ihre App muss bereitgestellt sein, um den Schutz von Daten verwenden zu können.||
|In-App-Einkauf|Ein In-App-Einkauf bettet einen Store direkt in Ihre App ein, indem Ihnen ermöglicht wird, eine Verbindung mit dem Store herzustellen und Zahlungen des Benutzers sicher zu verarbeiten. Mithilfe eines In-App-Einkaufs können Sie die Zahlungen für erweiterte Funktionen oder für zusätzliche Inhalte abwickeln, die von Ihrer App verwendet werden können.||
|Schlüsselbundfreigabe|Durch die Aktivierung der Schlüsselbundfreigabe kann Ihre App Kennwörter im Schlüsselbund gemeinsam mit anderen Apps verwenden, die von Ihrem Team entwickelt wurden.|Bei Verwendung der Schlüsselbundfreigabe verwenden Sie die umgekehrte DNS-Schreibweise:<br /><br />*com.companyName.KeychainGroup*|
|Persönliches VPN|Aktivieren Sie persönliches VPN, um Ihrer App das Erstellen und Kontrollieren einer benutzerdefinierten VPN-Systemkonfiguration unter Verwendung des Netzwerkerweiterungs-Frameworks zu gestatten.||
|Pushbenachrichtigungen|Der Apple Push Notification Service (APNs) ermöglicht einer App, die nicht im Vordergrund ausgeführt wird, den Benutzer darüber zu benachrichtigen, dass sie Informationen für den Benutzer hat.|Damit Pushbenachrichtigungen funktionieren, müssen Sie ein App-spezifisches Bereitstellungsprofil verwenden.<br /><br />Befolgen Sie die Schritte in der [Apple-Entwicklerdokumentation](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Konfiguration von drahtlosem Zubehör|Die Aktivierung der Konfiguration von drahtlosem Zubehör fügt Ihrem Projekt das Framework für externes Zubehör hinzu und ermöglicht Ihrer App die Einrichtung von MFi-WLAN-Zubehör.||

### <a name="steps-to-enable-entitlements"></a>Schritte zur Aktivierung von Berechtigungen

1.  Aktivieren Sie Funktionen in Ihrer App:

    ein.  Navigieren Sie in Xcode zum Ziel Ihrer App, und klicken Sie auf **Funktionen**.

    b.  Aktivieren Sie die entsprechenden Funktionen. Ausführlichere Informationen zu jeder einzelnen Funktion und wie Sie die richtigen Werte bestimmen, finden Sie unter [Hinzufügen von Funktionen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) in der iOS-Entwicklerbibliothek.

    c.  Notieren Sie sich alle IDs, die Sie während des Prozesses erstellt haben.

    d.  Erstellen und signieren Sie Ihre App, die umschlossen werden soll.

2.  Aktivieren Sie Berechtigungen in Ihrem Bereitstellungsprofil:

    ein.  Melden Sie sich beim „Apple Developer Member Center“ an.

    b.  Erstellen Sie ein Bereitstellungsprofil für Ihre App. Anleitungen hierzu finden Sie unter [Abrufen der erforderlichen Komponenten für das Intune App Wrapping Tool für iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/).

    c.  Aktivieren Sie in Ihrem Bereitstellungsprofil dieselben Berechtigungen, die Sie in Ihrer App haben. Sie müssen dieselben IDs angeben, die Sie während der Entwicklung Ihrer App angegeben haben.

    d.  Schließen Sie den Bereitstellungsprofil-Assistenten ab, und laden Sie Ihre Datei herunter.

3.  Stellen Sie sicher, dass Sie alle Voraussetzungen erfüllt haben, und umschließen Sie dann die App.

### <a name="troubleshoot-common-errors-with-entitlements"></a>Behandlung häufiger Fehler mit Berechtigungen
Wenn das App Wrapping Tool für iOS einen Berechtigungsfehler anzeigt, probieren Sie die folgenden Problembehandlungsschritte.

|Problem|Ursache|Lösung|
|---------|---------|--------------|
|Fehler beim Analysieren der von der Eingabeanwendung generierten Berechtigungen.|Das App Wrapping Tool kann die Berechtigungsdatei, die aus der App extrahiert wurde, nicht lesen. Die Berechtigungsdatei ist möglicherweise falsch formatiert.|Untersuchen Sie die Berechtigungsdatei für Ihre App. Mit den folgenden Anweisungen wird erläutert, wie hierbei vorzugehen ist. Überprüfen Sie beim Untersuchen der Berechtigungsdatei auf falsch formatierte Syntax. Die Datei sollte im XML-Format sein.|
|Berechtigungen fehlen im Bereitstellungsprofil (fehlende Berechtigungen sind aufgeführt). Packen Sie die App neu mit einem Bereitstellungsprofil, das diese Berechtigungen enthält.|Zwischen den im Bereitstellungsprofil aktivierten Berechtigungen und den in der App aktivierten Funktionen besteht ein Konflikt . Dieser Konflikt gilt auch für die IDs, die bestimmten Funktionen (wie App-Gruppen und Schlüsselbundzugriff) zugeordnet sind.|Im Allgemeinen können Sie ein neues Bereitstellungsprofil erstellen, das dieselben Funktionen wie die App aktiviert. Wenn die IDs zwischen dem Profil und der App nicht übereinstimmen, ersetzt das App Wrapping Tool die IDs, wenn es dazu in der Lage ist. Wenn der Fehler auch nach dem Erstellen eines neuen Bereitstellungsprofils auftritt, können Sie versuchen, das Problem zu beseitigen, indem Sie Berechtigungen mithilfe des Parameters „–e“ aus der App entfernen. (Informationen hierzu finden Sie im Abschnitt „Verwenden des Parameters „–e“ zum Entfernen von Berechtigungen aus einer App“).|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Ermitteln vorhandener Berechtigungen einer signierten App
So überprüfen Sie die vorhandenen Berechtigungen einer signierten App und eines Bereitstellungsprofils:

1.  Suchen Sie die IPA-Datei, und ändern Sie ihre Erweiterung in ZIP.

2.  Erweitern Sie die ZIP-Datei. Dies erzeugt einen Nutzlastordner, der Ihr .app-Paket enthält.

3.  Verwenden Sie das Codesignaturtool, um die Berechtigungen des APP-Pakets zu überprüfen. Dabei ist `YourApp.app` der tatsächliche Name Ihres APP-Pakets:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4.  Verwenden Sie das Sicherheitstool, um die Berechtigungen des in die App eingebetteten Bereitstellungsprofils zu überprüfen. Dabei ist `YourApp.app` der tatsächliche Name Ihres APP-Pakets.

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Entfernen von Berechtigungen aus einer App mit dem Parameter „–e“
Dieser Befehl entfernt alle aktivierten Funktionen in der App, die nicht in der Berechtigungsdatei enthalten sind. Wenn Sie Funktionen entfernen, die von der App verwendet werden, kann dies zu einer Beschädigung der App führen. Fehlende Funktionen können beispielsweise dann entfernt werden, wenn eine Drittanbieter-App standardmäßig über alle Funktionen verfügt.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Sicherheit und Datenschutz für das App Wrapping Tool
Verwenden Sie die folgenden bewährten Methoden zu Sicherheit und Datenschutz, wenn Sie das App Wrapping Tool verwenden.

-   Das von Ihnen angegebene Signaturzertifikat, das Bereitstellungsprofil und die Branchen-App müssen sich auf demselben macOS-Computer befinden, den Sie für die Ausführung des App Wrapping Tools verwenden. Wenn sich die Dateien in einem UNC-Pfad befinden, stellen Sie sicher, dass mit dem macOS-Computer darauf zugegriffen werden kann. Der Pfad muss über IPsec oder SMB-Signaturen geschützt werden.

    Die umschlossene Anwendung, die in die Administratorkonsole importiert wurde, muss sich auf dem Computer befinden, auf dem Sie das Tool ausführen. Wenn sich die Datei in einem UNC-Pfad befindet, stellen Sie sicher, dass der Computer mit der Administratorkonsole darauf zugreifen kann. Der Pfad muss über IPsec oder SMB-Signaturen geschützt werden.

-   Die Umgebung, in die das App Wrapping Tool aus dem GitHub-Repository heruntergeladen wird, muss über IPsec- oder SMB-Signaturen geschützt sein.

-   Die App, die Sie verarbeiten, muss zum Schutz gegen Angriffe aus einer vertrauenswürdigen Quelle stammen.

-   Stellen Sie sicher, dass der Ausgabeordner, den Sie im App Wrapping Tool angeben, gesichert ist, insbesondere, wenn es sich um einen Remoteordner handelt.

-   iOS-Apps, die ein Dialogfeld zum Hochladen von Dateien enthalten, können Benutzern erlauben, die Einschränkungen beim Ausschneiden, Kopieren und Einfügen für die App zu umgehen. Z. B. kann ein Benutzer das Dialogfeld zum Dateien hochladen verwenden, um einen Screenshot der App-Daten hochzuladen.

-   Wenn Sie den Dokumentordner auf Ihrem Gerät über eine umschlossenen App überwachen, sehen Sie möglicherweise einen Ordner namens „.msftintuneapplauncher“. Wenn Sie diese Datei ändern oder löschen, beeinträchtigt dies möglicherweise die ordnungsgemäße Funktionsweise der eingeschränkten Apps.

## <a name="getting-logs-for-your-wrapped-applications"></a>Abrufen von Protokollen für umschlossene Anwendungen
Führen Sie die folgenden Schritte durch, um bei der Problembehandlung Protokolle für umschlossene Anwendungen zu erhalten.

1. Navigieren Sie auf Ihrem Gerät zur App mit den iOS-Einstellungen, und wählen Sie Ihre branchenspezifische App aus.
2. Schalten Sie **Diagnosekonsole** auf **Ein** um.
3. Starten Sie die Branchenanwendung.
4. Klicken Sie auf den Link „Erste Schritte“.
5. Sie können jetzt Protokolle per E-Mail freigeben oder sie an einen OneDrive-Speicherort kopieren.

>[!NOTE]
Die Protokollierungsfunktionalität ist für Apps aktiviert, die mit dem Intune App Wrapping Tool Version 7.1.13 oder höher umschlossen wurden.

### <a name="see-also"></a>Siehe auch
- [Auswählen der Vorbereitung von Apps für die mobile Anwendungsverwaltung mit Microsoft Intune](apps-prepare-mobile-application-management.md)</br>
- [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)</br>
- [Verwenden des SDK zum Aktivieren von Apps für die Verwaltung von mobilen Anwendungen](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
