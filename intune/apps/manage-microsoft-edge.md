---
title: Verwalten von Microsoft Edge für iOS und Android mit Intune
titleSuffix: ''
description: Verwenden Sie Intune-App-Schutzrichtlinien mit Microsoft Edge, um sicherzustellen, dass auf Unternehmenswebsites immer mit eingerichteten Sicherheitsmaßnahmen zugegriffen wird.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 890709ccf176f2b0cc6c4a3af986d1bce642572d
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754408"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Verwalten des Webzugriffs mithilfe von Microsoft Edge mit Microsoft Intune

Die Verwendung von Intune-App-Schutzrichtlinien mit Microsoft Edge hilft dabei sicherzustellen, dass auf Unternehmenswebsites immer mit eingerichteten Sicherheitsmaßnahmen zugegriffen wird. Die folgenden durch Intune-Richtlinien ermöglichten Microsoft Edge-Unternehmensfunktionen sind verfügbar:

- **Zwei Identitäten**. Benutzer können sowohl Geschäftskonten als auch persönliche Konten zum Browsen hinzufügen. Die beiden Identitäten sind vollständig voneinander getrennt, ähnlich wie bei Office 365 und Outlook. Intune-Administratoren können die gewünschten Richtlinien für geschütztes Browsen im Geschäftskonto festlegen.
- **Integration von Intune-App-Schutzrichtlinien**. Da Microsoft Edge in das Intune SDK integriert ist, können Sie Anwendungsschutzrichtlinien darauf anwenden, um Schutz vor Datenverlust zu bieten. Diese Funktionen umfassen Folgendes: Kontrolle von Ausschneiden, Kopieren und Einfügen, Verhindern von Bildschirmaufnahmen und Sicherstellen, dass vom Benutzer ausgewählte Links nur in anderen verwalteten Apps geöffnet werden.
- **Integration des Azure-Anwendungsproxys**. Sie können den Zugriff auf SaaS-Apps (Software-as-a-Service) und Web-App kontrollieren. So können Sie sicherstellen, dass browserbasierte Apps nur im sicheren Microsoft Edge-Browser ausgeführt werden –unabhängig davon, ob Endbenutzer eine Verbindung über das Unternehmensnetzwerk oder das Internet herstellen.
- **Anwendungskonfiguration**. Sie können Einstellungen für die Anwendungskonfiguration nutzen, um den Sicherheitsstatus Ihrer Organisation zu verbessern und benutzerfreundliche Features für Ihre Endbenutzer zu konfigurieren. Beispielsweise können Sie Lesezeichen, eine Verknüpfung zur Startseite, zulässige/blockierte Websites sowie den Azure Active Directory-Anwendungsproxy definieren.

Microsoft Intune-Schutzrichtlinien für Microsoft Edge tragen dazu bei, die Daten und Ressourcen Ihres Unternehmens zu schützen. Durch die Verwendung dieser Richtlinien mit Microsoft Edge wird sichergestellt, dass die Ressourcen Ihres Unternehmens nicht nur in systemintern installierten Apps geschützt sind, sondern auch, wenn darauf über den Webbrowser zugegriffen wird.

## <a name="getting-started"></a>Erste Schritte

Sie und Ihre Endbenutzer können Microsoft Edge aus öffentlichen App-Stores für die Verwendung in Ihrer Organisation herunterladen. Für Browserrichtlinien ist eins der folgenden Betriebssysteme erforderlich:
- Android 4 und höher
- iOS 8.0 und höher

## <a name="application-protection-policies-for-microsoft-edge"></a>Anwendungsschutzrichtlinien für Microsoft Edge

Da Microsoft Edge in das Intune SDK integriert ist, können Sie Anwendungsschutzrichtlinien darauf anwenden.

Sie können diese Einstellungen auf Folgendes anwenden:
- Geräte, die bei Intune registriert sind
- Geräte, die mithilfe eines anderen Produkts für die Verwaltung mobiler Geräte verwaltet werden
- Nicht verwaltete Geräte

