---
title: Verwalten des Webzugriffs in Unternehmen mit einem durch eine Richtlinie geschützten Browser
titleSuffix: Microsoft Intune
description: Verwenden Sie einen durch eine Intune-Richtlinie geschützten Browser, um das Browsen und die Webdatenübertragung in Unternehmen zu verwalten.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 52f907b8762322684ec9e21910745a197c3dbe4e
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564317"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Verwalten des Webzugriffs durch einen mittels Microsoft Intune-Richtlinien geschützte Browser

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mit einem durch eine Intune-Richtlinie geschützten Browser (Microsoft Edge oder Intune Managed Browser) können Sie sicher sein, dass für den Zugriff auf Unternehmenswebsites immer Sicherheitsmaßnahmen in Kraft treten.  Nach der Konfiguration mit Intune können geschützte Browser von folgenden Punkten profitieren:

- Anwendungsschutzrichtlinien
- Bedingter Zugriff
- Einmaliges Anmelden
- Anwendungskonfigurationseinstellungen
- Integration des Azure-Anwendungsproxys

## <a name="microsoft-edge-support"></a>Microsoft Edge-Unterstützung

Sie können die Microsoft Edge-Unterstützung für Unternehmensszenarios auf iOS- und Android-Geräten verwenden. Microsoft Edge unterstützt alle Verwaltungsszenarios, die Intune Managed Browser auch unterstützt, und enthält Verbesserungen der Benutzerfreundlichkeit. Die folgenden durch Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures sind verfügbar:

- **Doppelte Identitäten:** Benutzer können sowohl Geschäftskonten als auch persönliche Konten zum Browsen hinzufügen. Die beiden Identitäten sind vollständig voneinander getrennt, ähnlich wie bei Office 365 und Outlook. Intune-Administratoren können die gewünschten Richtlinien für geschütztes Browsen im Geschäftskonto festlegen. 
- **Integration von Intune-App-Schutzrichtlinien:** Administratoren können jetzt App-Schutzrichtlinien für Microsoft Edge erstellen. U. a. können sie in diesem Rahmen festlegen, wie und ob Benutzer Inhalte ausschneiden, kopieren und einfügen können, ob Bildschirmaufnahmen zulässig sind, und sie können sicherstellen, dass von Benutzern ausgewählte Links nur in anderen verwalteten Apps geöffnet werden.
- **Azure-Anwendungspoxyintegration:** Administratoren können den Zugriff auf SaaS-Apps und Web-App festlegen, um sicherzustellen, dass browserbasierte Apps nur im sicheren Microsoft Edge-Browser ausgeführt werden, egal ob Endbenutzer eine Verbindung über ein Unternehmensnetzwerk oder über das Internet herstellen. 
- **Verknüpfungen zu Favoriten und der Startseite:** Für einen einfacheren Zugriff können Administratoren URLs festlegen, die unter Favoriten angezeigt werden, wenn sich Benutzer im Unternehmenskontext befinden. Administratoren können auch eine Verknüpfung zur Startseite hinzufügen, die als primäre Verknüpfung angezeigt wird, wenn der Unternehmensbenutzer eine neue Seite oder eine neue Registerkarte in Microsoft Edge öffnet.

Microsoft Intune-Schutzrichtlinien für Microsoft Edge tragen dazu bei, die Daten und Ressourcen Ihres Unternehmens zu schützen. Der durch Intune geschützte Microsoft Edge-Browser stellt sicher, dass die Ressourcen Ihres Unternehmens nicht nur in nativ installierten Apps geschützt sind, sondern auch, wenn darauf über einen Webbrowser zugegriffen wird.

## <a name="getting-started"></a>Erste Schritte

Der Microsoft Edge-Browser und Intune Managed Browser sind Webbrowser-Apps, die Sie und Ihre Endbenutzer aus öffentlichen App-Stores für die Verwendung in Ihrer Organisation herunterladen können. 

Betriebssystemanforderungen für Browserrichtlinien:
- Android 4 und höher oder
- iOS 8.0 oder höher

Frühere Versionen von Android und iOS können Managed Browser weiterhin verwenden, allerdings können keine neuen Versionen der App installiert werden, und einige App-Funktionen sind möglicherweise nicht verfügbar. Es wird empfohlen, dass Sie diese Geräte auf eine unterstützte Betriebssystemversion aktualisieren.

