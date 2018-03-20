---
title: Konfigurieren und Verwalten von SCEP-Zertifikaten mit Intune
titlesuffix: Azure portal
description: Erfahren Sie, wie Sie Ihre Infrastruktur konfigurieren und dann SCEP-Zertifikatprofile in Intune erstellen und zuweisen."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d723bc4d5032a7a5c330367fe83eabd4763917a2
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="configure-and-manage-scep-certificates-with-intune"></a>Konfigurieren und Verwalten von SCEP-Zertifikaten mit Intune
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Dieses Thema erläutert, wie Sie Ihre Infrastruktur konfigurieren und dann SCEP-Zertifikatprofile (Simple Certificate Enrollment Protocol) mit Intune erstellen und zuweisen.

## <a name="configure-on-premises-infrastructure"></a>Konfigurieren der lokalen Infrastruktur

-    **Active Directory-Domäne**: Alle in diesem Abschnitt aufgeführten Server (außer dem Webanwendungsproxy-Server) müssen der Active Directory-Domäne angehören.

-  **Zertifizierungsstelle** (Certification Authority, CA): Eine Unternehmenszertifizierungsstelle, die auf einer Enterprise-Edition von Windows Server 2008 R2 oder höher ausgeführt wird. Eine eigenständige Zertifizierungsstelle wird nicht unterstützt. Informationen finden Sie unter [Installieren der Zertifizierungsstelle](http://technet.microsoft.com/library/jj125375.aspx).
    Wenn die Zertifizierungsstelle unter Windows Server 2008 R2 ausgeführt wird, müssen Sie [den Hotfix von KB2483564 installieren](http://support.microsoft.com/kb/2483564/).

-  **NDES-Server**: Auf einem Server mit Windows Server 2012 R2 oder höher müssen Sie den Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service, NDES) einrichten. Intune unterstützt die Verwendung von NDES nicht, wenn es auf einem Server ausgeführt wird, der auch die Unternehmenszertifizierungsstelle ausführt. Im [Leitfaden für den Registrierungsdienst für Netzwerkgeräte](http://technet.microsoft.com/library/hh831498.aspx) finden Sie Anweisungen zum Konfigurieren von Windows Server 2012 R2 als Host für den Registrierungsdienst für Netzwerkgeräte (NDES).
Der NDES-Server muss in die Domäne eingebunden werden, die die Zertifizierungsstelle hostet, er darf sich aber nicht auf dem gleichen Server befinden wie die Zertifizierungsstelle. Weitere Informationen zum Bereitstellen des NDES-Servers in einer separaten Gesamtstruktur, in einem isolierten Netzwerk oder in einer internen Domäne finden Sie unter [Verwenden eines Richtlinienmoduls mit dem Registrierungsdienst für Netzwerkgeräte](https://technet.microsoft.com/library/dn473016.aspx).

-  **Microsoft Intune Certificate Connector**: Verwenden Sie das Azure-Portal zum Herunterladen des Installationsprogramms für den **Certificate Connector** (**ndesconnectorssetup.exe**). Dann können Sie **ndesconnectorssetup.exe** auf dem Server ausführen, der die Rolle „Registrierungsdienst für Netzwerkgeräte“ (Network Device Enrollment Service, NDES) hostet, wo Sie den Certificate Connector installieren möchten. 
-  **Webanwendungsproxy-Server** (optional): Verwenden Sie einen Server unter Windows Server 2012 R2 oder höher als Webanwendungsproxy-Server (WAP). Diese Konfiguration:
    -  ermöglicht Geräten das Empfangen von Zertifikaten über eine Internetverbindung,
    -  ist eine Sicherheitsempfehlung, wenn Geräte eine Verbindung über das Internet herstellen, um Zertifikate zu empfangen oder zu erneuern.

 > [!NOTE]           
> -    Auf dem Server, der den WAP hostet, [muss ein Update installiert werden](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) , das die Unterstützung für lange URLs aktiviert, die vom Registrierungsdienst für Netzwerkgeräte verwendet werden. Dieses Update ist im [Updaterollup vom Dezember 2014](http://support.microsoft.com/kb/3013769)enthalten oder kann auch einzeln von [KB3011135](http://support.microsoft.com/kb/3011135)heruntergeladen werden.
>-  Zudem muss der Server, der den WAP hostet, über ein SSL-Zertifikat verfügen, das mit dem Namen übereinstimmt, der für externe Clients veröffentlicht wird. Ferner muss das SSL-Zertifikat, das auf dem NDES-Server verwendet wird, vertrauenswürdig sein. Diese Zertifikate ermöglichen dem WAP-Server, die SSL-Verbindung von Clients zu beenden und eine neue SSL-Verbindung mit dem NDES-Server herzustellen.
    Weitere Informationen über Zertifikate für WAP finden Sie im Abschnitt **Planen von Zertifikaten** des Themas [Installieren und Konfigurieren des Webanwendungsproxys für die Veröffentlichung interner Anwendungen](https://technet.microsoft.com/library/dn383650.aspx). Allgemeine Informationen zu WAP-Servern finden Sie unter [Verwenden des Webanwendungsproxys](http://technet.microsoft.com/library/dn584113.aspx).|

### <a name="network-requirements"></a>Netzwerkanforderungen

Für Datenverkehr aus dem Internet zum Umkreisnetzwerk: Lassen Sie über Port 443 Datenverkehr von allen Hosts/IP-Adressen im Internet zum NDES-Server zu.

Für Datenverkehr aus dem Umkreisnetzwerk zum vertrauenswürdigen Netzwerk: Lassen Sie alle Ports und Protokolle zu, die für den Domänenzugriff auf den in die Domäne eingebundenen NDES-Server benötigt werden. Der NDES-Server benötigt Zugriff auf die Zertifikatserver, DNS-Server, Configuration Manager-Server und Domänencontroller.

Es wird empfohlen, den NDES-Server über einen Proxy zu veröffentlichen, z. B. über den [Azure AD-Anwendungsproxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [Web Access Proxy](https://technet.microsoft.com/library/dn584107.aspx) oder einen Proxy eines Drittanbieters.


### <a name="certificates-and-templates"></a>Zertifikate und Vorlagen

|Objekt|Details|
|----------|-----------|
|**Zertifikatvorlage**|Konfigurieren Sie diese Vorlage in der ausstellenden Zertifizierungsstelle.|
|**Clientauthentifizierungszertifikat**|Dieses Zertifikat, das von der ausstellenden oder öffentlichen Zertifizierungsstelle angefordert wurde, installieren Sie auf dem NDES-Server.|
|**Serverauthentifizierungszertifikat**|Dieses SSL-Zertifikat, das von der ausstellenden oder öffentlichen Zertifizierungsstelle angefordert wurde, installieren und binden Sie in IIS auf dem NDES-Server.|
|**Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle**|Sie exportieren dieses Zertifikat als **CER**-Datei aus der Stammzertifizierungsstelle oder von einem Gerät, das der Stammzertifizierungsstelle vertraut, und weisen es Geräten mithilfe des Zertifikatprofils der vertrauenswürdigen Zertifizierungsstelle zu.<br /><br />Sie verwenden für jede Betriebssystemplattform ein einzelnes Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle und ordnen es dem jeweiligen vertrauenswürdigen Stammzertifikatprofil zu, das Sie erstellen.<br /><br />Sie können bei Bedarf zusätzliche vertrauenswürdige Stammzertifizierungsstellenzertifikate verwenden. Sie können dies zum Beispiel vornehmen, um einer Zertifizierungsstelle eine Vertrauensstellung zu gewähren, die die Serverauthentifizierungszertifikate für Ihre WLAN-Zugriffspunkte signiert.|

### <a name="accounts"></a>Konten

|Name|Details|
|--------|-----------|
|**NDES-Dienstkonto**|Geben Sie ein Domänenbenutzerkonto an, das als NDES-Dienstkonto verwendet werden soll.|

## <a name="configure-your-infrastructure"></a>Konfigurieren der Infrastruktur
Vor dem Konfigurieren von Zertifikatprofilen müssen Sie die folgenden Aufgaben ausführen, für die Sie Kenntnisse über Windows Server 2012 R2 und Active Directory-Zertifikatdienste (ADCS) benötigen:

**Schritt 1**: Erstellen eines NDES-Dienstkontos

**Schritt 2**: Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle

**Schritt 3**: Konfigurieren der Voraussetzungen auf dem NDES-Server

**Schritt 4**: Konfigurieren von NDES für die Verwendung mit Intune

**Schritt 5**: Aktivieren, Installieren und Konfigurieren des Intune Certificate Connectors

#### <a name="step-1---create-an-ndes-service-account"></a>Schritt 1: Erstellen eines NDES-Dienstkontos

Erstellen Sie ein Domänenbenutzerkonto, das als NDES-Dienstkonto verwendet werden soll. Sie geben dieses Konto an, wenn Sie Vorlagen auf der ausstellenden Zertifizierungsstelle konfigurieren, bevor Sie NDES installieren und konfigurieren. Stellen Sie sicher, dass der Benutzer über die Standardrechte **Lokal anmelden**, **Anmelden als Dienst** und **Anmelden als Batchauftrag** verfügt. In einigen Organisationen werden diese Rechte durch Härtungsrichtlinien deaktiviert.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Schritt 2: Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle
Im Rahmen dieser Aufgabe führen Sie folgende Aktionen aus:

-   Konfigurieren einer Zertifikatvorlage für NDES

-   Veröffentlichen der Zertifikatvorlage für NDES

##### <a name="to-configure-the-certification-authority"></a>So konfigurieren Sie die Zertifizierungsstelle

1.  Melden Sie sich als Unternehmensadministrator an.

2.  Verwenden Sie auf der ausstellenden Zertifizierungsstelle das Zertifikatsvorlagen-Snap-In, um eine neue benutzerdefinierte Vorlage zu erstellen oder eine vorhandene Vorlage zu kopieren. Bearbeiten Sie dann eine vorhandene Vorlage (z. B. die Vorlage „Benutzer“) für die Verwendung mit NDES.

    >[!NOTE]
    > Die NDES-Zertifikatvorlage muss auf einer v2-Zertifikatvorlage (mit Windows 2003-Kompatibilität) basieren.

    Die Vorlage muss wie folgt konfiguriert sein:

    -   Geben Sie einen aussagekräftigen **Vorlagenanzeigenamen** für die Vorlage ein.

    -   Wählen Sie auf der Registerkarte **Antragstellername** die Option **Informationen werden in der Anforderung angegeben**. (Sicherheit wird durch das Intune-Richtlinienmodul für NDES erzwungen.)

    -   Stellen Sie sicher, dass auf der Registerkarte **Erweiterungen** die **Beschreibung der Anwendungsrichtlinien** die **Clientauthentifizierung**umfasst.

        > [!IMPORTANT]
        > Bearbeiten Sie für iOS- und macOS-Zertifikatvorlagen auf der Registerkarte **Erweiterungen** die Option **Schlüsselverwendung** , und stellen Sie sicher, dass die Option **Signatur ist Ursprungsnachweis** nicht aktiviert ist.

    -   Fügen Sie auf der Registerkarte **Sicherheit** das Dienstkonto für NDES hinzu, und weisen Sie ihm Berechtigungen zum **Registrieren** der Vorlage zu. Intune-Administratoren, die SCEP-Profile erstellen, benötigen die Berechtigung **Lesen**, damit sie beim Erstellen von SCEP-Profilen zu der Vorlage navigieren können.

    > [!NOTE]
    > Zum Widerrufen von Zertifikaten benötigt das NDES-Dienstkonto die Berechtigung *Zertifikate ausstellen und verwalten* für jede Zertifikatvorlage, die von einem Zertifikatprofil verwendet wird.

3.  Prüfen Sie auf der Registerkarte **Allgemein** die **Gültigkeitsdauer** der Vorlage. In der Standardeinstellung verwendet Intune den in der Vorlage konfigurierten Wert. Sie haben jedoch die Möglichkeit, die Zertifizierungsstelle so zu konfigurieren, dass dem Antragsteller ermöglicht wird, einen anderen Wert anzugeben, den Sie dann in der Intune-Verwaltungskonsole festlegen können. Wenn Sie immer den in der Vorlage festgelegten Wert verwenden möchten, überspringen Sie den Rest dieses Schritts.

    > [!IMPORTANT]
    > iOS und macOS verwenden immer den in der Vorlage festgelegten Wert, unabhängig von anderen Konfigurationen, die Sie vornehmen.

Hier sehen Sie einige Screenshots für eine Beispielkonfiguration:

![Vorlage, Registerkarte „Anforderungsverarbeitung“](.\media\scep_ndes_request_handling.png)

![Vorlage, Registerkarte „Antragstellername“](.\media\scep_ndes_subject_name.jpg)

![Vorlage, Registerkarte „Sicherheit“](.\media\scep_ndes_security.jpg)

![Vorlage, Registerkarte „Erweiterungen“](.\media\scep_ndes_extensions.jpg)

![Vorlage, Registerkarte „Ausstellungsvoraussetzungen“](.\media\scep_ndes_issuance_reqs.jpg)

>   [!IMPORTANT]
    > Fügen Sie unter „Anwendungsrichtlinien“ nur die erforderlichen Anwendungsrichtlinien hinzu. Sprechen Sie die auszuwählenden Optionen mit Ihren Sicherheitsadministratoren ab.



Um die Zertifizierungsstelle so zu konfigurieren, dass der Antragsteller die Gültigkeitsdauer festlegen kann, gehen Sie folgendermaßen vor:

1. Führen Sie in der Zertifizierungsstelle die folgenden Befehle aus:
    - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
    - **net stop certsvc**
    - **net start certsvc**
2. Verwenden Sie auf der ausstellenden Zertifizierungsstelle das Zertifizierungsstellen-Snap-In, um die Zertifikatvorlage zu veröffentlichen.
    Wählen Sie den Knoten **Zertifikatvorlagen** aus, klicken Sie auf **Aktion**-&gt; **Neu** &gt; **Auszustellende Zertifikatvorlage**, und wählen Sie dann die Vorlage aus, die Sie in Schritt 2 erstellt haben.
3. Überprüfen Sie, ob die Vorlage veröffentlicht wurde, indem Sie sie im Ordner **Zertifikatvorlagen** anzeigen.


#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Schritt 3: Konfigurieren der Voraussetzungen auf dem NDES-Server
In dieser Aufgabe können Sie die folgenden Aktionen durchführen:

-   Hinzufügen von NDES zu einem Windows-Server und Konfigurieren von IIS zur Unterstützung von NDES

-   Hinzufügen des NDES-Dienstkontos zur Gruppe „IIS_IUSR“

-   Festlegen des SPN für das NDES-Dienstkonto




   1.  Auf dem Server, der NDES hostet, müssen Sie sich als **Unternehmensadministrator** anmelden und dann den [Assistenten zum Hinzufügen von Rollen und Features](https://technet.microsoft.com/library/hh831809.aspx) zum Installieren von NDES verwenden:

    1.  Wählen Sie im Assistenten die Option **Active Directory-Zertifikatdienste** , um Zugriff auf die Rollendienste der AD-Zertifikatdienste zu erhalten. Wählen Sie die Option **Registrierungsdienst für Netzwerkgeräte**, deaktivieren Sie die Option **Zertifizierungsstelle**, und schließen Sie den Assistenten dann ab.

        > [!TIP]
        > Klicken Sie auf der Seite **Installationsvorgang** des Assistenten nicht auf **Schließen**. Klicken Sie stattdessen auf den Link **Active Directory-Zertifikatdienste auf dem Zielserver konfigurieren**. Daraufhin wird der Assistent zur **AD CS-Konfiguration** geöffnet, den Sie für die nächste Aufgabe verwenden. Nachdem der Assistent für die AD CS-Konfiguration geöffnet wurde, können Sie den Assistenten zum Hinzufügen von Rollen und Features schließen.

    2.  Wenn NDES zum Server hinzugefügt wird, installiert der Assistent ebenfalls IIS. Stellen Sie sicher, dass IIS wie folgt konfiguriert ist:

        -   **Webserver** &gt; **Sicherheit** &gt; **Anforderungsfilterung**

        -   **Webserver** &gt; **Anwendungsentwicklung** &gt; ** ASP.NET 3.5**. Bei der Installation von ASP.NET 3.5 wird .NET Framework 3.5 installiert. Installieren Sie bei Installation von .NET Framework 3.5 sowohl das Feature **.NET Framework 3.5** als auch die **HTTP-Aktivierung**.

        -   **Webserver** &gt; **Anwendungsentwicklung** &gt; **ASP.NET 4.5**. Bei der Installation von ASP.NET 4.5 wird .NET Framework 4.5 installiert. Installieren Sie bei der Installation von .NET Framework 4.5 das Kernfeature **.NET Framework 4.5**, das Feature **ASP.NET 4.5** und das Feature **WCF-Dienste** &gt; **HTTP-Aktivierung**.

        -   **Verwaltungstools** &gt; **IIS 6-Verwaltungskompatibilität** &gt; **IIS 6-Metabasiskompatibilität**

        -   **Verwaltungstools** &gt; **IIS 6-Verwaltungskompatibilität** &gt; **IIS 6-WMI-Kompatibilität**

  2.  Fügen Sie auf dem Server das NDES-Dienstkonto als Mitglied der Gruppe **IIS_IUSR** hinzu.

   3.  Führen Sie in einer Eingabeaufforderung mit erhöhten Rechten den folgenden Befehl aus, um den SPN (Service Principal Name, Dienstprinzipalname) des NDES-Dienstkontos festzulegen:

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   Wenn der NDES-Server zum Beispiel den Namen **Server01**hat, die Domäne **Contoso.com**ist und das Dienstkonto **NDESService**lautet, verwenden Sie Folgendes:

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Schritt 4: Konfigurieren von NDES für die Verwendung mit Intune
Im Rahmen dieser Aufgabe führen Sie folgende Aktionen aus:

-   Konfigurieren von NDES für die Verwendung mit der ausstellenden Zertifizierungsstelle

-   Binden des Serverauthentifizierungszertifikats (SSL) in IIS

-   Konfigurieren der Anforderungsfilterung in IIS


1.  Öffnen Sie auf dem NDES-Server den AD CS-Konfigurations-Assistenten, und nehmen Sie dann die folgenden Konfigurationen vor:

    > [!TIP]
    > Dieser Assistent ist bereits geöffnet, wenn Sie in der vorherigen Aufgabe auf den Link geklickt haben. Andernfalls öffnen Sie den Server-Manager, um auf die Konfiguration nach der Bereitstellung der Active Directory-Zertifikatdienste zuzugreifen.

    -   Wählen Sie auf der Seite **Rollendienste** die Option **Registrierungsdienst für Netzwerkgeräte**.

    -   Geben Sie auf der Seite **Dienstkonto für NDES** das NDES-Dienstkonto an.

    -   Klicken Sie auf der Seite **ZS für NDES** auf **Auswählen**, und wählen Sie dann die ausstellende Zertifizierungsstelle aus, auf der Sie die Zertifikatvorlage konfiguriert haben.

    -   Legen Sie auf der Seite **Kryptografie für NDES** die Schlüssellänge entsprechend den Anforderungen Ihres Unternehmens fest.

    Klicken Sie auf der Seite **Bestätigung** auf **Konfigurieren** , um den Assistenten zu beenden.

2.  Bearbeiten Sie nach Beendigung des Assistenten den folgenden Registrierungsschlüssel auf dem NDES-Server:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    Um diesen Schlüssel zu bearbeiten, ermitteln Sie den **Zweck** der Zertifikatvorlage, wie auf der entsprechenden Registerkarte **Anforderungsverarbeitung** aufgeführt, und bearbeiten Sie dann den zugehörigen Eintrag in der Registrierung. Ersetzen Sie hierzu die vorhandenen Daten durch den Namen der Zertifikatvorlage (nicht den Anzeigenamen der Vorlage), den Sie in Aufgabe 1 festgelegt haben. In der folgenden Tabelle ist der Zertifikatvorlagenzweck den Werten in der Registrierung zugeordnet:

    |Zertifikatvorlagenzweck (auf der Registerkarte „Anforderungsverarbeitung“)|Zu bearbeitender Registrierungswert|In der Intune-Verwaltungskonsole für das SCEP-Profil angezeigter Wert|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Signatur|SignatureTemplate|Digitale Signatur|
    |Verschlüsselung|EncryptionTemplate|Schlüsselverschlüsselung|
    |Signatur und Verschlüsselung|GeneralPurposeTemplate|Schlüsselverschlüsselung<br /><br />Digitale Signatur|
    Wenn der Zweck der Zertifizierungsvorlage zum Beispiel **Verschlüsselung**ist, bearbeiten Sie den Wert **EncryptionTemplate** so, dass er dem Namen der Zertifikatvorlage entspricht.

3. Der NDES-Server empfängt sehr lange URLs (Abfragen), weshalb Sie zwei Registrierungseinträge hinzufügen müssen:

    |Standort|Wert|Typ|Daten|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (Dezimal)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (Dezimal)|


4. Klicken Sie im IIS-Manager auf **Standardwebsite** -> **Anforderungsfilterung** -> **Edit Feature Setting** (Featureeinstellungen bearbeiten), und ändern Sie wie abgebildet die **Maximale URL-Länge** und die **Maximale Länge einer Abfragezeichenfolge** in *65534*.

    ![Maximale Länge für URL und Abfragezeichenfolge in IIS](.\media\SCEP_IIS_max_URL.png)

5.  Starten Sie den Server neu. Das Ausführen von **iisreset** auf dem Server reicht nicht aus, um diese Änderungen abzuschließen.
6. Navigieren Sie zu http://*FQDN*/certsrv/mscep/mscep.dll. Eine NDES-Seite wird angezeigt, die der Folgenden ähnelt:

    ![Testen von NDES](.\media\SCEP_NDES_URL.png)

    Wenn Sie die Meldung **503 – Dienst nicht verfügbar** erhalten, überprüfen Sie die Ereignisanzeige. Wahrscheinlich wurde der Anwendungspool beendet, weil eine notwendige Berechtigung für den NDES-Benutzer fehlt. Die entsprechenden Berechtigungen sind in Aufgabe 1 beschrieben.

##### <a name="to-install-and-bind-certificates-on-the-ndes-server"></a>So installieren und binden Sie Zertifikate auf dem NDES-Server

1.  Fordern Sie auf dem NDES-Server ein **Serverauthentifizierungszertifikat** von der internen oder einer öffentlichen Zertifizierungsstelle an, und installieren Sie es. Sie binden dieses SSL-Zertifikat anschließend in IIS.

    > [!TIP]
    > Nachdem Sie das SSL-Zertifikat in IIS gebunden haben, installieren Sie ein Clientauthentifizierungszertifikat. Dieses Zertifikat kann von jeder Zertifizierungsstelle ausgestellt werden, die vom NDES-Server als vertrauenswürdig eingestuft wird. Obwohl es sich nicht um die bewährte Methode handelt, können Sie das gleiche Zertifikat für die Server und die Clientauthentifizierung verwenden, solange das Zertifikat über beide erweiterten Schlüsselverwendungen (EKUs) verfügt. In den folgenden Schritten finden Sie Informationen zu diesen Authentifizierungszertifikaten.

    1.  Nachdem Sie das Serverauthentifizierungszertifikat erhalten haben, öffnen Sie den **IIS-Manager**, wählen im Fenster **Verbindungen** die Option **Standardwebsite** , und klicken dann im Fenster **Aktionen** auf **Bindungen** .

    2.  Klicken Sie auf **Hinzufügen**, legen Sie als **Typ** die Option **https**fest, und stellen Sie sicher, dass der Port **443**ist. (Für eigenständiges Intune wird nur Port 443 unterstützt.)

    3.  Geben Sie unter **SSL-Zertifikat**das Serverauthentifizierungszertifikat an.

        > [!NOTE]
        > Wenn der NDES-Server sowohl einen externen als auch einen internen Namen für eine einzelne Netzwerkadresse verwendet, muss das Serverauthentifizierungszertifikat über einen **Antragstellernamen** mit einem externen öffentlichen Servernamen sowie einen **alternativen Antragstellernamen** verfügen, der den Namen des internen Servers enthält.

2.  Fordern Sie auf dem NDES-Server ein **Clientauthentifizierungszertifikat** von der internen oder einer öffentlichen Zertifizierungsstelle an, und installieren Sie es. Dies kann dasselbe Zertifikat wie das Serverauthentifizierungszertifikat sein, wenn dieses Zertifikat über beide Funktionen verfügt.

    Das Clientauthentifizierungszertifikat muss die folgenden Eigenschaften aufweisen:

    **Erweiterte Schlüsselverwendung**: Dies muss die **Clientauthentifizierung** umfassen.

    **Antragstellername**: Dies muss mit dem DNS-Namen des Servers identisch sein, auf dem das Zertifikat installiert wird (d. h. dem NDES-Server).

##### <a name="to-configure-iis-request-filtering"></a>So konfigurieren Sie die IIS-Anforderungsfilterung

1.  Öffnen Sie auf dem NDES-Server den **IIS-Manager**, wählen Sie im Fenster **Verbindungen** die Option **Standardwebsite** , und öffnen Sie dann die **Anforderungsfilterung**.

2.  Klicken Sie auf **Featureeinstellungen bearbeiten**, und legen Sie dann die folgende Werte fest:

    **Abfragezeichenfolge (Bytes)** = **65534**

    **Maximale URL-Länge (Bytes)** = **65534**

3.  Überprüfen Sie den folgenden Registrierungsschlüssel:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Stellen Sie sicher, dass die folgenden Werte als DWORD-Einträge festgelegt sind:

    Name: **MaxFieldLength**mit einem Dezimalwert von **65534**

    Name: **MaxRequestBytes**mit einem Dezimalwert von **65534**

4. Starten Sie den NDES-Server neu. Der Server ist jetzt bereit zur Unterstützung des Zertifikatconnectors.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Schritt 5: Aktivieren, Installieren und Konfigurieren des Intune Certificate Connectors
Im Rahmen dieser Aufgabe führen Sie folgende Aktionen aus:

- Aktivieren der Unterstützung für NDES in Intune
- Laden Sie den Certificate Connector herunter, und installieren und konfigurieren Sie ihn auf dem Server, der die Rolle „Registrierungsdienst für Netzwerkgeräte“ (Network Device Enrollment Service, NDES) auf einem Server in Ihrer Umgebung hostet. Um die Skalierbarkeit der NDES-Implementierung in Ihrer Organisation zu erhöhen, können Sie mehrere NDES-Server mit einem Microsoft Intune Certificate Connector auf jedem NDES-Server installieren.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>So wird der Certificate Connector heruntergeladen, installiert und konfiguriert
![ConnectorDownload](./media/certificates-download-connector.png)   
 
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
4. Klicken Sie im Bereich **Gerätekonfiguration** auf die Option **Zertifizierungsstelle**.
5. Klicken Sie zuerst auf **Hinzufügen** und dann auf **Laden Sie die Connectordatei herunter**. Speichern Sie den Download an einem Speicherort, auf den Sie auf dem Server, auf dem der Connector installiert wird, zugreifen können. 
6.  Nachdem der Download abgeschlossen ist, führen Sie das heruntergeladene Installationsprogramm (**ndesconnectorssetup.exe**) auf dem Server aus, der die Rolle „Registrierungsdienst für Netzwerkgeräte“ (Network Device Enrollment Service, NDES) hostet. Das Installationsprogramm installiert auch das Richtlinienmodul für NDES und den CRP-Webdienst. (Der CRP-Webdienst „CertificateRegistrationSvc“ wird als Anwendung in IIS ausgeführt.)

    > [!NOTE]
    > Bei der Installation von NDES für eigenständiges Intune wird der CRP-Dienst automatisch mit dem Zertifikatconnector installiert. Bei Verwendung von Intune mit dem Konfigurations-Manager installieren Sie den Zertifikatregistrierungspunkt als eine separate Standortsystemrolle.

3.  Wenn Sie zur Eingabe des Clientzertifikats für den Certificate Connector aufgefordert werden, wählen Sie **Auswählen** aus, und wählen Sie das **Clientauthentifizierungszertifikat** aus, das Sie in Aufgabe 3 auf dem NDES-Server installiert haben.

    Nachdem Sie das Clientauthentifizierungszertifikat ausgewählt haben, wird erneut die Oberfläche **Clientzertifikat für den Microsoft Intune-Zertifikatconnector** angezeigt. Auch wenn das ausgewählte Zertifikat nicht angezeigt wird, klicken Sie auf **Weiter** , um die Eigenschaften des Zertifikats anzuzeigen. Klicken Sie dann auf **Weiter**, und klicken Sie anschließend auf **installieren**.

4.  Nach Abschluss des Assistenten, jedoch vor dem Schließen des Assistenten, klicken Sie auf **Zertifikatconnector-Benutzeroberfläche starten**.

    > [!TIP]
    > Wenn Sie den Assistenten schließen, bevor Sie die Benutzeroberfläche des Zertifikatconnectors starten, können Sie sie mit dem folgenden Befehl erneut öffnen:
    >
    > **&lt;Installationspfad&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Gehen Sie auf der Benutzeroberfläche von **Zertifikatconnector** so vor:

    Klicken Sie auf **Anmelden**, und geben Sie die Anmeldeinformationen des Intune-Dienstadministrators oder für einen Mandantenadministrator mit der globalen Administratorberechtigung ein.

    > [!IMPORTANT]
    > Dem Benutzerkonto muss eine gültige Intune-Lizenz zugewiesen werden. Wenn das Benutzerkonto nicht über eine gültige Intune-Lizenz verfügt, schlägt „NDESConnectorUI.exe“ fehl.

    Wenn Ihr Unternehmen einen Proxyserver verwendet und der Proxy erforderlich ist, damit der NDES-Server auf das Internet zugreifen kann, klicken Sie auf **Proxyserver verwenden**, und geben Sie dann den Proxyservernamen, Port und die Kontoanmeldedaten für die Verbindung an.

    Wählen Sie die Registerkarte **Erweitert** aus, und geben Sie dann die Anmeldeinformationen für ein Konto ein, das über die Berechtigung **Zertifikate ausgeben und verwalten** für die ausstellende Zertifizierungsstelle verfügt, und klicken Sie dann auf **Anwenden**.

    Sie können jetzt die Benutzeroberfläche des Zertifikatconnectors schließen.

6.  Öffnen Sie eine Eingabeaufforderung, und geben Sie **services.msc** ein. Drücken Sie dann die **EINGABETASTE**, klicken Sie mit der rechten Maustaste auf **Intune-Connectordienst**, und klicken Sie dann auf **Neu starten**.

Um zu überprüfen, das der Dienst ausgeführt wird, öffnen Sie einen Browser, und geben Sie die folgenden URL ein. Es sollte ein **403** -Fehler zurückgegeben werden:

**http:// &lt;FQDN_des_NDES_Servers&gt;/certsrv/mscep/mscep.dll**

## <a name="how-to-create-a-scep-certificate-profile"></a>So erstellen Sie ein SCEP-Zertifikatprofil

1. Klicken Sie im Azure-Portal auf die Workload **Gerätekonfiguration**.
2. Klicken Sie im Bereich **Gerätekonfiguration** auf die Option **Verwalten** > **Profile**.
3. Klicken Sie im Bereich „Profile“ auf die Option **Profil erstellen**.
4. Geben Sie im Bereich **Profil erstellen** einen **Namen** und eine **Beschreibung** für das SCEP-Zertifikatprofil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform für dieses SCEP-Zertifikat aus. Derzeit können Sie eine der folgenden Plattformen für Einstellungen für Geräteeinschränkungen auswählen:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **SCEP-Zertifikat** aus.
7. Konfigurieren Sie im Bereich **SCEP-Zertifikat** die folgenden Einstellungen:
    - **Gültigkeitsdauer des Zertifikats:** Wenn Sie den Befehl **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** für die ausstellende Zertifizierungsstelle ausgeführt haben, die eine benutzerdefinierte Gültigkeitsdauer ermöglicht, können Sie die verbleibende Dauer bis zum Ablauf des Zertifikats angeben.<br>Sie können einen niedrigeren Wert als den für die Gültigkeitsdauer in der angegebenen Zertifikatvorlage angeben, aber keinen höheren. Beispiel: Wenn die Gültigkeitsdauer des Zertifikats in der Zertifikatvorlage zwei Jahre beträgt, können Sie als Wert ein Jahr angeben, aber nicht fünf Jahre. Zudem muss der Wert niedriger als die verbleibende Gültigkeitsdauer des Zertifikats der ausstellenden Zertifizierungsstelle sein. 
    - **Schlüsselspeicheranbieter (KSP):** (Windows Phone 8.1, Windows 8.1, Windows 10) Geben Sie an, wo der Schlüssel für das Zertifikat gespeichert wird. Wählen Sie einen der folgenden Werte aus:
        - **Bei TPM-KSP (Trusted Platform Module) registrieren, falls vorhanden, andernfalls Software-KSP**
        - **Bei TPM-KSP (Trusted Platform Module) registrieren, andernfalls Fehler**
        - **Bei Passport registrieren, andernfalls Fehler (Windows 10 und höher)**
        - **Bei Software-KSP registrieren**
    - **Format des Antragstellernamens:** Wählen Sie in der Liste aus, wie Intune den Antragstellernamen in der Zertifikatanforderung automatisch erstellt. Wenn das Zertifikat für einen Benutzer bestimmt ist, können Sie auch die E-Mail-Adresse des Benutzers im Antragstellernamen einschließen. Es stehen die folgenden Optionen zur Auswahl:
        - **Nicht konfiguriert**
        - **Allgemeiner Name**
        - **Allgemeiner Name einschließlich E-Mail-Adresse**
        - **Allgemeiner Name als E-Mail-Adresse**
        - **IMEI (International Mobile Equipment Identity)**
        - **Seriennummer**
        - **Benutzerdefiniert**: Wenn Sie diese Option auswählen, wird ein weiteres Dropdownfeld angezeigt. In diesem Feld können Sie ein benutzerdefiniertes Format für den Antragstellernamen eingeben. Die beiden für das benutzerdefinierte Format unterstützten Variablen sind **Allgemeiner Name (CN)** und **E-Mail (E)**. Durch Kombination einer oder mehrerer dieser Variablen mit statischen Zeichenfolgen können Sie ein benutzerdefiniertes Format wie dieses für den Antragstellernamen erstellen: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US** In diesem Beispiel haben Sie ein Format für den Antragstellernamen erstellt, das neben den Variablen „CN“ und „E“ noch Zeichenfolgen für die Organisationseinheit, den Standort, den Bundesstaat und das Land verwendet. In [diesem Thema](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) werden die **CertStrToName**-Funktion und die unterstützten Zeichenfolgen gezeigt.
        
    - **Alternativer Antragstellername:** Geben Sie an, wie die Werte für den alternativen Antragstellernamen (Subject Alternative Name, SAN) in der Zertifikatanforderung von Intune automatisch erstellt werden sollen. Beispiel: Wenn Sie einen Benutzerzertifikattyp ausgewählt haben, könnten Sie in den alternativen Antragstellernamen den Benutzerprinzipalnamen (User Principal Name, UPN) aufnehmen. Wenn das Clientzertifikat für die Authentifizierung bei einem Netzwerkrichtlinienserver verwendet werden soll, müssen Sie den alternativen Antragstellernamen auf den Benutzerprinzipalnamen festlegen. 
    - **Schlüsselverwendung:** Geben Sie Schlüsselverwendungsoptionen für das Zertifikat an. Sie können unter folgenden Optionen wählen: 
        - **Schlüsselverschlüsselung:** Lässt den Schlüsselaustausch nur zu, wenn der Schlüssel verschlüsselt ist. 
        - **Digitale Signatur:** Lässt den Schlüsselaustausch nur zu, wenn der Schlüssel durch eine digitale Signatur geschützt ist. 
    - **Schlüsselgröße (Bits):** Wählen Sie die Anzahl der Bits aus, die im Schlüssel enthalten sein sollen. 
    - **Hashalgorithmus:** (Android, Windows Phone 8.1, Windows 8.1, Windows 10) Wählen Sie einen der verfügbaren Hashalgorithmustypen aus, der für dieses Zertifikat verwendet werden soll. Wählen Sie die höchste Sicherheitsebene aus, die die verbundenen Geräten unterstützen. 
    - **Stammzertifikat:** Wählen Sie ein Profil für ein Stamm-Zertifizierungsstellenzertifikat aus, das Sie zuvor konfiguriert und dem Benutzer oder Gerät zugewiesen haben. Dieses Zertifizierungsstellenzertifikat muss das Stammzertifikat für die Zertifizierungsstelle sein, die das Zertifikat ausstellt, das Sie in diesem Zertifikatprofil konfigurieren. 
    - **Erweiterte Schlüsselverwendung:** Klicken Sie auf **Hinzufügen**, um Werte für den beabsichtigten Zweck des Zertifikats hinzuzufügen. In den meisten Fällen erfordert das Zertifikat **Clientauthentifizierung**, damit der Benutzer bzw. das Gerät auf einem Server authentifiziert werden kann. Sie können jedoch nach Bedarf weitere Schlüsselverwendungen hinzufügen. 
    - **Registrierungseinstellungen**
        - **Erneuerungsschwellenwert (%):** Geben Sie den Prozentsatz der Zertifikatgültigkeitsdauer an, die verbleibt, bevor das Gerät eine Erneuerung des Zertifikats anfordert.
        - **SCEP-Server-URLs:** Geben Sie eine oder mehrere URLs für die NDES-Server an, die Zertifikate über SCEP ausstellen. 
8. Klicken Sie auf **OK**, gehen Sie zurück zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und im Bereich „Profilliste“ angezeigt.

## <a name="how-to-assign-the-certificate-profile"></a>Zuweisen des Zertifikatprofils

Beachten Sie Folgendes, bevor Sie Gruppen Zertifikatprofile zuweisen:

- Wenn Sie Gruppen Zertifikatprofile zuweisen, wird die Zertifikatsdatei aus dem Profil des vertrauenswürdigen Zertifizierungsstellenzertifikats auf dem Gerät installiert. Das Gerät verwendet das SCEP-Zertifikatprofil, um eine Zertifikatanforderung für das Gerät zu erstellen.
- Zertifikatprofile werden nur auf den Geräten installiert, auf denen die beim Erstellen des Profils verwendete Plattform ausgeführt wird.
- Sie können Zertifikatprofile zu Benutzer- oder Gerätesammlungen zuweisen.
- Damit Zertifikate möglichst schnell nach der Geräteregistrierung auf Geräten veröffentlicht werden können, weisen Sie das Zertifikatprofil besser einer Benutzergruppe zu (nicht einer Gerätegruppe). Wenn Sie es einer Gerätegruppe zuweisen, muss eine vollständige Geräteregistrierung stattfinden, bevor das Gerät Richtlinien empfängt.
- Obwohl Sie jedes Profil separat zuweisen, müssen Sie auch die vertrauenswürdige Stammzertifizierungsstelle und das SCEP- oder PKCS-Profil zuweisen. Andernfalls schlägt die SCEP- oder PKCS-Zertifikatrichtlinie fehl.

Informationen zum Zuweisen von Profilen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

