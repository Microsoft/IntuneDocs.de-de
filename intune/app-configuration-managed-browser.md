---
title: Verwalten des Webzugriffs mit der Managed Browser-App
titlesuffix: Microsoft Intune
description: Stellen Sie die Managed Browser-Anwendung bereit, um das Webbrowsen und die Übertragung von Webdaten an andere Apps einzuschränken.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4d0c63c5e926c3f8893762a9be3b6bed2d6844c4
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Managed Browser ist eine Webbrowser-App, die Sie aus öffentlichen App-Stores für die Verwendung in Ihrer Organisation herunterladen können. Nach der Konfiguration mit Intune kann Managed Browser:
- Auf Unternehmenswebsites und SaaS-Apps mit einmaliger Anmeldung über den MyApps-Dienst zugreifen, während Webdaten geschützt bleiben.
- Mit einer Liste von URLs und Domänen vorkonfiguriert werden, um die Möglichkeit des Zugriffs des Benutzers auf Websites im Unternehmenskontext zu beschränken.
- Mit einer Startseite und von Ihnen angegebenen Lesezeichen vorkonfiguriert werden.

Da diese App die Integration mit dem Intune SDK aufweist, können Sie auch App-Schutzrichtlinien auf sie anwenden, wie beispielsweise:
- Steuern der Verwendung von Ausschneiden, Kopieren und Einfügen
- Verhindern von Bildschirmaufnahmen
- Sicherstellen, dass Links zu Inhalten, die von Benutzern ausgewählt werden, nur in anderen verwalteten Apps geöffnet werden

Weitere Information finden Sie unter [Was sind App-Schutzrichtlinien?](/intune/app-protection-policy.md).

Sie können diese Einstellungen auf Folgendes anwenden:

- Geräte, die bei Intune registriert sind
- Geräte, die bei einem anderen MDM-Produkt registriert sind
- Nicht verwaltete Geräte

Wenn Benutzer Managed Browser aus dem App Store installieren und die App nicht von Intune verwaltet wird, kann sie als einfacher Webbrowser mit Unterstützung für einmaliges Anmelden über die Microsoft MyApps-Website verwendet werden. Benutzer werden direkt an die MyApps-Website weitergeleitet, wo alle ihre bereitgestellten SaaS-Anwendungen angezeigt werden.
Während Managed Browser nicht von Intune verwaltet wird, kann nicht auf Daten aus anderen von Intune verwalteten Anwendungen zugegriffen werden. 

Managed Browser unterstützt nicht das Kryptografieprotokoll von Secure Sockets Layer-Version 3 (SSLv3).

Sie können Managed Browser-Richtlinien für die folgenden Gerätetypen erstellen:

-   Geräte unter Android 4 und höher

-   Geräte unter iOS 8.0 und höher

>[!IMPORTANT]
>Ab Oktober 2017 unterstützt die Intune Managed Browser-App für Android nur noch Geräte mit Android 4.4 oder höher. Die Intune Managed Browser-App unter iOS unterstützt nur noch Geräte mit iOS 9.0 oder höher.
>Frühere Versionen von Android und iOS können Managed Browser weiterhin verwenden, allerdings können keine neuen Versionen der App installiert werden, und einige App-Funktionen sind möglicherweise nicht verfügbar. Es wird empfohlen, dass Sie diese Geräte auf eine unterstützte Betriebssystemversion aktualisieren.


