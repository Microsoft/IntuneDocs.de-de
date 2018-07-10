---
title: Registrieren Ihres Android-Geräts bei Intune | Microsoft-Dokumentation
description: Beschreibt, wie Sie ein Android-Gerät bei Intune registrieren.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: a48e43a024358b35c88014d2b4a05f2245f13a3f
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34449835"
---
# <a name="enroll-your-android-device-in-intune"></a>Registrieren Ihres Android-Geräts bei Intune

Wenn Ihr Unternehmen oder Ihre Schule Microsoft Intune verwendet, können Sie Ihr Android-Gerät registrieren, um Zugriff auf Unternehmens-E-Mails, Dateien und weitere Ressourcen zu erhalten. Wenn Sie Ihre Geräte registrieren, kann Ihre IT-Abteilung diese Geschäfts-, Schul- oder Uniressourcen verwalten, schützen und Ihnen gleichzeitig die Möglichkeit bieten, Ihr bevorzugtes Gerät zu verwenden, um Ihre Arbeit erledigen. Weitere Informationen zur Registrierung finden Sie unter [Was geschieht, wenn ich die Unternehmensportal-App installiere und mein Gerät registriere?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md)

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment/player]

Diese Registrierungsanweisungen gelten für native Android-Geräte und für Android-Geräte mit Samsung KNOX. Samsung KNOX ist ein Sicherheitssystem, mit dem bestimmte Geräte von Samsung neben den nativen Android-Sicherheitsfeatures zusätzlichen Schutz bieten. Navigieren Sie zu **Einstellungen** > **Geräteinformationen**, um zu überprüfen, ob es sich bei Ihrem Gerät um ein Samsung KNOX-Gerät handelt. Wird „KNOX-Version“ nicht angezeigt, verfügen Sie über ein natives Android-Gerät.

Vor oder nach der Registrierung werden Sie möglicherweise aufgefordert, eine Kategorie auszuwählen, die am besten beschreibt, wie Sie Ihr Gerät nutzen. Der Support Ihres Unternehmens verwendet diese Kategorie, um die Apps zu überprüfen, auf die Sie Zugriff haben.

**So registrieren Sie Ihr Android-Gerät:**

1. Installieren Sie die kostenlose Intune-Unternehmensportal-App aus [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).

2. Öffnen Sie die Unternehmensportal-App.

3. Tippen Sie im Unternehmensportal auf dem **Begrüßungsbildschirm** auf **Anmelden**, und melden Sie sich dann mit Ihrem Geschäfts-, Schul- oder Unikonto an.

   ![Die Willkommensseite der Unternehmensportal-App für Android mit der Aufforderung, sich mit dem erforderlichen Geschäfts-, Schul- oder Unikonto anzumelden. Zusätzlich wird darauf hingewiesen, dass Microsoft-Konten und andere persönliche Konten nicht akzeptiert werden.](./media/and-enroll-0-welcome-screen.png)   

