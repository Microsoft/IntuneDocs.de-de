---
title: Behandlung von Problemen bei der Windows-Geräteregistrierung in Microsoft Intune
titleSuffix: Microsoft Intune
description: Vorschläge zur Behandlung einiger der häufigsten Probleme beim Registrieren von Windows-Geräten in Intune.
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
ms.openlocfilehash: dae8e92209a8640ab3254e073d3043d390c3791b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514250"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Behandeln von Problemen bei der Windows-Geräteregistrierung in Microsoft Intune

Dieser Artikel bietet Intune-Administratoren Unterstützung bei der Diagnose und Behandlung von Problemen bei der Registrierung von Windows-Geräten in Intune.

## <a name="prerequisites"></a>Voraussetzungen
Bevor Sie mit der Problembehandlung beginnen, ist es wichtig, einige grundlegende Informationen zu sammeln. Diese Informationen können Ihnen helfen, das Problem besser zu verstehen und die Zeit für die Suche nach einer Lösung zu verkürzen.

Sammeln Sie die folgenden Informationen zum Problem:
- Ist dem Benutzer eine gültige Intune-Lizenz zugewiesen? Bevor Benutzer ihre Geräte registrieren können, müssen ihnen die nötigen Lizenzen zugewiesen werden.
- Ist das neueste Update auf dem Windows-Gerät installiert? Einige Features in Intune funktionieren nur mit der neuesten Version von Windows. Es gibt zahlreiche Korrekturen für bekannte Probleme, die über Windows Update zur Verfügung stehen. Durch die Anwendung aller aktuellen Updates kann ein Problem bei der Registrierung eines Windows-Geräts häufig behoben werden. 
- Wie lautet die genaue Fehlermeldung?
- Wo wird die Fehlermeldung angezeigt?
- Wann fing das Problem an? Hat die Registrierung jemals funktioniert? 
- Auf welcher Plattform (Android, iOS/iPadOS, Windows) tritt das Problem auf?
- Wie viele Benutzer sind betroffen? Sind alle oder nur einige Benutzer betroffen?
- Wie viele Geräte sind betroffen? Sind alle oder nur einige Geräte betroffen?
- Welche MDM-Autorität wird verwendet?
- Wie wird die Registrierung durchgeführt? Wird BYOD (Bring Your Own Device) oder das Apple-Programm zur Geräteregistrierung (DEP) mit Registrierungsprofilen verwendet?

## <a name="error-messages"></a>Fehlermeldungen

### <a name="this-user-is-not-authorized-to-enroll"></a>Dieser Benutzer ist nicht zur Registrierung autorisiert.

Fehler 0x801c003: „Dieser Benutzer ist nicht zur Registrierung autorisiert. Sie können den Vorgang wiederholen oder sich mit dem Fehlercode (0x801c0003) an Ihren Systemadministrator wenden.“
Fehler 80180003: „Es ist ein Problem aufgetreten. Dieser Benutzer ist nicht zur Registrierung autorisiert. Sie können den Vorgang wiederholen oder sich mit dem Fehlercode 80180003 an Ihren Systemadministrator wenden.“

**Ursache**: Jede der folgenden Bedingungen: 

- Der Benutzer hat bereits die maximal zulässige Anzahl von Geräten in Intune registriert.    
- Das Gerät wird durch Einschränkungen zum Gerätetyp blockiert.    
- Auf dem Computer wird Windows 10 Home ausgeführt. Die Registrierung in Intune oder der Beitritt zu Azure AD wird jedoch nur auf Windows 10 Pro und höheren Editionen unterstützt.

#### <a name="resolution"></a>Lösung
Für dieses Problem gibt es mehrere mögliche Lösungen:

##### <a name="remove-devices-that-were-enrolled"></a>Entfernen von registrierten Geräten
1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.    
2. Wechseln Sie zu **Benutzer** > **alle Benutzer**.    
3. Wählen Sie das betroffene Benutzerkonto aus, und klicken Sie dann auf **Geräte**.    
4. Wählen Sie ein nicht verwendetes oder nicht benötigtes Gerät aus, und klicken Sie dann auf **Löschen**. 

