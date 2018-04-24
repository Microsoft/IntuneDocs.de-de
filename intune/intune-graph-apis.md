---
title: Verwenden von Azure AD für den Zugriff auf Intune-APIs in Microsoft Graph
titlesuffix: Microsoft Intune
description: Beschreibung der Schritte, damit Apps über Azure AD auf die Intune-APIs in Microsoft Graph zugreifen können.
keywords: Intune Graph-API C# PowerShell Berechtigungsrollen
author: vhorne
manager: dougeby
ms.author: victorh
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f6e5955b690eedf06872171fcc22eb86a0f7764e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Verwenden von Azure AD für den Zugriff auf die Intune-APIs in Microsoft Graph

Die [Microsoft Graph-API](https://developer.microsoft.com/graph/) unterstützt jetzt Microsoft Intune mit bestimmten APIs und Berechtigungsrollen.  Die Microsoft Graph-API verwendet für die Authentifizierung und Zugriffsteuerung Azure Active Directory (Azure AD).  
Für den Zugriff auf die Intune-APIs in Microsoft Graph ist Folgendes erforderlich:

- Eine Anwendungs-ID mit:

    - Der Berechtigung, Azure AD und die Microsoft Graph-APIs aufzurufen.
    - Berechtigungsbereichen, die für bestimmte Anwendungsaufgaben relevant sind

- Benutzeranmeldeinformationen mit:

    - Zugriffsberechtigung für den Azure AD-Mandanten, der der Anwendung zugeordnet ist
    - Rollenberechtigungen zur Unterstützung der Anwendungsberechtigungsbereiche

- Der App durch den Endbenutzer erteilte Berechtigung zum Ausführen von Anwendungsaufgaben im Azure-Mandanten

Inhalt dieses Artikels

- Erläuterung der Registrierung einer Anwendung mit Zugriff auf die Microsoft Graph-API und relevante Berechtigungsrollen

- Beschreibung der Berechtigungsrollen der Intune-API

- Bereitstellung von Beispielen für die Authentifizierung der Intune-API für C# und PowerShell

- Beschreibung der Unterstützung mehrerer Mandanten

Weitere Informationen finden Sie unter:

- [Autorisieren des Zugriffs auf Webanwendungen mit OAuth 2.0 und Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Erste Schritte mit der Azure AD-Authentifizierung](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Integrieren von Anwendungen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [Grundlegendes zu OAuth 2.0](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Registrieren von Apps, um die Microsoft Graph-API zu verwenden

So registrieren Sie eine App, um die Microsoft Graph-API zu verwenden:

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) mit Administratoranmeldeinformationen an.

    Dazu können Sie Folgendes verwenden:
    - Die Administratorkonto des Mandanten
    - Ein Mandantenbenutzerkonto mit aktivierter Einstellung **Benutzer können Anwendungen registrieren**

2.  Wählen Sie im Menü **Azure Active Directory** &gt; **App-Registrierungen** aus.

    <img src="./media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3.  Wählen Sie entweder **Neue Anwendungsregistrierung**, um eine neue Anwendung erstellen, oder eine vorhandene Anwendung.  (Wenn Sie eine vorhandene Anwendung wählen, überspringen Sie den nächsten Schritt.)

4.  Geben Sie auf dem Blatt **Erstellen** Folgendes an:

    1.  Einen **Namen** für die Anwendung (der angezeigt wird, wenn Benutzer sich anmelden).

    2.  Werte für **Anwendungstyp** und **Umleitungs-URI**.

        Diese unterscheiden sich entsprechend Ihren Anforderungen. Wenn Sie beispielsweise eine Azure AD-[Authentifizierungsbibliothek](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) verwenden, legen Sie **Anwendungstyp** auf `Native` und **Umleitungs-URI** auf `urn:ietf:wg:oauth:2.0:oob` fest.

        <img src="media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        Weitere Informationen finden Sie unter [Authentifizierungsszenarien für Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

5.  Auf dem Blatt „Anwendung“:

    1.  Notieren Sie sich den Wert von **Anwendungs-ID**.

    2.  Wählen Sie **Einstellungen** &gt; **API-Zugriff** &gt; **Erforderliche Berechtigungen**.

    <img src="media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6.  Wählen Sie auf dem Blatt **Erforderliche Berechtigungen** nacheinander **Hinzufügen** &gt; **API-Zugriff hinzufügen** &gt; **API auswählen**.

    <img src="media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7.  Wählen Sie auf dem Blatt **API auswählen** nacheinander **Microsoft Graph** &gt; **Auswählen**.  Das Blatt **Zugriff aktivieren** wird geöffnet, auf dem die für Ihre Anwendung verfügbaren Berechtigungsbereiche aufgeführt sind.

    <img src="media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    Wählen Sie die für Ihre App erforderlichen Rollen, indem Sie ein Häkchen links neben den gewünschten Namen setzen.  Weitere Informationen zu bestimmten Berechtigungsbereichen in Intune finden Sie unter [Intune-Berechtigungsbereiche](#intune-permission-scopes).  Weitere Informationen zu anderen Berechtigungsbereichen für die Graph-API finden Sie in der [Microsoft Graph-Berechtigungsreferenz](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

    Wählen Sie für optimale Ergebnisse nur so viele Rollen, wie für die Implementierung Ihrer Anwendung erforderlich sind.

    Klicken Sie abschließend auf **Auswählen** und **Fertig**, um Ihre Änderungen zu speichern.

An diesem Punkt haben Sie auch folgende Möglichkeiten:

- Sie können allen Mandantenkonten die Berechtigung zum Verwenden der App ohne Angabe von Anmeldeinformationen erteilen.  

    Zu diesem Zweck wählen Sie **Berechtigungen** und akzeptieren die Bestätigungsaufforderung.

    Wenn Sie die Anwendung zum ersten Mal ausführen, werden Sie aufgefordert, die App-Berechtigung für die ausgewählten Rollen zu erteilen.

    <img src="media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- Sie können die App Benutzern außerhalb Ihres Mandanten zur Verfügung stellen.  (Dies ist normalerweise nur für Partner erforderlich, die mehrere Mandanten/Organisationen unterstützen.)  

    Gehen Sie hierzu folgendermaßen vor:

  1. Wählen sie auf dem Blatt der Anwendung **Manifest**, um das Blatt **Manifest bearbeiten** zu öffnen.

     <img src="media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. Ändern Sie den Wert der Einstellung `availableToOtherTenants` in `true`.

  3. Speichern Sie die Änderungen.

## <a name="intune-permission-scopes"></a>Intune-Berechtigungsbereiche

Azure AD und Microsoft Graph verwenden Berechtigungsbereiche zum Steuern des Zugriffs auf Unternehmensressourcen.  

Berechtigungsbereiche (auch _OAuth-Bereiche_ genannt) steuern den Zugriff auf bestimmte Intune-Entitäten und deren Eigenschaften. In diesem Abschnitt werden die Berechtigungsbereiche für die Features der Intune-API zusammengefasst.

Weitere Informationen:
- [Azure AD-Authentifizierung](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Anwendungsberechtigungsbereiche](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

Wenn Sie Microsoft Graph Berechtigungen erteilen, können Sie angeben, dass folgende Bereiche den Zugriff auf die Intune-Features steuern sollen. In der folgenden Tabelle werden die Berechtigungsbereiche der Intune-API zusammengefasst.  Die erste Spalte enthält den Namen der Funktion entsprechend der Anzeige im Azure-Portal, die zweite den Namen des Berechtigungsbereichs.

Einstellung _Zugriff aktivieren_ | Bereichsname
:--|:--
__Remoteaktionen mit Auswirkungen auf Benutzer auf Microsoft Intune-Geräten ausführen__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Microsoft Intune-Geräte lesen und schreiben__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Microsoft Intune-Geräte lesen__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Einstellungen für die rollenbasierte Zugriffssteuerung von Microsoft Intune-Geräten lesen und schreiben__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Einstellungen für die rollenbasierte Zugriffssteuerung von Microsoft Intune-Geräten lesen__ | [DeviceManagementRBAC.Read.All](#rac=ro)
__Microsoft Intune-Apps lesen und schreiben__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Microsoft Intune-Apps lesen__ | [DeviceManagementApps.Read.All](#app-ro)
__Microsoft Intune-Gerätekonfiguration und -Richtlinien lesen und schreiben__ | [DeviceManagementConfiguration.ReadWrite.All](#cfg-rw)
__Microsoft Intune-Gerätekonfiguration und -Richtlinien lesen__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Microsoft Intune-Konfiguration lesen und schreiben__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Microsoft Intune-Konfiguration lesen__ | [DeviceManagementServiceConfig.Read.All](#svc-ra)

Die Tabelle enthält die Einstellungen in der Reihenfolge, in der sie im Azure-Portal angezeigt werden. In den folgenden Abschnitten werden die Bereiche in alphabetischer Reihenfolge beschrieben.

Derzeit erfordern alle Intune-Berechtigungsbereiche Administratorzugriff.  Dies bedeutet, dass Sie zum Ausführen von Apps oder Skripts, die auf die Ressourcen der Intune-API zugreifen, entsprechende Anmeldeinformationen benötigen.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Apps lesen__

- Ermöglicht Lesezugriff auf die folgenden Eigenschaften und den Status der Entität:
    - Mobile Apps
    - Kategorien mobiler Apps
    - App-Schutzrichtlinien
    - App-Konfigurationen

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Apps lesen und schreiben__

- Ermöglicht die gleichen Vorgänge wie __DeviceManagementApps.Read.All__

- Ermöglicht zudem Änderungen an den folgenden Entitäten:

    - Mobile Apps
    - Kategorien mobiler Apps
    - App-Schutzrichtlinien
    - App-Konfigurationen

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Gerätekonfiguration und -Richtlinien lesen__

- Ermöglicht Lesezugriff auf die folgenden Eigenschaften und den Status der Entität:
    - Gerätekonfiguration
    - Gerätekonformitätsrichtlinie
    - Benachrichtigungen

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Gerätekonfiguration und -Richtlinien lesen und schreiben__

- Ermöglicht die gleichen Vorgänge wie __DeviceManagementConfiguration.Read.All__

- Apps können auch die folgenden Entitäten erstellen, zuweisen, löschen und ändern:
    - Gerätekonfiguration
    - Gerätekonformitätsrichtlinie
    - Benachrichtigungen

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- Einstellung **Zugriff aktivieren**: __Remoteaktionen mit Auswirkungen auf Benutzer auf Microsoft Intune-Geräten ausführen__

- Erlaubt die folgenden Remoteaktionen auf einem verwalteten Gerät:
    - Außerkraftsetzen
    - Zurücksetzen
    - Kennung zurücksetzen/wiederherstellen
    - Remotesperre
    - Modus für verlorene Geräte aktivieren/deaktivieren
    - PC bereinigen
    - Neustart
    - Benutzer von gemeinsam genutzten Gerät löschen

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Geräte lesen__

- Ermöglicht Lesezugriff auf die folgenden Eigenschaften und den Status der Entität:
    - Verwaltetes Gerät
    - Gerätekategorie
    - Erkannte App
    - Remoteaktionen
    - Informationen zu Schadsoftware

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Geräte lesen und schreiben__

- Ermöglicht die gleichen Vorgänge wie __DeviceManagementManagedDevices.Read.All__

- Apps können auch die folgenden Entitäten erstellen, löschen und ändern:
    - Verwaltetes Gerät
    - Gerätekategorie

- Die folgenden Remoteaktionen sind ebenfalls zulässig:
    - Geräte suchen
    - Aktivierungssperre umgehen
    - Remoteunterstützung anfordern

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- Einstellung **Zugriff aktivieren**: __Einstellungen für die rollenbasierte Zugriffssteuerung von Microsoft Intune-Geräten lesen__

- Ermöglicht Lesezugriff auf die folgenden Eigenschaften und den Status der Entität:
    - Rollenzuweisungen
    - Rollendefinitionen
    - Ressourcenvorgänge

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- Einstellung **Zugriff aktivieren**: __Einstellungen für die rollenbasierte Zugriffssteuerung von Microsoft Intune-Geräten lesen und schreiben__

- Ermöglicht die gleichen Vorgänge wie __DeviceManagementRBAC.Read.All__

- Apps können auch die folgenden Entitäten erstellen, zuweisen, löschen und ändern:
    - Rollenzuweisungen
    - Rollendefinitionen

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Konfiguration lesen__

- Ermöglicht Lesezugriff auf die folgenden Eigenschaften und den Status der Entität:
    - Geräteregistrierung
    - Apple Push Notification-Zertifikat
    - Apple-Programm zur Geräteregistrierung
    - Apple Volume Purchase Program
    - Exchange-Connector
    - Geschäftsbedingungen
    - Verwaltung von Ausgaben für Telekommunikation
    - PKI in der Cloud
    - Branding
    - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- Einstellung **Zugriff aktivieren**: __Microsoft Intune-Konfiguration lesen und schreiben__

- Ermöglicht die gleichen Vorgänge wie „DeviceManagementServiceConfig.Read.All_“

- Apps können auch die folgenden Intune-Features konfigurieren:
    - Geräteregistrierung
    - Apple Push Notification-Zertifikat
    - Apple-Programm zur Geräteregistrierung
    - Apple Volume Purchase Program
    - Exchange-Connector
    - Geschäftsbedingungen
    - Verwaltung von Ausgaben für Telekommunikation
    - PKI in der Cloud
    - Branding
    - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Beispiele für die Azure AD-Authentifizierung

In diesem Abschnitt wird gezeigt, wie Azure AD in Ihre C#- und PowerShell-Projekte integriert wird.

Bei jedem Beispiel müssen Sie eine Anwendungs-ID angeben, die mindestens den Berechtigungsbereich `DeviceManagementManagedDevices.Read.All` hat (siehe oben).

Wenn Sie eines der Beispiel testen, erhalten Sie ggf. die HTTP-Statusfehlermeldung 403 (Unzulässig):

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

Wenn dies erfolgt, überprüfen Sie Folgendes:

- Ob Sie die Anwendungs-ID in eine ID geändert haben, die für das Verwenden der Microsoft Graph-API und des Berechtigungsbereichs `DeviceManagementManagedDevices.Read.All` autorisiert ist.

- Ob die Anmeldeinformationen Ihres Mandanten administrative Funktionen unterstützen.

- Ob Ihr Code den gezeigten Beispielen ähnlich ist.


### <a name="authenticate-azure-ad-in-c"></a>Authentifizieren von Azure AD in C\#

Dieses Beispiel zeigt, wie Sie C# zum Abrufen einer Liste von Geräten verwenden, die Ihrem Intune-Konto zugeordnet sind.

1.  Starten Sie Visual Studio, und erstellen Sie dann ein neues Visual C#-App-Konsolenprojekt (.NET Framework).

2.  Geben Sie einen Namen für das Projekt und nach Wunsch weitere Details ein.

    <img src="media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3.  Fügen Sie im Projektmappen-Explorer das NuGet-Paket mit der Microsoft ADAL dem Projekt hinzu.

    1.  Klicken Sie mit der rechten Maustaste auf den Projektmappen-Explorer.
    2.  Wählen Sie **NuGet-Pakete verwalten** &gt; **Durchsuchen** aus.
    3.  Wählen Sie `Microsoft.IdentityModel.Clients.ActiveDirectory` aus, und klicken Sie anschließend auf **Installieren**.

    <img src="media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4.  Fügen Sie am Anfang der Datei **Program.cs** die folgenden Anweisungen ein:

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5.  Fügen Sie eine Methode zum Erstellen des Autorisierungsheaders hinzu:

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    Ändern Sie den Wert von `application_ID` entsprechend in einen Wert, der dem Berechtigungsbereich `DeviceManagementManagedDevices.Read.All` mindestens erteilt wurde (siehe oben).

6. Fügen Sie eine Methode zum Abrufen der Geräteliste hinzu:

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7.  Ändern Sie **Main** so, dass **GetMyManagedDevices** aufgerufen wird:

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8.  Kompilieren Sie Ihr Programm, und führen Sie es aus.  

Wenn Sie das Programm erstmals ausführen, sollten Sie zwei Eingabeaufforderungen erhalten.  Die erste fordert Ihre Anmeldeinformationen an, die zweite erteilt Berechtigungen für die Anforderung `managedDevices`.  

Zur Bezugnahme sehen Sie hier das vollständige Programm:

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Authentifizieren von Azure AD (PowerShell)

Das folgende PowerShell-Skript verwendet das AzureAD-PowerShell-Modul zur Authentifizierung.  Weitere Informationen finden Sie unter [Azure Active Directory PowerShell, Version 2](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) und [Intune PowerShell-Beispiele](https://github.com/microsoftgraph/powershell-intune-samples).

In diesem Beispiel aktualisieren Sie den Wert von `$clientID` so, dass er einer gültigen Anwendungs-ID entspricht.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>Unterstützen mehrerer Mandanten und Partner

Wenn Organisationen mit eigenen Azure AD-Mandanten von Ihrer Organisation unterstützt werden, möchten Sie ggf. Ihren Clients erlauben, Ihre Anwendung in ihren entsprechenden Mandanten zu nutzen.

Gehen Sie hierzu folgendermaßen vor:

1.  Stellen Sie sicher, dass das Konto im Azure AD-Zielmandanten vorhanden ist.

2.  Stellen Sie sicher, dass Ihr Mandantenkonto die Registrierung von Anwendungen durch Benutzer zulässt (siehe **Benutzereinstellungen**).

3.  Richten Sie eine Beziehung zwischen jedem Mandanten ein.  

    Gehen Sie hierfür so vor:

    ein. Definieren Sie im [Microsoft Partner Center](https://partnercenter.microsoft.com/) eine Beziehung mit Ihrem Client und seiner E-Mail-Adresse.

    b. Laden Sie den Benutzer ein, Gast Ihres Mandanten zu werden.

So laden Sie den Benutzer ein, Gast Ihres Mandanten zu werden

1.  Wählen Sie **Gastbenutzer hinzufügen** im Bereich **Schnellaufgaben** aus.

    <img src="media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2.  Geben Sie die E-Mail-Adresse des Clients ein, und fügen Sie (optional) eine personalisierte Nachricht für die Einladung hinzu.

    <img src="media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3.  Klicken Sie auf **Einladen**.

Dem Benutzer wird eine Einladung gesendet.

   <img src="media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   Der Benutzer muss auf den Link **Erste Schritte** klicken, um Ihre Einladung anzunehmen.

Nachdem die Beziehung eingerichtet oder Ihre Einladung akzeptiert wurde, fügen Sie das Benutzerkonto der **Verzeichnisrolle** hinzu.

Denken Sie daran, den Benutzer bei Bedarf anderen Rollen hinzuzufügen. Um beispielsweise dem Benutzer das Verwalten von Intune-Einstellungen zu erlauben, müssen Sie entweder ein **globaler Administrator** oder **Intune-Dienstadministrator** sein.

Ferner gilt Folgendes:

- Verwenden Sie https://portal.office.com, um Ihrem Benutzerkonto eine Intune-Lizenz zuzuweisen.

- Ändern Sie den Anwendungscode so, dass die Azure AD-Mandantendomäne des Clients und nicht Ihre eigene authentifiziert wird.

    Angenommen, die Mandantendomäne heißt `contosopartner.onmicrosoft.com` und die des Clients `northwind.onmicrosoft.com`. Sie müssen dann Ihren Code so ändern, dass Sie beim Mandanten des Clients authentifiziert werden.

    Um dies in einer C#-Anwendung basierend auf dem vorherigen Beispiel zu tun, ändern Sie den Wert der Variablen `authority`:

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    in

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