Intune Managed Browser unterstützt das Öffnen von Webinhalten von [Microsoft Intune-Anwendungspartnern](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="conditional-access-for-the-intune-managed-browser"></a>Bedingter Zugriff für Intune Managed Browser

Managed Browser wurde jetzt als Client-App für bedingten Zugriff freigegeben. Das bedeutet, dass Sie den Zugriff auf mit Azure AD verbundene Web-Apps über mobile Browser einschränken können, sodass die Benutzer nur noch Managed Browser verwenden können und der Zugriff über sämtliche anderen nicht geschützten Browser wie Safari oder Chrome blockiert wird. Dieser Schutz kann auf Azure-Ressourcen wie Exchange Online, SharePoint Online, das Office-Portal und sogar auf lokale Websites angewendet werden, die Sie für externe Benutzer über den [Azure AD-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) freigegeben haben. 

Wenn Sie verhindern wollen, dass mit Azure AD verbundene Web-Apps Intune Managed Browser auf mobilen Plattformen verwenden können, können Sie eine Azure AD-Richtlinie für bedingten Zugriff erstellen, über die zugelassene Client-Anwendungen erfordert werden. 

1. Klicken Sie im Azure-Portal auf **Azure Active Directory** > **Unternehmensanwendungen** > **Bedingter Zugriff** > **Neue Richtlinie**. 
2. Klicken Sie im Abschnitt **Zugriffssteuerungen** des Blatts auf die Option **Erteilen**. 
3. Klicken Sie auf **Genehmigte Client-App erforderlich**. 
4. Klicken Sie auf dem Blatt **Erteilen** auf **Auswählen**. Diese Richtlinie muss den Cloud-Apps zugewiesen sein, auf die nur über die Intune Managed Browser-App zugegriffen werden soll.

    ![Azure AD: Managed Browser-Richtlinie für bedingten Zugriff](./media/managed-browser-conditional-access-01.png)

5. Klicken Sie im Abschnitt **Zuweisungen** auf **Bedingungen** > **Client-Apps**. Dann wird das Blatt **Client-Apps** angezeigt.
6. Klicken Sie unter **Konfigurieren** auf **Ja**, um die Richtlinie auf bestimmte Client-Apps anzuwenden.
7. Überprüfen Sie, ob der **Browser** als Client-App ausgewählt ist.

    ![Azure AD: Managed Browser – Auswählen von Client-Apps](./media/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Wenn Sie festlegen möchten, welche nativen Apps (Apps, die nicht browserbasiert sind) auf die Cloudanwendungen zugreifen können, können Sie auch **Mobile apps and desktop clients** (Mobile Apps und Desktop-Clients) auswählen.

8. Klicken Sie im Bereich **Zuweisungen** auf **Benutzer und Gruppen**, und wählen Sie dann die Benutzer und Gruppen aus, die Sie dieser Richtlinie zuweisen möchten. 

    > [!NOTE]
    > Die Intune-App-Schutzrichtlinie muss außerdem auf Benutzer ausgerichtet sein. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md).

9. Klicken Sie im Abschnitt **Zuweisungen** auf **Cloud-Apps**, um auszuwählen, welche Apps mit dieser Richtlinie geschützt werden sollen.

Sobald diese Richtlinie konfiguriert wurde, müssen Benutzer Intune Managed Browser verwenden, um auf die mit Azure AD verbundenen Web-Apps zuzugreifen, die Sie mit dieser Richtlinie geschützt haben. Wenn Benutzer versuchen, dafür einen nicht verwalteten Browser zu verwenden, erhalten sie die Meldung, dass Intune Managed Browser verwendet werden muss.

Managed Browser unterstützt nicht die klassischen Richtlinien für den bedingten Zugriff. Weitere Informationen finden Sie unter [Migrieren klassischer Richtlinien in das Azure-Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

##  <a name="single-sign-on-to-azure-ad-connected-web-apps-in-the-intune-managed-browser"></a>Einmaliges Anmelden bei mit Azure AD verbundenen Web-Apps in Intune Managed Browser

Anwendungen unter iOS und Android, die für Intune Managed Browser konzipiert sind, können jetzt für alle Web-Apps (SaaS und lokal), die mit Azure AD verbunden sind, die Möglichkeit des einmaligen Anmeldens (Single Sign-on, SSO) nutzen. Wenn die Microsoft Authenticator-App unter iOS bzw. die Intune-Unternehmensportal-App unter Android vorhanden sind, können Benutzer von Intune Managed Browser auf mit Azure AD verbundene Web-Apps zugreifen und müssen dafür nicht erneut ihre Anmeldeinformationen eingeben.

Für SSO im Intune Managed Browser muss Ihr Gerät unter iOS durch Microsoft Authenticator und unter Android durch das Intune-Unternehmensportal registriert sein. Benutzer, die die Authenticator-App oder das Intune-Unternehmensportal verwenden, werden dazu aufgefordert, ihre Geräte zu registrieren, wenn sie zu einer mit Azure AD verbundenen Web-App im Intune Managed Browser navigieren, es sei denn, ihr Gerät wurde bereits von einer anderen Anwendung registriert. Nachdem das Gerät mit dem von Intune verwalteten Konto registriert wurde, ist für dieses Konto für mit Azure AD verbundene Web-Apps SSO aktiviert. 

> [!NOTE]
> Bei der Geräteregistrierung handelt es sich um einen einfachen Check-In beim Azure AD-Dienst. In diesem Zusammenhang wird keine vollständige Geräteregistrierung verwendet, und die IT-Abteilung erhält keine zusätzlichen Berechtigungen auf das Gerät.

## <a name="create-a-managed-browser-app-configuration"></a>Erstellen einer Managed Browser-App-Konfiguration

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3.  Gehen Sie zur Liste „Verwalten“ auf dem Blatt **Mobile Apps**, und wählen Sie die Option **App-Konfigurationsrichtlinien** aus.
4.  Wählen Sie auf dem Blatt **App-Konfigurationsrichtlinien** die Option **Hinzufügen** aus.
5.  Geben Sie auf dem Blatt **Konfigurationsrichtlinie hinzufügen** einen **Namen** und optional eine **Beschreibung** für die App-Konfigurationseinstellungen ein.
6.  Wählen Sie als Typ der **Geräteregistrierung** die Option **Verwaltete Apps** aus.
7.  Wählen Sie **Erforderliche App auswählen** aus, und wählen Sie auf dem Blatt **Ziel-Apps** die Option **Managed Browser** für iOS, für Android oder für beides aus.
8.  Wählen Sie **OK** aus, um zum Blatt **Konfigurationsrichtlinie hinzufügen** zurückzukehren.
9.  Wählen Sie **Konfigurationseinstellungen** aus. Auf dem Blatt **Konfiguration** definieren Sie Schlüssel-Wert-Paare, um Konfigurationen für Managed Browser bereitzustellen. In den folgenden Abschnitten erhalten Sie weitere Informationen zu den unterschiedlichen Schlüssel-Wert-Paaren, die Sie definieren können.
10. Wählen Sie abschließend **OK** aus.
11. Wählen Sie auf dem Blatt **Konfigurationsrichtlinie hinzufügen** die Option **Hinzufügen** aus.
12. Die neue Konfiguration wird erstellt und auf dem Blatt **App-Konfiguration** angezeigt.

>[!IMPORTANT]
>Derzeit verwendet Managed Browser die automatische Registrierung. Damit die App-Konfigurationen angewendet werden können, muss eine andere Anwendung auf dem Gerät bereits mit den Intune-App-Schutzrichtlinien verwaltet werden.

## <a name="assign-the-configuration-settings-you-created"></a>Zuweisen der erstellten Konfigurationseinstellungen

Sie weisen die Einstellungen Azure AD-Gruppen von Benutzern zu. Haben diese Benutzer die Managed Browser-App installiert, wird die App durch die angegebenen Einstellungen verwaltet.

1. Wählen Sie auf dem Blatt **Mobile Apps** im Intune-Dashboard für die Verwaltung von mobilen Anwendungen **App-Konfigurationsrichtlinie** aus.
2. Wählen Sie aus der Liste der App-Konfigurationen diejenige aus, die Sie zuweisen möchten.
3. Wählen Sie auf dem nächsten Blatt **Zuweisungen** aus.
4. Wählen Sie auf dem Blatt **Zuweisungen** die Azure AD-Gruppe aus, der Sie die App-Konfiguration zuweisen möchten, und wählen Sie dann **OK** aus.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Konfigurieren von Anwendungsproxyeinstellungen für Managed Browser

Intune Managed Browser und [Azure AD-Anwendungsproxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) können gemeinsam verwendet werden, um die folgenden Szenarios für Benutzer von iOS- und Android-Geräten zu unterstützen:

- Ein Benutzer lädt die Microsoft Outlook-App herunter und meldet sich an. Die Intune-App-Schutzrichtlinien werden automatisch angewendet. Diese verschlüsseln gespeicherte Daten und hindern den Benutzer daran, Unternehmensdateien auf nicht verwaltete Apps oder Speicherorte auf dem Gerät zu übertragen. Klickt der Benutzer dann auf einen Link zu einem Intranetwebsite in Outlook, können Sie angeben, dass der Link in der Managed Browser-App anstatt in einem anderen Browser geöffnet wird. Managed Browser erkennt, dass diese Intranetwebsite dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Benutzer werden automatisch über den Anwendungsproxy zur Authentifizierung mit jeder anwendbaren Multi-Factor Authentication und bedingtem Zugriff weitergeleitet, bevor sie die Intranetwebsite erreichen. Auf diese Website, die im Remotezugriff zuvor noch nicht gefunden werden konnte, kann nun zugegriffen werden, und der Link funktioniert in Outlook erwartungsgemäß.
- Ein Remotebenutzer öffnet die Managed Browser-Anwendung und navigiert mit der internen URL zu einer Intranetwebsite. Managed Browser erkennt, dass diese Intranetwebsite dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Benutzer werden automatisch über den Anwendungsproxy zur Authentifizierung mit jeder anwendbaren Multi-Factor Authentication und bedingtem Zugriff weitergeleitet, bevor sie die Intranetwebsite erreichen. Auf diese Website, die im Remotezugriff zuvor noch nicht gefunden werden konnte, kann nun zugegriffen werden.

### <a name="before-you-start"></a>Vorbereitung

- Richten Sie Ihre internen Anwendungen über den Azure AD-Anwendungsproxy ein.
    - Informationen zum Konfigurieren des Anwendungsproxys und zum Veröffentlichen von Anwendungen finden Sie in der [Setup-Dokumentation]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started). 
- Die Managed Browser-App muss in der Version 1.2.0 oder höher ausgeführt werden.
- Benutzer der Managed Browser-App verfügen über eine der App zugewiesene [Intune-App-Schutzrichtlinie]( app-protection-policy.md).

    > [!NOTE]
    > Es kann bis zu 24 Stunden dauern, bis aktualisierte Umleitungsdaten des Anwendungsproxys in Managed Browser in Kraft treten.


#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Schritt 1: Aktivieren der automatischen Umleitung zu Managed Browser aus Outlook
Outlook muss mit einer App-Schutzrichtlinie konfiguriert werden, mit der Einstellung **Anzeige von Webinhalten auf den Managed Browser beschränken** möglich ist.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Schritt 2: Zuweisen einer App-Konfigurationsrichtlinie für Managed Browser
Dieses Verfahren konfiguriert die Managed Browser-App, damit die App-Proxyumleitung verwendet wird. Geben Sie mit dem Verfahren zum Erstellen einer Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

| Key                                                             | Wert    |
|-----------------------------------------------------------------|----------|
| **com.microsoft.intune.mam.managedbrowser.AppProxyRedirection** | **TRUE** |

Weitere Informationen zur möglichen gemeinsamen Verwendung von Managed Browser und dem Azure AD-Anwendungsproxy für einheitlichen und geschützten Zugriff auf lokale Webb-Apps, finden Sie in einem Blogbeitrag zu Enterprise Mobility + Security mit dem Titel [Better together: Intune and Azure Active Directory team up to improve user access (Verwenden Sie Intune und Azure Active Directory gemeinsam, um den Benutzerzugriff zu verbessern)](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access).

## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Konfigurieren der Homepage für Managed Browser

Mit dieser Einstellung können Sie die Startseite konfigurieren, die Benutzern beim Starten von Managed Browser oder beim Erstellen einer neuen Registerkarte angezeigt wird. Geben Sie mit dem Verfahren zum Erstellen einer Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

|                                Key                                |                                                           Wert                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Geben Sie eine gültige URL ein. Ungültige URLs werden zur Sicherheit gesperrt.<br>Beispiel: <strong><https://www.bing.com></strong> |

## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Konfigurieren von Lesezeichen für Managed Browser

Mit dieser Einstellung können Sie einen Satz Lesezeichen konfigurieren, der den Benutzern von Managed Browser zur Verfügung steht.

- Diese Lesezeichen können von den Benutzern nicht gelöscht oder bearbeitet werden.
- Diese Lesezeichen werden oben in der Liste angezeigt. Alle von den Benutzern erstellten Lesezeichen werden unterhalb dieser Lesezeichen angezeigt.
- Wenn Sie die App-Proxyumleitung aktiviert haben, können Sie App-Proxy-Web-Apps mit deren interner oder externer URL hinzufügen.

Geben Sie mit dem Verfahren zum Erstellen einer Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

|                                Key                                 |                                                                                                                                                                                                                                                         Wert                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | Der Wert für diese Konfiguration ist eine Liste von Lesezeichen. Jedes Lesezeichen besteht aus dem Lesezeichentitel und der Lesezeichen-URL. Trennen Sie Titel und URL mit dem <strong>& #124;</strong>-Zeichen.<br><br>Beispiel: <strong>Microsoft Bing&#124;<https://www.bing.com></strong><br><br>Zum Konfigurieren von mehreren Lesezeichen trennen Sie jedes Paar mit einem doppelten <strong>&#124;&#124;</strong>-Zeichen.<br><br>Beispiel: <strong>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;<https://www.contoso.com></strong> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Angeben von zugelassenen und blockierten URLs für Managed Browser

Geben Sie mit dem Verfahren zum Erstellen einer Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

|Key|Wert|
|-|-|
|Es stehen die folgenden Optionen zur Auswahl:<br><br>- Angeben von zugelassenen URLs (nur diese URLs sind zugelassen, auf keine weiteren Websites kann zugegriffen werden): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br>- Angeben von blockierten URLs (auf alle anderen Websites kann zugegriffen werden): <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**|Der entsprechende Wert für den Schlüssel ist eine Liste mit URLs. Geben Sie alle URLs, die Sie zulassen oder blockieren möchten, als einen einzelnen Wert ein, der durch einen senkrechten Strich **&#124;** getrennt ist.<br><br>Beispiele:<br><br>`URL1\|URL2\|URL3`</code><br>`http://*.contoso.com/*\|https://*.bing.com/*\|https://expenses.contoso.com`|

>[!IMPORTANT]
>Geben Sie nicht beide Schlüssel an. Wenn beide Schlüssel für einen Benutzer eingerichtet sind, wird der Schlüssel für zugelassene URLs verwendet, da dies die restriktivste Option ist.
>Stellen Sie außerdem sicher, dass Sie keine wichtigen Seiten wie Ihre Unternehmenswebsites blockieren.

### <a name="url-format-for-allowed-and-blocked-urls"></a>URL-Format für zulässige und blockierte URLs
Nachfolgend wird erläutert, welche Formate und Platzhalter Sie zum Festlegen von URLs in den Zulassungs- und Blockierungslisten verwenden können:

- Sie können das Platzhaltersymbol (**&#42;**) gemäß den Regeln in der folgenden Liste mit zulässigen Mustern verwenden:

- Stellen Sie sicher, dass Sie bei der Eingabe in die Liste allen URLs **http** oder **https** voranstellen.

- Sie können Portnummern in der Adresse angeben. Wenn Sie keine Portnummer angeben, werden folgende Werte verwendet:

  -   Port 80 für http

  -   Port 443 für https

  Die Verwendung von Platzhaltern für die Portnummer wird nicht unterstützt. Zum Beispiel werden <strong>http&colon;//www&period;contoso&period;com:*;</strong> und <strong>http&colon;//www&period;contoso&period;com: /*;</strong> nicht unterstützt.

- In der folgenden Tabelle sind die zulässigen Muster aufgeführt, die Sie zum Festlegen von URLs verwenden können:

|                  URL                  |                     Details                      |                                                Treffer                                                |                                Stimmt nicht überein mit                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        http://www.contoso.com         |              Entspricht einer einzelnen Seite               |                                            www.contoso.com                                            |  host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/   |
|          http://contoso.com           |              Entspricht einer einzelnen Seite               |                                             contoso.com/                                              | host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com |
|    <http://www.contoso.com/&#42>;     | Entspricht allen URLs, die mit „www.contoso.com“ beginnen |      www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows      |              host.contoso.com<br /><br />host.contoso.com/images              |
|    http://&#42;.contoso.com/&#42;     |     Entspricht allen Unterdomänen unter „contoso.com“     | developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos |                               contoso.host.com                                |
|     http://www.contoso.com/images     |             Entspricht einem einzelnen Ordner              |                                        www.contoso.com/images                                         |                          www.contoso.com/images/dogs                          |
|       http://www.contoso.com:80       |  Entspricht einer einzelnen Seite mit einer Portnummer   |                                       http://www.contoso.com:80                                       |                                                                               |
|        https://www.contoso.com        |          Entspricht einer einzelnen, sicheren Seite           |                                        https://www.contoso.com                                        |                            http://www.contoso.com                             |
| <http://www.contoso.com/images/&#42>; |    Entspricht einem einzelnen Ordner und allen Unterordnern    |                  www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats                   |                            www.contoso.com/videos                             |

- Im Folgenden Beispiele für Eingaben, die nicht unterstützt werden:

  - &#42;.com

  - &#42;.contoso/&#42;

  - www.contoso.com/&#42;images

  - www.contoso.com/&#42;images&#42;pigs

  - www.contoso.com/page&#42;

  - IP-Adressen

  - https://&#42;

  - http://&#42;

  - http://www.contoso.com:&#42;

  - http://www.contoso.com: /&#42;

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Zugreifen auf Protokolle von verwalteten Apps mithilfe des Managed Browsers unter iOS

Endbenutzer, auf deren iOS-Gerät der Managed Browser installiert ist, können den Verwaltungsstatus aller von Microsoft veröffentlichten Apps anzeigen. Sie können Protokolle für die Problembehandlung ihrer verwalteten iOS-Apps senden.

1. Öffnen Sie die iOS-**Einstellungen**.
2. Wählen Sie die Anwendungseinstellungen für den **Managed Browser** aus.
3. Schalten Sie **Intune-Diagnose aktivieren** um, um den Browser in den Problembehandlungsmodus zu versetzen.
4. Öffnen Sie den **Managed Browser**. Klicken Sie auf **Intune-App-Status anzeigen**, um die Richtlinieneinstellungen für einzelne Anwendungen zu überprüfen.
5. Drücken Sie **Erste Schritte** und **Protokolle freigeben** oder **Protokolle an Microsoft senden**, um die Problembehandlungsprotokolle an Ihren IT-Administrator oder an Microsoft zu senden.

Sie können den Browser außerdem auch aus der App im Problembehandlungsmodus öffnen.

1. Öffnen Sie den Managed Browser.
2. Geben Sie im Adressfeld `about:intunehelp` ein.
Der Browser wird im Problembehandlungsmodus gestartet.

Eine Liste der in den App-Protokollen gespeicherten Einstellungen finden Sie unter [Prüfung der App-Schutzprotokolle in Managed Browser](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Sicherheit und Datenschutz für Managed Browser

-   Einstellungen, die Benutzer für den integrierten Browser auf ihren Geräten vornehmen, werden von Managed Browser nicht verwendet. Managed Browser kann auf diese Einstellungen nicht zugreifen.

-   Wenn Sie die Option **Einfache PIN für den Zugriff erforderlich** oder **Unternehmensanmeldeinformationen für den Zugriff erforderlich** in einer App-Schutzrichtlinie konfigurieren, die Managed Browser zugeordnet ist, und ein Benutzer auf der Authentifizierungsseite den Hilfelink auswählt, kann er beliebige Websites besuchen. Dies gilt unabhängig davon, ob sie in der Richtlinie einer Blockierungsliste hinzugefügt wurden.

-   Managed Browser kann den Zugriff auf Websites nur blockieren, wenn direkt darauf zugegriffen wird. Der Zugriff auf die Website wird nicht blockiert, wenn dafür Zwischendienste (z.B. ein Übersetzungsdienst) verwendet werden.

-   Um die Authentifizierung und den Zugriff auf die Intune-Dokumentation zuzulassen, ist **&#42;.microsoft.com** von den Zulassungs- oder Blockierungslisten ausgenommen. und immer zulässig.

### <a name="turn-off-usage-data"></a>Deaktivieren von Nutzungsdaten
Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung von Managed Browser, um Microsoft-Produkte und -Dienste zu verbessern. Benutzer können die Erfassung von Daten mithilfe der Einstellung für **Nutzungsdaten** auf ihren Geräten deaktivieren. Sie haben keine Kontrolle über die Erfassung dieser Daten.


-   Auf iOS-Geräten können von Benutzern besuchte Websites, deren Zertifikat abgelaufen oder nicht vertrauenswürdig ist, nicht geöffnet werden.
-   Einstellungen, die Benutzer für den integrierten Browser auf ihren Geräten vornehmen, werden von Managed Browser nicht verwendet. Managed Browser kann auf diese Einstellungen nicht zugreifen.

-   Wenn Sie die Option **Einfache PIN für den Zugriff erforderlich** oder **Unternehmensanmeldeinformationen für den Zugriff erforderlich** in einer App-Schutzrichtlinie konfigurieren, die Managed Browser zugeordnet ist, und ein Benutzer auf der Authentifizierungsseite den Hilfelink auswählt, kann er beliebige Websites besuchen. Dies gilt unabhängig davon, ob sie in der Richtlinie einer Blockierungsliste hinzugefügt wurden.

-   Managed Browser kann den Zugriff auf Websites nur blockieren, wenn direkt darauf zugegriffen wird. Der Zugriff auf die Website wird nicht blockiert, wenn dafür Zwischendienste (z.B. ein Übersetzungsdienst) verwendet werden.

-   Um die Authentifizierung und den Zugriff auf die Intune-Dokumentation zuzulassen, ist **&#42;.microsoft.com** von den Zulassungs- oder Blockierungslisten ausgenommen. und immer zulässig.

### <a name="turn-off-usage-data"></a>Deaktivieren von Nutzungsdaten
Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung von Managed Browser, um Microsoft-Produkte und -Dienste zu verbessern. Benutzer können die Erfassung von Daten mithilfe der Einstellung für **Nutzungsdaten** auf ihren Geräten deaktivieren. Sie haben keine Kontrolle über die Erfassung dieser Daten.

## <a name="next-steps"></a>Nächste Schritte

- [Was sind App-Schutzrichtlinien?](app-protection-policy.md)
