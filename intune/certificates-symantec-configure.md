---
title: Ausstellen von Symantec-PKCS-Zertifikaten mit Microsoft Intune
titlesuffix: ''
description: Installieren und Konfigurieren des Intune Certificate Connectors, um PKCS-Zertifikate aus dem Symantec PKI-Manager-Webdienst für mit Intune verwaltete Geräte auszustellen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d9c9027964648ad83c552f7dd7067598cacf560e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31836524"
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Einrichten des Intune Certificate Connectors für den Symantec PKI-Manager-Webdienst

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel erfahren Sie, wie Sie den Intune Certificate Connector installieren und konfigurieren, um PKCS-Zertifikate aus dem Symantec PKI-Manager-Webdienst für mit Intune verwaltete Geräte auszustellen.

Der Symantec PKI-Manager-Webdienst wird in diesem Artikel als Symantec-Zertifizierungsstelle bezeichnet. Wenn Sie den Intune Certificate Connector bereits für das Ausstellen von PKCS- und SCEP-Zertifikaten der Microsoft-Zertifizierungsstelle (CA) konfiguriert haben, kann derselbe Connector zum Konfigurieren und Ausstellen von PKCS-Zertifikaten einer Symantec-Zertifizierungsstelle verwendet werden. In diesem Fall kann der Intune Certificate Connector folgende Zertifikate ausstellen:

* PKCS-Zertifikate von einer Microsoft-Zertifizierungsstelle
* SCEP-Zertifikate von einer Microsoft-Zertifizierungsstelle
* PKCS-Zertifikate von einer Symantec-Zertifizierungsstelle

Wenn Sie den Intune Certificate Connector sowohl für die Microsoft-Zertifizierungsstelle als auch für die Symantec-Zertifizierungsstelle verwenden möchten, müssen Sie zuerst die Intune Certificate Connector-Konfiguration für die Microsoft-Zertifizierungsstelle durchführen und dann diese Schritte befolgen, um ihn für die Symantec-Zertifizierungsstelle zu konfigurieren.  Weitere Informationen zum Konfigurieren des Intune Certificate Connectors für eine Microsoft-Zertifizierungsstelle finden Sie unter [Konfigurieren von Zertifikaten in Microsoft Intune](certificates-configure.md).

## <a name="prepare-to-install-intune-certificate-connector"></a>Vorbereiten der Installation des Microsoft Intune Certificate Connectors

Wenn Sie den Intune Certificate Connector bereits für eine vorhandene Microsoft-Zertifizierungsstelle verwenden und Unterstützung für Symantec hinzufügen möchten, überspringen Sie diesen Schritt, und fahren Sie mit den übrigen Schritten fort, sobald Sie über das Intune-Verwaltungsportal den neuesten Intune Certificate Connector installiert haben. Dieser Schritt ist nur erforderlich, wenn Sie den Intune Certificate Connector für eine eigenständige Symantec-Zertifizierungsstelle verwenden möchten.

1. Wählen Sie eine der Windows-Betriebssystemversionen aus der folgenden Liste aus, und installieren Sie sie auf einem Computer:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Erstellen Sie einen Benutzer mit Administratorrechten, und verwenden Sie ihn zum Durchführen der folgenden Schritte.

3. Suchen Sie nach den neuesten Windows-Updates, und installieren Sie sie gegebenenfalls.

   > [!IMPORTANT]
   > Nach der Installation der Windows-Updates starten Sie den Computer neu.

4. Installieren Sie .NET Framework 3.5:

    ein. Öffnen Sie **Systemsteuerung** > **Programme und Features** > **Windows-Features aktivieren oder deaktivieren**.

    b. Wählen Sie **.NET Framework 3.5** aus, und installieren Sie es.

## <a name="install-the-symantec-registration-authorization-certificate"></a>Installieren des Symantec-Zertifikat zur Registrierungsautorisierung

Verwenden Sie die folgenden Schritte, um das RA-Zertifikat (Registrierungsautorisierung) von der Symantec-Zertifizierungsstelle zu erhalten. Sie benötigen ein aktives Abonnement bei der Symantec-Zertifizierungsstelle, um das RA-Zertifikat abzurufen.

