---
title: Querladen von Windows- und Windows Phone-Apps für Intune
description: Erfahren Sie, wie Sie branchenspezifische Apps signieren, um sie mit Intune bereitstellen zu können.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
ms.custom: intune-classic
ms.openlocfilehash: 617ff6c9c244d4bc38f1ee345f4df39965eaf037
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223921"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signieren Sie branchenspezifische Apps, damit sie mit Intune auf Windows-Geräten bereitgestellt werden können

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Als Intune-Administrator können Sie branchenspezifische Apps – einschließlich der Unternehmensportal-App – auf Windows- und Windows 10 Mobile-Geräten bereitstellen. Um APPX- oder XAP-Apps auf Windows 10- und Windows 10 Mobile-Geräten oder beliebige branchenspezifische App auf Windows 8.1- oder Windows Phone 8.1-Geräten bereitzustellen, müssen Sie ein **Symantec Enterprise Mobile Code Signing-Zertifikat** erwerben. Nur das Symantec-Zertifikat wird für diese Apps auf den jeweiligen Windows-Geräten als vertrauenswürdig eingestuft. Für Windows 10-Apps und universelle Apps können Sie Ihre eigene Zertifizierungsstelle verwenden. Dieses Zertifikat ist für folgende Zwecke erforderlich:

-   Signieren der Unternehmensportal-App für die Bereitstellung auf Windows-PCs, Windows 10 Mobile- und Windows Phone-Geräten

-   Signieren von branchenspezifischen Apps eines Unternehmens, damit sie über Intune für Windows-Geräte bereitgestellt werden können

Mithilfe der folgenden Schritte können Sie das erforderliche Zertifikat bereitstellen und die Apps signieren. Sie müssen sich als Microsoft-Entwickler registrieren und dann ein Symantec-Zertifikat erwerben.


