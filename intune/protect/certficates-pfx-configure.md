---
title: Verwenden von Zertifikaten mit privaten und öffentlichen Schlüsseln in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie PKCS-Zertifikate (Public Key Cryptography Standards) mit Intune, arbeiten Sie mit Stammzertifikaten und Zertifikatvorlagen, installieren Sie Microsoft Intune Certificate Connector (NDES), und verwenden Sie Gerätekonfigurationsprofile für ein PKCS-Zertifikat.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9142ea3f7728fd24883a311bbf967a7a59dbf457
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207246"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Konfigurieren und Verwenden Ihrer PKCS-Zertifikate mit Intune

Intune unterstützt die Verwendung von (PKCS-)Zertifikaten für private und öffentliche Schlüssel. In diesem Artikel erfahren Sie, wie Sie erforderliche Infrastrukturelemente wie lokale Zertifikatconnectors konfigurieren, ein PKCS-Zertifikat exportieren und dieses anschließend zu einem Intune-Gerätekonfigurationsprofil hinzufügen.

Mit den in Microsoft Intune integrierten Einstellungen lassen sich PKCS-Zertifikate für die Authentifizierung bei und den Zugriff auf Unternehmensressourcen verwenden. Mit Zertifikaten wird der Zugriff auf Unternehmensressourcen (z. B. ein VPN- oder ein WLAN-Netzwerk) authentifiziert und gesichert. Stellen Sie diese Einstellungen in Intune über Gerätekonfigurationsprofile bereit.

