---
title: Bereitstellen von Lookout for Work-Apps
description: Konfigurieren und Bereitstellen von Lookout for Work-Apps für Android.
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/21/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1b08ac6049bc7bbbf5c2203f156a6c03b6fc7a51
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configure-and-deploy-lookout-for-work-app"></a>Konfigurieren und Bereitstellen der Lookout for Work-App

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

In diesem Artikel wird die Konfiguration und Bereitstellung der Lookout for Work-App für Android- und iOS-Geräte beschrieben.

## <a name="android-google-play-store-app"></a>Android (Google Play Store-App)

1. Wechseln Sie in der [Microsoft Intune-Administratorkonsole](https://manage.microsoft.com) zu **Apps**, und wählen Sie **Apps hinzufügen** aus.
2. Klicken Sie auf der Seite **Softwaresetup** des Herausgebers auf **Externer Link** und geben Sie folgende URL ein: https://play.google.com/store/apps/details?id=com.lookout.enterprise.
   >[!NOTE]
   >Klicken Sie nicht auf das Feld, das einen verwalteten Browser vorschreibt.

3. Geben Sie auf der Seite **Softwarebeschreibung** die folgenden Informationen ein:
   * **Herausgeber:** Lookout Mobile Security
   * **Name:**   Lookout for Work
   * **Beschreibung:** Lookout bietet optimalen Schutz vor mobilen Bedrohungen, um die Sicherheit Ihres Geräts zu gewährleisten. Wenn die Lookout-App auf einem Gerät installiert ist, schützt die App das Gerät vor Bedrohungen und warnt Sie und Ihren Unternehmensadministrator, wenn Bedrohungen erkannt werden.
   * **Kategorie:** Computerverwaltung

4. Nach erfolgreichem Abschluss wird die Meldung **Daten wurden erfolgreich in Microsoft Intune hochgeladen** angezeigt.

   Wenn Sie in der Intune-Konsole auf **Apps** klicken, wird die **Lookout for Work**-App nun in der Liste angezeigt. ![Screenshot der Seite mit den Intune-Administratorkonsolen-Apps, auf der die Liste mit Lookout for Work-Apps angezeigt wird](../media/mtp/lookout-app-listed-intune-console.png)

5. Stellen Sie die App für Benutzer bereit, indem Sie die Lookout for Work-App und anschließend die Option **Bereitstellung verwalten** auswählen.

   Sie müssen die gleichen Benutzer auswählen, die unter der Option „Registrierungsverwaltung“ in der Lookout-MTP-Konsole hinzugefügt wurden.  Informationen zum Hinzufügen von Benutzergruppen zu Lookout MTP finden Sie unter Schritt 3 im Abschnitt [Konfigurieren Ihres Abonnements mit Lookout MTP](configure-deploy-lookout-for-work-app.md).

   >[!IMPORTANT]
   > Dem Intune-Assistenten für die App-Bereitstellung sind die Azure AD-Benutzergruppen nicht bekannt, er verwendet daher die Intune-Benutzergruppen. Sie müssen auf der Grundlage der Azure AD-Benutzergruppe, die bei der Lookout MTP-Konsole registriert ist, eine Intune-Benutzergruppe erstellen, wie in [diesem](plan-your-user-and-device-groups.md) Thema erläutert wird.

6. Aktivieren Sie die Option **Erforderliche Installation**, um vorzuschreiben, dass die Lookout-App auf dem Gerät des Benutzers installiert wird.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (Enterprise-signierte Version der Lookout-App)

1. Stellen Sie sicher, dass die **iOS-Verwaltung** auf Ihrem Gerät eingerichtet ist. Eine Anleitung zum Einrichten Ihres Geräts für die iOS-Verwaltung finden Sie unter [Einrichten der iOS- und Mac-Geräteverwaltung](set-up-ios-and-mac-management-with-microsoft-intune.md).

2. Sie müssen nun die Lookout for Work-App für iOS **erneut signieren**. Lookout verteilt die Lookout for Work-App für iOS außerhalb von iOS App Store. **Bevor Sie die App verteilen**, müssen Sie die App mit Ihrem iOS Enterprise Developer Certificate neu signieren. Ausführliche Anweisungen zum erneuten Signieren der Lookout for Work-Apps für iOS finden Sie unter [iOS App Re-Signing Process (Erneute Signatur bei iOS-Apps)](https://personal.support.lookout.com/hc/articles/114094038714) auf der Lookout-Website.

3. Aktivieren Sie die Azure Active Directory-Authentifizierung für iOS-Benutzer, indem Sie folgendermaßen vorgehen:
   1.  Melden Sie sich beim [Azure Active Directory-Verwaltungsportal](https://manage.windowsazure.com) an, und navigieren Sie zur Anwendungsseite.
   2.  Fügen Sie die **Lookout for Work iOS-App** als eine **native Clientanwendung** hinzu.
   ![Screenshot des Dialogfelds Apps hinzufügen mit der Option native Clientanwendung](../media/mtp/aad-add-app.png)
   3. Ersetzen Sie **com.lookout.enterprise.yourcompanyname** mit der Kundenbundle-ID, die Sie beim Unterzeichnen der IPA ausgewählt haben.
   4.  Hinzufügen von zusätzlichen Umleitungs-URI:  **&lt;companyportal://code/>** gefolgt von einer URL-codierten Version Ihrer ursprünglichen URI-Umleitung.
   5.  Fügen Sie **Delegierte Berechtigungen** zu Ihrer App hinzu.

   Weitere Informationen finden Sie unter [Konfigurieren Sie eine native Clientanwendung](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

4. Laden Sie die neu signierte IPA-Datei hoch, wie im Thema [Hinzufügen von Apps für mobile Geräte zu Microsoft Intune](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) beschrieben. Legen Sie iOS 8.0 oder höher als die mindestens erforderliche Betriebssystemversion fest.

   ![Screenshot der Apps-Seite in der Intune-Administratorkonsole, auf der die Lookout for Work-App in der Liste der Apps angezeigt wird](../media/mtp/ios-app-uploaded-intune.png)

5. Erstellen Sie die Konfigurationsrichtlinie für verwaltete Apps, wie im Thema [Konfigurieren von iOS-Apps mit Konfigurationsrichtlinien für mobile Apps in Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune) beschrieben.

   ![Screenshot des Assistenten zum Erstellen einer neuen Richtlinie, wobei die Konfigurationsrichtlinie für die App für iOS 8.0 oder höher hervorgehoben ist](../media/mtp/ios-app-config.png)

6. Wählen Sie zum **Bereitstellen der App für Benutzer** die Lookout for Work-App und anschließend die Option **Bereitstellung verwalten**.

   Sie müssen die gleichen Benutzer auswählen, die unter der Option „Registrierungsverwaltung“ in der Lookout-Konsole hinzugefügt wurden.  Informationen zum Hinzufügen von Benutzergruppen zu Lookout MTP finden Sie unter Schritt 3 im Artikel [Konfigurieren und Bereitstellen von Lookout for Work-Apps](https://docs.microsoft.com/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps).

   >[!IMPORTANT]
   > Dem Intune-Assistenten für die App-Bereitstellung sind die Azure AD-Benutzergruppen nicht bekannt, weshalb er die Intune-Benutzergruppen verwendet. Sie müssen daher auf Grundlage der Azure AD-Benutzergruppe, die bei der Lookout-Konsole registriert ist, eine Intune-Benutzergruppe erstellen, was in [diesem](plan-your-user-and-device-groups.md) Thema erläutert wird.

   Aktivieren Sie die Option **Erforderliche Installation**, um vorzuschreiben, dass die Lookout-App auf dem Gerät des Benutzers installiert wird.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Was geschieht beim Öffnen der bereitgestellten App auf dem Gerät?
https://github.com/Microsoft/Docs/blob/master/ContributorGuide/index.md Wenn der Benutzer Lookout for Work auf dem mobilen Gerät öffnet, wird er aufgefordert, die App zu aktivieren und die Option „Bei Azure Active Directory anmelden“ auszuwählen. Eine ausführliche exemplarische Vorgehensweise mit dem Arbeitsablauf für den Endbenutzer finden sich in folgenden Themen:

* [Sie werden zur Installation von Lookout for Work auf Ihrem Android-Gerät aufgefordert](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)

* [Sie müssen eine Bedrohung beheben, die Lookout for Work auf Ihrem Android-Gerät gefunden hat](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>Nächste Schritte
* [Erstellen einer Lookout-Gerätekonformitätsrichtlinie in Intune](https://docs.microsoft.com/sccm/protect/deploy-use/enable-device-threat-protection-rule-compliance-policy)