>[!NOTE]
>Managed Browser unterstützt nicht das Kryptografieprotokoll von Secure Sockets Layer-Version 3 (SSLv3).


## <a name="application-protection-policies-for-protected-browsers"></a>Anwendungsschutzrichtlinien für geschützte Browser

Weil Microsoft Edge und Managed Browser in das Intune SDK integriert sind, können Sie auch App-Schutzrichtlinien darauf anwenden, z.B.:
- Steuern der Verwendung von Ausschneiden, Kopieren und Einfügen
- Verhindern von Bildschirmaufnahmen
- Sicherstellen, dass Unternehmenslinks nur in verwalteten Apps und Browsern geöffnet werden

Weitere Information finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md).

Sie können diese Einstellungen auf Folgendes anwenden:

- Geräte, die bei Intune registriert sind
- Geräte, die bei einem anderen MDM-Produkt registriert sind
- Nicht verwaltete Geräte

>[!NOTE]
>Wenn Benutzer Managed Browser aus dem App Store installieren und die App nicht von Intune verwaltet wird, kann sie als einfacher Webbrowser mit Unterstützung für einmaliges Anmelden über die Microsoft MyApps-Website verwendet werden. Benutzer werden direkt an die MyApps-Website weitergeleitet, wo alle ihre bereitgestellten SaaS-Anwendungen angezeigt werden.
Da Managed Browser oder Microsoft Edge nicht von Intune verwaltet werden, können diese Browser nicht auf Daten aus anderen von Intune verwalteten Anwendungen zugreifen. 


## <a name="conditional-access-for-protected-browsers"></a>Bedingter Zugriff für geschützte Browser

Managed Browser wurde jetzt als Client-App für bedingten Zugriff freigegeben. Das bedeutet, dass Sie den Zugriff auf mit Azure AD verbundene Web-Apps über mobile Browser einschränken können, sodass die Benutzer nur noch Managed Browser verwenden können und der Zugriff über sämtliche anderen nicht geschützten Browser wie Safari oder Chrome blockiert wird. Dieser Schutz kann auf Azure-Ressourcen wie Exchange Online, SharePoint Online, das Microsoft 365 Admin Center und sogar auf lokale Websites angewendet werden, die Sie für externe Benutzer über den [Azure AD-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) freigegeben haben. 

Wenn Sie verhindern wollen, dass mit Azure AD verbundene Web-Apps Intune Managed Browser auf mobilen Plattformen verwenden können, können Sie eine Richtlinie für bedingten Zugriff erstellen, die zugelassene Clientanwendungen erforderlich macht. 