Informationen zur Verwendung importierter PKCS-Zertifikate finden Sie unter [Importierte PFX-Zertifikate](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Anforderungen

Wenn Sie PKCS-Zertifikate mit Intune verwenden möchten, müssen Sie über folgende Infrastruktur verfügen:

- **Active Directory-Domäne**:  
  Alle in diesem Abschnitt aufgeführten Server müssen der Active Directory-Domäne angehören.

  Informationen zum Installieren und Konfigurieren von Active Directory Domain Services (AD DS) finden Sie unter [AD DS Design and Planning (AD DS-Entwurf und -Planung)](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Zertifizierungsstelle:**  
   Eine Unternehmenszertifizierungsstelle

  Informationen zum Installieren und Konfigurieren von Active Directory-Zertifikatdiensten finden Sie unter [Active Directory Certificate Services Step-by-Step Guide (Ausführliche Anleitung zu den Active Directory-Zertifikatdiensten)](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > Für Intune müssen AD CS mit einer Unternehmenszertifizierungsstelle, nicht mit einer eigenständigen Zertifizierungsstelle ausgeführt werden.

- **Einen Client**  
  Zum Herstellen einer Verbindung mit der Unternehmenszertifizierungsstelle.

- **Ein Stammzertifikat:**  
  Eine exportierte Kopie Ihres Stammzertifikats aus Ihrer Unternehmenszertifizierungsstelle.

- **Microsoft Intune Certificate Connector** (auch als *NDES-Certificate Connector* bezeichnet):  
  Navigieren Sie im Intune-Portal zu **Gerätekonfiguration** > **Certificate Connectors** > **Hinzufügen**, und führen Sie die *notwendigen Schritte aus, um den Connector für PKCS #12 zu installieren*. Verwenden Sie den Downloadlink im Portal zum Herunterladen des Installationsprogramms für den Certificate Connector (**NDESConnectorSetup.exe**).  

  Intune unterstützt bis zu 100 Instanzen dieses Connectors pro Mandant. Jede Instanz des Connectors muss sich auf einem separaten Windows-Server befinden. Sie können eine Instanz dieses Connectors auf demselben Server wie eine Instanz des PFX-Zertifikatconnectors für Microsoft Intune installieren. Wenn Sie mehrere Connectors verwenden, unterstützt die Connectorinfrastruktur Hochverfügbarkeit und Lastenausgleich, da jede verfügbare Connectorinstanz ihre PKCS-Zertifikatanforderungen verarbeiten kann. 

  Dieser Connector verarbeitet PKCS-Zertifikatanforderungen, die für die Authentifizierung oder Signierung von E-Mails mit S/MIME verwendet werden.

  Der Microsoft Intune Certificate Connector unterstützt ebenfalls den FIPS-Modus (Federal Information Processing Standard). FIPS ist nicht erforderlich, Sie können jedoch Zertifikate ausstellen und widerrufen, wenn dieser Modus aktiviert ist.

- **PFX-Zertifikatconnector für Microsoft Intune:**  
  Wenn Sie die E-Mail-Verschlüsselung mit S/MIME einsetzen möchten, laden Sie im Intune-Portal den *PFX-Zertifikatconnector* herunter, der das Importieren von PFX-Zertifikaten unterstützt.  Navigieren Sie zu **Gerätekonfiguration** > **Certificate Connectors** > **Hinzufügen**, und führen Sie die *notwendigen Schritte aus, um den Connector für importierte PFX-Zertifikate zu installieren*. Verwenden Sie den Downloadlink im Portal zum Herunterladen des Installationsprogramms **PfxCertificateConnectorBootstrapper.exe**. 

  Jeder Intune-Mandant unterstützt eine einzelne Instanz dieses Connectors. Sie können diesen Connector auf demselben Server wie eine Instanz des Microsoft Intune Certificate Connectors installieren.

  Der Connector verarbeitet Anforderungen für PFX-Dateien, die in Intune importiert werden, um E-Mails eines bestimmten Benutzers mit S/MIME zu verschlüsseln.  

  Dieser Connector kann sich automatisch selbst installieren, sobald neue Versionen zur Verfügung stehen. Sie müssen Folgendes tun, um die Updatefunktion zu verwenden:
  - Installieren Sie den PFX-Zertifikatconnector für Microsoft Intune auf Ihrem Server.  
  - Wenn Sie automatisch wichtige Updates erhalten möchten, vergewissern Sie sich, dass die Firewalls geöffnet sind, über die der Connector **autoupdate.msappproxy.net** auf Port **443** kontaktieren kann.   

  Weitere Informationen zu den Netzwerkendpunkten, auf die Intune und der Connector zugreifen, finden Sie unter [Netzwerkendpunkte für Microsoft Intune](../fundamentals/intune-endpoints.md).

- **Windows Server:**  
  Verwenden Sie Windows Server, um Folgendes zu hosten:

  - den Microsoft Intune Certificate Connector zur Authentifizierung und Signierung von E-Mails mit S/MIME
  - den PFX-Certificate Connector für Microsoft Intune zur Verschlüsselung von E-Mails mit S/MIME

  Intune unterstützt die Installation des *PFX-Zertifikatconnectors* auf demselben Server, auf dem auch der *Microsoft Intune-Zertifikatconnector* installiert ist.
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportieren des Stammzertifikats aus der Unternehmenszertifizierungsstelle

Jedes Gerät benötigt ein Zertifikat einer Stamm- oder Zwischenzertifizierungsstelle für die Geräteauthentifizierung über VPN, WLAN oder andere Ressourcen. Die folgenden Schritte erläutern, wie das erforderliche Zertifikat von Ihrer Unternehmenszertifizierungsstelle abgerufen wird.

**Verwenden der Befehlszeile:**  
1. Melden Sie sich bei dem Server für Ihre Stammzertifizierungsstelle mit einem Administratorkonto an.
 
2. Navigieren Sie zu **Starten** > **Ausführen**, und geben Sie **Cmd** ein, um die Eingabeaufforderung zu öffnen. 
    
3. Geben Sie **certutil -ca.cert ca_name.cer** an, um das Stammzertifikat als Datei mit dem Namen *ca_name.cer* zu exportieren.



## <a name="configure-certificate-templates-on-the-ca"></a>Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle

1. Melden Sie sich bei Ihrer Unternehmenszertifizierungsstelle mit einem Konto an, das über Administratorrechte verfügt.
2. Öffnen Sie die Konsole **Zertifizierungsstelle**, klicken Sie mit der rechten Maustaste auf **Zertifikatvorlagen**, und klicken Sie dann auf **Verwalten**.
3. Suchen Sie die Zertifikatvorlage **Benutzer**, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Vorlage duplizieren** aus, um **Eigenschaften der neuen Vorlage** zu öffnen.

    > [!NOTE]
    > Zur Signierung und Verschlüsselung von E-Mails mit S/MIME nutzen viele Administratoren für die jeweiligen Schritte unterschiedliche Zertifikate. Wenn Sie Microsoft Active Directory-Zertifikatdienste verwenden, können Sie die Vorlage **Nur Exchange-Signatur** für Zertifikate zum Signieren von E-Mails mit S/MIME verwenden. Die Vorlage **Exchange-Benutzer** können Sie für Zertifikate zur Verschlüsselung mit S/MIME nutzen.  Wenn Sie auf eine Drittanbieter-Zertifizierungsstelle zurückgreifen, sollten Sie sich mit deren Leitfaden zum Einrichten von Signatur- und Verschlüsselungsvorlagen vertraut machen.

4. Gehen Sie auf der Registerkarte **Konformität** wie folgt vor:

    - Legen Sie **Zertifizierungsstelle** auf **Windows Server 2008 R2** fest.
    - Legen Sie **Zertifizierungsstelle** auf **Windows 7/Server 2008 R2** fest.

5. Legen Sie auf der Registerkarte **Allgemein** für **Vorlagenanzeigename** einen für Sie aussagekräftigen Namen fest.

    > [!WARNING]
    > **Vorlagenname** entspricht standardmäßig dem **Vorlagenanzeigenamen***ohne Leerzeichen*. Notieren Sie sich den Namen der Vorlage, da Sie diesen später brauchen werden.

6. Klicken Sie unter **Anforderungsverarbeitung** auf **Exportieren von privatem Schlüssel zulassen**.
7. Bestätigen Sie unter **Kryptografie**, dass die **Minimale Schlüsselgröße** auf 2048 festgelegt ist.
8. Klicken Sie unter **Antragstellername** auf **Supply in the request** (Informationen werden in der Anforderung angegeben).
9. Überprüfen Sie unter **Erweiterungen**, ob „Verschlüsselndes Dateisystem“, „Sichere E-Mail“ und „Clientauthentifizierung“ unter **Anwendungsrichtlinien** angezeigt werden.

    > [!IMPORTANT]
    > Wechseln Sie für iOS-Zertifikatvorlagen auf die Registerkarte **Erweiterungen**, aktualisieren Sie die Option **Schlüsselverwendung**, und stellen Sie sicher, dass die Option **Signatur ist Ursprungsnachweis** nicht aktiviert ist.

10. Fügen Sie unter **Sicherheit** das Computerkonto für den Server hinzu, auf dem Sie den Microsoft Intune Certificate Connector installieren. Weisen Sie diesem Konto die Berechtigungen **Lesen** und **Registrieren** zu.
11. Wählen Sie **Anwenden** > **OK** aus, um die Zertifikatvorlage zu speichern. Schließen Sie die **Zertifikatvorlagenkonsole**.
12. Klicken Sie in der Konsole **Zertifizierungsstelle** mit der rechten Maustaste auf **Zertifikatvorlagen** > **Neu** > **Auszustellende Zertifikatvorlage**. Wählen Sie die Vorlage aus, die Sie in den vorherigen Schritten erstellt haben. Klicken Sie auf **OK**.
13. Gehen Sie folgendermaßen vor, damit der Server Zertifikate für registrierte Geräte und Benutzer verwaltet:

    1. Klicken Sie mit der rechten Maustaste auf die Zertifizierungsstelle, und wählen Sie **Eigenschaften**.
    2. Fügen Sie auf der Registerkarte „Sicherheit“ das Computerkonto des Servers hinzu, auf dem Sie die Connectors (entweder den **Microsoft Intune Certificate Connector** oder den **PFX Certificate Connector für Microsoft Intune**) ausführen. 
    3. Erteilen Sie dem Computerkonto die Zulassungsberechtigungen **Zertifikate ausstellen und verwalten** und **Zertifikate anfordern**.

14. Melden Sie sich von der Unternehmenszertifizierungsstelle ab.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Herunterladen, Installieren und Konfigurieren des Microsoft Intune-Zertifikatconnectors

> [!IMPORTANT]  
> Der Microsoft Intune Certificate Connector kann nicht auf der ausgebenden Zertifizierungsstelle installiert werden. Die Installation muss auf einer separaten Windows Server-Instanz erfolgen.  

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Zertifikatconnectors** >  **+ Hinzufügen** aus.

3. Klicken Sie für den Connector für PKCS #12 auf *Zertifikatconnector-Software herunterladen*, und speichern Sie die Datei an einem Speicherort, auf den Sie über den Server zugreifen, auf dem Sie den Connector installieren werden.

   ![Herunterladen von Microsoft Intune Certificate Connector](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. Melden Sie sich beim Server an, sobald der Download abgeschlossen ist. Führen Sie anschließend Folgendes durch:

    1. Stellen Sie sicher, dass .NET Framework 4.5 oder höher installiert ist (dies ist für den NDES Certificate Connector erforderlich). .NET Framework 4.5 ist automatisch in Windows Server 2012 R2 und höheren Versionen enthalten.
    2. Führen Sie das Installationsprogramm (NDESConnectorSetup.exe) aus, und übernehmen Sie den Standardspeicherort. Dadurch wird der Connector unter `\Program Files\Microsoft Intune\NDESConnectorUI` installiert. Klicken Sie unter den Optionen des Installationsprogramms auf **PFX Distribution** (PFX-Verteilung). Setzen Sie die Installation fort, und schließen Sie sie ab.
    3. Der Connectordienst wird standardmäßig auf dem lokalen Systemkonto ausgeführt. Wenn ein Proxy für den Internetzugriff erforderlich ist, müssen Sie überprüfen, ob das lokale Dienstkonto auf die Proxyeinstellungen auf dem Server zugreifen kann.

5. Der Microsoft Intune Certificate Connector wird auf der Registerkarte **Registrierung** geöffnet. Klicken Sie zum Aktivieren der Verbindung mit Intune auf **Anmelden**, und geben Sie ein Konto mit globalen Administratorberechtigungen an.
6. Es wird empfohlen, auf der Registerkarte **Erweitert** die Option **Konto SYSTEM dieses Computers verwenden (Standard)** aktiviert zu lassen.
7. **Anwenden** > **Schließen**.
8. Wechseln Sie zurück zum Intune-Portal (**Intune** > **Gerätekonfiguration** > **Certificate Connectors**). Nach einigen Momenten wird ein grünes Häkchen angezeigt, und der **Verbindungsstatus** ist **Aktiv**. Ihr Connectorserver kann jetzt mit Intune kommunizieren.
9. Wenn Sie in Ihrer Netzwerkumgebung über einen Webproxy verfügen, müssen Sie möglicherweise zusätzliche Konfigurationen vornehmen, damit der Connector funktioniert. Weitere Informationen finden Sie in der Azure Active Directory-Dokumentation unter [Verwenden von vorhandenen lokalen Proxyservern](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers).
<ul><li>Android Enterprise (*Arbeitsprofil*)</li><li>iOS</li><li>macOS</li><li>Windows 10 und höher > Der Microsoft Intune Certificate Connector unterstützt TLS 1.2. Wenn TLS 1.2 auf dem Server installiert ist, der den Connector hostet, verwendet dieser TLS 1.2. Andernfalls wird TLS 1.1 verwendet. Derzeit wird TLS 1.1 für die Authentifizierung zwischen den Geräten und dem Server verwendet.

## <a name="create-a-trusted-certificate-profile"></a>Erstellen eines vertrauenswürdigen Zertifikatprofils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

   ![Navigieren Sie zu Intune, und erstellen Sie ein neues Profil für ein vertrauenswürdiges Zertifikat.](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Geben Sie die folgenden Eigenschaften ein:

    - **Name** für das Profil
    - Optional eine Beschreibung
    - **Plattform**, auf der das Profil bereitgestellt werden soll
    - Für **Profiltyp** die Option **Vertrauenswürdiges Zertifikat**

4. Wählen Sie **Einstellungen** aus, und geben Sie die zuvor exportierte CER-Datei mit dem Zertifikat der Stammzertifizierungsstelle an.

   > [!NOTE]
   > Je nach der in **Schritt 2** ausgewählten Plattform besitzen Sie möglicherweise die Option zum Auswählen des **Zielspeichers** für das Zertifikat.

   ![Profil erstellen und ein vertrauenswürdiges Zertifikat hochladen](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. Wählen Sie **OK** > **Erstellen** aus, um Ihr Profil zu speichern.

6. Informationen zum Zuweisen des neuen Profils zu einem oder mehreren Geräten finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Erstellen eines PKCS-Zertifikatprofils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

3. Geben Sie die folgenden Eigenschaften ein:

    - **Name** für das Profil
    - Optional eine Beschreibung
    - **Plattform**, auf der das Profil bereitgestellt werden soll
    - Für **Profiltyp** die Option **PKCS-Zertifikat**

4. Wählen Sie **Einstellungen** aus, und konfigurieren Sie die Eigenschaften, die auf die Plattform zutreffen, die Sie ausgewählt haben:
   
   |Einstellung     | Plattform     | Details   |
   |------------|------------|------------|
   |**Verlängerungsschwellenwert (%)**        |<ul><li>Alle         |Empfohlen sind 20 %.  | 
   |**Gültigkeitsdauer des Zertifikats**  |<ul><li>Alle         |Wenn Sie die Zertifikatvorlage nicht geändert haben, kann diese Option auf ein Jahr festgelegt werden. |
   |**Schlüsselspeicheranbieter (KSP)**   |<ul><li>Windows 10  | Wählen Sie für Windows den Schlüsselspeicherort auf dem Gerät aus. |
   |**Zertifizierungsstelle**      |<ul><li>Alle         |Zeigt den internen vollqualifizierten Domänennamen (FQDN) Ihrer Unternehmenszertifizierungsstelle an.  |
   |**Name der Zertifizierungsstelle** |<ul><li>Alle         |Zeigt den Namen der Unternehmenszertifizierungsstelle an (z.B. „Contoso-Zertifizierungsstelle“). |
   |**Zertifikattyp**             |<ul><li>Android Enterprise (*Arbeitsprofil*)</li><li>iOS</li><li>macOS</li><li>Windows 10 und höher|Wählen Sie einen Typ aus: <ul><li> Bei **Benutzerzertifikaten** können sowohl Benutzer- als auch Geräteattribute im Betreff und im alternativen Antragstellernamen des Zertifikats enthalten sein. </il><li>Beim Zertifikattyp **Gerät** können nur Geräteattribute im Betreff und im alternativen Antragstellernamen des Zertifikats enthalten sein. Versenden Sie „Gerät“ für Szenarios mit benutzerlosen Geräten (wie Kioske) oder geteilten Geräten.  <br><br> Diese Auswahl wirkt sich auf das Format des Antragstellernamens aus. |
   |**Format des Antragstellernamens**          |<ul><li>Alle         |Legen Sie für die meisten Plattformen diese Option auf **Allgemeiner Name** fest, falls kein anderes Format erforderlich ist.<br><br>Für die folgenden Plattformen wird das Format des Antragstellernamens durch den Zertifikattyp bestimmt: <ul><li>Android Enterprise (*Arbeitsprofil*)</li><li>iOS</li><li>macOS</li><li>Windows 10 und höher</li></ul>  <p> Siehe [Format des Antragstellers](#subject-name-format) weiter unten in diesem Artikel. |
   |**Alternativer Antragstellername**     |<ul><li>Alle         |Legen Sie diese Option auf **Benutzerprinzipalname (UPN)** fest, sofern nichts anderes erforderlich ist. |
   |**Erweiterte Schlüsselverwendung**           |<ul><li> Android-Geräteadministrator </li><li>Android Enterprise (*Gerätebesitzer*, *Arbeitsprofil*) </li><li>Windows 10 |Zertifikate erfordern in der Regel *Clientauthentifizierung*, damit der Benutzer bzw. das Gerät auf einem Server authentifiziert werden kann. |
   |**Allen Apps Zugriff auf den privaten Schlüssel gewähren** |<ul><li>macOS  |Stellen Sie **Aktiviert** ein, um Apps, die für das zugeordnete Mac-Gerät konfiguriert sind, Zugriff auf den privaten Schlüssel des PKCS-Zertifikats zu gewähren. <br><br> Weitere Informationen zu dieser Einstellung finden Sie unter *AllowAllAppsAccess* im Abschnitt zur Zertifikatnutzlast der [Referenz zum Konfigurationsprofil](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) in der Apple-Entwicklerdokumentation. |
   |**Stammzertifikat**             |<ul><li>Android-Geräteadministrator </li><li>Android Enterprise (*Gerätebesitzer*, *Arbeitsprofil*) |Wählen Sie ein Stammprofil für das ZS-Zertifikat aus, das zuvor zugewiesen wurde. |

5. Wählen Sie **OK** > **Erstellen** aus, um Ihr Profil zu speichern.

6. Informationen zum Zuweisen des neuen Profils zu einem oder mehreren Geräten finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](../configuration/device-profile-assign.md).

   > [!NOTE]
   > Auf Geräten mit einem Android Enterprise-Profil sind Zertifikate, die über ein PKCS-Zertifikatprofil installiert wurden, nicht sichtbar. Um die erfolgreiche Zertifikatbereitstellung zu bestätigen, überprüfen Sie den Status des Profils in der Intune-Konsole.

### <a name="subject-name-format"></a>Format des Antragstellernamens

Wenn Sie ein PKCS-Zertifikatsprofil für die folgenden Plattformen erstellen, sind die Optionen für das Format des Antragstellernamens abhängig vom ausgewählten Zertifikattyp und lauten entweder **Benutzer** oder **Gerät**.  

Plattformen:

- Android Enterprise (*Arbeitsprofil*)
- iOS
- macOS
- Windows 10 und höher

> [!NOTE]
> Es gibt ein bekanntes Problem bei der Verwendung von PKCS zum Abrufen von Zertifikaten, [welches das gleiche Problem ist wie bei SCEP](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters), wenn der Antragstellername in der resultierenden Zertifikatsignieranforderung (Certificate Signing Request, CSR) eines der folgenden Zeichen als Escapezeichen enthält (mit vorangestelltem Schrägstrich\\):
> - \+
> - ;
> - ,
> - =

- **Benutzerzertifikattyp**  
  Formatoptionen für das *Format des Antragstellernamens* enthalten zwei Variablen: **Common Name (CN)** (Allgemeiner Name) und **Email (E)** (E-Mail-Adresse). **Allgemeiner Name (CN)** kann auf eine der folgenden Variablen festgelegt werden:

  - **CN={{UserName}}** : Der Benutzerprinzipalname des Benutzers (z. B. janedoe@contoso.com)
  - **CN={{AAD_Device_ID}}** : Eine ID, die zugewiesen wird, wenn Sie ein Gerät in Azure Active Directory (AD) registrieren. Diese ID wird in der Regel für die Authentifizierung bei Azure Active Directory verwendet.
  - **CN={{SERIALNUMBER}}** : Die eindeutige Seriennummer (SN), die in der Regel vom Hersteller zum Identifizieren eines Geräts verwendet wird.
  - **CN={{IMEINumber}}** : Die eindeutige IMEI-Nummer (International Mobile Equipment Identity), die verwendet wird, um ein Mobiltelefon zu identifizieren.
  - **CN={{OnPrem_Distinguished_Name}}** : Eine Sequenz von durch Kommas getrennte relative definierte Namen wie *CN=Jane Doe, OU=UserAccounts, DC=corp, DC=contoso, DC=com*.

    Stellen Sie sicher, dass Sie das Benutzerattribut *onpremisesdistinguishedname* mithilfe von [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Azure AD synchronisieren, um die Variable *{{OnPrem_Distinguished_Name}}* zu verwenden.

  - **CN={{onPremisesSamAccountName}}** : Administratoren können das Attribut „samAccountName“ aus Active Directory mithilfe von Azure AD Connect in einem Attribut mit dem Namen *onPremisesSamAccountName* mit Azure AD synchronisieren. Intune kann diese Variable als Teil einer Zertifikatsausstellungsanforderung im Antragsteller eines Zertifikats ersetzen. Das Attribut „samAccountName“ ist der zur Unterstützung von Clients und Servern aus einer früheren Version von Windows (vor Windows 2000) verwendete Benutzeranmeldename. Das Format des Benutzeranmeldenamens lautet wie folgt: *DomainName\testUser*oder nur *testUser*.

    Stellen Sie sicher, dass Sie das Benutzerattribut *onPremisesSamAccountName* mithilfe von [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Azure AD synchronisieren, um die Variable *{{onPremisesSamAccountName}}* zu verwenden.

  Durch eine Kombination einer oder vieler dieser Variablen mit statischen Zeichenfolgen können Sie ein benutzerdefiniertes Format wie dieses für den Antragstellernamen erstellen:  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  Dieses Beispiel enthält das Format des Antragstellernamens, das die Variablen „CN“ und „E“ und Zeichenfolgen für die Werte „Organisationseinheit“, „Organisation“, „Standort“, „Bundesland/Kanton“ und „Land/Region“ verwendet. Die Funktion [CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) beschreibt diese Funktion und die unterstützten Zeichenfolgen.

- **Gerätzertifikattyp**  
  Formatoptionen für das Format des Antragstellernamens umfassen die folgenden Variablen: 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** *(Gilt nur für Windows-Geräte und in Domänen eingebundene Geräte)*
  - **{{MEID}}**

  Sie können diese Variablen, gefolgt vom Text für die Variablen, im Textfeld angeben. Beispielsweise kann der allgemeine Name für ein Gerät namens *Device1* als **CN={{DeviceName}}Device1** hinzugefügt werden.

  > [!IMPORTANT]  
  > - Schließen Sie den Variablennamen beim Angeben einer Variable wie im Beispiel veranschaulicht in geschweifte Klammern („{ }“) ein, um einen Fehler zu vermeiden.  
  > - Geräteeigenschaften, die im *Betreff* oder *alternativen Antragstellernamen* eines Gerätezertifikats wie **IMEI**, **SerialNumber** oder **FullyQualifiedDomainName** verwendet werden, sind Eigenschaften, die von einer Person mit Zugriff auf das Gerät gespooft sein könnten.
  > - Ein Gerät muss alle in einem Zertifikatprofil für dieses Profil angegebenen Variablen unterstützen, um auf diesem Gerät installiert werden zu können.  Wenn **{{IMEI}}** beispielsweise im Antragstellernamen eines SCEP-Profils verwendet wird und einem Gerät ohne IMEI-Nummer zugewiesen ist, tritt bei der Profilinstallation ein Fehler auf.  
 


## <a name="whats-new-for-connectors"></a>Neuerungen für Connectors

Es werden regelmäßig Updates für die beiden Certificate Connectors veröffentlicht. Sobald wir ein Update für einen Connector veröffentlichen, werden Sie hier darüber informiert.

Der *PFX-Certificate Connector für Microsoft Intune* [unterstützt automatische Updates](#requirements). Der *Intune Certificate Connector* wird hingegen manuell aktualisiert.

### <a name="may-17-2019"></a>17. Mai 2019

- **PFX-Zertifikatconnector für Microsoft Intune – Version 6.1905.0.404**  
  Änderungen in diesem Release:  
  - Ein Problem wurde behoben, bei dem vorhandene PFX-Zertifikate weiter erneut verarbeitet werden, was bewirkt, dass der Connector die Verarbeitung neuer Anforderungen beendet. 

### <a name="may-6-2019"></a>6\. Mai 2019

- **PFX-Zertifikatconnector für Microsoft Intune – Version 6.1905.0.402**  
  Änderungen in diesem Release:  
  - Das Abrufintervall für den Connector wird von 5 Minuten auf 30 Sekunden verkürzt.
 
### <a name="april-2-2019"></a>2\. April 2019

- **Intune-Zertifikatconnector – Version 6.1904.1.0**  
  Änderungen in diesem Release:  
  - Es wurde ein Problem behoben, bei dem die Möglichkeit bestand, dass sich der Connector nach der Anmeldung mit dem globalen Administratorkonto nicht bei Intune registrieren konnte.  
  - Umfasst Fehlerbehebungen in Bezug auf die Zuverlässigkeit bei Zertifikatsperrungen  
  - Umfasst Fehlerbehebungen in Bezug auf die Leistung, um die Verarbeitung von Anforderungen von PKCS-Zertifikaten zu beschleunigen  

- **PFX-Zertifikatconnector für Microsoft Intune – Version 6.1904.0.401**
  > [!NOTE]  
  > Ein automatisches Update für diese Version des PFX-Connectors ist erst ab dem 11. April 2019 verfügbar.  

  Änderungen in diesem Release:  
  - Es wurde ein Problem behoben, bei dem die Möglichkeit bestand, dass sich der Connector nach der Anmeldung mit dem globalen Administratorkonto nicht bei Intune registrieren konnte.  


## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../configuration/device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](../configuration/device-profile-monitor.md).

Lesen Sie auch die Artikel [Konfigurieren der Infrastruktur zur Unterstützung von SCEP in Intune](certificates-scep-configure.md) oder [Einrichten des Intune Certificate Connectors für den Symantec PKI-Manager-Webdienst](certificates-digicert-configure.md).
