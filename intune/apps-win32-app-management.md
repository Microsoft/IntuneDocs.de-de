---
title: Hinzufügen und Zuweisen von Win32-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Win32-Apps mit Microsoft Intune hinzufügen, zuweisen und verwalten können. Dieser Artikel enthält eine Übersicht über die Funktionen zum Bereitstellen und Verwalten von Win32-Apps, die Intune bietet, sowie Informationen zur Problembehandlung bei Win32-Apps.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8c4813d94a269ed6b8f944585814b54f36fef8c
ms.sourcegitcommit: 6e07c35145f70b008cf170bae57143248a275b67
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804704"
---
# <a name="intune-standalone---win32-app-management"></a>Eigenständiges Intune – Win32-App-Verwaltung

Die [eigenständige Intune-Version](mdm-authority-set.md) ermöglicht nun eine umfangreichere Verwaltung von Win32-Apps. Während es für Kunden mit Cloudverbindung möglich ist, den Configuration Manager für die Verwaltung von Win32-Anwendungen zu verwenden, verfügen Kunden, die ausschließlich Intune verwenden, über umfangreichere Verwaltungsfunktionen für ihre Win32-Branchenanwendungen (LOB, Line-of-Business). Dieser Artikel bietet eine Übersicht über das Intune-Feature zur Verwaltung von Win32-Apps und enthält Informationen zur Problembehandlung.

> [!NOTE]
> Für Windows-Anwendungen unterstützt dieses App-Verwaltungsfeature sowohl eine 32-Bit- als auch 64-Bit-Betriebssystemarchitektur.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass die folgenden Kriterien erfüllt sind, wenn Sie die Win32-App-Verwaltung verwenden wollen:

- Windows 10 Version 1607 oder höher (Education-, Pro- und Enterprise-Versionen)
- Folgendes muss für den Windows 10-Client zutreffen: 
    - Geräte müssen mit Azure AD verknüpft und automatisch registriert werden. Die Intune-Verwaltungserweiterung unterstützt Geräte, die mit Azure AD und hybriden Domänen verknüpft sind, sowie durch das Gruppenrichtlinien-Tool registrierte Geräte. 
    > [!NOTE]
    > Für durch das Gruppenrichtlinien-Tool registrierte Szenarios: Der Endbenutzer verwendet das lokale Benutzerkonto zum Einbinden seines Windows 10-Geräts in Azure AD. Der Benutzer muss sich mit seinem Azure AD-Benutzerkonto auf dem Gerät anmelden und sich bei Intune registrieren. Intune installiert die Intune-Verwaltungserweiterung auf dem Gerät, wenn ein PowerShell-Skript oder eine Win32-App auf einen Benutzer oder ein Gerät ausgerichtet sind.
- Die Größe der Windows-Anwendung ist auf 8 GB pro App begrenzt.

## <a name="prepare-the-win32-app-content-for-upload"></a>Vorbereiten des Inhalts der Win32-App für den Upload