1. Speichern Sie den folgenden Codeausschnitt in einer Datei namens **certreq.ini**, und aktualisieren Sie ihn nach Bedarf (z.B.: *Subject name in CN format*).

   ```
    [Version] 
    Signature="$Windows NT$" 

    [NewRequest] 
    ;Change to your,country code, company name and common name 
    Subject = "Subject Name in CN format"

    KeySpec = 1 
    KeyLength = 2048 
    Exportable = TRUE 
    MachineKeySet = TRUE 
    SMIME = False 
    PrivateKeyArchive = FALSE 
    UserProtected = FALSE 
    UseExistingKeySet = FALSE 
    ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
    ProviderType = 12 
    RequestType = PKCS10 
    KeyUsage = 0xa0 

    [EnhancedKeyUsageExtension] 
    OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication

    ;----------------------------------------------- 
   ```

2. Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und generieren Sie CSR-Inhalt mit dem folgenden Befehl:

   `Certreq.exe -new certreq.ini request.csr`

3. Öffnen Sie die Datei „request.csr“ in Editor, und kopieren Sie den CSR-Inhalt im folgenden Format:

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Melden Sie sich bei der Symantec-Zertifizierungsstelle an, und navigieren Sie von den Aufgaben aus zu **Get an RA Cert** (RA-Zertifikat abrufen).

   ein. Geben Sie den CSR-Inhalt aus Schritt 3 in das entsprechende Textfeld ein.

   b. Geben Sie den Anzeigenamen des Zertifikats in das entsprechende Textfeld ein.

   c. Klicken Sie auf **Continue**(Weiter).

      Ihnen wird ein Link zum Herunterladen des RA-Zertifikats angezeigt.

   d. Laden Sie das RA-Zertifikat auf den lokalen Computer herunter.

5. Importieren Sie das RA-Zertifikat in den Windows-Zertifikatspeicher:

    ein. Öffnen Sie eine MMC-Konsole.

    b. Klicken Sie auf **Datei** > **Snap-Ins hinzufügen bzw. entfernen** > **Zertifikat**, und klicken Sie dann auf **Hinzufügen**.

    c. Wählen Sie **Computerkonto** aus, und klicken Sie dann auf **Weiter**.

    d. Klicken Sie auf **Lokaler Computer** und dann auf **Fertig stellen**.

    e. Klicken Sie im Fenster **Snap-Ins hinzufügen oder entfernen** auf **OK**. Erweitern Sie **Zertifikate (lokaler Computer)** > **Persönlich** > **Zertifikate**.

    f. Klicken Sie mit der rechten Maustaste auf den Knoten **Zertifikat**, und wählen Sie **Alle Aufgaben** > **Importieren** aus.

    g. Wählen Sie den Speicherort des RA-Zertifikats aus, das Sie von der Symantec-Zertifizierungsstelle heruntergeladen haben, und klicken Sie auf **Weiter**.

    h. Wählen Sie **Persönlicher Zertifikatspeicher**, und klicken Sie dann auf **Weiter**.

    i. Klicken Sie auf **Fertig stellen**. Dadurch wird das RA-Zertifikat zusammen mit seinem privaten Schlüssel in den persönlichen Speicher auf dem lokalen Computer importiert.  

6. Exportieren und importieren Sie das Zertifikat mit dem privaten Schlüssel:

    ein. Erweitern Sie **Zertifikate (lokaler Computer)** > **Persönlich** > **Zertifikate**.

    b. Wählen Sie das Zertifikat aus, das im vorherigen Schritt importiert wurde.

    c. Klicken Sie mit der rechten Maustaste auf das Zertifikat, und wählen Sie **Alle Aufgaben** > **Exportieren**.

    d. Klicken Sie auf **Weiter**, und geben Sie das Kennwort ein.

    e. Wählen Sie den Speicherort für den Export, und klicken Sie auf **Fertig stellen**.

    f. Führen Sie das gleiche Verfahren in Schritt 5 durch, um das Zertifikat mit dem privaten Schlüssel in den persönlichen Speicher auf dem lokalen Computer zu importieren.

7. Kopieren Sie den RA-Zertifikatfingerabdruck ohne Leerzeichen.  Im Folgenden sehen Sie einen Beispielfingerabdruck:

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > Wenn Probleme mit dem Abrufen des RA-Zertifikats von der Symantec-Zertifizierungsstelle auftreten, wenden Sie sich an den Kundensupport von Symantec.

