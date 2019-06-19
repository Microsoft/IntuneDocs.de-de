---
title: Verwalten des Webzugriffs mithilfe von Microsoft Edge mit Microsoft Intune
titleSuffix: ''
description: Verwenden Sie Intune-App-Schutzrichtlinien mit Microsoft Edge, um sicherzustellen, dass auf Unternehmenswebsites immer mit eingerichteten Sicherheitsmaßnahmen zugegriffen wird.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1a255391a2cf27a764da6122031fd0c9cbb64cf
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751358"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>Verwalten des Webzugriffs mithilfe von Microsoft Edge mit Microsoft Intune

Die Verwendung von Intune-App-Schutzrichtlinien mit Microsoft Edge kann sicherstellen, dass auf Unternehmenswebsites immer mit eingerichteten Sicherheitsmaßnahmen zugegriffen wird. Die folgenden durch Intune-Richtlinien ermöglichten Microsoft Edge-Unternehmensfunktionen sind verfügbar. Zu diesen Unternehmensfunktionen zählen die folgenden:

1.  **Doppelte Identitäten:** Benutzer können sowohl Geschäftskonten als auch persönliche Konten zum Browsen hinzufügen. Die beiden Identitäten sind vollständig voneinander getrennt, ähnlich wie bei Office 365 und Outlook. Intune-Administratoren können die gewünschten Richtlinien für geschütztes Browsen im Geschäftskonto festlegen.
2.  **Integration von Intune-App-Schutzrichtlinien** – Da Microsoft Edge in das Intune SDK integriert ist, können Sie App-Schutzrichtlinien als Schutz vor einem Datenverlust festlegen. Diese Funktionen umfassen: Kontrolle von Ausschneiden, Kopieren und Einfügen, Verhindern von Bildschirmaufnahmen und Sicherstellen, dass vom Benutzer ausgewählte Links nur in anderen verwalteten Apps geöffnet werden.
3.  **Integration des Azure-Anwendungsproxys** – Sie können den Zugriff auf SaaS-Apps und Web-Apps festlegen, um sicherzustellen, dass browserbasierte Apps nur im sicheren Microsoft Edge-Browser ausgeführt werden –unabhängig davon, ob Endbenutzer eine Verbindung über das Unternehmensnetzwerk oder das Internet herstellen.
4.  **Anwendungskonfiguration** – Sie können die Einstellungen der Anwendungskonfiguration nutzen, um den Sicherheitsstatus Ihrer Organisation zu verbessern und benutzerfreundliche Features für Ihre Endbenutzer zu konfigurieren. So können Sie beispielsweise Lesezeichen, eine Verknüpfung zur Startseite, zulässige/blockierte Websites, Azure-Anwendungsproxy und vieles mehr definieren.
Microsoft Intune-Schutzrichtlinien für Microsoft Edge tragen dazu bei, die Daten und Ressourcen Ihres Unternehmens zu schützen. Durch die Verwendung dieser Richtlinien mit Microsoft Edge wird sichergestellt, dass die Ressourcen Ihres Unternehmens nicht nur in systemintern installierten Apps geschützt sind, sondern auch, wenn darauf über den Webbrowser zugegriffen wird.

## <a name="getting-started"></a>Erste Schritte

Sie und Ihre Endbenutzer können Microsoft Edge aus öffentlichen App-Stores für die Verwendung in Ihrer Organisation herunterladen. Betriebssystemanforderungen für Browserrichtlinien:
- Android 4 und höher oder
- iOS 8.0 und höher

## <a name="application-protection-policies-for-microsoft-edge"></a>Anwendungsschutzrichtlinien für Microsoft Edge

Weil Microsoft Edge in das Intune SDK integriert ist, können Sie darauf Anwendungsschutzrichtlinien anwenden, darunter:
- Steuern der Verwendung von Ausschneiden, Kopieren und Einfügen
- Verhindern von Bildschirmaufnahmen
- Sicherstellen, dass Unternehmenslinks nur in verwalteten Apps und Browsern geöffnet werden

