---
title: Ausstellen von DigiCert-PKCS-Zertifikaten mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Installieren und konfigurieren Sie den Intune Certificate Connector, um PKCS-Zertifikate von der DigiCert-PKI-Plattform für mit Intune verwaltete Geräte auszustellen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801653"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Einrichten des Intune Certificate Connectors für die DigiCert-PKI-Plattform

Verwenden Sie den Intune Certificate Connector, um PKCS-Zertifikate von der DigiCert-PKI-Plattform für mit Intune verwaltete Geräte auszustellen. Sie können den Connector nur mit einer DigiCert-Zertifizierungsstelle oder sowohl mit einer DigiCert- als auch mit einer Microsoft-Zertifizierungsstelle verwenden.

> [!TIP]
> DigiCert hat den Geschäftsbereich Website Security und die damit verbundenen PKI-Lösungen von Symantec übernommen. Weitere Informationen zu dieser Änderung finden Sie im [Artikel des technischen Supports von Symantec](https://support.symantec.com/en_US/article.INFO4722.html).

Wenn Sie den Intune Certificate Connector bereits zum Ausstellen von Zertifikaten einer Microsoft-Zertifizierungsstelle über PKCS oder System Center Endpoint Protection einsetzen, können Sie mit demselben Connector PKCS-Zertifikate einer DigiCert-Zertifizierungsstelle konfigurieren und ausstellen. Nachdem Sie die Konfiguration zur Unterstützung der DigiCert-Zertifizierungsstelle abgeschlossen haben, kann der Intune Certificate Connector die folgenden Zertifikate ausstellen:

* PKCS-Zertifikate einer Microsoft-Zertifizierungsstelle
* PKCS-Zertifikate einer DigiCert-Zertifizierungsstelle
* Endpoint Protection-Zertifikate einer Microsoft-Zertifizierungsstelle

Wenn Sie den Connector nicht installiert haben, ihn aber sowohl für eine Microsoft- als auch für eine DigiCert-Zertifizierungsstelle verwenden möchten, vervollständigen Sie zuerst die Connectorkonfiguration für die Microsoft-Zertifizierungsstelle. Kehren Sie dann zu diesem Artikel zurück, um ihn so zu konfigurieren, dass auch DigiCert unterstützt wird. Weitere Informationen zu Zertifikatprofilen und zum Connector finden Sie unter [Konfigurieren eines Zertifikatprofils für Ihre Geräte in Microsoft Intune](certificates-configure.md).  

Wenn Sie den Connector nur mit der DigiCert-Zertifizierungsstelle einsetzen möchten, können Sie die Anweisungen in diesem Artikel zur Installation und Konfiguration des Connectors befolgen.

## <a name="prerequisites"></a>Voraussetzungen

- **Ein aktives Abonnement bei der DigiCert-Zertifizierungsstelle**: Das Abonnement ist erforderlich, um von der DigiCert-Zertifizierungsstelle eine Registrierungsstelle abzurufen.

## <a name="install-the-digicert-ra-certificate"></a>Installieren des DigiCert-Registrierungsstellenzertifikats

1. Speichern Sie den folgenden Codeausschnitt in einer Datei namens **certreq.ini**, und aktualisieren Sie ihn nach Bedarf (z. B.: *Subject name in CN format* (Name des Antragstellers im CN-Format).

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

2. Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und generieren Sie mit dem folgenden Befehl eine Zertifikatsignieranforderung (Certificate Signing Request, CSR):

   `Certreq.exe -new certreq.ini request.csr`

3. Öffnen Sie die Datei „request.csr“ in Editor, und kopieren Sie den CSR-Inhalt im folgenden Format:

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Melden Sie sich bei der DigiCert-Zertifizierungsstelle an, und navigieren Sie in den Aufgaben zu **Get an RA Cert** (Registrierungsstellenzertifikat abrufen).

   a. Geben Sie in das Textfeld den CSR-Inhalt aus Schritt 3 ein.

   b. Geben Sie einen Anzeigenamen für das Zertifikat ein.

   c. Klicken Sie auf **Weiter**.

   d. Klicken Sie auf den bereitgestellten Link, um das Registrierungsstellenzertifikat auf Ihren lokalen Computer herunterzuladen.

5. Importieren Sie das Registrierungsstellenzertifikat in den Windows-Zertifikatspeicher:

   a. Öffnen Sie eine MMC-Konsole.

   b. Wählen Sie **Datei** > **Snap-Ins hinzufügen bzw. entfernen** > **Zertifikat** > **Hinzufügen** aus.

   c. Wählen Sie **Computerkonto** > **Weiter** aus.

   d. Wählen Sie **Lokaler Computer** > **Fertig stellen** aus.

   e. Klicken Sie im Fenster **Snap-Ins hinzufügen bzw. entfernen** auf **OK**. Erweitern Sie **Zertifikate (lokaler Computer)**  > **Persönlich** > **Zertifikate**.

   f. Klicken Sie mit der rechten Maustaste auf den Knoten **Zertifikat**, und wählen Sie **Alle Aufgaben** > **Importieren** aus.

   g. Wählen Sie den Speicherort des Registrierungsstellenzertifikats aus, das Sie von der DigiCert-Zertifizierungsstelle heruntergeladen haben, und klicken Sie dann auf **Weiter**.

   h. Wählen Sie **Persönlicher Zertifikatspeicher** > **Weiter** aus.

   i. Klicken Sie auf **Fertig stellen**, um das Registrierungsstellenzertifikat und dessen privaten Schlüssel in den Speicher **Lokaler Computer -> Persönlich** zu importieren.

6. Exportieren und importieren Sie das Zertifikat mit dem privaten Schlüssel:

   a. Erweitern Sie **Zertifikate (lokaler Computer)**  > **Persönlich** > **Zertifikate**.

   b. Wählen Sie das Zertifikat aus, das im vorherigen Schritt importiert wurde.

   c. Klicken Sie mit der rechten Maustaste auf das Zertifikat, und wählen Sie **Alle Aufgaben** > **Exportieren** aus.

   d. Klicken Sie auf **Weiter**, und geben Sie dann das Kennwort ein.

   e. Wählen Sie den Speicherort des Exports aus, und klicken Sie auf **Fertig stellen**.

   f. Führen Sie das Verfahren in Schritt 5 durch, um das Zertifikat mit dem privaten Schlüssel in den Speicher **Lokaler Computer -> Persönlich** zu importieren.

   g. Kopieren Sie den Zertifikatfingerabdruck der Registrierungsstelle ohne Leerzeichen. Es folgt ein Beispiel des Fingerabdrucks:

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > Wenn Sie Hilfe beim Abrufen des Registrierungsstellenzertifikats von der DigiCert-Zertifizierungsstelle benötigen, wenden Sie sich an den [Kundensupport von DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="prepare-to-install-intune-certificate-connector"></a>Vorbereiten der Installation des Microsoft Intune Certificate Connectors

> [!TIP]
> Dieser Abschnitt gilt, wenn Sie den Intune Certificate Connector nur mit einer DigiCert-Zertifizierungsstelle verwenden. Wenn Sie den Intune Certificate Connector mit einer Microsoft-Zertifizierungsstelle verwenden und Unterstützung für eine DigiCert-Zertifizierungsstelle hinzufügen möchten, fahren Sie mit [Konfigurieren des Connectors zur Unterstützung von DigiCert](#configure-the-connector-to-support-digicert) fort.

1. Wählen Sie in der folgenden Liste eine der Windows-Betriebssystemversionen aus, und installieren Sie sie auf einem Computer:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Erstellen Sie einen Benutzer mit Administratorrechten, und verwenden Sie ihn zum Durchführen der folgenden Schritte.

3. Suchen Sie nach den neuesten Windows-Updates, und installieren Sie sie, sofern vorhanden. Starten Sie den Computer nach der Installation der Windows-Updates neu.

4. Installieren Sie .NET Framework 3.5:

   a. Öffnen Sie **Systemsteuerung** > **Programme und Features** > **Windows-Features aktivieren oder deaktivieren**.

   b. Wählen Sie **.NET Framework 3.5** aus, und installieren Sie es.

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Installieren des Intune Certificate Connectors für den Einsatz mit DigiCert

> [!TIP]
> Wenn Sie den Intune Certificate Connector mit einer Microsoft-Zertifizierungsstelle verwenden und Unterstützung für eine DigiCert-Zertifizierungsstelle hinzufügen möchten, fahren Sie mit [Konfigurieren des Connectors zur Unterstützung von DigiCert](#configure-the-connector-to-support-digicert) fort.

Laden Sie die neueste Version des Intune Certificate Connectors aus dem Intune-Verwaltungsportal herunter, und befolgen Sie die folgenden Anweisungen.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Zertifikatconnectors** >  **+ Hinzufügen** aus.

3. Klicken Sie für den Connector für PKCS #12 auf *Zertifikatconnector-Software herunterladen*, und speichern Sie die Datei an einem Speicherort, auf den Sie über den Server zugreifen, auf dem Sie den Connector installieren werden.

   ![Herunterladen der Connectorsoftware](./media/certificates-digicert-configure/connector-download.png)

4. Führen Sie auf dem Server, auf dem Sie den Connector installieren möchten, **NDESConnectorSetup.exe** mit erhöhten Rechten aus.

5. Wählen Sie auf der Seite **Installationsoptionen** die Option **PFX-Verteilung** aus.

   ![PFX-Verteilung auswählen](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Wenn Sie den Intune Certificate Connector zum Ausstellen von Zertifikaten einer Microsoft-Zertifizierungsstelle und einer DigiCert-Zertifizierungsstelle verwenden möchten, wählen Sie **SCEP- und PFX-Profilverteilung** aus.

6. Übernehmen Sie die Standardoptionen, um die Einrichtung des Connectors abzuschließen.

## <a name="configure-the-connector-to-support-digicert"></a>Konfigurieren des Connectors zur Unterstützung von DigiCert

Standardmäßig wird der Intune Certificate Connector in **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc** installiert.

1. Öffnen Sie in Editor die Datei **NDESConnector.exe.config** im Ordner **NDESConnectorSvc**.

   a. Ändern Sie den Wert des Schlüssels `RACertThumbprint` in den Wert des Zertifikatfingerabdrucks, den Sie im vorherigen Abschnitt kopiert haben. Beispiel:

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. Speichern und schließen Sie die Datei.

2. Öffnen Sie **services.msc**:

   a. Wählen Sie **Intune-Connectordienst**.

   b. Beenden Sie den Dienst, und starten Sie ihn dann wieder.

   c. Schließen Sie das Fenster des Diensts.

## <a name="set-up-the-intune-administrator-account"></a>Einrichten des Intune-Administratorkontos  

> [!TIP]
> Wenn Sie den Intune Certificate Connector mit einer Microsoft-Zertifizierungsstelle verwenden und Unterstützung für eine DigiCert-Zertifizierungsstelle hinzufügen möchten, fahren Sie mit [Erstellen eines vertrauenswürdigen Zertifikatprofils](#create-a-trusted-certificate-profile) fort.
 
1. Öffnen Sie die Benutzeroberfläche des NDES-Connectors durch Ausführen von **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.

2. Wählen Sie auf der Registerkarte **Registrierung** den Befehl **Anmelden** aus.

3. Geben Sie die Administratoranmeldeinformationen für Ihren Intune-Mandanten an.

4. Klicken Sie auf **Anmelden** und dann auf **OK**, um eine erfolgreiche Registrierung zu bestätigen. Sie können anschließend die Benutzeroberfläche des NDES-Connectors schließen.

   ![Benutzeroberfläche des NDES-Connectors mit der Meldung „Erfolgreich registriert“](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>Erstellen eines vertrauenswürdigen Zertifikatprofils

Die von Ihnen für mit Intune verwaltete Geräte bereitgestellten PKCS-Zertifikate müssen mit einem vertrauenswürdigen Stammzertifikat verkettet werden. Dazu müssen Sie mit dem Stammzertifikat der DigiCert-Zertifizierungsstelle ein vertrauenswürdiges Intune-Zertifikatprofil erstellen.

1. Rufen Sie aus der DigiCert-Zertifizierungsstelle ein vertrauenswürdiges Stammzertifikat ab:

   a. Melden Sie sich beim Verwaltungsportal der DigiCert-Zertifizierungsstelle an.

   b. Klicken Sie unter **Tasks** (Aufgaben) auf **Manage CAs** (Zertifizierungsstellen verwalten).

   c. Wählen Sie in der Liste die entsprechende Zertifizierungsstelle aus.

   d. Klicken Sie auf **Download root certificate** (Stammzertifikat herunterladen), um das vertrauenswürdige Stammzertifikat herunterzuladen.

2. Erstellen Sie im Intune-Portal ein vertrauenswürdiges Zertifikatprofil:

   a. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

   b. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

   c. Geben Sie die folgenden Eigenschaften ein:

      - **Name** für das Profil
      - Optional können Sie eine **Beschreibung** einfügen.
      - **Plattform**, auf der das Profil bereitgestellt werden soll
      - Für **Profiltyp** die Option **Vertrauenswürdiges Zertifikat**

   d. Wählen Sie **Einstellungen**, und navigieren Sie dann zur CER-Datei des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle, die Sie zur Verwendung mit diesem Zertifikatprofil exportiert haben, und klicken Sie dann auf **OK**.

   e. Wählen Sie (nur bei Windows 8.1- und Windows 10-Geräten) den **Zielspeicher** für das vertrauenswürdige Zertifikat aus:
      - **Computerzertifikatspeicher – Stamm**
      - **Computerzertifikatspeicher – Zwischenspeicher**
      - **Benutzerzertifikatspeicher – Zwischenspeicher**

   f. Klicken Sie anschließend auf **OK**, navigieren Sie wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.  

  Das Profil wird in der Liste der Profile im Bereich **Gerätekonfiguration – Profile** mit dem Profiltyp **Vertrauenswürdiges Zertifikat** angezeigt.  Stellen Sie sicher, dass Sie dieses Profil Geräten zuweisen, die Zertifikate erhalten werden. Informationen zur Zuweisung des Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](../configuration/device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>Abrufen der Zertifikatprofil-OID  

Die Zertifikatprofil-OID ist einer Zertifikatprofilvorlage in der DigiCert-Zertifizierungsstelle zugeordnet. Um in Intune ein PKCS-Zertifikatprofil zu erstellen, muss der Name der Zertifikatvorlage in Form einer Zertifikatprofil-OID angegeben werden, die einer Zertifikatvorlage in der DigiCert-Zertifizierungsstelle zugeordnet ist.

1. Melden Sie sich beim Verwaltungsportal der DigiCert-Zertifizierungsstelle an.
2. Klicken Sie auf **Manage Certificate Profiles** (Zertifikatprofile verwalten).
3. Wählen Sie das zu verwendende Zertifikatprofil aus.
4. Kopieren Sie die Zertifikatprofil-OID. Sie sieht etwa folgendermaßen aus:

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> Wenn Sie beim Abruf der Zertifikatsprofile-OID Hilfe benötigen, wenden Sie sich an den [Kundensupport von DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="create-a-pkcs-certificate-profile"></a>Erstellen eines PKCS-Zertifikatprofils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

3. Geben Sie die folgenden Eigenschaften ein:

   - **Name** für das Profil
   - Optional können Sie eine **Beschreibung** einfügen.
   - **Plattform**, auf der das Profil bereitgestellt werden soll
   - Für **Profiltyp** die Option **PKCS-Zertifikat**

4. Konfigurieren Sie im Bereich **PKCS-Zertifikat** Parameter mit den Werten aus der folgenden Tabelle. Diese Werte sind erforderlich, um über den Intune Certificate Connector PKCS-Zertifikate einer DigiCert-Zertifizierungsstelle auszustellen.

   |PKCS-Zertifikatparameter | Wert | Beschreibung |
   | --- | --- | --- |
   | Zertifizierungsstelle | pki-ws.symauth.com | Dieser Wert muss dem vollqualifizierten Domänennamen (FQDN) des Basisdiensts der DigiCert-Zertifizierungsstelle ohne nachgestellte Schrägstriche entsprechen. Wenn Sie nicht sicher sind, ob dies der richtige Basisdienst-FQDN für Ihr DigiCert-Zertifizierungsstellenabonnement ist, wenden Sie sich an den Kundensupport von DigiCert. <br><br>*Nach dem Wechsel von Symantec zu DigiCert bleibt diese URL unverändert*. <br><br> Wenn dieser FQDN falsch ist, stellt der Intune Certificate Connector keine PKCS-Zertifikate der DigiCert-Zertifizierungsstelle aus.| 
   | Name der Zertifizierungsstelle | Symantec | Dieser Wert muss der Zeichenfolge **Symantec** entsprechen. <br><br> Wenn dieser Wert geändert wird, stellt der Intune Certificate Connector keine PKCS-Zertifikate der DigiCert-Zertifizierungsstelle aus.|
   | Name der Zertifikatvorlage | Die Zertifikatprofil-OID der DigiCert-Zertifizierungsstelle. Beispiel: **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Dieser Wert muss eine Zertifikatprofil-OID sein, die im [vorherigen Abschnitt](#get-the-certificate-profile-oid) aus der Zertifikatprofilvorlage der DigiCert-Zertifizierungsstelle abgerufen wurde. <br><br> Wenn der Intune Certificate Connector keine Zertifikatvorlage findet, die dieser Zertifikatprofil-OID in der DigiCert-Zertifizierungsstelle zugeordnet ist, werden keine PKCS-Zertifikate der DigiCert-Zertifizierungsstelle ausgestellt.|

   ![Auswahlmöglichkeiten für Zertifizierungsstelle und Zertifikatvorlage](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > Die PKCS-Zertifikatprofile für Windows-Plattformen müssen keinem vertrauenswürdigen Zertifikatprofil zugeordnet sein. Für Nicht-Windows-Plattformprofile wie z.B. Android ist dies hingegen erforderlich.

5. Vervollständigen Sie die Konfiguration des Profils entsprechend Ihren geschäftlichen Anforderungen, und klicken Sie dann auf **Erstellen**, um das Profil zu speichern.

6. Wählen Sie auf der Seite *Übersicht* des neuen Profils die Option **Zuweisungen** aus, und konfigurieren Sie eine geeignete Gruppe, die dieses Profil erhält. Mindestens ein Benutzer oder ein Gerät muss der zugewiesenen Gruppe angehören.
 
Nach Abschluss der vorherigen Schritte stellt der Intune Certificate Connector in der zugewiesenen Gruppe PKCS-Zertifikate der DigiCert-Zertifizierungsstelle für mit Intune verwaltete Geräte aus. Diese Zertifikate stehen auf dem mit Intune verwalteten Gerät im Speicher **Persönlich** des Zertifikatspeichers **Aktueller Benutzer** zur Verfügung.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>Vom PKCS-Zertifikatprofil unterstützte Attribute

|Attribut | Von Intune unterstützte Formate | Von der DigiCert Cloud-Zertifizierungsstelle unterstützte Formate | result |
| --- | --- | --- | --- |
| Antragstellername |Intune unterstützt den Antragstellernamen nur in den folgenden drei Formaten: <br><br> 1. Allgemeiner Name <br> 2. Allgemeiner Name einschließlich E-Mail-Adresse <br> 3. Allgemeiner Name als E-Mail-Adresse <br><br> Beispiel: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | Die DigiCert-Zertifizierungsstelle unterstützt weitere Attribute.  Wenn Sie weitere Attribute auswählen möchten, müssen diese in der DigiCert-Zertifikatprofilvorlage mit festen Werten definiert werden.| Wir verwenden den allgemeinen Namen oder die E-Mail-Adresse aus der PKCS-Zertifikatanforderung. <br><br> Konflikte bei der Attributauswahl zwischen dem Intune-Zertifikatprofil und der DigiCert-Zertifikatprofilvorlage führen dazu, dass von der DigiCert-Zertifizierungsstelle keine Zertifikate ausgestellt werden.|
| SAN | Intune unterstützt nur die folgenden SAN Feldwerte: <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (codierter Wert) | Die DigiCert Cloud-Zertifizierungsstelle unterstützt diese Parameter ebenfalls. Wenn Sie weitere Attribute auswählen möchten, müssen diese in der DigiCert-Zertifikatprofilvorlage mit festen Werten definiert werden. <br><br> **AltNameTypeEmail**: Wenn dieser Typ im SAN nicht gefunden wird, verwendet der Intune Certificate Connector den Wert von **AltNameTypeUpn**.  Wenn auch **AltNameTypeUpn** nicht im SAN gefunden wird, verwendet der Intune Certificate Connector der Wert des Antragstellernamens, sofern dieser im E-Mail-Adressformat vorliegt.  Wird auch dieser Typ nicht gefunden, kann der Intune Certificate Connector keine Zertifikate ausstellen. <br><br> Beispiel: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: Wenn dieser Typ im SAN nicht gefunden wird, verwendet der Intune Certificate Connector den Wert von **AltNameTypeEmail**. Wenn auch **AltNameTypeEmail** nicht im SAN gefunden wird, verwendet der Intune Certificate Connector der Wert des Antragstellernamens, sofern dieser im E-Mail-Adressformat vorliegt. Wird auch dieser Typ nicht gefunden, kann der Intune Certificate Connector keine Zertifikate ausstellen.  <br><br> Beispiel: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: Wenn dieser Typ nicht im SAN gefunden wird, kann der Intune Certificate Connector keine Zertifikate ausstellen. <br><br> Beispiel: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  Der Wert dieses Felds wird von der DigiCert-Zertifizierungsstelle nur im codierten Format (Hexadezimalwert) unterstützt. Daher wird jeder Wert in diesem Feld vom Intune Certificate Connector in die Base64-Codierung konvertiert, bevor die Zertifikatanforderung übermittelt wird. *Der Intune Certificate Connector überprüft nicht, ob dieser Wert bereits codiert ist.* | Keine |

## <a name="troubleshooting"></a>Problembehandlung

Die Dienstprotokolle von Intune Certificate Connector sind in **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** auf dem Computer mit NDES-Connector verfügbar. Öffnen Sie die Protokolle im [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe), und suchen Sie nach Ausnahme- oder Fehlermeldungen.

| Problem/Fehlermeldung | Lösungsschritte |
| --- | --- |
| Die Anmeldung bei der Benutzeroberfläche des NDES-Connectors ist über das Administratorkonto für den Intune-Mandanten nicht möglich. | Dies kann vorkommen, wenn der lokale Zertifikatconnector nicht im Microsoft Endpoint Manager Admin Center aktiviert ist. So beheben Sie dieses Problem <br><br> 1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an. <br> 2. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Zertifikatconnectors** aus. <br> 3. Suchen Sie den Zertifikatconnector, und stellen Sie sicher, dass er aktiviert ist. <br><br> Nachdem Sie die obigen Schritte durchgeführt haben, wiederholen Sie die Anmeldung mit demselben Administratorkonto für den Intune-Mandanten auf der Benutzeroberfläche des NDES-Connectors. |
| Das NDES-Connector-Zertifikat wurde nicht gefunden. <br><br> System.ArgumentNullException: Der Wert darf nicht NULL sein. | Der Intune Certificate Connector zeigt diesen Fehler an, wenn sich das Administratorkonto für den Intune-Mandanten noch nie bei der Benutzeroberfläche des NDES-Connectors angemeldet hat. <br><br> Wenn dieser Fehler weiterhin besteht, starten Sie den Intune-Connectordienst neu. <br><br> 1. Öffnen Sie **services.msc**. <br> 2. Wählen Sie **Intune-Connectordienst**. <br> 3. Klicken Sie mit der rechten Maustaste, und wählen Sie **Neu starten** aus.|
| NDES-Connector – IssuePfx – Generische Ausnahme: <br> System.NullReferenceException: Objektverweis nicht auf eine Instanz eines Objekts festgelegt. | Dieser Fehler ist vorübergehend. Starten Sie den Intune-Connectordienst neu. <br><br> 1. Öffnen Sie **services.msc**. <br> 2. Wählen Sie **Intune-Connectordienst**. <br> 3. Klicken Sie mit der rechten Maustaste, und wählen Sie **Neu starten** aus. |
| DigiCert-Anbieter: DigiCert-Richtlinie konnte nicht abgerufen werden. <br><br>„Das Zeitlimit für diesen Vorgang wurde überschritten.“ | Beim Intune Certificate Connector ist bei der Kommunikation mit der DigiCert-Zertifizierungsstelle ein Timeoutfehler aufgetreten. Wenn dieser Fehler weiterhin auftritt, erhöhen Sie den Timeoutwert der Verbindung, und versuchen Sie es noch mal. <br><br> So erhöhen Sie das Verbindungstimeout <br> 1. Wechseln Sie zum Computer mit dem NDES-Connector. <br>2. Öffnen Sie in Editor die Datei **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config**. <br> 3. Erhöhen Sie den Timeoutwert des folgenden Parameters: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Starten Sie den Intune Certificate Connector-Dienst neu. <br><br> Wenn das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von DigiCert. |
| DigiCert-Anbieter: Fehler beim Abrufen des Clientzertifikats | Der Intune Certificate Connector konnte das Zertifikat zur Ressourcenautorisierung nicht aus dem Zertifikatspeicher „Lokaler Computer -> Persönlich“ abrufen. Um dieses Problem zu beheben, installieren Sie das Ressourcenautorisierungszertifikat im Zertifikatspeicher „Lokaler Computer -> Persönlich“ zusammen mit dem zugehörigen privaten Schlüssel. <br><br> Das Ressourcenautorisierungszertifikat muss von der DigiCert-Zertifizierungsstelle abgerufen werden. Weitere Details hierzu erhalten Sie vom Kundensupport von DigiCert. | 
| DigiCert-Anbieter: DigiCert-Richtlinie konnte nicht abgerufen werden. <br><br>„Die Anforderung wurde abgebrochen: Es konnte kein geschützter SSL/TLS-Kanal erstellt werden. | Dieser Fehler tritt unter folgenden Bedingungen auf: <br><br> 1. Der Intune Certificate Connector-Dienst verfügt nicht über die Berechtigungen, im Zertifikatspeicher „Lokaler Computer -> Persönlich“ das Ressourcenautorisierungszertifikat zusammen mit dem zugehörigen privaten Schlüssel zu lesen. Um dieses Problem zu beheben, überprüfen Sie in „services.msc“ das Konto des Ausführungskontexts des Connectordiensts. Der Connectordienst muss im Kontext NT AUTHORITY\SYSTEM ausgeführt werden. <br><br> 2. Das PKCS-Zertifikatprofil im Intune-Verwaltungsportal wurde möglicherweise mit einem ungültigen Basisdienst-FQDN für die DigiCert-Zertifizierungsstelle konfiguriert. Der FQDN ähnelt **pki-ws.symauth.com**. Um dieses Problem zu beheben, fragen Sie beim Kundensupport von DigiCert nach, ob die URL für Ihr Abonnement richtig ist. <br><br> 3. Der Intune Certificate Connector kann sich über das Ressourcenautorisierungszertifikat nicht bei der DigiCert-Zertifizierungsstelle authentifizieren, weil der private Schlüssel nicht abgerufen werden kann. Um dieses Problem zu beheben, installieren Sie das Ressourcenautorisierungszertifikat zusammen mit dem zugehörigen privaten Schlüssel im Zertifikatspeicher „Lokaler Computer -> Persönlich“. <br><br> Wenn das Problem weiterhin besteht, wenden Sie sich an den Kundensupport von DigiCert. |
| DigiCert-Anbieter: DigiCert-Richtlinie konnte nicht abgerufen werden. <br><br>„Ein Anforderungselement wird nicht erkannt.“ | Der Intune Certificate Connector konnte die DigiCert-Zertifikatprofilvorlage nicht abrufen, weil die Clientprofil-OID nicht dem Intune-Zertifikatprofil entspricht. In einem anderen Fall kann der Intune Certificate Connector die Zertifikatprofilvorlage nicht finden, die der Clientprofil-OID in der DigiCert-Zertifizierungsstelle zugeordnet ist. <br><br> Um dieses Problem zu beheben, rufen Sie in der DigiCert-Zertifizierungsstelle die richtige Clientprofil-OID aus der DigiCert-Zertifikatvorlage ab. Aktualisieren Sie anschließend das PKCS-Zertifikatprofil im Intune-Verwaltungsportal. <br><br> Abrufen der Zertifikatprofil-OID der DigiCert-Zertifizierungsstelle: <br> 1. Melden Sie sich beim Verwaltungsportal der DigiCert-Zertifizierungsstelle an. <br> 2. Klicken Sie auf **Manage Certificate Profiles** (Zertifikatprofile verwalten). <br> 3. Wählen Sie das zu verwendende Zertifikatprofil aus. <br> 4. Rufen Sie die Zertifikatprofil-OID ab. Sie sieht etwa folgendermaßen aus: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Aktualisieren Sie das PKCS-Zertifikatprofil mit der richtigen Zertifikatprofil-OID: <br>1. Melden Sie sich beim Intune-Verwaltungsportal an. <br> 2. Wechseln Sie zum PKCS-Zertifikatprofil, und klicken Sie auf **Bearbeiten**. <br> 3. Aktualisieren Sie die Zertifikatprofil-OID im Feld mit dem Namen der Zertifikatvorlage. <br> 4. Speichern Sie das PKCS-Zertifikatprofil. |
| DigiCert-Anbieter: Fehler bei der Richtlinienüberprüfung. <br><br> Das Attribut ist nicht in der Liste mit von DigiCert unterstützten Zertifikatvorlagenattributen enthalten. | Die DigiCert-Zertifizierungsstelle zeigt diese Meldung an, wenn die DigiCert-Zertifikatprofilvorlage vom Intune-Zertifikatprofil abweicht. Dieses Problem ist wahrscheinlich aufgrund eines Attributkonflikts in **SubjectName** oder **SubjectAltName** aufgetreten. <br><br> Um dieses Problem zu beheben, wählen Sie für **SubjectName** und **SubjectAltName** von Intune unterstützte Attribute in der DigiCert-Zertifikatprofilvorlage aus. Weitere Informationen finden Sie im Abschnitt **Zertifikatparameter** unter „Von Intune unterstützte Attribute“. |
| Einige Benutzergeräte erhalten keine PKCS-Zertifikate der DigiCert-Zertifizierungsstelle. | Dieses Problem tritt auf, wenn der Benutzer-UPN Sonderzeichen wie z. B. einen Unterstrich enthält (Beispiel: `global_admin@intune.onmicrosoft.com`). <br><br> Die DigiCert-Zertifizierungsstelle unterstützt in **mail_firstname** und **mail_lastname** keine Sonderzeichen. <br><br> Führen Sie die folgenden Schritte aus, um das Problem zu lösen: <br><br> 1. Melden Sie sich beim Verwaltungsportal der DigiCert-Zertifizierungsstelle an. <br> 2. Klicken Sie auf **Manage Certificate Profiles** (Zertifikatprofile verwalten). <br> 3. Wählen Sie das für Intune verwendete Zertifikatprofil aus. <br> 4. Klicken Sie auf den Link **Customize options** (Optionen anpassen). <br> 5. Klicken Sie auf die Schaltfläche **Advanced options** (Erweiterte Optionen). <br> 6. Fügen Sie unter **Certificate fields – Subject DN** (Zertifikatfelder – Antragsteller-DN) das Feld **Common Name (CN)** (Allgemeiner Name) hinzu, und löschen Sie das vorhandene Feld **Common Name (CN)** . Das Hinzufügen und Löschen muss in einem Vorgang erfolgen. <br> 7. Wählen Sie **Speichern** aus. <br><br> Mit der vorherigen Änderung fordert das DigiCert-Zertifikatprofil **„CN =<upn>“** anstelle von **mail_firstname** und **mail_lastname** an. |
| Der Benutzer hat das bereits bereitgestellte Zertifikat manuell vom Gerät gelöscht. | Intune stellt das gleiche Zertifikat beim nächsten Einchecken oder bei der nächsten Durchsetzung von Richtlinien erneut bereit. In diesem Fall erhält der NDES-Connector keine PKCS-Zertifikatanforderung. |

## <a name="next-steps"></a>Nächste Schritte

Nutzen Sie die Informationen in diesem Artikel zusätzlich zu den Informationen im Artikel [Was sind Microsoft Intune-Geräteprofile?](../configuration/device-profiles.md), um die Geräte Ihrer Organisation und die darauf befindlichen Zertifikate zu verwalten.
