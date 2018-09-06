---
title: 'Verwenden von PKCS-Zertifikaten mit Microsoft Intune: Azure | Micrososft-Dokumentation'
description: Hinzufügen oder Erstellen von Zertifikaten für Public Key Cryptography Standards (PKCS) mit Microsoft Intune, einschließlich der Schritte zum Exportieren eines Stammzertifikats, Konfigurieren einer Zertifikatvorlage, Herunterladen und Installieren eines Microsoft Intune Certificate Connector (NDES), Erstellen eines Gerätekonfigurationsprofils, Erstellen eines PKCS-Zertifikatprofils in Azure und Ihrer Zertifizierungsstelle
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a86b53e34cc4fa24ec683657a646f8545396166e
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910835"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Konfigurieren und Verwenden Ihrer PKCS-Zertifikate mit Intune

> [!IMPORTANT]
> Wir nehmen zurzeit einige Verbesserungen an dem in diesem Artikel beschriebenen S/MIME-Feature vor. Deshalb wurde das S/MIME-Feature in Intune vorübergehend entfernt. Nach der Veröffentlichung des Features werden wir diesen Hinweis entfernen.

Mit Zertifikaten wird der Zugriff auf Unternehmensressourcen (z.B. ein VPN- oder ein WLAN-Netzwerk) authentifiziert und gesichert. In diesem Artikel wird erläutert, wie Sie ein PKCS-Zertifikat exportieren und anschließend dieses Zertifikat zu einem Intune-Profil hinzufügen.

## <a name="requirements"></a>Anforderungen

Zur Verwendung von PKCS-Zertifikaten mit Intune müssen Sie über folgende Infrastruktur verfügen:

- **Eine Active Directory-Domäne**: Alle in diesem Abschnitt aufgeführten Server müssen der Active Directory-Domäne angehören.

  Informationen zum Installieren und Konfigurieren von Active Directory Domain Services finden Sie unter [AD DS Design and Planning (AD DS-Entwurf und -Planung)](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Eine Zertifizierungsstelle (Certification Authority, CA):** Eine Unternehmenszertifizierungsstelle.

  Weitere Informationen zum Installieren und Konfigurieren von Active Directory-Zertifikatdiensten finden Sie unter [Active Directory Certificate Services Step-by-Step Guide (Ausführliche Anleitung zu den Active Directory-Zertifikatdiensten)](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Für Intune müssen AD CS mit einer Unternehmenszertifizierungsstelle, nicht mit einer eigenständigen Zertifizierungsstelle ausgeführt werden.

- **Einen Client** zum Herstellen einer Verbindung mit der Unternehmenszertifizierungsstelle.

- **Ein Stammzertifikat:** Eine exportierte Kopie Ihres Stammzertifikats aus Ihrer Unternehmenszertifizierungsstelle.

- **Microsoft Intune Certificate Connector:** Verwenden Sie das Azure-Portal zum Herunterladen des Installationsprogramms für den **Certificate Connector** (**NDESConnectorSetup.exe**). 

  Der Connector verarbeitet PKCS-Zertifikatanforderungen, die für die Authentifizierung oder Signierung von E-Mails mit S/MIME verwendet werden.

  Der NDES-Certificate Connector unterstützt ebenfalls den FIPS-Modus (Federal Information Processing Standard). FIPS ist nicht erforderlich, Sie können jedoch Zertifikate ausstellen und widerrufen, wenn dieser Modus aktiviert ist.

- **PFX Certificate Connector für Microsoft Intune**: Wenn Sie zur Verschlüsselung von E-Mails S/MIME verwenden möchten, ist es erforderlich, dass Sie im Azure-Portal den Installer für den **PFX Certificate Connector für Microsoft Intune** ( **PfxCertificateConnectorBootstrapper.exe**) herunterladen. Der Connector verarbeitet Anforderungen für PFX-Dateien, die in Intune importiert werden, um E-Mails eines bestimmten Benutzers mit S/MIME zu verschlüsseln.

- **Windows Server** hostet folgende Connectors:

  - den Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) zur Authentifizierung und Signierung von E-Mails mit S/MIME
  - den PFX Certificate Connector für Microsoft Intune (PfxCertificateConnectorBootstrapper.exe) zur Verschlüsselung von E-Mails mit S/MIME

  Sie können beide Connectors (den **Microsoft Intune Certificate Connector** und den **PFX Certificate Connector für Microsoft Intune**) auf demselben Server ausführen.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportieren des Stammzertifikats aus der Unternehmenszertifizierungsstelle

Sie benötigen auf jedem Gerät ein Zertifikat einer Stamm- oder Zwischenzertifizierungsstelle für die Authentifizierung über VPN, WLAN oder andere Ressourcen. Die folgenden Schritte erläutern, wie das erforderliche Zertifikat von Ihrer Unternehmenszertifizierungsstelle abgerufen wird.

1. Melden Sie sich bei Ihrer Unternehmenszertifizierungsstelle mit einem Konto an, das über Administratorrechte verfügt.
2. Öffnen Sie eine Eingabeaufforderung als Administrator.
3. Exportieren Sie das Zertifikat der Stammzertifizierungsstelle (.cer) an einen Speicherort, an dem Sie später darauf zugreifen können.
4. Nach Abschluss des Assistenten, jedoch vor dem Schließen des Assistenten, klicken Sie auf **Zertifikatconnector-Benutzeroberfläche starten**.

   `certutil -ca.cert certnew.cer`

   Weitere Informationen finden Sie unter [Certutil-Tasks zum Verwalten von Zertifikaten](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle

1. Melden Sie sich bei Ihrer Unternehmenszertifizierungsstelle mit einem Konto an, das über Administratorrechte verfügt.
2. Öffnen Sie die Konsole **Zertifizierungsstelle**, klicken Sie mit der rechten Maustaste auf **Zertifikatvorlagen**, und klicken Sie dann auf **Verwalten**.
3. Suchen Sie die Zertifikatvorlage **Benutzer**, klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Vorlage duplizieren**. Dann werden die **Eigenschaften der neuen Vorlage** geöffnet.

    > [!NOTE]
    > Zur Signierung und Verschlüsselung von E-Mails mit S/MIME nutzen viele Administratoren für die jeweiligen Schritte unterschiedliche Zertifikate. Wenn Sie Microsoft Active Directory-Zertifikatdienste verwenden, können Sie die Vorlage **Nur Exchange-Signatur** für Zertifikate zum Signieren von E-Mails mit S/MIME verwenden. Die Vorlage **Exchange-Benutzer** können Sie für Zertifikate zur Verschlüsselung mit S/MIME nutzen.  Wenn Sie auf eine Drittanbieter-Zertifizierungsstelle zurückgreifen, sollten Sie sich mit deren Leitfaden zum Einrichten von Signatur- und Verschlüsselungsvorlagen vertraut machen.

4. Gehen Sie auf der Registerkarte **Konformität** wie folgt vor:

  - Legen Sie **Zertifizierungsstelle** auf **Windows Server 2008 R2** fest.
  - Legen Sie **Zertifizierungsstelle** auf **Windows 7/Server 2008 R2** fest.

5. Legen Sie auf der Registerkarte **Allgemein** für **Vorlagenanzeigename** einen für Sie aussagekräftigen Namen fest.

    > [!WARNING]
    > **Vorlagenname** entspricht standardmäßig dem **Vorlagenanzeigenamen** *ohne Leerzeichen*. Notieren Sie sich den Namen der Vorlage, da Sie diesen später brauchen werden.

6. Klicken Sie unter **Anforderungsverarbeitung** auf **Exportieren von privatem Schlüssel zulassen**.
7. Bestätigen Sie unter **Kryptografie**, dass die **Minimale Schlüsselgröße** auf 2048 festgelegt ist.
8. Klicken Sie unter **Antragstellername** auf **Supply in the request** (Informationen werden in der Anforderung angegeben).
9. Überprüfen Sie unter **Erweiterungen**, ob „Verschlüsselndes Dateisystem“, „Sichere E-Mail“ und „Clientauthentifizierung“ unter **Anwendungsrichtlinien** angezeigt werden.

    > [!IMPORTANT]
    > Wechseln Sie für iOS-Zertifikatvorlagen auf die Registerkarte **Erweiterungen**, aktualisieren Sie die Option **Schlüsselverwendung**, und stellen Sie sicher, dass die Option **Signatur ist Ursprungsnachweis** nicht aktiviert ist.

10. Fügen Sie unter **Sicherheit** das Computerkonto für den Server hinzu, auf dem Sie den Microsoft Intune Certificate Connector installieren. Weisen Sie diesem Konto die Berechtigungen **Lesen** und **Registrieren** zu.
11. Klicken Sie zuerst auf **Anwenden** und dann auf **OK**, um die Zertifikatvorlage zu speichern.
12. Schließen Sie die **Zertifikatvorlagenkonsole**.
13. Klicken Sie in der Konsole der **Zertifizierungsstelle** mit der rechten Maustaste auf **Zertifikatvorlagen**, und klicken Sie dann auf **Neu** und auf **Auszustellende Zertifikatvorlage**. Klicken Sie auf die Vorlage, die Sie in den vorherigen Schritten erstellt haben, und klicken Sie anschließend auf **OK**.
14. Gehen Sie folgendermaßen vor, damit der Server Zertifikate im Namen von bei Intune registrierten Geräten und Benutzern verwaltet:

    1. Klicken Sie mit der rechten Maustaste auf die Zertifizierungsstelle, und wählen Sie **Eigenschaften**.
    2. Fügen Sie auf der Registerkarte „Sicherheit“ das Computerkonto des Servers hinzu, auf dem Sie die Connectors (entweder den **Microsoft Intune Certificate Connector** oder den **PFX Certificate Connector für Microsoft Intune**) ausführen. Erteilen Sie dem Computerkonto die Zulassungsberechtigungen **Zertifikate ausstellen und verwalten** und **Zertifikate anfordern**.

15. Melden Sie sich von der Unternehmenszertifizierungsstelle ab.

## <a name="download-install-and-configure-the-certificate-connectors"></a>Herunterladen, Installieren und Konfigurieren der Zertifikatconnectors

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune-Zertifikatconnector

![ConnectorDownload][ConnectorDownload]

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** und dann auf **Zertifizierungsstelle**.
4. Klicken Sie auf **Hinzufügen**, und laden Sie anschließend den Microsoft Intune Certificate Connector herunter. Speichern Sie den Download an einem Speicherort, auf den Sie auf dem Server zugreifen können, auf dem der Connector installiert wird.
5. Melden Sie sich beim Server an, sobald der Download abgeschlossen ist. Führen Sie anschließend Folgendes durch:

    1. Stellen Sie sicher, dass .NET Framework 4.5 oder höher installiert ist (dies ist für den NDES Certificate Connector erforderlich). .NET Framework 4.5 ist automatisch in Windows Server 2012 R2 und höheren Versionen enthalten.
    2. Führen Sie das Installationsprogramm (NDESConnectorSetup.exe) aus, und übernehmen Sie den Standardspeicherort. Dadurch wird der Connector unter `\Program Files\Microsoft Intune\NDESConnectorUI` installiert. Klicken Sie unter den Optionen des Installationsprogramms auf **PFX Distribution** (PFX-Verteilung). Setzen Sie die Installation fort, und schließen Sie sie ab.
    3. Der Connectordienst wird standardmäßig auf dem lokalen Systemkonto ausgeführt. Wenn ein Proxy für den Internetzugriff erforderlich ist, müssen Sie überprüfen, ob das lokale Dienstkonto auf die Proxyeinstellungen auf dem Server zugreifen kann.

6. Der NDES-Connector öffnet die Registerkarte **Registrierung**. Klicken Sie zum Aktivieren der Verbindung mit Intune auf **Anmelden**, und geben Sie ein Konto mit globalen Administratorberechtigungen an.
7. Es wird empfohlen, auf der Registerkarte **Erweitert** die Option **Use this computer's SYSTEM account (default)** (Konto SYSTEM dieses Computers verwenden (Standard)) aktiviert zu lassen.
8. Klicken Sie zuerst auf **Anwenden** und dann auf **Schließen**.
9. Wechseln Sie zurück zum Azure-Portal (**Intune** > **Gerätekonfiguration** > **Zertifizierungsstelle**). Nach einigen Momenten wird ein grünes Häkchen angezeigt, und der **Verbindungsstatus** ist **Aktiv**. Ihr Connectorserver kann jetzt mit Intune kommunizieren.

> [!NOTE]
> TLS 1.2 wird vom Microsoft Intune Certificate Connector standardmäßig unterstützt. Wenn also der Server, auf dem der Microsoft Intune Certificate Connector installiert ist, TLS 1.2 unterstützt, wird dieses Protokoll verwendet. Wenn der Server TLS 1.2 nicht unterstützt, wird TLS 1.1 verwendet. Derzeit wird TLS 1.1 für die Authentifizierung zwischen den Geräten und dem Server verwendet.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>PFX Certificate Connector für Microsoft Intune

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** und dann auf **Zertifizierungsstelle**.
4. Klicken Sie auf **Hinzufügen**, und laden Sie anschließend den PFX Certificate Connector für Microsoft Intune herunter. Speichern Sie den Download an einem Speicherort, auf den Sie auf dem Server zugreifen können, auf dem der Connector installiert wird.
5. Melden Sie sich beim Server an, sobald der Download abgeschlossen ist. Führen Sie anschließend Folgendes durch:

    1. Stellen Sie sicher, dass .NET Framework 4.6 oder höher installiert ist (dies ist für den PFX Certificate Connector für Microsoft Intune erforderlich). Wenn .NET Framework 4.6 nicht installiert ist, wird es vom Installer automatisch installiert.
    2. Führen Sie den Installer (PfxCertificateConnectorBootstrapper.exe) aus, und übernehmen Sie den Standardspeicherort. Dadurch wird der Connector unter `Program Files\Microsoft Intune\PFXCertificateConnector` installiert.
    3. Der Connectordienst wird auf dem lokalen Systemkonto ausgeführt. Wenn ein Proxy für den Internetzugriff erforderlich ist, müssen Sie überprüfen, ob das lokale Dienstkonto auf die Proxyeinstellungen auf dem Server zugreifen kann.

6. Nach der Installation wird die Registerkarte **Registrierung** vom PFX Certificate Connector für Microsoft Intune geöffnet. Klicken Sie auf **Anmelden**, und geben Sie anschließend ein Konto mit Berechtigungen eines globalen Administrators oder Intune-Administrators an, um die Verbindung mit Intune zu aktivieren.
7. Schließen Sie das Fenster.
8. Wechseln Sie zurück zum Azure-Portal (**Intune** > **Gerätekonfiguration** > **Zertifizierungsstelle**). Nach einigen Momenten wird ein grünes Häkchen angezeigt, und der **Verbindungsstatus** ist **Aktiv**. Ihr Connectorserver kann jetzt mit Intune kommunizieren.

## <a name="create-a-trusted-certificate-profile"></a>Erstellen eines vertrauenswürdigen Zertifikatprofils

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Navigieren Sie zu **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen**.

   ![NavigateIntune][NavigateIntune]

3. Geben Sie die folgenden Eigenschaften ein:

    - **Name** für das Profil
    - Optional eine Beschreibung
    - **Plattform**, auf der das Profil bereitgestellt werden soll
    - Für **Profiltyp** die Option **Vertrauenswürdiges Zertifikat**

4. Gehen Sie zu **Einstellungen**, und geben Sie die zuvor exportierte CER-Datei mit dem Zertifikat der Stammzertifizierungsstelle an.

   > [!NOTE]
   > Abhängig von der in **Schritt 3** ausgewählten Plattform besitzen Sie möglicherweise die Option zum Auswählen des **Zielspeichers** für das Zertifikat.

   ![ProfileSettings][ProfileSettings]

5. Klicken Sie auf **OK** und dann auf **Erstellen**, um Ihr Profil zu speichern.
6. Informationen zum Zuweisen des neuen Profils zu einem oder mehreren Geräten finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Erstellen eines PKCS-Zertifikatprofils

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Navigieren Sie zu **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name** für das Profil
    - Optional eine Beschreibung
    - **Plattform**, auf der das Profil bereitgestellt werden soll
    - Für **Profiltyp** die Option **PKCS-Zertifikat**

4. Gehen Sie zu **Einstellungen**, und geben Sie die folgenden Eigenschaften ein:

    - **Erneuerungsschwellenwert (%)**: Empfohlen wird ein Wert von 20 %.
    - **Gültigkeitsdauer des Zertifikats**: Wenn Sie die Zertifikatvorlage nicht geändert haben, kann diese Option auf ein Jahr festgelegt werden.
    - **Schlüsselspeicheranbieter (KSP)**: Wählen Sie für Windows den Schlüsselspeicherort auf dem Gerät aus.
    - **Zertifizierungsstelle**: Zeigt den internen vollqualifizierten Domänennamen (FQDN) Ihrer Unternehmenszertifizierungsstelle an.
    - **Name der Zertifizierungsstelle**: Zeigt den Namen der Unternehmenszertifizierungsstelle an (z.B. „Contoso-Zertifizierungsstelle“).
    - **Name der Zertifikatvorlage**: Der Name der zuvor erstellten Vorlage. Beachten Sie, dass der **Vorlagenname** standardmäßig dem **Vorlagenanzeigenamen** *ohne Leerzeichen* entspricht.
    - **Format des Antragstellernamens**: Legen Sie diese Option auf **Allgemeiner Name** fest, falls kein anderes Format erforderlich ist.
    - **Alternativer Antragstellername**: Legen Sie diese Option auf **Benutzerprinzipalname (UPN)** fest, sofern nichts anderes erforderlich ist.

5. Klicken Sie zuerst auf **OK** und dann auf **Erstellen**, um Ihr Profil zu speichern.
6. Informationen zum Zuweisen des neuen Profils zu einem oder mehreren Geräten finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Erstellen eines Profils für ein importiertes PKCS-Zertifikat

Sie können Zertifikate, die von einer beliebigen Zertifizierungsstelle für einen bestimmten Benutzer ausgestellt wurden, in Intune importieren. Importierte Zertifikate werden auf allen Geräten installiert, die ein Benutzer registriert. Die Verschlüsselung von E-Mails mit S/MIME ist das häufigste Szenario für den Import vorhandener PFX-Zertifikate in Intune. Ein Benutzer kann zum Verschlüsseln von E-Mails mehrere Zertifikate verwenden. Die privaten Schlüssel dieser Zertifikate müssen auf allen Geräten des Benutzers vorhanden sein, damit die zuvor verschlüsselten E-Mails entschlüsselt werden können.

Zum Importieren von Zertifikaten in Intune können Sie die [auf GitHub bereitgestellten PowerShell-Cmdlets](https://github.com/Microsoft/Intune-Resource-Access) verwenden.

Nach dem Importieren der Zertifikate in Intune erstellen Sie ein Profil für ein **importiertes PKCS-Zertifikat** und weisen es Azure Active Directory-Gruppen zu:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Navigieren Sie zu **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name** für das Profil
    - Optional eine Beschreibung
    - **Plattform**, auf der das Profil bereitgestellt werden soll
    - Für **Profiltyp** die Option **Importiertes PKCS-Zertifikat**

4. Gehen Sie zu **Einstellungen**, und geben Sie die folgenden Eigenschaften ein:

    - **Beabsichtigter Zweck**: Der Zweck der Zertifikate, die für dieses Profil importiert werden. Ein Administrator kann Zertifikate mit unterschiedlichen Zwecken (z.B. zur Authentifizierung oder zum Signieren/Verschlüsseln mit S/MIME) importieren. Der Zweck, der im Zertifikatprofil ausgewählt wird, entspricht demjenigen des Zertifikatprofils mit den korrekten importierten Zertifikaten.
    - **Gültigkeitsdauer des Zertifikats**: Wenn Sie die Zertifikatvorlage nicht geändert haben, kann diese Option auf ein Jahr festgelegt werden.
    - **Schlüsselspeicheranbieter (KSP)**: Wählen Sie für Windows den Schlüsselspeicherort auf dem Gerät aus.

5. Klicken Sie zuerst auf **OK** und dann auf **Erstellen**, um Ihr Profil zu speichern.
6. Informationen zum Zuweisen des neuen Profils zu einem oder mehreren Geräten finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).

## <a name="next-steps"></a>Nächste Schritte
[Verwenden Sie SCEP-Zertifikate](certificates-scep-configure.md) oder [stellen Sie PKCS-Zertifikate über einen Symantec-PKI-Verwaltungswebservice aus](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Im Azure-Portal zu Intune navigieren und ein neues Profil für ein vertrauenswürdiges Zertifikat erstellen"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Profil erstellen und ein vertrauenswürdiges Zertifikat hochladen"
[ConnectorDownload]: ./media/certificates-download-connector.png "Certificate Connector aus dem Azure-Portal herunterladen"  