Verwenden Sie das [Microsoft Win32-Inhaltsvorbereitungstool](https://go.microsoft.com/fwlink/?linkid=2065730) zum Vorverarbeiten von klassischen Windows-Apps (Win32). Das Tool konvertiert Anwendungsinstallationsdateien in das *INTUNEWIN*-Format. Das Tool erkennt auch einige der Attribute, die Intune benötigt, um den Installationsstatus der Anwendung zu bestimmen. Nachdem Sie dieses Tool im Installationsordner der App verwendet haben, können Sie in der Intune-Konsole eine Win32-App erstellen.

> [!IMPORTANT]
> Beim Erstellen der *.intunewin*-Datei zippt das [Microsoft Win32-Inhaltsvorbereitungstool](https://go.microsoft.com/fwlink/?linkid=2065730) alle Dateien und Unterordner. Achten Sie darauf, das Microsoft Win32-Inhaltsvorbereitungstool nicht zusammen mit den Installationsdateien und -ordnern zu speichern, damit Sie das Tool oder andere unnötige Dateien und Ordner nicht in Ihre *.intunewin*-Datei einschließen.

Sie können das [Microsoft Win32-Inhaltsvorbereitungstool](https://go.microsoft.com/fwlink/?linkid=2065730) als ZIP-Datei von GitHub herunterladen. Die ZIP-Datei enthält einen Ordner namens **Microsoft-Win32-Content-Prep-Tool-master**. Der Ordner enthält das Vorbereitungstool, die Lizenz, eine Infodatei und die Versionshinweise. 

### <a name="process-flow-to-create-intunewin-file"></a>Prozessflow zum Erstellen der .intunewin-Datei

   ![Prozessflow zum Erstellen einer .intunewin-Datei](./media/prepare-win32-app.svg)

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Ausführen des Microsoft Win32-Inhaltsvorbereitungstools

Wenn Sie `IntuneWinAppUtil.exe` aus dem Befehlsfenster ohne Parameter ausführen, leitet Sie das Tool Schritt für Schritt durch die Eingabe der erforderlichen Parameter. Sie können dem Befehl die Parameter auch basierend auf den folgenden verfügbaren Befehlszeilenparametern hinzufügen:

### <a name="available-command-line-parameters"></a>Verfügbare Befehlszeilenparameter: 

|    **Befehlszeilenparameter**    |    **Beschreibung**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Hilfe    |
|    `-c <setup_folder>`     |    Ordner für alle Setupdateien. Alle Dateien in diesem Ordner werden in die *.intunewin*-Datei komprimiert.    |
|   ` -s <setup_file>`     |    Setupdatei (z. B. *setup.exe* oder *setup.msi*).    |
|    `-o <output_folder>`     |    Ausgabeordner für die generierte *.intunewin*-Datei.    |
|    `-q`       |    Stiller Modus    |

### <a name="example-commands"></a>Beispiele für Befehle

|    **Beispielbefehl**    |    **Beschreibung**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Dieser Befehl zeigt Nutzungsinformationen für das Tool an.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    Mit diesem Befehl wird die Datei `.intunewin` aus dem angegebenen Quellordner und der Setupdatei generiert. Für die MSI-Setupdatei ruft dieses Tool die erforderlichen Informationen für Intune ab. Wenn `-q` angegeben ist, wird der Befehl im stillen Modus ausgeführt, und wenn die Ausgabedatei bereits vorhanden ist, wird sie überschrieben. Wenn der Ausgabeordner nicht vorhanden ist, wird er automatisch erstellt.    |

Wenn Sie eine Datei mit der Erweiterung *.intunewin* generieren, legen Sie alle Dateien, die Sie als Referenz benötigen, in einem Unterordner des Setupordners ab. Verwenden Sie dann einen relativen Pfad, um auf die gewünschte Datei zu verweisen. Beispiel:

**Setupquellordner**: *c:\testapp\v1.0*<br>
**Lizenzdatei**: *c:\testapp\v1.0\licenses\license.txt*

Verweisen Sie auf die Datei *license.txt* mit dem relativen Pfad *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Erstellen, Zuweisen und Überwachen einer Win32-App

Ähnlich wie eine Branchenanwendung (LOB) können Sie eine Win32-App zu Microsoft Intune hinzufügen. Diese Art von App wird typischerweise intern oder von einem Drittanbieter geschrieben. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Prozessflow für das Hinzufügen einer Win32-App zu Intune

   ![Prozessflow für das Hinzufügen einer Win32-App zu Intune](./media/add-win32-app.svg)

### <a name="add-a-win32-app-to-intune"></a>Hinzufügen einer Win32-App zu Intune

Die folgenden Schritte enthaltenen Informationen zum Hinzufügen einer Windows-App zu Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3.  Wählen Sie im **Intune**-Bereich die Option **Client-Apps** > **Apps** > **Hinzufügen** aus.
4.  Wählen Sie **Windows-App (Win32)** aus der Dropdownliste im App-Bereich **Hinzufügen** aus.

    ![Screenshot des Blatts „App hinzufügen“ – Dropdownfeld zum Hinzufügen des Typs](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Schritt 2: Hochladen der App-Paketdatei

1.  Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus, um eine Datei auszuwählen. Der Bereich „App-Paketdatei“ wird angezeigt.

    ![Screenshot des Blatts „App-Paketdatei“](./media/apps-win32-app-02.png)

2.  Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine Windows-Installationsdatei mit der Erweiterung *.intunewin* aus.

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie die neueste Version des Microsoft Win32-Inhaltsvorbereitungstools verwenden. Wenn Sie nicht die neueste Version verwenden, wird eine Warnung angezeigt, die angibt, dass die App mit einer älteren Version des Tools verpackt wurde. 

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

    Wenn Ihr App-Dateiname z. B. **MyApp123** lautet, fügen Sie Folgendes hinzu:<br>
    `msiexec /p “MyApp123.msp”`<p>
    Wenn die Anwendung `ApplicationName.exe` ist, entspricht der Befehl dem Anwendungsnamen gefolgt von den Befehlsargumenten, die vom Paket unterstützt werden. <br>Beispiel:<br>
    `ApplicationName.exe /quiet`<br>
    Im obigen Befehl unterstützt das `ApplicationName.exe`-Paket das `/quiet`-Befehlsargument.<p> Wenden Sie sich für die spezifischen Argumente, die das Anwendungspaket unterstützt, an den Anbieter der Anwendung.

3.  Fügen Sie die vollständige Befehlszeile zum Deinstallieren hinzu, um die App basierend auf der GUID der App zu deinstallieren. 

    Beispiel: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Sie können eine Win32-App für die Installation im **Benutzerkontext** oder **Systemkontext** konfigurieren. Der **Benutzerkontext** bezieht nur auf einen bestimmten Benutzer. Der **Systemkontext** bezieht sich auf alle Benutzer eines Windows 10-Geräts.
    >
    > Endbenutzer müssen nicht beim Gerät angemeldet sein, um Win32-Apps zu installieren.
    > 
    > Die Installation und Deinstallation der Win32-App wird mit Administratorberechtigungen (standardmäßig) ausgeführt, wenn die App auf Installation im Benutzerkontext festgelegt ist, und der Endbenutzer auf dem Gerät über Administratorrechte verfügt.

4.  Wählen Sie danach **OK**.

### <a name="step-5-configure-app-requirements"></a>Schritt 5: Konfigurieren der App-Anforderungen

1.  Wählen Sie im Bereich **App hinzufügen** die Option **Anforderungen** aus, um die Anforderungen zu konfigurieren, die Geräte erfüllen müssen, bevor die App installiert wird.
2.  Konfigurieren Sie im Bereich **Add a Requirement rule** (Anforderungsregel hinzufügen) die folgenden Informationen: Einige der Werte in diesem Bereich wurden möglicherweise automatisch ausgefüllt.
    - **Betriebssystemarchitektur**: Wählen Sie die Architekturen aus, die für die Installation der App erforderlich sind.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie die für die Installation der App mindestens erforderliche Version des Betriebssystems aus.
    - **Erforderlicher Speicherplatz (MB)** : Optional können Sie den freien Speicherplatz hinzufügen, der auf dem Systemlaufwerk erforderlich ist, um die App zu installieren.
    - **Erforderlicher physischer Speicher (MB)** : Optional können Sie den für die Installation der App erforderlichen physischen Arbeitsspeicher (RAM) hinzufügen.
    - **Mindestens erforderliche Anzahl logischer Prozessoren**: Optional können Sie die Anzahl von logischen Prozessoren hinzufügen, die für die Installation der App mindestens erforderlich sind.
    - **Mindestens erforderliche CPU-Geschwindigkeit (MHz)** : Optional können Sie die CPU-Geschwindigkeit hinzufügen, die für die Installation der App mindestens erforderlich ist.

3. Klicken Sie auf **Hinzufügen**, um das Blatt **Add a Requirement rule** (Anforderungsregel hinzufügen) anzuzeigen und weitere Anforderungsregeln zu konfigurieren. Wählen Sie den **Anforderungstyp** aus, um die Art der Regel auszuwählen, mit der Sie bestimmen, auf welche Art eine Anforderung überprüft wird. Anforderungsregeln können auf Dateisysteminformationen, Registrierungswerten oder PowerShell-Skripts basieren. 
    - **Datei:** Wenn Sie **Datei** als **Anforderungstyp** auswählen, muss die Anforderungsregel eine Datei oder einen Ordner, ein Datum, eine Version oder eine Größe erkennen. 
        - **Pfad** – Der vollständige Pfad des Ordners, der die zu erkennende Datei oder den Ordner enthält.
        - **Datei oder Ordner** – Die zu erkennende Datei oder der zu erkennende Ordner.
        - **Eigenschaft:** Wählen Sie die Art der Regel aus, mit der das Vorhandensein der App überprüft wird.
        - **Einer 32-Bit-App auf 64-Bit-Clients zugeordnet** – Wählen Sie **Ja** aus, um alle Pfadumgebungsvariablen im 32-Bit-Kontext auf 64-Bit-Clients zu erweitern. Wählen Sie **Nein** (Standard) aus, um Pfadvariablen im 64-Bit-Kontext auf 64-Bit-Clients zu erweitern. 32-Bit-Clients verwenden immer den 32-Bit-Kontext.
    - **Registrierung:** Wenn Sie **Registrierung** als **Anforderungstyp** auswählen, muss die Anforderungsregel eine auf Wert, Zeichenfolge, Integer oder Version basierte Registrierungseinstellung erkennen.
        - **Schlüsselpfad** – Der vollständige Pfad des Registrierungseintrags, der den zu erkennenden Wert enthält.
        - **Wertname** – Gibt den Namen des Registrierungswerts an. Wenn dieser Wert leer ist, erfolgt die Erkennung über den Schlüssel. Der (Standard-) Wert eines Schlüssels wird als Erkennungswert verwendet, wenn die Erkennungsmethode eine andere ist als das Vorhandensein von Dateien oder Ordnern.
        - **Registrierungsschlüsselanforderung:** Wählen Sie die Art des verwendeten Registrierungsschlüsselvergleichs, um zu bestimmen, wie die Anforderungsregel überprüft wird.
        - **Einer 32-Bit-App auf 64-Bit-Clients zugeordnet** – Wählen Sie **Ja** aus, um die 32-Bit-Registrierung auf 64-Bit-Clients zu durchsuchen. Wählen Sie **Nein** (Standard) aus, um die 64-Bit-Registrierung auf 64-Bit-Clients zu durchsuchen. 32-Bit-Clients durchsuchen immer die 32-Bit-Registrierung.
    - **Skript:** Wählen Sie **Skript** als **Anforderungstyp** aus, wenn Sie keine Anforderungsregel erstellen können, die auf Datei, Registrierung oder auf einer anderen in der Intune-Konsole verfügbaren Methode basiert.
        - **Skriptdatei:** Für eine Anforderungsregel, die auf einem PowerShell-Skript basiert. Wenn der Exitcode ein 0 ist, erfolgt die Erfassung von STDOUT genauer. Sie können z. B. STDOUT als einen Integer erkennen, der einen Wert 1 aufweist.
        - **Skript auf 64-Bit-Clients als 32-Bit-Prozess ausführen**: Wählen Sie **Ja** aus, um das Skript in einem 32-Bit-Prozess auf 64-Bit-Clients auszuführen. Wählen Sie **Nein** (Standardeinstellung) aus, um das Skript in einem 64-Bit-Prozess auf 64-Bit-Clients auszuführen. Auf 32-Bit-Clients wird das Skript in einem 32-Bit-Prozess ausgeführt.
        - **Dieses Skript mit den Anmeldeinformationen des angemeldeten Benutzers ausführen:** Wählen Sie **Ja** aus, um das Skript mit den Anmeldeinformationen** des angemeldeten Geräts auszuführen.
        - **Skriptsignaturprüfung erzwingen** – Wählen Sie **Ja** aus, um sicherzustellen, dass das Skript von einem vertrauenswürdigen Herausgeber signiert ist, sodass das Skript ohne Warnungen oder Aufforderungen ausgeführt werden kann. Das Skript wird ohne Blockierung ausgeführt. Wählen Sie **Nein** (Standard) aus, um das Skript mit Endbenutzerbestätigung ohne Signaturüberprüfung auszuführen.
        - **Ausgabedatentyp auswählen:** Wählen Sie den Datentyp aus, der beim Bestimmen einer Übereinstimmung mit einer Anforderungsregel verwendet wird.
4.  Wählen Sie danach **OK**.

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
            
            2.  Überprüfen Sie, ob der Registrierungswert vorhanden ist.
        
                ![Screenshot des Erkennungsregelbereichs – Registrierungswertvorkommen](./media/apps-win32-app-06.png)    
        
            3.  Überprüfen Sie, ob die Zeichenfolge für den Registrierungswert identisch ist.
        
                ![Screenshot des Erkennungsregelbereichs – Gleichheit der Registrierungsschlüsselzeichenfolge](./media/apps-win32-app-07.png)    
     
    - **Benutzerdefiniertes Erkennungsskript verwenden** – Geben Sie das PowerShell-Skript an, das zum Erkennen dieser App verwendet werden soll. 
    
        1.  **Skriptdatei** – Wählen Sie ein PowerShell-Skript aus, das das Vorhandensein der App auf dem Client erkennt. Die App wird erkannt, wenn das Skript sowohl einen 0-Wert als Exitcode zurückgibt als auch einen Zeichenfolgenwert an STDOUT ausgibt.

        2.  **Skript auf 64-Bit-Clients als 32-Bit-Prozess ausführen**: Wählen Sie **Ja** aus, um das Skript in einem 32-Bit-Prozess auf 64-Bit-Clients auszuführen. Wählen Sie **Nein** (Standardeinstellung) aus, um das Skript in einem 64-Bit-Prozess auf 64-Bit-Clients auszuführen. Auf 32-Bit-Clients wird das Skript in einem 32-Bit-Prozess ausgeführt.

        3.  **Skriptsignaturprüfung erzwingen** – Wählen Sie **Ja** aus, um sicherzustellen, dass das Skript von einem vertrauenswürdigen Herausgeber signiert ist, sodass das Skript ohne Warnungen oder Aufforderungen ausgeführt werden kann. Das Skript wird ohne Blockierung ausgeführt. Wählen Sie **Nein** (Standard) aus, um das Skript mit Endbenutzerbestätigung ohne Signaturüberprüfung auszuführen.
    
            Der Intune-Agent überprüft die Ergebnisse des Skripts. Es liest die Werte, die vom Skript in den Standardausgabestream (STDOUT), den Standardfehlerstream (STDERR) und den Exitcode geschrieben wurden. Wenn das Skript mit einem Wert ungleich 0 (null) beendet wird, schlägt das Skript fehl und der Erkennungszustand der Anwendung ist „nicht installiert“. Wenn der Exitcode gleich null ist und in „STDOUT“-Daten enthalten sind, ist der Erkennungszustand der Anwendung „Installiert“. 

            > [!NOTE]
            > Microsoft empfiehlt, Ihr Skript in UTF-8 zu codieren. Wenn das Skript mit dem Wert 0 beendet wird, war die Skriptausführung erfolgreich. Der zweite Ausgabekanal zeigt an, dass die App erkannt wurde – STDOUT-Daten zeigen an, dass die App auf dem Client gefunden wurde. Wir suchen nicht nach einer bestimmten Zeichenfolge von STDOUT.

        4.  Nachdem Sie Ihre Regel(n) hinzugefügt haben, wählen Sie **Hinzufügen** > **OK** aus.

### <a name="step-7-configure-app-return-codes"></a>Schritt 7: Konfigurieren der App-Rückgabecodes

1.  Wählen Sie im Bereich **App hinzufügen** die Option **Rückgabecodes** aus, um die Rückgabecodes hinzuzufügen, die verwendet werden, um entweder das Verhalten bei der erneuten Installation der App oder das Verhalten nach der Installation anzugeben. Rückgabecodeeinträge werden standardmäßig bei der Erstellung der App hinzugefügt. Sie können jedoch zusätzliche Rückgabecodes hinzufügen oder bestehende Rückgabecodes ändern. 
2.  Fügen Sie im Bereich **Rückgabecodes** zusätzliche Rückgabecodes hinzu oder ändern Sie bestehende Rückgabecodes.
    - **Fehlerhaft** – Der Rückgabewert, der auf einen Installationsfehler der App hinweist.
    - **Harter Neustart** – Der Rückgabecode für den harten Neustart gestattet es nicht, dass nachfolgende Win32-Apps ohne Neustart auf dem Client installiert werden. 
    - **Softneustart** – Der Rückgabecode „Softneustart“ ermöglicht es, die nächste Win32-App zu installieren, ohne dass ein Neustart des Clients erforderlich ist. Ein Neustart ist erforderlich, um die Installation der aktuellen Anwendung abzuschließen.
    - **Wiederholen** – Der Rückgabecode-Agent versucht dreimal, die App zu installieren. Zwischen den einzelnen Versuchen wird fünf Minuten gewartet. 
    - **Erfolg** – Der Rückgabewert, der angibt, dass die App erfolgreich installiert wurde.
3.  Wählen Sie **OK** aus, nachdem Sie Ihre Liste der Rückgabecodes hinzugefügt oder geändert haben.

### <a name="step-8-add-the-app"></a>Schritt 8: Hinzufügen der App

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

An dieser Stelle haben Sie alle Schritte zum Hinzufügen einer Win32-App zu Intune abgeschlossen. Informationen zur Zuweisung und Überwachung von Apps finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) und [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="app-dependencies"></a>App-Abhängigkeiten

App-Abhängigkeiten sind Anwendungen, die installiert sein müssen, bevor Ihre Win32-App installiert werden kann. Sie können anfordern, dass andere Apps als Abhängigkeiten installiert werden. Das heißt, das Gerät muss die abhängige(n) App(s) installieren, bevor die Win32-App installiert wird. Es sind maximal 100 Abhängigkeiten möglich. Dazu zählen die Abhängigkeiten aller eingeschlossenen Abhängigkeiten sowie die App selbst. Sie können Win32-App-Abhängigkeiten erst hinzufügen, nachdem Ihre Win32-App zu Intune hinzugefügt und darin hochgeladen wurde. Sobald Ihre Win32-App hinzugefügt wurde, sehen Sie die Option **Abhängigkeiten** auf dem Blatt für Ihre Win32-App. 

Wenn Sie eine App-Abhängigkeit hinzufügen, können Sie basierend auf dem Namen und dem Herausgeber der App Suchvorgänge ausführen. Darüber hinaus können Sie Ihre hinzugefügten Abhängigkeiten nach Name und Herausgeber der App sortieren. Bereits zuvor hinzugefügte App-Abhängigkeiten können nicht aus der Liste der hinzugefügten App-Abhängigkeiten ausgewählt werden. 

Sie können auswählen, ob jede abhängige App automatisch installiert wird. Standardmäßig ist für die Option **Automatisch installieren** für jede Abhängigkeit **Ja** festgelegt. Durch das automatische Installieren einer abhängigen App, selbst wenn diese nicht auf den Benutzer oder das Gerät ausgerichtet ist, installiert Intune die App auf dem Gerät. Dadurch wird das Abhängigkeitskriterium erfüllt, bevor Ihre Win32-App installiert wird. Dabei ist es wichtig, zu beachten, dass eine Abhängigkeit rekursive Unterabhängigkeiten haben kann, und jede Unterabhängigkeit vor der Hauptabhängigkeit installiert wird. Zudem erfolgt die Installation von Abhängigkeiten nicht in einer Installationsreihenfolge auf einer vorgegebenen Abhängigkeitsebene.

Führen Sie die folgenden Schritte aus, um eine App-Abhängigkeit zu Ihrer Win32-App hinzuzufügen:

1. Wählen Sie in Intune **Client-Apps** > **Apps** aus, um die Liste der hinzugefügten Client-Apps anzuzeigen. 
2. Wählen Sie eine hinzugefügte **Windows-App (Win32)** aus. 
3. Klicken Sie auf **Abhängigkeiten**, um die abhängigen Apps hinzuzufügen, die installiert werden müssen, bevor die Win32-App installiert werden kann. 
4. Klicken Sie auf **Hinzufügen**, um eine App-Abhängigkeit hinzuzufügen.
5. Nachdem Sie die abhängige(n) App(s) hinzugefügt haben, klicken Sie auf **Auswählen**.
6. Wählen Sie durch Klicken auf **Ja** oder **Nein** unter **Automatisch installieren** aus, ob die abhängige App automatisch installiert werden soll.
7. Klicken Sie auf **Speichern**.

Dem Endbenutzer werden Windows-Popupbenachrichtigungen angezeigt, die angeben, dass abhängige Apps heruntergeladen und zusammen mit der Win32-App installiert werden. Wenn darüber hinaus eine abhängige App nicht installiert ist, wird dem Endbenutzer in der Regel eine der folgenden Benachrichtigungen angezeigt:
- 1 or more dependent apps failed to install (Fehler bei der Installation von mindestens einer abhängigen App)
- 1 or more dependent app requirements not met (Mindestens eine abhängige App-Anforderung ist nicht erfüllt)
- 1 or more dependent apps are pending a device reboot (Geräteneustart für mindestens eine abhängige App ausstehend)

Wenn Sie für die Option **Automatisch installieren** die Auswahl „Nein“ festlegen, erfolgt kein Versuch, die Win32-App (Abhängigkeit) zu installieren. Darüber hinaus zeigt die App-Berichterstellung, dass die Abhängigkeit als `failed` gekennzeichnet wurde, und gibt eine Fehlerursache an. Durch Klicken auf einen Fehler (oder eine Warnung) in den [Installationsdetails](troubleshoot-app-install.md#win32-app-installation-troubleshooting) der Win32-App können Sie den Installationsfehler für die Abhängigkeit anzeigen. 

Jede Abhängigkeit entspricht der Wiederholungslogik für Win32-Apps in Intune (3 Installationsversuche mit jeweils 5 Minuten Wartezeit dazwischen) und dem globalen Zeitplan für die erneute Auswertung. Abhängigkeiten gelten außerdem nur während die Win32-App auf dem Gerät installiert wird. Abhängigkeiten gelten nicht, wenn eine Win32-App deinstalliert wird. Klicken Sie auf die Ellipsen (drei Punkte) links neben der abhängigen App am Ende des Datensatzes der Abhängigkeitsliste, um eine Abhängigkeit zu löschen. 

## <a name="delivery-optimization"></a>Übermittlungsoptimierung

Clients von Windows 10 Version 1709 und höher laden Intune Win32-App-Inhalte mit einer Komponente zur Übermittlungsoptimierung auf den Windows 10-Client herunter. Die Übermittlungsoptimierung bietet Peer-zu-Peer-Funktionen, die standardmäßig eingeschaltet sind. Die Übermittlungsoptimierung kann mit dem Gruppenrichtlinien-Tool und über die Intune-Gerätekonfiguration konfiguriert werden. Weitere Informationen finden Sie unter [Übermittlungsoptimierung für Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Installieren erforderlicher und verfügbarer Apps auf Geräten

Der Endbenutzer erhält Windows-Popupbenachrichtigungen für die erforderlichen und verfügbaren App-Installationen. Die folgende Abbildung zeigt eine exemplarische Popupbenachrichtigung, bei der die App-Installation erst nach einem Neustart des Geräts abgeschlossen ist. 

![Screenshot der Windows-Popupbenachrichtigungen für eine App-Installation](./media/apps-win32-app-08.png)    

Die folgende Abbildung zeigt dem Endbenutzer an, dass App-Änderungen am Gerät vorgenommen werden.

![Screenshot mit einer Benachrichtigung an den Benutzer, dass Änderungen an der App vorgenommen wurden](./media/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Popupbenachrichtigungen für Win32-Apps 
Bei Bedarf können Sie die Anzeige von Popupbenachrichtigungen für die Benutzer pro App-Zuweisung unterdrücken. Wählen Sie in Intune **Client-Apps** > **Apps** > App-Auswahl > **Zuweisungen** > **Gruppen einschließen**. 

> [!NOTE]
> Win32-Apps, die über die Intune-Verwaltungserweiterung installiert wurden, werden auf Geräten mit aufgehobener Registrierung nicht deinstalliert. Administratoren können Zuweisungsausnahmen nutzen, um Win32-Apps für BYOD-Geräte auszuschließen.

## <a name="troubleshoot-win32-app-issues"></a>Behandeln von Win32-App-Problemen
Agentprotokolle auf dem Clientcomputer befinden sich häufig unter `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Sie können `CMTrace.exe` nutzen, um diese Protokolldateien anzuzeigen. *CMTrace.exe* kann unter [Configuration Manager-Tools](https://docs.microsoft.com/sccm/core/support/tools) heruntergeladen werden. 

![Screenshot der Agent-Protokolle auf dem Clientcomputer](./media/apps-win32-app-10.png)    

> [!IMPORTANT]
> Durch die entsprechenden Antischadsoftwareeinstellungen sollte die Überprüfung der folgenden Verzeichnisse ausgeschlossen werden, damit Win32-Branchenanwendungen ordnungsgemäß installiert und ausgeführt werden können:<p>
> **Auf X64-Clientcomputern:**<br>
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **Auf X86-Clientcomputern:**<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>Ermitteln der Dateiversion einer Win32-App mithilfe von PowerShell

Wenn es für Sie schwierig ist, die Dateiversion einer Win32-App zu ermitteln, erwägen Sie die Verwendung oder Änderung des folgenden PowerShell-Befehls:

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}

```
Ersetzen Sie im vorstehenden PowerShell-Befehl die Zeichenfolge `<path to binary file>` durch den Pfad zu Ihrer Win32-App-Datei. Ein Beispielpfad würde etwa so aussehen:<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

Ersetzen Sie außerdem die Zeichenfolge `<file version of successfully detected file>` durch die Dateiversion, die Sie ermitteln müssen. Eine Beispielzeichenfolge für die Dateiversion würde etwa so aussehen:<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Wenn Sie die Versionsinformationen zu Ihrer Win32-App abrufen müssen, können Sie den folgenden PowerShell-Befehl verwenden:

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

Ersetzen Sie im vorstehenden PowerShell-Befehl `<path to binary file>` durch Ihren Dateipfad.

### <a name="additional-troubleshooting-areas-to-consider"></a>Weitere zu berücksichtigende Problembehandlungsbereiche
- Überprüfen Sie die Zielgruppenadressierung, um sicherzustellen, dass der Agent auf dem Gerät installiert ist – Win32-App, die auf eine Gruppe ausgerichtet ist, oder PowerShell-Skript, das auf eine Gruppe ausgerichtet ist, erstellt die Installationsrichtlinie für die Sicherheitsgruppe.
- Überprüfen Sie die Betriebssystemversion – Windows 10 1607 und höher.  
- Überprüfen Sie die Windows 10 SKU – Windows 10 S oder Windows-Versionen, die mit aktiviertem S-Modus ausgeführt werden, unterstützen keine MSI-Installation.

Weitere Informationen zur Behandlung von Problemen mit Win32-Apps finden Sie unter [Win32 app installation troubleshooting (Problembehandlung bei der Win32-App-Installation)](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Hinzufügen von Apps zu Intune finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).
