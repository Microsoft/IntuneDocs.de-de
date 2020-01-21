---
title: Behandlung von Problemen bei der Windows-Geräteregistrierung in Microsoft Intune
titleSuffix: Microsoft Intune
description: Vorschläge zur Behebung einiger der häufigsten Probleme beim Registrieren von Windows-Geräten in InTune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d5c6db598a7f64f75f6f5a8e0cf25b8e4b81465
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885894"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Behandeln von Problemen bei der Windows-Geräteregistrierung in Microsoft Intune

In diesem Artikel werden InTune-Administratoren beim Anmelden von Windows-Geräten in InTune unterstützt.

## <a name="prerequisites"></a>Voraussetzungen
Bevor Sie mit der Problembehandlung beginnen, ist es wichtig, einige grundlegende Informationen zu sammeln. Diese Informationen können Ihnen helfen, das Problem besser zu verstehen und die Zeit für die Suche nach einer Lösung zu verkürzen.

Sammeln Sie die folgenden Informationen zum Problem:
- Ist eine gültige InTune-Lizenz dem Benutzer zugewiesen? Bevor Benutzer ihre Geräte registrieren können, müssen ihnen die nötigen Lizenzen zugewiesen werden.
- Ist das neueste Update auf dem Windows-Gerät installiert? Einige Features in InTune funktionieren nur mit der neuesten Version von Windows. Es gibt viele Korrekturen für bekannte Probleme, die durch Windows Update verfügbar sind. Wenn Sie alle aktuellen Updates anwenden, wird häufig ein Problem mit der Registrierung von Windows-Geräten behoben. 
- Wie lautet die genaue Fehlermeldung?
- Wo wird die Fehlermeldung angezeigt?
- Wann fing das Problem an? Hat die Registrierung jemals funktioniert? 
- Welche Plattform (Android, Ios, Windows) hat das Problem?
- Wie viele Benutzer sind betroffen? Sind alle Benutzer betroffen oder nur einige?
- Wie viele Geräte sind betroffen? Sind alle Geräte betroffen oder nur einige?
- Was ist die MDM-Autorität?
- Wie wird die Registrierung durchgeführt? Handelt es sich um ein "Bring your own Device" (BYOD) oder Apple Programm zur Geräteregistrierung (DEP) mit Registrierungs Profilen?

## <a name="error-messages"></a>Fehlermeldungen

### <a name="this-user-is-not-authorized-to-enroll"></a>Dieser Benutzer ist nicht autorisiert, sich anzumelden.

Fehler 0x801c003: "dieser Benutzer ist nicht autorisiert, sich anzumelden. Versuchen Sie es erneut, oder wenden Sie sich mit dem Fehlercode (0x801c0003) an den Systemadministrator. "
Fehler 80180003: „Es ist ein Problem aufgetreten. Dieser Benutzer ist nicht autorisiert, sich anzumelden. Versuchen Sie es erneut, oder wenden Sie sich mit dem Fehlercode 80180003 an den Systemadministrator. "

**Ursache**: Jede der folgenden Bedingungen: 

- Der Benutzer hat bereits die maximal zulässige Anzahl von Geräten in InTune registriert.    
- Das Gerät wird durch die Gerätetyp Einschränkungen blockiert.    
- Auf dem Computer wird Windows 10 Home ausgeführt. Allerdings wird die Anmeldung bei InTune oder beim beitreten Azure AD nur für die Editionen Windows 10 pro und höher unterstützt.

#### <a name="resolution"></a>Lösung
Für dieses Problem gibt es mehrere mögliche Lösungen:

##### <a name="remove-devices-that-were-enrolled"></a>Registrierte Geräte entfernen
1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.    
2. Wechseln Sie zu **Benutzer** > **alle Benutzer**.    
3. Wählen Sie das betroffene Benutzerkonto aus, und klicken Sie dann auf **Geräte**.    
4. Wählen Sie nicht verwendete oder unerwünschte Geräte aus, und klicken Sie dann auf **Löschen**. 

