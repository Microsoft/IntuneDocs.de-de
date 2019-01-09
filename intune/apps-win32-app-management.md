---
title: Hinzufügen von Win32-Apps zu Microsoft Intune
titlesuffix: ''
description: Erfahren Sie, wie Sie Win32-Apps mit Microsoft Intune hinzufügen, bereitstellen und verwalten können. Dieser Artikel enthält eine Übersicht über die Funktionen zum Bereitstellen und Verwalten von Win32-Apps, die Intune bietet, sowie Informationen zur Problembehandlung bei Win32-Apps.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 11a698628e3ca1342f10f088045012523c8ac745
ms.sourcegitcommit: f114eeba1909c7d4e157003b1a9e2232dd1c99e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53734288"
---
# <a name="intune-standalone---win32-app-management-public-preview"></a>Intune Standalone – Win32-App-Verwaltung (Public Preview)

Intune Standalone ermöglicht eine umfangreichere Verwaltung von Win32-Anwendungen. Während es für Kunden mit Cloudverbindung möglich ist, den Configuration Manager für die Verwaltung von Win32-Anwendungen zu verwenden, verfügen Kunden, die ausschließlich Intune verwenden, über umfangreichere Verwaltungsfunktionen für ihre Win32-Branchenanwendungen (LOB, Line-of-Business). Dieser Artikel bietet eine Übersicht über das Intune-Feature zur Verwaltung von Win32-Apps und enthält Informationen zur Problembehandlung.

## <a name="prerequisites-for-public-preview"></a>Voraussetzungen für die öffentliche Vorschau

- Windows 10 Version 1607 oder höher (Education-, Pro- und Enterprise-Versionen)
- Folgendes muss für den Windows 10-Client zutreffen: 
    - Beitritt zu Azure Active Directory (AAD) oder Hybrid Azure Active Directory und
    - Registrierung bei Intune (MDM-verwaltet)
- Die Größe der Windows-Anwendung ist in der öffentlichen Vorschau auf 8 GB pro App begrenzt 

## <a name="prepare-the-win32-app-content-for-upload"></a>Vorbereiten des Inhalts der Win32-App für den Upload

Verwenden Sie das [Microsoft Intune-Tool zur Vorbereitung des Uploads von Win32-Apps](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool), um Win32-Apps vorab zu verarbeiten. Das Paketerstellungstool konvertiert die Installationsdateien der Anwendung in der *.intunewin*-Format. Das Paketerstellungstool erkennt auch einige der Attribute, die Intune benötigt, um den Installationsstatus der Anwendung zu bestimmen. Nachdem Sie dieses Tool im Installationsordner der App verwendet haben, können Sie in der Intune-Konsole eine Win32-App erstellen.

Sie können das [Microsoft Intune-Tool zur Vorbereitung des Uploads von Win32-Apps](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool) von GitHub herunterladen.

### <a name="available-command-line-parameters"></a>Verfügbare Befehlszeilenparameter: 

|    **Befehlszeilenparameter**    |    **Beschreibung**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Hilfe    |
|    `-c <setup_folder>`     |    Setupordner für alle Setupdateien.    |
|   ` -s <setup_file>`     |    Setupdatei (z. B. *setup.exe* oder *setup.msi*).    |
|    `-o <output_folder>`     |    Ausgabeordner für die generierte *.intunewin*-Datei.    |
|    `-q`       |    Stiller Modus    |

### <a name="example-commands"></a>Beispiele für Befehle

|    **Beispielbefehl**    |    **Beschreibung**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Dieser Befehl zeigt Nutzungsinformationen für das Tool an.    |
|    `IntuneWinAppUtil -c <setup_folder> -s <source_setup_file> -o <output_folder> <-q>`    |    Mit diesem Befehl wird die Datei `.intunewin` aus dem angegebenen Quellordner und der Setupdatei generiert. Für die MSI-Setupdatei ruft dieses Tool die erforderlichen Informationen für Intune ab. Wenn `-q` angegeben ist, wird der Befehl im stillen Modus ausgeführt, und wenn die Ausgabedatei bereits vorhanden ist, wird sie überschrieben. Wenn der Ausgabeordner nicht vorhanden ist, wird er automatisch erstellt.    |

