---
title: 'Verwenden von PKCS-Zertifikaten mit Microsoft Intune: Azure | Micrososft-Dokumentation'
description: "Hinzufügen oder Erstellen von Zertifikaten für Public Key Cryptography Standards (PKCS) mit Microsoft Intune, einschließlich der Schritte zum Exportieren eines Stammzertifikats, Konfigurieren einer Zertifikatvorlage, Herunterladen und Installieren eines Microsoft Intune Certificate Connector, Erstellen eines Gerätekonfigurationsprofils, Erstellen eines PKCS-Zertifikatprofils in Azure und Ihrer Zertifizierungsstelle"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c0668921f03b24b319c2c37837dbd2cc053370ca
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Konfigurieren und Verwenden Ihrer PKCS-Zertifikate mit Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Zertifikate werden verwendet, um den Zugriff auf Ihre Unternehmensressourcen (z.B. ein VPN- oder ein WLAN-Netzwerk) zu authentifizieren und zu sichern. In diesem Artikel wird erläutert, wie Sie ein PKCS-Zertifikat exportieren und anschließend dieses Zertifikat zu einem Intune-Profil hinzufügen. 

## <a name="requirements"></a>Anforderungen

Zur Verwendung von PKCS-Zertifikaten mit Intune müssen Sie über folgende Infrastruktur verfügen:

* Eine vorhandene konfigurierte AD DS-Domäne (Active Directory Domain Services).
 
  Informationen zum Installieren und Konfigurieren von Active Directory Domain Services finden Sie unter [AD DS Design and Planning (AD DS-Entwurf und -Planung)](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

* Eine vorhandene konfigurierte Unternehmenszertifizierungsstelle.

  Weitere Informationen zum Installieren und Konfigurieren von Active Directory-Zertifikatdiensten finden Sie unter [Active Directory Certificate Services Step-by-Step Guide (Ausführliche Anleitung zu den Active Directory-Zertifikatdiensten)](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Für Intune müssen AD CS mit einer Unternehmenszertifizierungsstelle, nicht mit einer eigenständigen Zertifizierungsstelle ausgeführt werden.

* Ein Client mit Konnektivität zur Unternehmenszertifizierungsstelle.
* Eine exportierte Kopie Ihres Stammzertifikats aus Ihrer Unternehmenszertifizierungsstelle.
* Der Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) muss aus dem Intune-Portal heruntergeladen worden sein.
* Ein Windows Server zum Hosten des Microsoft Intune-Zertifikatconnectors (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportieren des Stammzertifikats aus der Unternehmenszertifizierungsstelle

Sie benötigen auf jedem Gerät ein Zertifikat einer Stamm- oder Zwischenzertifizierungsstelle für die Authentifizierung über VPN, WLAN und anderen Ressourcen. Die folgenden Schritte erläutern, wie das erforderliche Zertifikat von Ihrer Unternehmenszertifizierungsstelle abgerufen wird.

1. Melden Sie sich bei Ihrer Unternehmenszertifizierungsstelle mit einem Konto an, das über Administratorrechte verfügt.
2. Öffnen Sie eine Eingabeaufforderung als Administrator.
3. Exportieren Sie das Zertifikat der Stammzertifizierungsstelle (.cer) an einen Speicherort, an dem Sie später darauf zugreifen können.

   Beispiel:

4.  Nach Abschluss des Assistenten, jedoch vor dem Schließen des Assistenten, klicken Sie auf **Zertifikatconnector-Benutzeroberfläche starten**.

   `certutil -ca.cert certnew.cer`

   Weitere Informationen finden Sie unter [Certutil-Tasks zum Verwalten von Zertifikaten](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle

1. Melden Sie sich bei Ihrer Unternehmenszertifizierungsstelle mit einem Konto an, das über Administratorrechte verfügt.
2. Öffnen Sie die Konsole **Zertifizierungsstelle**, klicken Sie mit der rechten Maustaste auf **Zertifikatvorlagen**, und klicken Sie dann auf **Verwalten**.
3. Suchen Sie die Zertifikatvorlage **Benutzer**, klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Vorlage duplizieren**. Dann werden die **Eigenschaften der neuen Vorlage** geöffnet.
4. Gehen Sie auf der Registerkarte **Konformität** wie folgt vor: 
   * Legen Sie **Zertifizierungsstelle** auf **Windows Server 2008 R2** fest.
   * Legen Sie **Zertifizierungsstelle** auf **Windows 7/Server 2008 R2** fest.
5. Auf der Registerkarte **Allgemein** :
   * Legen Sie für **Vorlagenanzeigename** einen für Sie aussagekräftigen Namen fest.

   > [!WARNING]
   > **Vorlagenname** entspricht standardmäßig dem **Vorlagenanzeigenamen** *ohne Leerzeichen*. Notieren Sie sich den Namen der Vorlage, da Sie diesen später brauchen werden.

6. Klicken Sie unter **Anforderungsverarbeitung** auf **Exportieren von privatem Schlüssel zulassen**.
7. Bestätigen Sie unter **Kryptografie**, dass die **Minimale Schlüsselgröße** auf 2048 festgelegt ist.
8. Klicken Sie unter **Antragstellername** auf **Supply in the request** (Informationen werden in der Anforderung angegeben).
9. Überprüfen Sie unter **Erweiterungen**, ob „Verschlüsselndes Dateisystem“, „Sichere E-Mail“ und „Clientauthentifizierung“ unter **Anwendungsrichtlinien** angezeigt werden.
    
      > [!IMPORTANT]
      > Gehen Sie für iOS- und macOS-Zertifikatvorlagen auf die Registerkarte **Erweiterungen**, aktualisieren Sie die Option **Schlüsselverwendung**, und überprüfen Sie, ob die Option **Signature is proof of origin** (Signatur ist Ursprungsnachweis) nicht aktiviert ist.

10. Fügen Sie unter **Sicherheit** das Computerkonto für den Server hinzu, auf dem Sie den Microsoft Intune Certificate Connector installieren.
    * Weisen Sie diesem Konto die Berechtigungen **Lesen** und **Registrieren** zu.
11. Klicken Sie zuerst auf **Anwenden** und dann auf **OK**, um die Zertifikatvorlage zu speichern.
12. Schließen Sie die **Zertifikatvorlagenkonsole**.
13. Klicken Sie in der Konsole der **Zertifizierungsstelle** mit der rechten Maustaste auf **Zertifikatvorlagen**, und klicken Sie dann auf **Neu** und auf **Auszustellende Zertifikatvorlage**.
    * Klicken Sie auf die Vorlage, die Sie in den vorherigen Schritten erstellt haben, und klicken Sie anschließend auf **OK**.
14. Gehen Sie folgendermaßen vor, damit der Server Zertifikate im Namen von bei Intune registrierten Geräten und Benutzern verwaltet:

    ein. Klicken Sie mit der rechten Maustaste auf die Zertifizierungsstelle, und wählen Sie **Eigenschaften**.

    b. Fügen Sie auf der Registerkarte „Sicherheit“ das Computerkonto des Servers hinzu, auf dem Sie den Microsoft Intune Certificate Connector ausführen.
      * Erteilen Sie dem Computerkonto die Zulassungsberechtigungen **Zertifikate ausstellen und verwalten** und **Zertifikate anfordern**.
15. Melden Sie sich von der Unternehmenszertifizierungsstelle ab.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Laden Sie den Microsoft Intune Certificate Connector herunter, und installieren und konfigurieren Sie ihn.

![ConnectorDownload][ConnectorDownload]

1. Klicken Sie im [Azure-Portal](https://portal.azure.com) auf die Option **Alle Dienste**, und suchen Sie nach **Intune**. Klicken Sie zuerst auf **Microsoft Intune** und dann auf **Gerätekonfiguration**. 
2. Klicken Sie zuerst auf **Zertifizierungsstelle** > **Hinzufügen**, und klicken Sie anschließend auf **Download the Connector file** (Connectordatei herunterladen). Speichern Sie den Download an einem Speicherort, auf den Sie auf dem Server, auf dem der Connector installiert wird, zugreifen können. 
3. Melden Sie sich auf diesem Server an, und führen Sie das Installationsprogramm aus: 

    1. Übernehmen Sie den Standardspeicherort. Dadurch wird der Connector unter `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe` installiert.
    2. Klicken Sie unter den Optionen des Installationsprogramms auf **PFX Distribution** (PFX-Verteilung) und anschließend auf **Weiter**.
    3. Klicken Sie auf **Installieren**, und warten Sie auf den Abschluss der Installation.
    4. Aktivieren Sie danach das Feld **Intune-Connector starten**, und klicken Sie auf **Fertig stellen**.

4. Das Fenster des NDES-Connectors wird jetzt mit der Registerkarte **Registrierung** geöffnet. Klicken Sie zum Aktivieren der Verbindung mit Intune auf **Anmelden**, und geben Sie ein Konto mit globalen Administratorberechtigungen an.
5. Lassen Sie auf der Registerkarte **Erweitert** Optionsfeld **Use this computer's SYSTEM account (default)** (Konto SYSTEM dieses Computers verwenden (Standard)) aktiviert.
6. Klicken Sie zuerst auf **Anwenden** und dann auf **Schließen**.
7. Wechseln Sie zurück zum Azure-Portal (**Intune** > **Gerätekonfiguration** > **Zertifizierungsstelle**). Nach einigen Minuten wird ein grünes Häkchen angezeigt und der **Verbindungsstatus** ist **Aktiv**. Ihr Connectorserver kann jetzt mit Intune kommunizieren.

## <a name="create-a-device-configuration-profile"></a>Erstellen eines Gerätekonfigurationsprofils

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Gehen Sie zu **Intune** > **Gerätekonfiguration** > **Profile**, und klicken Sie auf **Profil erstellen**.

   ![NavigateIntune][NavigateIntune]

3. Geben Sie die folgenden Eigenschaften ein:
   * **Name** für das Profil
   * Optional eine Beschreibung
   * **Plattform**, auf der das Profil bereitgestellt werden soll
   * Für **Profiltyp** die Option **Vertrauenswürdiges Zertifikat**

4. Gehen Sie zu **Einstellungen**, und geben Sie die zuvor exportierte CER-Datei mit dem Zertifikat der Stammzertifizierungsstelle an.

   > [!NOTE]
   > Abhängig von der in **Schritt 3** ausgewählten Plattform besitzen Sie möglicherweise die Option zum Auswählen des **Zielspeichers** für das Zertifikat.

   ![ProfileSettings][ProfileSettings]

5. Klicken Sie auf **OK** und dann auf **Erstellen**, um Ihr Profil zu speichern.
6. Informationen zum Zuweisen des neuen Profils zu einem oder mehreren Geräten finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Erstellen eines PKCS-Zertifikatprofils

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Gehen Sie zu **Intune** > **Gerätekonfiguration** > **Profile**, und klicken Sie auf **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:
   * **Name** für das Profil
   * Optional eine Beschreibung
   * **Plattform**, auf der das Profil bereitgestellt werden soll
   * Für **Profiltyp** die Option **PKCS-Zertifikat**
4. Gehen Sie zu **Einstellungen**, und geben Sie die folgenden Eigenschaften ein:
   * **Erneuerungsschwellenwert (%)**: Empfohlen wird ein Wert von 20 %.
   * **Gültigkeitsdauer des Zertifikats:** Wenn Sie die Zertifikatvorlage nicht geändert haben, ist diese Option auf ein Jahr festgelegt.
   * **Zertifizierungsstelle:** Zeigt den internen vollqualifizierten Domänennamen (FQDN) Ihrer Unternehmenszertifizierungsstelle an.
   * **Name der Zertifizierungsstelle:** Gibt den Namen Ihrer Unternehmenszertifizierungsstelle an, der sich ggf. vom vorherigen Element unterscheidet.
   * **Name der Zertifikatvorlage:** Der Name der zuvor erstellten Vorlage. Beachten Sie, dass der **Vorlagenname** standardmäßig dem **Vorlagenanzeigenamen** *ohne Leerzeichen* entspricht.
   * **Format des Antragstellernamens**: Legen Sie diese Option auf **Allgemeiner Name** fest, sofern kein anderes Format erforderlich ist.
   * **Alternativer Antragstellername**: Legen Sie diese Option auf **Benutzerprinzipalname (UPN)** fest, sofern nichts anderes erforderlich ist.
   * **Erweiterte Schlüsselverwendung:** Sofern Sie im vorherigen Abschnitt [Konfigurieren von Zertifikatvorlagen für die Zertifizierungsstelle](#configure-certificate-templates-on-the-certification-authority) für Schritt 10 die Standardeinstellungen verwendet haben, fügen Sie aus dem Auswahlfeld die folgenden **vordefinierten Werte** hinzu:
      * **Verwendung für beliebigen Zweck**
      * **Clientauthentifizierung**
      * **Sichere E-Mail**
   * **Stammzertifikat** (für Android-Profile): Gibt die CER-Datei an, die in Schritt 3 im Abschnitt [Exportieren des Stammzertifikats aus der Unternehmenszertifizierungsstelle](#export-the-root-certificate-from-the-enterprise-ca) exportiert wurde.

5. Klicken Sie zuerst auf **OK** und dann auf **Erstellen**, um Ihr Profil zu speichern.
6. Informationen zum Zuweisen des neuen Profils zu einem oder mehreren Geräten finden Sie im Artikel [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Im Azure-Portal zu Intune navigieren und ein neues Profil für ein vertrauenswürdiges Zertifikat erstellen"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Profil erstellen und ein vertrauenswürdiges Zertifikat hochladen"
[ConnectorDownload]: ./media/certificates-download-connector.png "Certificate Connector aus dem Azure-Portal herunterladen"  
