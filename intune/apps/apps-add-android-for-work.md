---
title: Zuweisen verwalteter Google Play-Apps zu Android Enterprise-Geräten
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie über den verwalteten Google Play Store Apps zu Android Enterprise-Geräten zuweisen und synchronisieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc777cc6d8b803c502d847114ef7cff04ceb26
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725334"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Hinzufügen verwalteter Google Play-Apps zu Android Enterprise-Geräten mit Intune

Verwaltetes Google Play ist der Enterprise App Store von Google und die einzige Quelle von Anwendungen für Android Enterprise. Mit Intune können Sie die App-Bereitstellung über verwaltetes Google Play für jedes Android Enterprise-Szenario (einschließlich Arbeitsprofil, dedizierte und vollständig verwaltete Anmeldungen) orchestrieren. Das Hinzufügen von verwalteten Google Play-Apps zu Intune unterscheidet sich vom Hinzufügen von Android-Apps zu Nicht-Android Enterprise-Geräten. Store-, branchenspezifische und Web-Apps werden in verwaltetem Google Play genehmigt oder hinzugefügt und dann so mit Intune synchronisiert, dass sie in der Liste „Client-Apps“ angezeigt werden. Sobald sie in der Liste „Client-Apps“ aufgeführt sind, können Sie die Zuweisung einer verwalteten Google Play-App wie bei jeder anderen App verwalten.