##### <a name="increase-the-device-enrollment-limit"></a>Erhöhen des Grenzwerts für die Geräteregistrierung

> [!NOTE]
> Durch diese Methode wird das Limit für die Geräteregistrierung für alle Benutzer erhöht, nicht lediglich für den betroffenen Benutzer.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wechseln Sie zu **Geräte** > **Registrierungsbeschränkungen** > **Standard** (unter **Einschränkungen zum Gerätelimit**) > **Eigenschaften** > **Bearbeiten** (neben **Gerätelimit**). Erhöhen Sie den Wert für **Gerätelimit** (maximal 15), und klicken Sie auf **Überprüfen und speichern**.    
 

##### <a name="check-device-type-restrictions"></a>Überprüfen der Gerätetypbeschränkungen
1. Melden Sie sich mit einem globalen Administratorkonto beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wechseln Sie zu **Geräte** > **Registrierungsbeschränkungen**, und wählen Sie unter **Einschränkungen zum Gerätetyp** die Einschränkung **Standard** aus.    
3. Klicken Sie auf **Plattformen**, und wählen Sie dann für **Windows (MDM)** die Option **Zulassen** aus.

    > [!IMPORTANT]
    > Wenn die aktuelle Einstellung bereits **Zulassen** lautet, ändern Sie sie in **Blockieren**, und speichern Sie die Einstellung. Ändern Sie die Einstellung anschließend zurück in **Zulassen**, und speichern Sie die Einstellung erneut. Dadurch wird die Registrierungseinstellung zurückgesetzt.

4. Warten Sie etwa 15 Minuten, und registrieren Sie das betroffene Gerät anschließend erneut.    

##### <a name="upgrade-windows-10-home"></a>Upgrade auf Windows 10 Home
[Führen Sie ein Upgrade von Windows 10 Home auf Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) oder eine höhere Edition durch. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Dieser Benutzer ist nicht zur Registrierung zugelassen.

Fehler 0x801c0003: „Dieser Benutzer ist nicht zur Registrierung zugelassen. Versuchen Sie es noch mal, oder wenden Sie sich mit dem Fehlercode 801c0003 an Ihren Systemadministrator.“

**Ursache:** Die Einstellung **Benutzer dürfen Geräte in Azure AD einbinden** ist auf **Keine** festgelegt. Dadurch wird verhindert, dass neue Benutzer ihre Geräte in Azure AD einbinden können. Aus diesem Grund ist die Intune-Registrierung nicht erfolgreich.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) als Administrator an.    
2. Wechseln Sie zu **Azure Active Directory** > **Geräte** > **Geräteeinstellungen**.    
3. Legen Sie **Benutzer dürfen Geräte in Azure AD einbinden** auf **Alle** fest.    
4. Registrieren Sie das Gerät erneut.   

### <a name="the-device-is-already-enrolled"></a>Das Gerät ist bereits registriert.

Fehler 8018000a: „Es ist ein Problem aufgetreten. Das Gerät ist bereits registriert.  Wenden Sie sich mit dem Fehlercode 8018000a an Ihren Systemadministrator.“

**Ursache**: Eine der folgenden Bedingungen ist erfüllt:
- Ein anderer Benutzer hat das Gerät bereits in Intune registriert oder das Gerät in Azure AD eingebunden. Um zu ermitteln, ob dies der Fall ist, wechseln Sie zu **Einstellungen** > **Konten** > **Arbeitsplatzzugriff**. Suchen Sie nach einer Meldung ähnlich der folgenden: „Ein anderer Benutzer im System ist bereits mit einem Unternehmen oder einer Schule verbunden. Entfernen Sie die betreffende Verbindung, und versuchen Sie es erneut.“    

#### <a name="resolution"></a>Lösung

Nutzen Sie eines der folgenden Verfahren, um dieses Problem zu beheben:

##### <a name="remove-the-other-work-or-school-account"></a>Entfernen des anderen Geschäfts-, Schul- oder Unikontos
1. Melden Sie sich von Windows ab, und melden Sie sich dann mit dem anderen Konto an, das zum Registrieren oder Einbinden des Geräts verwendet wurde.    
2. Wechseln Sie zu **Einstellungen** > **Konten** > **Arbeitsplatzzugriff**, und entfernen Sie dann das Geschäfts-, Schul- oder Unikonto.
3. Melden Sie sich von Windows ab, und melden Sie sich anschließend mit Ihrem Konto an.    
4. Registrieren Sie das Gerät bei Intune, oder binden Sie das Gerät in Azure AD ein. 



