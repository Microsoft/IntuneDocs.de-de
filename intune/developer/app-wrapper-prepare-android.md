---
title: Umschließen von Android-Apps mit dem Intune App Wrapping Tool
description: Hier erfahren Sie, wie Sie Ihre Android-Apps umschließen, ohne den Code der App selbst zu ändern. Bereiten Sie die Apps vor, damit Sie Verwaltungsrichtlinien für mobile Apps anwenden können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 107624ac5d0c5eab423c0d5051ceca45e41de0b9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490755"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Vorbereiten von Android-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool

Verwenden Sie das Microsoft Intune App Wrapping Tool für Android zum Ändern des Verhaltens Ihrer internen Android-Apps, indem Sie die Features der App einschränken, ohne den eigentlichen Code der App zu ändern.

Das Tool ist eine Windows-Befehlszeilenanwendung, die in PowerShell ausgeführt wird und einen Wrapper um die Android-App erstellt. Nachdem der Wrapper um die App erstellt wurde, können Sie die App-Funktionalität ändern, indem Sie in Intune [Verwaltungsrichtlinien für mobile Anwendungen](../apps/app-protection-policies.md) konfigurieren.

Lesen Sie vor dem Ausführen des Tools die [Sicherheitsüberlegungen für das Ausführen des App Wrapping Tools](#security-considerations-for-running-the-app-wrapping-tool). Sie können das Tool von der GitHub-Seite [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) herunterladen.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Erfüllen der Voraussetzungen zur Verwendung des App Wrapping Tools

- Sie müssen das App Wrapping Tool auf einem Windows-Computer unter Windows 7 oder höher ausführen.

- Die Eingabe-App muss ein gültiges Android-Anwendungspaket mit der Dateierweiterung „APK“ sein und folgende Kriterien aufweisen:

  - Darf nicht verschlüsselt sein.
  - Darf nicht zuvor bereits vom Intune App Wrapping Tool umschlossen worden sein.
  - Muss für Android 4.0 oder höher geschrieben sein.

- Die App muss von Ihrem oder für Ihr Unternehmen entwickelt werden. Sie können dieses Tool nicht für aus dem Google Play Store heruntergeladene Apps verwenden.

- Um das App Wrapping Tool auszuführen, müssen Sie die neueste Version der [Java Runtime Environment](https://java.com/download/) installieren und sicherstellen, dass die Java-Pfadvariable in den Windows-Umgebungsvariablen auf C:\ProgramData\Oracle\Java\javapath festgelegt wurde. Weitere Informationen finden Sie in der [Java-Dokumentation](https://java.com/download/help/).

    > [!NOTE]
    > In einigen Fällen kann die 32-Bit-Version von Java zu Speicherproblemen führen. Es ist eine gute Idee, die 64-Bit-Version zu installieren.

- Für Android müssen alle App-Pakete (APK-Dateien) signiert sein. Informationen zum **Wiederverwenden** vorhandener Zertifikate und für allgemeine Anleitungen für Signaturzertifikate finden Sie unter [Wiederverwendung von Signaturzertifikaten und Umschließen von Apps](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps). Das ausführbare Java-Tool „keytool.exe“ wird zum Generieren **neuer** Anmeldeinformationen verwendet, die zum Signieren der umschlossenen Ausgabe-App erforderlich sind. Kennwörter, die festgelegt werden, müssen sicher sein. Notieren Sie sich diese Kennwörter jedoch, denn sie werden benötigt, um das App Wrapping Tool auszuführen.

    > [!NOTE]
    > Das Intune App Wrapping Tool unterstützt nicht die v2- und anstehenden v3-Signaturschemen von Google für App-Signierung. Nachdem Sie die APK-Datei mit dem Intune App Wrapping Tool umschlossen haben, wird empfohlen, das [von Google bereitgestellte Apksigner Tool]( https://developer.android.com/studio/command-line/apksigner) zu verwenden. Dadurch wird Folgendes sichergestellt: Sobald Ihre App auf Endbenutzergeräte abgerufen wurde, kann sie durch Android-Standards ordnungsgemäß gestartet werden. 

- (Optional) In einigen Fällen erreicht eine App das Größenlimit der ausführbaren Dalvik-Datei (DEX) aufgrund der Intune MAM SDK-Klassen, die während der Umschließung hinzugefügt werden. DEX-Dateien sind Teil der Kompilierung einer Android-App. Das InTune App Wrapping-Tool verarbeitet den DEX-Datei Überlauf beim umschließen von apps mit einer minimalen API-Ebene von 21 oder höher (ab [v. 1.0.2501.1-](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android/releases)). Bei apps mit einer minimalen API-Ebene von < 21 besteht die empfohlene Vorgehensweise darin, die minimale API-Ebene mithilfe des `-UseMinAPILevelForNativeMultiDex` Flags des Wrappers zu erhöhen. Damit Kunden die minimale API-Ebene der APP nicht erhöhen können, sind die folgenden DEX-Überlauf Umgehungen verfügbar. In bestimmten Organisationen erfordert dies möglicherweise eine Zusammenarbeit mit demjenigen, der die App kompiliert (z.B. dem App-Entwicklungsteam):
* Verwenden Sie proguard, um nicht verwendete Klassen Verweise aus der primären DEX-Datei der APP auszuschließen.
* Deaktivieren Sie für Kunden, die v 3.1.0 oder höher des Android gradle-Plug-Ins verwenden, den [D8 dexer](https://android-developers.googleblog.com/2018/04/android-studio-switching-to-d8-dexer.html).  

## <a name="install-the-app-wrapping-tool"></a>Installieren des App Wrapping Tools

1. Laden Sie die Installationsdatei „InstallAWT.exe“ für das Intune App Wrapping Tool für Android aus dem [GitHub-Repository](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) auf einen Windows-Computer herunter. Öffnen Sie die Installationsdatei.

2. Akzeptieren Sie den Lizenzvertrag, und schließen Sie die Installation ab.

Merken Sie sich den Ordner, in dem Sie das Tool installieren. Der Standardspeicherort lautet: C:\Programme (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Ausführen des App Wrapping Tools

1. Öffnen Sie auf dem Windows-Computer, auf dem Sie das App Wrapping Tool installiert haben, ein PowerShell-Fenster.

2. Importieren Sie das PowerShell-Modul des App Wrapping Tools aus dem Ordner, in dem Sie das Tool installiert haben:

   ```PowerShell
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Führen Sie das Tool mit dem Befehl **invoke-AppWrappingTool** aus, der die folgende Verwendungssyntax aufweist:

   ```PowerShell
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   Die folgende Tabelle führt die Eigenschaften des Befehls **invoke-AppWrappingTool** auf:

|Eigenschaft|Informationen|Beispiel|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Pfad der Android-Quelle-App (.apk).| |
 |**-OutputPath**&lt;String&gt;|Pfad zur Android-Ausgabe-App. Ist dies der gleiche Verzeichnispfad wie InputPath, schlägt das Verpacken fehl.| |
|**-KeyStorePath**&lt;String&gt;|Pfad zur Keystoredatei, die das öffentliche/private Schlüsselpaar zum Signieren enthält.|Standardmäßig werden Keystoredateien unter „C:\Programme (x86)\Java\jreX.X.X_XX\bin“ gespeichert. |
|**-KeyStorePassword**&lt;SecureString&gt;|Das Kennwort zum Entschlüsseln des KeyStore. Für Android müssen alle Anwendungspakete (APK-Dateien) signiert sein. Verwenden Sie das Java-Keytool, um das KeyStorePassword zu generieren. Weitere Informationen über den Java-[Keystore](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) finden Sie hier.| |
|**-KeyAlias**&lt;String&gt;|Der Name des Schlüssels, der zum Signieren verwendet werden soll.| |
|**-KeyPassword**&lt;SecureString&gt;|Das Kennwort zum Entschlüsseln des privaten Schlüssels, der zum Signieren verwendet wird.| |
|**-SigAlg**&lt;SecureString&gt;| (Optional) Der Name des Signaturalgorithmus, der zum Signieren verwendet werden soll. Der Algorithmus muss mit dem privaten Schlüssel kompatibel sein.|Beispiele: SHA256withRSA, SHA1withRSA|
|**-UseMinAPILevelForNativeMultiDex**| Optionale Verwenden Sie dieses Flag, um die minimale API-Ebene der Android-App auf 21 zu erhöhen. Dieses Flag fordert zur Bestätigung auf, da es einschränkt, wer diese APP installieren darf. Benutzer können das Bestätigungs Dialogfeld überspringen, indem Sie den Parameter "-Confirm: $false" an Ihren PowerShell-Befehl anhängen. Das Flag sollte nur von Kunden in apps mit minimaler API-< 21 verwendet werden, die aufgrund von Fehlern aufgrund von DEX-Überlauf nicht erfolgreich eingebunden werden können. | |
| **&lt;CommonParameters&gt;** | (Optional) Der Befehl unterstützt allgemeine PowerShell-Parameter, wie z.B. „verbose“ und „debug“. |


- Eine Liste der allgemeinen Parameter finden Sie im [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Um ausführliche Informationen zu dem Tool zu erhalten, geben Sie folgenden Befehl ein:

    ```PowerShell
    Help Invoke-AppWrappingTool
    ```

**Beispiel:**

Importieren Sie das PowerShell-Modul.

```PowerShell
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```

Führen Sie das App Wrapping Tool in der nativen App „HelloWorld.apk“ aus.

```PowerShell
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Sie werden zur Eingabe von **KeyStorePassword** und **KeyPassword**aufgefordert. Geben Sie die Anmeldeinformationen ein, die Sie zum Erstellen der Keystore-Datei verwendet haben.

Es wird sowohl die umschlossene App als auch eine Protokolldatei generiert und in dem von Ihnen angegebenen Ausgabepfad gespeichert.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>Wie häufig sollten Android-Anwendungen mithilfe des App Wrapping Tools von Intune erneut umschlossen werden?
In den folgenden Hauptszenarios besteht die Notwendigkeit, Anwendungen erneut zu umschließen:
* Die Anwendung hat eine neue Version veröffentlicht. Die Vorgängerversion der App wurde umschlossen und in die Intune-Konsole hochgeladen.
* Das App Wrapping Tool von Intune für Android hat eine neue Version veröffentlicht, mit der wichtige Fehler behoben oder neue Intune-spezifische Richtlinienfunktionen zum Schutz von Anwendungen eingeführt werden. Dies geschieht alle sechs bis acht Wochen über das GitHub-Repository für das [App Wrapping Tool von Microsoft Intune für Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android).

Im Folgenden werden bewährte Methoden für das erneute Umschließen aufgeführt: 
* Verwalten von im Buildvorgang verwendeten Signaturzertifikaten. Informationen dazu finden Sie im Abschnitt [Wiederverwendung von Signaturzertifikaten und Umschließen von Apps](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps).

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>Wiederverwendung von Signaturzertifikaten und Umschließen von Apps
Für Android müssen alle Apps durch ein gültiges Zertifikat signiert sein, um auf Android-Geräten installiert werden zu können.

Umschlossene Apps können entweder als Teil des Umschließungsprozesses oder *nach* der Umschließung mithilfe Ihrer vorhandenen Tools für die Signatur signiert werden (alle Signierungsinformationen in der App, bevor die Umschließung verworfen wird). Wenn möglich sollten die Signierungsinformationen, die bereits während des Erstellungsprozesses verwendet wurden, während der Umschließung verwendet werden. In bestimmten Organisationen erfordert dies möglicherweise eine Zusammenarbeit mit der Person, die über die Keystore-Informationen verfügt (z.B. aus dem App-Entwicklungsteam). 

Wenn das vorherige Signaturzertifikat nicht verwendet werden kann oder die App zuvor nicht bereitgestellt wurde, können Sie möglicherweise ein neues Signaturzertifikat erstellen, indem Sie die Anweisungen im [Android Developer-Handbuch](https://developer.android.com/studio/publish/app-signing.html#signing-manually) befolgen.

Wenn die App zuvor mit einem anderen Signaturzertifikat bereitgestellt wurde, kann sie nach dem Upgrade nicht zu Intune hochgeladen werden. App-Upgradeszenarios sind dann fehlerhaft, wenn Ihre App mit einem anderen Zertifikat signiert wird, als mit dem, mit dem die App erstellt wurde. Deshalb müssen alle neuen Signaturzertifikate für App-Upgrades verwaltet werden. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Sicherheitsüberlegungen zum Ausführen des App Wrapping Tools
So verhindern Sie ein mögliches Spoofing, das Offenlegen von Informationen und Angriffe durch Rechteerweiterungen:

- Stellen Sie sicher, dass sich die Branchenanwendung für die Eingabe, die Ausgabeanwendung und der Java-Keystore auf demselben Windows-Computer befinden, auf dem auch das App Wrapping Tool ausgeführt wird.

- Importieren Sie die Ausgabeanwendung auf demselben Computer, auf dem das Tool ausgeführt wird, in die Intune-Konsole. Weitere Informationen zum Java-Keytool finden Sie unter [Keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html).

- Wenn sich die Ausgabeanwendung und das Tool in einem UNC-Pfad (Universal Naming Convention) befinden und Sie das Tool und die Eingabedateien nicht auf demselben Computer ausführen, sichern Sie die Umgebung, indem Sie [Internet Protocol Security (IPsec)](https://wikipedia.org/wiki/IPsec) oder [SMB-Signaturen (Server Message Block)](https://support.microsoft.com/kb/887429) einrichten.

- Stellen Sie sicher, dass die Anwendung von einer vertrauenswürdigen Quelle stammt.

- Sichern Sie das Ausgabeverzeichnis, das die umschlossene Anwendung enthält. Erwägen Sie für die Ausgabe ein Verzeichnis auf Benutzerebene zu verwenden.

## <a name="see-also"></a>Siehe auch
- [Auswählen der Vorbereitung von Apps für die mobile Anwendungsverwaltung mit Microsoft Intune](../developer/apps-prepare-mobile-application-management.md)

- [Entwicklerhandbuch zum Microsoft Intune App SDK für Android](../developer/app-sdk-android.md)
