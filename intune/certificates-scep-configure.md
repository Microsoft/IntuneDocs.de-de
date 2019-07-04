---
title: 'Verwenden von SCEP-Zertifikaten mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Konfigurieren Sie ihre lokale AD-Domäne, erstellen Sie eine Zertifizierungsstelle, richten Sie den NDES-Server ein und installieren Sie Intune Certificate Connector, um SCEP-Zertifikate in Microsoft Intune zu verwenden. Erstellen Sie dann ein SCEP-Zertifikatprofil, und weisen Sie dieses Gruppen zu. Sie können sich außerdem einen Überblick über die verschiedenen Ereignis-IDs und ihre Beschreibungen sowie über Diagnosecodes für den Intune-Connectordienst verschaffen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/24/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2e8e7e6c244e14e880dddb7ae76ab0c08ef5088a
ms.sourcegitcommit: edf0f4e791138dcf589dec8b633edc6eda55ef8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344084"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Konfigurieren und Verwenden von SCEP-Zertifikaten mit Intune

In diesem Artikel wird erläutert, wie Sie Ihre Infrastruktur konfigurieren und dann SCEP-Zertifikatprofile (Simple Certificate Enrollment Protocol) mit Intune erstellen und zuweisen.

## <a name="configure-on-premises-infrastructure"></a>Konfigurieren der lokalen Infrastruktur

- **Active Directory-Domäne**: Alle in diesem Abschnitt aufgeführten Server (außer dem Webanwendungsproxy-Server) müssen der Active Directory-Domäne angehören.

