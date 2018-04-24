---
title: Konfigurieren der Zertifikatinfrastruktur für PFX
description: Erstellen Sie PFX-Zertifikatprofile, und stellen Sie sie bereit.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/17/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 819c314b2fe69077fb545afa670587c85d4fa7ef
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configure-certificate-infrastructure"></a>Konfigurieren der Zertifikatinfrastruktur

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

In diesem Thema werden die Anforderungen beschrieben, die zum Erstellen und Bereitstellen von PFX-Zertifikatprofilen erfüllt sein müssen.

Für jede zertifikatbasierte Authentifizierung im Unternehmen benötigen Sie eine Unternehmenszertifizierungsstelle.

Damit Sie PFX-Zertifikatprofile verwenden können, benötigen Sie zusätzlich zur Unternehmenszertifizierungsstelle auch Folgendes:

-   einen Computer, der mit der Zertifizierungsstelle kommunizieren kann (Sie können auch den Computer der Zertifizierungsstelle selbst verwenden).

-  den Intune Zertifikatconnector, der auf dem Computer ausgeführt wird, der mit der Zertifizierungsstelle kommunizieren kann.

## <a name="on-premises-infrastructure-description"></a>Beschreibung der lokalen Infrastruktur


- **Active Directory-Domäne**: Alle in diesem Abschnitt aufgeführten Server (außer dem Webanwendungsproxy-Server) müssen der Active Directory-Domäne angehören.