##### <a name="increase-the-device-enrollment-limit"></a>Erhöhen des Grenzwerts für die Geräteregistrierung

> [!NOTE]
> Diese Methode erhöht den Grenzwert für die Geräteregistrierung für alle Benutzer, nicht nur für den betroffenen Benutzer.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wechseln Sie zu **Geräte** > Registrierungs **Beschränkungen** > **Standardeinstellung** (unter Beschränkungen für das **Geräte Limit**) > **Eigenschaften** > **Bearbeiten** (neben **Geräte Limit**) > erhöhen Sie das **Geräte Limit** (maximal 15) > **Überprüfung und speichern**.    
 

##### <a name="check-device-type-restrictions"></a>Überprüfen der Gerätetypbeschränkungen
1. Melden Sie sich mit einem globalen Administrator Konto beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wechseln Sie zu **Geräte** > Registrierungs **Beschränkungen**, und wählen Sie dann die **Standard** Einschränkung unter **Gerätetyp Einschränkungen**aus.    
3. Wählen Sie **Plattformen**und dann **zulassen** für **Windows (MDM)** aus.

    > [!IMPORTANT]
    > Wenn die aktuelle **Einstellung bereits zulässig**ist, ändern Sie Sie in **blockieren**, speichern Sie die Einstellung, und ändern Sie Sie zurück, um die Einstellung erneut **zuzulassen** und zu speichern. Dadurch wird die Registrierungs Einstellung zurückgesetzt.

4. Warten Sie ca. 15 Minuten, und melden Sie das betroffene Gerät dann erneut an.    

##### <a name="upgrade-windows-10-home"></a>Upgrade auf Windows 10 Home
[Aktualisieren Sie Windows 10 Home auf Windows 10 pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) oder eine höhere Edition. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Dieser Benutzer darf sich nicht registrieren.

Fehler 0x801c0003: "dieser Benutzer darf nicht registriert werden. Versuchen Sie es noch mal, oder wenden Sie sich mit dem Fehlercode 801c0003 an den Systemadministrator.

**Ursache:** Die **Benutzer können Geräte zu Azure AD** die Einstellung ist auf **keine**festgelegt. Dadurch wird verhindert, dass neue Benutzer ihre Geräte zu Azure AD hinzufügen. Daher tritt bei der InTune-Registrierung ein Fehler auf.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) als Administrator an.    
2. Wechseln Sie zu **Azure Active Directory** > **Geräte** > Geräte **Einstellungen**.    
3. Legen Sie **Benutzer dürfen Geräte in Azure AD einbinden** auf **Alle** fest.    
4. Registrieren Sie das Gerät erneut.   

### <a name="the-device-is-already-enrolled"></a>Das Gerät ist bereits registriert.

Fehler 8018000a: "etwas ist schief gelaufen. Das Gerät ist bereits registriert.  Wenden Sie sich mit dem Fehlercode 8018000a an Ihren Systemadministrator.

**Ursache**: Eine der folgenden Bedingungen ist erfüllt:
- Ein anderer Benutzer hat das Gerät bereits in InTune registriert oder dem Gerät hinzugefügt, um Azure AD. Um zu ermitteln, ob dies der Fall ist, wechseln Sie zu **Einstellungen** > **Konten** > **Arbeits Zugriff**. Suchen Sie nach einer Meldung, die der folgenden Meldung ähnelt: "ein anderer Benutzer im System ist bereits mit einer Arbeit oder Schule verbunden. Entfernen Sie diese Arbeits-oder Schul Verbindung, und wiederholen Sie den Vorgang. "    

#### <a name="resolution"></a>Lösung

Nutzen Sie eines der folgenden Verfahren, um dieses Problem zu beheben:

##### <a name="remove-the-other-work-or-school-account"></a>Anderes Geschäfts-, Schul-oder unikonto entfernen
1. Melden Sie sich von Windows ab, und melden Sie sich dann mit dem anderen Konto an, das registriert oder dem Gerät beigetreten ist.    
2. Wechseln Sie zu **Einstellungen** > **Konten** > **Arbeits Zugriff**, und entfernen Sie dann das Geschäfts-, Schul-oder unikonto.
3. Melden Sie sich von Windows ab, und melden Sie sich dann mit Ihrem Konto an.    
4. Registrieren Sie das Gerät bei InTune, oder fügen Sie das Gerät zu Azure AD hinzu. 



