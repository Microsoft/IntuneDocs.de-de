---
title: Problembehandlung bei der JAMF pro-Integration mit Microsoft InTune
titleSuffix: Microsoft Intune
description: Vorschläge zur Behebung einiger der häufigsten Probleme bei der Integration von JAMF pro für Mac-Geräte mit Microsoft InTune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e92e3442e1347cb1a2cd1c737078912b74f075c9
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817637"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Behandeln von Problemen bei der Integration von JAMF pro mit Microsoft InTune

Dieser Artikel unterstützt InTune-Administratoren beim verstehen und Beheben von Problemen bei der Integration von JAMF pro für macOS in InTune.

> [!TIP]  
> Ein Großteil der Informationen in diesem Artikel war ursprünglich in [Beheben von Problemen bei der Integration von JAMF in Microsoft InTune](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune) auf Support.Microsoft.com aufgetreten.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit der Problembehandlung beginnen, erfassen Sie grundlegende Informationen, um das Problem zu verdeutlichen und die Zeit für die Suche nach einer Lösung zu verkürzen Wenn beispielsweise ein Problem mit der JAMF-InTune-Integration auftritt, überprüfen Sie immer, ob alle Voraussetzungen erfüllt sind. Überprüfen Sie vor Beginn der Problembehandlung die folgenden Punkte:

- Überprüfen Sie die Voraussetzungen für die [Integration von JAMF pro in InTune](conditional-access-integrate-jamf.md#prerequisites).
- Alle Benutzer müssen über Microsoft InTune-und Microsoft Aad Premium P1-Lizenzen verfügen. 
- Sie müssen über ein Benutzerkonto verfügen, das über Microsoft InTune Integrations Berechtigungen in der JAMF pro-Konsole verfügt.
- Sie müssen über ein Benutzerkonto verfügen, das über globale Administrator Berechtigungen in Azure verfügt.


Beachten Sie die folgenden Informationen, wenn Sie die JAMF pro-Integration in InTune untersuchen: 
- Wie lautet die genaue Fehlermeldung?
- Wo ist die Fehlermeldung?
- Wann fing das Problem an?  Hat die JAMF pro-Integration in InTune jemals funktioniert?
- Wie viele Benutzer sind betroffen? Sind alle Benutzer betroffen oder nur einige?
- Wie viele Geräte sind betroffen? Sind alle Geräte betroffen oder nur einige?
 

## <a name="common-problems"></a>Häufige Probleme 

Die folgenden Informationen können Ihnen helfen, häufige Probleme für Geräte zu identifizieren und zu beheben, nachdem Sie die Integration von InTune und JAMF pro eingerichtet haben.  

| Problem   | Weitere Informationen                  |
|-----------------|--------------------------|
| **Geräte werden in JAMF pro als nicht reagierend markiert**  | [Geräte können nicht mit JAMF pro oder mit Azure AD einchecken.](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **Mac-Geräte Aufforderung zur Eingabe der Keychain-Anmeldung beim Öffnen einer APP-Geräte können nicht registriert werden**  | [Benutzer werden aufgefordert, Ihr Kennwort einzugeben, damit Apps bei Azure AD registriert werden können](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **Geräte können nicht registriert werden**  | Die folgenden Gründe können zutreffen: <br> **-** [ ***Ursache 1*** : die JAMF pro-app in Azure verfügt über falsche Berechtigungen.](#cause-1) <br> **-** [ ***Ursache 2*** : Es gibt ein Problem für den *nativen JAMF-macOS-Connector* in Azure AD](#cause-2) <br> **-** [ ***Ursache 3*** : der Benutzer verfügt nicht über eine gültige InTune-oder JAMF-Lizenz.](#cause-3) <br> **-** [ ***Ursache 4*** : der Benutzer hat den JAMF-Self-Service nicht verwendet, um die Unternehmensportal-APP zu starten.](#cause-4) <br> **-** [ ***Ursache 5*** : InTune-Integration ist deaktiviert.](#cause-5) <br> **-** [ ***Ursache 6*** : das Gerät wurde zuvor bei InTune registriert, oder der Benutzer hat versucht, das Gerät mehrmals zu registrieren.](#cause-6) <br> **-** [ ***Ursache 7*** -jamfaad fordert Zugriff auf einen "Microsoft Workplace Join Schlüssel" aus der Keychain des Benutzers an.](#cause-7) |
|  **Mac-Gerät zeigt Konformität in InTune an, aber nicht kompatibel in Azure** | [Probleme mit der Geräteregistrierung](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Doppelte Einträge werden in der InTune-Konsole für Mac-Geräte angezeigt, die mit JAMF registriert wurden.** | [Mehrere Registrierungen für dasselbe Gerät](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **Die Konformitäts Richtlinie kann das Gerät nicht auswerten.** | [Richtlinie zielt auf Gerätegruppen ab](#compliance-policy-fails-to-evaluate-the-device) |
| **Das Zugriffs Token für Microsoft Graph-API konnte nicht abgerufen werden.** | Die folgenden Gründe können zutreffen: <br> --[Berechtigungen für die JAMF pro-app in Azure](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> - [abgelaufene Lizenz für JAMF oder InTune](#a-license-required-for-jamf-intune-integration-has-expired) <br> **--** [Ports sind nicht geöffnet](#the-required-ports-arent-open-on-your-network) .|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Geräte werden in JAMF pro als nicht reagierend markiert  

**Ursache**: die folgenden Ursachen sind häufig, wenn Geräte von JAMF pro als *nicht reagierend* gekennzeichnet werden:

- Gerät kann nicht mit JAMF pro einchecken.  
  JAMF pro erwartet, dass Geräte alle 15 Minuten einchecken. Geräte werden durch JAMF als nicht reagierend gekennzeichnet, wenn Sie über einen Zeitraum von 24 Stunden nicht eingecheckt werden können.  

- Das Gerät kann nicht mit Azure AD eingecheckt werden.  
  Bei erfolgreicher Registrierung bei Azure AD erhalten macOS-Geräte ein Azure-Token:
  - Dieses Token wird alle 12 Stunden aktualisiert.   
  - Wenn die tokenaktualisierung 24 Stunden oder mehr fehlschlägt, kennzeichnet JAMF pro das Gerät als nicht reagierend.  
  - Wenn das Azure-Token abläuft, werden Benutzer aufgefordert, sich bei Azure anzumelden, um ein neues Token zu erhalten. Ein Aktualisierungs Token für Azure Access wird alle sieben Tage generiert.

**Lösung**  
Nachdem ein Gerät von JAMF pro als *nicht reagierend* gekennzeichnet wurde, muss sich der registrierte Benutzer des Geräts anmelden, um den nicht reagierenden Zustand zu korrigieren. Dabei muss es sich um den Benutzer handeln, dem das Konto in der von InTune angehörenden Identität in seiner Anmelde Schlüsselkette beigetreten ist.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>Mac-Geräte Eingabeaufforderung für die Schlüsselbund Anmeldung beim Öffnen einer APP  

Nachdem Sie die Integration von InTune und JAMF pro konfiguriert und Richtlinien für den bedingten Zugriff bereitgestellt haben, erhalten Benutzer von Geräten, die mit JAMF pro verwaltet werden, beim Öffnen Microsoft Office 365-Anwendungen, wie z. b. Teams, Outlook und andere apps, die Azure benötigen AD-Authentifizierung. 

Beim Öffnen von Microsoft Teams wird z. b. eine Eingabeaufforderung mit Text angezeigt, der dem folgenden Beispiel ähnelt:

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**Ursache**: diese Eingabe Aufforderungen werden von JAMF pro für jede anwendbare App generiert, für die Azure AD Registrierung erforderlich ist. 

**Lösung**   
An der Eingabeaufforderung muss der Benutzer sein Geräte Kennwort angeben, um sich bei Azure AD anzumelden. Zu den Optionen gehören:
- **Verweigern** : Melden Sie sich nicht an, und verwenden Sie die APP nicht.
- **Zulassen** : einmalige Anmeldung. Wenn die APP das nächste Mal geöffnet wird, werden Sie zur erneuten Anmeldung aufgefordert.
- **Immer zulassen** : die Anmelde Informationen werden für die Anwendung zwischengespeichert. Wenn die APP das nächste Mal geöffnet wird, werden Sie nicht aufgefordert, sich anzumelden.  

Wenn Sie für eine APP *immer zulassen* auswählen, wird diese APP nur für die zukünftige Anmeldung genehmigt. Zusätzliche apps fordert zur Authentifizierung auf, bis Sie auch als *immer zulassen*festgelegt sind. Zwischengespeicherte Anmelde Informationen für eine APP können nicht von einer anderen APP verwendet werden.  

### <a name="devices-fail-to-register"></a>Geräte können nicht registriert werden  

Es gibt verschiedene Häufige Gründe für Macintosh-Geräte, die nicht registriert werden können.  

#### <a name="cause-1"></a>Ursache 1  

**Die JAMF pro Enterprise-Anwendung in Azure hat die falsche Berechtigung oder verfügt über mehr als eine Berechtigung.**  

  Wenn Sie die app in Azure erstellen, müssen Sie alle Standard-API-Berechtigungen entfernen und InTune dann eine einzige Berechtigung *update_device_attributes*zuweisen. 

  **Lösung**  
  Überprüfen Sie die Berechtigungen für die JAMF-APP, die Sie in Azure AD erstellt haben, und korrigieren Sie Sie. Weitere Informationen finden Sie [im Verfahren So erstellen Sie eine Anwendung für JAMF in Azure AD](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory). 

#### <a name="cause-2"></a>Ursache 2  

**Die **native JAMF-macOS-Connector** -App wurde nicht in Ihrem Azure AD Mandanten erstellt, oder die Zustimmung für den Connector wurde von einem Konto signiert, das keine globalen Administratorrechte hat.**  

  **Lösung**  
  Weitere Informationen finden Sie im Abschnitt *Konfigurieren der macOS-InTune-Integration* in [Integration mit Microsoft InTune](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html) auf docs.JAMF.com. 

#### <a name="cause-3"></a>Ursache 3

**Der Benutzer verfügt nicht über eine gültige InTune-oder JAMF-Lizenz.**  

  Wenn keine gültige Lizenz vorliegt, kann der folgende Fehler auftreten, der darauf hinweist, dass die JAMF-Lizenz abgelaufen ist:  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **Lösung**
  - JAMF-Lizenz: wenden Sie sich an JAMF, um Hilfe beim Abrufen einer neuen Lizenz für JAMF zu erhalten.  
  - InTune-Lizenz: weisen Sie dem Benutzer eine gültige Lizenz zu, oder wenden Sie sich an Microsoft oder Ihren Partner, um zu erfahren, wie Sie eine aktuelle Lizenz erhalten.

#### <a name="cause-4"></a>Ursache 4  

**Der Benutzer hat den *JAMF-Self-Service* nicht zum Starten der Unternehmensportal-App verwendet.**

Damit ein Gerät erfolgreich registriert und bei InTune über JAMF registriert werden kann, muss der Benutzer den JAMF-Self-Service verwenden, um die Intune-Unternehmensportal zu öffnen. Wenn der Benutzer das Unternehmensportal manuell öffnet, registriert und registriert das Gerät ohne zugehörige Verbindung mit JAMF.  

Überprüfen Sie die Unternehmensportal-App auf dem Gerät, um zu bestimmen, für welchen Dienst das Gerät registriert und registriert wurde. Wenn Sie über JAMF registriert werden, sollten Sie eine Benachrichtigung erhalten, um die Self-Service-APP zu öffnen und Änderungen vorzunehmen.

In der Unternehmensportal-App kann der Benutzer **`Not registered`** sehen, und ein Eintrag ähnlich dem folgenden Beispiel wird möglicherweise in den Unternehmensportal Protokollen angezeigt:  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**Lösung**  
So ändern Sie die Registrierungs Quelle von InTune in JAMF:
1. [Aufheben der Registrierung Ihres macOS-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos). Informationen zu weiteren Komplikationen für Geräte, die nicht vollständig aus InTune entfernt werden, finden Sie in dieser Liste der Ursachen in der [*Ursache 6*](#cause-6) .  

2. Verwenden Sie auf dem Gerät den JAMF-Self-Service, um die Unternehmensportal-APP zu öffnen, und registrieren Sie das Gerät anschließend bei InTune. Diese Aufgabe erfordert, dass Sie [JAMF für die Bereitstellung der Unternehmensportal-App für macOS verwendet](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)haben und [eine Richtlinie in JAMF pro erstellt haben, die das Benutzergerät bei Azure AD registriert](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory).  

3. Wenn das Portal geöffnet wird, werden Sie auf dem ersten angezeigten Bildschirm aufgefordert, sich anzumelden. Verwenden Sie Ihr Geschäfts-, Schul- oder Unikonto.  

4. Das Unternehmensportal bestätigt Ihre Kontoinformationen und zeigt Ihnen Ihren Status zur Geräteregistrierung und Gerätekompatibilität an. Gelbe Dreiecke heben die Aktionen hervor, die Sie ergreifen müssen, um Ihr macOS-Gerät für die Schule, die Uni oder die Arbeit zu sichern. Klicken Sie auf „Begin“ (Starten), um die Registrierung zu starten.  

5. Geben Sie die Anmeldeinformationen für Ihren Computer ein, wenn Sie dazu aufgefordert werden.  
     
Das Registrieren Ihres Geräts für die Verwaltung kann einige Minuten beanspruchen. Während dieser Zeit können Sie auf dem Gerät andere Vorgänge ausführen. Sobald das Setup des Unternehmenszugriffs abgeschlossen ist, wird Ihnen eine Meldung angezeigt, die Sie darüber informiert.

#### <a name="cause-5"></a>Ursache 5  

**Die Intune-Integration ist deaktiviert.**

Wenn die Intune-Integration deaktiviert ist, erhalten Benutzer ein Popup Fenster im Unternehmensportal mit der folgenden Meldung, wenn Sie versuchen, ein Gerät zu registrieren:  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

Der JAMF pro-Server sendet bei deaktivierter Integration einen Impuls an die Intune-Server, der InTune mitteilt, dass die Integration deaktiviert ist. 

**Lösung**  
Aktivieren Sie die Intune-Integration in JAMF pro erneut. Weitere Informationen finden Sie unter [Konfigurieren der Microsoft Intune-Integration in Jamf Pro](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro).


#### <a name="cause-6"></a>Ursache 6  

**Das Gerät wurde zuvor bei InTune registriert, oder der Benutzer hat versucht, das Gerät mehrmals zu registrieren.**

Wenn die Registrierung eines Geräts bei JAMF aufgehoben, aber nicht ordnungsgemäß aus InTune entfernt wird oder mehrere Registrierungs Versuche durchgeführt werden, werden möglicherweise mehrere Instanzen desselben Geräts im Portal angezeigt. Dies bewirkt, dass die JAMF-Registrierung fehlschlägt.

**Lösung**  
1. Starten Sie auf dem Mac das **Terminal**.
2. Führen **Sie sudo JAMF removemdmprofile**aus.
3. Führen **Sie sudo JAMF removeframework**aus.
4. Löschen Sie auf dem JAMF pro-Server den Inventur Daten Satz des Computers.
5. Löschen Sie das Gerät aus azuread.
6. Löschen Sie die folgenden Dateien auf dem Gerät, sofern diese vorhanden sind:
   - /Library/Application Support/com. Microsoft. companyportal. userContext. info
   - /Library/Application-Unterstützung/com. Microsoft. companyportal
   - /Library/Application Support/com. JAMF Software. Selfservice. Mac
   - /Library/saved-Anwendung
   - State/com. JAMF Software. Selfservice. Mac. savedState
   - /Library/saved Anwendungs Status/com. Microsoft. companyportal. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/Bibliothek/Cookies/com. Microsoft. companyportal. binarycookies
   - /Users/<username>/Bibliothek/Cookies/com. JAMF. Management. jamfaad. binarycookies
   - com. Microsoft. companyportal
   - com. Microsoft. companyportal. hockeysdk
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft-Sitzungs Transport Schlüssel (öffentliche und private Schlüssel)
   - Microsoft Workplace Join-Schlüssel (öffentliche und private Schlüssel)
7. Entfernen Sie alles aus der Keychain auf dem Gerät, das auf *Microsoft*, *InTune*oder *Unternehmensportal*verweist, einschließlich DeviceLogin.Microsoft.com-Zertifikaten. Entfernen Sie *JAMF* -Verweise außer dem öffentlichen und privaten JAMF-Schlüssel. 
   > [!IMPORTANT]  
   > Durch das Entfernen des öffentlichen und des privaten Schlüssels wird die Geräteregistrierung unterbricht.

8. Löschen Sie die folgenden Einträge, die Sie finden:  
   - Art: Anwendungs Kennwort; Konto: com. Microsoft. workplacejoin. Thumbprint
   - Art: Anwendungs Kennwort; Konto: com. Microsoft. workplacejoin. registereduserprincipalname
   - Art: Zertifikat; Ausgestellt von: ms-Organization-Access
   - Kind: Identitäts Präferenz; Name (ADFS STS-URL, falls vorhanden): https://adfs\<DNSName>.com/adfs/ls
   - Kind: Identitäts Präferenz; Name: https://enterpriseregistration.windows.net
   - Kind: Identitäts Präferenz; Name: https://enterpriseregistration.windows.net/  
9. Starten Sie das Mac-Gerät neu.
10. Deinstallieren Sie Unternehmensportal vom Gerät.
11. Wechseln Sie zu Portal.Manage.Microsoft.com, und löschen Sie alle Instanzen des Mac-Geräts. Warten Sie mindestens 30 Minuten, bevor Sie mit dem nächsten Schritt fortfahren.
12. Registrieren Sie das Gerät erneut bei JAMF pro.
13. Self-Service erneut öffnen und Registrierungs Richtlinie starten.


#### <a name="cause-7"></a>Ursache 7  

**Jamfaad fordert den Zugriff auf einen "Microsoft Workplace Join-Schlüssel" aus der Keychain des Benutzers an.**

Während der Registrierung erhält der Benutzer eines macOS-Geräts die folgende Eingabeaufforderung, um den jamfaad-Zugriff auf einen Schlüssel aus der Keychain zu gestatten: 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**Lösung**  
Damit das Gerät erfolgreich bei Azure AD registriert werden kann, erfordert JAMF, dass der Benutzer sein Konto Kennwort bereitstellt, und wählen Sie **zulassen**aus.

Diese Anforderung ähnelt der Anforderung für [Mac-Geräte bei der Eingabeaufforderung für die Schlüsselbund Anmeldung beim Öffnen einer APP](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)weiter oben in diesem Artikel.  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Mac-Gerät zeigt Konformität in InTune an, aber nicht kompatibel in Azure  

**Ursache**: die folgenden Bedingungen können bewirken, dass ein Gerät in InTune als kompatibel angezeigt wird, aber nicht als kompatibel in Azure:  
- Das Gerät ist nicht ordnungsgemäß registriert.  
- Das Gerät wurde mehrmals registriert, ohne dass ein Cleanup erforderlich ist.

**Lösung**  
Um dieses Problem zu beheben, führen Sie weiter oben in diesem Artikel die Lösung für [*Ursache 6*](#cause-6) für *Geräte nicht registrieren*aus. 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Doppelte Einträge werden in der InTune-Konsole für Mac-Geräte angezeigt, die mit JAMF registriert wurden.  
 
**Ursache**: ein Gerät wird mehrmals bei InTune registriert und wird in der Regel nach dem Entfernen aus InTune erneut registriert.  

Wenn ein Gerät aus der InTune-und JAMF pro-Integration entfernt wird, können einige Daten zurückgelassen werden, was dazu führen kann, dass aufeinanderfolgende Registrierungen doppelte Einträge erstellen.  

**Lösung**  
Um dieses Problem zu beheben, führen Sie weiter oben in diesem Artikel die Lösung für [*Ursache 6*](#cause-6) für *Geräte nicht registrieren*aus. 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>Die Konformitäts Richtlinie kann das Gerät nicht auswerten.  

**Ursache**: die JAMF-Integration in InTune unterstützt keine Konformitäts Richtlinien für Gerätegruppen. 

**Lösung**  
Ändern Sie die Konformitäts Richtlinie für macOS-Geräte, die Benutzergruppen zugewiesen werden sollen. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Das Zugriffs Token für Microsoft Graph-API konnte nicht abgerufen werden.

Sie erhalten die folgende Fehlermeldung:

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

Die Ursache für diesen Fehler kann eine der folgenden Gründe haben: 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Bei der JAMF pro-Anwendung in Azure liegt ein Berechtigungsproblem vor.

Beim Registrieren der JAMF pro-app in Azure ist eine der folgenden Bedingungen aufgetreten:  
- Die APP hat mehr als eine Berechtigung erhalten.
- Die Option " **Administrator Zustimmung für *\<your Company >* gewähren** " wurde nicht ausgewählt.  

**Lösung**  
Weitere Informationen finden Sie weiter oben in diesem Artikel unter Lösung für Ursache 1 für [Geräte nicht registrieren](#devices-fail-to-register).

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Eine für die JAMF-InTune-Integration erforderliche Lizenz ist abgelaufen.

**Lösung**: sehen Sie sich die Lösung für Ursache 3 für [Geräte nicht registrieren an](#devices-fail-to-register). 

#### <a name="the-required-ports-arent-open-on-your-network"></a>Die erforderlichen Ports sind in Ihrem Netzwerk nicht geöffnet.

**Lösung**: Überprüfen Sie die Informationen für Netzwerkports unter [Voraussetzungen](conditional-access-integrate-jamf.md#prerequisites) für die Integration von JAMF pro in InTune.


## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zur [Integration von JAMF pro in InTune](conditional-access-integrate-jamf.md)