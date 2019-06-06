---
title: Nur-Anwendung-Authentifizierung von Intune Data Warehouse
titleSuffix: Microsoft Intune
description: Dieses Thema beschreibt die Authentifizierung nur von Data Warehouse-Anwendungen für Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/31/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9d3cd7dfb28d26451da95861fe9a3011c2556b1
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454033"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Nur-Anwendung-Authentifizierung von Intune Data Warehouse

Sie können eine Anwendung mithilfe von Azure Active Directory (Azure AD) einrichten und bei Intune Data Warehouse authentifizieren. Dieser Vorgang eignet sich für Websites, Apps und Hintergrundprozesse, bei denen die Anwendung keinen Zugriff auf Benutzeranmeldeinformationen haben soll. In den folgenden Schritte autorisieren Sie mithilfe von OAuth 2.0 Ihre Anwendung bei Azure AD.

## <a name="authorization"></a>Autorisierung

Azure Active Directory (Azure AD) bietet Ihnen über OAuth 2.0 die Möglichkeit, den Zugriff auf Webanwendungen und Web-APIs in Ihrem Azure AD-Mandanten zu autorisieren. Dieser Leitfaden zeigt, wie Sie Ihre Anwendung mit C# authentifizieren. Der Codefluss zur Autorisierung mit OAuth 2.0 wird in Abschnitt 4.1 der OAuth 2.0-Spezifikation beschrieben. Weitere Informationen finden Sie unter [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorisieren des Zugriffs zu Webanwendungen mithilfe von OAuth 2.0 und Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).


## <a name="azure-keyvault"></a>Azure-Schlüsseltresor (Key Vault)

