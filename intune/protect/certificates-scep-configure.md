---
title: 'Konfigurieren der Infrastruktur für die Unterstützung von SCEP-Zertifikatprofilen mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Konfigurieren Sie ihre lokale AD-Domäne, erstellen Sie eine Zertifizierungsstelle, richten Sie den NDES-Server ein und installieren Sie den Intune Certificate Connector, um SCEP in Microsoft Intune zu verwenden.
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
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86640c831e8836a72ad5a0a7d5023ff7d836a43a
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801576"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Konfigurieren der Infrastruktur für die Unterstützung von SCEP mit Intune

Intune unterstützt die Verwendung des SCEP (Simple Certificate Enrollment-Protokoll), um [Verbindungen mit Ihren Apps und Unternehmensressourcen zu authentifizieren](certificates-configure.md). SCEP verwendet das Zertifizierungsstellenzertifikat, um den Nachrichtenaustausch für die Zertifikatsignieranforderung zu schützen. Wenn Ihre Infrastruktur das SCEP unterstützt, können Sie *SCEP-Zertifikatprofile* von Intune (eine Art Geräteprofil in Intune) verwenden, um die Zertifikate für Ihre Geräten bereitzustellen. Der Microsoft Intune Certificate Connector ist für die Verwendung von SCEP-Zertifikatprofilen in Intune erforderlich, wenn Sie eine Zertifizierungsstelle der Active Directory-Zertifikatdienste verwenden. Der Connector ist nicht erforderlich, wenn Sie [Zertifizierungsstellen von Drittanbietern](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration) verwenden. 

Die in diesem Artikel enthaltenen Informationen helfen Ihnen beim Konfigurieren Ihrer Infrastruktur, um das SCEP bei Verwendung der Active Directory-Zertifikatdienste zu unterstützen. Nachdem Ihre Infrastruktur konfiguriert wurde, können Sie [SCEP-Zertifikatprofil mit Intune erstellen und bereitstellen](certificates-profile-scep.md).