## <a name="install-intune-certificate-connector"></a>Installieren des Intune Certificate Connectors

Wenn Sie den neuesten Intune Certificate Connector bereits für eine vorhandene Microsoft-Zertifizierungsstelle verwenden und Unterstützung für eine Symantec-Zertifizierungsstelle hinzufügen möchten, überspringen Sie diesen Schritt. Laden Sie andernfalls den neuesten Intune Certificate Connector aus dem Intune-Verwaltungsportal herunter, und befolgen Sie die folgenden Anweisungen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
4. Klicken Sie im Bereich **Gerätekonfiguration** auf die Option **Zertifizierungsstelle**.
5. Klicken Sie zuerst auf **Hinzufügen** und dann auf **Laden Sie die Connectordatei herunter**. Speichern Sie den Download an einem Speicherort, auf den Sie auf dem Server, auf dem der Connector installiert wird, zugreifen können. 
3. Führen Sie „NDESConnectorSetup.exe“ mit erweiterten Berechtigungen aus.

    ein. Wählen Sie auf dem Bildschirm **Installationsoptionen** die Option **PFX-Verteilung** aus, wie im folgenden Screenshot gezeigt.  Führen Sie das verbleibende Setup mit der Standardauswahl durch.

   > [!IMPORTANT]
   > Wenn Sie den Intune Certificate Connector zum Ausstellen von Zertifikaten von einer Microsoft-Zertifizierungsstelle und von einer Symantec-Zertifizierungsstelle konfigurieren möchten, wählen Sie **SCEP- und PFX-Profilverteilung**. Führen Sie das verbleibende Setup mit der Standardauswahl durch.

   ![InstallConnector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Konfigurieren des Intune Certificate Connectors

Der Intune Certificate Connector wird standardmäßig unter `%ProgramFiles%\Microsoft Intune` installiert.

1. Öffnen Sie in Editor die Datei „%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config“.

    ein. Aktualisieren Sie den Wert des RACertThumbprint-Schlüssels mit dem Wert des Zertifikatfingerabdrucks, den Sie im vorherigen Abschnitt kopiert haben.  Im Folgenden finden Sie ein Beispiel:

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. Speichern und schließen Sie die Datei.

2. Öffnen Sie „services.msc“.

    ein. Wählen Sie **Intune-Connectordienst**.

    b. Beenden Sie den Dienst, und starten Sie ihn dann wieder.

    c. Schließen Sie das Fenster "Dienste".

## <a name="setup-the-intune-administrator-account"></a>Einrichten des Intune-Administratorkontos

Wenn Sie den Intune Certificate Connector bereits für eine vorhandene Microsoft-Zertifizierungsstelle verwenden und Unterstützung für eine Symantec-Zertifizierungsstelle hinzufügen möchten, überspringen Sie diesen Schritt, und fahren Sie mit den übrigen Schritten fort. 

1. Starten Sie die Benutzeroberfläche des NDES-Connectors von ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe ` aus.

    ein. Klicken Sie auf die Registerkarte **Registrierung**, und klicken Sie dann auf **Anmelden**.

    b. Geben Sie Ihre Administratoranmeldeinformationen für den Intune-Mandanten in den entsprechenden Textfeldern an.

    c. Klicken Sie auf **Anmelden**.  Ein Bestätigungsdialogfeld mit der Meldung **Erfolgreich registriert** wird angezeigt, wie im folgenden Screenshot dargestellt.
2. Schließen Sie die Benutzeroberfläche des NDES-Connectors.

![ConfigureConnector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>Erstellen eines vertrauenswürdigen Zertifikatprofils

Die für mit Intune verwaltete Geräte bereitgestellten PKCS-Zertifikate müssen mit einem vertrauenswürdigen Stammzertifikat verkettet werden. Dazu müssen Sie ein vertrauenswürdiges Intune-Zertifikatprofil mit dem Stammzertifikat erstellen, das Sie von der Symantec-Zertifizierungsstelle erhalten haben.

1. Rufen Sie ein vertrauenswürdiges Stammzertifikat aus der Symantec-Zertifizierungsstelle ab:

    ein. Melden Sie sich beim Symantec-Verwaltungsportal für Zertifizierungsstellen an.

    b. Klicken Sie unter „Tasks“ (Aufgaben) auf „Manage CAs“ (Zertifizierungsstellen verwalten).

    c. Wählen Sie die entsprechende Zertifizierungsstelle aus der Liste der Zertifizierungsstellen aus.

    d. Klicken Sie auf „Download root certificate“ (Stammzertifikat herunterladen), um das vertrauenswürdige Stammzertifikat herunterzuladen.

2. Erstellen Sie ein vertrauenswürdiges Zertifikatprofil im Intune-Verwaltungsportal:

    ein. Melden Sie sich mit den Administratoranmeldeinformationen für den Intune-Mandanten beim [Azure-Portal](https://portal.azure.com) an, und suchen Sie nach Intune Ressourcen.

    b. Erstellen Sie ein vertrauenswürdiges Zertifikatprofil über **Microsoft Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen**.

    c. Geben Sie die erforderliche Informationen in den Feldern **Name** und **Beschreibung** an, und wählen Sie dann die Zielplattform aus. 

    d. Wählen Sie in der Dropdownliste „Profiltyp“ das vertrauenswürdige Zertifikatprofil aus.

    e. Laden Sie das vertrauenswürdige Stammzertifikat hoch, das Sie von der Symantec-Zertifizierungsstelle im vorherigen Schritt erhalten haben.

    f. Führen Sie die verbleibenden Schritte zur Profilerstellung durch. 

    g. Klicken Sie auf **Zuweisungen**, und wählen Sie die entsprechende Gruppe aus.  Mindestens ein Benutzer oder ein Gerät muss der zugewiesenen Gruppe angehören.

## <a name="get-the-certificate-profile-oid"></a>Abrufen der Zertifikatprofil-OID

Die Zertifikatprofil-OID ist einer Zertifikatprofilvorlage in der Symantec-Zertifizierungsstelle zugeordnet.  Um im Intune-Verwaltungsportal ein PKCS-Zertifikatprofil zu erstellen, muss der Name der Zertifikatvorlage in Form einer Zertifikatprofil-OID angegeben werden, die einer Zertifikatvorlage in der Symantec-Zertifizierungsstelle zugeordnet ist.

1. Melden Sie sich beim Symantec-Verwaltungsportal für Zertifizierungsstellen an.
2. Klicken Sie auf „Manage Certificate Profiles“ (Zertifikatprofile verwalten).
3. Wählen Sie das zu verwendende Zertifikatprofil aus.
4. Kopieren Sie die Zertifikatprofil-OID. Sie sieht etwa folgendermaßen aus:

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > Wenn beim Abrufen der Zertifikatprofil-OID Probleme auftreten, wenden Sie sich an den Kundensupport von Symantec.

## <a name="create-a-pkcs-certificate-profile"></a>Erstellen eines PKCS-Zertifikatprofils

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen für den Intune-Mandanten beim [Azure-Portal](https://portal.azure.com) an, und suchen Sie nach Intune Ressourcen.
2. Erstellen Sie ein PKCS-Zertifikatprofil über **Microsoft Intune** > **Gerätekonfiguration > Profile** > **Profil erstellen**.

    ein. Geben Sie die erforderlichen Informationen in den Feldern **Name** und **Beschreibung** an, und wählen Sie dann die Zielplattform aus.

    b. Wählen Sie in der Dropdownliste **Profiltyp** das **PKCS-Zertifikatprofil** aus.  

    c. Schließen Sie die verbleibenden Schritte zum Erstellen des Profils ab.

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > Die folgenden Parameter des PKCS-Zertifikatprofils müssen mit den in der folgenden Tabelle angegebenen Werten konfiguriert werden (wie im Screenshot gezeigt), um PKCS-Zertifikate über den Intune Certificate Connector von der Symantec-Zertifizierungsstelle aus auszustellen. 

    |PKCS-Zertifikatparameter | Wert | Beschreibung |
    | --- | --- | --- |
    | Zertifizierungsstelle | pki-ws.symauth.com | Dieser Wert muss dem vollqualifizierten Domänennamen (FQDN) des Basisdiensts der Symantec-Zertifizierungsstelle ohne nachgestellte Schrägstriche entsprechen.  Wenn Sie nicht sicher sind, ob dies der richtige Basisdienst-FQDN für Ihr Symantec-Zertifizierungsstellenabonnement ist, wenden Sie sich an den Symantec-Kundendienst. <br><br> Wenn dieser FQDN falsch ist, stellt der Intune Certificate Connector keine PKCS-Zertifikate von der Symantec-Zertifizierungsstelle aus.| 
    | Name der Zertifizierungsstelle | Symantec | Dieser Wert muss der Zeichenfolge **Symantec** entsprechen. <br><br> Wenn dieser Wert geändert wird, stellt der Intune Certificate Connector keine PKCS-Zertifikate von der Symantec-Zertifizierungsstelle aus.|
    | Name der Zertifikatvorlage | Die Zertifikatprofil-OID von der Symantec-Zertifizierungsstelle. <br><br> Beispiel: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| Dieser Wert muss eine Zertifikatprofil-OID sein, die im vorherigen Abschnitt aus der Zertifikatprofilvorlage der Symantec-Zertifizierungsstelle abgerufen wurde. <br><br> Wenn der Intune Certificate Connector keine Zertifikatvorlage findet, die dieser Zertifikatprofil-OID in der Symantec-Zertifizierungsstelle zugeordnet ist, werden keine PKCS-Zertifikate von der Symantec-Zertifizierungsstelle ausgestellt.|

   > [!NOTE]
   > Die PKCS-Zertifikatprofile für Windows-Plattformen müssen keinem vertrauenswürdigen Zertifikatprofil zugeordnet sein. Für Nicht-Windows-Plattformprofile wie z.B. Android ist dies hingegen erforderlich.

3. Klicken Sie auf **Zuweisungen**, und wählen Sie die entsprechende Gruppe aus.  Mindestens ein Benutzer oder ein Gerät muss der zugewiesenen Gruppe angehören.
 
Nach Abschluss der vorherigen Schritte stellt der Intune Certificate Connector PKCS-Zertifikate von der Symantec-Zertifizierungsstelle für mit Intune verwaltete Geräte in der zugewiesenen Gruppe aus. Diese Zertifikate stehen im persönlichen Speicher des Zertifikatspeichers des aktuellen Benutzers auf dem mit Intune verwalteten Gerät zur Verfügung.

### <a name="pkcs-certificate-profile-supported-attributes"></a>Vom PKCS-Zertifikatprofil unterstützte Attribute

|Attribut | Von Intune unterstützte Formate | Von der Symantec-Cloudzertifizierungsstelle unterstützte Formate | Result |
| --- | --- | --- | --- |
| Antragstellername |Intune unterstützt den Antragstellernamen nur in den folgenden drei Formaten: <br><br> 1. Allgemeiner Name <br> 2. Allgemeiner Name einschließlich E-Mail-Adresse <br> 3. Allgemeiner Name als E-Mail-Adresse <br><br> Im Folgenden finden Sie ein Beispiel: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | Die Symantec-Zertifizierungsstelle unterstützt zusätzliche Attribute.  Wenn Sie zusätzliche Attribute auswählen möchten, müssen diese mit festen Werten in der Symantec-Zertifikatprofilvorlage definiert werden.| Wir verwenden den allgemeinen Namen oder die E-Mail-Adresse aus der PKCS-Zertifikatanforderung. <br><br> Konflikte bei der Attributauswahl zwischen dem Intune-Zertifikatprofil und der Symantec-Zertifikatprofilvorlage führen dazu, dass von der Symantec-Zertifizierungsstelle keine Zertifikate ausgestellt werden.|
| SAN | Intune unterstützt nur die folgenden SAN Feldwerte: <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (codierter Wert) | Die Symantec-Cloudzertifizierungsstelle unterstützt diese Parameter ebenfalls. Wenn Sie zusätzliche Attribute auswählen möchten, müssen diese mit festen Werten in der Symantec-Zertifikatprofilvorlage definiert werden. <br><br> AltNameTypeEmail: Wenn dieser Typ im SAN nicht gefunden wird, wird der Wert von AltNameTypeUpn verwendet.  Wenn auch AltNameTypeUpn im SAN nicht gefunden wird, wird der Wert des Antragstellernamens verwendet, sofern dieser im E-Mail-Adressformat vorliegt.  Wird auch dieser nicht gefunden, kann der Intune Certificate Connector keine Zertifikate ausstellen. <br><br> Beispiel: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: Wenn dieser Typ im SAN nicht gefunden wird, wird der Wert von AltNameTypeEmail verwendet. Wenn auch AltNameTypeEmail im SAN nicht gefunden wird, wird der Wert des Antragstellernamens verwendet, sofern dieser im E-Mail-Adressformat vorliegt.  Wird auch dieser nicht gefunden, kann der Intune Certificate Connector keine Zertifikate ausstellen.  <br><br> Beispiel: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: Wenn dieser Typ im SAN nicht gefunden wird, kann der Intune Certificate Connector keine Zertifikate ausstellen. <br><br> Beispiel: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **Wichtiger Hinweis:** Der Wert dieses Felds wird nur in codiertem Format (Hexadezimalwert) von der Symantec-Zertifizierungsstelle unterstützt. Daher wird jeder Wert in diesem Feld von Intune Certificate Connector in die Base-64-Codierung konvertiert, bevor er die Zertifikatanforderung übermittelt. **Der Intune Certificate Connector überprüft nicht, ob dieser Wert bereits codiert ist.** | Keine |

## <a name="troubleshooting"></a>Problembehandlung

Protokolle des Intune Certificate Connector-Diensts stehen auf dem NDES-Connector-Computer unter `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` zur Verfügung. Öffnen Sie die Protokolle im [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe), und suchen Sie nach Ausnahme- oder Fehlermeldungen.

| Problem/Fehlermeldung | Lösungsschritte |
| --- | --- |
| Die Anmeldung bei der Benutzeroberfläche des NDES-Connectors ist über das Administratorkonto für den Intune-Mandanten nicht möglich. | Dies kann vorkommen, wenn der lokale Certificate Connector im Intune-Verwaltungsportal nicht aktiviert ist. Führen Sie die folgenden Schritte aus, um das Problem zu lösen: <br><br> Über die Silver Light-Benutzeroberfläche: <br> 1. Melden Sie sich beim [Intune-Verwaltungsportal](https://admin.manage.microsoft.com) an. <br> 2. Klicken Sie auf ADMIN. <br> 3. Wählen Sie „Mobile Geräteverwaltung“ > „Certificate Connector“. <br> 4. Klicken Sie auf **Lokalen Certificate Connector konfigurieren**. <br> 5. Wählen Sie das Kontrollkästchen **Certificate Connector aktivieren** aus. <br> 6. Klicken Sie auf **OK**. <br><br>oder <br><br> Über die Benutzeroberfläche des Azure-Portals: <br> 1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an. <br> 2. Wechseln Sie zu Microsoft Intune. <br> 3. Wählen Sie **Gerätekonfiguration** > **Zertifizierungsstelle** aus. <br> 4. Klicken Sie auf **Aktivieren**. <br><br> Nachdem Sie die obigen Schritte entweder über die Silver Light-Benutzeroberfläche oder über das Azure-Portal durchgeführt haben, wiederholen Sie die Anmeldung mit demselben Administratorkonto für den Intune-Mandanten auf der Benutzeroberfläche des NDES-Connectors. |
| Das NDES-Connector-Zertifikat wurde nicht gefunden. <br><br> System.ArgumentNullException: Der Wert darf nicht NULL sein. | Der Intune Certificate Connector zeigt diesen Fehler an, wenn sich das Administratorkonto für den Intune-Mandanten noch nie bei der Benutzeroberfläche des NDES-Connectors angemeldet hat. <br><br> Wenn dieser Fehler weiterhin besteht, starten Sie den Intune-Connectordienst neu. <br><br> 1. Öffnen Sie „services.msc“. <br> 2. Wählen Sie **Intune-Connectordienst**. <br> 3. Klicken Sie mit der rechten Maustaste, und wählen Sie **Neu starten** aus.|
| NDES-Connector – IssuePfx – Generische Ausnahme: <br> System.NullReferenceException: Der Objektverweis ist nicht auf eine Objektinstanz festgelegt. | Dieser Fehler ist vorübergehend. Starten Sie den Intune-Connectordienst neu. <br><br> 1. Öffnen Sie „services.msc“. <br> 2. Wählen Sie **Intune-Connectordienst**. <br> 3. Klicken Sie mit der rechten Maustaste, und wählen Sie **Neu starten** aus. |
| Symantec-Anbieter – Fehler beim Abrufen der Symantec-Richtlinie „The operation has timed out“ (Timeout für Vorgang überschritten) | Der Intune Certificate Connector hat bei der Kommunikation mit der Symantec-Zertifizierungsstelle einen Timeoutfehler erhalten. Wenn dieser Fehler weiterhin auftritt, erhöhen Sie den Timeoutwert der Verbindung, und versuchen Sie es noch mal. <br><br> So erhöhen Sie das Verbindungstimeout <br> 1. Wechseln Sie zum Computer mit dem NDES-Connector. <br>2. Öffnen Sie die Datei `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` im Editor. <br> 3. Erhöhen Sie den Zeitlimitwert für den folgenden Parameter: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Starten Sie den Intune-Connectordienst neu. <br><br> Wenn das Problem weiterhin besteht, wenden Sie sich an den Kundendienst von Symantec. |
| Symantec-Anbieter – Fehler beim Abrufen des Clientzertifikats | Der Intune Certificate Connector konnte das Zertifikat zur Ressourcenautorisierung nicht aus dem persönlichen Zertifikatspeicher auf dem lokalen Computer abrufen. Um dieses Problem zu beheben, installieren Sie das Ressourcenautorisierungszertifikat im persönlichen Zertifikatspeicher auf dem lokalen Computer zusammen mit dem zugehörigen privaten Schlüssel. <br><br> **Hinweis:** Das Ressourcenautorisierungszertifikat muss von der Symantec-Zertifizierungsstelle abgerufen werden. Weitere Details hierzu erhalten Sie vom Symantec-Kundendienst. | 
| Symantec-Anbieter – Fehler beim Abrufen der Symantec-Richtlinie „The request was aborted: Could not create SSL/TLS secure channel.“ (Die Anforderung wurde abgebrochen: Es konnte kein sicherer SSL-/TLS-Kanal erstellt werden.) | Dieser Fehler tritt unter folgenden Bedingungen auf: <br><br> 1. Der Intune Certificate Connector-Dienst verfügt nicht über ausreichende Berechtigungen, um das Ressourcenautorisierungszertifikat zusammen mit dem zugehörigen privaten Schlüssel aus dem persönlichen Zertifikatspeicher auf dem lokalen Computer zu lesen. Um dieses Problem zu beheben, überprüfen Sie das ausführende Kontextkonto des Connectordiensts in „services.msc“. Der Connectordienst muss im Kontext NT AUTHORITY\SYSTEM ausgeführt werden. <br><br> 2. Das PKCS-Zertifikatprofil im Intune-Verwaltungsportal wurde möglicherweise mit einem ungültigen Basisdienst-FQDN für die Symantec-Zertifizierungsstelle konfiguriert. Der FQDN lautet in etwa `pki-ws.symauth.com`. Um dieses Problem zu beheben, fragen Sie beim Symantec-Kundendienst nach, ob die URL für Ihr Abonnement richtig ist. <br><br> 3. Der Intune Certificate Connector kann sich über das Ressourcenautorisierungszertifikat nicht bei der Symantec-Zertifizierungsstelle anmelden, weil der zugehörige private Schlüssel nicht abgerufen werden kann. Um dieses Problem zu beheben, installieren Sie das Ressourcenautorisierungszertifikat zusammen mit dem zugehörigen privaten Schlüssel im persönlichen Zertifikatspeicher auf dem lokalen Computer. <br><br> Wenn das Problem weiterhin besteht, wenden Sie sich an den Kundendienst von Symantec. |
| Symantec-Anbieter – Fehler beim Abrufen der Symantec-Richtlinie „A request element is not understood.“ (Ein Anforderungselement wird nicht unterstützt.) | Der Intune Certificate Connector konnte die Symantec-Zertifikatprofilvorlage nicht abrufen, weil die Clientprofil-OID nicht dem Intune-Zertifikatprofil entspricht. In einem anderen Fall kann der Intune Certificate Connector die Zertifikatprofilvorlage nicht finden, die der angegebenen Clientprofil-OID in der Symantec-Zertifizierungsstelle zugeordnet ist. <br><br> Um dieses Problem zu beheben, stellen Sie sicher, dass Sie in der Symantec-Zertifizierungsstelle die richtige Clientprofil-OID aus der Symantec-Zertifikatvorlage abrufen. Aktualisieren Sie anschließend das PKCS-Zertifikatprofil im Intune-Verwaltungsportal. <br><br> Rufen Sie die Clientprofil-OID von der Symantec-Zertifizierungsstelle ab: <br> 1. Melden Sie sich beim Symantec-Verwaltungsportal für Zertifizierungsstellen an. <br> 2. Klicken Sie auf „Manage Certificate Profiles“ (Zertifikatprofile verwalten). <br> 3. Wählen Sie das zu verwendende Zertifikatprofil aus. <br> 4. Kopieren Sie die Zertifikatprofil-OID. Sie sieht etwa folgendermaßen aus: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Aktualisieren Sie das PKCS-Zertifikatprofil mit der richtigen Zertifikatprofil-OID: <br>1. Melden Sie sich beim Intune-Verwaltungsportal an. <br> 2. Wechseln Sie zum PKCS-Zertifikatprofil, und klicken Sie auf **Bearbeiten**. <br> 3. Aktualisieren Sie die Zertifikatprofil-OID im Feld „Name der Zertifikatvorlage“. <br> 4. Speichern Sie das PKCS-Zertifikatprofil. |
| Symantec-Anbieter – Fehler bei der Richtlinienüberprüfung. <br><br> Das Attribut ist nicht in der Liste mit von Symantec unterstützten Zertifikatvorlagenattributen enthalten. | Die Symantec-Zertifizierungsstelle zeigt diese Meldung an, wenn die Symantec-Zertifikatprofilvorlage vom Intune-Zertifikatprofil abweicht. Dieses Problem ist wahrscheinlich aufgrund eines Attributkonflikts in SubjectName oder SubjectAltName aufgetreten. <br><br> Um dieses Problem zu beheben, stellen Sie sicher, dass Sie für SubjectName und SubjectAltName von Intune unterstützte Attribute in der Symantec-Zertifikatprofilvorlage auswählen. Weitere Informationen finden Sie im Abschnitt „Zertifikatparameter“ unter „Von Intune unterstützte Attribute“. |
| Einige Benutzergeräte erhalten keine PKCS-Zertifikate von der Symantec-Zertifizierungsstelle. | Dieses Problem tritt auf, wenn der Benutzer-UPN Sonderzeichen wie z.B. den Unterstrich enthält (Beispiel: `global_admin@intune.onmicrosoft.com`). <br><br> Die Symantec-Zertifizierungsstelle unterstützt keine Sonderzeichen in mail_firstname und mail_lastname. <br><br> Führen Sie die folgenden Schritte aus, um das Problem zu lösen: <br><br> 1.   Melden Sie sich beim Symantec-Verwaltungsportal für Zertifizierungsstellen an. <br> 2. Wechseln Sie zu „Manage Certificate Profiles“ (Zertifikatprofile verwalten). <br> 3.   Klicken Sie auf das für Intune verwendete Zertifikatprofil. <br> 4.  Klicken Sie auf den Link „Customize options“ (Optionen anpassen). <br> 5.   Klicken Sie auf die Schaltfläche „Advanced options“ (Erweiterte Optionen). <br> 6.  Fügen Sie unter „Certificate fields – Subject DN“ (Zertifikatfelder – Antragsteller-DN) das Feld „Common Name (CN)“ (Allgemeiner Name) hinzu, und löschen Sie das vorhandene Feld „Common Name (CN)“. Das Hinzufügen und Löschen muss in einem Vorgang ausgeführt werden. <br> 7.    Klicken Sie auf "Speichern". <br><br> Mit der vorherigen Änderung fordert das Symantec-Zertifikatprofil „CN =<upn>“ anstelle von mail_firstname und mail_lastname an. |
| Der Benutzer hat das bereits bereitgestellte Zertifikat manuell vom Gerät gelöscht. | Intune stellt das gleiche Zertifikat beim nächsten Check-In oder bei der nächsten Durchsetzung von Richtlinien erneut bereit. In diesem Fall erhält der NDES-Connector keine PKCS-Zertifikatanforderung. |

## <a name="next-steps"></a>Nächste Schritte

- Verwenden Sie die Informationen in diesem Artikel zusätzlich zu den Informationen im Artikel [Was sind Microsoft Intune-Geräteprofile?](device-profiles.md), um die Geräte Ihrer Organisation und die darauf befindlichen Zertifikate zu verwalten.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Installieren des Intune Certificate Connectors und Auswählen der PFX-Verteilung"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Konfigurieren des Intune Certificate Connectors"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Erstellen des PKCS-Zertifikatprofils im Azure-Portal"