> [!TIP]  
> Der bedingte Zugriff ist eine Technologie von Azure Active Directory (Azure AD). Bei dem Knoten für bedingten Zugriff, auf den aus *Intune* zugegriffen wird, handelt es sich um denselben Knoten, auf den aus *Azure AD* zugegriffen wird.  

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Bedingter Zugriff** > **Neue Richtlinie** aus.
3. Fügen Sie den **Namen** für die Richtlinie hinzu. 
4. Klicken Sie im Abschnitt **Zuweisungen** auf **Bedingungen** > **Client-Apps**. Der Bereich **Client-Apps** wird angezeigt.
5. Klicken Sie unter **Konfigurieren** auf **Ja**, um die Richtlinie auf bestimmte Client-Apps anzuwenden.
6. Überprüfen Sie, ob der **Browser** als Client-App ausgewählt ist.

    ![Azure AD: Managed Browser – Auswählen von Client-Apps](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Wenn Sie festlegen möchten, welche nativen Apps (Apps, die nicht browserbasiert sind) auf die Cloudanwendungen zugreifen können, können Sie auch **Mobile apps and desktop clients** (Mobile Apps und Desktop-Clients) auswählen.

7. Klicken Sie auf **Fertig** > **Fertig**.
8. Wählen Sie im Bereich **Zuweisungen** die Option **Benutzer und Gruppen** und dann die Benutzer und Gruppen aus, die Sie dieser Richtlinie zuweisen möchten. Klicken Sie auf **Fertig**, um den Bereich zu schließen.
9. Wählen Sie im Abschnitt **Zuweisungen** mithilfe der Option **Cloud-Apps oder -aktionen** aus, welche Apps mit dieser Richtlinie geschützt werden sollen. Klicken Sie auf **Fertig**, um den Bereich zu schließen.
10. Wählen Sie im Abschnitt **Zugriffssteuerungen** des Bereichs auf **Gewähren**. 
11. Klicken Sie auf **Zugriff gewähren** und dann auf **Genehmigte Client-App erforderlich**. 
12. Klicken Sie im Bereich **Gewähren** auf **Auswählen**. Diese Richtlinie muss den Cloud-Apps zugewiesen sein, auf die nur über die Intune Managed Browser-App zugegriffen werden soll.

    ![Azure AD: Managed Browser-Richtlinie für bedingten Zugriff](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)



Sobald diese Richtlinie konfiguriert wurde, müssen Benutzer Intune Managed Browser verwenden, um auf die mit Azure AD verbundenen Web-Apps zuzugreifen, die Sie mit dieser Richtlinie geschützt haben. Wenn Benutzer versuchen, dafür einen nicht verwalteten Browser zu verwenden, erhalten sie die Meldung, dass Intune Managed Browser verwendet werden muss.

Managed Browser unterstützt nicht die klassischen Richtlinien für den bedingten Zugriff. Weitere Informationen finden Sie unter [Migrieren klassischer Richtlinien in das Azure-Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Einmaliges Anmelden bei mit Azure AD verbundenen Web-Apps in richtliniengeschützten Browsern

Microsoft Edge und Intune Managed Browser unter iOS und Android können für alle Web-Apps (SaaS und lokal), die mit Azure AD verbunden sind, die Möglichkeit des einmaligen Anmeldens (Single Sign-on, SSO) nutzen. Wenn die Microsoft Authenticator-App unter iOS bzw. die Intune-Unternehmensportal-App unter Android vorhanden sind, können Benutzer eines mit Richtlinien geschützten Browser auf mit Azure AD verbundene Web-Apps zugreifen und müssen dafür nicht erneut ihre Anmeldeinformationen eingeben.

Für SSO muss Ihr Gerät unter iOS durch Microsoft Authenticator und unter Android durch das Intune-Unternehmensportal registriert sein. Benutzer, die die Authenticator-App oder das Intune-Unternehmensportal verwenden, werden dazu aufgefordert, ihre Geräte zu registrieren, wenn sie zu einer mit Azure AD verbundenen Web-App im richtliniengeschützten Browser navigieren, es sei denn, ihr Gerät wurde bereits von einer anderen Anwendung registriert. Nachdem das Gerät mit dem von Intune verwalteten Konto registriert wurde, ist für dieses Konto für mit Azure AD verbundene Web-Apps SSO aktiviert. 

> [!NOTE]
> Bei der Geräteregistrierung handelt es sich um einen einfachen Check-In beim Azure AD-Dienst. In diesem Zusammenhang wird keine vollständige Geräteregistrierung verwendet, und die IT-Abteilung erhält keine zusätzlichen Berechtigungen auf das Gerät.

## <a name="create-a-protected-browser-app-configuration"></a>Erstellen einer geschützten Browser-App-Konfiguration

>[!IMPORTANT]
>Damit die App-Konfigurationen angewendet werden können, muss der geschützte Browser des Benutzers oder eine andere App auf dem Gerät bereits mit der [Intune-App-Schutzrichtlinie]( ../app-protection-policy.md) verwaltet werden.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen** > **Verwaltete Apps** aus.
3. Geben Sie auf der Seite **Grundeinstellungen** des Bereichs **App-Konfigurationsrichtlinie erstellen** einen **Namen** und optional eine **Beschreibung** für die App-Konfigurationseinstellungen ein.
4. Wählen Sie **Öffentliche App auswählen** und dann **Managed Browser** und/oder **Microsoft Edge** für iOS, für Android oder für beides aus.
5. Klicken Sie auf **Auswählen**, um zum Bereich **App-Konfigurationsrichtlinie erstellen** zurückzukehren.
6. Klicken Sie auf **Weiter**, um die Seite **Einstellungen** anzuzeigen.
7. Definieren Sie auf der Seite **Einstellungen** Schlüssel-Wert-Paare, um Konfigurationen für die App bereitzustellen. In den folgenden Abschnitten erhalten Sie weitere Informationen zu den unterschiedlichen Schlüssel-Wert-Paaren, die Sie definieren können.
8. Klicken Sie auf **Weiter**, um die Seite **Zuweisung** anzuzeigen, und klicken Sie dann auf **Einzuschließende Gruppen auswählen** und/oder **Auszuschließende Gruppen auszuwählen**.
9. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen.
10. Nachdem Sie die App-Konfigurationsrichtlinie überprüft haben, klicken Sie auf **Erstellen**.

Die neue Konfiguration wird erstellt und auf im Bereich **App-Konfigurationsrichtlinien** angezeigt.


## <a name="assign-the-configuration-settings-you-created"></a>Zuweisen der erstellten Konfigurationseinstellungen

Sie weisen die Einstellungen Azure AD-Gruppen von Benutzern zu. Haben diese Benutzer die geschützte Browser-Ziel-App installiert, wird die App durch die angegebenen Einstellungen verwaltet.

1. Wählen Sie im Bereich **Apps** im Intune-Dashboard für die Verwaltung von mobilen Anwendungen die Option **App-Konfigurationsrichtlinien** aus.
2. Wählen Sie aus der Liste der App-Konfigurationen diejenige aus, die Sie zuweisen möchten.
3. Wählen Sie im nächsten Bereich **Zuweisungen** aus.
4. Wählen Sie im Bereich **Zuweisungen** die Azure AD-Gruppe, der Sie die App-Konfiguration zuweisen möchten, und dann **OK** aus.

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>Einrichten von Microsoft Edge als geschützten Browser für Ihre Organisation

Mit dieser Einstellung können Sie konfigurieren, ob Ihre Benutzer an Microsoft Edge oder den Intune Managed Browser weitergeleitet werden, vorausgesetzt, dass für beide Browser eine App-Schutzrichtlinie eingerichtet wurde. **Diese Richtlinieneinstellung für die Anwendungskonfiguration sollte auf von Intune verwaltete Apps ausgerichtet werden, aus denen der Weblink geöffnet wird.** 

Wenn diese Einstellung auf „true“ festgelegt ist, gilt Folgendes:

- Ihre Benutzer werden an Microsoft Edge weitergeleitet, wenn sie Links aus von Intune verwalteten Apps öffnen, für die diese Einstellung eingerichtet wurde. 
- Wenn Benutzer noch nicht über diese App verfügen, werden sie aufgefordert, Microsoft Edge aus dem Store herunterzuladen, unabhängig davon, ob der Intune Managed Browser bereits heruntergeladen wurde.

Wenn diese Einstellung auf „false“ festgelegt ist, gilt Folgendes:

- Wenn Ihre Benutzer **sowohl** den Managed Browser **als auch** Microsoft Edge heruntergeladen haben, wird der Managed Browser gestartet. 
- Wenn Ihre Benutzer **entweder** den Managed Browser **oder** Microsoft Edge heruntergeladen haben, wird die entsprechende Browser-App gestartet. 
- Wenn Ihre Benutzer keine der Browser-Apps heruntergeladen haben, werden sie aufgefordert, den Managed Browser herunterzuladen.

Verwenden Sie das oben beschriebene Verfahren, um eine Microsoft Edge-App-Konfiguration zu erstellen. Geben Sie das folgende Schlüssel-Wert-Paar an, wenn Sie die **Konfigurationseinstellungen** im Bereich **Konfiguration** auswählen (Schritt 9):

| Key                              |  Wert   |
|----------------------------------|----------|
| **com.microsoft.intune.useEdge** | **TRUE** |

> [!NOTE]
> Vergewissern Sie sich in der App-Schutzrichtlinie, die Microsoft Edge und die in der App-Konfiguration angegebenen zugehörigen Apps verwaltet, dass die folgenden Einstellungen für die Datenschutzrichtlinie festgelegt sind:
> - Organisationsdaten an andere Apps senden: **Richtlinienverwaltete Apps**
> - Übertragung von Webinhalten mit anderen Apps einschränken: **Mit Richtlinien verwaltete Browser**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Konfigurieren von Anwendungsproxyeinstellungen für geschützte Browser

Microsoft Edge, Intune Managed Browser und der [Azure AD-Anwendungsproxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) können gemeinsam verwendet werden, um die folgenden Szenarien für Benutzer von iOS- und Android-Geräten zu unterstützen:

- Ein Benutzer lädt die Microsoft Outlook-App herunter und meldet sich an. Die Intune-App-Schutzrichtlinien werden automatisch angewendet. Diese verschlüsseln gespeicherte Daten und hindern den Benutzer daran, Unternehmensdateien auf nicht verwaltete Apps oder Speicherorte auf dem Gerät zu übertragen. Klickt der Benutzer dann auf einen Link zu einer Intranetwebsite in Outlook, können Sie angeben, dass der Link in einer geschützten Browser-Anwendung anstatt in einem anderen Browser geöffnet wird. Der geschützte Browser erkennt, dass diese Intranetwebsite dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Der Benutzer wird automatisch über den Anwendungsproxy weitergeleitet, um sich mit einer anwendbaren Option für die mehrstufige Authentifizierung und den bedingten Zugriff zu authentifizieren, bevor er zur Intranetsite gelangt. Auf diese Website, die im Remotezugriff zuvor noch nicht gefunden werden konnte, kann nun zugegriffen werden, und der Link funktioniert in Outlook erwartungsgemäß.
- Ein Remotebenutzer öffnet die geschützte Browser-Anwendung und navigiert mit der internen URL zu einer Intranetwebsite. Der geschützte Browser erkennt, dass diese Intranetwebsite dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Der Benutzer wird automatisch über den Anwendungsproxy weitergeleitet, um sich mit einer anwendbaren Option für die mehrstufige Authentifizierung und den bedingten Zugriff zu authentifizieren, bevor er zur Intranetsite gelangt. Auf diese Website, die im Remotezugriff zuvor noch nicht gefunden werden konnte, kann nun zugegriffen werden.

### <a name="before-you-start"></a>Vorbereitung

- Richten Sie Ihre internen Anwendungen über den Azure AD-Anwendungsproxy ein.
  - Informationen zum Konfigurieren des Anwendungsproxys und zum Veröffentlichen von Anwendungen finden Sie in der [Setup-Dokumentation](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). 
  - [Benutzer müssen der Unternehmensanwendung zugewiesen sein](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing), für die die Umleitung erfolgen soll. Dies muss auch dann eingerichtet werden, wenn die Anwendung zur Vorauthentifizierung auf den Passthroughmodus festgelegt ist und die Anforderung zur Benutzerzuweisung in den Einstellungen des Anwendungsproxys deaktiviert wurde.
- Die Managed Browser-App muss in der Version 1.2.0 oder höher ausgeführt werden.
- Benutzer der Managed Browser- oder Microsoft Edge-App verfügen über eine der App zugewiesenen [Intune-App-Schutzrichtlinie](app-protection-policy.md).

    > [!NOTE]
    > Es kann bis zu 24 Stunden dauern, bis aktualisierte Umleitungsdaten des Anwendungsproxys in Managed Browser und Microsoft Edge in Kraft treten.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Schritt 1: Aktivieren der automatischen Umleitung von Outlook zu einem geschützten Browser
Outlook muss mit einer App-Schutzrichtlinie konfiguriert werden, mit der Einstellung **Anzeige von Webinhalten auf den Managed Browser beschränken** möglich ist.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>Schritt 2: Zuweisen einer App-Konfigurationsrichtlinie für den geschützten Browser
Dieses Verfahren konfiguriert die Managed Browser- oder Microsoft Edge-App, damit die App-Proxyumleitung verwendet wird. 

Öffnen Sie in den Konfigurationseinstellungen für die Richtlinie die Registerkarte **Edge**, und wählen Sie **Aktivieren** als Wert für die Umleitung des Anwendungsproxys aus. Durch Aktivieren dieser Einstellung erhalten Benutzer Zugriff auf Unternehmenslinks und lokale Web-Apps, die über den Azure-Anwendungsproxy veröffentlicht wurden.

Weitere Informationen zur möglichen gemeinsamen Verwendung von Managed Browser, Microsoft Edge und dem Azure AD-Anwendungsproxy für nahtlosen (und geschützten) Zugriff auf lokale Web-Apps finden Sie in dem Blogbeitrag zu Enterprise Mobility + Security mit dem Titel [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Intune und Azure Active Directory gemeinsam verwenden, um den Benutzerzugriff zu verbessern).

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>Konfigurieren der Startseite für einen geschützten Browser

Mit dieser Einstellung können Sie die Startseite konfigurieren, die Benutzern beim Starten eines geschützten Browsers oder beim Erstellen einer neuen Registerkarte angezeigt wird. 
- Diese Einstellung zeigt die Webseite des Managed Browser an.  Microsoft Edge zeigt stattdessen eine Verknüpfung zur Startseite an.
- Das Symbol der Verknüpfung zur Startseite wird als Symbol unterhalb des Suchsteuerelements angezeigt.  Es kann weder bearbeitet noch gelöscht werden.
- Die Verknüpfung für die Startseite zeigt den Namen Ihrer Organisation zur Unterscheidung an.  Er wird immer als das erste Symbol angezeigt.

Geben Sie über die Prozedur zum Erstellen einer Microsoft Edge- oder Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

|                                Key                                |                                                           Wert                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Geben Sie eine gültige URL ein. Ungültige URLs werden zur Sicherheit gesperrt.<br>Beispiel: `https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>Konfigurieren von Lesezeichen für einen geschützten Browser

Mit dieser Einstellung können Sie mehrere Lesezeichen konfigurieren, die den Benutzern von Microsoft Edge oder Managed Browser zur Verfügung stehen.

- Diese Lesezeichen können von den Benutzern nicht gelöscht oder bearbeitet werden.
- Diese Lesezeichen werden oben in der Liste angezeigt. Alle von den Benutzern erstellten Lesezeichen werden unterhalb dieser Lesezeichen angezeigt.
- Wenn Sie die App-Proxyumleitung aktiviert haben, können Sie App-Proxy-Web-Apps mit deren interner oder externer URL hinzufügen.

Geben Sie über die Prozedur zum Erstellen einer Microsoft Edge- oder Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

|                                Key                                 |                                                                                                                                                                                                                                                         Wert                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | Der Wert für diese Konfiguration ist eine Liste von Lesezeichen. Jedes Lesezeichen besteht aus dem Lesezeichentitel und der Lesezeichen-URL. Trennen Sie Titel und URL mit dem <strong>&#124;</strong>-Zeichen.<br><br>Beispiel:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>Zum Konfigurieren von mehreren Lesezeichen trennen Sie jedes Paar mit einem doppelten <strong>&#124;&#124;</strong>-Zeichen.<br><br>Beispiel:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>Angeben von zugelassenen und blockierten URLs für einen geschützten Browser

Geben Sie über die Prozedur zum Erstellen einer Microsoft Edge- oder Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

|Key|Wert|
|-|-|
|Es stehen die folgenden Optionen zur Auswahl:<br><ul><li>Geben Sie zulässige URLs an (nur diese URLs sind zulässig. Es kann nicht auf andere Websites zugegriffen werden):<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Angeben von blockierten URLs (auf alle anderen Websites kann zugegriffen werden):<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|Der entsprechende Wert für den Schlüssel ist eine Liste mit URLs. Geben Sie alle URLs, die Sie zulassen oder blockieren möchten, als einen einzelnen Wert ein, der durch einen senkrechten Strich **&#124;** getrennt ist.<br><br>Beispiele:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>Geben Sie nicht beide Schlüssel an. Wenn beide Schlüssel für einen Benutzer eingerichtet sind, wird der Schlüssel für zugelassene URLs verwendet, da dies die restriktivste Option ist.
>Stellen Sie außerdem sicher, dass Sie keine wichtigen Seiten wie Ihre Unternehmenswebsites blockieren.

### <a name="url-format-for-allowed-and-blocked-urls"></a>URL-Format für zulässige und blockierte URLs
Nachfolgend wird erläutert, welche Formate und Platzhalter Sie zum Festlegen von URLs in den Zulassungs- und Blockierungslisten verwenden können:

- Sie können das Platzhaltersymbol ( **&#42;** ) gemäß den Regeln in der folgenden Liste mit zulässigen Mustern verwenden:

- Stellen Sie sicher, dass Sie bei der Eingabe in die Liste allen URLs **http** oder **https** voranstellen.

- Sie können Portnummern in der Adresse angeben. Wenn Sie keine Portnummer angeben, werden folgende Werte verwendet:

  - Port 80 für http

  - Port 443 für https

  Die Verwendung von Platzhaltern für die Portnummer wird nicht unterstützt. Beispielsweise werden `http://www.contoso.com:;` und `http://www.contoso.com: /;` nicht unterstützt.

- In der folgenden Tabelle sind die zulässigen Muster aufgeführt, die Sie zum Festlegen von URLs verwenden können:

|                  URL                  |                     Details                      |                                                Treffer                                                |                                Stimmt nicht überein mit                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              Entspricht einer einzelnen Seite               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              Entspricht einer einzelnen Seite               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | Entspricht allen URLs, die mit `www.contoso.com` beginnen |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     Entspricht allen Unterdomänen unter „contoso.com“     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             Entspricht einem einzelnen Ordner              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  Entspricht einer einzelnen Seite mit einer Portnummer   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          Entspricht einer einzelnen, sicheren Seite           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    Entspricht einem einzelnen Ordner und allen Unterordnern    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- Im Folgenden Beispiele für Eingaben, die nicht unterstützt werden:

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - IP-Adressen

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>Weiche Übergänge von Arbeitskonten zu persönlichen Konten

Der Eckpfeiler des mobilen Benutzererlebnisses des Microsoft Edge-Unternehmensbrowsers ist das Modell mit zwei Identitäten. Dies bedeutet, dass Microsoft Edge sowohl Arbeits- als auch persönliche Identitäten unterstützt. Wie bei den Office 365- und Outlook-Apps ermöglicht dieses Modell es Endbenutzern, Microsoft Edge für alle Browseranforderungen zu verwenden und dabei ganz einfach zwischen beiden Identitäten zu wechseln – basierend auf den vom Administrator definierten Inhaltsrichtlinien. Das Browsen im persönlichen Kontext wird dabei nicht beeinträchtigt, und Unternehmensinformationen verbleiben vollständig im Arbeitskontext innerhalb von Microsoft Edge. 

Einer der Vorteile dieses Modells ist, dass Benutzer einen Link (z. B. einen Zeitungsartikel) zu einer Website, die von Ihrer Organisation nicht zugelassen ist, in ihrem persönlichen Kontext öffnen können. Dieser ist vollständig vom Arbeitskontext getrennt. Diese weichen Übergänge sind standardmäßig aktiviert. 

Geben Sie über die Prozedur zum Erstellen einer Microsoft Edge- oder Managed Browser-App-Konfiguration das folgende Schlüssel-Wert-Paar an:

| Key                                                                | Wert                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock** | **False** blockiert diese weichen Übergänge. |

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

- Einstellungen, die Benutzer für den integrierten Browser auf ihren Geräten vornehmen, werden von Managed Browser nicht verwendet. Managed Browser kann auf diese Einstellungen nicht zugreifen.

- Wenn Sie die Option **Einfache PIN für den Zugriff erforderlich** oder **Unternehmensanmeldeinformationen für den Zugriff erforderlich** in einer App-Schutzrichtlinie konfigurieren, die Managed Browser zugeordnet ist, und ein Benutzer auf der Authentifizierungsseite den Hilfelink auswählt, kann er beliebige Websites besuchen. Dies gilt unabhängig davon, ob sie in der Richtlinie einer Blockierungsliste hinzugefügt wurden.

- Managed Browser kann den Zugriff auf Websites nur blockieren, wenn direkt darauf zugegriffen wird. Der Zugriff auf die Website wird nicht blockiert, wenn dafür Zwischendienste (z.B. ein Übersetzungsdienst) verwendet werden.

- Um die Authentifizierung und den Zugriff auf die Intune-Dokumentation zuzulassen, ist **&#42;.microsoft.com** von den Zulassungs- oder Blockierungslisten ausgenommen. und immer zulässig.

### <a name="turn-off-usage-data"></a>Deaktivieren von Nutzungsdaten
Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung von Managed Browser, um Microsoft-Produkte und -Dienste zu verbessern. Benutzer können die Erfassung von Daten mithilfe der Einstellung für **Nutzungsdaten** auf ihren Geräten deaktivieren. Sie haben keine Kontrolle über die Erfassung dieser Daten.

- Auf iOS-Geräten können von Benutzern besuchte Websites, deren Zertifikat abgelaufen oder nicht vertrauenswürdig ist, nicht geöffnet werden.

## <a name="next-steps"></a>Nächste Schritte

- [Was sind App-Schutzrichtlinien?](app-protection-policy.md) 