1. **Registrieren als Microsoft-Entwickler**<br>
   [Registrieren Sie sich als Microsoft-Entwickler](http://go.microsoft.com/fwlink/?LinkId=268442), indem Sie die Unternehmenskontodaten nutzen, die Sie bei der Anmeldung zum Erwerb Ihres Unternehmenskontos verwendet haben. Diese Anforderung muss von einem Mitglied der Geschäftsleitung autorisiert werden, bevor Sie ein Codesignaturzertifikat erhalten.

2. **Beziehen eines Symantec-Zertifikats für Unternehmen**<br>
  Erwerben Sie unter Verwendung Ihrer Symantec-ID ein Zertifikat von der [Symantec-Website](http://go.microsoft.com/fwlink/?LinkId=268441) . Nach dem Kauf des Zertifikats erhält die genehmigende Person in Ihrem Unternehmen, die Sie bei der Registrierung als Microsoft-Entwickler bestimmt haben, eine E-Mail, in der die Genehmigung der Zertifikatanforderung angefordert wird. Weitere Informationen zu den Anforderungen des Symantec-Zertifikats finden Sie unter [Warum ist für Windows Phone ein Symantec-Zertifikat erforderlich?](https://technet.microsoft.com/library/dn764959.aspx#BKMK_Symantec) in den häufig gestellten Fragen zur Windows-Geräteregistrierung.

3.  **Importieren von Zertifikaten**<br>
    Nachdem die Anforderung genehmigt wurde, erhalten Sie eine E-Mail mit Anweisungen zum Importieren von Zertifikaten. Führen Sie die Anweisungen in der E-Mail aus, um die Zertifikate zu importieren.

4.  **Überprüfen der importierten Zertifikate**<br>
    Zum Überprüfen, ob die Zertifikate ordnungsgemäß importiert wurden, navigieren Sie zum Snap-In **Zertifikate**, klicken mit der rechten Maustaste auf **Zertifikate** und klicken dann auf **Zertifikate suchen**. Geben Sie „Symantec“ in das Feld **Enthält** ein, und klicken Sie auf **Jetzt suchen**. Die importierten Zertifikate werden in den Ergebnissen angezeigt.

    ![Suchen des Symantec-Zertifikats](./media/wit.gif)

5. **Exportieren eines Signaturzertifikats**<br>
    Wenn Sie überprüft haben, dass die Zertifikate vorhanden sind, können Sie die PFX-Datei exportieren, um das Unternehmensportal zu signieren. Wählen Sie das Symantec-Zertifikat mit **Beabsichtigter Zweck** "Codesignatur" aus. Klicken Sie mit der rechten Maustaste auf das Codesignaturzertifikat, und wählen Sie **Exportieren** aus.

    ![Exportieren des Signaturzertifikats](./media/wit-walk-cert2.gif)

    Wählen Sie im **Assistenten zum Exportieren von Zertifikaten**die Option **Ja, privaten Schlüssel exportieren** aus, und klicken Sie dann auf **Weiter**. Wählen Sie die Option **Privater Informationsaustausch –PKCS #12 (.PFX)** aus, und aktivieren Sie das Kontrollkästchen **Möglichst alle Zertifikate im Zertifizierungspfad berücksichtigen**. Schließen Sie den Assistenten ab. Weitere Informationen finden Sie unter [Exportieren eines Zertifikats mit dem privaten Schlüssel](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Hochladen der App in Intune**<br>
    Laden Sie die signierte App-Datei und Ihr Codesignaturzertifikat hoch, um die App den Endbenutzern zur Verfügung zu stellen.

    1.  Klicken Sie im Azure-Portal auf **Verwaltung** &gt; **Windows Phone**.

    2.  Klicken Sie auf **Signierte App-Datei hochladen**, und melden Sie sich mit Ihrer Intune-Administrator-ID an.

    3.  Fügen Sie die Zertifikatdatei (.pfx) hinzu, die Sie in das **Codesignaturzertifikat** exportiert haben, und erstellen Sie ein Kennwort für das Zertifikat.

    4.  Schließen Sie den Assistenten ab.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Beispiel: Herunterladen, Signieren und Bereitstellen der Unternehmensportal-App für Windows-Geräte

Sie können die Unternehmensportal-App mit Intune auf Windows-Geräten (Windows Phone- und Windows 10 Mobile-Geräte eingeschlossen) bereitstellen, statt sie über den Microsoft Store zu installieren. Sie müssen hierzu die Unternehmensportal-App herunterladen und mit Ihrem Zertifikat signieren.  Dies ist nur erforderlich, wenn Ihre Benutzer nicht den Store des Unternehmens verwenden und Sie das Unternehmensportal für Windows Phone 8.1-Geräte bereitstellen möchten.


1.  **Herunterladen des Unternehmensportals**

    Um die Unternehmensportal-App mit Intune bereitzustellen, können Sie die [Microsoft Intune-Unternehmensportal-App für Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) aus dem Download Center herunterladen und die selbstextrahierende Datei (.exe) ausführen. Diese Datei enthält zwei Dateien:

    -   CompanyPortal.appx: Die Installations-App des Unternehmensportals für Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1: Ein PowerShell-Skript, das Sie verwenden können, um die Unternehmensportal-App-Datei zu signieren, sodass sie für Windows Phone 8.1-Geräte bereitgestellt werden kann

    Alternativ können Sie das Windows Phone 8.1-Unternehmensportal (offline lizenziertes Paket) oder das Windows 10-Unternehmensportal (offline lizenziertes Paket) aus dem [Microsoft Store für Unternehmen](http://businessstore.microsoft.com/) herunterladen. Die Unternehmensportal-App muss mit einer Offlinelizenz und dem geeigneten Paket zur Offlineverwendung erworben werden. Einträge für die Plattformen Windows 8 und Windows Phone 8 in der Auswahl beziehen sich auf die entsprechenden 8.1-Komponenten. Weitere Informationen, wie Sie dies in Intune ausführen, finden Sie unter [Verwalten von Apps, die im Microsoft Store für Unternehmen erworben wurden](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune).

2.  **Herunterladen des Windows Phone SDK** Laden Sie das Windows Phone SDK 8.0 (http://go.microsoft.com/fwlink/?LinkId=615570)) herunter, und installieren Sie es auf Ihrem Computer. Dieses SDK ist erforderlich, um ein Anwendungsregistrierungstoken zu generieren.

3.  **Generieren einer AETX-Datei** Generieren Sie aus der Symantec PFX-Datei eine Anwendungsregistrierungstoken-Datei (.aetx) mithilfe von AETGenerator.exe. Dieses Tool ist Teil von Windows Phone SDK 8.0. Eine Anleitung zum Erstellen einer AETX-Datei finden Sie im Abschnitt über das [Generieren eines Anwendungsregistrierungstokens für Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx).

4.  **Herunterladen des Windows SDK für Windows 8.1** Laden Sie das [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525) herunter (http://go.microsoft.com/fwlink/?LinkId=613525)), und installieren Sie es. Beachten Sie, dass das in der Unternehmensportal-App verwendete PowerShell-Skript den Standardinstallationsort `${env:ProgramFiles(x86)}\Windows Kits\8.1`nutzt. Wenn Sie die App an einem anderen Ort installieren möchten, beziehen Sie den Speicherort in einem Cmdlet-Parameter ein.

5.  **Codesignieren der App mithilfe von PowerShell** Öffnen Sie als Administrator **Windows PowerShell** auf dem Hostcomputer, auf dem Windows SDK mit dem Symantec Enterprise Mobile Code Signing Certificate installiert wurde. Navigieren Sie zur Datei „Sign-WinPhoneCompanyPortal.ps1“, und führen Sie das Skript aus.

    **Beispiel 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    In diesem Beispiel wird die Datei "CompanyPortal.appx" unter "C:\temp\" signiert und die Datei "CompanyPortalEnterpriseSigned.appx" erstellt. Das PFX-Kennwort "1234" wird verwendet und die Herausgeber-ID wird aus der PFX-Datei gelesen. Die Unternehmens-ID wird aus der Datei "cert.aetx" gelesen.

    **Beispiel 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    In diesem Beispiel wird die Datei "CompanyPortal.appx" unter "C:\temp\" signiert und die Datei "CompanyPortalEnterpriseSigned.appx" erstellt. Das PFX-Kennwort "1234" und die festgelegte Herausgeber-ID werden verwendet.

    **Parameter:**

    -   `-InputAppx` : Der lokale Pfad zur Datei "CompanyPortal.appx" in einfachen Anführungszeichen. Beispiel: 'C:\temp\CompanyPortal.appx'

    -   `-OutputAppx` : Der lokale Pfad und Dateiname für die signierte Unternehmensportal-App in einfachen Anführungszeichen. Beispiel: 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` : Der lokale Pfad und Dateiname für die exportierte PFX-Datei mit dem Symantec-Zertifikat. Beispiel: 'C:\signing\cert.pfx'

    -   `-PfxPassword` : Das Kennwort, das zum Signieren der PFX-Datei verwendet wird, in einfachen Anführungszeichen. Beispiel: '1234'

    -   `-AetxPath` : Der lokale Pfad zur AETX-Datei, die zum Lesen der Unternehmens-ID verwendet wird, wenn das Argument "EnterpriseId" nicht definiert ist. Dieses Argument oder EnterpriseId muss angegeben werden. Beispiel: 'C:\signing\cert.aetx'

    -   `-PublisherId`: Die Herausgeber-ID des Unternehmens. Wenn sie nicht vorhanden ist, wird das Feld "Subject" von Symantec Enterprise Mobile Code Signing Certificate verwendet. Beispiel: 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1'

    -   `-SdkPath`: Der Pfad zum Stammordner des Windows SDK für Windows 8.1. Dieses Argument ist optional und wird standardmäßig auf "${env:ProgramFiles(x86)}\Windows Kits\8.1" gesetzt.

    -   `-EnterpriseId`: Die Unternehmens-ID. Dieses Argument oder "AetxPath" muss angegeben werden. Wenn dieses Argument nicht angegeben ist, wird die Unternehmens-ID aus der AETX-Datei gelesen. Beispiel: 1000000001

6.  Stellen Sie die Unternehmensportal-App (SSP.appx) für Windows Phone 8.1 bereit. Eine Anleitung finden Sie unter [Informationen zum Hinzufügen branchenspezifischer Windows Phone-Apps](lob-apps-windows-phone.md) ([klassisches Portal](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>So wird das Symantec-Codesignaturzertifikat erneuert

Das zur Bereitstellung von mobilen Windows- und Windows Phone-Geräten verwendete Symantec-Zertifikat muss regelmäßig verlängert werden.

1.  Suchen Sie nach einer Erneuerungs-E-Mail, die ungefähr 14 Tage vor Ablauf des Zertifikats von Symantec gesendet wurde. Diese E-Mail enthält Anweisungen von Symantec zum Erneuern des Zertifikats für Ihr Unternehmen.

    Weitere Informationen zu Symantec-Zertifikaten erhalten Sie unter [www.symantec.com](http://www.symantec.com) oder telefonisch unter 1-877-438-8776 oder + 1-650-426-3400.

2.  Navigieren Sie zur Website (Beispiel: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)), und melden Sie sich mit der Symantec Herausgeber-ID und der E-Mail-Adresse an, die mit dem Zertifikat verknüpft ist. Denken Sie daran, den gleichen Computer für das Starten der Erneuerung zu verwenden, den Sie auch zum Herunterladen des Zertifikats verwenden werden.

3.  Sobald die Erneuerung genehmigt und bezahlt wurde, können Sie das Zertifikat herunterladen.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Installieren des aktualisierten Zertifikats für branchenspezifische Apps

1.  Signieren Sie die neueste Version Ihrer branchenspezifischen App.

2.  Öffnen Sie das Azure-Portal, wechseln Sie zu **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **Windows Phone**, und klicken Sie auf **Signierte App hochladen**.

3.  Laden Sie das neu signierte Unternehmensportal hoch. Sie benötigen die neu signierte SSP.XAP-Datei und die neue PFX-Datei, die Sie von Symantec erhalten, oder das Anwendungsregistrierungstoken, das mit dieser neuen PFX-Datei erstellt wurde.

4.  Wenn das Hochladen abgeschlossen ist, entfernen Sie die alte Version des Unternehmensportals im Arbeitsbereich **Software**.

5.  Signieren Sie alle neuen und aktualisierten Unternehmens-Apps unter Verwendung des neuen Zertifikats. Vorhandene Anwendungen müssen nicht erneut signiert und erneut bereitgestellt werden.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Manuelles Bereitstellen der Windows 10-Unternehmensportal-App
Sie können die Windows 10-Unternehmensportal-App manuell direkt über Intune bereitstellen. Das funktioniert auch, wenn Intune nicht in den Microsoft Store für Unternehmen integriert wurde.

 > [!NOTE]
 > Bei dieser Option müssen ggf. veröffentlichte App-Updates manuell bereitgestellt werden.

1. Melden Sie sich bei Ihrem Konto im [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store) an, und beziehen Sie die **Offlinelizenzversion** der Unternehmensportal-App.  
2. Wenn Sie über die App verfügen, wählen Sie sie auf der Seite **Inventory** (Bestand) aus.  
3. Wählen Sie unter **Plattform** die Option **Windows 10 all devices** (Windows 10: alle Geräte) sowie die passende **Architektur** aus, und starten Sie den Downloadvorgang. Für diese App wird keine App-Lizenzdatei benötigt.
![Abbildung mit Details zum Downloadpaket für „Windows 10 all devices“ (Windows 10: alle Geräte) und x86-Architektur](./media/Win10CP-all-devices.png)
4. Laden Sie alle Pakete unter „Erforderliche Frameworks“ herunter. Dieser Schritt muss für die x86-, x64- und ARM-Architektur ausgeführt werden. Dadurch ergeben sich insgesamt neun Pakete, wie im Anschluss zu sehen.

![Abbildung mit den herunterzuladenden Abhängigkeitsdateien ](./media/Win10CP-dependent-files.png)
5. Erstellen Sie einen Ordner (beispielsweise „C:&#92;Company Portal“), bevor Sie die Unternehmensportal-App in Intune hochladen, und strukturieren Sie die Pakete wie folgt:
   1. Platzieren Sie das Unternehmensportal-Paket im Ordner „C:\Company Portal“. Erstellen Sie dort auch einen Unterordner namens „Dependencies“.  
   ![Abbildung mit dem Ordner „Dependencies“ und der APPXBUN-Datei](./media/Win10CP-Dependencies-save.png)
   2. Platzieren Sie die neun Abhängigkeitspakete im Ordner „Dependencies“.  
   Sind die Abhängigkeiten nicht wie hier beschrieben strukturiert, werden sie von Intune nicht erkannt und nicht hochgeladen. In diesem Fall tritt der folgende Fehler auf:  
   ![Die Windows App-Abhängigkeit für dieses Softwareinstallationsprogramm wurde im Anwendungsordner nicht gefunden. Sie können diese Anwendung weiterhin erstellen und bereitstellen. Sie können sie jedoch nicht ausführen, bis die fehlende Windows App-Abhängigkeit bereitgestellt wird.](./media/Win10CP-error-message.png)
6. Kehren Sie zu Intune zurück, und laden Sie die Unternehmensportal-App als neue App hoch. Stellen Sie sie als erforderliche App für die gewünschte Gruppe von Zielbenutzern bereit.  

Weitere Informationen zur Behandlung von Abhängigkeiten für universelle Apps durch Intune finden Sie unter [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Bereitstellen einer APPXBUNDLE-Datei mit Abhängigkeiten über Microsoft Intune MDM).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Wie aktualisiere ich das Unternehmensportal auf den Geräten meiner Benutzer, wenn diese bereits die älteren Apps aus dem Store installiert haben?
Falls Ihre Benutzer bereits die Unternehmensportal-App für Windows 8.1 oder Windows Phone 8.1 aus dem Store installiert haben, sollte diese automatisch auf die neue Version aktualisiert werden, ohne dass Sie oder Ihre Benutzer dazu aktiv werden müssen. Sollte die Aktualisierung nicht erfolgen, fordern Sie die Benutzer auf, sich zu vergewissern, dass sie auf ihren Geräten automatische Updates für Store-Apps aktiviert haben.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner quergeladenen Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Wir empfehlen für die Migration die folgende Vorgehensweise: Legen Sie die Bereitstellungsaktion auf „Deinstallieren“ fest, um die Bereitstellung der Windows 8.1-Unternehmensportal-App zu löschen. Anschließend kann die Windows 10-Unternehmensportal-App mit einer der oben genannten Optionen bereitgestellt werden.  

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal bereitgestellt haben, ohne es mit dem Symantec-Zertifikat zu signieren, führen Sie zur Durchführung des Upgrades die Schritte aus, die weiter oben im Abschnitt zur direkten Bereitstellung über Intune beschrieben sind.

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal mit dem Symantec-Codesignaturzertifikat bereitgestellt und signiert haben, führen Sie die Schritte des folgenden Abschnitts aus.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner signierten quergeladenen Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Wir empfehlen für die Migration die folgende Vorgehensweise: Legen Sie die Bereitstellungsaktion auf „Deinstallieren“ fest, um die vorhandene Bereitstellung der Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App zu löschen. Anschließend kann die Windows 10-Unternehmensportal-App ganz normal bereitgestellt werden.  

Andernfalls muss die Windows 10-Unternehmensportal-App entsprechend aktualisiert und signiert werden, um sicherzustellen, dass der Upgradepfad eingehalten wird.  

Wenn die Windows 10-Unternehmensportal-App auf diese Weise signiert und bereitgestellt wird, müssen Sie diesen Prozess für jedes neue App-Update wiederholen, das im Store verfügbar wird. Die App wird nicht automatisch aktualisiert, wenn der Store aktualisiert wird.  

Im Anschluss erfahren Sie, wie Sie die App auf diese Weise signieren und bereitstellen:

1. Laden Sie unter [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) das Microsoft Intune-Signierungsskript für die Windows 10-Unternehmensportal-App herunter.  Für dieses Skript muss das Windows SDK für Windows 10 auf dem Hostcomputer installiert sein. Besuchen Sie die Seite [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296), um das Windows SDK für Windows 10 herunterzuladen.
2. Laden Sie die Windows 10-Unternehmensportal-App wie weiter oben beschrieben aus dem Microsoft Store für Unternehmen herunter.  
3. Führen Sie das Skript mit den im Skriptheader angegebenen Eingabeparametern aus, um die Windows 10-Unternehmensportal-App zu signieren (siehe Auszug weiter unten). An das Skript müssen keine Abhängigkeiten übergeben werden. Diese sind nur erforderlich, wenn die App in die Intune-Verwaltungskonsole hochgeladen wird.

|       Parameter       |                                                                    Beschreibung                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Der Pfad, an dem sich die APPXBUNDLE-Quelldatei befindet.                                              |
| OutputWin10AppxBundle |                                                  Der Ausgabepfad für die signierte APPXBUNDLE-Datei.                                                  |
|       Win81Appx       |                          Der Pfad, an dem sich die APPX-Datei des Windows 8.1- oder Windows Phone 8.1-Unternehmensportals befindet.                           |
|      PfxFilePath      |                                   Der Pfad der PFX-Datei für das Symantec Enterprise Mobile-Codesignaturzertifikat.                                    |
|      PfxPassword      |                                     Das Kennwort des Symantec Enterprise Mobile-Codesignaturzertifikats.                                      |
|      PublisherId      |      Die Herausgeber-ID des Unternehmens. Wenn sie nicht vorhanden ist, wird das Feld "Subject" von Symantec Enterprise Mobile Code Signing Certificate verwendet.       |
|        SdkPath        | Der Pfad des Stammordners für das Windows SDK für Windows 10. Dieses Argument ist optional und wird standardmäßig auf „${env:ProgramFiles(x86)}\Windows Kits\10“ festgelegt. |

Das Skript gibt nach der Ausführung die signierte Version der Windows 10-Unternehmensportal-App aus. Anschließend können Sie die signierte Version der Anwendung über Intune als branchenspezifische App bereitstellen. Dadurch wird für die derzeit bereitstellten Versionen ein Upgrade auf die neue App durchgeführt.  