### <a name="this-account-is-not-allowed-on-this-phone"></a>Dieses Konto ist auf diesem Telefon nicht zulässig.

Fehler: "dieses Konto ist auf diesem Telefon nicht zulässig. Stellen Sie sicher, dass die von Ihnen angegebenen Informationen korrekt sind, und versuchen Sie es dann erneut, oder fordern Sie Unterstützung von Ihrem Unternehmen

**Ursache:** Der Benutzer, der versucht hat, das Gerät zu registrieren, verfügt über keine gültige InTune-Lizenz.

#### <a name="resolution"></a>Lösung
Weisen Sie dem Benutzer eine gültige InTune-Lizenz zu, und registrieren Sie das Gerät.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Der Endpunkt für die MDM-Nutzungsbedingungen ist anscheinend nicht ordnungsgemäß konfiguriert.

**Ursache**: Eine der folgenden Bedingungen ist erfüllt: 
 - Sie verwenden die Mobile Geräteverwaltung (Mobile Device Management, MDM) für Office 365 und InTune für den Mandanten, und der Benutzer, der versucht, das Gerät zu registrieren, verfügt nicht über eine gültige InTune-Lizenz oder eine Office 365-Lizenz.     
- Die MDM-Nutzungsbedingungen in Azure AD sind leer oder enthalten nicht die richtige URL.    

#### <a name="resolution"></a>Lösung

Verwenden Sie eine der folgenden Methoden, um dieses Problem zu beheben: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Zuweisen einer gültigen Lizenz zum Benutzer
Wechseln Sie zum [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home), und weisen Sie dem Benutzer dann entweder eine InTune-oder eine Office 365-Lizenz zu.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Korrigieren Sie die URL für die MDM-Nutzungsbedingungen.
  1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und klicken Sie dann auf **Azure Active Directory**.    
  2. Wählen Sie **Mobilität (MDM und MAM)** aus, und klicken Sie dann auf **Microsoft InTune**.    
  3. Wählen Sie **MDM-Standard-URLs wiederherstellen**aus, vergewissern Sie sich, dass die **MDM-URL für Nutzungsbedingungen** auf **https://portal.manage.microsoft.com/TermsofUse.aspx** festgelegt    
  4. Wählen Sie **Speichern** aus.    


### <a name="something-went-wrong"></a>Es ist ein Problem aufgetreten.

Fehler 80180026: „Es ist ein Problem aufgetreten. Vergewissern Sie sich, dass Sie die richtigen Anmelde Informationen verwenden und dass Ihre Organisation dieses Feature verwendet. Versuchen Sie es erneut, oder wenden Sie sich mit dem Fehlercode 80180026 an den Systemadministrator. "

**Ursache:** Dieser Fehler kann auftreten, wenn Sie versuchen, einen Windows 10-Computer mit Azure AD zu verbinden, und die beiden folgenden Bedingungen zutreffen: 
- Die automatische MDM-Registrierung ist in Azure aktiviert.    
- Der InTune-PC-Client (InTune-PC-Agent) ist auf dem Windows 10-Computer installiert.

#### <a name="resolution"></a>Lösung
Nutzen Sie eines der folgenden Verfahren, um dieses Problem zu beheben:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Deaktivieren Sie die automatische MDM-Registrierung in Azure.
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.    
2. Wechseln Sie zu **Azure Active Directory** > **Mobility (MDM und MAM)**  > **Microsoft InTune**.    
3. Legen Sie den **MDM-Benutzerbereich** auf **None**fest, und klicken Sie dann auf **Speichern**.    
     
##### <a name="uninstall"></a>Deinstallieren
Deinstallieren Sie den InTune-PC-Client-Agent vom Computer.    

### <a name="the-software-cannot-be-installed"></a>Die Software kann nicht installiert werden.