> [!TIP]
> Intune unterstützt auch die Verwendung von [Zertifikaten des Public Key Cryptography-Standards #12](certficates-pfx-configure.md) (PKCS).

## <a name="prerequisites-for-using-scep-for-certificates"></a>Voraussetzung für die Verwendung von SCEP für Zertifikate

Stellen Sie sicher, dass Sie ein [vertrauenswürdiges *Zertifikatprofil* auf den Geräten erstellt und bereitgestellt haben](certificates-configure.md#export-the-trusted-root-ca-certificate), die SCEP-Zertifikatprofile verwenden sollen, bevor Sie fortfahren. SCEP-Zertifikatprofile referenzieren direkt das vertrauenswürdige Zertifikatprofil, das Sie verwendet haben, um vertrauenswürdige Zertifikate der Stammzertifizierungsstelle für die Geräte bereitzustellen.

### <a name="servers-and-server-roles"></a>Server und Serverrollen

Die folgende lokale Infrastruktur muss auf Servern ausgeführt werden, die in Ihre Active Directory-Domäne eingebunden sind, mit Ausnahme des Webanwendungsproxy-Servers.

- **Zertifizierungsstelle:** Verwenden Sie eine Unternehmenszertifizierungsstelle der Microsoft Active Directory-Zertifikatdienste, die in der Enterprise Edition von Windows Server 2008 R2 mit Service Pack 1 oder höher ausgeführt wird. Die von Ihnen verwendete Version von Windows Server muss von Microsoft unterstützt werden. Eine eigenständige Zertifizierungsstelle wird nicht unterstützt. Weitere Informationen finden Sie unter [Installieren der Zertifizierungsstelle](https://technet.microsoft.com/library/jj125375.aspx). Wenn Ihre Zertifizierungsstelle unter Windows Server 2008 R2 SP1 ausgeführt wird, müssen Sie [den Hotfix KB2483564 installieren](https://support.microsoft.com/kb/2483564/).

- **NDES-Serverrolle:** Sie müssen eine NDES-Serverrolle unter Windows Server 2012 R2 oder höher konfigurieren. In einem späteren Abschnitt dieses Artikels finden Sie [Anweisungen zur Installation von NDES](#set-up-ndes).

  - Der Server, der NDES hostet, muss an dieselbe Domäne und die gleiche Gesamtstruktur wie Ihre Unternehmenszertifizierungsstelle gekoppelt sein.
  - Sie können NDES nicht verwenden, wenn die Installation sich auf dem Server befindet, der die Unternehmenszertifizierungsstelle hostet.
  - Sie installieren Microsoft Intune Certificate Connector auf dem gleichen Server, der NDES hostet.

  Weitere Informationen über NDES finden Sie im [Leitfaden für den Registrierungsdienst für Netzwerkgeräte](https://technet.microsoft.com/library/hh831498.aspx) in der Windows Server-Dokumentation und unter [Verwenden eines Richtlinienmoduls mit dem Registrierungsdienst für Netzwerkgeräte](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector:** Der Microsoft Intune Certificate Connector ist für die Verwendung von SCEP-Zertifikatprofilen in Intune erforderlich. Dieser Artikel enthält Anweisungen zur [Installation des Connectors](#install-the-intune-certificate-connector).

  Der Connector unterstützt den FIPS-Modus (Federal Information Processing Standard). FIPS ist zwar nicht erforderlich, wenn er jedoch aktiviert ist, können Sie Zertifikate ausstellen und widerrufen.
  - Der Connector muss auf dem gleichen Server wie die NDES-Serverrolle ausgeführt werden, ein Server, auf dem Windows Server 2012 R2 oder höher ausgeführt wird.
  - .NET Framework 4.5 ist für den Connector erforderlich und standardmäßig in Windows Server 2012 R2 enthalten.
  - Die verstärkte Sicherheitskonfiguration für Internet Explorer [muss auf dem NDES hostenden Server und dem Microsoft Intune Certificate Connector deaktiviert sein](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx).

Die folgende lokale Infrastruktur ist optional:

Sie müssen Ihre NDES-URL extern in Ihrem Unternehmensnetzwerk veröffentlichen, um Geräten zu ermöglichen, Zertifikate über das Internet abzurufen. Sie können entweder den Azure Active Directory-Anwendungsproxy, den Webanwendungsproxy-Server oder einen anderen Reverseproxy verwenden.

- **Azure AD-Anwendungsproxy** (optional): Sie können den Azure AD-Anwendungsproxy anstelle eines dedizierten WAP-Servers (Webanwendungsproxy) verwenden, um Ihre NDES-URL im Internet zu veröffentlichen. Dies ermöglicht sowohl Geräten mit Zugriff auf das Intranet als auch Geräten mit Zugriff auf das Internet, Zertifikate abzurufen. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen von sicherem Remotezugriff auf lokale Anwendungen](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

- **Webanwendungsproxy-Server** (optional): Verwenden Sie einen Server unter Windows Server 2012 R2 oder höher als WAP-Server, um Ihre NDES-URL im Internet zu veröffentlichen.  Dies ermöglicht sowohl Geräten mit Zugriff auf das Intranet als auch Geräten mit Zugriff auf das Internet, Zertifikate abzurufen.

  Auf dem Server, der den WAP hostet, [muss ein Update installiert werden](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) , das die Unterstützung für lange URLs aktiviert, die vom Registrierungsdienst für Netzwerkgeräte verwendet werden. Dieses Update ist im [Updaterollup vom Dezember 2014](https://support.microsoft.com/kb/3013769) enthalten oder kann auch einzeln von [KB3011135](https://support.microsoft.com/kb/3011135) heruntergeladen werden.

  Der WAP-Server muss über ein SSL-Zertifikat verfügen, das mit dem Namen übereinstimmt, der für externe Clients veröffentlicht wurde. Außerdem muss der WAP-Server dem SSL-Zertifikat vertrauen, das auf dem Computer verwendet wird, auf dem der NDES-Dienst gehostet wird. Diese Zertifikate ermöglichen dem WAP-Server, die SSL-Verbindung von Clients zu beenden und eine neue SSL-Verbindung mit dem NDES-Dienst herzustellen.

  Weitere Informationen finden Sie unter [Planzertifikate](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) und [Arbeiten mit dem Webanwendungsproxy](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Konten

- **NDES-Dienstkonto:** Wählen Sie ein Domänenbenutzerkonto zur Verwendung als NDES-Dienstkonto aus, bevor Sie NDES einrichten. Sie geben dieses Konto an, wenn Sie die Vorlagen für Ihre ausstellende Zertifizierungsstelle konfigurieren, bevor Sie NDES konfigurieren.

  Dieses Konto muss auf dem Server, der NDES hostet, über die folgenden Berechtigungen verfügen:

  - **lokale Anmeldung**
  - **Anmeldung als Dienst**
  - **Anmeldung als Batchauftrag**

  Weitere Informationen finden Sie unter [Erstellen eines Domänenbenutzerkontos zur Verwendung als NDES-Dienstkonto](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account).

- **Zugriff auf den Computer, der den NDES-Dienst hostet:** Sie benötigen ein Domänenbenutzerkonto mit den Berechtigungen zum Installieren und Konfigurieren von Windows-Serverrollen auf dem Server, auf dem Sie NDES installieren.

- **Zugriff auf die Zertifizierungsstelle:** Sie benötigen ein Domänenbenutzerkonto mit den Berechtigungen zum Verwalten Ihrer Zertifizierungsstelle.

### <a name="network-requirements"></a>Netzwerkanforderungen

Es wird empfohlen, den NDES-Dienst über einen Reverseproxy zu veröffentlichen, z. B. über den [Azure AD-Anwendungsproxy, Webzugriffsproxy](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/) oder einen Drittanbieterproxy. Wenn Sie keinen Reverseproxy verwenden, lassen Sie TCP-Datenverkehr über Port 443 von allen Hosts und IP-Adressen des Internets zum NDES-Dienst zu.

Genehmigen Sie alle Ports und Protokolle, die für die Kommunikation zwischen dem NDES-Dienst und jeglicher unterstützender Infrastruktur in Ihrer Umgebung erforderlich sind. Beispielsweise muss der Computer, der den NDES-Dienst hostet, mit der Zertifizierungsstelle, den DNS-Servern, den Domänencontrollern und möglicherweise anderen Diensten oder Servern in Ihrer Umgebung kommunizieren, z. B. mit Configuration Manager.

### <a name="certificates-and-templates"></a>Zertifikate und Vorlagen

Die folgenden Zertifikate und Vorlagen werden verwendet, wenn Sie das SCEP verwenden.

|Objekt    |Details    |
|----------|-----------|
|**SCEP-Zertifikatvorlage**         |Diese Vorlage konfigurieren Sie für Ihre ausstellende Zertifizierungsstelle, die zur Erfüllung der SCEP-Anforderungen der Geräte verwendet wird. |
|**Clientauthentifizierungszertifikat** |Wird von Ihrer ausstellenden oder öffentlichen Zertifizierungsstelle angefordert.<br /> Sie installieren dieses Zertifikat auf dem Computer, der den NDES-Dienst hostet. Es wird dann vom Intune Certificate Connector verwendet.<br /> Wenn für das Zertifikat die Schlüsselverwendung für die *Client-* und *Serverauthentifizierung* für die Zertifizierungsstellenvorlage festgelegt ist (**Erweiterte Schlüsselverwendung**), die Sie zum Ausstellen dieses Zertifikats verwenden. Sie können dann dasselbe Zertifikat für die Server- und Clientauthentifizierung verwenden. |
|**Serverauthentifizierungszertifikat** |Das Webserverzertifikat, das von Ihrer ausstellenden oder öffentlichen Zertifizierungsstelle angefordert wird.<br /> Sie installieren und binden dieses SSL-Zertifikat auf dem NDES hostenden Computer in IIS ein.<br />Wenn für das Zertifikat die Schlüsselverwendung für die *Client-* und *Serverauthentifizierung* für die Zertifizierungsstellenvorlage festgelegt ist (**Erweiterte Schlüsselverwendung**), die Sie zum Ausstellen dieses Zertifikats verwenden. Sie können dann dasselbe Zertifikat für die Server- und Clientauthentifizierung verwenden. |
|**Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle**       |Für die Verwendung eines SCEP-Zertifikatprofils müssen Geräte Ihrer vertrauenswürdigen Stammzertifizierungsstelle vertrauen. Verwenden Sie ein *vertrauenswürdiges Zertifikatprofil* in Intune, um die vertrauenswürdige Stammzertifizierungsstelle für Benutzer und Geräte bereitzustellen. <br/><br/> **–** Verwenden Sie eine vertrauenswürdige Stammzertifizierungsstelle pro Betriebssystemplattform, und weisen Sie dieses Zertifikat allen vertrauenswürdigen Zertifikatprofilen zu, die Sie erstellen. <br /><br /> **–** Bei Bedarf können Sie zusätzliche Zertifikate der vertrauenswürdigen Stammzertifizierungsstelle verwenden. Beispielsweise können Sie zusätzliche Zertifikate verwenden, um einer Zertifizierungsstelle eine Vertrauensstellung zu gewähren, die die Serverauthentifizierungszertifikate für Ihre WLAN-Zugriffspunkte signiert. Erstellen Sie zusätzliche Zertifikate der vertrauenswürdigen Stammzertifizierungsstelle für ausstellende Zertifizierungsstellen.  Stellen Sie sicher, dass Sie das Profil der vertrauenswürdigen Stammzertifizierungsstelle für die ausstellende Zertifizierungsstelle im SCEP-Zertifikatprofil festlegen, das Sie in Intune erstellen.<br/><br/> Weitere Informationen zum vertrauenswürdigen Zertifikatprofil finden Sie unter [Exportieren des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle](certificates-configure.md#export-the-trusted-root-ca-certificate) und [Erstellen vertrauenswürdiger Zertifikatprofile](certificates-configure.md#create-trusted-certificate-profiles) in *Verwenden von Zertifikaten für die Authentifizierung in Intune*. |

## <a name="configure-the-certification-authority"></a>Konfigurieren der Zertifizierungsstelle

In den folgenden Abschnitten:

- konfigurieren und veröffentlichen Sie die erforderliche Vorlage für NDES
- legen Sie die erforderlichen Berechtigungen für die Zertifikatsperrung fest.

Für die folgenden Abschnitte sind Kenntnisse über Windows Server 2012 R2 oder höher und Active Directory-Zertifikatdienste erforderlich.

### <a name="access-your-issuing-ca"></a>Zugriff auf die ausstellende Zertifizierungsstelle

1. Melden Sie sich mit einem Domänenkonto mit den entsprechenden Rechten zum Verwalten der Zertifizierungsstelle bei der ausstellenden Zertifizierungsstelle an.

2. Öffnen Sie die MMC (Microsoft Management Console) für die Zertifizierungsstelle. Sie können entweder die Datei „certsrv.msc“ **ausführen** oder im **Server-Manager** auf **Extras** und dann auf **Zertifizierungsstelle** klicken.

3. Wählen Sie den Knoten **Zertifikatvorlagen** aus, und klicken Sie auf **Aktion** > **Verwalten**.

### <a name="create-the-scep-certificate-template"></a>Erstellen der SCEP-Zertifikatvorlage

1. Erstellen Sie eine v2-Zertifikatvorlage (mit Windows 2003-Kompatibilität) zur Verwendung als SCEP-Zertifikatvorlage. Sie können:

   - Verwenden Sie das *Zertifikatvorlagen-Snap-In*, um eine neue benutzerdefinierte Vorlage zu erstellen.
   - Kopieren Sie eine vorhandene Vorlage (z. B. die Benutzervorlage), und aktualisieren Sie dann die Kopie, die als NDES-Vorlage verwendet werden soll.

2. Konfigurieren Sie die folgenden Einstellungen auf den jeweiligen Registerkarten für die Vorlage:

   - **Allgemein:**

     - Deaktivieren Sie die Option **Zertifikat in Active Directory veröffentlichen**.
     - Legen Sie einen angemessenen **Vorlagenanzeigenamen** fest, damit Sie die Vorlage später identifizieren können.

   - **Antragstellername**:

     - Aktivieren Sie die Option **Informationen werden in der Anforderung angegeben**. Die Sicherheit wird durch das Intune-Richtlinienmodul für NDES erzwungen.

       ![Vorlage, Registerkarte „Antragstellername“](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)

   - **Erweiterungen:**

     - Stellen Sie sicher, dass die **Beschreibung von Anwendungsrichtlinien** die **Clientauthentifizierung** umfasst.

       > [!IMPORTANT]
       > Fügen Sie nur die Anwendungsrichtlinien hinzu, die Sie benötigen. Sprechen Sie die auszuwählenden Optionen mit Ihren Sicherheitsadministratoren ab.

     - Bearbeiten Sie für iOS- und macOS-Zertifikatvorlagen auch die **Schlüsselverwendung**, und stellen Sie sicher, dass die Option **Signatur ist Ursprungsnachweis** nicht aktiviert ist.

     ![Vorlage, Registerkarte „Erweiterungen“](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Sicherheit**:

     - Fügen Sie das **NDES-Dienstkonto** hinzu. Dieses Konto benötigt Berechtigungen zum **Lesen** und **Registrieren** dieser Vorlage.

     - Fügen Sie weitere Konten für Intune-Administratoren hinzu, die SCEP-Profile erstellen werden. Diese Konten benötigen **Leseberechtigungen** für die Vorlage, damit diese Administratoren die Vorlage beim Erstellen von SCEP-Profilen aufrufen können.

     ![Vorlage, Registerkarte „Sicherheit“](./media/certificates-scep-configure/scep-ndes-security.jpg)

   - **Anforderungsverarbeitung:**

     Die folgende Abbildung dient lediglich als Beispiel. Ihre Konfiguration kann abweichen.  

     ![Vorlage, Registerkarte „Anforderungsverarbeitung“](./media/certificates-scep-configure/scep-ndes-request-handling.png)

   - **Ausstellungsvoraussetzungen:**

     Die folgende Abbildung dient lediglich als Beispiel. Ihre Konfiguration kann abweichen.

     ![Vorlage, Registerkarte „Ausstellungsvoraussetzungen“](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)

3. Speichern Sie die Zertifikatvorlage.

### <a name="create-the-client-certificate-template"></a>Erstellen der Clientzertifikatvorlage

Der Intune Certificate Connector erfordert ein Zertifikat mit der erweiterten Schlüsselverwendung *Clientauthentifizierung* und einem Antragstellernamen, der dem FQDN des Computers entspricht, auf dem der Connector installiert ist. Eine Vorlage mit folgenden Eigenschaften ist erforderlich:

- **Erweiterungen** > **Anwendungsrichtlinien** muss die **Clientauthentifizierung** enthalten.
- **Antragstellername** > **Informationen werden in der Anforderung angegeben**.

Wenn Sie bereits über eine Vorlage verfügen, die diese Eigenschaften umfasst, können Sie diese wieder verwenden. Erstellen Sie andernfalls eine neue Vorlage, indem Sie eine vorhandene duplizieren oder eine benutzerdefinierte Vorlage erstellen.

### <a name="create-the-server-certificate-template"></a>Erstellen der Serverzertifikatvorlage

Für die Kommunikation zwischen verwalteten Geräten und IIS auf dem NDES-Server wird HTTPS verwendet, daher ist die Verwendung eines Zertifikats erforderlich. Sie können die Zertifikatvorlage **Webserver** verwenden, um dieses Zertifikat auszustellen. Alternativ können Sie eine dedizierte Vorlage mit den folgenden erforderlichen Eigenschaften verwenden, wenn Sie dies bevorzugen:

- **Erweiterungen** > **Anwendungsrichtlinien** muss die **Serverauthentifizierung** enthalten.
- **Antragstellername** > **Informationen werden in der Anforderung angegeben**.

> [!NOTE]
> Wenn Sie über ein Zertifikat verfügen, das die Anforderungen für die Client- und Serverzertifikatvorlagen erfüllt, können Sie ein einzelnes Zertifikat für IIS und den Intune Certificate Connector verwenden.

### <a name="grant-permissions-for-certificate-revocation"></a>Erteilen der Berechtigungen für die Zertifikatsperrung

Damit Intune Zertifikate widerrufen kann, die nicht mehr erforderlich sind, müssen Sie Berechtigungen in der Zertifizierungsstelle erteilen.

Für den Intune Certificate Connector können Sie entweder das **Systemkonto** für den NDES-Server oder ein spezifisches Konto wie das **NDES-Dienstkonto** verwenden.

1. Klicken Sie in der Zertifizierungsstellenkonsole mit der rechten Maustaste auf den Namen der Zertifizierungsstelle, und wählen Sie dann **Eigenschaften** aus.

2. Klicken Sie auf der Registerkarte **Sicherheit** auf **Hinzufügen**.

3. Erteilen Sie die Berechtigung **Ausstellen und Verwalten von Zertifikaten**:

   - Wenn Sie das **Systemkonto** des NDES-Servers verwenden, erteilen Sie die Berechtigung dem NDES-Server.
   - Wenn Sie das **NDES-Dienstkonto** verwenden, erteilen Sie die Berechtigung stattdessen dem Konto.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Anpassen der Gültigkeitsdauer der Zertifikatvorlage

Das Anpassen der Gültigkeitsdauer der Zertifikatvorlage ist optional.  

Nachdem Sie [die SCEP-Zertifikatvorlage erstellt haben](#create-the-scep-certificate-template), können Sie die Vorlage bearbeiten, um die **Gültigkeitsdauer** auf der Registerkarte **Allgemein** zu überprüfen.

In der Standardeinstellung verwendet Intune den in der Vorlage konfigurierten Wert. Allerdings können Sie die Zertifizierungsstelle so konfigurieren, dass der Anforderer einen anderen Wert eingeben kann und dass dieser Wert über die Intune-Konsole festgelegt werden kann.

> [!IMPORTANT]
> Verwenden Sie für iOS und macOS immer einen Wert, der in der Vorlage festgelegt wird.

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Konfigurieren eines Werts, der über die Intune-Konsole festgelegt werden kann

1. Führen Sie in der Zertifizierungsstelle die folgenden Befehle aus:

   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   -**net stop certsvc**
   -**net start certsvc**

2. Verwenden Sie auf der ausstellenden Zertifizierungsstelle das Zertifizierungsstellen-Snap-In, um die Zertifikatvorlage zu veröffentlichen. Wählen Sie den Knoten **Zertifikatvorlagen** aus, klicken Sie auf **Aktion** > **Neu** > **Auszustellende Zertifikatvorlage**, und wählen Sie dann die Zertifikatvorlage aus, die Sie im vorherigen Abschnitt erstellt haben.

3. Überprüfen Sie, ob die Vorlage veröffentlicht wurde, indem Sie sie im Ordner **Zertifikatvorlagen** anzeigen.

## <a name="set-up-ndes"></a>Einrichten von NDES

Die folgenden Prozeduren können Ihnen dabei helfen, den NDES (Registrierungsdienst für Netzwerkgeräte) zur Verwendung mit Intune zu konfigurieren. Weitere Informationen zu NDES finden Sie unter [Leitfaden zum Registrierungsdienst für Netzwerkgeräte](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)).

### <a name="install-the-ndes-service"></a>Installieren des NDES-Diensts

1. Melden Sie sich auf dem Server als **Unternehmensadministrator** an, der Ihren NDES-Dienst hosten soll, und verwenden Sie dann den [Assistent zum Hinzufügen von Rollen und Features](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)), um NDES zu installieren:

   1. Wählen Sie im Assistenten die Option **Active Directory-Zertifikatdienste** , um Zugriff auf die Rollendienste der AD-Zertifikatdienste zu erhalten. Wählen Sie die Option **Registrierungsdienst für Netzwerkgeräte** aus, deaktivieren Sie die Option **Zertifizierungsstelle**, und schließen Sie den Assistenten dann ab.

      > [!TIP]
      > Klicken Sie im **Installationsstatus** nicht auf **Schließen**. Klicken Sie stattdessen auf den Link **Active Directory-Zertifikatdienste auf dem Zielserver konfigurieren**. Daraufhin wird der **AD CS-Konfigurationsassistent** geöffnet, den Sie für die nächste Prozedur in diesem Artikel verwenden, um *den NDES-Dienst zu konfigurieren*. Nachdem der Assistent für die AD CS-Konfiguration geöffnet wurde, können Sie den Assistenten zum Hinzufügen von Rollen und Features schließen.

   2. Wenn NDES zum Server hinzugefügt wird, installiert der Assistent ebenfalls IIS. Stellen Sie sicher, dass IIS die folgenden Konfigurationen aufweist:

      - **Webserver** > **Sicherheit** > **Anforderungsfilterung**
      - **Webserver** > **Anwendungsentwicklung** > **ASP.NET 3.5**

        Bei der Installation von ASP.NET 3.5 wird .NET Framework 3.5 installiert. Installieren Sie bei Installation von .NET Framework 3.5 sowohl das Feature **.NET Framework 3.5** als auch die **HTTP-Aktivierung**.

      - **Webserver** > **Anwendungsentwicklung** > **ASP.NET 4.5**

        Bei der Installation von ASP.NET 4.5 wird .NET Framework 4.5 installiert. Installieren Sie bei der Installation von .NET Framework 4.5 das Kernfeature **.NET Framework 4.5**, das Feature **ASP.NET 4.5** und das Feature **WCF-Dienste** > **HTTP-Aktivierung**.

      - **Verwaltungstools** > **IIS 6-Verwaltungskompatibilität** > **IIS 6-Metabasiskompatibilität**
      - **Verwaltungstools** > **IIS 6-Verwaltungskompatibilität** > **Kompatibilität mit WMI für IIS 6**
      - Fügen Sie auf dem Server das NDES-Dienstkonto als Mitglied der lokalen Gruppe **IIS_IUSR** hinzu.

2. Führen Sie den folgenden Befehl auf dem Computer, der den NDES-Dienst hostet, in einer Eingabeaufforderung mit erhöhten Rechten aus. Mit dem folgenden Befehl wird der Dienstprinzipalname des NDES-Dienstkontos festgelegt:

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`

   Wenn der Computer, der den NDES-Dienst hostet, beispielsweise **Server01** heißt, Ihre Domäne **Contoso.com** und das Dienstkonto **NDESService** ist, verwenden Sie den folgenden Befehl:

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>Konfigurieren des NDES-Diensts

1. Öffnen Sie den **AD CS-Konfigurationsassistenten** auf dem Computer, der den NDES-Dienst hostet, und nehmen Sie die folgenden Änderungen vor:

   > [!TIP]
   > Wenn Sie das letzte Verfahren durchgeführt haben und auf den Link **Active Directory-Zertifikatdienste auf dem Zielserver konfigurieren** geklickt haben, sollte der Assistent bereits geöffnet sein. Andernfalls öffnen Sie den Server-Manager, um auf die Konfiguration nach der Bereitstellung der Active Directory-Zertifikatdienste zuzugreifen.

   - Wählen Sie unter **Rollendienste** die Option **Registrierungsdienst für Netzwerkgeräte** aus.
   - Geben Sie unter **Dienstkonto für NDES** das NDES-Dienstkonto an.
   - Klicken Sie unter **Zertifizierungsstelle für NDES** auf **Auswählen**, und wählen Sie dann die ausstellende Zertifizierungsstelle aus, auf der Sie die Zertifikatvorlage konfiguriert haben.
   - Legen Sie unter **Kryptografie für NDES** die Schlüssellänge entsprechend den Anforderungen Ihres Unternehmens fest.
   - Klicken Sie unter **Bestätigung** auf **Konfigurieren**, um den Assistenten zu beenden.

2. Aktualisieren Sie nach Fertigstellung des Assistenten den folgenden Registrierungsschlüssel auf dem Computer, der den NDES-Dienst hostet.

   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

   Identifizieren Sie zunächst den **Zweck** der Zertifikatvorlage (auffindbar in der Registerkarte **Anforderungsverarbeitung**), um diesen Schlüssel zu aktualisieren. Aktualisieren Sie anschließend den dazugehörigen Registrierungseintrag, indem Sie die vorhandenen Daten durch den Namen der Zertifikatvorlage (nicht durch den Anzeigenamen der Vorlage) ersetzen, den Sie angegeben haben, als Sie [die Zertifikatvorlage erstellt haben](#create-the-scep-certificate-template).

   In der folgenden Tabelle ist der Zertifikatvorlagenzweck den Werten in der Registrierung zugeordnet:

   |Zertifikatvorlagenzweck (auf der Registerkarte „Anforderungsverarbeitung“)|Zu bearbeitender Registrierungswert|In der Intune-Verwaltungskonsole für das SCEP-Profil angezeigter Wert|
   |------------------------|-------------------------|---|
   |Signatur               |SignatureTemplate        |Digitale Signatur |
   |Verschlüsselung              |EncryptionTemplate       |Schlüsselverschlüsselung  |
   |Signatur und Verschlüsselung|GeneralPurposeTemplate   |Schlüsselverschlüsselung <br/> Digitale Signatur |

   Wenn der Zweck der Zertifizierungsvorlage zum Beispiel **Verschlüsselung** ist, bearbeiten Sie den Wert **EncryptionTemplate** so, dass er dem Namen der Zertifikatvorlage entspricht.

3. Konfigurieren Sie die IIS-Anforderungsfilterung, um Unterstützung für die langen URLs (Abfragen) zu IIS hinzuzufügen, die der NDES-Dienst empfängt.

   1. Klicken Sie im IIS-Manager auf **Default Web Site** > **Request Filtering** > **Edit Feature Setting** (Standardwebsite > Abfragefilterung > Featureeinstellungen bearbeiten), um die Seite **Einstellungen für die Anforderungsfilterung bearbeiten** zu öffnen.

   2. Konfigurieren Sie die folgenden Einstellungen:

      - **Maximale URL-Länge (Bytes)**  = 65534
      - **Maximale Länge einer Abfragezeichenfolge (Bytes)**  = 65534

   3. Klicken Sie auf **OK**, um diese Konfiguration zu speichern und den IIS-Manager zu schließen.

   4. Überprüfen Sie diese Konfiguration, indem Sie den folgenden Registrierungsschlüssel anzeigen und nach den folgenden Werten prüfen:

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

      Die folgenden Werte werden als DWORD-Einträge festgelegt:

      - Name: **MaxFieldLength** mit einem Dezimalwert von **65534**
      - Name: **MaxRequestBytes** mit einem Dezimalwert von **65534**

4. Starten Sie den Server neu, der den NDES-Dienst hostet. Verwenden Sie nicht **iireset**, da die erforderlichen Änderungen dadurch nicht abgeschlossen werden.

5. Öffnen Sie *http://* Server_FQDN */certsrv/mscep/mscep.dll*. Eine NDES-Seite ähnlich der folgenden Abbildung sollte angezeigt werden:

   ![Testen von NDES](./media/certificates-scep-configure/scep-ndes-url.png)

   Wenn die Webadresse den Fehler **HTTP 503: Dienst nicht verfügbar** zurückgibt, überprüfen Sie die Ereignisanzeige des Computers. Dieser Fehler tritt in der Regel auf, wenn der Anwendungspool aufgrund einer fehlender [Berechtigung für das NDES-Dienstkonto](#accounts) beendet wird.
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Installieren und Einbinden von Zertifikaten auf dem NDES-Server

> [!TIP]
> Im folgenden Verfahren können Sie ein einzelnes Zertifikat für die *Serverauthentifizierung* und die *Clientauthentifizierung* verwenden, wenn das Zertifikat so konfiguriert ist, dass die Bedingungen beider Authentifizierungen erfüllt sind. Die Bedingungen werden in den Schritten 1 und 3 des folgenden Verfahrens beschrieben.

1. Fordern Sie ein **Serverauthentifizierungszertifikat** von ihrer internen oder öffentlichen Zertifizierungsstelle an, und installieren Sie das Zertifikat dann auf dem Server.

   Wenn der Server einen externen und einen internen Namen für einzelne Netzwerkadressen verwendet, muss das Serverauthentifizierungszertifikat Folgendes enthalten:

   - Einen **Antragstellernamen** mit einem externen öffentlichen Servernamen
   - Einen **alternativen Antragstellernamen**, der den internen Servernamen enthält

2. Binden Sie das Serverauthentifizierungszertifikat in IIS ein:

   1. Nachdem Sie das Serverauthentifizierungszertifikat installiert haben, öffnen Sie den **IIS-Manager**, und wählen Sie **Standardwebsite** aus. Klicken Sie im Bereich **Aktionen** auf **Bindungen**.

   1. Klicken Sie auf **Hinzufügen**, legen Sie als **Typ** die Option **https** fest, und stellen Sie sicher, dass der Port **443** ist.
   
   1. Geben Sie unter **SSL-Zertifikat**das Serverauthentifizierungszertifikat an.

3. Fordern Sie auf dem NDES-Server ein **Clientauthentifizierungszertifikat** von der internen oder einer öffentlichen Zertifizierungsstelle an, und installieren Sie es.

   Das Clientauthentifizierungszertifikat muss die folgenden Eigenschaften aufweisen:

   - **Erweiterte Schlüsselverwendung:** Dieser Wert muss die **Clientauthentifizierung** enthalten.
   - **Antragstellername**: Der Wert muss mit dem DNS-Namen des Servers identisch sein, auf dem das Zertifikat installiert wird (d. h. dem Namen des NDES-Servers).

4. Der Server, der den NDES-Dienst hostet, kann jetzt den Intune Certificate Connector unterstützen.

## <a name="install-the-intune-certificate-connector"></a>Installieren des Intune Certificate Connectors

Der Microsoft Intune Certificate Connector wird auf dem Server installiert, der Ihren NDES-Dienst ausführt. Die Verwendung von NDES oder des Intune Certificate Connectors wird nicht auf dem gleichen Server unterstützt, der Ihre ausstellende Zertifizierungsstelle hostet.

### <a name="to-install-the-certificate-connector"></a>So installieren Sie denZertifikatconnector

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Zertifikatconnectors** > **Hinzufügen** aus.

3. Laden Sie die Datei des Connectors für die SCEP-Datei herunter, und speichern Sie sie. Speichern Sie sie an einem Ort, auf den von dem Server aus zugegriffen werden kann, auf dem der Connector installiert wird.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. Nachdem der Download abgeschlossen ist, navigieren Sie zum Server, der die NDES-Rolle hostet. Führen Sie anschließend Folgendes durch:

   1. Stellen Sie sicher, dass .NET Framework 4.5 installiert ist, da dies für den Intune Certificate Connector erforderlich ist. .NET Framework 4.5 ist standardmäßig in Windows Server 2012 R2 und höheren Versionen enthalten.

   2. Führen Sie den Installer aus (**NDESConnectorSetup.exe**). Das Installationsprogramm installiert auch das Richtlinienmodul für NDES und den IIS-Zertifikatregistrierungspunkt-Webdienst (CRP). Der CRP-Webdienst *CertificateRegistrationSvc* wird als Anwendung in IIS ausgeführt.

      - Bei der Installation von NDES für eigenständiges Intune wird der CRP-Dienst automatisch mit dem Zertifikatconnector installiert.
      - Bei Verwendung von Intune mit dem Configuration Manager installieren Sie den Zertifikatregistrierungspunkt als eine Configuration Manager-Standortsystemrolle.

5. Wenn Sie zur Eingabe des Clientzertifikats für den Certificate Connector aufgefordert werden, klicken Sie auf **Auswählen**, und wählen Sie das **Clientauthentifizierungszertifikat** aus, das Sie im Verfahren [Installieren und Einbinden von Zertifikaten auf dem NDES-Server](#install-and-bind-certificates-on-the-server-that-hosts-ndes) in Schritt 3 in diesem Artikel auf dem NDES-Server installiert haben.

   Nachdem Sie das Clientauthentifizierungszertifikat ausgewählt haben, wird die Anzeige **Client Certificate for Microsoft Intune Certificate Connector** (Clientzertifikat für Microsoft Intune Certificate Connector) noch mal angezeigt. Auch wenn das ausgewählte Zertifikat nicht angezeigt wird, klicken Sie auf **Weiter**, um die Eigenschaften des Zertifikats anzuzeigen. Klicken Sie auf **Weiter** und anschließend auf **Installieren**.

6. Klicken Sie nach Abschluss des Assistenten, jedoch vor dem Schließen des Assistenten auf **Zertifikatconnector-Benutzeroberfläche starten**.

   Wenn Sie den Assistenten schließen, bevor Sie die Benutzeroberfläche des Zertifikatconnectors starten, können Sie sie mit dem folgenden Befehl erneut öffnen:

   *<install_Path>\NDESConnectorUI\NDESConnectorUI.exe*

7. Gehen Sie auf der Benutzeroberfläche von **Zertifikatconnector** so vor:

   1. Klicken Sie auf **Anmelden**, und geben Sie die Anmeldeinformationen des Intune-Dienstadministrators oder für einen Mandantenadministrator mit der globalen Administratorberechtigung ein.

   2. Dem Benutzerkonto, das Sie verwenden, muss eine gültige Intune-Lizenz zugewiesen werden.

   3. Nach der Anmeldung lädt der Intune Certificate Connector ein Zertifikat von Intune herunter. Dieses Zertifikat wird zur Authentifizierung zwischen dem Connector und Intune verwendet. Wenn das verwendete Konto über keine Intune-Lizenz verfügt, kann der Connector (NDESconnectorUI.exe) das Zertifikat nicht von Intune abrufen.  

      Wenn Ihre Organisation einen Proxyserver verwendet und der Proxy erforderlich ist, damit der NDES-Server auf das Internet zugreifen kann, klicken Sie auf **Proxyserver verwenden**. Geben Sie dann den Proxyservernamen, den Port und die Kontoanmeldeinformationen für die Verbindung ein.

   4. Wählen Sie die Registerkarte **Erweitert** aus, und geben Sie anschließend die Anmeldeinformationen für ein Konto ein, das über die Berechtigung **Zertifikate ausstellen und verwalten** für die ausstellende Zertifizierungsstelle verfügt. **Übernehmen** Sie Ihre Änderungen.  

    5. Sie können jetzt die Benutzeroberfläche des Zertifikatconnectors schließen.

8. Öffnen Sie eine Eingabeaufforderung, geben Sie **services.msc** ein, und drücken Sie dann die **EINGABETASTE**. Klicken Sie mit der rechten Maustaste auf **Intune-Connectordienst**, und klicken Sie auf **Neu starten**.

Öffnen Sie zum Überprüfen, ob der Dienst ausgeführt wird, einen Browser, und geben Sie die folgende URL ein. Es sollte ein **403**-Fehler zurückgegeben werden: `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Der Intune Certificate Connector unterstützt TLS 1.2. Wenn der Server, der den Connector hostet, TLS 1.2 unterstützt, wird TLS 1.2 verwendet. Wenn der Server TLS 1.2 nicht unterstützt, wird TLS 1.1 verwendet. Derzeit wird TLS 1.1 für die Authentifizierung zwischen den Geräten und dem Server verwendet.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen eines SCEP-Zertifikatprofils](certificates-profile-scep.md)  
[Problembehandlung beim Intune Certificate Connector](troubleshoot-certificate-connector-events.md)
