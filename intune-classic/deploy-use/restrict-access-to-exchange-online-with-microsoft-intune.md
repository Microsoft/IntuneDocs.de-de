---
title: "Schützen von E-Mail an Exchange Online"
description: "Schützen und steuern Sie den Zugriff auf Unternehmens-E-Mail in Exchange Online mit bedingtem Zugriff."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5ea0e0c31dc3b24c0093d6e3b73d38f2bee50bd7
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="protect-email-access-to-exchange-online-and-new-exchange-online-dedicated-with-intune"></a>Schützen des E-Mail-Zugriffs auf Exchange Online- und neue Exchange Online Dedicated-Umgebungen mit Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können bedingten Zugriff für Exchange Online oder Exchange Online Dedicated mithilfe Microsoft Intune konfigurieren. Weitere Informationen zur Funktionsweise des bedingten Zugriffs finden Sie im Artikel [Protect access to email, O365, and other services (Schützen des Zugriffs auf E-Mail, O365 und andere Dienste)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!NOTE]
>Wenn Sie über eine Exchange Online Dedicated-Umgebung verfügen und herausfinden müssen, ob es sich um die neue oder die ältere Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer.

## <a name="before-you-begin"></a>Vorbereitung

Um den bedingten Zugriff zu konfigurieren, müssen Sie folgende Schritte ausführen:

-   Sie müssen über ein **Office 365-Abonnement verfügen, das Exchange Online (z.B. E3)** umfasst, und die Benutzer müssen für Exchange Online lizenziert sein.