Weitere Informationen finden Sie unter „Was sind App-Schutzrichtlinien?“.
Sie können diese Einstellungen auf Folgendes anwenden:
- Geräte, die bei Intune registriert sind
- Geräte, die bei einem anderen MDM-Produkt registriert sind
- Nicht verwaltete Geräte

Wenn Microsoft Edge keine Intune-Richtlinie zugeordnet wird, können es Benutzer nicht verwenden, um auf Daten aus anderen von Intune verwalteten Anwendungen wie Office-Apps zuzugreifen. 

## <a name="conditional-access-for-microsoft-edge"></a>Bedingter Zugriff für Microsoft Edge

Sie können den bedingten Azure AD-Zugriff nutzen, um Ihre Benutzer weiterzuleiten, damit sie nur über Microsoft Edge auf Unternehmensdaten zugreifen können. Dadurch würde der mobile Browserzugriff auf mit Azure AD-verbundene Web-Apps über durch Richtlinien geschütztes Microsoft Edge eingeschränkt und folglich der Zugriff aus anderen nicht geschützten Browsern wie Safari oder Chrome blockiert. Bedingter Zugriff kann auf Azure-Ressourcen wie Exchange Online, SharePoint Online, das Microsoft 365 Admin Center und sogar auf lokale Websites angewendet werden, die Sie für externe Benutzer über den [Azure AD-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) freigegeben haben.