- **Zertifizierungsstelle**: Hierbei muss es sich um eine Unternehmenszertifizierungsstelle von Microsoft handeln, die auf einer Enterprise-Edition von Windows Server 2008 R2 oder höher ausgeführt wird. Eine eigenständige Zertifizierungsstelle wird nicht unterstützt. Informationen finden Sie unter [Installieren der Zertifizierungsstelle](http://technet.microsoft.com/library/jj125375.aspx).
    Wenn die Zertifizierungsstelle unter Windows Server 2008 R2 ausgeführt wird, müssen Sie [den Hotfix von KB2483564 installieren](http://support.microsoft.com/kb/2483564/).

- **NDES-Server**: Richten Sie auf einem Server mit Windows Server 2012 R2 oder höher die Serverrolle „Registrierungsdienst für Netzwerkgeräte“ (Network Device Enrollment Service, NDES) ein. Intune unterstützt die Verwendung von NDES nicht auf Servern, die auch die Unternehmenszertifizierungsstelle ausführen. Im [Leitfaden für den Registrierungsdienst für Netzwerkgeräte](http://technet.microsoft.com/library/hh831498.aspx) finden Sie Anweisungen zum Konfigurieren von Windows Server 2012 R2 zum Hosten von NDES.
Der NDES-Server muss mit einer Domäne verknüpft sein, die dieselbe Gesamtstruktur aufweist wie die Unternehmenszertifizierungsstelle. Weitere Informationen zum Bereitstellen des NDES-Servers in einer separaten Gesamtstruktur, in einem isolierten Netzwerk oder in einer internen Domäne finden Sie unter [Verwenden eines Richtlinienmoduls mit dem Registrierungsdienst für Netzwerkgeräte](https://technet.microsoft.com/library/dn473016.aspx). Es ist nicht möglich, einen NDES-Server zu verwenden, der bereits mit einer anderen MDM verwendet wird.

- **Microsoft Intune Certificate Connector**: Navigieren Sie im Intune-Portal zu **Gerätekonfiguration** > **Certificate Connectors** > **Hinzufügen**, und führen Sie die *notwendigen Schritte aus, um den Connector für SCEP zu installieren*. Verwenden Sie den Downloadlink im Portal zum Herunterladen des Installationsprogramms für den Certificate Connector (**NDESConnectorSetup.exe**).  Führen Sie diesen Installer über die NDES-Rolle auf dem Server aus.  

Dieser NDES-Certificate Connector unterstützt ebenfalls den FIPS-Modus (Federal Information Processing Standard). FIPS ist nicht erforderlich, Sie können jedoch Zertifikate ausstellen und widerrufen, wenn dieser Modus aktiviert ist.

- **Webanwendungsproxy-Server** (optional): Verwenden Sie einen Server, der Windows Server 2012 R2 oder höher ausführt, als Webanwendungsproxy-Server (WAP). Diese Konfiguration:
  - ermöglicht Geräten das Empfangen von Zertifikaten über eine Internetverbindung,
  - ist eine Sicherheitsempfehlung, wenn Geräte eine Verbindung über das Internet herstellen, um Zertifikate zu empfangen oder zu erneuern.
  
- **Azure AD-Anwendungsproxy** (optional): Der Azure AD-Anwendungsproxy kann anstelle eines dedizierten WAP-Servers (Webanwendungsproxy) verwendet werden, um den NDES-Server im Internet zu veröffentlichen. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen von sicherem Remotezugriff auf lokale Anwendungen](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="additional"></a>Zusätzliche Informationen

- Auf dem Server, der den WAP hostet, [muss ein Update installiert werden](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) , das die Unterstützung für lange URLs aktiviert, die vom Registrierungsdienst für Netzwerkgeräte verwendet werden. Dieses Update ist im [Updaterollup vom Dezember 2014](http://support.microsoft.com/kb/3013769)enthalten oder kann auch einzeln von [KB3011135](http://support.microsoft.com/kb/3011135)heruntergeladen werden.
- Der WAP-Server muss über ein SSL-Zertifikat verfügen, das mit dem Namen übereinstimmt, der für externe Clients veröffentlicht wird. Außerdem muss das SSL-Zertifikat, das auf dem NDES-Server verwendet wird, vertrauenswürdig sein. Diese Zertifikate ermöglichen dem WAP-Server, die SSL-Verbindung von Clients zu beenden und eine neue SSL-Verbindung mit dem NDES-Server herzustellen.

Weitere Informationen finden Sie unter [Planzertifikate](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) und [Arbeiten mit dem Webanwendungsproxy](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>Netzwerkanforderungen

Wenn Sie keinen Reverseproxy wie WAP oder den Azure AD-App-Proxy verwenden, sollten Sie TCP-Datenverkehr auf Port 443 über alle Hosts bzw. IP-Adressen im Internet auf den NDES-Server zulassen.

Genehmigen Sie sämtliche Ports und Protokolle, die zwischen dem NDES-Server und jeglicher unterstützender Infrastruktur benötigt werden. Beispielsweise muss der NDES-Server mit der Authentifizierungsstelle, den DNS-Servern, den Configuration Manager-Servern, den Domänencontrollern und möglichen anderen Diensten in Ihrer Umgebung kommunizieren.

Es wird dringend empfohlen, den NDES-Server über einen Reverseproxy zu veröffentlichen, z.B. über den [Azure AD-Anwendungsproxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), den [Web Access-Proxy](https://technet.microsoft.com/library/dn584107.aspx) oder den Proxy eines Drittanbieters.

### <a name="certificates-and-templates"></a>Zertifikate und Vorlagen  

|Objekt|Details|
|----------|-----------|
|**Zertifikatvorlage**|Konfigurieren Sie diese Vorlage in der ausstellenden Zertifizierungsstelle.|
|**Clientauthentifizierungszertifikat**|Dieses Zertifikat, das von der ausstellenden oder öffentlichen Zertifizierungsstelle angefordert wurde, installieren Sie auf dem NDES-Server.|
|**Serverauthentifizierungszertifikat**|Dieses SSL-Zertifikat, das von der ausstellenden oder öffentlichen Zertifizierungsstelle angefordert wurde, installieren und binden Sie in IIS auf dem NDES-Server. Wenn für das Zertifikat die Schlüsselverwendung für die Client- und Serverauthentifizierung festgelegt ist (**Erweiterte Schlüsselverwendung**), können Sie dasselbe Zertifikat verwenden.|
|**Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle**|Exportieren Sie dieses Zertifikat als **CER**-Datei von der Stammzertifizierungsstelle oder von einem Gerät, das die Stammzertifizierungsstelle als vertrauenswürdig erachtet. Weisen Sie es dann mit dem Zertifikatprofil einer vertrauenswürdigen Zertifizierungsstelle den Benutzern und/oder Geräten zu.<br /> **HINWEIS<br />: Vergewissern Sie sich beim Zuweisen eines SCEP-Zertifikatprofils, dass Sie das *Profil für das vertrauenswürdige Stammzertifikat*, auf das in Ihrem SCEP-Zertifikatprofil verwiesen wird, demselben Benutzer oder derselben Gerätegruppe zuweisen.  Informationen zum Erstellen dieses Profils finden Sie unter [Erstellen eines vertrauenswürdigen Zertifikatprofils](certficates-pfx-configure.md#create-a-trusted-certificate-profile), dokumentiert im Artikel zu PKCS-Zertifikatprofilen.** <br/><br />Sie verwenden für jede Betriebssystemplattform ein einzelnes Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle und ordnen es dem jeweiligen vertrauenswürdigen Stammzertifikatprofil zu, das Sie erstellen. <br /><br />Sie können bei Bedarf zusätzliche vertrauenswürdige Stammzertifizierungsstellenzertifikate verwenden. Sie können dies zum Beispiel vornehmen, um einer Zertifizierungsstelle eine Vertrauensstellung zu gewähren, die die Serverauthentifizierungszertifikate für Ihre WLAN-Zugriffspunkte signiert.|

### <a name="accounts"></a>Konten

|Name|Details|
|--------|-----------|
|**NDES-Dienstkonto**|Geben Sie ein Domänenbenutzerkonto ein, das als NDES-Dienstkonto verwendet werden soll. |

## <a name="configure-your-infrastructure"></a>Konfigurieren der Infrastruktur
Bevor Sie Zertifikatprofile konfigurieren können, müssen Sie die folgenden Schritte ausführen. Für die Ausführung dieser Schritte werden Kenntnisse in Windows Server 2012 R2 und höher sowie in Active Directory-Zertifikatdiensten (Active Directory Certificate Services (ADCS)) vorausgesetzt:

#### <a name="step-1---create-an-ndes-service-account"></a>Schritt 1: Erstellen eines NDES-Dienstkontos

Erstellen Sie ein Domänenbenutzerkonto, das als NDES-Dienstkonto verwendet werden soll. Sie geben dieses Konto an, wenn Sie Vorlagen auf der ausstellenden Zertifizierungsstelle konfigurieren, bevor Sie NDES installieren und konfigurieren. Stellen Sie sicher, dass der Benutzer über die Standardrechte **Lokal anmelden**, **Anmelden als Dienst** und **Anmelden als Batchauftrag** verfügt. In einigen Organisationen werden diese Rechte durch Härtungsrichtlinien deaktiviert.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Schritt 2: Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle
In diesem Schritt führen Sie die folgenden Aktionen aus:

- Konfigurieren einer Zertifikatvorlage für NDES
- Veröffentlichen der Zertifikatvorlage für NDES

##### <a name="configure-the-certification-authority"></a>Konfigurieren der Zertifizierungsstelle

1. Melden Sie sich als Unternehmensadministrator an.

2. Verwenden Sie das Snap-In der Zertifizierungsvorlage auf der Zertifizierungsstelle, um eine neue benutzerdefinierte Vorlage zu erstellen. Kopieren Sie alternativ eine vorhandene Vorlage, und aktualisieren Sie dann die vorhandene Vorlage (z.B. die Vorlage „Benutzer“) zur Verwendung mit NDES.

   >[!NOTE]
   > Die NDES-Zertifikatvorlage muss auf einer v2-Zertifikatvorlage (mit Windows 2003-Kompatibilität) basieren.

   Die Vorlage muss wie folgt konfiguriert sein:

   - Führen Sie unter **Allgemein** die folgenden Schritte durch:
   
       - Vergewissern Sie sich, dass die Eigenschaft **Zertifikat in Active Directory veröffentlichen** **nicht** aktiviert ist.
       - Geben Sie einen aussagekräftigen **Vorlagenanzeigenamen** für die Vorlage ein.

   - Klicken Sie unter **Antragstellername** auf **Informationen werden in der Anforderung angegeben**. (Sicherheit wird durch das Intune-Richtlinienmodul für NDES erzwungen.)

   - Stellen Sie sicher, dass die **Beschreibung der Anwendungsrichtlinien** unter **Erweiterungen** die **Clientauthentifizierung** umfasst.

     > [!IMPORTANT]
     > Bearbeiten Sie für iOS- und macOS-Zertifikatvorlagen auf der Registerkarte **Erweiterungen** die Option **Schlüsselverwendung**, und stellen Sie sicher, dass die Option **Signatur ist Ursprungsnachweis** nicht aktiviert ist.

   - Fügen Sie unter **Sicherheit** das NDES-Dienstkonto hinzu, und weisen Sie ihm Berechtigungen zum **Registrieren** der Vorlage zu. Intune-Administratoren, die SCEP-Profile erstellen, benötigen die Berechtigung **Lesen**, damit sie beim Erstellen von SCEP-Profilen zu der Vorlage navigieren können.

     > [!NOTE]
     > Zum Widerrufen von Zertifikaten benötigt das NDES-Dienstkonto Rechte des Typs *Zertifikate ausstellen und verwalten* für die Zertifizierungsstelle. Um diese Berechtigung zu delegieren, öffnen Sie die Verwaltungskonsole der Zertifizierungsstelle, und klicken Sie mit der rechten Maustaste auf den Namen der Zertifizierungsstelle. Fügen Sie dann auf der Registerkarte „Sicherheit“ das Konto hinzu, oder wählen Sie es aus. Aktivieren Sie dann das Kontrollkästchen **Zertifikate ausstellen und verwalten**.


3. Prüfen Sie auf der Registerkarte **Allgemein** die **Gültigkeitsdauer** der Vorlage. In der Standardeinstellung verwendet Intune den in der Vorlage konfigurierten Wert. Sie können jedoch die Zertifizierungsstelle konfigurieren, um dem Antragsteller zu ermöglichen, einen anderen Wert einzugeben, den Sie dann in der Intune-Verwaltungskonsole festlegen können. Wenn Sie immer den in der Vorlage festgelegten Wert verwenden möchten, überspringen Sie den Rest dieses Schritts.

   > [!IMPORTANT]
   > iOS und macOS verwenden immer den in der Vorlage festgelegten Wert, unabhängig von anderen Konfigurationen, die Sie vornehmen.

Beispiel für die Konfiguration einer Vorlage:

![Vorlage, Registerkarte „Anforderungsverarbeitung“](./media/scep_ndes_request_handling.png)

![Vorlage, Registerkarte „Antragstellername“](./media/scep_ndes_subject_name.jpg)

![Vorlage, Registerkarte „Sicherheit“](./media/scep_ndes_security.jpg)

![Vorlage, Registerkarte „Erweiterungen“](./media/scep_ndes_extensions.jpg)

![Vorlage, Registerkarte „Ausstellungsvoraussetzungen“](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> Fügen Sie unter „Anwendungsrichtlinien“ nur die erforderlichen Anwendungsrichtlinien hinzu. Sprechen Sie die auszuwählenden Optionen mit Ihren Sicherheitsadministratoren ab.

Konfigurieren Sie die Zertifizierungsstelle, um dem Antragsteller zu ermöglichen, die Gültigkeitsdauer einzugeben:

1. Führen Sie in der Zertifizierungsstelle die folgenden Befehle aus:
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. Verwenden Sie auf der ausstellenden Zertifizierungsstelle das Zertifizierungsstellen-Snap-In, um die Zertifikatvorlage zu veröffentlichen.
   Wählen Sie den Knoten **Zertifikatvorlagen**, klicken Sie auf **Aktion** > **Neu** > **Auszustellende Zertifikatvorlage**, und wählen Sie dann die Vorlage aus, die Sie in Schritt 2 erstellt haben.

3. Überprüfen Sie, ob die Vorlage veröffentlicht wurde, indem Sie sie im Ordner **Zertifikatvorlagen** anzeigen.

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Schritt 3: Konfigurieren der Voraussetzungen auf dem NDES-Server
In diesem Schritt führen Sie die folgenden Aktionen aus:

- Hinzufügen von NDES zu einem Windows-Server und Konfigurieren von IIS zur Unterstützung von NDES
- Hinzufügen des NDES-Dienstkontos zur Gruppe „IIS_IUSR“
- Festlegen eines Dienstprinzipalnamens (Service Principal Name, SPN) für das NDES-Dienstkonto

1. Auf dem Server, der NDES hostet, müssen Sie sich als **Unternehmensadministrator** anmelden und dann den [Assistenten zum Hinzufügen von Rollen und Features](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) zum Installieren von NDES verwenden:

   1. Wählen Sie im Assistenten die Option **Active Directory-Zertifikatdienste** , um Zugriff auf die Rollendienste der AD-Zertifikatdienste zu erhalten. Wählen Sie die Option **Registrierungsdienst für Netzwerkgeräte**, deaktivieren Sie die Option **Zertifizierungsstelle**, und schließen Sie den Assistenten dann ab.

      > [!TIP]
      > Klicken Sie im **Installationsfortschritt** nicht auf **Schließen**. Klicken Sie stattdessen auf den Link **Active Directory-Zertifikatdienste auf dem Zielserver konfigurieren**. Der Assistent für die **AD CS-Konfiguration** wird geöffnet, den Sie für den nächsten Schritt verwenden. Nachdem der Assistent für die AD CS-Konfiguration geöffnet wurde, können Sie den Assistenten zum Hinzufügen von Rollen und Features schließen.

   2. Wenn NDES zum Server hinzugefügt wird, installiert der Assistent ebenfalls IIS. Stellen Sie sicher, dass die IIS wie folgt konfiguriert sind:

       - **Webserver** > **Sicherheit** > **Anforderungsfilterung**

       - **Webserver** > **Anwendungsentwicklung** > **ASP.NET 3.5** 

            Bei der Installation von ASP.NET 3.5 wird .NET Framework 3.5 installiert. Installieren Sie bei Installation von .NET Framework 3.5 sowohl das Feature **.NET Framework 3.5** als auch die **HTTP-Aktivierung**.

       - **Webserver** > **Anwendungsentwicklung** > **ASP.NET 4.5** 

            Bei der Installation von ASP.NET 4.5 wird .NET Framework 4.5 installiert. Installieren Sie bei der Installation von .NET Framework 4.5 das Kernfeature **.NET Framework 4.5**, das Feature **ASP.NET 4.5** und das Feature **WCF-Dienste** > **HTTP-Aktivierung**.

       - **Verwaltungstools** > **IIS 6-Verwaltungskompatibilität** > **IIS 6-Metabasiskompatibilität**

       - **Verwaltungstools** > **IIS 6-Verwaltungskompatibilität** > **Kompatibilität mit WMI für IIS 6**

       - Fügen Sie auf dem Server das NDES-Dienstkonto als Mitglied der lokalen Gruppe **IIS_IUSR** hinzu.

2. Führen Sie in einer Eingabeaufforderung mit erhöhten Rechten den folgenden Befehl aus, um den SPN (Service Principal Name, Dienstprinzipalname) des NDES-Dienstkontos festzulegen:

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Wenn der NDES-Server zum Beispiel den Namen **Server01**hat, die Domäne **Contoso.com**ist und das Dienstkonto **NDESService**lautet, verwenden Sie Folgendes:

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Schritt 4: Konfigurieren von NDES für die Verwendung mit Intune
In diesem Schritt führen Sie die folgenden Aktionen aus:

- Konfigurieren von NDES für die Verwendung mit der ausstellenden Zertifizierungsstelle
- Binden des Serverauthentifizierungszertifikats (SSL) in IIS
- Konfigurieren der Anforderungsfilterung in IIS

1. Öffnen Sie den AD CS-Konfigurations-Assistent auf dem NDES-Server, und nehmen Sie dann die folgenden Änderungen vor:

    > [!TIP]
    > Wenn Sie im vorherigen Schritt auf den Link geklickt haben, ist dieser Assistent bereits geöffnet. Andernfalls öffnen Sie den Server-Manager, um auf die Konfiguration nach der Bereitstellung der Active Directory-Zertifikatdienste zuzugreifen.

   - Wählen Sie unter **Rollendienste** die Option **Registrierungsdienst für Netzwerkgeräte** aus.
   - Geben Sie unter **Dienstkonto für NDES** das NDES-Dienstkonto an.
   - Klicken Sie unter **Zertifizierungsstelle für NDES** auf **Auswählen**, und wählen Sie dann die ausstellende Zertifizierungsstelle aus, auf der Sie die Zertifikatvorlage konfiguriert haben.
   - Legen Sie unter **Kryptografie für NDES** die Schlüssellänge entsprechend den Anforderungen Ihres Unternehmens fest.
   - Klicken Sie unter **Bestätigung** auf **Konfigurieren**, um den Assistenten zu beenden.

2. Aktualisieren Sie nach Beendigung des Assistenten den folgenden Registrierungsschlüssel auf dem NDES-Server:

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    Identifizieren Sie zunächst den **Zweck** der Zertifikatvorlage (auffindbar in der Registerkarte **Anforderungsverarbeitung**), um diesen Schlüssel zu aktualisieren. Aktualisieren Sie anschließend den dazugehörigen Registrierungseintrag, indem Sie die vorhandenen Daten durch den Namen der Zertifikatvorlage (nicht durch den Anzeigenamen der Vorlage) ersetzen, den Sie in Schritt 2 angegeben haben. In der folgenden Tabelle ist der Zertifikatvorlagenzweck den Werten in der Registrierung zugeordnet:

    |Zertifikatvorlagenzweck (auf der Registerkarte „Anforderungsverarbeitung“)|Zu bearbeitender Registrierungswert|In der Intune-Verwaltungskonsole für das SCEP-Profil angezeigter Wert|
    |---|---|---|
    |Signatur|SignatureTemplate|Digitale Signatur|
    |Verschlüsselung|EncryptionTemplate|Schlüsselverschlüsselung|
    |Signatur und Verschlüsselung|GeneralPurposeTemplate|Schlüsselverschlüsselung<br/>Digitale Signatur|

    Wenn der Zweck der Zertifizierungsvorlage zum Beispiel **Verschlüsselung**ist, bearbeiten Sie den Wert **EncryptionTemplate** so, dass er dem Namen der Zertifikatvorlage entspricht.

3. Der NDES-Server empfängt sehr lange URLs (Abfragen), weshalb Sie zwei Registrierungseinträge hinzufügen müssen:


   |                        Standort                        |      Wert      | Typ  |      Daten       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (Dezimal) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (Dezimal) |

4. Wählen Sie in IIS-Manager **Default Web Site** > **Request Filtering** > **Edit Feature Setting** (Standardwebsite > Abfragefilterung > Featureeinstellungen bearbeiten) aus. Ändern Sie wie im Folgenden dargestellt die **Maximale URL-Länge** und die **Maximale Länge einer Abfragezeichenfolge** in *65534*:

    ![Maximale Länge für URL und Abfragezeichenfolge in IIS](./media/SCEP_IIS_max_URL.png)

5. Starten Sie den Server neu. Verwenden Sie nicht **iisreset**, da es diese Änderungen nicht abschließt.
6. Navigieren Sie zu `http://*FQDN*/certsrv/mscep/mscep.dll`. Eine NDES-Seite wird angezeigt, die der Folgenden ähnelt:

    ![Testen von NDES](./media/SCEP_NDES_URL.png)

    Wenn Sie die Meldung **503 – Dienst nicht verfügbar** erhalten, überprüfen Sie die Ereignisanzeige. Wahrscheinlich wurde der Anwendungspool beendet, weil eine notwendige Berechtigung für den NDES-Benutzer fehlt. Diese Berechtigungen werden in Schritt 1 beschrieben.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Installieren und Binden von Zertifikaten auf dem NDES-Server

1. Fordern Sie auf dem NDES-Server ein **Serverauthentifizierungszertifikat** von der internen oder einer öffentlichen Zertifizierungsstelle an, und installieren Sie es. Sie binden dieses SSL-Zertifikat anschließend in IIS.

    > [!TIP]
    > Nachdem Sie das SSL-Zertifikat in IIS gebunden haben, installieren Sie ein Clientauthentifizierungszertifikat. Dieses Zertifikat kann von jeder Zertifizierungsstelle ausgestellt werden, die vom NDES-Server als vertrauenswürdig eingestuft wird. Sie können dasselbe Zertifikat verwenden, wenn für dieses die Schlüsselverwendung für die Client- und Serverauthentifizierung festgelegt ist (**Erweiterte Schlüsselverwendung**). In den folgenden Schritten finden Sie Informationen zu diesen Authentifizierungszertifikaten.

   1. Nachdem Sie das Serverauthentifizierungszertifikat erhalten haben, öffnen Sie **IIS-Manager**, und wählen Sie **Standardwebsite** aus. Klicken Sie im Bereich **Aktionen** auf **Bindungen**.

   2. Klicken Sie auf **Hinzufügen**, legen Sie als **Typ** die Option **https**fest, und stellen Sie sicher, dass der Port **443**ist. Für eigenständiges Intune wird nur Port 443 unterstützt.

   3. Geben Sie unter **SSL-Zertifikat** das Serverauthentifizierungszertifikat ein.

      > [!NOTE]
      > Wenn der NDES-Server einen externen und einen internen Namen für einzelne Netzwerkadressen verwendet, muss das Serverauthentifizierungszertifikat Folgendes enthalten:
      > - Einen **Antragstellernamen** mit einem externen öffentlichen Servernamen
      > - Einen **alternativen Antragstellernamen**, der den internen Servernamen enthält

2. Fordern Sie auf dem NDES-Server ein **Clientauthentifizierungszertifikat** von der internen oder einer öffentlichen Zertifizierungsstelle an, und installieren Sie es. Dieses Zertifikat kann dasselbe Zertifikat wie das Serverauthentifizierungszertifikat sein, wenn es über beide Funktionen verfügt.

    Das Clientauthentifizierungszertifikat muss die folgenden Eigenschaften aufweisen:

    - **Erweiterte Schlüsselverwendung:** Dieser Wert muss die **Clientauthentifizierung** enthalten.

    - **Antragstellername**: Der Wert muss mit dem DNS-Namen des Servers identisch sein, auf dem das Zertifikat installiert wird (d.h. dem NDES-Server).

##### <a name="configure-iis-request-filtering"></a>Konfigurieren der IIS-Anforderungsfilterung

1. Öffnen Sie auf dem NDES-Server den **IIS-Manager**, wählen Sie im Bereich **Verbindungen** die Option **Standardwebsite**, und öffnen Sie dann die **Anforderungsfilterung**.

2. Klicken Sie auf **Featureeinstellungen bearbeiten**, und legen Sie dann die folgenden Werte fest:

    - **Abfragezeichenfolge (Bytes)**  = **65534**
    - **Maximale URL-Länge (Bytes)**  = **65534**

3. Überprüfen Sie den folgenden Registrierungsschlüssel:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Stellen Sie sicher, dass die folgenden Werte als DWORD-Einträge festgelegt sind:

    - Name: **MaxFieldLength** mit einem Dezimalwert von **65534**
    - Name: **MaxRequestBytes** mit einem Dezimalwert von **65534**

4. Starten Sie den NDES-Server neu. Der Server ist jetzt bereit zur Unterstützung des Zertifikatconnectors.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Schritt 5: Aktivieren, Installieren und Konfigurieren des Intune Certificate Connectors
In diesem Schritt führen Sie die folgenden Aktionen aus:

- Aktivieren der Unterstützung für NDES in Intune
- Laden Sie den Certificate Connector herunter, und installieren und konfigurieren Sie ihn auf dem Server, der die Rolle „Registrierungsdienst für Netzwerkgeräte“ (Network Device Enrollment Service, NDES) auf einem Server in Ihrer Umgebung hostet. Zum Erhöhen der Skalierbarkeit der NDES-Implementierung ihrer Organisation können Sie mehrere NDES-Server mit einem Microsoft Intune Certificate Connector auf jedem NDES-Server installieren.

##### <a name="download-install-and-configure-the-certificate-connector"></a>Herunterladen, Installieren und Konfigurieren von Certificate Connector

> [!IMPORTANT] 
> Der Microsoft Intune Certificate Connector **muss** auf einem separaten Windows-Server installiert sein. Er kann nicht in der ausstellenden Zertifizierungsstelle installiert werden. Zudem **muss** er auf dem gleichen Server installiert werden, dem die NDES-Rolle (Network Device Enrollment Service) zugewiesen ist.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Certificate Connectors** > **Hinzufügen**.
3. Laden Sie die Datei des Connectors für die SCEP-Datei herunter, und speichern Sie sie. Speichern Sie sie an einem Ort, auf den von dem NDES-Server aus zugegriffen werden kann, auf dem der Connector installiert wird.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)


4. Nachdem der Download abgeschlossen ist, navigieren Sie zu dem NDES-Server, der den Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service, NDES) hostet. Führen Sie anschließend Folgendes durch:

    1. Stellen Sie sicher, dass .NET Framework 4.5 installiert ist (dies ist für den NDES-Certificate Connector erforderlich). .NET Framework 4.5 ist automatisch in Windows Server 2012 R2 und höheren Versionen enthalten.
    2. Verwenden Sie ein Konto mit Administratorrechten für den Server zur Ausführung des Installationsprogramms (**NDESConnectorSetup.exe**). Das Installationsprogramm installiert auch das Richtlinienmodul für NDES und den CRP-Webdienst. Der CRP-Webdienst „CertificateRegistrationSvc“ wird als Anwendung in IIS ausgeführt.

    > [!NOTE]
    > Bei der Installation von NDES für eigenständiges Intune wird der CRP-Dienst automatisch mit dem Zertifikatconnector installiert. Bei Verwendung von Intune mit dem Konfigurations-Manager installieren Sie den Zertifikatregistrierungspunkt als eine separate Standortsystemrolle.

5. Wenn Sie nach dem Clientzertifikat für den Zertifikatconnector gefragt werden, klicken Sie auf **Auswählen**, und wählen Sie das Zertifikat für die **Clientauthentifizierung** aus, das Sie auf Ihrem NDES-Server in Schritt 4 installiert haben.

    Nachdem Sie das Clientauthentifizierungszertifikat ausgewählt haben, wird erneut die Oberfläche **Clientzertifikat für den Microsoft Intune-Zertifikatconnector** angezeigt. Auch wenn das ausgewählte Zertifikat nicht angezeigt wird, klicken Sie auf **Weiter**, um die Eigenschaften des Zertifikats anzuzeigen. Klicken Sie auf **Weiter** und anschließend auf **Installieren**.

    > [!IMPORTANT]
    > Die verstärkte Sicherheitskonfiguration für Internet Explorer [muss auf dem NDES-Server deaktiviert sein](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx), der den Intune Certificate Connector hostet.

6. Klicken Sie nach Abschluss des Assistenten, jedoch vor dem Schließen des Assistenten auf **Zertifikatconnector-Benutzeroberfläche starten**.

    > [!TIP]
    > Wenn Sie den Assistenten schließen, bevor Sie die Benutzeroberfläche des Zertifikatconnectors starten, können Sie sie mit dem folgenden Befehl erneut öffnen:
    >
    > <Installationspfad>\NDESConnectorUI\NDESConnectorUI.exe

7. Gehen Sie auf der Benutzeroberfläche von **Zertifikatconnector** so vor:

    Klicken Sie auf **Anmelden**, und geben Sie die Anmeldeinformationen des Intune-Dienstadministrators oder für einen Mandantenadministrator mit der globalen Administratorberechtigung ein. Nach der Anmeldung lädt der Intune Certificate Connector ein Zertifikat von Intune herunter. Dieses Zertifikat wird zur Authentifizierung zwischen dem Connector und Intune verwendet.

    > [!IMPORTANT]
    > Dem Benutzerkonto muss eine gültige Intune-Lizenz zugewiesen werden. Wenn das Benutzerkonto nicht über eine gültige Intune-Lizenz verfügt, schlägt „NDESConnectorUI.exe“ fehl.

    Wenn Ihre Organisation einen Proxyserver verwendet und der Proxy erforderlich ist, damit der NDES-Server auf das Internet zugreifen kann, klicken Sie auf **Proxyserver verwenden**. Geben Sie dann den Proxyservernamen, den Port und die Kontoanmeldeinformationen für die Verbindung ein.

    Wählen Sie die Registerkarte **Erweitert** aus, und geben Sie anschließend die Anmeldeinformationen für ein Konto ein, das über die Berechtigung **Zertifikate ausstellen und verwalten** für die ausstellende Zertifizierungsstelle verfügt. **Übernehmen** Sie Ihre Änderungen. Wenn Sie diese Berechtigung beim [Konfigurieren Ihrer Zertifizierungsstelle](#configure-the-certification-authority) an Ihr NDES-Dienstkonto delegiert haben, geben Sie dieses Konto hier an. 

    Sie können jetzt die Benutzeroberfläche des Zertifikatconnectors schließen.

8. Öffnen Sie eine Eingabeaufforderung, geben Sie **services.msc** ein, und drücken Sie dann die **EINGABETASTE**. Klicken Sie mit der rechten Maustaste auf **Intune-Connectordienst**, und klicken Sie auf **Neu starten**.

Öffnen Sie zum Überprüfen, ob der Dienst ausgeführt wird, einen Browser, und geben Sie die folgende URL ein. Es sollte ein **403**-Fehler zurückgegeben werden:

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Die Unterstützung für TLS 1.2 ist im NDES-Certificate Connector enthalten. Wenn der Server, auf dem NDES-Certificate Connector installiert ist, TLS 1.2 unterstützt, wird TLS 1.2 verwendet. Wenn der Server TLS 1.2 nicht unterstützt, wird TLS 1.1 verwendet. Derzeit wird TLS 1.1 für die Authentifizierung zwischen den Geräten und dem Server verwendet.

## <a name="create-a-scep-certificate-profile"></a>Erstellen eines SCEP-Zertifikatprofils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie für das SCEP-Zertifikatprofil einen **Namen** und eine **Beschreibung** ein.
4. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform für dieses SCEP-Zertifikat aus. Derzeit können Sie eine der folgenden Plattformen für Einstellungen für Geräteeinschränkungen auswählen:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 und höher**
   - **Windows 10 und höher**
5. Wählen Sie in der Dropdownliste **Profiltyp** die Option **SCEP-Zertifikat** aus.
6. Legen Sie folgende Einstellungen fest:

   - **Zertifikattyp**: Wählen Sie **Benutzer** für Benutzerzertifikate aus. Beim Zertifikattyp **Benutzer** können sowohl Benutzer- als auch Geräteattribute im Betreff und im alternativen Antragstellernamen des Zertifikats enthalten sein.  Klicken Sie für benutzerlose Geräte wie Kiosks oder für Windows-Geräte auf **Gerät**. Dadurch wird das Zertifikat im Zertifikatspeicher des lokalen Computers gespeichert. Beim Zertifikattyp **Gerät** können nur Geräteattribute im Betreff und im alternativen Antragstellernamen des Zertifikats enthalten sein.  Zertifikate für **Geräte** sind für folgende Plattformen verfügbar:  
     - Android Enterprise-Arbeitsprofil
     - iOS
     - macOS
     - Windows 8.1 und höher
     - Windows 10 und höher


   - **Format des Antragstellernamens**: Wählen Sie aus, auf welche Weise Intune den Antragstellernamen in der Zertifikatanforderung automatisch erstellen soll. Diese Optionen ändern sich, wenn Sie den Zertifikattyp **Benutzer** oder **Gerät** auswählen. 

        **Benutzerzertifikattyp**  

        Sie können die E-Mail-Adresse des Benutzers im Antragstellernamen einschließen. Es stehen die folgenden Optionen zur Auswahl:

        - **Nicht konfiguriert**
        - **Allgemeiner Name**
        - **Allgemeiner Name einschließlich E-Mail-Adresse**
        - **Allgemeiner Name als E-Mail-Adresse**
        - **IMEI (International Mobile Equipment Identity)**
        - **Seriennummer**
        - **Benutzerdefiniert**: Bei Auswahl dieser Option wird auch ein **benutzerdefiniertes** Textfeld angezeigt. In dieses Feld können Sie ein benutzerdefiniertes Format für den Antragstellernamen, einschließlich Variablen, eingeben. Das benutzerdefinierte Format unterstützt zwei Variablen: **Common Name (CN)** (Allgemeiner Name) und **Email (E)** (E-Mail-Adresse). **Allgemeiner Name (CN)** kann auf eine der folgenden Variablen festgelegt werden:

            - **CN={{UserName}}** : Der Benutzerprinzipalname des Benutzers, z.B. „janedoe@contoso.com“
            - **CN={{AAD_Device_ID}}** : Eine ID, die zugewiesen wird, wenn Sie ein Gerät in Azure Active Directory (AD) registrieren. Diese ID wird in der Regel für die Authentifizierung bei Azure Active Directory verwendet.
            - **CN={{SERIALNUMBER}}** : Die eindeutige Seriennummer (SN), die in der Regel vom Hersteller zum Identifizieren eines Geräts verwendet wird.
            - **CN={{IMEINumber}}** : Die eindeutige IMEI-Nummer (International Mobile Equipment Identity), die verwendet wird, um ein Mobiltelefon zu identifizieren.
            - **CN={{OnPrem_Distinguished_Name}}** : Eine Sequenz von relativen definierten Namen, die durch Kommas getrennt sind, z.B. `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`.

                Damit Sie die `{{OnPrem_Distinguished_Name}}`-Variable verwenden können, stellen Sie sicher, dass das `onpremisesdistingishedname`-Benutzerattribut mithilfe von [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Ihrem Azure AD synchronisiert wird.

            - **CN={{onPremisesSamAccountName}}** : Administratoren können das samAccountName-Attribut aus Active Directory mithilfe von Azure AD Connect in einem Attribut mit dem Namen `onPremisesSamAccountName` mit Azure AD synchronisieren. Intune kann die Variable als Teil einer Zertifikatsausstellungsanforderung im Antragsteller eines SCEP-Zertifikats ersetzen.  Das Attribut samAccountName ist der zur Unterstützung von Clients und Servern aus einer früheren Version von Windows (vor Windows 2000) verwendete Benutzeranmeldename. Das Format des Benutzeranmeldenamens ist: `DomainName\testUser`, oder nur `testUser`.

                Damit Sie die `{{onPremisesSamAccountName}}`-Variable verwenden können, stellen Sie sicher, dass das `onPremisesSamAccountName`-Benutzerattribut mithilfe von [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Ihrem Azure AD synchronisiert wird.

            Durch eine Kombination einer oder vieler dieser Variablen mit statischen Zeichenfolgen können Sie ein benutzerdefiniertes Format wie dieses für den Antragstellernamen erstellen:  

            **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

            In diesem Beispiel haben Sie ein Format für den Antragstellernamen erstellt, das zusätzlich zu den Variablen CN und E entsprechende Zeichenfolgen für Organisationseinheit (OU), Organisation (O), Ort (L), Bundesland/Kanton (ST) und Land/Region (C) verwendet. Die Funktion [CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) beschreibt diese Funktion und die unterstützten Zeichenfolgen.

        **Gerätzertifikattyp**  

        Bei Verwendung des Zertifikattyps **Gerät** können Sie auch die folgenden Gerätzertifikatvariablen für den Wert verwenden:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Diese Variablen können mit statischem Text in einem benutzerdefinierten Werttextfeld hinzugefügt werden. Beispielsweise kann der allgemeine Name als `CN = {{DeviceName}}text` hinzugefügt werden.

        > [!IMPORTANT]
        >  - In einem statischen Text des Antragstellers verursachen geschweifte Klammern **{}** , die keine Variable einschließen, einen Fehler. 
        >  - Wenn Sie eine Gerätezertifikatvariable verwenden, schließen Sie die Variable in geschweifte Klammern **{ }{ }** ein.
        >  - `{{FullyQualifiedDomainName}}` funktioniert nur für Windows und in die Domäne eingebundene Geräte. 
        >  -  Bei der Verwendung von Geräteeigenschaften wie IMEI, Seriennummer und vollständig qualifiziertem Domänennamen im Betreff oder SAN für ein Gerätezertifikat achten Sie unbedingt darauf, dass diese Eigenschaften von einer Person mit Zugriff auf das Gerät gespooft sein könnten.
        >  - Das Profil wird nicht auf dem Gerät installiert, wenn die angegebenen Gerätevariablen nicht unterstützt werden. Beispiel: Wenn „{{IMEI}}“ im Antragstellernamen des SCEP-Profils, das einem Gerät ohne IMEI-Nummer zugewiesen ist, verwendet wird, tritt bei der Profilinstallation ein Fehler auf. 


   - **Alternativer Antragstellername**: Wählen Sie aus, auf welche Weise Intune die Werte für den alternativen Antragstellernamen (Subject Alternative Name, SAN) in der Zertifikatanforderung automatisch erstellen soll. Diese Optionen ändern sich, wenn Sie den Zertifikattyp **Benutzer** oder **Gerät** auswählen. 

        **Benutzerzertifikattyp**  

        Die folgenden Attribute sind verfügbar:

        - E-Mail-Adresse
        - Benutzerprinzipalname (UPN)

            Wenn Sie beispielsweise einen Benutzerzertifikattyp auswählen, können Sie den Benutzerprinzipalnamen (User Principal Name, UPN) in den alternativen Antragstellernamen aufnehmen. Wenn ein Clientzertifikat für die Authentifizierung bei einem Netzwerkrichtlinienserver verwendet wird, legen Sie den alternativen Antragstellernamen auf den Benutzerprinzipalnamen fest. 

        **Gerätzertifikattyp**  

        Ein Textfeld im Tabellenformat, das Sie anpassen können. Die folgenden Attribute sind verfügbar:

        - DNS

        Mit dem Zertifikattyp **Gerät** können Sie die folgenden Gerätzertifikatvariablen für den Wert verwenden:  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        Diese Variablen können mit statischem Text im benutzerdefinierten Werttextfeld hinzugefügt werden. Beispielsweise kann das DNS-Attribut als `DNS name = {{AzureADDeviceId}}.domain.com` hinzugefügt werden.

        > [!IMPORTANT]
        >  - Im statischen Text des SAN funktionieren geschweifte Klammern **{ }** , Pipesymbole **|** und Semikolons **;** nicht. 
        >  - Wenn Sie eine Gerätezertifikatvariable verwenden, schließen Sie die Variable in geschweifte Klammern **{ }{ }** ein.
        >  - `{{FullyQualifiedDomainName}}` funktioniert nur für Windows und in die Domäne eingebundene Geräte. 
        >  -  Bei der Verwendung von Geräteeigenschaften wie IMEI, Seriennummer und vollständig qualifiziertem Domänennamen im Betreff oder SAN für ein Gerätezertifikat achten Sie unbedingt darauf, dass diese Eigenschaften von einer Person mit Zugriff auf das Gerät gespooft sein könnten.
        >  - Das Profil wird nicht auf dem Gerät installiert, wenn die angegebenen Gerätevariablen nicht unterstützt werden. Beispiel: Wenn „{{IMEI}}“ im alternativer Antragstellernamen des SCEP-Profils, das einem Gerät ohne IMEI-Nummer zugewiesen ist, verwendet wird, tritt bei der Profilinstallation ein Fehler auf.  

   - **Gültigkeitsdauer des Zertifikats**: Wenn Sie den Befehl `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE`, der eine benutzerdefinierte Gültigkeitsdauer ermöglicht, für die ausstellende Zertifizierungsstelle ausgeführt haben, können Sie die verbleibende Dauer vor dem Ablaufen des Zertifikats angeben.<br>Sie können einen niedrigeren Wert als den für die Gültigkeitsdauer in der Zertifikatvorlage eingeben, aber keinen höheren. Wenn die Gültigkeitsdauer des Zertifikats in der Zertifikatvorlage beispielsweise zwei Jahre beträgt, können Sie als Wert „ein Jahr“ eingeben, aber nicht „fünf Jahre“. Zudem muss der Wert niedriger als die verbleibende Gültigkeitsdauer des Zertifikats der ausstellenden Zertifizierungsstelle sein. 
   - **Schlüsselspeicheranbieter (Key Storage Provider, KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): Geben Sie an, wo der Schlüssel für das Zertifikat gespeichert wird. Wählen Sie einen der folgenden Werte aus:
     - **Bei TPM-KSP (Trusted Platform Module) registrieren, falls vorhanden, andernfalls Software-KSP**
     - **Bei TPM-KSP (Trusted Platform Module) registrieren, andernfalls Fehler**
     - **Bei Passport registrieren, andernfalls Fehler (Windows 10 und höher)**
     - **Bei Software-KSP registrieren**

   - **Schlüsselverwendung**: Geben Sie Schlüsselverwendungsoptionen für das Zertifikat an. Folgende Optionen sind verfügbar:
     - **Schlüsselverschlüsselung**: Der Schlüsselaustausch wird nur gestattet, wenn der Schlüssel verschlüsselt ist.
     - **Digitale Signatur**: Der Schlüsselaustausch wird nur gestattet, wenn der Schutz des Schlüssels durch eine digitale Signatur unterstützt wird.
   - **Schlüsselgröße (Bits)** : Wählen Sie die Anzahl der Bits aus, die im Schlüssel enthalten sein sollen.
   - **Hashalgorithmus** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): Wählen Sie einen der verfügbaren Hashalgorithmustypen, der für dieses Zertifikat verwendet werden soll. Wählen Sie die höchste Sicherheitsebene aus, die die verbundenen Geräten unterstützen.
   - **Stammzertifikat**: Wählen Sie ein [Profil für das vertrauenswürdige Stammzertifikat](certficates-pfx-configure.md#create-a-trusted-certificate-profile) aus, das Sie zuvor konfiguriert und dem Benutzer und/oder dem Gerät zugewiesen haben. Dieses Zertifizierungsstellenzertifikat muss das Stammzertifikat für die Zertifizierungsstelle sein, die das Zertifikat ausstellt, das Sie in diesem Zertifikatprofil konfigurieren. Vergewissern Sie sich, dass Sie dieses Profil für das vertrauenswürdige Stammzertifikat der Gruppe zuweisen, die auch dem SCEP-Zertifikatprofil zugewiesen ist.
   - **Erweiterte Schlüsselverwendung**: Hier können Sie Werte für den beabsichtigten Zweck des Zertifikats **hinzufügen**. In den meisten Fällen erfordert das Zertifikat **Clientauthentifizierung**, damit der Benutzer bzw. das Gerät auf einem Server authentifiziert werden kann. Sie können jedoch nach Bedarf weitere Schlüsselverwendungen hinzufügen.
   - **Registrierungseinstellungen**
     - **Verlängerungsschwellenwert (%)** : Geben Sie den Prozentsatz der Zertifikatgültigkeitsdauer an, die verbleibt, bevor das Gerät eine Verlängerung des Zertifikats anfordert.
     - **SCEP-Server-URLs**: Geben Sie mindestens eine URL für die NDES-Server ein, die Zertifikate über SCEP ausstellen. Geben Sie zum Beispiel `https://ndes.contoso.com/certsrv/mscep/mscep.dll` ein.
     - Klicken Sie auf **OK**, und **erstellen** Sie Ihr Profil.

Das Profil wird erstellt und im Bereich „Profilliste“ angezeigt.

## <a name="assign-the-certificate-profile"></a>Zuweisen des Zertifikatprofils

Beachten Sie Folgendes, bevor Sie Gruppen Zertifikatprofile zuweisen:

- Wenn Sie Gruppen Zertifikatprofile zuweisen, wird die Zertifikatsdatei aus dem Profil des vertrauenswürdigen Zertifizierungsstellenzertifikats auf dem Gerät installiert. Das Gerät verwendet das SCEP-Zertifikatprofil, um eine Zertifikatanforderung für das Gerät zu erstellen.
- Zertifikatprofile werden nur auf den Geräten installiert, auf denen die beim Erstellen des Profils verwendete Plattform ausgeführt wird.
- Sie können Zertifikatprofile zu Benutzer- oder Gerätesammlungen zuweisen.
- Damit Zertifikate möglichst schnell nach der Geräteregistrierung auf Geräten veröffentlicht werden können, weisen Sie das Zertifikatprofil besser einer Benutzergruppe zu (nicht einer Gerätegruppe). Wenn Sie es einer Gerätegruppe zuweisen, muss eine vollständige Geräteregistrierung stattfinden, bevor das Gerät Richtlinien empfängt.
- Obwohl Sie jedes Profil separat zuweisen, müssen Sie auch die vertrauenswürdige Stammzertifizierungsstelle und das SCEP- oder PKCS-Profil zuweisen. Andernfalls schlägt die SCEP- oder PKCS-Zertifikatrichtlinie fehl.

    > [!NOTE]
    > Unter iOS sollten Ihnen mehrere Kopien des Zertifikats im Verwaltungsprofil angezeigt werden, wenn Sie mehrere Ressourcenprofile bereitstellen, die das gleiche Zertifikatprofil verwenden.
- Wenn Sie die Co-Verwaltung für Intune und Configuration Manager verwenden, bewegen Sie in Configuration Manager den [Schieberegler für Workloads](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads) für die *Ressourcenzugriffsrichtlinie* auf **Intune** oder **Pilot Intune**. Diese Einstellung ermöglicht es Windows 10-Clients, den Prozess zur Anforderung des Zertifikats zu starten.  

Informationen zum Zuweisen von Profilen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Überprüfen und Behandeln von Problemen beim Setup des Intune-Connectors

Informationen zum Beheben von Problemen und Überprüfen des Intune-Connector-Setups finden Sie unter [Certificate Authority script samples (Skriptbeispiele für die Zertifizierungsstelle)](https://aka.ms/intuneconnectorverificationscript).

## <a name="intune-connector-events-and-diagnostic-codes"></a>Ereignisse und Diagnosecodes des Intune-Connectors

Ab Version 6.1806.x.x protokolliert der Intune-Connectordienst Ereignisse in der **Ereignisanzeige** (**Anwendungs- und Dienstprotokolle** > **Microsoft Intune-Connector**). Mit diesen Ereignissen können Sie mögliche Probleme bei der Konfiguration des Intune-Connectors beheben. In diesen Ereignissen werden erfolgreiche und fehlgeschlagene Vorgänge protokolliert. Außerdem enthalten sie Diagnosecodes mit Meldungen, die IT-Administratoren bei der Problembehandlung helfen.

### <a name="event-ids-and-descriptions"></a>Ereignis-IDs und -beschreibungen

> [!NOTE]
> Ausführliche Informationen zu den Diagnosecodes für jedes Ereignis finden Sie in der Tabelle **Diagnosecodes** weiter unten in diesem Artikel.

| Ereignis-ID      | Ereignisname    | Ereignisbeschreibung | Zugehörige Diagnosecodes |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Der Connectordienst wurde gestartet. | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Der Connectordienst wurde beendet. | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Das Connectorregistrierungszertifikat wurde erfolgreich erneuert. | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Das Connectorregistrierungszertifikat konnte nicht erneuert werden. Installieren Sie den Connector neu. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Das Connectorregistrierungszertifikat konnte nicht aus der Registrierung abgerufen werden. Den Zertifikatfingerabdruck für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Diagnoseinformationen finden Sie in den Ereignisdetails. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Ein PKCS-Zertifikat wurde erfolgreich ausgestellt. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen, den Zertifizierungsvorlagennamen und den Zertifikatfingerabdruck für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Ein PKCS-Zertifikat konnte nicht ausgestellt werden. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen, den Zertifizierungsvorlagennamen und den Zertifikatfingerabdruck für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Das Zertifikat wurde erfolgreich widerrufen. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen und die Zertifikatseriennummer für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Das Zertifikat konnte nicht widerrufen werden. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen und die Zertifikatseriennummer für dieses Ereignis finden Sie in den Ereignisdetails. Weitere Informationen finden Sie in den SCEP-SVC-Protokollen.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Die Zertifikatanforderung oder die Widerrufdaten wurden erfolgreich hochgeladen. Informationen zu Uploads finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Die Zertifikatanforderung oder die Widerrufdaten konnten nicht hochgeladen werden. Zur Ermittlung des Fehlers können Sie den Uploadstatus in den Ereignisdetails überprüfen.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Eine Anforderung zum Signieren eines Zertifikats, Herunterladen eines Clientzertifikats oder Widerrufen eines Zertifikats wurde erfolgreich heruntergeladen. Informationen zu Downloads finden Sie in den Ereignisdetails.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Eine Anforderung zum Signieren eines Zertifikats, Herunterladen eines Clientzertifikats oder Widerrufen eines Zertifikats konnte nicht heruntergeladen werden. Informationen zu Downloads finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Der Zertifikatregistrierungspunkt hat die Clientabfrage erfolgreich überprüft. | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Der Zertifikatregistrierungspunkt hat die Anforderung zwar abgeschlossen, diese jedoch abgelehnt. Weitere Informationen erhalten Sie durch den Diagnosecode und die zugehörige Meldung. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Der Zertifikatregistrierungspunkt konnte die Clientabfrage nicht überprüfen. Weitere Informationen erhalten Sie durch den Diagnosecode und die zugehörige Meldung. Die Geräte-ID und die zugehörige Abfrage finden Sie in den Ereignismeldungsdetails. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | Der Zertifikatregistrierungspunkt hat den Benachrichtigungsprozess erfolgreich abgeschlossen und das Zertifikat an das Clientgerät gesendet. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | Der Zertifikatregistrierungspunkt konnten den Benachrichtigungsprozess nicht abschließen. Informationen zur Anforderung finden Sie in den Ereignismeldungsdetails. Überprüfen Sie die Verbindung zwischen dem SCEP-Server und der Zertifizierungsstelle. | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>Diagnosecodes

| Diagnosecode | Diagnosename | Diagnosemeldung |
| -------------   | -------------   | -------------      |
| 0x00000000 | Erfolgreich  | Erfolgreich |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | Die Zertifizierungsstelle ist ungültig oder nicht erreichbar. Stellen Sie sicher, dass die Zertifizierungsstelle verfügbar ist und Ihr Server mit dieser kommunizieren kann. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Das Symantec-Clientauthentifizierungszertifikat konnte im lokalen Zertifikatspeicher nicht gefunden werden. Weitere Informationen finden Sie im Artikel [Einrichten des Intune-Zertifikatconnectors für die DigiCert-PKI-Plattform](https://docs.microsoft.com/intune/certificates-digicert-configure#troubleshooting).  |
| 0x00000402 | RevokeCert_AccessDenied  | Für das angegebene Konto sind keine Berechtigungen vorhanden, mit denen ein Zertifikat der Zertifizierungsstelle widerrufen werden kann. Die ausstellende Zertifizierungsstelle können Sie durch das Feld für den Namen der Zertifizierungsstelle in den Ereignismeldungsdetails ermitteln.  |
| 0x00000403 | CertThumbprint_NotFound  | Für Ihre Eingabe konnte kein zugehöriges Zertifikat gefunden werden. Registrieren Sie den Zertifikatconnector, und wiederholen Sie den Vorgang. |
| 0x00000404 | Certificate_NotFound  | Für die Eingabe konnte kein zugehöriges Zertifikat gefunden werden. Registrieren Sie den Zertifikatconnector erneut, und wiederholen Sie den Vorgang. |
| 0x00000405 | Certificate_Expired  | Ein Zertifikat ist abgelaufen. Registrieren Sie den Zertifikatconnector erneut, um das Zertifikat zu erneuern, und wiederholen Sie den Vorgang. |
| 0x00000408 | CRPSCEPCert_NotFound  | Das CRP-Verschlüsselungszertifikat wurde nicht gefunden. Stellen Sie sicher, dass SCEP und der Intune-Connector richtig eingerichtet sind. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Das Signaturzertifikat konnte nicht abgerufen werden. Stellen Sie sicher, dass der Intune-Connectordienst richtig konfiguriert ist und der Intune-Connectordienst ausgeführt wird. Achten Sie außerdem darauf, dass Zertifikatdownloads erfolgreich abgeschlossen wurden. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Die SCEP-Abfrage konnte nicht deserialisiert werden. Stellen Sie sicher, dass SCEP und der Intune-Connector richtig eingerichtet sind. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Die Anforderung wurde aufgrund einer abgelaufenen Zertifikatabfrage abgelehnt. Das Clientgerät kann eine neue Anforderung stellen, nachdem es eine neue Abfrage vom Verwaltungsserver abgerufen hat. |
| 0x0FFFFFFFF | Unknown_Error  | Die Anforderung kann nicht abgeschlossen werden, da ein serverseitiger Fehler aufgetreten ist. Bitte versuchen Sie es erneut. |

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden Sie PKCS-Zertifikate](certficates-pfx-configure.md), oder [stellen Sie PKCS-Zertifikate über einen Symantec-PKI-Verwaltungswebservice aus](certificates-symantec-configure.md).
- [Hinzufügen einer Partnerzertifizierungsstelle in Intune mithilfe von SCEP](certificate-authority-add-scep-overview.md)
- Zusätzliche Unterstützung finden Sie in den folgenden Anleitungen:
  - [Problembehandlung für die Bereitstellung eines SCEP-Zertifikatprofils in Microsoft Intune](https://support.microsoft.com/help/4457481)
  - [Problembehandlung der NDES-Konfiguration für die Verwendung mit Microsoft Intune-Zertifikatprofilen](https://support.microsoft.com/help/4459540)