- Sie müssen über ein **Enterprise Mobility + Security- (EMS)** oder **Azure Active Directory (Azure AD) Premium-Abonnement** verfügen, und Benutzer müssen für EMS oder Azure AD lizenziert sein. Weitere Informationen finden Sie in der [Preisübersicht für Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) oder der [Preisübersicht für Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

-  Sie sollten erwägen, den optionalen **Intune Service to Service Connector** zu konfigurieren, der Intune mit Exchange Online verbindet und die Verwaltung von Geräteinformationen über die Intune-Konsole ermöglicht. Der Connector ist zur Verwendung von Kompatibilitätsrichtlinien oder Richtlinien für den bedingten Zugriff nicht zwingend erforderlich, Sie benötigen ihn aber zum Ausführen von Berichten, mit deren Hilfe die Auswirkungen des bedingten Zugriffs bewertet werden.
    -  Erfahren Sie mehr über den [Intune Service to Service Connector](intune-service-to-service-exchange-connector.md).

   > [!NOTE]
   > Konfigurieren Sie den Intune Service to Service Connector nicht, wenn Sie beabsichtigen, die Zugangsberechtigung für Exchange Online und lokales Exchange zu verwenden.

### <a name="device-compliance-requirements"></a>Konformitätsanfoderungen für Geräte

Wenn Sie Richtlinien für bedingten Zugriff konfigurieren und auf einen Benutzer anwenden, muss das **Gerät**, das der Benutzer zum Abrufen von E-Mails verwendet, folgende Voraussetzungen erfüllen:

- Es muss ein in die Domäne eingebundener PC oder bei Intune **registriert** sein.

- **Es muss in Azure Active Directory registriert sein**. Die erfolgt automatisch, wenn das Gerät bei Intune registriert ist. Darüber hinaus muss die Exchange ActiveSync-ID des Clients in Azure Active Directory registriert sein.

  Der Azure Active Directory-Geräteregistrierungsdienst wird automatisch für Intune- und Office 365-Kunden aktiviert. Kunden, die bereits den AD FS Device Registration Service bereitgestellt haben, sehen keine registrierten Geräte im lokalen Active Directory.

- Es muss mit allen Intune-Konformitätsrichtlinien **konform** sein, die auf diesem Gerät bereitgestellt wurden, oder es muss einer lokalen Domäne beigetreten sein.

### <a name="when-the-device-is-not-compliant"></a>Wenn das Gerät nicht konform ist

Wenn eine Richtlinie für bedingten Zugriff nicht erfüllt wird, wird das Gerät sofort unter Quarantäne gestellt, und der Benutzer erhält bei der Anmeldung eine E-Mail-Nachricht mit einer der folgenden Quarantänenachrichten:

- Wenn das Gerät nicht bei Intune oder in Azure Active Directory registriert ist, wird eine Meldung mit Anweisungen zum Installieren der Unternehmensportal-App, zum Registrieren des Geräts und zum Aktivieren des E-Mail-Zugriffs angezeigt. Dieser Prozess verknüpft auch die Exchange ActiveSync-ID mit dem Eintrag in Azure Active Directory.

-   Wenn das Gerät als nicht kompatibel mit den Kompatibilitätsrichtlinien ausgewertet wird, wird der Benutzer zur Intune-Unternehmensportalwebsite oder zur Unternehmensportal-App weitergeleitet. Dort findet der Benutzer Informationen zum Problem und zur Lösung.

### <a name="how-conditional-access-works-with-exchange-online"></a>So funktioniert der bedingte Zugriff für Exchange Online

Das folgende Diagramm veranschaulicht den Ablauf, den Richtlinien für bedingten Zugriff für Exchange Online befolgen.

![Diagramm zur Veranschaulichung der Entscheidungspunkte, die bestimmen, ob der Zugriff für das Gerät zugelassen oder blockiert wird](../media/ConditionalAccess8-1.png)

## <a name="support-for-mobile-devices"></a>Unterstützung für mobile Geräte
Sie können den Zugriff auf Exchange Online-E-Mails über **Outlook** und andere **Apps, die die moderne Authentifizierung verwenden**, schützen. Die folgenden Betriebssysteme werden unterstützt:

- Android 4.0 und höher, Samsung KNOX Standard 4.0 und höher sowie Android for Work
- iOS 8.0 und höher

Die **moderne Authentifizierung** ermöglicht das ADAL-basierte (Active Directory Authentication Library) Anmelden für Microsoft Office-Clients.

-   Die ADAL-basierte Authentifizierung ermöglicht Office-Clients die Einbindung in die browserbasierte Authentifizierung (auch als passive Authentifizierung bekannt). Ein Benutzer wird zur Authentifizierung zu einer Anmeldewebseite umgeleitet.
-   Diese neue Anmeldemethode bietet mehr Sicherheitsmerkmale wie z.B. die **mehrstufige Authentifizierung** und die **zertifikatbasierte Authentifizierung**. Weitere ausführliche Informationen finden Sie unter [Funktionsweise der modernen Authentifizierung](https://support.office.com/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517). Sie können Anspruchsregeln für Active Directory-Verbunddienste (AD FS) so einrichten, dass nicht moderne Authentifizierungsprotokolle blockiert werden. Detaillierte Anleitungen werden in Szenario 3 beschrieben: [Blockieren des gesamten Zugriffs auf Office 365 außer durch browserbasierte Anwendungen](https://technet.microsoft.com/library/dn592182.aspx).

Sie können den Zugriff auf **Outlook Web Access (OWA)** auf Exchange Online schützen, wenn von einem Browser auf **iOS**- und **Android**-Geräten aus zugegriffen wird. Der Zugriff wird nur von unterstützten Browsern auf kompatiblen Geräten gewährt:

* Safari (iOS)
* Chrome (Android)
* Intune Managed Browser (iOS, Android 5.0 und höher)

   > [!IMPORTANT]
   > **Nicht unterstützte Browser werden blockiert**.

**Die OWA-App für iOS und Android kann so geändert werden, dass die moderne Authentifizierung nicht verwendet und unterstützt wird. Der Zugriff über die OWA-App muss durch AD FS-Anspruchsregeln blockiert werden.**


Auf folgenden Plattformen können Sie den Zugriff auf Exchange-E-Mails über den integrierten **Exchange ActiveSync-E-Mail-Client** schützen:

- Android 4.0 und höher, Samsung KNOX Standard 4.0 und höher

- iOS 8.0 und höher

- Windows Phone 8.1 und höher

## <a name="support-for-pcs"></a>Unterstützung für PCs

Sie können den bedingten Zugriff für PCs einrichten, auf denen Office-Desktopanwendungen ausgeführt werden, um auf **Exchange Online** und **SharePoint Online** zuzugreifen. Dies gilt für PCs, die folgende Anforderungen erfüllen:

- Der PC muss unter Windows 7.0, Windows 8.1 oder Windows 10 ausgeführt werden.

  >[!NOTE]
  > Damit Sie den bedingten Zugriff auf Windows 10-PCs verwenden können, müssen Sie diese PCs mit dem Windows 10 Anniversary-Update aktualisieren.

  Der PC muss entweder in die Domäne eingebunden oder mit den Kompatibilitätsrichtlinien kompatibel sein.

  Damit der PC als kompatibel bewertet wird, muss er bei Intune registriert sein und den Richtlinien entsprechen.

  Für in die Domäne eingebundene PCs müssen Sie den bedingten Zugriff für das Gerät einrichten, damit es bei Azure Active Directory [automatisch registriert wird](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/).

  >[!NOTE]
  >Bedingter Zugriff wird nicht auf PCs unterstützt, auf denen der Intune-Computerclient ausgeführt wird.

- [Die moderne Authentifizierung von Office 365 muss aktiviert sein](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) und alle neuesten Office-Updates enthalten.

  Die moderne Authentifizierung ermöglicht das ADAL-basierte (Active Directory Authentication Library) Anmelden für Office 2013/Windows-Clients. Diese neue Anmeldemethode bietet mehr Sicherheitsmerkmale wie z.B. die **mehrstufige Authentifizierung** und die **zertifikatbasierte Authentifizierung**.

- Anspruchsregeln für Active Directory-Verbunddienste (AD FS) sind so eingerichtet, dass nicht moderne Authentifizierungsprotokolle blockiert werden. Detaillierte Anleitungen werden in Szenario 3 beschrieben: [Blockieren des gesamten Zugriffs auf Office 365 außer durch browserbasierte Anwendungen](https://technet.microsoft.com/library/dn592182.aspx).

## <a name="configure-conditional-access"></a>Konfigurieren des bedingten Zugriffs
### <a name="step-1-configure-and-deploy-a-compliance-policy"></a>Schritt 1: Konfigurieren und Bereitstellen einer Konformitätsrichtlinie
Stellen Sie sicher, dass Sie eine Kompatibilitätsrichtlinie für die Benutzergruppen [erstellen](create-a-device-compliance-policy-in-microsoft-intune.md) und [bereitstellen](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md), für die auch die Richtlinie für bedingten Zugriff gelten soll.


> [!IMPORTANT]
> Wenn Sie keine Kompatibilitätsrichtlinie bereitgestellt haben, werden die Geräte als kompatibel bewertet und erhalten Zugriff auf Exchange.

### <a name="step-2-evaluate-the-effect-of-the-conditional-access-policy"></a>Schritt 2: Bewerten der Auswirkungen der Richtlinie für bedingten Zugriff
Mithilfe der **Inventurberichte für mobile Geräte** können Sie ermitteln, für welche Geräte der Zugriff auf Exchange blockiert wird, nachdem Sie die Richtlinie für bedingten Zugriff konfiguriert haben.

Konfigurieren Sie dafür eine Verbindung zwischen Intune und Exchange mithilfe des [Microsoft Intune Service to Service Connectors](intune-service-to-service-exchange-connector.md).
1.  Navigieren Sie zu **Berichte** > **Inventurberichte für mobile Geräte**.
![Screenshot der Seite mit den Inventurberichten für mobile Geräte](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  Wählen Sie in den Berichtsparametern die auszuwertende Intune-Gruppe sowie gegebenenfalls die Geräteplattformen aus, für die die Richtlinie gelten soll.
3.  Nachdem Sie die Kriterien ausgewählt haben, die den Anforderungen Ihres Unternehmens entsprechen, wählen Sie **Bericht anzeigen** aus.
Die Berichtsanzeige wird in einem neuen Fenster geöffnet.
![Screenshot eines Beispielinventurberichts für mobile Geräte](../media/IntuneSA2cViewReport.PNG)

Überprüfen Sie nach der Ausführung des Berichts die folgenden vier Spalten auf blockierte Benutzer:

-   **Verwaltungskanal**: Gibt an, ob das Gerät von Intune und/oder Exchange ActiveSync verwaltet wird.

-   **Bei AAD registriert**: Gibt an, ob das Gerät bei Azure Active Directory registriert ist (dies wird als Arbeitsbereichsverknüpfung bezeichnet).

-   **Kompatibel**: Gibt an, ob das Gerät mit den von Ihnen bereitgestellten Konformitätsrichtlinien kompatibel ist.

-   **Exchange ActiveSync-ID**: Bei IOS- und Android-Geräten muss die Exchange ActiveSync-ID mit der Geräteregistrierung in Azure Active Directory verknüpft sein. Dies erfolgt, wenn ein Benutzer in der Quarantäne-E-Mail den Link zum **Aktivieren von E-Mails** auswählt.

    > [!NOTE]
    > Für Windows Phone-Geräte wird in dieser Spalte immer ein Wert angezeigt.

Bei Geräten, die Teil einer Zielgruppe sind, ist der Zugriff auf Exchange blockiert, sofern die Spaltenwerte nicht mit den in der folgenden Tabelle aufgeführten Werten übereinstimmen:

--------------------------

|                          Verwaltungskanal                          | Bei AAD registriert | Kompatibel | Exchange ActiveSync-ID |    Resultierende Aktion     |
|----------------------------------------------------------------------|----------------|-----------|------------------------|-------------------------|
| <strong>Von Microsoft Intune und Exchange ActiveSync verwaltet</strong> |      Ja        |    Ja     |  Es wird ein Wert angezeigt.  | E-Mail-Zugriff erlaubt |
|                           Beliebiger anderer Wert                            |       Nein       |    Nein     | Es wird kein Wert angezeigt.  | E-Mail-Zugriff blockiert |

----------------------
Sie können den Inhalt des Berichts exportieren und die Benutzer über die in der Spalte **E-Mail-Adresse** enthaltene Adresse informieren, dass sie blockiert werden.

### <a name="step-3-configure-user-groups-for-the-conditional-access-policy"></a>Schritt 3: Konfigurieren von Benutzergruppen für die Richtlinie für bedingten Zugriff
Richtlinien für bedingten Zugriff werden auf verschiedene Azure Active Directory-Sicherheitsgruppen mit Benutzern angewendet. Sie können auch bestimmte Benutzergruppen von dieser Richtlinie für bedingten Zugriff ausnehmen. Bei Benutzern, für die eine Richtlinie gelten soll, muss jedes von ihnen verwendete Gerät die Richtlinie erfüllen, damit sie auf ihre E-Mails zugreifen können.

Sie können diese Gruppen im **Office 365 Admin Center** oder im **Intune-Kontenportal** konfigurieren.

Sie können für jede Richtlinie zwei Arten von Gruppen angeben:

-   **Zielgruppen**: Benutzergruppen, für die die Richtlinie gilt.

-   **Ausgenommene Gruppen**: Benutzergruppen, die von der Richtlinie ausgenommen sind (optional).

Benutzer, die in beiden Gruppen enthalten sind, werden von der Richtlinie ausgenommen.

Es werden nur die Gruppen ausgewertet, für die die Richtlinie für bedingten Zugriff gilt.

### <a name="step-4-configure-the-conditional-access-policy"></a>Schritt 4: Konfigurieren der Richtlinie für bedingten Zugriff

> [!NOTE]
> Sie können eine Richtlinie für bedingten Zugriff auch in der Azure AD-Verwaltungskonsole erstellen. In der Azure AD-Verwaltungskonsole können Sie zusätzlich zu anderen Richtlinien für bedingten Zugriff wie Richtlinien für die mehrstufige Authentifizierung auch Richtlinien für bedingten Zugriff für Intune-Geräte erstellen (die in Azure AD als **gerätebasierte bedingte Zugriffsrichtlinien** bezeichnet werden).
> 
> Sie können auch Richtlinien für bedingten Zugriff für von Azure AD unterstützte Unternehmens-Apps von Drittanbietern festlegen, z. B. Salesforce und Box. Weitere Informationen finden Sie unter [Festlegen von gerätebasierten Azure Active Directory-Richtlinien für bedingten Zugriff zur Steuerung des Zugriffs auf über Azure Active Directory verbundene Anwendungen](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).


1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Richtlinie** > **Bedingter Zugriff** > **Exchange Online-Richtlinie**.

2. Aktivieren Sie auf der Seite **Exchange Online-Richtlinie** die Option **Bedingte Zugriffsrichtlinie für Exchange Online aktivieren**.

   > [!NOTE]
   > Wenn Sie keine Kompatibilitätsrichtlinie bereitgestellt haben, werden Geräte als kompatibel behandelt.
   >
   > Unabhängig vom Konformitätsstatus müssen alle Benutzer, denen die Richtlinie zugewiesen ist, ihre Geräte bei Intune registrieren.

3. Unter **Anwendungszugriff** haben Sie für Apps, die die moderne Authentifizierung verwenden, zwei Möglichkeiten, auszuwählen, auf welche Plattformen die Richtlinie angewendet werden soll. Zu den unterstützten Plattformen gehören Android, iOS, Windows und Windows Phone.

   -   **Alle Plattformen**

       Dies setzt voraus, dass jedes Gerät, das für den Zugriff auf **Exchange Online** verwendet wird, in Intune registriert und mit den Richtlinien kompatibel ist. Jede Clientanwendung, die die **moderne Authentifizierung** verwendet, unterliegt der Richtlinie für bedingten Zugriff. Wenn die Plattform zurzeit von Intune nicht unterstützt wird, ist der Zugriff auf **Exchange Online** blockiert.

       Die Auswahl der Option **Alle Plattformen** bedeutet, dass Azure Active Directory diese Richtlinie auf alle Authentifizierungsanforderungen anwendet, unabhängig von der Plattform, die von der Clientanwendung gemeldet wird. Alle Plattformen müssen registriert und kompatibel sein, mit Ausnahme von:
       *   Windows-Geräten. Diese müssen registriert werden und kompatibel sein, mit der lokalen Active Directory-Domäne verknüpft sein oder beides.
       * Nicht unterstützte Plattformen wie Mac OS Allerdings werden Apps, die die moderne Authentifizierung von diesen Plattformen verwenden, weiterhin blockiert.

   -   **Bestimmte Plattformen**

        Die Richtlinie für bedingten Zugriff gilt für jede Client-App, die die **moderne Authentifizierung** auf den von Ihnen festgelegten Plattformen verwendet.

4. Unter **Outlook Web Access (OWA)** können Sie auswählen, dass der Zugriff auf Exchange Online nur durch die unterstützten Browser Safari (iOS) und Chrome (Android) gestattet sein soll. Der Zugriff von anderen Browsern aus wird blockiert. Die gleichen Plattformeinschränkungen, die Sie für den Anwendungszugriff für Outlook ausgewählt haben, gelten auch hier.

   Auf **Android**-Geräten müssen die Benutzer den Browserzugriff aktivieren. Zu diesem Zweck müssen Endbenutzer die Option **Browserzugriff aktivieren** auf dem registrierten Gerät wie folgt aktivieren:
   1.    Öffnen Sie die **Unternehmensportal-App**.
   2.    Wechseln Sie über die Schaltfläche mit den Auslassungspunkten (...) oder die Schaltfläche „Hardwaremenü“ zur Seite **Einstellungen**.
   3.    Klicken Sie auf die Schaltfläche **Browserzugriff aktivieren**.
   4.    Melden Sie sich im Chrome-Browser aus Office 365 ab, und starten Sie Chrome neu.

   Auf **iOS**- und **Android**-Plattformen stellt Azure Active Directory ein Transport Layer Security-Zertifikat (TLS) für das Gerät aus, das für den Zugriff auf den Dienst verwendet wird, damit es identifiziert werden kann. Das Gerät zeigt den Benutzern das Zertifikat zusammen mit einer Eingabeaufforderung zur Auswahl des Zertifikats an, wie in den folgenden Screenshots dargestellt. Der Benutzer muss dieses Zertifikat auswählen, bevor der Browser weiterhin verwendet werden kann.

   **iOS**

   ![Screenshot der Zertifikataufforderung auf einem iPad](../media/mdm-browser-ca-ios-cert-prompt.png)

   **Android**

   ![Screenshot der Zertifikatseingabeaufforderung auf einem Android-Gerät](../media/mdm-browser-ca-android-cert-prompt.png)

5. Unter **Exchange ActiveSync-Apps** können Sie festlegen, dass der Zugriff auf Exchange Online für nicht kompatible Geräte blockiert wird. Sie können auch auswählen, ob der Zugriff auf E-Mails zugelassen oder blockiert werden soll, wenn das Gerät nicht unter einer unterstützten Plattform ausgeführt wird. Zu den unterstützten Plattformen gehören Android, iOS, Windows und Windows Phone.

   Exchange Active Sync-Apps für **Android for Work**-Geräte:
   -  Nur **Gmail**- und **Nine Work**-Apps im **Arbeitsprofil** werden auf Android for Work-Geräten unterstützt. Damit der bedingte Zugriff auf Android for Work-Geräten funktioniert, müssen Sie ein E-Mail-Profil für die Gmail- oder Nine Work-App bereitstellen und dieses zudem als **erforderliche** Installation bereitstellen.

6. Wählen Sie unter **Zielgruppen** die Active Directory-Sicherheitsgruppen der Benutzer aus, für die die Richtlinie gilt. Sie können dies entweder auf alle Benutzer oder eine ausgewählte Liste von Benutzergruppen ausrichten.
   ![Screenshot der Seite mit der Exchange Online-Richtlinie für bedingten Zugriff, mit den Optionen für Zielgruppen und ausgenommene Gruppen](../media/IntuneSA5eTargetedExemptedGroups.PNG)
   > [!NOTE]
   > Für Benutzer in den **Zielgruppen** werden die Exchange-Regeln und -Richtlinien durch Intune-Richtlinien ersetzt.
   >
   > Exchange erzwingt nur in den folgenden Situationen die Exchange-Regeln zum Zulassen, Blockieren und für die Quarantäne sowie Exchange-Richtlinien:
   >
   > -   Ein Benutzer ist nicht für Intune lizenziert.
   > -   Ein Benutzer ist für Intune lizenziert, gehört aber keiner Sicherheitsgruppe an, die in der Richtlinie für den bedingten Zugriff angegeben ist.

7. Wählen Sie unter **Ausgenommene Gruppen**die Active Directory-Sicherheitsgruppen der Benutzer aus, die von dieser Richtlinie ausgenommen werden. Wenn ein Benutzer sowohl in den Zielgruppen als auch in den ausgenommenen Gruppen enthalten ist, wird er von der Richtlinie ausgenommen.

8. Wenn Sie fertig sind, wählen Sie **Speichern** aus.

-   Die Richtlinie für bedingten Zugriff wird sofort wirksam und muss nicht explizit bereitgestellt werden.

-   Nachdem ein Benutzer ein E-Mail-Konto erstellt hat, wird das Gerät sofort blockiert.

-   Sobald ein blockierter Benutzer das Gerät bei Intune registriert und Probleme mit der Nichtkompatibilität behebt, wird der E-Mail-Zugriff innerhalb von zwei Minuten entsperrt.

-   Wenn der Benutzer die Registrierung seines Geräts aufhebt, wird der E-Mail-Zugriff nach ca. sechs Stunden blockiert.

**Beispielszenarios für die Konfiguration von Richtlinien für bedingten Zugriff zum Schutz des Gerätezugriffs** finden Sie unter [Protect email access example scenarios (Beispielszenarios für den Schutz des E-Mail-Zugriffs)](restrict-email-access-example-scenarios.md).

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Überwachen der Richtlinien für Konformität und bedingten Zugriff

#### <a name="to-view-devices-that-are-blocked-from-exchange"></a>So zeigen Sie Geräte an, die in Exchange blockiert wurden

Wählen Sie im Intune-Dashboard die Kachel **Geräte mit blockiertem Exchange-Zugriff** aus, um die Anzahl der blockierten Geräte und Links zu weiteren Informationen anzuzeigen.
![Screenshot des Intune-Dashboards mit der Anzahl der Geräte, für die der Zugriff auf Exchange blockiert ist](../media/IntuneSA6BlockedDevices.PNG)

## <a name="next-steps"></a>Nächste Schritte
- [Protect access to SharePoint Online (Schützen des Zugriffs auf SharePoint Online)](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

- [Protect access to Skype for Business Online (Schützen des Zugriffs auf Skype for Business Online)](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