Um bei mit Azure AD verbundenen Web-Apps die Verwendung von Microsoft Edge unter iOS und Android einzuschränken, führen Sie die folgenden Schritte aus:
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie unter dem Intune-Knoten **Conditional access** > **New policy** (Bedingter Zugriff > Neue Richtlinie) aus.
3. Klicken Sie im Abschnitt **Zugriffssteuerungen** des Blatts auf die Option **Erteilen**.
4. Klicken Sie auf **Genehmigte Client-App erforderlich**.
5. Klicken Sie auf dem Blatt **Erteilen** auf **Auswählen**. Diese Richtlinie muss den Cloud-Apps zugewiesen sein, auf die nur über die Intune Managed Browser-App zugegriffen werden soll.

    ![Richtlinie für bedingten Zugriff – Gewähren](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Wählen Sie im Abschnitt „Zuweisungen“ nacheinander „Bedingungen“ > „Client-Apps“ aus. Das Blatt „Client-Apps“ wird angezeigt.
7. Klicken Sie unter „Konfigurieren“ auf „Ja“, um die Richtlinie auf bestimmte Client-Apps anzuwenden.
8. Überprüfen Sie, ob „Browser“ als Client-App ausgewählt ist.

    ![Richtlinie für bedingten Zugriff – Auswählen von Client-Apps](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Wenn Sie festlegen möchten, welche nativen Apps (Apps, die nicht browserbasiert sind) auf die Cloudanwendungen zugreifen können, können Sie auch **Mobile apps and desktop clients** (Mobile Apps und Desktop-Clients) auswählen.

9. Klicken Sie im Bereich **Zuweisungen** auf **Benutzer und Gruppen**, und wählen Sie dann die Benutzer und Gruppen aus, die Sie dieser Richtlinie zuweisen möchten.

    > [!NOTE]
    > Benutzer müssen ebenfalls durch die Intune-App-Schutzrichtlinie involviert werden, sodass App-Konfigurationsrichtlinien für sie gelten. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

10. Klicken Sie im Abschnitt **Zuweisungen** auf **Cloud-Apps**, um auszuwählen, welche Apps mit dieser Richtlinie geschützt werden sollen.

Sobald diese Richtlinie konfiguriert wurde, müssen Benutzer Microsoft Edge verwenden, um auf die mit Azure AD verbundenen Web-Apps zuzugreifen, die Sie mit der Richtlinie geschützt haben. Wenn Benutzer versuchen, in diesem Szenario einen nicht verwalteten Browser zu verwenden, werden sie mit einer Meldung informiert, dass sie Microsoft Edge verwenden müssen.

> [!TIP]
> Der bedingte Zugriff ist eine Technologie von Azure Active Directory (Azure AD). Bei dem Knoten für bedingten Zugriff, auf den aus Intune zugegriffen wird, handelt es sich um denselben Knoten, auf den aus Azure AD zugegriffen wird.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Einmaliges Anmelden bei mit Azure AD verbundenen Web-Apps in richtliniengeschützten Browsern

Microsoft Edge unter iOS und Android kann für alle Web-Apps (SaaS und lokal), die mit Azure AD verbunden sind, die Möglichkeit des einmaligen Anmeldens (Single Sign-on, SSO) nutzen. SSO ermöglicht Benutzern, auf mit Azure AD verbundene Web-Apps über Microsoft Edge zuzugreifen, ohne ihre Anmeldeinformationen erneut eingeben zu müssen.

Für SSO muss Ihr Gerät entweder durch die Microsoft Authenticator-App für iOS-Geräte oder durch das Intune-Unternehmensportal unter Android registriert werden. Wenn Benutzer die Authenticator-App oder das Intune-Unternehmensportal haben, werden sie zur Registrierung ihres Geräts aufgefordert, wenn sie zu einer mit Azure AD verbundenen Web-App in einem durch Richtlinien geschützten Browser navigieren – sofern ihr Gerät noch nicht registriert wurde. Nachdem das Gerät mit dem von Intune verwalteten Benutzerkonto registriert wurde, wird bei diesem Konto für mit Azure AD verbundene Web-Apps SSO aktiviert.

> [!NOTE]
> Bei der Geräteregistrierung handelt es sich um einen einfachen Check-In beim Azure AD-Dienst. In diesem Zusammenhang wird keine vollständige Geräteregistrierung verwendet, und die IT-Abteilung erhält keine zusätzlichen Berechtigungen auf das Gerät.

## <a name="create-a-protected-browser-app-configuration"></a>Erstellen einer geschützten Browser-App-Konfiguration

Damit App-Konfigurationen angewendet werden können, muss der geschützte Browser des Benutzers oder eine andere App auf dem Gerät bereits mit der [Intune-App-Schutzrichtlinie](app-protection-policy.md) verwaltet werden.

Die folgenden Schritte dienen zum Erstellen einer geschützten Browser-App-Konfiguration:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Client-Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen** aus.
3. Geben Sie auf dem Blatt **Konfigurationsrichtlinie hinzufügen** einen **Namen** und optional eine **Beschreibung** für die App-Konfigurationseinstellungen ein.
4. Wählen Sie als Typ der **Geräteregistrierung** die Option **Verwaltete Apps** aus.
5. Wählen Sie **Erforderliche App auswählen** und dann auf dem Blatt **Ziel-Apps** die Option **Managed Browser** und/oder **Microsoft Edge** für iOS, für Android oder für beides aus.
6. Wählen Sie **OK** aus, um zum Blatt **Konfigurationsrichtlinie hinzufügen** zurückzukehren.
7. Wählen Sie **Konfigurationseinstellungen** aus. Auf dem Blatt **Konfiguration** definieren Sie Schlüssel-Wert-Paare, um Konfigurationen für Microsoft Edge bereitzustellen. In den folgenden Abschnitten erhalten Sie weitere Informationen zu den unterschiedlichen Schlüssel-Wert-Paaren, die Sie definieren können.

    > [!NOTE]
    > Microsoft Edge verwendet die gleichen Schlüssel-Wert-Paare wie Managed Browser. 

8.  Klicken Sie abschließend auf **OK**.
9.  Wählen Sie auf dem Blatt **Konfigurationsrichtlinie hinzufügen** die Option **Hinzufügen** aus.<br>
    Die neue Konfiguration wird erstellt und auf dem Blatt **App-Konfiguration** angezeigt.

## <a name="assign-the-configuration-settings-you-created"></a>Zuweisen der erstellten Konfigurationseinstellungen 

Sie weisen die Einstellungen Azure AD-Gruppen von Benutzern zu. Haben diese Benutzer die geschützte Browser-Ziel-App installiert, wird die App durch die angegebenen Einstellungen verwaltet.

1. Wählen Sie auf dem Blatt **Client-Apps** im Intune-Dashboard für die Verwaltung von mobilen Anwendungen **App-Konfigurationsrichtlinie** aus.
2. Wählen Sie aus der Liste der App-Konfigurationen diejenige aus, die Sie zuweisen möchten.
3. Wählen Sie auf dem nächsten Blatt **Zuweisungen** aus.
4. Wählen Sie auf dem Blatt **Zuweisungen** die Azure AD-Gruppe aus, der Sie die App-Konfiguration zuweisen möchten, und wählen Sie dann **OK** aus.

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Konfigurieren von Anwendungsproxyeinstellungen für geschützte Browser

Microsoft Edge und [Azure AD-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) können zusammen verwendet werden, um Benutzern Zugriff auf Intranetsites auf ihren mobilen Geräten zu ermöglichen. 

Dies sind einige Beispiele für Szenarien mit aktiviertem AD-Anwendungsproxy: 

- Ein Benutzer verwendet die mobile Outlook-App, die durch Intune geschützt ist. Dann klickt er in einer E-Mail auf einen Link zu einer Intranetsite, und Microsoft Edge erkennt, dass diese Site dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Der Benutzer wird über den Anwendungsproxy automatisch weitergeleitet, um sich mit einer anwendbaren mehrstufigen Authentifizierung und bedingtem Zugriff zu authentifizieren, bevor er die Intranetsite erreicht. Benutzer können jetzt sogar auf ihren mobilen Geräten auf interne Websites zugreifen, und der Link in Outlook funktioniert wie erwartet.
- Ein Benutzer öffnet Microsoft Edge auf seinem iOS- oder Android-Gerät. Wenn Microsoft Edge mit Intune geschützt ist und der Anwendungsproxy aktiviert wurde, kann der Benutzer über die gewohnte interne URL zu einer Intranetsite navigieren. Microsoft Edge erkennt, dass diese Intranetsite dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Der Benutzer wird über den Proxy automatisch weitergeleitet, damit er sich authentifiziert, bevor er die Site erreicht. 

### <a name="before-you-start"></a>Vorbereitung

- Richten Sie Ihre internen Anwendungen über den Azure AD-Anwendungsproxy ein.
    - Informationen zum Konfigurieren des Anwendungsproxys und zum Veröffentlichen von Anwendungen finden Sie in der [Setup-Dokumentation](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- Der Microsoft Edge-App muss die [Intune-App-Schutzrichtlinie](app-protection-policy.md) zugewiesen werden.

> [!NOTE]
> Es kann bis zu 24 Stunden dauern, bis aktualisierte Umleitungsdaten des Anwendungsproxys in Managed Browser und Microsoft Edge in Kraft treten.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Schritt 1: Aktivieren der automatischen Umleitung von Outlook zu einem geschützten Browser
Outlook muss mit einer App-Schutzrichtlinie konfiguriert werden, mit der die Einstellung **Webinhalt für per Richtlinie verwaltete Browser freigeben** aktiviert wird.

![App-Schutzrichtlinie – Webinhalt für per Richtlinie verwaltete Browser freigeben](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Schritt 2: Festlegen der App-Konfigurationseinstellung zum Aktivieren des Anwendungsproxys
Ordnen Sie Microsoft Edge das folgende Schlüssel-Wert-Paar zu, um den Anwendungsproxy für Microsoft Edge zu aktivieren:

|    Key    |    Wert    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Weitere Informationen zur möglichen gemeinsamen Verwendung von Microsoft Edge und dem Azure AD-Anwendungsproxy für nahtlosen (und geschützten) Zugriff auf lokale Web-Apps finden Sie im Blogbeitrag zu Enterprise Mobility + Security mit dem Titel [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Intune und Azure Active Directory gemeinsam verwenden, um den Benutzerzugriff zu verbessern). Dieser Blogbeitrag verweist auf den Intune Managed Browser; der Inhalt gilt aber auch für Microsoft Edge.

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>Konfigurieren einer Verknüpfung zur Startseite für Microsoft Edge

Diese Einstellung ermöglicht Ihnen das Konfigurieren einer Verknüpfung zur Startseite für Microsoft Edge.  Die von Ihnen konfigurierte Verknüpfung zur Startseite wird als erstes Symbol unter der Suchleiste angezeigt, wenn ein Benutzer eine neue Registerkarte in Microsoft Edge öffnet. Der Benutzer kann diese Verknüpfung in seinem verwalteten Kontext nicht bearbeiten oder löschen. Die Verknüpfung für die Startseite zeigt den Namen Ihrer Organisation zur Unterscheidung an. 

Verwenden Sie das folgende Schlüssel-Wert-Paar zum Konfigurieren einer Verknüpfung zur Startseite:

|    Key    |    Wert    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Geben Sie eine gültige URL ein. Ungültige URLs werden zur Sicherheit gesperrt.<br>**Beispiel:** `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>Konfigurieren von verwalteten Lesezeichen für Microsoft Edge

Für erleichterte Bedienung können Sie Lesezeichen konfigurieren, die Ihren Benutzern bei der Verwendung von Microsoft Edge zur Verfügung stehen sollen. Hier sind einige Details:

- Diese Lesezeichen werden für die Benutzer nur angezeigt, wenn sie den Unternehmensmodus von Microsoft Edge verwenden. 
- Diese Lesezeichen können von den Benutzern nicht gelöscht oder geändert werden.
- Diese Lesezeichen werden oben in der Liste angezeigt. Alle von den Benutzern erstellten Lesezeichen werden unterhalb dieser Lesezeichen angezeigt.
- Wenn Sie die App-Proxyumleitung aktiviert haben, können Sie App-Proxy-Web-Apps mit deren interner oder externer URL hinzufügen.

Verwenden Sie das folgende Schlüssel-Wert-Paar zum Konfigurieren von verwalteten Lesezeichen:

|    Key    |    Wert    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    Der Wert für diese Konfiguration ist eine Liste von Lesezeichen. Jedes Lesezeichen besteht aus dem Lesezeichentitel und der Lesezeichen-URL. Trennen Sie Titel und URL durch das `|`-Zeichen.      **Beispiel:**<br>`Microsoft Bing|https://www.bing.com`<p>Zum Konfigurieren von mehreren Lesezeichen trennen Sie jedes Paar durch ein doppeltes `||`-Zeichen.<p>**Beispiel:**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>Anzeigen von „MyApps“ in Microsoft Edge-Lesezeichen

Ihren Benutzern werden standardmäßig die „MyApps“-Websites angezeigt, die für sie in einem Ordner innerhalb der Microsoft Edge-Lesezeichen konfiguriert wurden. Der Ordner wird mit dem Namen Ihrer Organisation bezeichnet.

|    Key    |    Wert    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** zeigt „MyApps“ in den Microsoft Edge-Lesezeichen.<p>**False** blendet „MyApps“ in den Microsoft Edge-Lesezeichen aus.    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Angeben der Liste zulässiger oder blockierter Websites für Microsoft Edge
Sie können mit der App-Konfiguration definieren, auf welche Websites Ihre Benutzer unter Verwendung ihres Arbeitsprofils zugreifen können. Wenn Sie eine Zulassungsliste verwenden, können Ihre Benutzer nur auf die Websites zugreifen, die Sie explizit aufgelistet haben. Wenn Sie eine Sperrliste verwenden, können Ihre Benutzer auf alle Websites zugreifen – mit Ausnahme der Websites, die Sie explizit blockiert haben. Sie sollten entweder nur eine Zulassungsliste oder nur eine Blockierungsliste vorgeben, nicht beide Listen. Wenn beide dem Gerät zugeordnet werden, wird die Zulassungsliste berücksichtigt.  

Sie können die folgenden Schlüssel-Wert-Paare verwenden, um eine Liste zulässiger oder blockierter Websites für Microsoft Edge zu konfigurieren. Lesen Sie weiter, um mehr zu gültigen URL-Formaten zu erfahren. 

|    Key    |    Wert    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Es stehen die folgenden Optionen zur Auswahl:<p>1. Geben Sie zulässige URLs an (nur diese URLs sind zulässig. Es kann nicht auf andere Websites zugegriffen werden):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Angeben von blockierten URLs (auf alle anderen Websites kann zugegriffen werden):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    Der entsprechende Wert für den Schlüssel ist eine Liste mit URLs. Sie geben alle URLs, die Sie zulassen oder blockieren möchten, als einen einzelnen Wert ein, der durch einen senkrechten Strich (`|`) getrennt ist.<p>**Beispiele:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>URL-Formate für die Liste zulässiger und blockierter Websites 
Sie können verschiedene URL-Formate verwenden, um Ihre Listen für zulässige/blockierte Websites zu erstellen. Diese zulässigen Muster werden in der folgenden Tabelle beschrieben. Einige Hinweise, bevor Sie beginnen: 
- Stellen Sie sicher, dass Sie bei der Eingabe in die Liste allen URLs **http** oder **https** voranstellen.
- Sie können das Platzhaltersymbol (*) entsprechend den Regeln in der folgenden Liste mit zulässigen Mustern verwenden.
- Sie können Portnummern in der Adresse angeben. Wenn Sie keine Portnummer angeben, werden folgende Werte verwendet:
    - Port 80 für http
    - Port 443 für https
- Die Verwendung von Platzhaltern für die Portnummer wird **nicht** unterstützt. Beispielsweise werden `http://www.contoso.com:*` und `http://www.contoso.com:*/` nicht unterstützt.

    |    URL    |    Details    |    Treffer    |    Stimmt nicht überein mit    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Entspricht einer einzelnen Seite    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Entspricht einer einzelnen Seite    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    Entspricht allen URLs, die mit `www.contoso.com` beginnen    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Entspricht allen Unterdomänen unter `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    Entspricht einem einzelnen Ordner    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Entspricht einer einzelnen Seite, unter Verwendung einer Portnummer    |    http://www.contoso.com:80    |         |
    |    `https://www.contoso.com`    |    Entspricht einer einzelnen, sicheren Seite    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Entspricht einem einzelnen Ordner und allen Unterordnern    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
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
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>Definieren des Verhaltens, wenn Benutzer versuchen, auf eine blockierte Website zuzugreifen

Mit dem in Microsoft Edge integrierten Modell doppelter Identitäten können Sie eine flexiblere Erfahrung für Ihre Endbenutzer bieten, was mit dem Intune Managed Browser nicht möglich war. Wenn Benutzer in Microsoft Edge auf eine blockierte Website klicken, können sie aufgefordert werden, den Link in ihrem privaten Kontext statt ihrem geschäftlichen Kontext zu öffnen. Dadurch bleiben sie selber und gleichzeitig die Unternehmensressourcen geschützt. Wenn ein Benutzer beispielsweise einen Link zu einem Nachrichtenartikel über sein Outlook gesendet hat, kann er ihn seinem privaten Kontext oder auf einer InPrivate-Registerkarte statt in seinem geschäftlichen Kontext öffnen, der Nachrichtenwebsites nicht zulässt. Diese Übergänge sind standardmäßig zulässig.

Verwenden Sie das nachstehende Schlüssel-Wert-Paar, um zu konfigurieren, ob diese weichen Übergänge zulässig sind:

|    Key    |    Wert    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** erlaubt es Microsoft Edge, Benutzer an ihren privaten Kontext zu übergeben, um blockierte Websites zu öffnen.<p>**Block** verhindert, dass Microsoft Edge Benutzer übergibt. Den Benutzern wird in einer Meldung einfach mitgeteilt, dass die Website, auf die sie zuzugreifen versuchen, blockiert ist.    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Weiterleiten von Benutzern an Microsoft Edge statt an den Intune Managed Browser 

Sowohl der Intune Managed Browser als auch Microsoft Edge werden jetzt als durch eine Richtlinie geschützte Browser verwendet. Wenn Sie sicherstellen möchten, dass Ihre Benutzer weitergeleitet werden, damit sie die richtige Browser-App verwenden, legen Sie für alle Ihre von Intune verwalteten Apps (z.B. Outlook und OneDrive) die folgende Konfigurationseinstellung fest:

|    Key    |    Wert    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Der Wert `true` leitet Ihre Benutzer weiter, damit sie Microsoft Edge verwenden.<p>Der Wert `false` leitet Ihre Benutzer weiter, damit sie den Intune Managed Browser verwenden.    |

Wenn dieser App-Konfigurationswert nicht festgelegt wird, definiert die folgende Logik, welcher Browser zum Öffnen von Unternehmenslinks verwendet werden soll.

Unter Android:
- Der Intune Managed Browser wird gestartet, wenn ein Benutzer sowohl den Intune Managed Browser als auch Microsoft Edge auf sein Gerät heruntergeladen hat. 
- Microsoft Edge wird geöffnet, wenn nur Microsoft Edge auf das Gerät heruntergeladen und eine entsprechende Intune-Richtlinie festgelegt wurde.
- Managed Browser wird geöffnet, wenn nur Managed Browser auf dem Gerät installiert ist und eine entsprechende Intune-Richtlinie festgelegt wurde.

Unter iOS für Apps, in denen das Intune SDK für iOS, Version 9.0.9+ integriert ist:
- Der Intune Managed Browser wird gestartet, wenn sowohl der Managed Browser als auch Microsoft Edge auf dem Gerät installiert sind.  
- Microsoft Edge wird gestartet, wenn nur Microsoft Edge auf dem Gerät installiert ist und eine entsprechende Intune-Richtlinie festgelegt wurde.
- Managed Browser wird gestartet, wenn nur Managed Browser auf dem Gerät installiert ist und eine entsprechende Intune-Richtlinie festgelegt wurde.

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Verwenden von Microsoft Edge unter iOS für den Zugriff auf verwaltete App-Protokolle 

Endbenutzer, auf deren iOS-Gerät Microsoft Edge installiert ist, können den Verwaltungsstatus aller von Microsoft veröffentlichten Apps anzeigen. Sie können Protokolle für die Problembehandlung ihrer verwalteten iOS-Apps senden.
1. Öffnen Sie Microsoft Edge auf Ihrem iOS-Gerät.
2. Geben Sie im Adressfeld `about:intunehelp` ein. 
3. Der Problembehandlungsmodus wird in Microsoft Edge gestartet.

Eine Liste der in den App-Protokollen gespeicherten Einstellungen finden Sie unter [Prüfung der App-Schutzprotokolle in Managed Browser](app-protection-policy-settings-log.md).

Informationen zum Anzeigen von Protokollen auf Android-Geräten finden Sie unter [Senden von Protokollen an Ihren IT-Administrator per E-Mail](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Sicherheit und Datenschutz für Microsoft Edge

Zusätzliche Überlegungen zu Sicherheit und Datenschutz für Microsoft Edge:

- Microsoft Edge nutzt keine Einstellungen, die Benutzer für den systemeigenen Browser auf ihren Geräten festlegen, weil Microsoft Edge auf diese Einstellungen nicht zugreifen kann.
- Wenn Sie die Option **Einfache PIN für den Zugriff erforderlich** oder **Unternehmensanmeldeinformationen für den Zugriff erforderlich** in einer App-Schutzrichtlinie konfigurieren, die Microsoft Edge zugeordnet ist, und ein Benutzer auf der Authentifizierungsseite den Hilfelink auswählt, kann er beliebige Websites besuchen. Dies gilt unabhängig davon, ob sie in der Richtlinie einer Blockierungsliste hinzugefügt wurden.
- Microsoft Edge kann den Zugriff auf Websites nur blockieren, wenn darauf direkt zugegriffen wird. Der Zugriff auf die Website wird nicht blockiert, wenn dafür Zwischendienste (z.B. ein Übersetzungsdienst) verwendet werden.
- Um die Authentifizierung und den Zugriff auf die Intune-Dokumentation zuzulassen, ist * **.microsoft.com** von den Einstellungen für Zulassungs- oder Blockierungsliste ausgenommen. Es ist immer zulässig.
Deaktivieren Sie Nutzungsdaten. Microsoft sammelt automatisch anonyme Daten über die Leistung und Verwendung von Managed Browser, um Microsoft-Produkte und -Dienste zu verbessern. Benutzer können die Erfassung von Daten mithilfe der Einstellung für **Nutzungsdaten** auf ihren Geräten deaktivieren. Sie haben keine Kontrolle über die Erfassung dieser Daten. Auf iOS-Geräten können von Benutzern besuchte Websites, deren Zertifikat abgelaufen oder nicht vertrauenswürdig ist, nicht geöffnet werden.

## <a name="next-steps"></a>Nächste Schritte

- [Was sind App-Schutzrichtlinien?](app-protection-policy.md) 