Fehler: "die Software kann nicht installiert werden, 0x80cf4017."

**Ursache:** Die Client Software ist veraltet.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich bei [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) an.    
2. Wechseln Sie zu **Admin** > **Client Software Download**, und klicken Sie dann auf **Client Software herunterladen**.    
3. Speichern Sie das Installationspaket, und installieren Sie dann die-Client Software. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>Das Kontozertifikat ist ungültig und ist möglicherweise abgelaufen.

Fehler: „Das Kontozertifikat ist ungültig und ist möglicherweise abgelaufen, 0x80cf4017.“

**Ursache:** Die Client Software ist veraltet.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich bei [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) an.    
2. Wechseln Sie zu **Admin** > **Client Software Download**, und klicken Sie dann auf **Client Software herunterladen**.    
3. Speichern Sie das Installationspaket, und installieren Sie dann die-Client Software.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Diese Windows-Version wird von Ihrer Organisation nicht unterstützt. 

Fehler: "Es ist ein Problem aufgetreten. Diese Windows-Version wird von Ihrer Organisation nicht unterstützt.  (0x80180014) "

**Ursache:** Die Windows MDM-Registrierung ist in Ihrem InTune-Mandanten deaktiviert.

#### <a name="resolution"></a>Lösung
Um dieses Problem in einer eigenständigen InTune-Umgebung zu beheben, führen Sie die folgenden Schritte aus: 
 
1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) **Geräte** > Registrierungs **Beschränkungen** aus, > Wählen Sie eine Gerätetyp Einschränkung aus.    
2. Wählen Sie **Eigenschaften** > **Bearbeiten** (neben **Platt Form Einstellungen**) > **Windows (MDM)** **zulassen** .    
3. Klicken Sie auf **überprüfen und speichern**.    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Bei der Massen Registrierung ist ein Setup Fehler aufgetreten.

**Ursache:** Die Azure AD Benutzerkonten im Kontopaket (Package_GUID) für das jeweilige Bereitstellungs Paket dürfen Geräte nicht Azure AD hinzufügen. Diese Azure Ad Konten werden automatisch erstellt, wenn Sie ein Bereitstellungs Paket mit Windows Configuration Designer (WCD) oder der APP zum Einrichten von Schul-PCs einrichten. diese Konten werden dann verwendet, um die Geräte mit Azure AD zu verbinden.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) als Administrator an.    
2. Wechseln Sie zu **Azure Active Directory > Geräte > Geräteeinstellungen**.    
3. Legen Sie **Benutzer dürfen Geräte in Azure AD einbinden** auf **Alle** oder **Ausgewählte** fest.

   Wenn Sie **ausgewählt**auswählen, klicken Sie auf **ausgewählt**und dann auf **Mitglieder hinzufügen** , um alle Benutzer hinzuzufügen, die Ihre Geräte mit Azure AD verbinden können. Stellen Sie sicher, dass alle Azure Ad Konten für das Bereitstellungs Paket hinzugefügt werden.
 