Beim folgenden Prozess wird zum Verarbeiten und Konvertieren eines App-Schlüssels eine private Methode verwendet. Diese private Methode wird SecureString genannt. Alternativ können Sie den Azure-Schlüsseltresor zum Speichern von App-Schlüsseln verwenden. Weitere Informationen finden Sie unter [Key Vault](https://azure.microsoft.com/services/key-vault/) (Schlüsseltresor).

## <a name="create-a-web-app"></a>Erstellen einer Web-App

In diesem Abschnitt stellen Sie Details zu der Web-App bereit, auf die bei Intune verwiesen werden soll. Bei einer Web-App handelt es sich um eine Client/Server-Anwendung. Der Server stellt die Web-App bereit, welche die Benutzeroberfläche, den Inhalt und die Funktionen umfasst. Der App-Typ wird separat im Web verwaltet. Um einer Web-App Zugriff auf Intune zu gewähren, verwenden Sie Intune. Der Datenfluss wird von der Web-App initiiert. 

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2.  Suchen Sie im oberen Bereich des Azure-Portals im Feld **Ressourcen, Dienste und Dokumente durchsuchen** nach **Azure Active Directory**.
3.  Wählen Sie unter **Dienste** im Dropdownmenü **Azure Active Directory** aus.
4.  Wählen Sie **App-Registrierungen** aus.
5.  Klicken Sie auf **Registrierung einer neuen Anwendung**, um das Blatt **Erstellen** anzuzeigen.
6.  Fügen Sie auf dem Blatt **Erstellen** die Details Ihrer App hinzu:

    - Name der App, z. B. *Intune Nur-Anwendung-Authentifizierung*.
    - **Anwendungstyp**. Wählen Sie **Web-App/API** aus, um eine App hinzuzufügen, die eine Webanwendung und/oder eine Web-API darstellt.
    - **Anmelde-URL** der Anwendung. Dies ist die Stelle, an die der Benutzer während des Authentifizierungsprozesses automatisch navigiert. Hier muss er nachweisen, dass er tatsächlich die Person ist, als die er sich ausgibt. Weitere Informationen finden Sie unter [Was ist Anwendungszugriff und Single Sign-On (SSO) bei Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

7.  Klicken Sie unten auf dem Blatt **Erstellen** auf **Erstellen**.

    >[!NOTE] 
    > Kopieren Sie die **Anwendungs-ID** auf dem Blatt **Registrierte App** zur späteren Verwendung.

## <a name="create-a-key"></a>Erstellen eines Schlüssels

In diesem Abschnitt generiert Azure AD einen Schlüsselwert für die App.

1.  Wählen Sie auf dem Blatt **App-Registrierungen** Ihre neu erstellte App aus, um das Blatt für die App anzuzeigen.
2.  Wählen Sie im oberen Bereich des Blatts **Einstellungen** aus, um das Blatt **Einstellungen** anzuzeigen.
3.  Wählen Sie **Schlüssel** auf dem Blatt **Einstellungen** aus.
4.  Fügen Sie den Schlüssel **Beschreibung**, unter **Läuft ab** eine Gültigkeitsdauer und einen **Wert** für den Schlüssel hinzu.
5.  Klicken Sie auf **Speichern**, um die Schlüssel der Anwendung zu speichern und zu aktualisieren.
6.  Sie müssen den generierten Schlüsselwert (Base64-codiert) kopieren.

    >[!NOTE] 
    > Der Schlüsselwert wird nicht mehr angezeigt, wenn Sie das Blatt **Schlüssel** verlassen haben. Sie können den Schlüssel später nicht mehr von diesem Blatt abrufen. Kopieren Sie ihn zur späteren Verwendung.

## <a name="grant-application-permissions"></a>Erteilen von Anwendungsberechtigungen

In diesem Abschnitt erteilen Sie Berechtigungen für die Anwendungen.

1.  Wählen Sie **Erforderliche Berechtigungen** auf dem Blatt **Einstellungen** aus.
2.  Klicken Sie auf **Hinzufügen**.
3.  Wählen Sie **API hinzufügen** aus, um das Blatt **Hiermit wählen Sie eine API aus** anzuzeigen.
4.  Wählen Sie **Microsoft Intune-API (MicrosoftIntuneAPI)** aus, und klicken Sie dann auf dem Blatt **Hiermit wählen Sie eine API au** auf **Auswählen**. Der Schritt **Berechtigungen auswählen** ist aktiviert, und das Blatt **Zugriff aktivieren** wird angezeigt.
5.  Wählen Sie im Abschnitt **Anwendungsberechtigungen** die Option **Data Warehouse-Informationen von Microsoft Intune abrufen** aus.
6.  Klicken Sie auf dem Blatt **Zugriff aktivieren** auf **Auswählen**.
7.  Klicken Sie auf dem Blatt **API-Zugriff hinzufügen** auf **Fertig**.
8.  Klicken Sie auf dem Blatt **Erforderliche Berechtigungen** auf **Berechtigungen erteilen**, und klicken Sie beim Höherstufen auf **Ja**, um alle vorhandenen Berechtigungen zu aktualisieren, über die diese Anwendung bereits verfügt.

## <a name="generate-token"></a>Generieren eines Tokens

Erstellen Sie mit Visual Studio ein Konsolen-App (.NET Framework)-Projekt, das .NET Framework unterstützt und C# als Codesprache verwendet.

1.  Wählen Sie **Datei** > **Neu** > **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.
2.  Wählen Sie auf der linken Seite **Visual C#** aus, um alle .NET Framework-Projekte anzuzeigen.
3.  Wählen Sie **Konsolen-App (.NET Framework)** aus, fügen Sie einen Anwendungsnamen hinzu, und klicken Sie dann auf **OK**, um die App zu erstellen.
4.  Wählen Sie im **Projektmappen-Explorer** die Option **Program.cs** aus, um den Code anzuzeigen.
5.  Fügen Sie im Projektmappen-Explorer einen Verweis auf die Assembly `System.Configuration` hinzu.
6.  Wählen Sie im Popupmenü **Hinzufügen** > **Neues Element** aus. Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.
7.  Wählen Sie auf der linken Seite unter **Visual C#** die Option **Code** aus.
8.  Wählen Sie **Klasse** aus, ändern Sie den Namen der Klasse in *IntuneDataWarehouseClass.cs*, und klicken Sie auf **Hinzufügen**.
9.  Fügen Sie in der Methode <code>Main</code> den folgenden Code hinzu:

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

10. Fügen Sie zusätzliche Namespaces hinzu, indem Sie am Anfang der Codedatei den folgenden Code hinzufügen:

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

11. Fügen Sie hinter der Methode <code>Main</code> die folgende private Methode zum Verarbeiten und Konvertieren des App-Schlüssels hinzu:

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

12. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie dann **NuGet-Pakete verwalten** aus.
13. Suchen Sie nach *Microsoft.IdentityModel.Clients.ActiveDirectory*, und installieren Sie das zugehörige Microsoft NuGet-Paket.
14. Wählen Sie im **Projektmappen-Explorer** die Datei *App.config* aus, und öffnen Sie sie.
15. Fügen Sie den Abschnitt <code>appSettings</code> hinzu, damit der XML-Code wie folgt aussieht:

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

16. Aktualisieren Sie die Werte <code>appId</code>, <code>appKey</code> und <code>tenantDomain</code>, damit diese mit den eindeutigen anwendungsbezogenen Werten übereinstimmen.
17. Erstellen Sie Ihre App.

    >[!NOTE] 
    > Zusätzlichen Implementierungscode finden Sie unter [Intune Data Warehouse-Codebeispiel](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp ).

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zum Azure-Schlüsseltresor finden Sie unter [Was ist der Azure-Schlüsseltresor?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)