### <a name="this-account-is-not-allowed-on-this-phone"></a>Dieses Konto ist auf diesem Telefon nicht zulässig.

Fehler: „Dieses Konto ist auf diesem Telefon nicht zulässig. Stellen Sie sicher, dass die von Ihnen angegebenen Informationen korrekt sind. Versuchen Sie es anschließend erneut, oder fordern Sie Unterstützung von Ihrem Unternehmen an.“

**Ursache:** Der Benutzer, der versucht hat, das Gerät zu registrieren, verfügt über keine gültige Intune-Lizenz.

#### <a name="resolution"></a>Lösung
Weisen Sie dem Benutzer eine gültige Intune-Lizenz zu, und registrieren Sie dann das Gerät.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Der Endpunkt für die MDM-Nutzungsbedingungen ist offenbar nicht ordnungsgemäß konfiguriert.

**Ursache**: Eine der folgenden Bedingungen ist erfüllt: 
 - Sie verwenden die mobile Geräteverwaltung (Mobile Device Management, MDM) für Office 365 und Intune für den Mandanten, und der Benutzer, der die Geräteregistrierung durchführen möchte, besitzt keine gültige Intune- oder Office 365-Lizenz.     
- Die MDM-Nutzungsbedingungen in Azure AD sind leer oder enthalten nicht die richtige URL.    

#### <a name="resolution"></a>Lösung

Verwenden Sie eine der folgenden Methoden, um dieses Problem zu beheben: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Zuweisen einer gültigen Lizenz für den Benutzer
Wechseln Sie zum [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home), und weisen Sie dem Benutzer entweder eine Intune- oder eine Office 365-Lizenz zu.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Korrigieren Sie die URL für die MDM-Nutzungsbedingungen.
  1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und klicken Sie dann auf **Azure Active Directory**.    
  2. Wählen Sie **Mobilität (MDM und MAM)** aus, und klicken Sie dann auf **Microsoft Intune**.    
  3. Wählen Sie **MDM-Standard-URLs wiederherstellen** aus, vergewissern Sie sich, dass die **MDM-URL für Nutzungsbedingungen** auf **https://portal.manage.microsoft.com/TermsofUse.aspx** festgelegt ist.    
  4. Wählen Sie **Speichern** aus.    


### <a name="something-went-wrong"></a>Es ist ein Problem aufgetreten.

Fehler 80180026: „Es ist ein Problem aufgetreten. Vergewissern Sie sich, dass Sie die richtigen Anmeldeinformationen verwenden und Ihre Organisation dieses Feature verwendet. Sie können den Vorgang wiederholen oder sich mit dem Fehlercode 80180026 an Ihren Systemadministrator wenden.“

**Ursache:** Dieser Fehler kann auftreten, wenn beim Versuch der Einbindung eines Windows 10-Computers in Azure AD beide der folgenden Bedingungen erfüllt sind: 
- Die automatische MDM-Registrierung ist in Azure aktiviert.    
- Der Intune-PC-Client (Intune-PC-Agent) ist auf dem Windows 10-Computer installiert.

#### <a name="resolution"></a>Lösung
Nutzen Sie eines der folgenden Verfahren, um dieses Problem zu beheben:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Deaktivieren Sie die automatische MDM-Registrierung in Azure.
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.    
2. Wechseln Sie zu **Azure Active Directory** > **Mobilität (MDM und MAM)**  > **Microsoft Intune**.    
3. Legen Sie den **MDM-Benutzerbereich** auf **Keine** fest, und klicken Sie dann auf **Speichern**.    
     
##### <a name="uninstall"></a>Deinstallieren
Deinstallieren Sie den Intune-PC-Client-Agent vom Computer.    

### <a name="the-software-cannot-be-installed"></a>Die Software kann nicht installiert werden.

Fehler: „Die Software kann nicht installiert werden, 0x80cf4017.“

