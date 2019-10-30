---
title: 'Verwenden von SCEP-Zertifikatprofilen mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen und Zuweisen von SCEP-Zertifikatprofilen (Simple Certificate Enrollment Protocol) mit Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
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
ms.openlocfilehash: 4e28db0d24101ae65ff8c5e49febd0ff5dddc6e2
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585431"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Erstellen und Zuweisen eines SCEP-Zertifikatprofils in Intune

Nachdem Sie [Ihre Infrastruktur für die Unterstützung von SCEP-Zertifikaten (Simple Certificate Enrollment Protocol) konfiguriert haben](certificates-scep-configure.md), können Sie SCEP-Zertifikatprofile erstellen und Benutzern und Geräten in Intune zuweisen.

> [!IMPORTANT]  
> Bevor Sie SCEP-Zertifikatprofile erstellen, müssen Geräte, die ein SCEP-Zertifikatprofil verwenden werden, Ihrer vertrauenswürdigen Stammzertifizierungsstelle (CA) vertrauen. Verwenden Sie in Intune ein *vertrauenswürdiges Zertifikatprofil* zum Bereitstellen des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle für Benutzer und Geräte. Informationen zum vertrauenswürdigen Zertifikatprofil finden Sie unter [Exportieren des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle](certificates-configure.md#export-the-trusted-root-ca-certificate) und [Erstellen vertrauenswürdiger Zertifikatprofile](certificates-configure.md#create-trusted-certificate-profiles) in *Verwenden von Zertifikaten für die Authentifizierung in Intune*.


## <a name="create-a-scep-certificate-profile"></a>Erstellen eines SCEP-Zertifikatprofils

1. Melden Sie sich beim [Intune-Portal](https://aka.ms/intuneportal) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie für das SCEP-Zertifikatprofil einen **Namen** und eine **Beschreibung** ein.
4. Wählen Sie in der Dropdownliste **Plattform** eine [unterstützte Geräteplattform](certificates-configure.md#supported-platforms-and-certificate-profiles) für dieses SCEP-Zertifikat aus. 
5. Wählen Sie in der Dropdownliste **Profiltyp** die Option **SCEP-Zertifikat** aus.  
   
   Für die **Android Enterprise**-Plattform ist der *Profiltyp* in zwei Kategorien unterteilt: *Nur Gerätebesitzer* und *Nur Arbeitsprofil*. Stellen Sie sicher, dass Sie das richtige SCEP-Zertifikatprofil für die von Ihnen verwalteten Geräte auswählen.  

   Bei SCEP-Zertifikatprofilen für das Profil *Nur Gerätebesitzer* gelten folgende Einschränkungen:  

   1. Die folgenden Variablen werden nicht unterstützt:  

      - CN={{OnPrem_Distinguished_Name}}  
      - CN={{onPremisesSamAccountName}}  

   2. Unter „Überwachung“ ist die Zertifikatberichterstellung für SCEP-Zertifikatprofile für Gerätebesitzer nicht verfügbar.
   
   3. Sie können Intune nicht verwenden, um Zertifikate zu widerrufen, die von SCEP-Zertifikatsprofilen für Gerätebesitzer bereitgestellt wurden. Sie können den Widerruf über einen externen Prozess oder direkt mit der Zertifizierungsstelle verwalten. 

6. Klicken Sie auf **Einstellungen**, und nehmen Sie die folgenden Konfigurationen vor:

   - **Zertifikattyp**:   
     *(Gilt für:  Android, Android Enterprise, iOS, macOS, Windows 8.1 und höher sowie Windows 10 und höher)*  

      Wählen Sie je nach Verwendung des Zertifikatprofils einen Typ aus:
      - **Benutzer:** Bei *Benutzerzertifikaten* können sowohl Benutzer- als auch Geräteattribute im Betreff und im alternativen Antragstellernamen des Zertifikats enthalten sein.  
      - **Gerät:**  Beim Zertifikattyp *Gerät* können nur Geräteattribute im Betreff und im alternativen Antragstellernamen des Zertifikats enthalten sein.  
      
        Benutzen Sie **Gerät** für Szenarios mit benutzerlosen Geräten (wie Kioske) oder Windows-Geräten. Auf Windows-Geräten wird das Zertifikat in den Zertifikatspeicher des lokalen Computers eingefügt.  

   - **Format des Antragstellernamens**:  
     Wählen Sie aus, auf welche Weise Intune den Antragstellernamen in der Zertifikatanforderung automatisch erstellen soll. Die Optionen für das Format des Antragstellernamens sind abhängig vom ausgewählten Zertifikattyp (**Benutzer** oder **Gerät**).  

     > [!NOTE]  
     > Es gibt ein [bekanntes Problem](#avoid-certificate-signing-requests-with-escaped-special-characters) bei der Verwendung von SCEP zum Abrufen von Zertifikaten, wenn der Antragstellername in der resultierenden Zertifikatsignieranforderung (Certificate Signing Request, CSR) eines der folgenden Zeichen als Escapezeichen enthält (mit vorangestelltem Schrägstrich\\):
     > - \+
     > - ;
     > - ,
     > - =

     - **Benutzerzertifikattyp**  
       Formatoptionen für das *Format des Antragstellernamens*:  
       - **Nicht konfiguriert**
       - **Allgemeiner Name**
       - **Allgemeiner Name einschließlich E-Mail-Adresse**
       - **Allgemeiner Name als E-Mail-Adresse**
       - **IMEI (International Mobile Equipment Identity)**
       - **Seriennummer**
       - **Benutzerdefiniert**: Bei Auswahl dieser Option wird auch ein **benutzerdefiniertes** Textfeld angezeigt. In dieses Feld können Sie ein benutzerdefiniertes Format für den Antragstellernamen, einschließlich Variablen, eingeben. Das benutzerdefinierte Format unterstützt zwei Variablen: **Common Name (CN)** (Allgemeiner Name) und **Email (E)** (E-Mail-Adresse). **Allgemeiner Name (CN)** kann auf eine der folgenden Variablen festgelegt werden:

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

   - **Alternativer Antragstellername**:  
     Wählen Sie aus, auf welche Weise Intune den alternativen Antragstellernamen (Subject Alternative Name, SAN) in der Zertifikatanforderung automatisch erstellen soll. Die Optionen für den alternativen Antragstellernamen sind abhängig vom ausgewählten Zertifikattyp (**Benutzer** oder **Gerät**).  

      - **Benutzerzertifikattyp**  
        Wählen Sie aus den verfügbaren Attributen aus:  
        - **E-Mail-Adresse**
        - **Benutzerprinzipalname (UPN)** 

        Benutzerzertifikattypen können beispielsweise den Benutzerprinzipalnamen (User Principal Name, UPN) in den alternativen Antragstellernamen aufnehmen. Wenn ein Clientzertifikat für die Authentifizierung bei einem Netzwerkrichtlinienserver verwendet wird, legen Sie den alternativen Antragstellernamen auf den Benutzerprinzipalnamen fest.

      - **Gerätzertifikattyp**  
        Verwenden Sie die Dropdownoption **Attribut**, wählen Sie ein Attribut aus, weisen Sie einen **Wert** zu, und klicken Sie auf **Hinzufügen**, um diesen hinzuzufügen. Sie können mehrere Werte hinzufügen, indem Sie zusätzliche Attribute auswählen.  

        Zu den verfügbaren Attributen zählen:
        - **E-Mail-Adresse**
        - **Benutzerprinzipalname (UPN)**
        - **DNS**

        Mit dem Zertifikattyp *Gerät* können Sie die folgenden Gerätzertifikatvariablen für den Wert verwenden:  

        - **{{AAD_Device_ID}}**
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{AzureADDeviceId}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        Schließen Sie den Variablennamen in geschweifte Klammern ein („{ }“), und fügen Sie den Text für diese Variable hinzu, um einen Wert für ein Attribut anzugeben. Beispielsweise kann mit **{{AzureADDeviceId}}.domain.com** ein Wert für das DNS-Attribut hinzugefügt werden, wobei *.domain.com* der Text ist. Einem Benutzer namens *User1* wird eine E-Mail-Adresse möglicherweise als {{FullyQualifiedDomainName}}User1@Contoso.com angezeigt.  

        > [!IMPORTANT]  
        > - Wenn Sie eine Gerätezertifikatvariable verwenden, schließen Sie den Variablennamen in geschweifte Klammern ein („{ }“).  
        > - Verwenden Sie für den Text nach der Variable keine geschweiften Klammern **{ }** , senkrechten Striche **|** und Semikolons **;** .  
        > - Geräteeigenschaften, die im *Betreff* oder *alternativen Antragstellernamen* eines Gerätezertifikats wie **IMEI**, **SerialNumber** oder **FullyQualifiedDomainName** verwendet werden, sind Eigenschaften, die von einer Person mit Zugriff auf das Gerät gespooft sein könnten.  
        > - Ein Gerät muss alle in einem Zertifikatprofil für dieses Profil angegebenen Variablen unterstützen, um auf diesem Gerät installiert werden zu können.  Wenn **{{IMEI}}** beispielsweise im alternativen Antragstellernamen eines SCEP-Profils verwendet wird und einem Gerät ohne IMEI-Nummer zugewiesen ist, tritt bei der Profilinstallation ein Fehler auf.

   - **Gültigkeitsdauer des Zertifikats**:  
     Sie können einen niedrigeren Wert als den für die Gültigkeitsdauer in der Zertifikatvorlage eingeben, aber keinen höheren. Wenn Sie die Zertifikatvorlage so konfiguriert haben, dass [ein benutzerdefinierter Wert unterstützt wird, der in der Intune-Konsole festgelegt werden kann](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template), geben Sie mit dieser Einstellung die verbleibende Zeit bis zum Ablauf des Zertifikats an.  

     Wenn die Gültigkeitsdauer des Zertifikats in der Zertifikatvorlage beispielsweise zwei Jahre beträgt, können Sie als Wert „ein Jahr“ eingeben, aber nicht „fünf Jahre“. Zudem muss der Wert niedriger als die verbleibende Gültigkeitsdauer des Zertifikats der ausstellenden Zertifizierungsstelle sein.

   - **Schlüsselspeicheranbieter (KSP)** :  
     *(Gilt für:  Windows 8.1 und höher sowie Windows 10 und höher)*  
     
     Geben Sie an, wo der Schlüssel für das Zertifikat gespeichert wird. Wählen Sie aus den folgenden Werten aus:  
     - **Bei TPM-KSP (Trusted Platform Module) registrieren, falls vorhanden, andernfalls Software-KSP**
     - **Bei TPM-KSP (Trusted Platform Module) registrieren, andernfalls Fehler**
     - **Bei Passport registrieren, andernfalls Fehler (Windows 10 und höher)**
     - **Bei Software-KSP registrieren**

   - **Schlüsselverwendung**:  
     Wählen Sie Schlüsselverwendungsoptionen für das Zertifikat aus:

     - **Digitale Signatur**: Der Schlüsselaustausch wird nur gestattet, wenn der Schutz des Schlüssels durch eine digitale Signatur unterstützt wird.
     - **Schlüsselverschlüsselung**: Der Schlüsselaustausch wird nur gestattet, wenn der Schlüssel verschlüsselt ist.  

   - **Schlüsselgröße (Bits)** :  
     Wählen Sie die Anzahl der Bits aus, die im Schlüssel enthalten sein sollen.  

   - **Hashalgorithmus**:  
     *(Gilt für Android, Android Enterprise, Windows Phone 8.1, Windows 8.1 und höher sowie Windows 10 und höher)*  

     Wählen Sie einen der verfügbaren Hashalgorithmustypen, der für dieses Zertifikat verwendet werden soll. Wählen Sie die höchste Sicherheitsebene aus, die die verbundenen Geräten unterstützen.

   - **Stammzertifikat**:  
     Wählen Sie das *vertrauenswürdige Zertifikatprofil* aus, das Sie zuvor konfiguriert und den entsprechenden Benutzern und Geräten für dieses SCEP-Zertifikatprofil zugewiesen haben. Das vertrauenswürdige Zertifikatprofil wird zum Bereitstellen von Benutzern und Geräten mit dem Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle verwendet. Weitere Informationen zum vertrauenswürdigen Zertifikatprofil finden Sie unter [Exportieren des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle](certificates-configure.md#export-the-trusted-root-ca-certificate) und [Erstellen vertrauenswürdiger Zertifikatprofile](certificates-configure.md#create-trusted-certificate-profiles) in *Verwenden von Zertifikaten für die Authentifizierung in Intune*. Wenn Sie über eine Stammzertifizierungsstelle und eine ausstellende Zertifizierungsstelle verfügen, wählen Sie das vertrauenswürdige Stammzertifikatprofil aus, das der ausstellenden Zertifizierungsstelle zugeordnet ist.

   - **Erweiterte Schlüsselverwendung**:  
     Fügen Sie Werte für den beabsichtigten Zweck des Zertifikats hinzu. In den meisten Fällen erfordert das Zertifikat *Clientauthentifizierung*, damit der Benutzer bzw. das Gerät auf einem Server authentifiziert werden kann. Sie können ggf. weitere Schlüsselverwendungen hinzufügen.

   - **Verlängerungsschwellenwert (%)** :  
     Geben Sie den Prozentsatz der Zertifikatgültigkeitsdauer an, die verbleibt, bevor das Gerät eine Verlängerung des Zertifikats anfordert. Wenn Sie beispielsweise „20“ eingeben, wird versucht, das Zertifikat zu erneuern, wenn das Zertifikat bereits zu 80 % abgelaufen ist. Die Erneuerungsversuche werden fortgesetzt, bis die Erneuerung erfolgreich ist. Bei der Erneuerung wird ein neues Zertifikat generiert, das zu einem neuen öffentlichen/privaten Schlüsselpaar führt.

   - **SCEP-Server-URLs**:  
     Geben Sie mindestens eine URL für die NDES-Server ein, die Zertifikate über SCEP ausstellen. Geben Sie zum Beispiel *https://ndes.contoso.com/certsrv/mscep/mscep.dll* ein. Sie können ggf. zusätzliche SCEP-URLs für den Lastenausgleich hinzufügen, wenn URLs mit dem Profil nach dem Zufallsprinzip auf das Gerät übertragen werden. Wenn ein SCEP-Server nicht verfügbar ist, tritt bei der SCEP-Anforderung ein Fehler auf. Außerdem ist es möglich, dass die Cert-Anforderung bei nachfolgenden Eincheckvorgängen von Geräten für denselben nicht verfügbaren Server durchgeführt wird.

7. Klicken Sie zuerst auf **OK** und dann auf **Erstellen**. Das Profil wird erstellt und in der Liste *Gerätekonfiguration > Profile* angezeigt.

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>Vermeiden von Zertifikatsignieranforderungen mit Sonderzeichen als Escapezeichen
Es gibt ein bekanntes Problem bei SCEP- und PKCS-Zertifikatanforderungen, die einen Antragstellernamen (CN) mit einem oder mehreren der folgenden Sonderzeichen als Escapezeichen enthalten. Antragstellernamen, die eines der Sonderzeichen als Escapezeichen enthalten, führen zu einer CSR mit einem falschen Antragstellernamen. Ein falscher Antragstellername führt dazu, dass die SCEP-Challenge-Validierung fehlschlägt und kein Zertifikat ausgestellt wird.

Die Sonderzeichen sind:
- \+
- ,
- ;
- =

Wenn Ihr Antragstellername eines der Sonderzeichen enthält, verwenden Sie eine der folgenden Optionen, um diese Einschränkung zu umgehen:  
- Kapseln Sie den CN-Wert, der das Sonderzeichen enthält, mit Anführungszeichen.  
- Entfernen Sie das Sonderzeichen aus dem CN-Wert.  

**Beispielsweise** haben Sie einen Antragstellernamen, der als *Test user (TestCompany, LLC)* angezeigt wird.  Eine CSR, die einen CN mit dem Komma zwischen *TestCompany* und *LLC* umfasst, stellt ein Problem dar.  Das Problem kann vermieden werden, indem Sie den gesamten CN in Anführungszeichen setzen oder das Komma zwischen *TestCompany* und *LLC* entfernen:
- **Fügen Sie Anführungszeichen hinzu**: *CN=* ”Test User (TestCompany, LLC)”,OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **Entfernen Sie das Komma**: *CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 Allerdings tritt bei Versuchen, das Komma mithilfe eines umgekehrten Schrägstrichs mit einem Escapezeichen zu versehen, ein Fehler in den CRP-Protokollen auf:  
- **Mit Escapezeichen versehenes Komma**: *CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

Der Fehler ähnelt dem folgenden: 

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>Zuweisen des Zertifikatprofils
Weisen Sie SCEP-Zertifikatprofile auf die gleiche Weise zu, wie Sie [Geräteprofile für andere Zwecke bereitstellen](../configuration/device-profile-assign.md). Beachten Sie jedoch Folgendes, bevor Sie fortfahren:

- Wenn Sie Gruppen SCEP-Zertifikatprofile zuweisen, wird die vertrauenswürdige Zertifikatsdatei der Stammzertifizierungsstelle (wie im *vertrauenswürdigen Zertifikatprofil* angegeben) auf dem Gerät installiert. Das Gerät verwendet das SCEP-Zertifikatprofil, um eine Zertifikatanforderung für das vertrauenswürdige Zertifikat der Stammzertifizierungsstelle zu erstellen.  

- Das SCEP-Zertifikatprofil wird nur auf Geräten installiert, auf denen die Plattform ausgeführt wird, die Sie beim Erstellen des Zertifikatprofils angegeben haben.

- Sie können Zertifikatprofile zu Benutzer- oder Gerätesammlungen zuweisen.

- Damit Zertifikate möglichst schnell nach der Geräteregistrierung auf Geräten veröffentlicht werden können, weisen Sie das Zertifikatprofil besser einer Benutzergruppe zu (nicht einer Gerätegruppe). Wenn Sie es einer Gerätegruppe zuweisen, muss eine vollständige Geräteregistrierung stattfinden, bevor das Gerät Richtlinien empfängt.  

- Wenn Sie die Co-Verwaltung für Intune und Configuration Manager verwenden, bewegen Sie in Configuration Manager den [Schieberegler für Workloads](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads) für die Ressourcenzugriffsrichtlinie auf **Intune** oder **Intune-Pilot**. Diese Einstellung ermöglicht es Windows 10-Clients, den Prozess zur Anforderung des Zertifikats zu starten.

- Obwohl Sie das vertrauenswürdige Zertifikatprofil und das SCEP-Zertifikatprofil separat erstellen und zuweisen, müssen beide zugewiesen werden. Wenn nicht beide auf einem Gerät installiert sind, schlägt die SCEP-Zertifikatrichtlinie fehl. Stellen Sie sicher, dass alle vertrauenswürdigen Stammzertifikatprofile auch für dieselben Gruppen wie das SCEP-Profil bereitgestellt werden.


> [!NOTE]
> Wenn auf iOS-Geräten ein SCEP-Zertifikatprofil einem zusätzlichen Profil (z. B. einem WLAN- oder VPN-Profil) zugeordnet ist, erhält das Gerät ein Zertifikat für jedes der zusätzlichen Profile. Dadurch werden dem iOS-Gerät mehrere Zertifikate über die SCEP-Zertifikatanforderung bereitgestellt.  Wenn ein einzelnes Zertifikat gewünscht ist, müssen Sie PKCS-Zertifikate anstelle von SCEP-Zertifikaten verwenden.  Dies liegt an der unterschiedlichen Art und Weise, wie SCEP- und PKCS-Zertifikate an Geräte übermittelt werden.


## <a name="next-steps"></a>Nächste Schritte  

[Zuweisen von Profilen](../configuration/device-profile-assign.md)  