Weitere Informationen zum Erstellen eines Bereitstellungs Pakets für Windows Configuration Designer finden Sie unter [Erstellen eines Bereitstellungs Pakets für Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Weitere Informationen zur App "Einrichtung von PCs" finden Sie unter [Verwenden der App "Einrichten der PCs-App](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app)".


### <a name="auto-mdm-enroll-failed"></a>Automatische MDM-Registrierung: Fehler 

Wenn Sie versuchen, ein Windows 10-Gerät automatisch mithilfe von Gruppenrichtlinie zu registrieren, treten folgende Probleme auf: 
- In Taskplaner ist unter **Microsoft** > **Windows** > **enterprisemgmt**das Ergebnis der letzten Ausführung des Zeitplans, der **vom Registrierungs Client für die automatische Registrierung bei MDM von Aad erstellt wurde** , wie folgt: **Ereignis 76 automatische MDM-Registrierung: Fehler (Unbekannter Win32-Fehlercode: 0x8018002b)**       
- In Ereignisanzeige wird das folgende Ereignis unter **Anwendungs-und Dienst Protokolle/Microsoft/Windows/Devicemanagement-Enterprise-Diagnostics-Provider/admin**protokolliert:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Ursache**: Eine der folgenden Bedingungen ist erfüllt: 
- Der UPN enthält eine nicht überprüfte oder nicht routingfähige Domäne wie z. B. .local (z. B. joe@contoso.local).    
- Der **MDM-Benutzerbereich** ist auf **Keine** festgelegt. 

#### <a name="resolution"></a>Lösung
Wenn der UPN eine nicht überprüfte oder nicht Routing fähige Domäne enthält, führen Sie die folgenden Schritte aus: 

1. Öffnen Sie auf dem Server, auf dem Active Directory Domain Services (AD DS) ausgeführt wird, **Active Directory Benutzer und Computer** , indem Sie **DSA. msc** im Dialogfeld **Ausführen** eingeben, und klicken Sie dann auf **OK**.    
2. Klicken Sie unter Ihrer Domäne auf **Benutzer** , und gehen Sie dann wie folgt vor:  
    - Wenn nur ein betroffener Benutzer vorhanden ist, klicken Sie mit der rechten Maustaste auf den Benutzer, und klicken Sie dann auf **Eigenschaften**. Wählen Sie auf der Registerkarte **Konto** in der Dropdown Liste UPN-Suffix unter **Benutzer Anmelde Name**ein gültiges UPN-Suffix aus, z. b. contoso.com, und klicken Sie dann auf **OK**.    
    - Wenn mehrere betroffene Benutzer vorhanden sind, wählen Sie die Benutzer aus, und klicken Sie im Menü **Aktion** auf **Eigenschaften**. Aktivieren Sie auf der Registerkarte **Konto** das Kontrollkästchen **UPN-Suffix** , wählen Sie in der Dropdown Liste ein gültiges UPN-Suffix aus, z. b. contoso.com, und klicken Sie dann auf **OK**.
3. Warten Sie die nächste Synchronisierung, oder erzwingen Sie eine Delta Synchronisierung vom Synchronisierungs Server, indem Sie die folgenden Befehle an einer PowerShell-Eingabeaufforderung mit erhöhten Rechten ausführen:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Wenn der **MDM-Benutzerbereich** auf **None**festgelegt ist, führen Sie die folgenden Schritte aus: 
 
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und klicken Sie dann auf **Azure Active Directory**.
2. Wählen Sie **Mobilität (MDM und MAM)** aus, und klicken Sie dann auf **Microsoft InTune**.    
3. Legen Sie den **MDM-Benutzerbereich** auf **alle**fest. Oder legen Sie den **MDM-Benutzerbereich** auf **einige**fest, und wählen Sie die Gruppen aus, die Ihre Windows 10-Geräte automatisch registrieren können.    
4. Legen Sie den **MAM-Benutzerbereich** auf **None**fest.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Fehler beim Erstellen des Autopilot-Profils.

**Ursache:** Das angegebene Benennungs Format der Gerätenamen Vorlage entspricht nicht den Anforderungen. Beispielsweise verwenden Sie Kleinbuchstaben für das serielle Makro, z. b .% Serial% anstelle von% Serial%.

#### <a name="resolution"></a>Lösung

Stellen Sie sicher, dass das Benennungs Format die folgenden Anforderungen erfüllt:

- Erstellen Sie einen eindeutigen Namen für Ihre Geräte. Namen dürfen höchstens 15 Zeichen lang sein und können Buchstaben (a-z, A-Z), Zahlen (0-9) und Bindestriche (-) enthalten.
- Ein Name darf nicht nur aus Zahlen bestehen.
- Namen dürfen keinen leeren Bereich enthalten.
- Verwenden Sie das %SERIAL%-Makro, um eine hardwarespezifische Seriennummer hinzuzufügen. Oder verwenden Sie die% Rand: < # der Ziffern >% Macro, um eine zufällige Zeichenfolge mit Zahlen hinzuzufügen. die Zeichenfolge enthält < Ziffern > Ziffern. Beispielsweise generiert MyPC-% Rand: 6% einen Namen wie z. b. MyPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Es ist ein Problem aufgetreten. OOBEIDPS.

**Ursache:** Dieses Problem tritt auf, wenn ein Proxy, eine Firewall oder ein anderes Netzwerkgerät vorhanden ist, das den Zugriff auf den Identitäts Anbieter (Identity Provider, IDP) blockiert.

#### <a name="resolution"></a>Lösung
Stellen Sie sicher, dass der erforderliche Zugriff auf internetbasierte Dienste für Autopilot nicht blockiert ist. Weitere Informationen finden Sie unter [Windows Autopilot-Netzwerk Anforderungen](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registrieren Ihres Geräts für die mobile Verwaltung (Fehler: 3, 0x801c03ea).

**Ursache:** Das Gerät verfügt über einen TPM-Chip, der Version 2,0 unterstützt, aber noch nicht auf Version 2,0 aktualisiert wurde.

#### <a name="resolution"></a>Lösung
Aktualisieren Sie den TPM-Chip auf Version 2,0.

Wenn das Problem weiterhin besteht, überprüfen Sie, ob sich das gleiche Gerät in zwei zugewiesenen Gruppen befindet, wobei jeder Gruppe ein anderes Autopilot-Profil zugewiesen wird. Wenn Sie sich in zwei Gruppen befinden, legen Sie fest, welches Autopilot-Profil auf das Gerät angewendet werden soll, und entfernen Sie dann die Zuweisung des anderen Profils.

Weitere Informationen zum Bereitstellen eines Windows-Geräts im Kiosk Modus mit Autopilot finden Sie unter Bereitstellen [eines Kiosks mithilfe von Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Sichern der Hardware (Fehler: 0x800705b4).

Fehler 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Ursache:** Das Windows-Ziel Gerät erfüllt nicht die folgenden Anforderungen:

- Das Gerät muss über einen physischen TPM 2,0-Chip verfügen. Geräte mit virtuellen TPMs (z. b. Hyper-V-VMS) oder TPM 1,2-Chips funktionieren nicht mit dem selbst Bereitstellungs Modus.
- Auf dem Gerät muss eine der folgenden Versionen von Windows ausgeführt werden:
    - Windows 10 Build 1703 oder eine höhere Version.
    - Wenn Azure AD Hybrid Join verwendet wird, ist Windows 10 Build 1809 oder eine höhere Version.


#### <a name="resolution"></a>Lösung
Stellen Sie sicher, dass das Zielgerät die Anforderungen erfüllt, die im Abschnitt " **Ursache** " beschrieben werden.

Weitere Informationen zum Bereitstellen eines Windows-Geräts im Kiosk Modus mit Autopilot finden Sie unter Bereitstellen [eines Kiosks mithilfe von Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Es ist ein Problem aufgetreten. Fehlercode 80070774.

Fehler 0x80070774: ein Fehler ist aufgetreten. Vergewissern Sie sich, dass Sie die richtigen Anmelde Informationen verwenden und dass Ihre Organisation dieses Feature verwendet. Versuchen Sie es erneut, oder wenden Sie sich mit dem Fehlercode 80070774 an den Systemadministrator.

Dieses Problem tritt normalerweise auf, bevor das Gerät in einem Azure AD Hybrid Autopilot-Szenario neu gestartet wird, wenn das Gerät während des ersten Anmeldebildschirms ein Timeout auftritt. Dies bedeutet, dass der Domänen Controller aufgrund von Konnektivitätsproblemen nicht gefunden oder erfolgreich erreicht werden kann. Oder dass sich das Gerät in einem Zustand befindet, der nicht der Domäne beitreten kann.

**Ursache:** Die häufigste Ursache ist, dass Azure AD Hybrid Join verwendet wird und die Funktion "Benutzer zuweisen" im Autopilot-Profil konfiguriert wird. Durch die Verwendung der Funktion "Benutzer zuweisen" wird während des ersten Anmeldebildschirms ein Azure AD Join auf dem Gerät durchführt, bei dem das Gerät in einen Zustand versetzt wird, in dem es nicht der lokalen Domäne beitreten kann. Aus diesem Grund sollte die Funktion "Benutzer zuweisen" nur in den Autopilot-Szenarios des Standard Azure AD verwendet werden.  Die Funktion sollte nicht in Azure AD Hybrid Join Szenarios verwendet werden.

#### <a name="resolution"></a>Lösung

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431)die Option > **Geräte** > **Windows** - > **Windows-Geräte**aus.
2. Wählen Sie das Gerät aus, auf dem das Problem auftritt, > Klicken Sie auf die Auslassungs Punkte (...) auf der rechten Seite.
3. Wählen Sie **Benutzer Zuweisung** aufheben aus, und warten Sie, bis der Prozess abgeschlossen ist.
4. Vergewissern Sie sich, dass das Azure AD Hybrid Autopilot-Profil zugewiesen wurde, bevor Sie den Versuch wiederholen.

#### <a name="second-resolution"></a>Zweite Auflösung
Wenn das Problem weiterhin auftritt, überprüfen Sie auf dem Server, der den InTune-Offline-Domänen Beitritt hostet, ob die Ereignis-ID 30312 innerhalb des ODJ-Connector-Dienst Protokolls protokolliert wird. Das Ereignis 30312 ähnelt dem folgenden:

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

Dieses Problem tritt normalerweise auf, wenn die Berechtigungen für die Organisationseinheit, in der die Windows Autopilot-Geräte erstellt werden, falsch delegiert werden. Weitere Informationen finden Sie unter [erhöhen des Computer Konto Limits in der Organisationseinheit](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Öffnen Sie **Active Directory-Benutzer und -Computer** („DSA.msc“).
2. Klicken Sie mit der rechten Maustaste auf die Organisationseinheit, mit der Sie die in Azure AD Hybrid eingebundenen Computer erstellen möchten, und wählen Sie **Objektverwaltung zuweisen** aus.
3. Wählen Sie im Assistenten zum Zuweisen der **Objektverwaltung** die Optionen **Weiter** > **Hinzufügen...**  > **Objekttypen** aus.
4. Aktivieren Sie im Bereich **Objekttypen** das Kontrollkästchen **Computer**, und klicken Sie dann auf **OK**.
5. Geben Sie im Bereich **Benutzer**, **Computer** oder **Gruppen auswählen** im Feld **Geben Sie die zu verwenden Objektnamen ein** den Namen des Computers ein, auf dem der Connector installiert ist.
6. Wählen Sie **Namen überprüfen** aus, um den Eintrag zu überprüfen > **OK** > **weiter**.
7. Wählen Sie **Create a custom task to delegate** > **Next** (Benutzerdefinierte Aufgaben zum Zuweisen erstellen > Weiter) aus.
8. Aktivieren Sie das Kontrollkästchen **Only the following objects in the folder** (Nur die folgenden Objekte im Ordner) und anschließen die Kontrollkästchen **Computer objects** (Computerobjekte), **Delete selected objects in this folder** (Gewählte Objekte in diesem Ordner löschen) und **Create selected objects in this folder** (Gewählte Objekte in diesem Ordner erstellen).
9. Wählen Sie **Weiter** aus.
10. Aktivieren Sie unter **Permissions** (Berechtigungen) das Kontrollkästchen **Full Control** (Vollzugriff). Durch diese Auswahl werden auch alle anderen Optionen aktiviert.
11. Wählen Sie **weiter** > **Fertig**stellen aus.

## <a name="next-steps"></a>Nächste Schritte

- [Behandlung von Problemen bei der Geräteregistrierung bei Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Stellen Sie eine Frage im Intune-Forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Lesen Sie den Blog des Microsoft Intune-Supportteams.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Lesen Sie den Blog zu Microsoft Enterprise Mobility + Security.](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Support für Microsoft Intune](../fundamentals/get-support.md)
- [Registrierungsfehler bei der Co-Verwaltung suchen](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