**Ursache:** Die Clientsoftware ist veraltet.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich bei [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) an.    
2. Wechseln Sie zu **Verwaltung** > **Download der Clientsoftware**, und klicken Sie dann auf **Clientsoftware herunterladen**.    
3. Speichern Sie das Installationspaket, und installieren Sie dann die Clientsoftware. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>Das Kontozertifikat ist ungültig und ist möglicherweise abgelaufen.

Fehler: „Das Kontozertifikat ist ungültig und ist möglicherweise abgelaufen, 0x80cf4017.“

**Ursache:** Die Clientsoftware ist veraltet.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich bei [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com) an.    
2. Wechseln Sie zu **Verwaltung** > **Download der Clientsoftware**, und klicken Sie dann auf **Clientsoftware herunterladen**.    
3. Speichern Sie das Installationspaket, und installieren Sie dann die Clientsoftware.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Diese Windows-Version wird von Ihrer Organisation nicht unterstützt. 

Fehler: „Es ist ein Problem aufgetreten. Diese Windows-Version wird von Ihrer Organisation nicht unterstützt.  (0x80180014)“

**Ursache:** Die Windows MDM-Registrierung ist in Ihrem Intune-Mandanten deaktiviert.

#### <a name="resolution"></a>Lösung
Um dieses Problem in einer eigenständigen Intune-Umgebung zu beheben, führen Sie die folgenden Schritte aus: 
 
1. Klicken Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Registrierungseinschränkungen**, und wählen Sie eine Einschränkung zum Gerätetyp aus.    
2. Wählen Sie **Eigenschaften** > **Bearbeiten** (neben **Plattformeinstellungen**) > **Zulassen** für **Windows (MDM)** aus.    
3. Klicken Sie auf **Überprüfen und speichern**.    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Setupfehler bei der Massenregistrierung.

**Ursache:** Die Azure AD-Benutzerkonten im Kontopaket (Paket_GUID) für das jeweilige Bereitstellungspaket dürfen keine Geräte in Azure AD einbinden. Diese Azure AD-Konten werden automatisch erstellt, wenn Sie zur Einrichtung eines Bereitstellungspaket WCD (Windows Configuration Designer) oder die App „Schul-PCs einrichten“ verwenden, und die Geräte werden dann über diese Konten in Azure AD eingebunden.

#### <a name="resolution"></a>Lösung
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) als Administrator an.    
2. Navigieren Sie zu **Azure Active Directory > Geräte > Geräteeinstellungen**.    
3. Legen Sie **Benutzer dürfen Geräte in Azure AD einbinden** auf **Alle** oder **Ausgewählte** fest.

   Wenn Sie **Ausgewählt** auswählen, klicken Sie auf **Ausgewählt** und dann auf **Mitglieder hinzufügen**, um alle Benutzer hinzuzufügen, die ihre Geräte in Azure AD einbinden können. Stellen Sie sicher, dass alle Azure AD-Konten für das Bereitstellungspaket hinzugefügt werden.
 