- **Zertifizierungsstelle**: Eine Unternehmenszertifizierungsstelle (Certification Authority; CA), die auf einer Enterprise-Edition von Windows Server 2008 R2 oder höher ausgeführt wird. Eine eigenständige Zertifizierungsstelle wird nicht unterstützt. Anleitungen zum Einrichten einer Zertifizierungsstelle finden Sie unter [Installieren der Zertifizierungsstelle](http://technet.microsoft.com/library/jj125375.aspx).
   Wenn die Zertifizierungsstelle unter Windows Server 2008 R2 ausgeführt wird, müssen Sie [den Hotfix von KB2483564 installieren](http://support.microsoft.com/kb/2483564/).

- **Computer, der mit der Zertifizierungsstelle kommunizieren kann**: Verwenden Sie alternativ den Computer der Zertifizierungsstelle selbst.
- **Microsoft Intune-Zertifikatconnector**: Sie verwenden die Intune-Verwaltungskonsole zum Herunterladen des Installationsprogramms für den **Zertifikatconnector** (**ndesconnectorssetup.exe**). Führen Sie **ndesconnectorssetup.exe** dann auf dem Computer aus, auf dem Sie den Zertifikatconnector installieren möchten. Installieren Sie für PFX-Zertifikatprofile den Zertifikatconnector auf dem Computer, der mit der Zertifizierungsstelle kommuniziert.
- **Webanwendungsproxy-Server** (optional): Sie können einen Server mit Windows Server 2012 R2 oder höher als Webanwendungsproxy-Server (WAP) verwenden. Diese Konfiguration:
   -  ermöglicht Geräten das Empfangen von Zertifikaten über eine Internetverbindung,
   -  ist eine Sicherheitsempfehlung, wenn Geräte eine Verbindung über das Internet herstellen, um Zertifikate zu empfangen oder zu erneuern.

  > [!NOTE]           
  > -    Auf dem Server, der den WAP hostet, [muss ein Update installiert werden](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx), das die Unterstützung für lange URLs aktiviert, die vom Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service; NDES) verwendet werden. Dieses Update ist im [Updaterollup vom Dezember 2014](http://support.microsoft.com/kb/3013769)enthalten oder kann auch einzeln von [KB3011135](http://support.microsoft.com/kb/3011135)heruntergeladen werden.
  >-  Zudem muss der Server, der den WAP hostet, über ein SSL-Zertifikat verfügen, das mit dem Namen übereinstimmt, der für externe Clients veröffentlicht wird. Ferner muss das SSL-Zertifikat, das auf dem NDES-Server verwendet wird, vertrauenswürdig sein. Diese Zertifikate ermöglichen dem WAP-Server, die SSL-Verbindung von Clients zu beenden und eine neue SSL-Verbindung mit dem NDES-Server herzustellen.
   Weitere Informationen über Zertifikate für WAP finden Sie im Abschnitt **Planen von Zertifikaten** des Themas [Installieren und Konfigurieren des Webanwendungsproxys für die Veröffentlichung interner Anwendungen](https://technet.microsoft.com/library/dn383650.aspx). Allgemeine Informationen zu WAP-Servern finden Sie unter [Verwenden des Webanwendungsproxys](http://technet.microsoft.com/library/dn584113.aspx).|


### <a name="certificates-and-templates"></a>Zertifikate und Vorlagen

|Objekt|Details|
|----------|-----------|
|**Zertifikatvorlage**|Sie konfigurieren diese Vorlage auf der ausstellenden Zertifizierungsstelle.|
|**Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle**|Sie exportieren dies als eine **CER** -Datei von der ausstellenden Zertifizierungsstelle oder von Geräten, die der ausstellenden Zertifizierungsstelle vertrauen, und stellen es mit dem Zertifikatprofil der vertrauenswürdigen Zertifizierungsstelle für Geräte bereit.<br /><br />Sie verwenden für jede Betriebssystemplattform ein einzelnes Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle und ordnen es dem jeweiligen vertrauenswürdigen Stammzertifikatprofil zu, das Sie erstellen.<br /><br />Sie können bei Bedarf zusätzliche vertrauenswürdige Stammzertifizierungsstellenzertifikate verwenden. Sie können dies zum Beispiel vornehmen, um einer Zertifizierungsstelle eine Vertrauensstellung zu gewähren, die die Serverauthentifizierungszertifikate für Ihre WLAN-Zugriffspunkte signiert.|


## <a name="configure-your-infrastructure"></a>Konfigurieren der Infrastruktur
Bevor Sie Zertifikatprofile konfigurieren können, müssen Sie die folgenden Aufgaben ausführen. Diese Aufgaben setzen Kenntnisse in Windows Server 2012 R2 und Active Directory-Zertifikatdiensten voraus:

- **Aufgabe 1**: Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle
- **Aufgabe 2**: Aktivieren, Installieren und Konfigurieren des Intune Certificate Connectors

### <a name="task-1---configure-certificate-templates-on-the-certification-authority"></a>Aufgabe 1: Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle
Bei dieser Aufgabe veröffentlichen Sie die Zertifikatvorlage.

##### <a name="to-configure-the-certification-authority"></a>So konfigurieren Sie die Zertifizierungsstelle

1.  Verwenden Sie auf der ausstellenden Zertifizierungsstelle das Zertifikatvorlagen-Snap-In, um eine neue benutzerdefinierte Vorlage zu erstellen oder eine vorhandene Vorlage (z.B. die Vorlage „Benutzer“) zu kopieren und sie anschließend für die Verwendung mit PFX zu bearbeiten.

    Für die Vorlage müssen Sie folgende Aktionen ausführen:

    -   Geben Sie einen aussagekräftigen **Vorlagenanzeigenamen** für die Vorlage ein.

    -   Wählen Sie auf der Registerkarte **Antragstellername** die Option **Informationen werden in der Anforderung angegeben**. 

    -   Stellen Sie sicher, dass auf der Registerkarte **Erweiterungen** die **Beschreibung der Anwendungsrichtlinien** die **Clientauthentifizierung**umfasst.

        > [!IMPORTANT]
        > Bearbeiten Sie für iOS- und Mac OS X-Zertifikatvorlagen auf der Registerkarte **Erweiterungen** die Option **Schlüsselverwendung**, und stellen Sie sicher, dass die Option **Signatur ist Ursprungsnachweis** nicht aktiviert ist.

2.  Prüfen Sie auf der Registerkarte **Allgemein** die **Gültigkeitsdauer** der Vorlage. In der Standardeinstellung verwendet Intune den in der Vorlage konfigurierten Wert. Sie haben jedoch die Möglichkeit, die Zertifizierungsstelle so zu konfigurieren, dass dem Antragsteller ermöglicht wird, einen anderen Wert anzugeben, den Sie dann in der Intune-Verwaltungskonsole festlegen können. Wenn Sie immer den in der Vorlage festgelegten Wert verwenden möchten, überspringen Sie den Rest dieses Schritts.

    > [!IMPORTANT]
    > Die iOS- und Mac OS X-Plattformen verwenden immer den in der Vorlage festgelegten Wert, unabhängig von anderen Konfigurationen, die Sie vornehmen.

    Um die Zertifizierungsstelle so zu konfigurieren, dass der Antragsteller die Gültigkeitsdauer festlegen kann, führen Sie auf der Zertifizierungsstelle die folgenden Befehle aus:

    ein.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  Verwenden Sie auf der ausstellenden Zertifizierungsstelle das Zertifizierungsstellen-Snap-In, um die Zertifikatvorlage zu veröffentlichen.

    ein.  Wählen Sie den Knoten **Zertifikatvorlagen** aus, klicken Sie auf **Aktion**-&gt; **Neu** &gt; **Auszustellende Zertifikatvorlage**, und wählen Sie dann die Vorlage aus, die Sie in Schritt 2 erstellt haben.

    b.  Überprüfen Sie, ob die Vorlage veröffentlicht wurde, indem Sie sie im Ordner **Zertifikatvorlagen** anzeigen.

4.  Stellen Sie auf dem Zertifizierungsstellencomputer sicher, dass der Computer, der den Intune Certificate Connector hostet, die Berechtigung „Registrieren“ hat, damit dieser auf die Vorlage zugreifen kann, die zum Erstellen des PFX-Profils verwendet wurde. Legen Sie diese Berechtigung auf der Registerkarte **Sicherheit** in den Eigenschaften des Computers mit der Zertifizierungsstelle fest.

### <a name="task-2---enable-install-and-configure-the-intune-certificate-connector"></a>Aufgabe 2: Aktivieren, Installieren und Konfigurieren des Intune Certificate Connectors
Im Rahmen dieser Aufgabe führen Sie die folgenden Aktionen aus:

Herunterladen, Installieren und Konfigurieren des Certificate Connectors

##### <a name="to-enable-support-for-the-certificate-connector"></a>So aktivieren Sie die Unterstützung für den Zertifikatconnector

1.  Öffnen Sie die [Intune-Verwaltungskonsole](https://manage.microsoft.com), und wählen Sie **Verwaltung** &gt; **Certificate Connector** aus.

2.  Wählen Sie **Lokalen Certificate Connector konfigurieren** aus.

3.  Wählen Sie **Certificate Connector aktivieren** aus, und klicken Sie anschließend auf **OK**.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>So wird der Certificate Connector heruntergeladen, installiert und konfiguriert

1. Öffnen Sie die [Intune-Verwaltungskonsole](https://manage.microsoft.com), und klicken Sie anschließend auf **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **Certificate Connector** &gt; **Certificate Connector herunterladen**.

2. Nachdem der Download abgeschlossen ist, führen Sie das heruntergeladene Installationsprogramm (**ndesconnectorssetup.exe**) aus.

   Führen Sie das Installationsprogramm auf dem Computer aus, der eine Verbindung mit der Zertifizierungsstelle herstellen kann. Wählen Sie die Option „PFX-Verteilung“ aus, und klicken Sie auf **Installieren**. Fahren Sie nach Abschluss der Installation mit dem Erstellen eines Zertifikatprofils fort, wie unter [Konfigurieren von Zertifikatprofilen](configure-intune-certificate-profiles.md) beschrieben.

   <!-- Not sure about step 3 below -->

3. Wenn Sie zur Eingabe des Clientzertifikats für den Certificate Connector aufgefordert werden, wählen Sie **Auswählen** aus, und wählen Sie das **Clientauthentifizierungszertifikat** aus, das Sie in Aufgabe 3 installiert haben.

   Nachdem Sie das Clientauthentifizierungszertifikat ausgewählt haben, wird erneut die Oberfläche **Clientzertifikat für den Microsoft Intune-Zertifikatconnector** angezeigt. Auch wenn das ausgewählte Zertifikat nicht angezeigt wird, klicken Sie auf **Weiter**, um die Eigenschaften des Zertifikats anzuzeigen. Wählen Sie **Weiter**, und klicken Sie anschließend **Installieren**.

4. Nach Abschluss des Assistenten, jedoch vor dem Schließen des Assistenten, klicken Sie auf **Zertifikatconnector-Benutzeroberfläche starten**.

   > [!TIP]
   > Wenn Sie den Assistenten schließen, bevor Sie die Benutzeroberfläche des Zertifikatconnectors starten, können Sie sie mit dem folgenden Befehl erneut öffnen:
   >
   > **&lt;Installationspfad&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5. Gehen Sie auf der Benutzeroberfläche von **Zertifikatconnector** so vor:

   ein. Klicken Sie auf **Anmelden**, und geben Sie die Anmeldeinformationen des Intune-Dienstadministrators oder eines Mandantenadministrators mit der globalen Administratorberechtigung ein.

   b. Wählen Sie die Registerkarte **Erweitert** aus, und geben Sie anschließend die Anmeldeinformationen für ein Konto ein, das über die Berechtigung **Zertifikate ausstellen und verwalten** für die ausstellende Zertifizierungsstelle verfügt.

   c. Wählen Sie **Anwenden** aus.

   Sie können jetzt die Benutzeroberfläche des Zertifikatconnectors schließen.

6. Öffnen Sie eine Eingabeaufforderung, und geben Sie **services.msc** ein. Drücken Sie anschließend die **EINGABETASTE**, führen Sie einen Rechtsklick auf **Intune-Connectordienst** aus, und wählen Sie **Neu starten** aus.


### <a name="next-steps"></a>Nächste Schritte
Sie sind jetzt bereit, Zertifikatprofile gemäß der Beschreibung in [Konfigurieren von Intune-Zertifikatprofilen](Configure-Intune-certificate-profiles.md) zu konfigurieren.