Wenn Microsoft Edge keine Intune-Richtlinie zugeordnet wird, können Benutzer diesen Browser nicht verwenden, um auf Daten aus anderen von Intune verwalteten Anwendungen wie Office-Apps zuzugreifen. 

## <a name="conditional-access-for-microsoft-edge"></a>Bedingter Zugriff für Microsoft Edge

Sie können den bedingten Azure AD-Zugriff nutzen, um Ihre Benutzer weiterzuleiten, damit diese nur über Microsoft Edge auf Unternehmensdaten zugreifen können. Das schränkt den mobilen Browserzugriff bei mit Azure AD verbundenen Web-Apps auf den richtliniengeschützten Microsoft Edge-Browser ein. Der Zugriff über andere, nicht geschützte Browser wie z.B. Safari oder Chrome ist gesperrt. Sie können den bedingten Zugriff auf Azure-Ressourcen wie Exchange Online, SharePoint Online, das Microsoft 365 Admin Center und sogar auf lokale Websites anwenden, die Sie über den [Azure AD-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) für externe Benutzer verfügbar gemacht haben.

So schränken Sie bei mit Azure AD verbundenen Web-Apps die Verwendung von Microsoft Edge unter iOS und Android ein:
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie unter dem Knoten „Intune“ die Optionen **Bedingter Zugriff** > **Neue Richtlinie** aus.
3. Klicken Sie im Abschnitt **Zugriffssteuerungen** des Blatts auf **Gewähren**.
4. Klicken Sie auf **Genehmigte Client-App erforderlich**.
5. Klicken Sie auf dem Blatt **Gewähren** auf **Auswählen**. Diese Richtlinie muss den Cloud-Apps zugewiesen sein, auf die nur über die Intune Managed Browser-App zugegriffen werden soll.

    ![Screenshot der Richtlinie für bedingten Zugriff: Gewähren von Zugriff](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Klicken Sie im Abschnitt „Zuweisungen“ auf **Bedingungen** > **Client-Apps**. Das Blatt **Client-Apps** wird angezeigt.
7. Klicken Sie unter **Konfigurieren** auf **Ja**, um die Richtlinie auf bestimmte Client-Apps anzuwenden.
8. Überprüfen Sie, ob der **Browser** als Client-App ausgewählt ist.

    ![Screenshot der Richtlinie für bedingten Zugriff: Auswählen von Client-Apps](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Wenn Sie festlegen möchten, welche nativen Apps (Apps, die nicht browserbasiert sind) auf die Cloudanwendungen zugreifen können, können Sie auch **Mobile apps and desktop clients** (Mobile Apps und Desktop-Clients) auswählen.

9. Klicken Sie im Bereich **Zuweisungen** auf **Benutzer und Gruppen**, und wählen Sie dann die Benutzer und Gruppen aus, denen Sie diese Richtlinie zuweisen möchten.

10. Klicken Sie im Abschnitt **Zuweisungen** auf **Cloud-Apps**, um auszuwählen, welche Apps mit dieser Richtlinie geschützt werden sollen.

Nach diese Richtlinie konfiguriert wurde, müssen Benutzer Microsoft Edge verwenden, um auf die mit Azure AD verbundenen Web-Apps zuzugreifen, die Sie mit der Richtlinie geschützt haben. Wenn Benutzer versuchen, in diesem Szenario einen nicht verwalteten Browser zu verwenden, werden sie in einer Meldung informiert, dass sie Microsoft Edge verwenden müssen.

> [!TIP]
> Der bedingte Zugriff ist eine Azure AD-Technologie. Bei dem Knoten für bedingten Zugriff, auf den aus Intune zugegriffen wird, handelt es sich um denselben Knoten, auf den aus Azure AD zugegriffen wird.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Einmaliges Anmelden bei mit Azure AD verbundenen Web-Apps in richtliniengeschützten Browsern

Microsoft Edge unter iOS und Android kann für alle Web-Apps (SaaS und lokal), die mit Azure AD verbunden sind, die Möglichkeit des einmaligen Anmeldens (Single Sign-On, SSO) nutzen. Dank SSO können Benutzer über Microsoft Edge auf mit Azure AD verbundene Web-Apps zugreifen, ohne ihre Anmeldeinformationen erneut eingeben zu müssen.

Für SSO muss Ihr Gerät entweder durch die Microsoft Authenticator-App für iOS-Geräte oder durch das Intune-Unternehmensportal unter Android registriert werden. Wenn Benutzer über eine dieser beiden Optionen verfügen, werden sie aufgefordert, ihr Gerät zu registrieren, wenn sie eine Web-App in einem richtliniengeschützten Browser öffnen, die mit Azure AD verbunden ist. (Dies gilt nur, wenn ihr Gerät noch nicht registriert wurde.) Nachdem das Gerät mit dem von Intune verwalteten Benutzerkonto registriert wurde, ist bei diesem Konto SSO für mit Azure AD verbundene Web-Apps aktiviert.

> [!NOTE]
> Bei der Geräteregistrierung handelt es sich um einen einfachen Check-In beim Azure AD-Dienst. Hierbei ist keine vollständige Geräteregistrierung erforderlich, und die IT-Abteilung erhält keine zusätzlichen Berechtigungen auf dem Gerät.

## <a name="create-a-protected-browser-app-configuration"></a>Erstellen einer geschützten Browser-App-Konfiguration

So erstellen Sie eine App-Konfiguration für Microsoft Edge:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Client-Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen** aus.
3. Geben Sie auf dem Blatt **Konfigurationsrichtlinie hinzufügen** einen **Namen** und optional eine **Beschreibung** für die App-Konfigurationseinstellungen ein.
4. Wählen Sie als Typ der **Geräteregistrierung** die Option **Verwaltete Apps** aus.
5. Klicken Sie auf **Wählen Sie die erforderliche App aus**. Wählen Sie dann auf dem Blatt **Ziel-Apps** entweder den **Managed Browser** oder **Edge** für iOS, für Android oder für beides aus.
6. Klicken Sie auf **OK**, um zum Blatt **Konfigurationsrichtlinie hinzufügen** zurückzukehren.
7. Wählen Sie **Konfigurationseinstellungen** aus. Auf dem Blatt **Konfiguration** definieren Sie Schlüssel-Wert-Paare, um Konfigurationen für Microsoft Edge bereitzustellen. In den folgenden Abschnitten erhalten Sie weitere Informationen zu den unterschiedlichen Schlüssel-Wert-Paaren, die Sie definieren können.

    > [!NOTE]
    > Microsoft Edge verwendet die gleichen Schlüssel-Wert-Paare wie Managed Browser. Unter Android muss Microsoft Edge App-Schutzrichtlinien enthalten, damit App-Konfigurationsrichtlinien wirksam werden.

8. Klicken Sie abschließend auf **OK**.
9. Wählen Sie auf dem Blatt **Konfigurationsrichtlinie hinzufügen** die Option **Hinzufügen** aus.<br>
    Die neue Konfiguration wird erstellt und auf dem Blatt **App-Konfiguration** angezeigt.

## <a name="assign-the-configuration-settings-you-created"></a>Zuweisen der erstellten Konfigurationseinstellungen 

Sie weisen die Einstellungen Gruppen von Benutzern in Azure AD zu. Haben diese Benutzer die geschützte Browser-Ziel-App installiert, wird die App durch die angegebenen Einstellungen verwaltet.

1. Wählen Sie auf dem Blatt **Client-Apps** im Intune-Dashboard für die Verwaltung von mobilen Anwendungen die Option **App-Konfigurationsrichtlinie** aus.
2. Wählen Sie aus der Liste der App-Konfigurationen diejenige aus, die Sie zuweisen möchten.
3. Wählen Sie auf dem nächsten Blatt **Zuweisungen** aus.
4. Wählen Sie auf dem Blatt **Zuweisungen** die Azure AD-Gruppe aus, der Sie die App-Konfiguration zuweisen möchten, und klicken Sie dann auf **OK**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Weiterleiten von Benutzern an Microsoft Edge statt an den Intune Managed Browser 

Sowohl der Intune Managed Browser als auch Microsoft Edge können als richtliniengeschützte Browser verwendet werden. Wenn Sie sicherstellen möchten, dass Ihre Benutzer an die richtige Browser-App weitergeleitet werden, legen Sie für all Ihre von Intune verwalteten Apps (z.B. Outlook, OneDrive und SharePoint) die folgende Konfigurationseinstellung fest:

|    Key    |    Wert    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Wenn der Wert `true` festgelegt ist, werden Ihre Benutzer zum Download und zur Verwendung von Microsoft Edge angewiesen.<br>Wenn der Wert `false` festgelegt ist, können Ihre Benutzer Intune Managed Browser verwenden.    |

Wenn dieser App-Konfigurationswert **nicht** festgelegt ist, definiert die folgende Logik, welcher Browser zum Öffnen von Unternehmenslinks verwendet wird.

Unter Android:
- Wenn ein Benutzer sowohl den Intune Managed Browser als auch Microsoft Edge auf sein Gerät heruntergeladen hat, wird der Intune Managed Browser gestartet. 
- Wenn nur Microsoft Edge auf das Gerät heruntergeladen und eine entsprechende Intune-Richtlinie festgelegt wurde, wird Microsoft Edge gestartet.
- Wenn sich nur der Managed Browser auf dem Gerät befindet und eine entsprechende Intune-Richtlinie festgelegt wurde, wird der Managed Browser gestartet.

Unter iOS für Apps, in denen das Intune SDK für iOS, Version 9.0.9+ integriert ist:
- Wenn sowohl der Managed Browser als auch Microsoft Edge auf dem Gerät installiert sind, wird der Intune Managed Browser gestartet.  
- Wenn sich nur Microsoft Edge auf dem Gerät befindet und eine entsprechende Intune-Richtlinie festgelegt wurde, wird Microsoft Edge gestartet.
- Wenn sich nur der Managed Browser auf dem Gerät befindet und eine entsprechende Intune-Richtlinie festgelegt wurde, wird der Managed Browser gestartet.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Konfigurieren von Anwendungsproxyeinstellungen für Microsoft Edge

Sie können Microsoft Edge und den [Azure AD-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) gemeinsam verwenden, um Benutzern auf ihren mobilen Geräten Zugriff auf Intranetsites zu ermöglichen. 

Im Folgenden finden Sie einige Beispiele für Szenarien, die durch den Azure AD-Anwendungsproxy ermöglicht werden: 

- Ein Benutzer verwendet die mobile Outlook-App, die durch Intune geschützt ist. Dann klickt er in einer E-Mail auf einen Link zu einer Intranetsite, und Microsoft Edge erkennt, dass diese Site dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Der Benutzer wird automatisch über den Anwendungsproxy weitergeleitet, um sich mit einer anwendbaren Option für die mehrstufige Authentifizierung und bedingtem Zugriff zu authentifizieren, bevor er zur Intranetsite gelangt. Der Benutzer kann jetzt auch auf seinem mobilen Gerät auf Intranetsites zugreifen, und der Link in Outlook funktioniert wie erwartet.
- Ein Benutzer öffnet Microsoft Edge auf seinem iOS- oder Android-Gerät. Wenn Microsoft Edge durch Intune geschützt ist und der Anwendungsproxy aktiviert wurde, kann der Benutzer über die gewohnte interne URL zu einer Intranetsite navigieren. Microsoft Edge erkennt, dass diese Intranetsite dem Benutzer über den Anwendungsproxy verfügbar gemacht wurde. Der Benutzer wird zur Authentifizierung automatisch über den Anwendungsproxy weitergeleitet, bevor er zur Intranetsite gelangt. 

### <a name="before-you-start"></a>Vorbereitung

- Richten Sie Ihre internen Anwendungen über den Azure AD-Anwendungsproxy ein.
  - Informationen zum Konfigurieren des Anwendungsproxys und zum Veröffentlichen von Anwendungen finden Sie in der [Setup-Dokumentation](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- Der Microsoft Edge-App muss eine [Intune-App-Schutzrichtlinie](app-protection-policy.md) zugewiesen werden.

> [!NOTE]
> Es kann bis zu 24 Stunden dauern, bis aktualisierte Umleitungsdaten des Anwendungsproxys in Managed Browser und Microsoft Edge in Kraft treten.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>Schritt 1: Aktivieren der automatischen Umleitung von Outlook zu Microsoft Edge
Konfigurieren Sie Outlook mit einer App-Schutzrichtlinie, mit der die Einstellung **Webinhalt für per Richtlinie verwaltete Browser freigeben** aktiviert wird.

![Screenshot der App-Schutzrichtlinie „Webinhalt für per Richtlinie verwaltete Browser freigeben“](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Schritt 2: Festlegen der App-Konfigurationseinstellung zum Aktivieren des Anwendungsproxys
Geben Sie Microsoft Edge als Ziel für das folgende Schlüssel-Wert-Paar an, um den Anwendungsproxy für Microsoft Edge zu aktivieren:

|    Key    |    Wert    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Weitere Informationen zur gemeinsamen Verwendung von Microsoft Edge und dem Azure AD-Anwendungsproxy für nahtlosen (und geschützten) Zugriff auf lokale Web-Apps finden Sie im Blogbeitrag [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Intune und Azure Active Directory gemeinsam verwenden, um den Benutzerzugriff zu verbessern). Dieser Blogbeitrag verweist auf den Intune Managed Browser; der Inhalt gilt aber auch für Microsoft Edge.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Konfigurieren einer Verknüpfung mit der Homepage für Microsoft Edge

Diese Einstellung ermöglicht Ihnen das Konfigurieren einer Verknüpfung zur Startseite für Microsoft Edge. Die von Ihnen konfigurierte Verknüpfung mit der Homepage wird als erstes Symbol unterhalb der Suchleiste angezeigt, wenn ein Benutzer eine neue Registerkarte in Microsoft Edge öffnet. Der Benutzer kann diese Verknüpfung in seinem verwalteten Kontext nicht bearbeiten oder löschen. Die Verknüpfung mit der Homepage zeigt zur besseren Erkennbarkeit den Namen Ihrer Organisation an. 

Verwenden Sie das folgende Schlüssel-Wert-Paar zum Konfigurieren einer Verknüpfung mit der Homepage:

|    Key    |    Wert    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Geben Sie eine gültige URL ein. Ungültige URLs werden zur Sicherheit gesperrt.<br>**Beispiel**: <`https://www.bing.com`>

## <a name="configure-your-organizations-logo-and-brand-color-for-new-tab-pages-in-microsoft-edge"></a>Konfigurieren des Logos und der Markenfarbe Ihrer Organisation für neue Registerkartenseiten in Microsoft Edge

Mit diesen Einstellungen können Sie die „Neuer Tab“-Seite für Microsoft Edge so anpassen, dass das Logo und die Markenfarbe Ihrer Organisation als Seitenhintergrund angezeigt werden.

Um das Logo und die Farbe Ihrer Organisation hochzuladen, führen Sie zuerst die folgenden Schritte aus:
- Navigieren Sie im Azure-Portal zu „Intune -> Client-Apps -> Branding und Anpassung -> Branding des Unternehmensportals“.
- Um das Logo Ihrer Marke festzulegen, wählen Sie unter „Anzeigen“ die Option „Nur Firmenlogo“ aus. Es empfiehlt sich, transparente Hintergrundlogos zu verwenden. 
- Um die Hintergrundfarbe Ihrer Marke festzulegen, wählen Sie unter „Anzeigen“ die Option „Designfarbe“ aus. Microsoft Edge wendet einen helleren Farbton der Farbe auf die Seite „Neuer Tab“ an. Dadurch ist sichergestellt, dass die Seite gut lesbar ist. 

Verwenden Sie nun die folgenden Schlüssel/Wert-Paare, um das Branding Ihrer Organisation in Microsoft Edge zu übernehmen:

|    Key    |    Wert    |
|--------------------------------------------------------------------|------------|
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandLogo    |    True    |
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandColor    |    True    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Konfigurieren von verwalteten Lesezeichen für Microsoft Edge

Für erleichterte Bedienung können Sie Lesezeichen konfigurieren, die Ihren Benutzern bei der Verwendung von Microsoft Edge zur Verfügung stehen sollen. 

Hier sind einige Details:

- Diese Lesezeichen werden Benutzern nur angezeigt, wenn sie den [Unternehmensmodus](https://docs.microsoft.com/intune/apps/app-configuration-managed-browser#how-to-configure-bookmarks-for-a-protected-browser) von Microsoft Edge verwenden. 
- Diese Lesezeichen können von Benutzern nicht gelöscht oder geändert werden.
- Diese Lesezeichen werden oben in der Liste angezeigt. Alle von Benutzern erstellten Lesezeichen werden unterhalb dieser Lesezeichen angezeigt.
- Wenn Sie die Anwendungsproxyumleitung aktiviert haben, können Sie Anwendungsproxy-Web-Apps mit deren interner oder externer URL hinzufügen.

Verwenden Sie das folgende Schlüssel-Wert-Paar zum Konfigurieren von verwalteten Lesezeichen:

|    Key    |    Wert    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    Der Wert für diese Konfiguration ist eine Liste von Lesezeichen. Jedes Lesezeichen besteht aus dem Lesezeichentitel und der Lesezeichen-URL. Trennen Sie Titel und URL durch das `|`-Zeichen.      Beispiel:<br>`Microsoft Bing|https://www.bing.com`<br>Zum Konfigurieren von mehreren Lesezeichen trennen Sie jedes Paar durch ein doppeltes `||`-Zeichen.<p>Beispiel:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Anzeigen von „MyApps“ in Microsoft Edge-Lesezeichen

Ihren Benutzern werden standardmäßig die MyApps-Websites angezeigt, die für sie in einem Ordner innerhalb der Microsoft Edge-Lesezeichen konfiguriert wurden. Der Ordner wird mit dem Namen Ihrer Organisation bezeichnet.

|    Key    |    Wert    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** zeigt „MyApps“ in den Microsoft Edge-Lesezeichen.<p>**False** blendet „MyApps“ in den Microsoft Edge-Lesezeichen aus.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Angeben der Liste zulässiger oder blockierter Websites für Microsoft Edge
Sie können mit der App-Konfiguration definieren, auf welche Websites Ihre Benutzer unter Verwendung ihres Arbeitsprofils zugreifen können. Wenn Sie eine Zulassungsliste verwenden, können Ihre Benutzer nur auf die Websites zugreifen, die Sie explizit aufgelistet haben. Wenn Sie eine Sperrliste verwenden, können Ihre Benutzer auf alle Websites zugreifen – mit Ausnahme der Websites, die Sie explizit blockiert haben. Sie sollten entweder nur eine Zulassungsliste oder nur eine Blockierungsliste vorgeben, nicht beide Listen. Wenn Sie beide Listen angeben, wird die Zulassungsliste berücksichtigt.  

Verwenden Sie die folgenden Schlüssel-Wert-Paare, um entweder eine Zulassungsliste oder eine Sperrliste für Websites in Microsoft Edge zu konfigurieren. 

|    Key    |    Wert    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Es stehen die folgenden Optionen zur Auswahl:<p>1. Geben Sie zulässige URLs an (nur diese URLs sind zulässig. Es kann nicht auf andere Websites zugegriffen werden):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Angeben von blockierten URLs (auf alle anderen Websites kann zugegriffen werden):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    Der entsprechende Wert für den Schlüssel ist eine Liste mit URLs. Sie geben alle URLs, die Sie zulassen oder blockieren möchten, als einen einzelnen Wert ein, der durch einen senkrechten Strich (`|`) getrennt ist.<br>**Beispiele:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>URL-Formate für die Liste zulässiger und blockierter Websites 
Sie können verschiedene URL-Formate verwenden, um Ihre Listen für zulässige/blockierte Websites zu erstellen. Diese zulässigen Muster werden in der folgenden Tabelle beschrieben. Einige Hinweise, bevor Sie beginnen: 
- Stellen Sie sicher, dass Sie bei der Eingabe in die Liste allen URLs **http** oder **https** voranstellen.
- Sie können das Platzhaltersymbol (\*) entsprechend den Regeln in der folgenden Liste mit zulässigen Mustern verwenden.
- Ein Platzhalter kann nur mit einer vollständigen Komponente des (durch Punkte getrennten) Hostnamens oder mit vollständigen Teilen des (durch Schrägstriche getrennten) Pfads übereinstimmen. `http://*contoso.com` wird beispielsweise **nicht** unterstützt.
- Sie können Portnummern in der Adresse angeben. Wenn Sie keine Portnummer angeben, werden folgende Werte verwendet:
  - Port 80 für http
  - Port 443 für https
- Die Verwendung von Platzhaltern für die Portnummer wird **nicht** unterstützt. Beispielsweise werden `http://www.contoso.com:*` und `http://www.contoso.com:*/` nicht unterstützt. 

    |    URL    |    Details    |    Treffer    |    Stimmt nicht überein mit    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Entspricht einer einzelnen Seite    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Entspricht einer einzelnen Seite    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    Entspricht allen URLs, die mit `www.contoso.com` beginnen    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Entspricht allen Unterdomänen unter `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`
    |    `http://*contoso.com/*`    |    Entspricht allen Unterdomänen, die mit `contoso.com/` enden    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    Entspricht einem einzelnen Ordner    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Entspricht einer einzelnen Seite, unter Verwendung einer Portnummer    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Entspricht einer einzelnen, sicheren Seite    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Entspricht einem einzelnen Ordner und allen Unterordnern    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Im Folgenden finden Sie Beispiele für Eingaben, die nicht unterstützt werden:
  - `*.com`
  - `*.contoso/*`
  - `www.contoso.com/*images`
  - `www.contoso.com/*images*pigs`
  - `www.contoso.com/page*`
  - IP-Adressen
  - `https://*`
  - `http://*`
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="define-behavior-when-users-try-to-access-a-blocked-site"></a>Definieren des Verhaltens, wenn Benutzer versuchen, auf eine blockierte Website zuzugreifen

Mit dem in Microsoft Edge integrierten Modell für doppelte Identitäten können Sie Ihren Endbenutzern ein flexibleres Benutzererlebnis bieten, was mit dem Intune Managed Browser nicht möglich war. Wenn Benutzer versuchen, in Microsoft Edge eine blockierte Website zu öffnen, können sie aufgefordert werden, den Link in ihrem persönlichen Kontext anstatt in ihrem Arbeitskontext zu öffnen. So bleiben der Schutz der Benutzer und die Sicherheit der Unternehmensressourcen erhalten. Wenn ein Benutzer beispielsweise über Outlook einen Link zu einem Nachrichtenartikel erhält, kann er diesen Link im persönlichen Kontext oder auf einer privaten Registerkarte öffnen. Der Arbeitskontext lässt keine Nachrichtenwebsites zu. Diese Übergänge sind standardmäßig zulässig.

Verwenden Sie das folgende Schlüssel-Wert-Paar, um zu konfigurieren, ob diese weichen Übergänge zulässig sind:

|    Key    |    Wert    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** erlaubt es Microsoft Edge, Benutzer an ihren persönlichen Kontext weiterzuleiten, um blockierte Websites zu öffnen.<p>**Block** verhindert, dass Microsoft Edge Benutzer weiterleitet. Benutzern wird einfach eine Meldung angezeigt, die besagt, dass die Website, auf die sie versuchen zuzugreifen, gesperrt ist.    |

## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Verwenden von Microsoft Edge unter iOS für den Zugriff auf Protokolle für verwaltete Apps 

Benutzer, auf deren iOS-Gerät Microsoft Edge installiert ist, können den Verwaltungsstatus aller von Microsoft veröffentlichten Apps anzeigen. Sie können Protokolle für die Problembehandlung ihrer verwalteten iOS-Apps senden. Gehen Sie wie folgt vor:
1. Öffnen Sie Microsoft Edge auf Ihrem iOS-Gerät.
2. Geben Sie im Adressfeld `about:intunehelp` ein. 
3. Microsoft Edge wird im Problembehandlungsmodus gestartet.

Eine Liste der in den App-Protokollen gespeicherten Einstellungen finden Sie unter [Prüfung der App-Schutzprotokolle in Managed Browser](app-protection-policy-settings-log.md).

Informationen zum Anzeigen von Protokollen auf Android-Geräten finden Sie unter [Senden von Protokollen an Ihren IT-Administrator per E-Mail](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Sicherheit und Datenschutz für Microsoft Edge

Im Folgenden finden Sie einige weitere Überlegungen zu Sicherheit und Datenschutz für Microsoft Edge:

- Microsoft Edge nutzt keine Einstellungen, die Benutzer für den nativen Browser auf ihren Geräten festlegen, weil Microsoft Edge auf diese Einstellungen nicht zugreifen kann.
- Sie können die Option **Einfache PIN für den Zugriff erforderlich** oder **Unternehmensanmeldeinformationen für den Zugriff erforderlich** in einer App-Schutzrichtlinie konfigurieren, die Microsoft Edge zugeordnet ist. Wenn ein Benutzer auf der Authentifizierungsseite den Link „Hilfe“ auswählt, kann er beliebige Websites aufrufen, unabhängig davon, ob diese in der Richtlinie einer Sperrliste hinzugefügt wurden.
- Microsoft Edge kann den Zugriff auf Websites nur blockieren, wenn darauf direkt zugegriffen wird. Der Zugriff auf die Website wird nicht blockiert, wenn Benutzer dafür Zwischendienste (z.B. einen Übersetzungsdienst) verwenden.
- Um die Authentifizierung und den Zugriff auf die Intune-Dokumentation zuzulassen, ist * **.microsoft.com** von den Einstellungen für Zulassungs- oder Blockierungsliste ausgenommen. Dies ist immer zulässig.
- Benutzer können die Datensammlung deaktivieren. Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung von Managed Browser, um Microsoft-Produkte und -Dienste zu verbessern. Benutzer können die Erfassung von Daten mithilfe der Einstellung für **Nutzungsdaten** auf ihren Geräten deaktivieren. Sie haben keine Kontrolle über die Erfassung dieser Daten. Auf iOS-Geräten können von Benutzern besuchte Websites, deren Zertifikat abgelaufen oder nicht vertrauenswürdig ist, nicht geöffnet werden.

## <a name="next-steps"></a>Nächste Schritte

- [Was sind App-Schutzrichtlinien?](app-protection-policy.md) 