Wenn Sie eine Datei mit der Erweiterung *.intunewin* generieren, legen Sie alle Dateien, die Sie als Referenz benötigen, in einem Unterordner des Setupordners ab. Verwenden Sie dann einen relativen Pfad, um auf die gewünschte Datei zu verweisen. Beispiel:

**Setupquellordner**: *c:\testapp\v1.0*<br>
**Lizenzdatei**: *c:\testapp\v1.0\licenses\license.txt*

Verweisen Sie auf die Datei *license.txt* mit dem relativen Pfad *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Erstellen, Zuweisen und Überwachen einer Win32-App

Ähnlich wie eine Branchenanwendung (LOB) können Sie eine Win32-App zu Microsoft Intune hinzufügen. Diese Art von App wird typischerweise intern oder von einem Drittanbieter geschrieben. Die folgenden Schritte enthaltenen Informationen zum Hinzufügen einer Windows-App zu Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.
2.  Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3.  Wählen Sie im **Intune**-Bereich die Option **Client-Apps** > **Apps** > **Hinzufügen** aus.
4.  Wählen Sie im Bereich **App hinzufügen** die Option **Windows-App (Win32) – Vorschau** aus der bereitgestellten Dropdownliste aus.

    ![Screenshot des Blatts „App hinzufügen“ – Dropdownfeld zum Hinzufügen des Typs](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Schritt 2: Hochladen der App-Paketdatei

1.  Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus, um eine Datei auszuwählen. Der Bereich „App-Paketdatei“ wird angezeigt.

    ![Screenshot des Blatts „App-Paketdatei“](./media/apps-win32-app-02.png)

2.  Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine Windows-Installationsdatei mit der Erweiterung *.intunewin* aus.
3.  Wählen Sie danach **OK**.

### <a name="step-3-configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1.  Wählen Sie im Bereich **App hinzufügen** die Option **App-Informationen** aus, um die App zu konfigurieren.
2.  Konfigurieren Sie im Bereich **App-Informationen** die folgenden Informationen. Einige der Werte in diesem Bereich wurden möglicherweise automatisch ausgefüllt.
    - **Name**: Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt wird. Wenn derselbe App-Name doppelt vorhanden ist, wird jede App im Unternehmensportal angezeigt.
    - **Beschreibung**: Geben Sie eine Beschreibung der App ein. Die Beschreibung wird im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Kategorie**: Wählen Sie eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App über das Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Präsentieren Sie die App herausgehoben auf der Hauptseite des Unternehmensportals, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional die URL einer Website ein, die Informationen über die App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional die URL einer Website ein, die Datenschutzinformationen für diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein. Ein Beispiel ist **Personalabteilung**.
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Laden Sie ein Symbol hoch, das der App zugeordnet wird. Das Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
3.  Wählen Sie danach **OK**.

### <a name="step-4-configure-app-installation-details"></a>Schritt 4: Konfigurieren von Details zur Installation der App
1.  Wählen Sie im Bereich **App hinzufügen** die Option **Programm** aus, um die Befehle zur Installation und Entfernung der App zu konfigurieren.
2.  Füge die komplette Befehlszeile für die Installation hinzu, um die App zu installieren. 

    Wenn Ihr App-Dateiname z. B. **MyApp123** lautet, fügen Sie Folgendes hinzu: `msiexec /i “MyApp123.msi”`

3.  Fügen Sie die vollständige Befehlszeile zum Deinstallieren hinzu, um die App basierend auf der GUID der App zu deinstallieren. 

    Beispiel: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Sie können eine Win32-App für die Installation im **Benutzerkontext** oder **Systemkontext** konfigurieren. Der **Benutzerkontext** bezieht nur auf einen bestimmten Benutzer. Der **Systemkontext** bezieht sich auf alle Benutzer eines Windows 10-Geräts.
    >
    > Endbenutzer müssen nicht beim Gerät angemeldet sein, um Win32-Apps zu installieren.

4.  Wählen Sie danach **OK**.

### <a name="step-5-configure-app-requirements"></a>Schritt 5: Konfigurieren der App-Anforderungen

1.  Wählen Sie im Bereich **App hinzufügen** die Option **Anforderungen** aus, um die Anforderungen zu konfigurieren, die Geräte erfüllen müssen, bevor die App installiert wird.
2.  Konfigurieren Sie im Bereich **Anforderungen** die folgenden Informationen. Einige der Werte in diesem Bereich wurden möglicherweise automatisch ausgefüllt.
    - **Betriebssystemarchitektur**: Wählen Sie die Architekturen aus, die für die Installation der App erforderlich sind.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie die für die Installation der App mindestens erforderliche Version des Betriebssystems aus.
    - **Erforderlicher Speicherplatz (MB)**: Optional können Sie den freien Speicherplatz hinzufügen, der auf dem Systemlaufwerk erforderlich ist, um die App zu installieren.
    - **Erforderlicher physischer Speicher (MB)**: Optional können Sie den für die Installation der App erforderlichen physischen Arbeitsspeicher (RAM) hinzufügen.
    - **Mindestens erforderliche Anzahl logischer Prozessoren**: Optional können Sie die Anzahl von logischen Prozessoren hinzufügen, die für die Installation der App mindestens erforderlich sind.
    - **Mindestens erforderliche CPU-Geschwindigkeit (MHz)**: Optional können Sie die CPU-Geschwindigkeit hinzufügen, die für die Installation der App mindestens erforderlich ist.
3.  Wählen Sie danach **OK**.

### <a name="step-6-configure-app-detection-rules"></a>Schritt 6: Konfigurieren von App-Erkennungsregeln

1.  Wählen Sie im Bereich **App hinzufügen** die Option **Erkennungsregeln** aus, um die Regeln so zu konfigurieren, dass sie das Vorhandensein der App erkennen.
2.  Wählen Sie im Feld **Regelformat** aus, wie das Vorhandensein der App erkannt werden soll. Sie können auswählen, ob Sie die Erkennungsregeln manuell konfigurieren oder ein benutzerdefiniertes Skript verwenden möchten, um das Vorhandensein der App zu erkennen. Sie müssen mindestens eine Erkennungsregel auswählen. 

    > [!NOTE]
    > Im Bereich **Erkennungsregeln** können Sie auswählen, ob Sie mehrere Regeln hinzufügen möchten. Die Bedingungen für **alle** Regeln müssen erfüllt sein, um die App zu erkennen.

    - **Manuelles Konfigurieren von Erkennungsregeln** – Sie können einen der folgenden Regeltypen auswählen:
        1.  **MSI** – Überprüfung auf der Grundlage der MSI-Versionsprüfung. Diese Option kann nur einmal hinzugefügt werden. Wenn Sie diesen Regeltyp auswählen, gibt es zwei Einstellungen:
            - **MSI-Produktcode** – Fügen Sie einen gültigen MSI-Produktcode für die App hinzu.
            - **MSI-Produktversionsprüfung** – Wählen Sie **Ja** aus, um die MSI-Produktversion zusätzlich zum MSI-Produktcode zu überprüfen.
        2.  **Datei** – Überprüfen Sie anhand von Datei- oder Ordnererkennung, Datum, Version oder Größe.
            - **Pfad** – Der vollständige Pfad des Ordners, der die zu erkennende Datei oder den Ordner enthält.
            - **Datei oder Ordner** – Die zu erkennende Datei oder der zu erkennende Ordner.
            - **Erkennungsmethode** – Wählen Sie die Art der Erkennungsmethode aus, mit der das Vorhandensein der App überprüft wird.
            - **Einer 32-Bit-App auf 64-Bit-Clients zugeordnet** – Wählen Sie **Ja** aus, um alle Pfadumgebungsvariablen im 32-Bit-Kontext auf 64-Bit-Clients zu erweitern. Wählen Sie **Nein** (Standard) aus, um Pfadvariablen im 64-Bit-Kontext auf 64-Bit-Clients zu erweitern. 32-Bit-Clients verwenden immer den 32-Bit-Kontext.
            
            **Beispiele für dateibasierte Erkennung**
            1.  Überprüfen Sie, ob die Datei vorhanden ist.
         
                ![Screenshot des Erkennungsregelbereichs – Dateivorkommen](./media/apps-win32-app-03.png)
        
            2.  Überprüfen Sie, ob der Ordner vorhanden ist.
         
                ![Screenshot des Erkennungsregelbereichs – Ordnervorkommen](./media/apps-win32-app-04.png)
        
        3. **Registrierung** – Überprüfen Sie anhand von Wert, Zeichenfolge, Ganzzahl oder Version.
            - **Schlüsselpfad** – Der vollständige Pfad des Registrierungseintrags, der den zu erkennenden Wert enthält.
            - **Wertname** – Gibt den Namen des Registrierungswerts an. Wenn dieser Wert leer ist, erfolgt die Erkennung über den Schlüssel. Der (Standard-) Wert eines Schlüssels wird als Erkennungswert verwendet, wenn die Erkennungsmethode eine andere ist als das Vorhandensein von Dateien oder Ordnern.
            - **Erkennungsmethode** – Wählen Sie die Art der Erkennungsmethode aus, mit der das Vorhandensein der App überprüft wird.
            - **Einer 32-Bit-App auf 64-Bit-Clients zugeordnet** – Wählen Sie **Ja** aus, um die 32-Bit-Registrierung auf 64-Bit-Clients zu durchsuchen. Wählen Sie **Nein** (Standard) aus, um die 64-Bit-Registrierung auf 64-Bit-Clients zu durchsuchen. 32-Bit-Clients durchsuchen immer die 32-Bit-Registrierung.
            
            **Beispiele für registrierungsbasierte Erkennung**
            1.  Überprüfen Sie, ob der Registrierungsschlüssel vorhanden ist.
            
                ![Screenshot des Erkennungsregelbereichs – Registrierungsschlüsselvorkommen](./media/apps-win32-app-05.png)    
            
            2.  Überprüfen Sie auf vorhandene Registrierungswerte (**Nicht verfügbar in der Vorschau**).
        
                ![Screenshot des Erkennungsregelbereichs – Registrierungswertvorkommen](./media/apps-win32-app-06.png)    
        
            3.  Überprüfen Sie, ob die Zeichenfolge für den Registrierungswert identisch ist.
        
                ![Screenshot des Erkennungsregelbereichs – Gleichheit der Registrierungsschlüsselzeichenfolge](./media/apps-win32-app-07.png)    
     
    - **Benutzerdefiniertes Erkennungsskript verwenden** – Geben Sie das PowerShell-Skript an, das zum Erkennen dieser App verwendet werden soll. 
    
        1.  **Skriptdatei** – Wählen Sie ein PowerShell-Skript aus, das das Vorhandensein der App auf dem Client erkennt. Die App wird erkannt, wenn das Skript sowohl einen 0-Wert als Exitcode zurückgibt als auch einen Zeichenfolgenwert an STDOUT ausgibt.

        2.  **Skript auf 64-Bit-Clients als 32-Bit-Prozess ausführen**: Wählen Sie **Ja** aus, um das Skript in einem 32-Bit-Prozess auf 64-Bit-Clients auszuführen. Wählen Sie **Nein** (Standardeinstellung) aus, um das Skript in einem 64-Bit-Prozess auf 64-Bit-Clients auszuführen. Auf 32-Bit-Clients wird das Skript in einem 32-Bit-Prozess ausgeführt.

        3.  **Skriptsignaturprüfung erzwingen** – Wählen Sie **Ja** aus, um sicherzustellen, dass das Skript von einem vertrauenswürdigen Herausgeber signiert ist, sodass das Skript ohne Warnungen oder Aufforderungen ausgeführt werden kann. Das Skript wird ohne Blockierung ausgeführt. Wählen Sie **Nein** (Standard) aus, um das Skript mit Endbenutzerbestätigung ohne Signaturüberprüfung auszuführen.
    
            Der Intune-Agent überprüft die Ergebnisse des Skripts. Es liest die Werte, die vom Skript in den Standardausgabestream (STDOUT), den Standardfehlerstream (STDERR) und den Exitcode geschrieben wurden. Wenn das Skript mit einem Wert ungleich 0 (null) beendet wird, schlägt das Skript fehl und der Erkennungszustand der Anwendung ist „nicht installiert“. Wenn der Exitcode gleich null ist und in „STDOUT“-Daten enthalten sind, ist der Erkennungszustand der Anwendung „Installiert“. 

            > [!NOTE]
            > Wenn das Skript mit dem Wert 0 beendet wird, war die Skriptausführung erfolgreich. Der zweite Ausgabekanal zeigt an, dass die App erkannt wurde – STDOUT-Daten zeigen an, dass die App auf dem Client gefunden wurde. Wir suchen nicht nach einer bestimmten Zeichenfolge von STDOUT.

        4.  Nachdem Sie Ihre Regel(n) hinzugefügt haben, wählen Sie **Hinzufügen** > **OK** aus.

### <a name="step-7-configure-app-return-codes"></a>Schritt 7: Konfigurieren der App-Rückgabecodes

1.  Wählen Sie im Bereich **App hinzufügen** die Option **Rückgabecodes** aus, um die Rückgabecodes hinzuzufügen, die verwendet werden, um entweder das Verhalten bei der erneuten Installation der App oder das Verhalten nach der Installation anzugeben. Rückgabecodeeinträge werden standardmäßig bei der Erstellung der App hinzugefügt. Sie können jedoch zusätzliche Rückgabecodes hinzufügen oder bestehende Rückgabecodes ändern. 
2.  Fügen Sie im Bereich **Rückgabecodes** zusätzliche Rückgabecodes hinzu oder ändern Sie bestehende Rückgabecodes.
    - **Fehlerhaft** – Der Rückgabewert, der auf einen Installationsfehler der App hinweist.
    - **Harter Neustart** – Der Rückgabecode für den harten Neustart gestattet es nicht, dass nachfolgende Win32-Apps ohne Neustart auf dem Client installiert werden. 
    - **Softneustart** – Der Rückgabecode „Softneustart“ ermöglicht es, die nächste Win32-App zu installieren, ohne dass ein Neustart des Clients erforderlich ist. Ein Neustart ist erforderlich, um die Installation der aktuellen Anwendung abzuschließen.
    - **Wiederholen** – Der Rückgabecode-Agent versucht dreimal, die App zu installieren. Zwischen den einzelnen Versuchen wird fünf Minuten gewartet. 
    - **Erfolg** – Der Rückgabewert, der angibt, dass die App erfolgreich installiert wurde.
3.  Wählen Sie **OK** aus, nachdem Sie Ihre Liste der Rückgabecodes hinzugefügt oder geändert haben.

### <a name="step-8-add-the-app"></a>Schritt 8: Hinzufügen der App

1.  Überprüfen Sie im Bereich **App hinzufügen**, ob die konfigurierten App-Informationen richtig sind.
2.  Wählen Sie **Hinzufügen**, um die App in Intune hochzuladen.

### <a name="step-9-assign-the-app"></a>Schritt 9: Zuweisen der App

1.  Wählen Sie im App-Bereich die Option **Zuweisungen** aus.
2.  Wählen Sie **Gruppe hinzufügen** aus, um den Bereich **Gruppe hinzufügen** zu öffnen, der mit der App verknüpft ist.
3.  Wählen Sie für die bestimmte App einen **Zuweisungstyp** aus:
    - **Für registrierte Geräte verfügbar**: Benutzer installieren die App über die Unternehmensportal-App oder -Website.
    - **Erforderlich**: Die App wird auf Geräten in den ausgewählten Gruppen installiert.
    - **Deinstallieren**: Die App wird auf Geräten in den ausgewählten Gruppen deinstalliert.
4.  Wählen Sie **Eingeschlossene Gruppen** aus und weisen Sie die Gruppen zu, die diese App verwenden werden.
5.  Wählen Sie im Bereich **Zuweisen** die Option **OK** aus, um die Auswahl der eingeschlossenen Gruppe abzuschließen.
6.  Wenn Sie Benutzergruppen von dieser App-Zuweisung ausschließen möchten, wählen Sie **Gruppen ausschließen** aus.
7.  Wählen Sie im Bereich **Gruppe hinzufügen** die Option **OK** aus.
8.  Wählen Sie im Bereich **Zuweisungen** die Option **Speichern** aus.

An dieser Stelle haben Sie die Schritte zum Hinzufügen einer Win32-App zu Intune abgeschlossen. Informationen zur Zuweisung und Überwachung von Apps finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) und [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="delivery-optimization"></a>Übermittlungsoptimierung

Clients von Windows 10 RS3 und höher laden Intune Win32-App-Inhalte mit einer Komponente zur Übermittlungsoptimierung auf den Windows 10-Client herunter. Die Übermittlungsoptimierung bietet Peer-zu-Peer-Funktionen, die standardmäßig eingeschaltet sind. Die Übermittlungsoptimierung kann mit einer Gruppenrichtlinie und in der Zukunft über Intune MDM konfiguriert werden. Weitere Informationen finden Sie unter [Übermittlungsoptimierung für Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Installieren erforderlicher und verfügbarer Apps auf Geräten

Der Endbenutzer erhält Windows-Popupbenachrichtigungen für die erforderlichen und verfügbaren App-Installationen. Die folgende Abbildung zeigt eine exemplarische Popupbenachrichtigung, bei der die App-Installation erst nach einem Neustart des Geräts abgeschlossen ist. 

![Screenshot der Windows-Popupbenachrichtigungen für eine App-Installation](./media/apps-win32-app-08.png)    

Die folgende Abbildung zeigt dem Endbenutzer an, dass App-Änderungen am Gerät vorgenommen werden.

![Screenshot mit einer Benachrichtigung an den Benutzer, dass Änderungen an der App vorgenommen wurden](./media/apps-win32-app-09.png)    

## <a name="troubleshoot-win32-app-issues"></a>Behandeln von Win32-App-Problemen
Agentprotokolle auf dem Clientcomputer befinden sich häufig unter `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Sie können `CMTrace.exe` nutzen, um diese Protokolldateien anzuzeigen. *CMTrace.exe* kann unter [SCCM-Clienttools](https://docs.microsoft.com/sccm/core/support/tools) heruntergeladen werden. 

![Screenshot der Agent-Protokolle auf dem Clientcomputer](./media/apps-win32-app-10.png)    

### <a name="troubleshooting-areas-to-consider"></a>Zu berücksichtigende Problembehandlungsbereiche
- Überprüfen Sie die Zielgruppenadressierung, um sicherzustellen, dass der Agent auf dem Gerät installiert ist – Win32-App, die auf eine Gruppe ausgerichtet ist, oder PowerShell-Skript, das auf eine Gruppe ausgerichtet ist, erstellt die Installationsrichtlinie für die Sicherheitsgruppe.
- Überprüfen Sie die Betriebssystemversion – Windows 10 1607 und höher.  
- Überprüfen Sie die Windows 10 SKU – Windows 10 S oder Windows-Versionen, die mit aktiviertem S-Modus ausgeführt werden, unterstützen keine MSI-Installation.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Hinzufügen von Apps zu Intune finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).
