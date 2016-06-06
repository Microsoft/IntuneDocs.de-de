---
# required metadata

title: Beschränken des E-Mail-Zugriffs auf Exchange Online- und neue Exchange Online Dedicated-Umgebungen | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Beschränken des E-Mail-Zugriffs auf Exchange Online- und neue Exchange Online Dedicated-Umgebungen mit Intune

Wenn Sie über eine Exchange Online Dedicated-Umgebung verfügen und herausfinden müssen, ob es sich um die neue oder die ältere Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer.

Um den E-Mail-Zugriff auf Exchange Online oder die neue Exchange Online Dedicated-Umgebung zu steuern, konfigurieren Sie den bedingten Zugriff für Exchange Online in Intune.
Weitere Informationen zur Funktionsweise des bedingten Zugriffs finden Sie im Artikel [Beschränken des Zugriffs auf E-Mail- und Office 365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

>[!IMPORTANT]
>Der bedingte Zugriff für PCs und Windows 10 Mobile-Geräte mit Apps, die die moderne Authentifizierung verwenden, steht zurzeit nicht für alle Intune-Kunden zur Verfügung. Wenn Sie diese Funktionen bereits verwenden, müssen Sie keine weiteren Maßnahmen ergreifen. Sie können diese weiter verwenden.

>Wenn Sie keine Richtlinien für bedingten Zugriff für PCs oder Windows 10 Mobile-Geräte mit Apps, die die moderne Authentifizierung verwenden, erstellt haben und dies jetzt tun möchten, müssen Sie eine Anforderung übermitteln.  Allgemeine Informationen, Informationen zu bekannten Problemen sowie Informationen zum Zugriff auf dieses Feature finden Sie auf der [Microsoft Connect-Website](http://go.microsoft.com/fwlink/?LinkId=761472)..

**Bevor** Sie den bedingten Zugriff konfigurieren können, müssen folgende Voraussetzungen erfüllt sein:

-   Sie müssen über ein **Office 365-Abonnement verfügen, das Exchange Online (z. B. E3)** umfasst, und die Benutzer müssen für Exchange Online lizenziert sein.

-  Sie sollten erwägen, den optionalen **Microsoft Intune Service to Service Connector** zu konfigurieren, der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] mit Microsoft Exchange Online verbindet und die Verwaltung von Geräteinformationen über die [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-Konsole ermöglicht. Der Connector ist zur Verwendung von Kompatibilitätsrichtlinien oder Richtlinien für den bedingten Zugriff nicht zwingend erforderlich, Sie benötigen ihn aber zum Ausführen von Berichten, mit deren Hilfe die Auswirkungen des bedingten Zugriffs bewertet werden.

   > [!NOTE]
   > Konfigurieren Sie den Service to Service Connector nicht, wenn Sie beabsichtigen, bedingten Zugriff für Exchange Online und lokales Exchange zu verwenden.

   Informationen zum Konfigurieren des Connectors finden Sie unter [Intune Service to Service Connector](intune-service-to-service-exchange-connector.md).

Wenn Richtlinien für bedingten Zugriff konfiguriert und auf einen Benutzer angewendet wurden, muss das **Gerät**, das der Benutzer zum Abrufen von E-Mails verwendet, folgende Voraussetzungen erfüllen:

-   Es muss bei [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] **registriert** sein oder sich um einen in die Domäne eingebundenen PC handeln.

-  **Es muss in Azure Active Directory registriert sein**. Die erfolgt automatisch, wenn das Gerät bei [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] registriert ist. Darüber hinaus muss die Exchange ActiveSync-ID des Clients in Azure Active Directory registriert sein.

  AAD DRS wird automatisch für Intune und Office 365-Kunden aktiviert. Kunden, die bereits den AD FS Device Registration Service bereitgestellt haben, sehen keine registrierten Geräte in ihrem lokalen Active Directory.

-   Es muss mit allen [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-Kompatibilitätsrichtlinien **kompatibel** sein, die auf diesem Gerät bereitgestellt wurden, oder es muss einer lokalen Domäne beigetreten sein.

Wenn eine Richtlinie für bedingten Zugriff nicht erfüllt wird, erhält der Benutzer bei der Anmeldung eine der folgenden Meldungen:

- Wenn das Gerät nicht bei [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] oder in Azure Active Directory registriert ist, wird eine Meldung mit Anweisungen zum Installieren der Unternehmensportal-App, zum Registrieren des Geräts und zum Aktivieren des E-Mail-Zugriffs angezeigt. Dieser Prozess verknüpft auch die Exchange ActiveSync-ID mit dem Eintrag in Azure Active Directory.

-   Wenn das Gerät als nicht kompatibel mit den Kompatibilitätsrichtlinien ausgewertet wird, wird der Endbenutzer zur [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-Unternehmensportalwebsite oder zur Unternehmensportal-App weitergeleitet. Dort findet der Endbenutzer Informationen zum Problem und zur Lösung.


Das folgende Diagramm veranschaulicht den Ablauf, der von den Richtlinien für bedingten Zugriff für Exchange Online verwendet wird.

![Diagramm zur Veranschaulichung der Entscheidungspunkte, die bestimmen, ob der Zugriff für das Gerät zugelassen oder blockiert wird](../media/ConditionalAccess8-1.png)

## Unterstützung für mobile Geräte
Sie können den Zugriff auf Exchange Online-E-Mails über **Outlook** und andere ** Apps, die die moderne Authentifizierung verwenden**, beschränken:

- Android 4.0 und höher, Samsung KNOX Standard 4.0 und höher
- iOS 7.1 und höher
- Windows Phone 8.1 und höher

 Die **moderne Authentifizierung** ermöglicht das ADAL-basierte (Active Directory Authentication Library) Anmelden für Microsoft Office-Clients.

> -   Die ADAL-basierte Authentifizierung ermöglicht Office-Clients die Einbindung in die browserbasierte Authentifizierung (auch als passive Authentifizierung bekannt).  Der Benutzer wird zur Authentifizierung zu einer Anmeldewebseite umgeleitet. Diese neue Anmeldemethode bietet größere Sicherheit durch **mehrstufige Authentifizierung** und **zertifikatbasierte Authentifizierung**.
> Dieser [Artikel](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) enthält weitere ausführliche Informationen zur Funktionsweise der modernen Authentifizierung.


Auf folgenden Plattformen können Sie den Zugriff auf Exchange-E-Mails über den integrierten **Exchange ActiveSync-E-Mail-Client** blockieren:

- Android 4.0 und höher, Samsung KNOX Standard 4.0 und höher

- iOS 7.1 und höher

- Windows Phone 8.1 und höher

## Unterstützung für PCs

Sie können den bedingten Zugriff für PCs einrichten, auf denen Office-Desktopanwendungen ausgeführt werden, um auf **Exchange Online** und **SharePoint Online** zuzugreifen. Dies gilt für PCs, die folgende Anforderungen erfüllen:

-   Auf dem PC muss Windows 7.0 oder Windows 8.1 ausgeführt werden.

-   Der PC muss entweder in die Domäne eingebunden oder mit den Kompatibilitätsrichtlinien kompatibel sein.

    Damit der PC als kompatibel bewertet wird, muss er bei [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] registriert sein und den Richtlinien entsprechen.

    Für in die Domäne eingebundene PCs müssen Sie das Gerät für eine [automatische Registrierung](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) bei Azure Active Directory einrichten.

-   [Die moderne Authentifizierung von Office 365 muss aktiviert sein](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) und alle neuesten Office-Updates enthalten.

    Die moderne Authentifizierung ermöglicht Windows-Clients mit Office 2013 eine ADAL-basierte Anmeldung (Active Directory Authentication Library) und bietet größere Sicherheit durch **mehrstufige Authentifizierung** und **zertifikatbasierte Authentifizierung**..

-   Setup-ADFS beansprucht Regeln zum Blockieren von nicht moderner Authentifizierungsprotokolle. Detaillierte Anleitungen werden in Szenario 3 beschrieben: [Blockieren des gesamten Zugriffs auf Office 365 außer durch browserbasierte Anwendungen](https://technet.microsoft.com/library/dn592182.aspx)..

## Konfigurieren des bedingten Zugriffs
### Schritt 1: Konfigurieren und Bereitstellen einer Konformitätsrichtlinie
Stellen Sie sicher, dass Sie eine Kompatibilitätsrichtlinie für die Benutzergruppen [erstellen](create-a-device-compliance-policy-in-microsoft-intune.md) und [bereitstellen](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md), für die auch die Richtlinie für bedingten Zugriff gelten soll.


> [!IMPORTANT]
> Wenn Sie keine Kompatibilitätsrichtlinie bereitgestellt haben, werden die Geräte als kompatibel bewertet und erhalten Zugriff auf Exchange.

### Schritt 2: Bewerten der Auswirkungen der Richtlinie für bedingten Zugriff
Mithilfe der **Inventurberichte für mobile Geräte** können Sie ermitteln, für welche Geräte der Zugriff auf Exchange blockiert wird, nachdem Sie die Richtlinie für bedingten Zugriff konfiguriert haben.

Konfigurieren Sie dafür eine Verbindung zwischen [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und Exchange mithilfe des [Microsoft Intune Service to Service Connectors](intune-service-to-service-exchange-connector.md)..
1.  Navigieren Sie zu **Berichte -> Inventurberichte für mobile Geräte**..
![Screenshot Seite mit dem Inventurbericht für mobile Geräte](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  Wählen Sie in den Berichtsparametern die auszuwertende [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-Gruppe sowie gegebenenfalls die Geräteplattformen aus, auf denen die Richtlinie angewendet werden soll.
3.  Nachdem Sie die Kriterien ausgewählt haben, die den Anforderungen Ihres Unternehmens entsprechen, wählen Sie **Bericht anzeigen** aus..
Die Berichtsanzeige wird in einem neuen Fenster geöffnet.
![Screenshot eines Beispielinventurberichts für mobile Geräte](../media/IntuneSA2cViewReport.PNG)

Überprüfen Sie nach der Ausführung des Berichts die folgenden vier Spalten auf blockierte Benutzer:

-   **##Verwaltungskanal** – Gibt an, ob das Gerät durch Intune und/oder Exchange ActiveSync verwaltet wird.

-   **Bei AAD registriert** – Gibt an, ob das Gerät bei Azure Active Directory registriert ist (dies wird als Arbeitsbereichsverknüpfung bezeichnet).

-   **Kompatibel** – Gibt an, ob das Gerät mit den von Ihnen bereitgestellten Konformitätsrichtlinien kompatibel ist.

-   **##Exchange ActiveSync-ID** – Bei IOS- und Android-Geräten muss die Exchange ActiveSync-ID mit der Geräteregistrierung in Azure Active Directory verknüpft sein. Dies erfolgt, wenn der Benutzer in der Quarantäne-E-Mail den Link zum **Aktivieren von E-Mails** auswählt.

    > [!NOTE]
    > Für Windows Phone-Geräte wird in dieser Spalte immer ein Wert angezeigt.

Bei Geräten, die Teil einer Zielgruppe sind, ist der Zugriff auf Exchange blockiert, sofern die Spaltenwerte nicht mit den in der folgenden Tabelle aufgeführten Werten übereinstimmen:

--------------------------
|Verwaltungskanal|Bei AAD registriert|Kompatibel|Exchange ActiveSync-ID|Resultierende Aktion|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Von Microsoft Intune und Exchange ActiveSync verwaltet**|Ja|Ja|Es wird ein Wert angezeigt.|E-Mail-Zugriff erlaubt|
|Beliebiger anderer Wert|Nein|Nein|Es wird kein Wert angezeigt.|E-Mail-Zugriff blockiert|
----------------------
Sie können den Inhalt des Berichts exportieren und die Benutzer über die in der Spalte **E-Mail-Adresse** enthaltene Adresse informieren, dass sie blockiert werden.

### Schritt 3: Konfigurieren von Benutzergruppen für die Richtlinie für bedingten Zugriff
Richtlinien für bedingten Zugriff werden auf verschiedene Azure Active Directory-Sicherheitsgruppen mit Benutzern angewendet. Sie können auch bestimmte Benutzergruppen von dieser Richtlinie ausnehmen.  Bei Benutzern, für die eine Richtlinie gelten soll, muss jedes von ihnen verwendete Gerät die Richtlinie erfüllen, damit sie auf ihre E-Mails zugreifen können.

Sie können diese Gruppen im **Office 365 Admin Center**oder **Intune-Kontenportal** konfigurieren..

Sie können für jede Richtlinie zwei Arten von Gruppen angeben:

-   **Zielgruppen** – Benutzergruppen, auf die die Richtlinie angewendet wird

-   **Ausgenommene Gruppen** – Benutzergruppen, die von der Richtlinie ausgenommen sind (optional)

Benutzer, die in beiden Gruppen enthalten sind, werden von der Richtlinie ausgenommen.

Es werden nur die Gruppen ausgewertet, für die die Richtlinie für bedingten Zugriff gilt.

### Schritt 4: Konfigurieren der Richtlinie für bedingten Zugriff

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** > **Bedingter Zugriff** > **Exchange Online-Richtlinie**..
![Screenshot der Seite mit der Exchange Online-Richtlinie für bedingten Zugriff](../media/IntuneSA5dExchangeOnlinePolicy.png)

2.  Aktivieren Sie auf der Seite **Exchange Online-Richtlinie** die Option **Richtlinie für bedingten Zugriff für Exchange Online aktivieren**..

    > [!NOTE]
    > Wenn Sie keine Kompatibilitätsrichtlinie bereitgestellt haben, werden Geräte als kompatibel ausgewertet.
    >
    > Unabhängig vom Kompatibilitätsstatus müssen alle Benutzer, für die die Richtlinie gilt, ihre Geräte bei Intune registrieren. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

3.  Unter **Anwendungszugriff** haben Sie für Apps, die die moderne Authentifizierung verwenden, zwei Möglichkeiten, auszuwählen, auf welche Plattformen die Richtlinie angewendet werden soll. Zu den unterstützten Plattformen gehören Android, iOS, Windows und Windows Phone.

    -   **Alle Plattformen**

        Dies setzt voraus, dass jedes Gerät, das für den Zugriff auf **Exchange Online** verwendet wird, in Intune registriert und kompatibel zu den Richtlinien ist.  Jede Clientanwendung, die die **moderne Authentifizierung** verwendet, unterliegt der Richtlinie für den bedingten Zugriff, und wenn die Plattform gegenwärtig nicht von Intune unterstützt wird, wird der Zugriff auf **Exchange Online** blockiert.
        >[!TIP]
           Wenn Sie den bedingten Zugriff für PCs nicht bereits verwenden, wird Ihnen diese Option möglicherweise nicht angezeigt.  Verwenden Sie stattdessen die Option **Spezifische Plattformen**, Der bedingte Zugriff für PCs steht zurzeit nicht allen Intune-Kunden zur Verfügung.   Allgemeine Informationen, Informationen zu bekannten Problemen sowie Informationen zum Zugriff auf dieses Feature finden Sie auf der [Microsoft Connect-Website](http://go.microsoft.com/fwlink/?LinkId=761472)..

    -   **Bestimmte Plattformen**

         Die Richtlinie für bedingten Zugriff wird auf jede Client-App angewendet, die die **moderne Authentifizierung** auf den von Ihnen festgelegten Geräteplattformen verwendet.

4.  Unter **Exchange ActiveSync-Apps** können Sie festlegen, dass der Zugriff auf Exchange Online für nicht kompatible Geräte blockiert wird. Sie können auch auswählen, ob der Zugriff auf E-Mails zugelassen oder blockiert werden soll, wenn das Gerät nicht unter einer unterstützten Plattform ausgeführt wird. Zu den unterstützten Plattformen gehören Android, iOS, Windows und Windows Phone.


5.  Wählen Sie unter **Zielgruppen**die Active Directory-Sicherheitsgruppen der Benutzer aus, auf die die Richtlinie angewendet wird. Sie können dies entweder auf alle Benutzer oder eine ausgewählte Liste von Benutzergruppen ausrichten.
![Screenshot der Seite mit der Exchange Online-Richtlinie für bedingten Zugriff, mit den Optionen für Zielgruppen und ausgenommene Gruppen](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE]
    > Für Benutzer in den **Zielgruppen** werden die Exchange-Regeln und -Richtlinien durch Intune-Richtlinien ersetzt.
    >
    > Exchange erzwingt nur in den folgenden Situationen die Exchange-Regeln für Zulassung, Blockierung und Quarantäne sowie Exchange-Richtlinien:
    >
    > -   Der Benutzer ist nicht für Intune lizenziert.
    > -   Der Benutzer ist für Intune lizenziert, gehört aber keiner Sicherheitsgruppe an, die in der Richtlinie für den bedingten Zugriff angegeben ist.

6.  Wählen Sie unter **Ausgenommene Gruppen**die Active Directory-Sicherheitsgruppen der Benutzer aus, die von dieser Richtlinie ausgenommen werden. Wenn ein Benutzer sowohl in den Zielgruppen als auch in den ausgenommenen Gruppen enthalten ist, wird er von der Richtlinie ausgenommen.

7.  Wählen Sie abschließend **Speichern** aus..

-   Die Richtlinie für bedingten Zugriff wird sofort wirksam und muss nicht explizit bereitgestellt werden.

-   Nachdem ein Benutzer ein E-Mail-Konto erstellt hat, wird das Gerät sofort blockiert.

-   Sobald ein blockierter Benutzer das Gerät bei [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] registriert und Probleme mit der Nichtkompatibilität behebt, wird der E-Mail-Zugriff innerhalb von 2 Minuten entsperrt.

-   Wenn der Benutzer die Registrierung seines Geräts aufhebt, wird der E-Mail-Zugriff nach ca. 6 Stunden blockiert.

**Beispielszenarien für die Konfiguration von Richtlinien für bedingten Zugriff, um den Gerätezugriff zu beschränken, finden Sie unter [Beispielszenarien für die Beschränkung des E-Mail-Zugriffs](restrict-email-access-example-scenarios.md)..**

## Überwachen der Richtlinien für Konformität und bedingten Zugriff

#### So zeigen Sie Geräte an, die in Exchange blockiert wurden

Wählen Sie im [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-Dashboard die Kachel **Geräte mit blockiertem Exchange-Zugriff** aus, um die Anzahl der blockierten Geräte und Links zu weiteren Informationen anzuzeigen.
![Screenshot des Intune-Dashboards mit der Anzahl der Geräte, für die der Zugriff auf Exchange blockiert ist](../media/IntuneSA6BlockedDevices.PNG)

## Nächste Schritte
[Beschränken des Zugriffs auf SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Beschränken des Zugriffs auf Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->

