---
title: Updates der Benutzeroberfläche für Endbenutzer-Apps in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, was sich an der Benutzeroberfläche für Apps geändert hat, die auf Endbenutzergeräten mit Microsoft Intune verwendet werden können.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1710fd315803c4b47ad3be343893f93f7d155135
ms.sourcegitcommit: 27e63a96d15bc4062af68c2764905631bd928e7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71061730"
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Updates der Benutzeroberfläche für Endbenutzer-Apps in Intune
Lernen Sie die neuesten Updates für die Microsoft Intune-Apps kennen. Wir verbessern regelmäßig die App und Website des Intune-Unternehmensportals und fügen Neues hinzu. Wenn Sie ein Intune-Administrator sind oder im Support arbeiten, bietet Ihnen dieser Artikel Informationen für Folgendes:

* Benachrichtigen von Kursteilnehmern und Mitarbeitern über Änderungen bei App und Registrierung.
* Aktualisieren der Dokumentation oder Helpdesk-Abläufe Ihrer Organisation.  

Wenn Sie ein Mitarbeiter oder Kursteilnehmer sind, sollten Sie sich die Screenshots und Links zur Hilfedokumentation für das Unternehmensportal ansehen. Weitere Informationen zur Benutzung der Unternehmensportal-App finden Sie in der [Benutzerhilfe-Dokumentation für das Unternehmensportal](https://docs.microsoft.com/intune-user-help/).  

<!---End-user messaging for accounts 1573558, 1712; changes to be made for other platforms for 1801 Users of the Company Portal website, will be blocked from taking actions that require write access to your tenant. They will see appropriate error messaging explaining that their account is under maintenance. Similar changes are coming to the Company Portal apps for Android, iOS, macOS, and Windows soon. ![Error message that occurs during account move](./media/account-move-rom-iwp-user-1712.png)--->


## <a name="week-of-september-9-2019"></a>Woche vom 9. September 2019

### <a name="updates-to-microsoft-intune-app----4997846---"></a>Updates der Microsoft Intune-App <!-- 4997846 -->
Die Microsoft Intune-App für Android wurde mit den folgenden Verbesserungen aktualisiert:
- Das Layout wurde aktualisiert und verbessert, um das unterste Navigationsmenü für die wichtigsten Aktionen einzubeziehen.
- Eine zusätzliche Seite, die das Profil des Benutzers anzeigt, wurde hinzugefügt.
- Die Anzeige von handlungsrelevanten Benachrichtigungen für den Benutzer wurde in der App hinzugefügt, z. B. die Notwendigkeit, die Geräteeinstellungen zu aktualisieren.
- Die Anzeige von benutzerdefinierten Pushbenachrichtigungen wurde hinzugefügt, wodurch die App der Unterstützung angepasst wird, die kürzlich in den Unternehmensportal-Apps für iOS und Android hinzugefügt wurde. Weitere Informationen finden Sie unter [Senden benutzerdefinierter Benachrichtigungen in Intune](custom-notifications.md).

    Beispiel für ein Benutzerprofil:<br>
    <img src="./media/intune-app-android-device-profile.png" alt="Screenshot of Microsoft Intune app for Android - User Profile" width="300">   

    Beispiel für Benachrichtigungen und die Navigation im unteren Seitenbereich:<br>
    <img src="./media/intune-app-android-device-notify.png" alt="Screenshot of Microsoft Intune app for Android - Notification" width="300">   


## <a name="week-of-june-24-2019"></a>Woche vom 24. Juni 2019  

### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Anzeigen aller installierten Apps auf der neuen Unternehmensportal-Webseite <!-- 4224326 -->
Auf der neuen Seite **Installierte Apps** der Unternehmensportalwebsite werden alle verwalteten Apps (sowohl erforderliche als auch verfügbare) aufgeführt, die auf den Geräten eines Benutzers installiert sind. Neben dem Zuweisungstyp können Benutzer auch den Herausgeber, das Veröffentlichungsdatum und den aktuellen Installationsstatus der Apps sehen. Wenn Sie keine Apps für Ihre Benutzer als erforderlich oder verfügbar eingerichtet haben, erhalten sie die Meldung, dass keine Unternehmens-Apps installiert wurden. Die neue Webseite finden Sie, indem Sie die [Unternehmensportalwebsite](https://portal.manage.microsoft.com) aufrufen und auf **Installierte Apps** klicken.   

![Screenshot: Seite „Installierte Apps“ auf der Unternehmensportalwebsite](/intune-user-help/media/intune-installed-apps-1907.png)     

### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>Mit der neuen Ansicht können Benutzer alle verwalteten Apps sehen, die auf einem Gerät installiert sind <!-- 2352913 -->
In der Unternehmensportal-App für Windows werden nun alle verwalteten (sowohl erforderlichen als auch verfügbaren) Apps aufgelistet, die auf dem Gerät eines Benutzers installiert sind. Benutzer können versuchte und ausstehende App-Installationen sowie deren aktuellen Status einsehen. Wenn Sie keine Apps für Ihre Benutzer als erforderlich oder verfügbar eingerichtet haben, erhalten sie die Meldung, dass keine Unternehmens-Apps installiert wurden. Die neue Ansicht finden Sie im Navigationsbereich des Unternehmensportals unter **Apps** > **Installierte Apps**.   

![Beispielscreenshot: Seite „Installierte Apps“ in der Unternehmensportal-App für Windows 10 ](/intune-user-help/media/installed-apps-cp-1906.png)  


## <a name="week-of-june-17-2019"></a>Woche vom 17. Juni 2019  

### <a name="new-features-in-microsoft-intune-app"></a>Neue Features in der Microsoft Intune-App
Der Microsoft Intune-App (Preview) für Android wurden neue Features hinzugefügt. Benutzer mit vollständig verwalteten Android-Geräten haben jetzt folgende Möglichkeiten:  

* Sie können die Geräte anzeigen und verwalten, die sie über das Intune-Unternehmensportal oder die Microsoft Intune-App registriert haben.    
* Sie können sich an ihre Organisation wenden, um Unterstützung zu erhalten.    
* Sie können Feedback an Microsoft senden.    
* Sie können Geschäftsbedingungen anzeigen, sofern diese von ihrer Organisation festgelegt wurden. 

## <a name="week-of-april-15-2019"></a>Woche vom 15. April 2019  

### <a name="new-end-user-app-microsoft-intune-app---3903244---"></a>Neue Endbenutzer-App (Microsoft Intune-App) <!--3903244 -->  
Für vollständig verwaltete Android-Geräte gibt es die neue Endbenutzer-App **Microsoft Intune**. Diese neue App ist besonders schlank und modern. Sie bietet ähnliche Funktionen wie die Unternehmensportal-App, aber für vollständig verwaltete unternehmenseigene Geräte. Weitere Informationen finden Sie unter der [Microsoft Intune-App auf Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).  

Beispielscreenshot der Gerätedetailanzeige: 

![Screenshot: Microsoft Intune-App mit Gerätedetails für „Jane's Android“](./media/1904-intune-app-device-details.png)   

Beispielscreenshot der Anzeige **Setup access** (Zugriff einrichten):  

![Screenshot: Microsoft Intune-App mit Anzeige zum Einrichten der Registrierung für den Zugriff](./media/1904-intune-app-setup-access.png)   

Beispielscreenshot des App-Menüs:  

![Screenshot: Microsoft Intune-App mit Seitenmenü](./media/1904-intune-app-navigation-menu.png)   

Beispielscreenshot der Anzeige **Hilfe**:  

![Screenshot: Microsoft Intune-App, Anzeige „Hilfe“](./media/1904-intune-app-help.png)   


## <a name="week-of-april-1-2019"></a>Woche vom 1. April 2019  

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Änderungen der Unternehmensportal-Registrierung für Benutzer von iOS 12-Geräten <!--3448635 -->  
Die Anzeigen und Schritte bei der Registrierung im Unternehmensportal für iOS wurden aktualisiert und entsprechen nun den Änderungen der MDM-Registrierung, die mit Apple iOS 12.2 veröffentlicht wurden. Der aktualisierte Workflow fordert Benutzer zu Folgendem auf:  

* Zulassen, dass Safari die Unternehmensportal-Website öffnet, das Verwaltungsprofil herunterlädt und dann zur Unternehmensportal-App zurückkehrt.  
* Öffnen der App „Settings“ (Einstellungen), um das Verwaltungsprofil auf dem Gerät zu installieren.  
* Rückkehr zur Unternehmensportal-App, um die Registrierung abzuschließen.  

Die aktualisierten Registrierungsschritte und -anzeigen finden Sie unter [Enroll iOS device in Intune (Registrieren eines iOS-Geräts in Intune)](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Update für die Benutzeroberfläche für die Unternehmensportal-App für iOS <!-- 2536024 -->
Die Startseite der Unternehmensportal-App für iOS-Geräte wurde neu gestaltet. Sie entspricht nun mehr dem Muster der iOS-Benutzeroberfläche, und zudem können Apps und E-Books besser gefunden werden.  

## <a name="week-of-february-19-2019"></a>Woche vom 19. Februar 2019  
### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780-wnready4review---"></a>Neue Anzeige „App-Kategorien“ in der Unternehmensportal-App für Windows 10<!-- 3834780 WNready4Review -->  
Eine neue Anzeige namens **App-Kategorien** wurde hinzugefügt, um das Durchsuchen und Auswählen von Apps im Unternehmensportal für Windows 10 zu verbessern. Für Benutzer werden Apps nun sortiert nach Kategorien wie **Empfohlen**, **Bildung** und **Produktivität** angezeigt. Diese Änderung ist im Unternehmensportal ab Version 10.3.3451.0 vorhanden. Weitere Informationen zum Installieren von Apps im Unternehmensportal finden Sie unter [Install and share apps on your device (Installieren und Freigeben von Apps auf Ihrem Gerät)](/intune-user-help/install-apps-cpapp-windows).  

![Screenshot: Unternehmensportal für Windows 10, Anzeige „App-Kategorien“](./media/1902_CP_app_categories.png)   


## <a name="week-of-november-12-2018"></a>Woche vom 12. November 2018

### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Tastenkombinationen für die Windows-Unternehmensportal-App <!-- 2771518 -->
Endbenutzer können ab sofort [mithilfe von Tastenkombinationen](https://docs.microsoft.com/intune/company-portal-app#windows-company-portal-keyboard-shortcuts) App- und Geräteaktionen im Windows-Unternehmensportal auslösen.

## <a name="week-of-october-22-2018"></a>Woche vom 22. Oktober 2018

### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Hinzufügen eines benutzerdefinierten Markenbilds für die Unternehmensportal-App <!-- 1916266 -->
Als Microsoft Intune-Administrator können Sie ein benutzerdefiniertes Markenbild hochladen, das als Hintergrundbild auf der Profilseite des Benutzers in der iOS-Unternehmensportal-App angezeigt wird. Weitere Informationen zum Konfigurieren der Unternehmensportal-App finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).  

## <a name="week-of-august-27-2018"></a>Woche vom 27. August 2018  

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Neues Update für die Benutzeroberfläche für die Unternehmensportal-Website <!--2000968 -->  
Die Unternehmensportalwebsite wurde auf der Grundlage von Kundenfeedback um neue Features ergänzt. Sie werden eine erhebliche Verbesserung der vorhandenen Funktionen und Benutzerfreundlichkeit Ihrer Geräte feststellen können. Bestimmte Bereiche der Website wie Gerätedetails, Feedback und Support sowie die Geräteübersicht wurden mit einem neuen, modernen und dynamischen Design ausgestattet. Die [Dokumentation zur Intune-Unternehmensportalwebsite](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) wurde entsprechend dieser Änderungen aktualisiert.   

Folgende Updates werden Sie bemerken:  

- optimierte Workflows auf allen Geräteplattformen
- eine verbesserte Geräteidentifikation und optimierte Registrierungsworkflows
- aussagekräftigere Fehlermeldungen
- Benutzerfreundlichere Sprache, weniger technischer Jargon
- Möglichkeit zur Freigabe direkter Links für Apps
- Verbesserte Leistung bei großen App-Katalogen
- verbesserte Barrierefreiheit für alle Benutzer  

|Aktualisiert|Zurück|
|---|---|
|![Auf der aktualisierten Geräteseite wird das Gerät auf die Geräteinformationen ausgerichtet und wird nicht mehr oberhalb der vollständigen Liste angezeigt.](./media/iwp-device-after-1803.png)|![Die Vorgängerversion der Geräteseite.](./media/iwp-device-before-1803.png)|
|![Auf der aktualisierten Seite zur App-Installation wird die App oberhalb einer Beschreibung und verschiedener Informationen zur Installation angezeigt. Dies umfasst ein Veröffentlichungsdatum, eine Version und einen App-Typ.](./media/iwp-app-install-after-1803.png)|![Die Vorgängerversion der Seite zur App-Installation.](./media/iwp-app-install-before-1803.png)|  

## <a name="week-of-july-16-2018"></a>Woche vom 16. Juli 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Weitere Synchronisierungsoptionen in der Unternehmensportal-App für Windows   
Mit der Unternehmensportal-App für Windows können Sie nun direkt über die Windows-Taskleiste und das Startmenü eine Synchronisierung starten. Dieses Feature ist besonders hilfreich, wenn Sie nur Geräte synchronisieren und auf Unternehmensressourcen zugreifen müssen. Klicken Sie mit der rechten Maustaste auf das Unternehmensportalsymbol, das an die Taskleiste oder das **Startmenü** angeheftet ist, um das neue Feature zu verwenden. Klicken Sie in den Menüoptionen (auch als Sprungliste bezeichnet) auf **Dieses Gerät synchronisieren**. Die Unternehmensportal-App wird geöffnet und zeigt die Seite **Einstellungen** an. Außerdem wird die Synchronisierung gestartet.  

![Screenshot der Windows-Taskleiste auf dem Desktop eines Geräts Es wurde auf das Symbol der Unternehmensportal-App geklickt, um ein Menü mit den Optionen „An Taskleiste anheften“, „Fenster schließen“ und „Dieses Gerät synchronisieren“ anzuzeigen.](./media/sync-device-from-start-menu-1807.png)  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Geänderte Durchsuchen-Funktion in der Unternehmensportal-App für Windows  

Beim Durchsuchen von oder Suchen nach Apps in der Unternehmensportal-App für Windows können Sie nun zwischen der Ansicht **Kacheln** und der neue Ansicht **Details** wechseln. In dieser neuen Ansicht werden Anwendungsdetails wie Name, Herausgeber, Veröffentlichungsdatum und Installationsstatus angezeigt.  

Auf der Seite **Apps** können Sie sich in der Ansicht **Installiert** Details zu abgeschlossenen und laufenden App-Installationen anzeigen lassen.  

Beispielscreenshot der Ansicht „Kacheln“:  
 
![Screenshot der Intune-Unternehmensportal-App für Windows mit den installierten Apps in der Kachelansicht](/intune/media/tiles-installed-view-cpapp-1807.png)  

Beispielscreenshot der Ansicht „Details“:  

![Screenshot der Intune-Unternehmensportal-App für Windows, die die installierten Apps in der Detailansicht anzeigt](/intune/media/details-installed-view-cpapp-1807.png) 

## <a name="week-of-april-23-2018"></a>Woche vom 23. April 2018
### <a name="updated-navigation-view-in-the-company-portal-app-for-windows-10----1195010---"></a>Aktualisierte Navigationsansicht in der Unternehmensportal-App für Windows 10 <!-- 1195010 -->
Die Intune-Unternehmensportal-App für Windows 10 wurde mit der [Navigationsansicht von Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics) aktualisiert. An der Seite der App befindet sich eine statische, vertikale Liste aller Seiten der obersten Ebene. Klicken Sie auf einen beliebigen Link, um Seiten schnell anzuzeigen und zwischen ihnen zu wechseln. Dies ist das erste von mehreren Updates, die wir Ihnen im Rahmen unserer fortlaufenden Bestrebungen präsentieren werden, die Intune-Benutzeroberfläche zu optimieren. 

![Screenshot des Unternehmensportal-App-Dashboards mit der Fluent Design-Navigationsansicht](./media/1804_WindowsCP_Fluent_01.png)


## <a name="week-of-april-2-2018"></a>Woche vom 2. April 2018

### <a name="user-experience-update-for-the-company-portal-app-for-ios----1412866---"></a>Update für die Benutzeroberfläche für die Unternehmensportal-App für iOS <!-- 1412866 -->
Für die Unternehmensportal-App für iOS wurde ein großes Update für die Benutzeroberfläche veröffentlicht. Das Update enthält eine vollständige visuelle Überarbeitung, einschließlich eines moderneren Designs und einer verbesserten Handhabung. Wir haben die Funktion der App beibehalten, haben jedoch die Benutzerfreundlichkeit und Barrierefreiheit verbessert.  

Weiterhin sind enthalten:
- Support für iPhone X
- Schnellerer App-Start und Reaktionszeiten, damit Benutzer Zeit sparen
- Zusätzliche Statusanzeigen, damit Benutzer stets mit den neuesten Statusinformationen versorgt sind
- Verbesserungen beim Uploadprozess von Protokollen. Wenn Sie also auf ein Problem stoßen, können Sie es viel einfacher melden.  

|Vorher|Danach|
|---|---|
|![01](/intune/media/cp_iosRedesign_before_1803_01.png)|![01](/intune/media/cp_iosRedesign_after_1803_01.png)|
|*Kombiniert mit vorherigen Schritten*|![02](/intune/media/cp_iosRedesign_after_1803_02.png)|
|![03](/intune/media/cp_iosRedesign_before_1803_02.png)|![03](/intune/media/cp_iosRedesign_after_1803_03.png)|

### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Sprachverbesserungen in der Unternehmensportal-App für Windows <!-- 1683758 -->
Die Sprache im Unternehmensportal für Windows 10 wurde verbessert und ist nun benutzerfreundlicher und unternehmensspezifischer.

|Vorher|Danach|
|---|---|
|![01](./media/windows_enroll_before_1803.png)|![01](./media/windows_enroll_after_1803.png)|
|![02](./media/windows_view_policy_issues_before_1803.png)|![02](./media/windows_view_policy_issues_after_1803.png)

## <a name="week-of-march-12-2018"></a>Woche vom 12. März 2018

### <a name="company-portal-for-android-visual-updates----976944---"></a>Visuelle Updates des Unternehmensportals für Android <!-- 976944 -->

Die Unternehmensportal-App wird für Android aktualisiert, um den [Material Design](https://material.io/)-Richtlinien von Android zu entsprechen.

|Vorher|Danach|
|---|---|
|![01](./media/android_about_before_1803.png)|![01](./media/androidCP_about_after_1803.png)|
|![02](./media/android_contact_it_before_1803.png)|![02](./media/android_contact_it_after_1803.png)|
|![03](./media/android_devices_before_1803.png)|![03](./media/androidCP_devicelist_after_1803.png)|
|![04](./media/android_device_details_before_1803.png)|![05](./media/androidCP_devicedetails_1_after1803.png)|
|![05](./media/android_device_details_update_settings_before_1803.png)|![05](./media/androidCP_devicedetails_red_box_2_after1803.png)|
|![06](./media/android_profile_before_1803.png)|![06](./media/android_profile_after_1803.png)|
|![07](./media/androidCP_Setup01_before_1803.png)|![07](./media/androidCP_Setup01_after_1803.png)|


## <a name="week-of-november-27-2017"></a>Woche vom 27. November 2017

### <a name="new-device-categories-step-in-guided-setup-for-the-company-portal-app-for-windows-10----1335292---"></a>Neuer Schritt „Gerätekategorien“ im geführten Setup für die Unternehmensportal-App für Windows 10 <!-- 1335292 -->

Wenn Sie [Gerätegruppenzuordnung](device-group-mapping.md) aktiviert haben, führt die Unternehmensportal-App für Windows 10 Ihre Benutzer nun durch die Auswahl einer Gerätekategorie, nachdem sie ihr Gerät registriert haben.

![Kategorie „Gerätegruppenzuordnung“](./media/w10_cp_category_device_setup_after_1711.png)

## <a name="week-of-november-13-2017"></a>Woche vom 13. November 2017

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Verbesserungen des Workflows für das Gerätesetup im Unternehmensportal für iOS in Version 2.9.0 <!-- 1417174 -->

Der Workflow für die Geräteinstallation in der Unternehmensportal-App unter iOS wurde verbessert. Die Sprache ist nun benutzerfreundlicher. Zudem haben wir Bildschirme nach Möglichkeit zusammengefasst. Zudem haben wir die Sprache speziell für Ihr Unternehmen angepasst, indem der Name Ihres Unternehmens im gesamten Setuptext verwendet wird.

> [!NOTE]
> Wir verwenden den Unternehmensnamen, den Sie im Azure-Portal unter **Microsoft Intune** > **Client-Apps** > **Branding des Unternehmensportals** > **Unternehmensname** festgelegt haben. Wenn Sie diesen Wert nicht festgelegt haben, verwenden wir den Namen des Mandanten, der unter **Azure Active Directory** > **Eigenschaften** > **Name** festgelegt wurde. Wenn Sie im Branding des Unternehmensportals keinen Unternehmensnamen festgelegt haben und nicht möchten, dass der Mandantennamen angezeigt wird, empfiehlt es sich, den Unternehmensnamen auf der Registerkarte „Branding des Unternehmensportals“ festzulegen. Wenn Sie nicht möchten, dass diese Zeichenfolge in der Kopfzeile im Unternehmensportal angezeigt wird, können Sie das Kontrollkästchen „Unternehmensnamen neben Logo anzeigen“ deaktivieren.

|Vorher|Danach|
|---|---|
|![01](./media/ios_cp_enroll_01_before_1711.png)|![01](./media/ios_cp_enroll_01_after_1711.png)|
|![02](./media/ios_cp_enroll_02_before_1711.png)|*Kombiniert mit vorherigen Schritten*|
|![03](./media/ios_cp_enroll_03_before_1711.png)|![03](./media/ios_cp_enroll_03_after_1711.png)|
|![04](./media/ios_cp_enroll_04_before_1711.png)|![04](./media/ios_cp_enroll_04_after_1711.png)|
|![05](./media/ios_cp_enroll_05_before_1711.png)|![05](./media/ios_cp_enroll_05_after_1711.png)|
|![06](./media/ios_cp_enroll_06_before_1711.png)|![06](./media/ios_cp_enroll_06_after_1711.png)|
|![07](./media/ios_cp_enroll_07_before_1711.png)|![07](./media/ios_cp_enroll_07_after_1711.png)|


## <a name="week-of-november-6-2017"></a>Woche vom 6. November 2017

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Updates an der Unternehmensportal-App für Windows 10 <!--1299474-->
Die Seite „Einstellungen“ in der Unternehmensportal-App für Windows 10 wurde aktualisiert, um die Einstellungen und beabsichtigten Benutzeraktionen für alle Einstellungen konsistenter zu gestalten. Sie wurde zudem an das Layout anderer Windows-Apps angepasst.

|Vorher|Danach|
|---|---|
|![01](./media/w10-share-logs.png)|![02](./media/w10-share-logs-after-1711.png)|


### <a name="search-improvements-to-the-company-portal-apps-and-website----1418189---"></a>Verbesserungen der Suchfunktion für Unternehmensportal-Apps und -Website <!-- 1418189 -->
Für die Apps im Unternehmensportal werden jetzt Suchläufe anhand von App-Kategorien, Namen und Beschreibungen unterstützt. Die Ergebnisse werden absteigend nach der Relevanz sortiert. Diese Updates stehen auch auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com) zur Verfügung.

Die Funktion zur Nachverfolgung der Relevanz wird weiterhin angepasst. Geben Sie uns daher gerne eine Rückmeldung über den „Feedback“-Link unten auf der Unternehmensportal-Website.

## <a name="week-of-october-16-2017"></a>Woche vom 16. Oktober 2017

### <a name="search-improvements-to-the-company-portal-website----1331697---"></a>Verbesserungen der Suchfunktion auf der Unternehmensportal-Website <!-- 1331697 -->
Die Suchfunktion unserer App soll verbessert werden. Dabei beginnen wir mit der [Unternehmensportal-Website](https://portal.manage.microsoft.com). Suchen werden nun neben den Feldern für Name und Beschreibung über App-Kategorien ausgeführt. Die Ergebnisse werden standardmäßig nach abnehmender Relevanz sortiert. 

Auch iOS-Benutzer profitieren von dieser Änderung, da die Unternehmensportal-Website auch Teil der Unternehmensportal-App unter iOS ist. In den folgenden Monaten wird es ähnliche Updates für Unternehmensportal-Apps für Android und Windows geben.

Die Funktion zur Nachverfolgung der Relevanz wird weiterhin angepasst. Geben Sie uns daher gerne eine Rückmeldung über den „Feedback“-Link unten auf der Unternehmensportal-Website.


### <a name="ios-company-portal-displays-large-icons----1454593---"></a>iOS-Unternehmensportal zeigt große Symbole an <!-- 1454593 -->
Das bekannte Problem, dass im iOS-Unternehmensportal Symbole in der App-Kachel angezeigt werden, wird mit dieser Version behoben. Wenn Sie App-Symbole mit einer Auflösung von 120 x 120 Pixel oder höher hochladen, werden sie nun auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com) und den App-Seiten des iOS-Unternehmensportals in voller Größe der App-Kachel angezeigt.


## <a name="week-of-october-2-2017"></a>Woche vom 2. Oktober 2017

### <a name="improvements-to-device-setup-workflow-in-company-portal----1490692---"></a>Verbesserungen des Workflows für das Gerätesetup im Unternehmensportal <!-- 1490692 -->
Der Workflow für die Geräteinstallation in der Unternehmensportal-App unter Android wurde verbessert. Die Sprache ist nun benutzerfreundlicher und spezifisch für Ihr Unternehmen. Zudem haben wir wo es möglich war Bildschirme vereint. 

|Vorher|Danach|
|---|---|
|![01](./media/android_cp_enroll_01_post_1709.png)|![01](./media/android_cp_enroll_01_1709_new.png)|
|![01a](./media/android_cp_enroll_01_before_1710.png)| *Kombiniert mit vorherigen Schritten* |
|![02](./media/android_cp_enroll_02_before_1710.png)|![02](./media/android_cp_enroll_02_after_1710.png)|
|![03](./media/android_cp_enroll_03_before_1710.png)|![03](./media/android_cp_enroll_03_after_1710.png)|

Zusätzliche Schritte wurden auf Android-Arbeitsprofilgeräten verbessert.

|Vorher|Danach|
|---|---|
|![04](./media/android_work_cp_enroll_01_before_1710.png)|![04](./media/android_work_cp_enroll_01_after_1710.png)|
|![05](./media/android_work_cp_enroll_02_before_1710.png)| *Kombiniert mit vorherigen Schritten* |
|![06](./media/android_work_cp_enroll_03_before_1710.png)|![06](./media/android_work_cp_enroll_03_after_1710.png)|
|![07](./media/android_work_cp_enroll_04_before_1710.png)|![07](./media/android_work_cp_enroll_04_after_1710.png)|
|![08](./media/android_work_cp_enroll_05_before_1710.png)| *Kombiniert mit vorherigen Schritten* |


Außerdem wurde der Aktivierungsbildschirm für bedingten Zugriff auf E-Mails aktualisiert.

|Vorher|Danach|
|---|---|
|![06](./media/android_conditional_access_email_before_1710.png)|![06](./media/android_conditional_access_email_after_1710.png)

## <a name="week-of-september-11-2017"></a>Die Woche vom 11. September 2017

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Vereinfachung der Formulierung für die Unternehmensportal-App für Android <!-- 1396349 -->  

Der Registrierungsvorgang für die Unternehmensportal-App für Android wurde durch einen neuen Text vereinfacht, um Endbenutzern eine einfachere Registrierung zu bieten. Wenn Sie über eine benutzerdefinierte Registrierungsdokumentation verfügen, sollten Sie diese aktualisieren, damit diese die neuesten Bildschirme anzeigt. Unten finden Sie Abbildungen von Beispielen:

|Vorher|Danach|
|---|---|
|![01](./media/android_cp_enroll_01_before_1709.png)|![01](./media/android_cp_enroll_01_post_1709.png)|
|![02](./media/android_cp_enroll_02_before_1709.png)|![02](./media/android_cp_enroll_02_post_1709.png)|
|![03](./media/android_cp_enroll_03_before_1709.png)|![03](./media/android_cp_enroll_03_post_1709.png)|
|![04](./media/android_cp_enroll_04_before_1709.png)|![04](./media/android_cp_enroll_04_post_1709.png)|
|![05](./media/android_cp_enroll_05_before_1709.png)|![05](./media/android_cp_enroll_05_post_1709.png)|


## <a name="august-2017"></a>August 2017

### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11-Mail-App unterstützt nun OAuth <!-- 1196951 -->

Der bedingte Zugriff über Intune unterstützt nun eine sicherere Authentifizierung auf iOS-Geräten mit OAuth. Der Ablauf der Unternehmensportal-App für iOS hat sich geändert, um dies zu unterstützen und eine sicherere Authentifizierung zu ermöglichen. Wenn Endbenutzer versuchen, sich mit einem neuen Exchange-Konto in der Mail-App anzumelden, wird ihnen eine Aufforderung in der Webansicht angezeigt. Bei der Registrierung in Intune werden Benutzer dazu aufgefordert, der nativen Mail-App den Zugriff auf ein Zertifikat zu gewähren. Den meisten Benutzern werden isolierte E-Mails nicht mehr angezeigt. Bestehende E-Mail-Konten werden weiterhin das Standardauthentifizierungsprotokoll verwenden. Diesen Benutzern werden also immer noch isolierte E-Mails zugestellt. Die Anmeldung für Endbenutzer ähnelt der Anmeldung bei mobilen Office-Apps.

![Auswählen des Kontotyps in der nativen Mail-App.](./media/ios-11-ca-email-after-1708-01.png)

![Nachdem Sie Exchange ausgewählt haben, werden Sie aufgefordert, die E-Mail-Adresse und den Kontonamen auf Ihrem iOS-Gerät einzugeben.](./media/ios-11-ca-email-after-1708-02.png)

![Geben Sie die E-Mail-Adresse und einen Namen für das Konto ein.](./media/ios-11-ca-email-after-1708-03.png)

![Weiterleitung auf die externe Microsoft-Anmeldeseite.](./media/ios-11-ca-email-after-1708-04.png)

![Angeben des Kennworts auf der Microsoft-Seite.](./media/ios-11-ca-email-after-1708-05.png)

![Microsoft fordert den Benutzer dazu auf, das Gerät für die Verwaltung zu registrieren.](./media/ios-11-ca-email-after-1708-06.png)

![Der Benutzer wird aufgefordert, die Registrierung über die Website des Unternehmensportals vorzunehmen.](./media/ios-11-ca-email-after-1708-07.png)



### <a name="intune-mobile-application-management-mam-dialog-boxes-will-have-a-modern-interface----1199015---"></a>Dialogfelder der mobilen Anwendungsverwaltung mit Intune erhalten eine moderne Schnittstelle <!-- 1199015 -->

Die Dialogfelder der mobilen Anwendungsverwaltung mit Intune (MAM) werden moderner aussehen und sich verhalten. Die Dialogfelder funktionieren wie zuvor.

**Bisherige Benutzeroberfläche**

![alte Schnittstelle](./media/NewUI_Old_AttachFileHandler.jpg)

**Moderne Benutzeroberfläche**

![moderne Schnittstelle](./media/NewUI_Modern_AttachFileHandler.jpg)


### <a name="updates-to-the-device-details-page-on-the-company-portal-app-for-windows-10----1287448---"></a>Updates für die Seite „Gerätedetails“ der Unternehmensportal-App für Windows 10 <!-- 1287448 -->

Das Tag __Kategorie__ wird in der Unternehmensportal-App für Windows 10 von dem Platz unter dem Titel zu einer Eigenschaft auf der Seite __Gerätedetails__ verschoben.

![Der Windows-Bildschirm „Gerätedetails“ in der Unternehmensportal-App, auf dem das Feld „Kategorien“ als Eigenschaft und nicht direkt unter dem Titel des Bildschirms angezeigt wird](./media/cp_win10_category_tag_move_after_1708.png)

## <a name="july-2017"></a>Juli 2017

### <a name="apps-details-pages-will-display-new-information-for-android-devices---1287476--"></a>Detailseiten von Apps zeigen neue Informationen für Android-Geräte an <!--1287476-->

Die Detailseite der Unternehmensportal-App für Android zeigt nun die App-Kategorien an, die der IT-Administrator für diese App definiert hat.

![Die neue Detailseite der App](./media/cp_android_appdetails_after_1708.png)

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Verbesserte Anmeldefunktion für alle Unternehmensportal-Apps auf allen Plattformen <!--User Story 1132123-->

Wir kündigen eine in den nächsten Monaten kommende Änderung an, durch die der Anmeldevorgang für die Intune-Unternehmensportal-Apps für Android, iOS und Windows verbessert wird. Die neue Benutzeroberfläche wird für die Unternehmensportal-App automatisch auf allen Plattformen eingeführt, sobald Azure AD die Änderung umsetzt. Darüber hinaus können Benutzer sich jetzt mithilfe eines generierten Codes zur einmaligen Verwendung von einem anderen Gerät aus beim Unternehmensportal anmelden. Dies ist besonders nützlich, wenn Benutzer sich ohne Anmeldeinformationen anmelden müssen.  

Unten sehen Sie die vorherige Anmeldeoberfläche, die neue Anmeldeoberfläche mit Anmeldeinformationen und die neue Anmeldeoberfläche zur Anmeldung von einem anderen Gerät aus.

__Vorherige Anmeldeoberfläche__

![Die Seite für die Anmeldung beim Unternehmensportal mit einem Symbol für eine Person vor der grafischen Darstellung einer Website. Die Schaltfläche zum Anmelden befindet sich darunter. Ein Link am unteren Seitenrand führt zu Informationen von Microsoft zu Datenschutz und Cookies.](./media/cp_ios_aad_signin_before_1704_001.png)

![Nach dem Tippen auf „Anmelden“ geben Benutzer auf dieser Seite ihre Anmeldeinformationen ein. Die Seite erfordert die Eingabe von E-Mail-Adresse und Kennwort und bietet Möglichkeiten, Kennwortfehler zu beheben.](./media/cp_ios_aad_signin_before_1704_002.png)

![Nach Eingabe des Kennworts meldet sich die Unternehmensportal-App an und zeigt einen Ladebalken an.](./media/cp_ios_aad_signin_before_1704_003.png)

__Neue Anmeldeoberfläche__

![Die Seite für die Anmeldung beim Unternehmensportal mit einem Symbol für eine Person vor der grafischen Darstellung einer Website. Darunter befindet sich die Schaltfläche zum Anmelden. Ein Link am unteren Seitenrand führt zu Informationen von Microsoft zu Datenschutz und Cookies.](./media/cp_ios_aad_signin_after_1704_001.png)

![Der Benutzer wird nur zur Eingabe der E-Mail-Adresse aufgefordert, nicht zur Eingabe von E-Mail-Adresse und Kennwort im gleichen Bildschirm.](./media/cp_ios_aad_signin_after_1704_002.png)

![Der Benutzer wird erst zur Eingabe des Kennworts aufgefordert, wenn die E-Mail-Adresse akzeptiert wurde.](./media/cp_ios_aad_signin_after_1704_003.png)

![Nach Abschluss des Authentifizierungsprozesses meldet sich die Unternehmensportal-App an und zeigt einen entsprechenden Ladebalken an.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Neue Anmeldeoberfläche bei Anmeldung von einem anderen Gerät aus__

![Die Seite für die Anmeldung beim Unternehmensportal mit einem Symbol für eine Person vor der grafischen Darstellung einer Website. Darunter befindet sich die Schaltfläche zum Anmelden. Ein Link am unteren Seitenrand führt zu Informationen von Microsoft zu Datenschutz und Cookies.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Tippen Sie auf den Link __Sign-in from another device__ (Von einem anderem Gerät aus anmelden).

![Der Benutzer erhält die Anweisung, mit einem über den Arbeitscomputer bezogenen eindeutigen Passcode zur Seite „aka.ms/devicelogin“ zu wechseln und sich dort mit dem Code anzumelden.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Starten Sie einen Browser, und gehen Sie zu [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Ein Bild des Browsers des Benutzers auf dem Arbeitscomputer statt in der Unternehmensportal-App. Die angezeigte Seite „Geräteanmeldung“ fordert den Benutzer auf, den über die Unternehmensportal-App empfangenen Code einzugeben.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Geben Sie den Code ein, den Sie in der Unternehmensportal-App erhalten haben. Wenn Sie __Weiter__ auswählen, können Sie sich mit jeder von Ihrem Unternehmen unterstützten Methode authentifizieren, z.B. per Smartcard.

![Der Benutzer hat den eindeutigen Code in das Feld eingegeben und wurde auf der Seite „Geräteanmeldung“ aufgefordert, zu bestätigen, dass das Intune-Unternehmensportal die App ist, die zur Anmeldung autorisiert werden soll.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Eine Bestätigungsseite informiert darüber, dass der Benutzer sich jetzt auf dem Gerät bei der Unternehmensportal-App angemeldet hat und dass diese Seite geschlossen werden kann.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

Die Unternehmensportal-App beginnt mit der Anmeldung.

![Nach Abschluss des Authentifizierungsprozesses meldet sich die Unternehmensportal-App an und zeigt einen entsprechenden Ladebalken an.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="june-2017"></a>Juni 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies"></a>Die Unternehmensportal-App für Android verfügt nun über eine neue Benutzeroberfläche für App-Schutzrichtlinien
Auf Grundlage von Benutzerfeedback haben wir die Unternehmensportal-App für Android modifiziert, sodass sie nun die Schaltfläche **Auf Unternehmensinhalte zugreifen** besitzt. Der Hintergrund dazu ist, Endbenutzer daran zu hindern, unnötigerweise den Registrierungsprozess zu durchlaufen, wenn sie nur auf Apps zugreifen müssen, die App-Schutzrichtlinien unterstützen, eine Funktion der mobilen Anwendungsverwaltung von Intune.

Der Benutzer muss dann einfach nur auf die Schaltfläche **Auf Unternehmensinhalte zugreifen** tippen, statt mit der Registrierung des Geräts zu beginnen.

![Ein Bild der Unternehmensportal-App von Android, auf dem man in der Mitte groß „Auf Unternehmensinhalte zugreifen“ lesen kann, statt direkt Registrierungsoptionen wie im Normalfall zu sehen.](./media/and_access_company_content_after_1706.png)

Dann wird der Benutzer auf die Website des Unternehmensportals weitergeleitet, um den Gebrauch der App auf seinem Gerät zu autorisieren. Die Website des Unternehmensportals überprüft dann seine Anmeldeinformationen.

![Ein Bild der Unternehmensportalwebsite mit Bestätigung der erfolgreichen Anmeldung.](./media/and_iwp_sign_in_auth_page_after_1706.png)

Das Gerät kann immer noch für die vollständige Verwaltung registriert werden. Klicken Sie dazu auf das Menü **Aktion**.

![Ein Bild der Unternehmensportal-App für Android mit dem Menü in der rechten oberen Ecke des Bildschirms mit der Option, ein Gerät zu registrieren.](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Verbesserungen bei der App-Synchronisierung mit dem Windows 10 Creators Update <!--676505-->

Die Unternehmensportal-App für Windows 10 löst nun automatisch eine Synchronisierung für App-Installationsanforderungen für Geräte mit dem Windows 10 Creators Update (Version 1703) aus. Dadurch wird das Problem beseitigt, dass App-Installationen während des Zustands „Synchronisierung ausstehend“ verzögert reagieren. Darüber hinaus können Benutzer die Synchronisierung innerhalb der App manuell initiieren.

![Ein Bild der Unternehmensportal-App für Windows 10, wobei sich der Download von Microsoft Word aus dem App-Store des Unternehmensportals im ausstehenden Status befindet.](./media/w10_download_pending_after_1706.png)

![Ein Bild der Intune-Unternehmensportal-App für Windows 10 mit dem neuen automatischen Synchronisierungsstatus mit einer Meldung, die angibt, dass das Gerät synchronisiert und der Download der App versucht wird.](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Neues benutzerfreundlicheres Windows 10-Unternehmensportal <!---1058938--->
Die Unternehmensportal-App für Windows 10 bietet eine geführte Intune-Anleitung für Geräte, die nicht identifiziert oder registriert wurden. Die neue Anleitung umfasst Schritt-für-Schritt-Anweisungen, mit denen die Registrierung bei Azure Active Directory (erforderlich für Funktionen zum bedingten Zugriff) und die MDM-Registrierung (erforderlich für Funktionen zur Geräteverwaltung) durch den Benutzer erläutert werden. Auf die geführte Anleitung kann über die Hauptseite des Unternehmensportals zugegriffen werden. Benutzer können die App weiter verwenden, auch wenn sie die Registrierung nicht abgeschlossen haben, erhalten aber eingeschränkte Funktionalität.

Dieses Update ist nur auf Geräten unter Windows 10 Anniversary Update (Build 1607) oder höher sichtbar.

![Ein Bild der Startbildschirms der Unternehmensportal-App von Windows 10 mit einer Statusmeldung in der Mitte in der Liste „Geräte“, die einen Benutzer darüber informiert, dass sein Gerät noch nicht für den Einsatz im Unternehmen eingerichtet wurde, und dass der Benutzer die Meldung auswählen kann, um mit dem Einrichten zu beginnen.](./media/win10_guided_enroll_select_setup_after_1706.png)

![Ein Bild der Einrichtungsseite der Unternehmensportal-App von Windows 10 mit einer Warnung, dass ein Benutzer ein Unternehmenskonto auf seinem Gerät hinzufügen muss, um sich für die Verwaltung zu registrieren.](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![Ein Bild des Bildschirms „Unternehmenskonto auf diesem Gerät hinzufügen“ der Unternehmensportal-App für Windows 10 mit der Meldung an den Benutzer, dass er zum Abschließen der Registrierung in der App „Einstellungen“ die Option „Verbinden“ auswählen muss. Nachdem sie dies gemacht haben, werden sie auf dem Bildschirm informiert, dass sie zum Abschließen der Registrierung zur Unternehmensportal-App zurückkehren müssen.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Ein Bild des Bildschirms „Für die Verwaltung registrieren“ der Unternehmensportal-App für Windows 10 mit der Meldung zum abgeschlossenen Status, dass das Gerät des Benutzers jetzt registriert ist und dass Sie auf die Schaltfläche „Weiter“ klicken müssen, um fortzufahren.](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![Ein Bild des Bildschirms „Abgeschlossen“ der Unternehmensportal-App für Windows 10, die den Benutzer darüber informiert, dass die Einrichtung abgeschlossen ist und dass das Gerät mit einem Unternehmenskonto registriert wurde.](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Neue Menüaktion zum mühelosen Entfernen des Unternehmensportals <!--1164569-->
Basierend auf Benutzerfeedback wurde der Unternehmensportal-App für Android eine neue Menüaktion hinzugefügt, über die das Entfernen des Unternehmensportals von Ihrem Gerät eingeleitet werden kann. Über diese Aktion wird das Gerät aus der Intune-Verwaltung entfernt, damit die App vom Benutzer vom Gerät entfernt werden kann.

![Ein Bild der Android-Unternehmensportal-App mit geöffnetem Aktionsmenü oben rechts. Die neue Option „Unternehmensportal entfernen“ steht als die dritte Option unter „Mein Profil“ und „Einstellungen“ und über „Nutzungsbedingungen“, „Hilfe und Feedback“ und „Info“ zur Verfügung.](./media/android_remove_cp_menu_action_after_1705.png)

![Ein Bild mit dem Bestätigungsdialogfeld, das nach der Auswahl der neuen Option „Unternehmensportal entfernen“ im Aktionsmenü verfügbar ist. Das Dialogfeld informiert den Benutzer über Folgendes: „Wenn Sie das Unternehmensportal entfernen, wird Ihr Gerät nicht länger durch Ihren IT-Administrator verwaltet, und der Zugriff auf Unternehmensdaten, Unternehmens-Apps und Unternehmens-E-Mails wird möglicherweise beendet.“ Anschließend muss der Benutzer bestätigen, dass er die Unternehmensportal-App entfernen möchte, indem er „Ja“ auswählt.](./media/android_remove_cp_menu_confirmation_after_1705.png)

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios---1230777--"></a>Verbesserungen an den App-Kacheln in der Unternehmensportal-App für iOS <!--1230777-->
Wir haben das Design der App-Kacheln auf der Startseite entsprechend der Brandingfarbe geändert, die Sie für das Unternehmensportal festgelegt haben.

**Vorher**

![Abbildung der Unternehmensportal-App für iOS vor dem Update mit vordefinierten Füllungsbildern für „Alle Apps“, „Ausgewählte Apps“ und „Kategorien“.](./media/cp_ios_homepage_before_1705.png)

**Nachher**

![Bild der Unternehmensportal-App für iOS nach dem Update, das nun die Möglichkeit zum Auswählen der Farben wiedergibt, die für Ihre Organisation relevant sind.](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Kontoauswahl nun für die Unternehmensportal-App für iOS verfügbar
Wenn Benutzer auf ihrem iOS-Gerät Ihr Geschäfts, Schul- oder Unikonto zum Anmelden bei anderen Microsoft-Apps verwendet haben, wird ihnen nun ggf. unsere neue Kontoauswahl angezeigt, sobald sie sich zum ersten Mal beim Unternehmensportal anmelden.

![Bild der Kontoauswahl, das zeigt, wie der Testbenutzer „Robin Swanson“ zwischen seinen beiden E-Mail-Adressen eine Wahl trifft. Unter den beiden Adressen gibt es eine Schaltfläche, die dem Benutzer das Anmelden mit einem anderen Konto erlaubt.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>April 2017

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Neue Symbole für Managed Browser und das Unternehmensportal <!--918433, 918431-->

Managed Browser erhält aktualisierte Symbole für die Android- und iOS-Versionen der App. Das neue Symbol enthält den aktualisierten Intune-Badge, damit es konsistenter mit anderen Apps in Enterprise Mobility + Security (EM+S) wird.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width="200" height="366" align="center">
           </td>
      </tr>
   </table>
</body>
</html>

Das Unternehmensportal erhält auch aktualisierte Symbole für die Android-, iOS- und Windows-Versionen der App, um die Konsistenz mit anderen Apps in EM+S zu verbessern. Diese Symbole werden von April bis Ende Mai schrittweise auf den Plattformen veröffentlicht.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Statusanzeige zur Anmeldung im Android-Unternehmensportal <!--953374-->

Ein Update auf die Android-Unternehmensportal-App zeigt eine Statusanzeige der Anmeldung an, wenn der Benutzer die App startet oder fortsetzt. Die Statusanzeige durchläuft die neuen Phasen, beginnend mit „Verbindung wird aufgebaut“, „Anmeldung“ und dann „Suchen nach Sicherheitsanforderungen“, bevor dem Benutzer der Zugriff auf die App gewährt wird.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width="200" height="366" align="center">
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width="200" height="366" align="center">
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Verbesserter App-Installationsstatus für die Windows 10-Unternehmensportal-App <!--676495-->
Die Windows 10-Unternehmensportal-App bietet jetzt auf der Seite mit den App-Details eine Installationsstatusanzeige. Diese wird für moderne Apps auf Geräten mit Windows 10 Anniversary Update und höher unterstützt.

__Vorher__ ![Eine Abbildung der vorherigen Version des Ladebildschirms, auf dem der Status schlicht „Wird installiert“ lautet.](./media/cp_win10_install_status_before_1704.png)

__Nachher__ ![Eine Abbildung der aktualisierten Version des Ladebildschirms, der nun eine Statusanzeige für die Installation zeigt.](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>Februar 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Neue Benutzeroberfläche für die Unternehmensportal-App für Android <!--621622, announced 1702-->
Ab März befolgt die Unternehmensportal-App für Android die [material design guidelines (Richtlinien für Materialdesign)](https://material.io/guidelines/material-design/introduction.html), um ein moderneres Erscheinungsbild zu vermitteln. Diese verbesserte Benutzeroberfläche enthält Folgendes:

* __Farben__: Die Farben der Registerkartentitel können mithilfe Ihrer benutzerdefinierten Farbpalette angepasst werden.

![Auf der linken Seite sehen Sie ein Bild der Unternehmensportal-App für Android vor der Aktualisierung. Auf der rechten Seite sehen Sie ein Bild der Unternehmensportal-App für Android nach der Aktualisierung. Beide Bilder zeigen als ausgewählte Registerkarte die Registerkarte „Geräte“ aus den drei Registerkarten „Apps“, „Geräte“ und „An IT-Abteilung wenden“.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Schnittstelle__: Auf der Registerkarte __Apps__ wurden die Schaltflächen __Empfohlene Apps__ und __Alle Apps__ aktualisiert. Die Schaltfläche __Suche__ ist nun eine unverankerte interaktive Schaltfläche.

![Auf der linken Seite sehen Sie ein Bild der Unternehmensportal-App für Android vor der Aktualisierung. Auf der rechten Seite sehen Sie ein Bild der Unternehmensportal-App für Android nach der Aktualisierung. Beide Bilder zeigen als ausgewählte Registerkarte die Registerkarte „Apps“ aus den drei Registerkarten „Apps“, „Geräte“ und „An IT-Abteilung wenden“.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navigation__: Alle Apps zeigen die Registerkartenansicht __Empfohlen__, __Alle__ und __Kategorien__ für eine einfachere Navigation an. __An IT-Abteilung wenden__ wurde zur besseren Lesbarkeit optimiert.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width="200" height="366" align="center">
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Januar 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Modernisieren der Unternehmensportal-Website <!--753980, announced 1701-->
Ab Februar unterstützt die Unternehmensportal-Website Apps, die für Benutzer bestimmt sind, die über keine verwalteten Geräte verfügen. Die Website wird an andere Microsoft-Produkte und -Dienste mithilfe eines neuen Farbschemas, dynamischen Illustrationen und einem „Hamburger-Menü“ ausgerichtet, ![Miniaturansicht des Hamburger-Menüs, das nun in der linken oberen Ecke der Unternehmensportal-App zu sehen ist,](./media/CP_hamburger_menu.png) das nun Helpdesk-Kontaktdetails enthält sowie Informationen zu vorhandenen verwalteten Diensten. Die Angebotsseite wird neu angeordnet, um Apps hervorzuheben, die für Benutzer verfügbar sind, und mit einer Karussellsicht für empfohlene und kürzlich aktualisierte Apps.

![Auf der linken Seite sehen Sie ein Bild der aktuellen Version der Unternehmensportal-Website mit den derzeitigen Versionen von Apps, Meine Geräte sowie den Ansichten „Featured“ (Highlights) und „Kategorien“. Auf der rechten Seite sehen Sie ein Bild der neuen Version der Unternehmensportal-Website mit einem aktualisierten App-Karussell, einer Liste mit kürzlich veröffentlichten Apps und einer aktualisierten Ansicht „Kategorien“.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>In Kürze auf der Benutzeroberfläche verfügbar
Es folgen die Pläne für Möglichkeiten zum Verbessern der Benutzererfahrung durch Ändern unserer Benutzeroberfläche.

> [!Note]
> Bei den Abbildungen unten kann es sich um eine Vorschau handeln, und das angekündigte Produkt kann sich von den abgebildeten Versionen unterscheiden.  


## <a name="see-also"></a>Siehe auch
* [Microsoft Intune-Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roadmap für die Cloudplattform](https://www.microsoft.com/cloud-platform/roadmap)
* [Neuerungen in Intune](https://docs.microsoft.com/intune/whats-new)