Weitere Informationen zum Erstellen eines Bereitstellungspakets für Windows Configuration Designer finden Sie unter [Erstellen eines Bereitstellungspakets für Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Weitere Informationen zur App „Schul-PC einrichten“ finden Sie unter [Verwenden der App „Schul-PC einrichten“](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Automatische MDM-Registrierung: Fehler 

Wenn Sie versuchen, ein Windows 10-Gerät automatisch mithilfe der Gruppenrichtlinie zu registrieren, treten folgende Probleme auf: 
- In der Aufgabenplanung lautet unter **Microsoft** > **Windows** > **EnterpriseMgmt** das letzte Ausführungsergebnis der Aufgabe **Durch Registrierungsclient erstellter Zeitplan für die automatische Registrierung in MDM aus AAD** wie folgt: **Ereignis 76: Automatische MDM-Anmeldung: Fehler (Unbekannter Win32-Fehlercode: 0x8018002b)**       
- In der Ereignisanzeige wird unter **Anwendungs- und Dienstprotokolle/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/Admin** das folgende Ereignis protokolliert:   
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
Wenn der UPN eine nicht überprüfte oder nicht routingfähige Domäne enthält, führen Sie die folgenden Schritte aus: 

1. Öffnen Sie auf dem Server, auf dem AD DS (Active Directory Domain Services) ausgeführt wird, die Konsole **Active Directory-Benutzer und Computer**, indem Sie **dsa.msc** im Dialogfeld **Ausführen** eingeben und dann auf **OK** klicken.    
2. Klicken Sie unterhalb Ihrer Domäne auf **Benutzer**, und gehen Sie dann wie folgt vor:  
    - Wenn nur ein Benutzer betroffen ist, klicken Sie mit der rechten Maustaste auf den Benutzer und anschließend auf **Eigenschaften**. Wählen Sie auf der Registerkarte **Konto** in der Dropdownliste für das UPN-Suffix unter **Benutzeranmeldename** ein gültiges UPN-Suffix aus (z. B. contoso.com), und klicken Sie dann auf **OK**.    
    - Wenn mehrere Benutzer betroffen sind, wählen Sie die Benutzer aus, und klicken Sie im Menü **Aktion** auf **Eigenschaften**. Aktivieren Sie auf der Registerkarte **Konto** das Kontrollkästchen **UPN-Suffix**, wählen Sie in der Dropdown Liste ein gültiges UPN-Suffix aus (z. B. contoso.com), und klicken Sie dann auf **OK**.
3. Warten Sie auf die nächste Synchronisierung, oder erzwingen Sie eine Deltasynchronisierung durch den Synchronisierungsserver, indem Sie an einer PowerShell-Eingabeaufforderung mit erhöhten Rechten die folgenden Befehle eingeben:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Wenn der **MDM-Benutzerbereich** auf **Keine** festgelegt ist, führen Sie die folgenden Schritte aus: 
 
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an, und klicken Sie dann auf **Azure Active Directory**.
2. Wählen Sie **Mobilität (MDM und MAM)** aus, und klicken Sie dann auf **Microsoft Intune**.    
3. Legen Sie den **MDM-Benutzerbereich** auf **Alle** fest. Oder legen Sie den **MDM-Benutzerbereich** auf **Einige** fest, und wählen Sie die Gruppen aus, die Ihre Windows 10-Geräte automatisch registrieren können.    
4. Legen Sie den **MAM-Benutzerbereich** auf **Keine** fest.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Fehler beim Erstellen des Autopilot-Profils.

**Ursache:** Das angegebene Namensformat der Vorlage für Gerätenamen entspricht nicht den Anforderungen. Beispielsweise verwenden Sie %serial% (Kleinbuchstaben) anstelle von %SERIAL% für das %SERIAL%-Makro.

#### <a name="resolution"></a>Lösung

Stellen Sie sicher, dass das Namensformat die folgenden Anforderungen erfüllt:

- Erstellen Sie einen eindeutigen Namen für Ihre Geräte. Namen dürfen höchstens 15 Zeichen lang sein und können Buchstaben (a-z, A-Z), Zahlen (0-9) und Bindestriche (-) enthalten.
- Ein Name darf nicht nur aus Zahlen bestehen.
- Namen dürfen keinen leeren Bereich enthalten.
- Verwenden Sie das %SERIAL%-Makro, um eine hardwarespezifische Seriennummer hinzuzufügen. Oder verwenden Sie das Makro %RAND:<Anzahl von Ziffern>%, um eine zufällige Ziffernfolge hinzuzufügen, die die angegebene <Anzahl von Ziffern> enthält. Beispielsweise generiert MYPC-%RAND:6% einen Namen wie MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Es ist ein Problem aufgetreten. OOBEIDPS.

**Ursache:** Dieses Problem tritt auf, wenn der Zugriff auf den Identitätsanbieter (IDP) durch einen Proxy, eine Firewall oder ein anderes Netzwerkgerät blockiert wird.

#### <a name="resolution"></a>Lösung
Stellen Sie sicher, dass der erforderliche Zugriff auf internetbasierte Dienste für Autopilot nicht blockiert ist. Weitere Informationen finden Sie unter [Netzwerkanforderungen für Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Ihr Gerät wird für die mobile Verwaltung registriert (Fehler: 3, 0x801C03EA).

**Ursache:** Das Gerät verfügt über einen TPM-Chip mit Unterstützung von Version 2.0, wurde jedoch noch nicht auf Version 2.0 aktualisiert.

#### <a name="resolution"></a>Lösung
Aktualisieren Sie den TPM-Chip auf Version 2.0.

Falls das Problem weiterhin besteht, überprüfen Sie, ob sich das Gerät in zwei zugewiesenen Gruppen befindet, die jeweils einem unterschiedlichen Autopilot-Profil zugewiesen sind. Befindet sich das Gerät in zwei Gruppen, bestimmen Sie, welches Autopilot-Profil auf das Gerät angewendet werden soll, und entfernen Sie die zweite Profilzuweisung.

Weitere Informationen zum Bereitstellen eines Windows-Geräts im Kioskmodus mit Autopilot finden Sie unter [Bereitstellen eines Kiosks mithilfe von Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Schützen Sie Ihre Hardware (Fehler: 0x800705b4).

Fehler 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Ursache:** Das Windows-Zielgerät erfüllt keine der folgenden Anforderungen:

- Das Gerät muss über einen physischen TPM 2.0-Chip verfügen. Geräte mit virtuellen TPMs (z. B. Hyper-V-VMs) oder TPM 1.2-Chips funktionieren nicht mit dem Modus für automatische Bereitstellung.
- Auf dem Gerät muss eine der folgenden Versionen von Windows ausgeführt werden:
    - Windows 10 Build 1703 oder eine höhere Version.
    - Bei Verwendung von Azure AD Hybrid Join wird Windows 10 Build 1809 oder eine höhere Version benötigt.


#### <a name="resolution"></a>Lösung
Stellen Sie sicher, dass das Zielgerät beide Anforderungen erfüllt, die im Abschnitt **Ursache** beschrieben werden.

Weitere Informationen zum Bereitstellen eines Windows-Geräts im Kioskmodus mit Autopilot finden Sie unter [Bereitstellen eines Kiosks mithilfe von Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Es ist ein Problem aufgetreten. Fehlercode 80070774.

Fehler 0x80070774: Es ist ein Problem aufgetreten. Vergewissern Sie sich, dass Sie die richtigen Anmeldeinformationen verwenden und Ihre Organisation dieses Feature verwendet. Sie können den Vorgang wiederholen oder sich mit dem Fehlercode 80070774 an Ihren Systemadministrator wenden.

Dieses Problem tritt üblicherweise vor dem Neustart des Geräts in einem Azure AD Hybrid-Autopilot-Szenario auf, wenn für das Gerät während des ersten Anmeldebildschirms ein Timeout auftritt. Dies bedeutet, dass der Domänencontroller aufgrund von Konnektivitätsproblemen nicht gefunden wurde oder nicht erreichbar war. Alternativ befindet sich das Gerät in einem Zustand, der einen Beitritt zur Domäne nicht zulässt.

**Ursache:** Die häufigste Ursache ist die Verwendung von Azure AD Hybrid Join mit konfigurierter Benutzerzuweisung im Autopilot-Profil. Durch die Verwendung des Features „Benutzer zuweisen“ wird während des ersten Anmeldebildschirms ein Azure AD-Beitritt für das Gerät durchgeführt. Hierdurch wird das Gerät in einen Zustand versetzt, der den Beitritt zu Ihrer lokalen Domäne verhindert. Aus diesem Grund sollte das Feature „Benutzer zuweisen“ nur in Autopilot-Standardszenarien für den Azure AD-Beitritt verwendet werden.  Verwenden Sie das Feature nicht in Azure AD Hybrid Join-Szenarien.

#### <a name="resolution"></a>Lösung

1. Klicken Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Windows** > **Windows-Geräte**.
2. Wählen Sie das Gerät aus, auf dem das Problem auftritt, und klicken Sie auf der rechten Seite auf die Auslassungspunkte (...).
3. Wählen Sie **Benutzerzuweisung aufheben** aus, und warten Sie, bis der Vorgang abgeschlossen wurde.
4. Vergewissern Sie sich, dass das Azure AD Hybrid-Autopilot-Profil zugewiesen wurde, bevor Sie die Willkommensseite erneut öffnen.

#### <a name="second-resolution"></a>Zweite Lösungsmöglichkeit
Falls das Problem weiterhin auftritt, überprüfen Sie auf dem Server, der den Intune-Connector für den Offlinedomänenbeitritt hostet, ob das Ereignis mit der ID 30312 im Protokoll des ODJ-Connectordiensts aufgezeichnet wird. Das Ereignis 30312 ähnelt dem folgenden:

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

Dieses Problem wird in der Regel durch das falsche Delegieren von Berechtigungen an die Organisationseinheit verursacht, in der die Windows-Autopilot-Geräte erstellt werden. Weitere Informationen finden Sie unter [Erhöhen des Kontolimits für den Computer in der Organisationseinheit](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Öffnen Sie **Active Directory-Benutzer und -Computer** („DSA.msc“).
2. Klicken Sie mit der rechten Maustaste auf die Organisationseinheit, mit der Sie die in Azure AD Hybrid eingebundenen Computer erstellen möchten, und wählen Sie **Objektverwaltung zuweisen** aus.
3. Wählen Sie im Assistenten zum Zuweisen der **Objektverwaltung** die Optionen **Weiter** > **Hinzufügen...**  > **Objekttypen** aus.
4. Aktivieren Sie im Bereich **Objekttypen** das Kontrollkästchen **Computer**, und klicken Sie dann auf **OK**.
5. Geben Sie im Bereich **Benutzer**, **Computer** oder **Gruppen auswählen** im Feld **Geben Sie die zu verwenden Objektnamen ein** den Namen des Computers ein, auf dem der Connector installiert ist.
6. Wählen Sie **Namen überprüfen** aus, um den Eintrag zu überprüfen, und klicken Sie auf **OK** > **Weiter**.
7. Wählen Sie **Create a custom task to delegate** > **Next** (Benutzerdefinierte Aufgaben zum Zuweisen erstellen > Weiter) aus.
8. Aktivieren Sie das Kontrollkästchen **Only the following objects in the folder** (Nur die folgenden Objekte im Ordner) und anschließen die Kontrollkästchen **Computer objects** (Computerobjekte), **Delete selected objects in this folder** (Gewählte Objekte in diesem Ordner löschen) und **Create selected objects in this folder** (Gewählte Objekte in diesem Ordner erstellen).
9. Wählen Sie **Weiter** aus.
10. Aktivieren Sie unter **Permissions** (Berechtigungen) das Kontrollkästchen **Full Control** (Vollzugriff). Durch diese Auswahl werden auch alle anderen Optionen aktiviert.
11. Klicken Sie auf **Weiter** > **Fertig stellen**.

### <a name="the-enrollment-status-page-times-out-before-the-sign-in-screen"></a>Timeout der Seite zum Registrierungsstatus vor Anzeige des Anmeldebildschirms

**Ursache:** Dieses Problem kann auftreten, wenn alle der folgenden Bedingungen zutreffen:
- Sie verwenden die Seite zum Registrierungsstatus, um Microsoft Store für Unternehmen-Anwendungen zu verfolgen.
- Sie verfügen über eine Azure AD-Richtlinie für bedingten Zugriff, bei der ein Gerät als konform markiert werden muss.
- Die Richtlinie gilt für alle Cloud-Apps und Windows.

#### <a name="resolution"></a>Lösung:
Versuchen Sie Folgendes:
- Wenden Sie Ihre Intune-Konformitätsrichtlinien auf Geräte an. Stellen Sie sicher, dass die Konformität bestimmt werden kann, bevor sich der Benutzer anmeldet.
- Verwenden Sie für Store-Apps die Offlinelizenzierung. Auf diese Weise muss der Windows-Client nicht den Microsoft Store überprüfen, bevor die Gerätekonformität festgestellt wird.



## <a name="next-steps"></a>Nächste Schritte

- [Behandlung von Problemen bei der Geräteregistrierung bei Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Stellen Sie eine Frage im Intune-Forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Lesen Sie den Blog des Microsoft Intune-Supportteams.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Lesen Sie den Blog zu Microsoft Enterprise Mobility + Security.](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Support für Microsoft Intune](../fundamentals/get-support.md)
- [Ermitteln von Registrierungsfehlern bei der Co-Verwaltung](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