4. Wenn der Support Ihres Unternehmens Nutzungsbedingungen des Unternehmens eingerichtet hat, tippen Sie auf **AKZEPTIEREN**, um sie anzunehmen. Dieser Bildschirm kann sich von der nachstehenden Abbildung je nach aktuell verwendeter Version von Android geringfügig unterscheiden.

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. Melden Sie sich bei der Unternehmensportal-App mit Ihrem Geschäfts-, Schul- oder Unikonto und dem zugehörigen Kennwort an, und tippen Sie dann auf **Anmelden**.

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. Tippen Sie auf dem Bildschirm **Unternehmenszugriff einrichten** auf **WEITER**.

   ![Bildschirm „Unternehmenszugriff einrichten“](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > Die gelben Dreiecke bedeuten nicht, dass bereits ein Fehler vorliegt. Sie geben lediglich an, dass für den Registrierungsprozess noch Schritte ausgeführt werden müssen.

7. Prüfen Sie in der angezeigten Liste, was der Support Ihres Unternehmens auf Ihrem Gerät sehen kann und was nicht, und tippen Sie auf **WEITER**.

   ![Datenschutzeinstellungen](/intune/media/android_cp_enroll_02_after_1710.png)

8. Lesen Sie auf dem Bildschirm **What's next?** (Wie geht es weiter?), was während der Registrierung passiert, und tippen Sie dann auf **REGISTRIEREN**.

   ![Was ist der nächste Schritt?](/intune/media/android_cp_enroll_03_after_1710.png)

9. Wenn Sie Android 6.0 oder höher verwenden, führen Sie diesen Schritt aus. Fahren Sie andernfalls mit dem nächsten Schritt fort.

   Wenn der Support Ihres Unternehmens bestimmte Richtlinien eingerichtet hat, werden möglicherweise folgende Meldungen angezeigt:
   - **Zulassen, dass das Unternehmensportal Telefonanrufe tätigt und verwaltet?**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   Wenn diese Meldung angezeigt wird, tippen Sie auf **ZULASSEN**. Sie können ruhig auf „ZULASSEN“ tippen, weil **Microsoft niemals Ihre Telefonanrufe tätigt oder verwaltet**! Google steuert den Meldungstext, daher kann er von Microsoft nicht geändert werden. Wenn Sie den Zugriff gewähren, erlauben Sie Ihrem Gerät schlicht, die IMEI-Nummer (International Mobile Station Equipment Identity) Ihres Geräts an Intune zu senden. Die IMEI ähnelt einer Seriennummer, mit der ein mobiles Gerät eindeutig identifiziert werden kann.

   Wenn Sie den Zugriff verweigern, wird die Meldung bei Ihrer nächsten Anmeldung beim Unternehmensportal angezeigt. Sie können künftige Meldungen jedoch deaktivieren, indem Sie das Kontrollkästchen **Nicht mehr nachfragen** aktivieren. Wenn Sie den Zugriff später erlauben möchten, wechseln Sie zu **Einstellungen** &gt; **Apps** &gt; **Unternehmensportal** &gt; **Berechtigungen** &gt; **Telefon**, um die Berechtigung zu aktivieren.

   - **Zulassen, dass das Unternehmensportal auf Ihre Kontakte zugreift?**

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     Wenn diese Meldung angezeigt wird, tippen Sie auf **ZULASSEN**. Sie können ruhig auf „ZULASSEN“ tippen, weil **Microsoft niemals auf Ihre Kontakte zugreift**! Google steuert den Meldungstext, daher kann er von Microsoft nicht geändert werden. Wenn Sie den Zugriff gewähren, wird der Unternehmensportal-App lediglich das Erstellen, Verwenden und Verwalten Ihres Geschäftskontos erlaubt.

     Wenn Sie den Zugriff verweigern, wird die Meldung bei Ihrer nächsten Anmeldung beim Unternehmensportal angezeigt. Sie können künftige Meldungen jedoch deaktivieren, indem Sie das Kontrollkästchen **Nicht mehr nachfragen** aktivieren. Wenn Sie den Zugriff später erlauben möchten, wechseln Sie zu **Einstellungen** &gt; **Apps** &gt; **Unternehmensportal** &gt; **Berechtigungen** &gt; **Telefon**, um die Berechtigung zu aktivieren.

10. Klicken Sie auf dem Bildschirm **Geräteadministrator aktivieren** auf **Aktivieren**.

    ![Bildschirm „Geräteadministrator aktivieren?“](./media/and-enroll-5-activate.png)

    Die Geräteadministratorrolle wird vom Unternehmensportal benötigt, um Ihr Gerät zu verwalten. Damit kann Ihr Administrator bestimmte Dinge sehen – zum Beispiel wie oft Sie versucht haben, Ihren Bildschirm zu entsperren – und einige Aktionen vornehmen.

    Es gilt zu beachten, dass diese Aktionen im Namen der Sicherheit ausgeführt werden. Der Support Ihres Unternehmens wird nicht versuchen, Ihre Privatsphäre zu verletzen oder Ihre Daten ohne Grund zu löschen, möchte aber sicherstellen, dass Unternehmensdaten sicher aufbewahrt werden.

    Microsoft wird diese Meldung nicht kontrollieren, und wir wissen, dass die Ausdrucksweise etwas drastisch erscheinen kann. Es gibt keine Möglichkeit, dass das Unternehmensportal nur die Einschränkungen und Zugriffe anzeigt, die für Ihre Organisation relevant sind. Alle werden auf diesem Bildschirm auf einmal erteilt. Wenden Sie sich mithilfe der Kontaktinformationen auf der [Unternehmensportalwebsite](https://portal.manage.microsoft.com#HelpDeskDialog) an den Support Ihres Unternehmens, wenn Sie spezifische Fragen zur Verwendung in Ihrer Organisation haben.

11. Befolgen Sie die Aufforderungen zur Eingabe einer PIN oder eines Kennworts. Wenn Sie bereits eine PIN oder ein Kennwort auf diesem Gerät eingerichtet haben, wird dieser Bildschirm nicht angezeigt, und Sie werden nicht zur Eingabe einer neuen PIN oder eines neuen Kennworts aufgefordert.

    ![Eingeben von PIN oder Kennwort](./media/and-enroll-6-PIN-native.png)

12. Wenn Sie ein Samsung Knox-Gerät verwenden, tippen Sie auf **Bestätigen**. Es wird eine Meldung angezeigt, die besagt, dass das Gerät registriert wird. Wenn Sie ein natives Android-Gerät verwenden, beachten Sie den folgenden Bildschirm, der anzeigt, dass das Gerät registriert wird.

    ![Samsung KNOX-Datenschutzrichtlinie](./media/and-enroll-7-knox-privacy-policy.png)

    Dieser Bildschirm zeigt an, dass das Gerät registriert wird.

    ![Bildschirm „Gerät wird registriert“](./media/and-enroll-8-device-enrolling.png)

13. Wenn der Bildschirm **Einrichten des Unternehmenszugriffs** angezeigt wird, tippen Sie auf **WEITER**. Wenn eine Meldung anzeigt, dass Ihr Gerät nicht kompatibel ist, befolgen Sie die Anweisungen zum Beheben des Problems, und tippen Sie dann auf **WEITER**.

    ![Das Gerät ist nicht kompatibel, aber registriert.](/intune/media/android_cp_enroll_05_post_1709.png)

    ![Es liegen Probleme mit der Gerätekompatibilität vor, die behoben werden müssen.](/intune/media/android_cp_enroll_03_post_1709.png)

    Tippen Sie ggf. auf die einzelnen Probleme, um weitere Informationen zu erhalten.

    ![Erweiterte Ansicht von Gerätekompatibilitätsproblemen](/intune/media/android_cp_enroll_04_post_1709.png)

    ![Bildschirm „Unternehmenszugriff einrichten“](./media/and-enroll-9d-comp-access-setup.png)  

14. Tippen Sie auf dem Bildschirm **Einrichten des Unternehmenszugriffs abgeschlossen** auf **FERTIG**. Ihr Gerät ist jetzt bei registriert.

    ![Bildschirm „Einrichten des Unternehmenszugriffs abgeschlossen“](./media/and-enroll-10-comp-access-setup-complete.png)

Bevor Sie versuchen, Unternehmens-Apps zu installieren, wechseln Sie zu **Einstellungen** &gt; **Sicherheit**, und aktivieren Sie **Unknown sources** (Unbekannte Quellen). Wenn Sie diese Option nicht aktivieren, bevor Sie versuchen, Apps zu installieren, wird die folgende Meldung angezeigt: „Installation blockiert. Aus Sicherheitsgründen ist Ihr Gerät so eingestellt, dass die Installation von Apps aus unbekannten Quellen blockiert wird.“ Sie können im Fehlerdialogfeld auf **Einstellungen** tippen, um zur Option **Unknown sources** zu wechseln.

> [!Note]
> Wenn Ihre Organisation Telecom Expense Management-Software verwendet, müssen Sie ein paar zusätzliche Schritte ausführen, bevor das Gerät vollständig registriert ist. [Hier](enroll-your-device-with-telecom-expense-management-android.md) erfahren Sie mehr.

Sollte beim Versuch der Registrierung Ihres Geräts bei Intune ein Fehler auftreten, können Sie [Registrierungsfehler an den Support Ihres Unternehmens senden](send-enrollment-errors-to-your-it-admin-android.md).

Benötigen Sie weitere Unterstützung? Wenden Sie sich an den Support Ihres Unternehmens (suchen Sie auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com#HelpDeskDialog) nach Kontaktinformationen) oder an das <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-Team</a>.