Intune fügt bei der Verbindung Ihres Intune-Mandanten mit verwaltetem Google Play automatisch vier gängige auf Android Enterprise bezogene Apps zur Intune-Verwaltungskonsole hinzu, um Ihnen die Konfiguration und Nutzung der Android Enterprise-Verwaltung zu erleichtern. Es handelt sich um diese vier Apps:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : für vollständig verwaltete Android Enterprise-Szenarien. Diese App wird während des Geräteregistrierungsprozesses automatisch auf vollständig verwalteten Geräten installiert.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : hilft bei der Anmeldung bei Ihren Konten, wenn Sie die zweistufige Überprüfung verwenden. Diese App wird während des Geräteregistrierungsprozesses automatisch auf vollständig verwalteten Geräten installiert.
- **[Intune-Unternehmensportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : wird für App Protection Policies (APP) und Szenarien mit Android Enterprise-Arbeitsprofilen genutzt.
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** : wird für dedizierte/Kioskszenarien mit Android Enterprise verwendet. IT-Administratoren sollten eine Zuweisung erstellen, um diese App auf dedizierten Geräten zu installieren, die in Kioskszenarien mit mehreren Apps verwendet werden sollen.

>[!NOTE]
>Wenn ein Endbenutzer sein von Android Enterprise vollständig verwaltetes Gerät registriert, wird die App „Intune-Unternehmensportal“ automatisch installiert, woraufhin das Anwendungssymbol dem Endbenutzer möglicherweise angezeigt wird. Wenn der Endbenutzer versucht, die App „Intune-Unternehmensportal“ zu starten, wird der Endbenutzer zur App „Microsoft Intune“ umgeleitet, woraufhin das Symbol der Unternehmensportal-App ausgeblendet wird.

## <a name="before-you-start"></a>Vorbereitung
- Vergewissern Sie sich, dass Sie Ihren Intune-Mandanten mit verwaltetem Google Play verbunden haben.  Weitere Informationen finden Sie unter [Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto](../enrollment/connect-intune-android-enterprise.md).
- Wenn Sie vorhaben, Arbeitsprofilgeräte zu registrieren, stellen Sie sicher, dass Sie Intune und Android-Arbeitsprofile im Azure-Portal für die Workload **Geräteregistrierung** so konfiguriert haben, dass beide zusammenarbeiten. Weitere Informationen finden Sie unter [Registrieren von Android-Geräten](../enrollment/android-work-profile-enroll.md).

>[!NOTE]
>Für die Arbeit mit Microsoft Intune wird als Browser Microsoft Edge oder Google Chrome empfohlen.

## <a name="managed-google-play-app-types"></a>Typen verwalteter Google Play-Apps
Es gibt drei Arten von Apps, die mit verwaltetem Google Play verfügbar sind:

* **Verwaltete Google Play Store-App**: öffentliche Apps, die im Play Store allgemein verfügbar sind. Verwalten Sie diese Apps in Intune, indem Sie nach den Apps suchen, die Sie verwalten möchten, sie genehmigen und sie dann mit Intune synchronisieren.
* **Verwaltete private Google Play-App**: Hierbei handelt es sich um branchenspezifische Apps, die von Intune-Administratoren in verwaltetem Google Play veröffentlicht werden.  Diese Apps sind privat und nur für Ihren Intune-Mandanten verfügbar. Auf diese Weise werden branchenspezifische Apps mit verwaltetem Google Play und Android Enterprise verwaltet und bereitgestellt.
* **Weblinks zu verwaltetem Google Play**: Weblinks mit von IT-Administratoren definierten Symbolen, die auf Android Enterprise-Geräten bereitgestellt werden können. Diese werden auf einem Gerät wie normale Apps in dessen App-Liste angezeigt.

## <a name="managed-google-play-store-apps"></a>Apps im verwalteten Google Play Store
Es gibt zwei Möglichkeiten zum Suchen und Genehmigen verwalteter Google Play Store-Apps mit Intune:

1. Direkt in der Intune-Konsole: Suchen und genehmigen Sie Store-Apps in einer in Intune gehosteten Ansicht. Dieser Vorgang wird direkt in der Intune-Konsole geöffnet, sodass Sie sich nicht mit einem anderen Konto erneut authentifizieren müssen.
1. In der Konsole von verwaltetem Google Play: Sie können optional die Konsole von verwaltetem Google Play direkt öffnen und Apps dort genehmigen. Weitere Informationen finden Sie unter [Synchronisieren einer App aus dem verwalteten Google Play Store mit Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).  Dazu ist eine separate Anmeldung über das Konto erforderlich, mit dem Sie Ihren Intune-Mandanten mit verwaltetem Google Play verbunden haben.


### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Hinzufügen einer verwalteten Google Play Store-App direkt in der Intune-Konsole

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im **Intune**-Bereich die Option **Client-Apps** > **Apps** aus.
5. Klicken Sie im Bereich **Apps** auf **Hinzufügen**.
6. Wählen Sie in der Dropdownliste **App-Typ** **Verwaltetes Google Play** aus.
7. Wählen Sie **Verwaltetes Google Play -> Öffnen** aus, um den Katalog für verwaltetes Google Play zu öffnen.
7. Wählen Sie im Google Play-Katalog **Play Store durchsuchen** aus.
8. Verwenden Sie das Suchfeld, um nach Apps zu suchen, die Sie verwalten möchten.
9. Klicken Sie auf **Genehmigen**, um die App in verwaltetem Google Play zu genehmigen, und klicken Sie auf **Genehmigen**, um die App-Berechtigungen anzunehmen.
10. Wählen Sie **Genehmigt lassen, wenn Apps neue Berechtigungen anfordern** im Fenster „Genehmigungseinstellungen“ aus, und klicken Sie dann auf **Speichern**. Wenn Sie diese Option nicht auswählen, müssen Sie alle neuen Berechtigungen manuell genehmigen, wenn der App-Entwickler ein Update veröffentlicht. Dadurch werden Installationen und Updates für die App unterbrochen, bis die Berechtigungen genehmigt wurden. Aus diesem Grund wird empfohlen, die Option zum automatischen Genehmigen neuer Berechtigungen auszuwählen. 
11. Klicken Sie auf **OK**, um die App(s) einzuschließen, die Sie genehmigt haben.
12. Klicken Sie im Bereich **App** auf **Synchronisieren**, um eine Synchronisierung mit dem verwalteten Google Play-Dienst durchzuführen.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Hinzufügen einer verwalteten Google Play Store-App in der Konsole von verwaltetem Google Play (Alternative)
Wenn Sie es vorziehen, eine verwaltete Google Play-App mit Intune zu synchronisieren, anstatt sie direkt mit Intune hinzuzufügen, gehen Sie wie folgt vor.

> [!IMPORTANT]
> Die folgenden Informationen sind eine alternative Methode, um eine verwaltete Google Play-App mit Intune wie oben beschrieben hinzuzufügen.

1. Besuchen Sie den [Managed Google Play Store](https://play.google.com/work). Melden Sie sich mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android Enterprise verwendet haben.
2. Suchen Sie im Store nach der App, die Sie mithilfe von Intune zuweisen möchten, und wählen Sie die App aus.
3. Wählen Sie auf der Seite, die die App anzeigt, **Genehmigen** aus.  
    Im folgenden Beispiel wurde die Microsoft Excel-App ausgewählt.

    ![Die Schaltfläche „Genehmigen“ im Managed Google Play-Store](./media/apps-add-android-for-work/approve.png)

   Ein Fenster für die App wird geöffnet, und Sie werden gebeten, der App Berechtigungen zum Durchführen verschiedener Vorgänge zu erteilen.

4. Klicken Sie auf **Genehmigen**, um die App-Berechtigungen zu akzeptieren und fortzufahren.

    ![Die Schaltfläche „Genehmigen“ für App-Berechtigungen](./media/apps-add-android-for-work/approve-app-permissions.png)

5. Wählen Sie eine Option für die Behandlung neuer App-Berechtigungsanforderungen und dann **Speichern** aus.

    ![Optionen für die Behandlung neuer App-Berechtigungsanforderungen](./media/apps-add-android-for-work/approve-app-settings.png)

    Die App wird genehmigt und in Ihrer IT-Verwaltungskonsole angezeigt. Als Nächstes können Sie [die Android-Arbeitsprofil-App mit Intune synchronisieren](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).

## <a name="managed-google-play-private-lob-apps"></a>Private (branchenspezifische) verwaltete Google Play-Apps

Es gibt zwei Möglichkeiten, verwaltetem Google Play branchenspezifische Apps hinzuzufügen:

1. Direkt in der Intune-Konsole: Direkt in der Intune-Konsole: Dies ermöglicht Ihnen das Hinzufügen branchenspezifischer Apps direkt in Intune, indem Sie nur das APK der App und einen Titel übermitteln. Diese Methode erfordert weder ein Google-Entwicklerkonto noch die Zahlung der Gebühr zur Registrierung bei Google als Entwickler.  Diese Methode ist einfacher, weist deutlich weniger Schritte auf und macht branchenspezifische Apps in nur zehn Minuten für die Verwaltung verfügbar.
1. In der Google Play Developer Console: Wenn Sie ein Google-Entwicklerkonto haben oder erweiterte Verteilungsfunktionen konfigurieren möchten, die nur in der Google Play Developer Console verfügbar sind (z.B. das Hinzufügen zusätzlicher App-Screenshots), können Sie die [Google Play Developer Console](https://play.google.com/apps/publish) verwenden. 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Veröffentlichen privater branchenspezifischer verwalteter Google Play-Apps direkt in der Intune-Konsole

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im **Intune**-Bereich die Option **Client-Apps** > **Apps** aus.
5. Klicken Sie im Bereich **Apps** auf **Hinzufügen**.
6. Wählen Sie in der Dropdownliste **App-Typ** **Verwaltetes Google Play** aus.
7. Wählen Sie **Verwaltetes Google Play -> Öffnen** aus, um den Katalog für verwaltetes Google Play zu öffnen.
7. Wählen Sie im Google Play-Katalog **Private Apps** aus.
7. Klicken Sie auf die Schaltfläche **+** , um eine neue App hinzuzufügen.
8. Übermitteln eines App-Titels und eines APK-Pakets für die App
9. Klicken Sie auf **Erstellen**.
9. Schließen Sie den Bereich „Verwaltetes Google Play“, wenn das Hinzufügen von Apps abgeschlossen ist.
12. Klicken Sie im Bereich **App** auf **Synchronisieren**, um eine Synchronisierung mit dem verwalteten Google Play-Dienst durchzuführen. Beachten Sie, dass es mehrere Minuten dauern kann, bis private Apps zur Synchronisierung verfügbar sind. Wenn die App bei der ersten Synchronisierung nicht angezeigt wird, warten Sie ein paar Minuten und starten dann eine neue Synchronisierung.

Weitere Informationen zu privaten verwalteten Google Play-Apps sowie häufig gestellte Fragen finden Sie im Google-Supportartikel: https://support.google.com/googleplay/work/answer/9146439

>[!NOTE]
>Mit dieser Methode hinzugefügte private Apps können nicht öffentlich gemacht werden. Wählen Sie diese Veröffentlichungsoption nur, wenn Sie sicher sind, dass diese App für Ihre Organisation stets privat bleiben wird.
  

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Veröffentlichen privater branchenspezifischer verwalteter Google Play-Apps mithilfe der Google Developer Console

1. Melden Sie sich bei der [Google Play Developer Console](https://play.google.com/apps/publish) mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android Enterprise verwendet haben.  
    Wenn Sie sich zum ersten Mal anmelden, müssen Sie sich registrieren und eine Gebühr bezahlen, um Mitglied im Google Developer-Programm zu werden.
2. Wählen Sie in der Konsole **Neue Anwendung hinzufügen** aus.
3. Informationen über Ihre App laden Sie auf dieselbe Weise hoch wie Sie Apps im Google Play Store veröffentlichen. Sie müssen jedoch **Only make this application available to my organization (<*organization name*>)** (Diese Anwendung nur für meine Organisation [<Name der Organisation>] verfügbar machen) auswählen.

    ![Verfügbarmachen der App nur für Ihre Organisation](./media/apps-add-android-for-work/restrict.png)

    Durch diese Aktion wir die App nur für Ihre Organisation verfügbar gemacht. Sie wird nicht im öffentlichen Google Play Store verfügbar gemacht.

    Weitere Informationen zum Hochladen und Veröffentlichen von Android-Apps finden Sie in der [Google Developer Console-Hilfe](https://support.google.com/googleplay/android-developer/answer/113469).
4. Nachdem Sie Ihre App veröffentlicht haben, melden Sie sich beim [verwalteten Google Play Store](https://play.google.com/work) mit dem Konto an, das Sie zum Konfigurieren der Verbindung zwischen Intune und Android Enterprise verwendet haben.
5. Prüfen Sie im Knoten **Apps** im Store, ob die veröffentlichte App angezeigt wird.  
    Die App ist automatisch für die Synchronisierung mit Intune genehmigt.

## <a name="managed-google-play-web-links"></a>Weblinks „Verwaltetes Google Play“

Weblinks für verwaltetes Google Play können wie andere Android-Apps installiert und verwaltet werden. Bei Installation auf einem Gerät werden sie in der App-Liste des Benutzers neben den anderen installierten Apps angezeigt. Wenn darauf getippt wird, werden sie im Browser des Geräts gestartet.

Weblinks werden in Microsoft Edge oder einer anderen Browser-App geöffnet, die Sie bereitstellen möchten. Stellen Sie sicher, dass Sie mindestens eine Browser-App auf Geräten bereitstellen, damit Weblinks ordnungsgemäß geöffnet werden können. Alle für Weblinks verfügbaren Optionen für die **Anzeige** (Vollbildschirm, eigenständige und minimale Benutzeroberfläche) funktionieren jedoch nur im Browser Chrome. 

> [!IMPORTANT]
> Zum Zeitpunkt der Veröffentlichung dieses Dokuments gibt es einen bekannten Google-Fehler, der das Öffnen von Weblinks auf Geräten mit anderen Browsern als Chrome verhindert. Google arbeitet an der Korrektur dieses Fehlers.  Dieser Hinweis wird entfernt, sobald Microsoft die Bestätigung erhält, dass Google die Korrektur veröffentlicht hat.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im **Intune**-Bereich die Option **Client-Apps** > **Apps** aus.
5. Klicken Sie im Bereich **Apps** auf **Hinzufügen**.
6. Wählen Sie in der Dropdownliste **App-Typ** **Verwaltetes Google Play** aus.
7. Wählen Sie **Verwaltetes Google Play -> Öffnen** aus, um den Katalog für verwaltetes Google Play zu öffnen.
7. Wählen Sie im Google Play-Katalog **Web-Apps** aus.
7. Klicken Sie auf die Schaltfläche **+** , um eine neue App hinzuzufügen.
7. Geben Sie die erforderlichen Informationen ein, und klicken Sie dann auf **Erstellen**.
7. Schließen Sie den Bereich „Verwaltetes Google Play“, wenn das Hinzufügen von Apps abgeschlossen ist.
12. Klicken Sie im Bereich **App** auf **Synchronisieren**, um eine Synchronisierung mit dem verwalteten Google Play-Dienst durchzuführen. Beachten Sie, dass es mehrere Minuten dauern kann, bis private Apps zur Synchronisierung verfügbar sind. Wenn die App bei der ersten Synchronisierung nicht angezeigt wird, warten Sie ein paar Minuten und starten dann eine neue Synchronisierung.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Synchronisieren einer App aus dem Managed Google Play Store mit Intune

Wenn Sie eine App aus dem Store genehmigt haben und diese nicht in der Workload **Client-Apps** angezeigt wird, erzwingen Sie wie folgt eine sofortige Synchronisierung:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Setup** die Option **Managed Google Play** aus.
5. Klicken Sie im Bereich **Managed Google Play** auf **Aktualisieren**.  
    Auf der Seite werden Uhrzeit und Status der letzten Synchronisierung aktualisiert.
6. Wählen Sie im Workloadbereich **Client-Apps** die Option **Apps** aus.  
    Die neu verfügbare Managed Google Play-App wird angezeigt.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Zuweisen einer verwalteten Google Play-App zu Android Enterprise-Arbeitsprofilgeräten

Wenn die App im Knoten **App-Lizenzen** des Workloadbereichs **Client-Apps** angezeigt wird, können Sie sie [wie jede andere App zuweisen](/intune-azure/manage-apps/deploy-apps), indem Sie die App Benutzergruppen zuweisen.

Nachdem Sie die App zugewiesen haben, wird sie auf den Geräten der von Ihnen ausgewählten Benutzern installiert (oder zur Installation verfügbar). Der Benutzer des Geräts wird nicht zur Genehmigung der Installation aufgefordert. Weitere Informationen zu dedizierten Android Enterprise-Arbeitsprofilgeräten finden Sie unter [Einrichten der Registrierung von Android Enterprise-Arbeitsprofilgeräten](../enrollment/android-work-profile-enroll.md). 

> [!NOTE] 
> Nur Apps, die zugewiesen wurden, werden einem Endbenutzer im verwalteten Google Play Store angezeigt. Dies ist daher ein wichtiger Schritt für den Administrator bei der Einrichtung von Apps mit verwaltetem Google Play.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Zuweisen einer verwalteten Google Play-App zu vollständig verwalteten Android Enterprise-Geräten

[Vollständig verwaltete Android Enterprise-Geräte](../enrollment/android-fully-managed-enroll.md) sind unternehmenseigene Geräte, die einem einzelnen Benutzer zugeordnet sind und ausschließlich für Arbeits- und nicht für persönliche Zwecke genutzt werden. Benutzer vollständig verwalteter Geräte können ihre verfügbaren Unternehmens-Apps von der verwalteten Google Play-App auf ihrem Gerät beziehen.

Standardmäßig erlaubt ein vollständig verwaltetes Android Enterprise-Gerät Mitarbeitern nicht, Apps zu installieren, die nicht von der Organisation genehmigt sind. Außerdem können Mitarbeiter keine installierten Apps gegen geltende Richtlinien entfernen. Wenn Sie Benutzern den Zugriff auf den vollständigen Google Play-Store ermöglichen möchten, um Apps zu installieren, anstatt ihnen nur Zugriff auf die genehmigten Apps im verwalteten Google Play-Store einzuräumen, können Sie die Einstellung **Zugriff auf alle Apps im Google Play Store zulassen** auf **Zulassen** festlegen. Bei dieser Einstellung kann der Benutzer über sein Unternehmenskonto auf alle Apps im Google Play Store zugreifen, wobei Käufe jedoch eingeschränkt sein können. Sie können die Kaufbeschränkung aufheben, indem Sie Benutzern erlauben, neue Konten zum Gerät hinzuzufügen. Auf diese Weise können Endbenutzer Apps im Google Play Store über persönliche Konten erwerben und auch In-App-Käufe durchführen. Weitere Informationen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md). 

> [!NOTE]
> Die Apps Microsoft Intune und Microsoft Authenticator werden während des Onboardings bei Bedarf auf allen vollständig verwalteten Geräten installiert. Die automatische Installation dieser Apps bietet Unterstützung für bedingten Zugriff. Benutzer der App Microsoft Intune können Konformitätsprobleme erkennen und beheben. 

## <a name="manage-android-enterprise-app-permissions"></a>Verwalten von Berechtigungen für Android Enterprise-Apps
Android Enterprise erfordert, dass Sie Apps in der Webkonsole von verwaltetem Google Play genehmigen, bevor Sie sie mit Intune synchronisieren und Ihren Benutzern zuweisen. Da Sie diese Apps mit Android Enterprise im Hintergrund und automatisch auf die Geräte der Benutzer übertragen können, müssen Sie die App-Berechtigungen im Interesse aller Ihrer Benutzer akzeptieren. Benutzern werden bei der Installation der Apps keine App-Berechtigungen angezeigt. Daher ist es wichtig, dass Sie diese Berechtigungen verstehen.

Wenn ein App-Entwickler eine neue Version der App mit aktualisierten Berechtigungen veröffentlicht, werden diese Berechtigungen auch dann nicht automatisch akzeptiert, wenn Sie die vorherigen Berechtigungen genehmigt haben. Geräte, auf denen die vorherige Version der App ausgeführt wird, können diese weiterhin verwenden. Die App wird jedoch erst dann aktualisiert, wenn die neuen Berechtigungen genehmigt wurden. Geräte, auf denen die App nicht installiert ist, können die App nicht installieren, solange Sie die neuen Berechtigungen der App nicht genehmigt haben. 

### <a name="update-app-permissions"></a>Aktualisieren von App-Berechtigungen

Besuchen Sie regelmäßig die verwaltete Google Play-Konsole, um zu prüfen, ob neue Berechtigungen vorliegen. Sie können Google Play so konfigurieren, dass eine E-Mail an Sie oder andere Personen gesendet wird, wenn neue Berechtigungen für eine genehmigte App erforderlich sind. Wenn Sie eine App zuweisen und feststellen, dass sie nicht auf Geräten installiert ist, überprüfen Sie folgendermaßen, ob neue Berechtigungen vorliegen:

1. Wechseln Sie zu [Google Play](https://play.google.com/work).
2. Melden Sie sich mit dem Google-Konto an, das Sie zum Veröffentlichen und Genehmigen der Apps verwendet haben.
3. Wählen Sie die Registerkarte **Updates** aus, und überprüfen Sie, ob andere Apps ein Update erfordern.  
    Alle aufgelisteten Apps erfordern neue Berechtigungen und werden erst zugewiesen, wenn diese Berechtigungen angewendet wurden.

Alternativ können Sie Google Play so konfigurieren, dass App-Berechtigungen auf App-Basis automatisch erneut genehmigt werden.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Zusätzliche Berichterstellung für verwaltete Google Play-Apps für Android Enterprise-Arbeitsprofilgeräte

Sie können die Versionsnummer von auf Android Enterprise-Arbeitsprofilgeräten bereitgestellten, verwalteten Google Play-Apps anzeigen. Dies gilt nur für erforderliche Apps. 


## <a name="delete-managed-google-play-apps"></a>Löschen von verwalteten Google Play-Apps
Sie können verwaltete Google Play-Apps bei Bedarf aus Microsoft Intune löschen. Um eine verwaltete Google Play-App zu löschen, öffnen Sie Microsoft Intune im Azure-Portal und wählen **Client-Apps** > **Apps** aus. Klicken Sie in der App-Liste auf die Auslassungspunkte (...) rechts neben der verwalteten Google Play-App, und wählen Sie dann in der angezeigten Liste die Option **Löschen** aus. Wenn Sie eine verwaltete Google Play-App aus der App-Liste löschen, wird die Genehmigung für die Google Play-App automatisch aufgehoben.

## <a name="android-enterprise-system-apps"></a>Android Enterprise-System-Apps

Sie können für [dedizierte Android Enterprise-Geräte](../enrollment/android-kiosk-enroll.md) oder [ vollständig verwaltete Geräte](../enrollment/android-fully-managed-enroll.md) eine Android Enterprise-System-App aktivieren. Weitere Informationen zum Hinzufügen einer Android Enterprise-System-App finden Sie unter [Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune](apps-ae-system.md).

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
