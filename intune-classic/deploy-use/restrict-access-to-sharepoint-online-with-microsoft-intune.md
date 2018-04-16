---
title: "Schützen von SharePoint Online"
description: "Schützen und steuern Sie den Zugriff auf Unternehmensdaten in SharePoint Online mithilfe von bedingtem Zugriff."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2b7285c272efac8eab406393b0b896795fa5d8ed
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="protect-access-to-sharepoint-online-with-microsoft-intune"></a>Schützen des Zugriffs auf SharePoint Online mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Verwenden Sie den bedingten Zugriff von Microsoft Intune, um den Zugriff auf Dateien zu steuern, die in SharePoint Online gespeichert sind.
Der bedingte Zugriff besteht aus zwei Komponenten:
- Einer Gerätekompatibilitätsrichtlinie, die das Gerät erfüllen muss, um als kompatibel bewertet zu werden
- Einer Richtlinie für bedingten Zugriff, in der Sie die Bedingungen festlegen, die das Gerät erfüllen muss, um auf den Dienst zugreifen zu können
Weitere Informationen zur Funktionsweise des bedingten Zugriffs finden Sie im Thema [Protect access to email, O365, and other services (Schützen des Zugriffs auf E-Mail, O365 und andere Dienste)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Sie stellen Benutzern die Richtlinien für Konformität und bedingten Zugriff bereit. Jedes Gerät, das ein Benutzer zum Zugriff auf die Dienste verwendet, wird auf die Einhaltung der Richtlinien überprüft.

Wenn ein Benutzer versucht, mit einer unterstützten App wie z. B. OneDrive auf seinem Gerät eine Verbindung mit einer Datei herzustellen, erfolgt die folgende Auswertung:

![Diagramm zur Veranschaulichung der Entscheidungspunkte, mit denen ermittelt wird, ob ein Gerät Zugriff auf SharePoint erhält oder blockiert wird](../media/ConditionalAccess8-6.png)


**Bevor** Sie eine bedingte Zugriffsrichtlinie für SharePoint Online konfigurieren, müssen folgende Voraussetzungen erfüllt sein:
- Sie müssen über ein **SharePoint Online-Abonnement** verfügen, und Benutzer müssen für SharePoint Online lizenziert sein.
- Sie müssen über ein **Enterprise Mobility + Security- (EMS)** oder **Azure Active Directory (Azure AD) Premium-Abonnement** verfügen, und Benutzer müssen für EMS oder Azure AD lizenziert sein. Weitere Informationen finden Sie in der [Preisübersicht für Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) oder der [Preisübersicht für Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).


  Zum Herstellen einer Verbindung mit den gewünschten Dateien muss das Gerät die folgenden Voraussetzungen erfüllen:
-   Es muss bei Intune oder einem in die Domäne eingebundenen PC **registriert** sein.

-   Es muss in Azure Active Directory **registriert** sein (dies erfolgt automatisch bei der Registrierung des Geräts bei Intune).


-   Es muss mit allen bereitgestellten Konformitätsrichtlinien **kompatibel** sein.

Der Gerätestatus wird in Azure Active Directory gespeichert. Die Anwendung gewährt oder blockiert den Zugriff auf Dateien entsprechend den von Ihnen angegebenen Bedingungen.

Wenn eine Bedingung nicht erfüllt wird, erhält der Benutzer bei der Anmeldung die folgenden Meldungen:

-   Wenn das Gerät nicht bei Intune oder in Azure Active Directory registriert ist, wird eine Meldung mit Anweisungen zum Installieren der Unternehmensportal-App und zum Registrieren des Geräts angezeigt.

-   Wenn das Gerät nicht kompatibel ist, wird eine Meldung angezeigt, die den Benutzer zum Intune-Unternehmensportalwebsite oder zur Unternehmensportal-App weiterleitet. Dort findet der Benutzer Informationen zum Problem und zur Lösung.

**Keine Anwendung des bedingten Zugriffs bei externer Freigabe**. Um zu erfahren, wie die externe Freigabe in Ihrer Mandanten- oder Websitesammlung verhindert werden kann, lesen Sie [Verwalten der externen Freigabe für Ihre SharePoint Online-Umgebung](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85).

>[!NOTE]
>Wenn Sie den bedingten Zugriff für SharePoint Online aktivieren, sollten Sie die Domäne in der Liste wie im Thema [Remove-SPOTenantSyncClientRestriction](https://technet.microsoft.com/library/dn917451.aspx) beschrieben deaktivieren.  

## <a name="support-for-mobile-devices"></a>Unterstützung für mobile Geräte
Die folgenden Betriebssysteme werden unterstützt:
- iOS 8.0 und höher
- Android 4.0 und höher, Samsung KNOX Standard 4.0 oder höher
- Windows Phone 8.1 und höher

Sie können den Zugriff auf SharePoint Online schützen, wenn der Zugriff von **iOS**- und **Android**-Geräten über einen Browser erfolgt. Der Zugriff wird nur von unterstützten Browsern auf kompatiblen Geräten gewährt:
* Safari (iOS)
* Chrome (Android)
* Intune Managed Browser (iOS und Android 5.0 und höher)

**Nicht unterstützte Browser werden blockiert**.

## <a name="support-for-pcs"></a>Unterstützung für PCs
Die folgenden Betriebssysteme werden unterstützt:
- Windows 8.1 und höher (bei Registrierung von PCs mit Intune)
- Windows 7.0, Windows 8.1 oder Windows 10 (bei Einbindung von PCs in eine Domäne)
  > [!NOTE]
  >Damit Sie den bedingten Zugriff auf Windows 10-PCs verwenden können, müssen Sie diese PCs mit dem Windows 10 Anniversary-Update aktualisieren.

  - Sie müssen in die Domäne eingebundene PCs für die [automatische Registrierung](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) bei Azure Active Directory einrichten. Der Azure AD Device Registration-Dienst wird automatisch für Intune und Office 365-Kunden aktiviert. Kunden, die bereits den AD FS Device Registration Service bereitgestellt haben, sehen keine registrierten Geräte im lokalen Active Directory.

  - Wenn die Richtlinie das Beitreten zu einer Domäne erfordert und der PC nicht in die Domäne eingebunden ist, wird die Meldung angezeigt, dass der IT-Administrator kontaktiert werden sollte.

  - Wenn die Richtlinie das Beitreten zu einer Domäne oder Kompatibilität erfordert und der PC keine der Anforderungen erfüllt, wird eine Meldung mit einer Anleitung zum Installieren der Unternehmensportal-App und zur Registrierung angezeigt.
    >[!NOTE]
    >Bedingter Zugriff wird nicht auf PCs unterstützt, auf denen der Intune Computerclient-Agent ausgeführt wird.

[Die moderne Authentifizierung von Office 365 muss aktiviert sein](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) und alle neuesten Office-Updates enthalten.

Die moderne Authentifizierung ermöglicht Windows-Clients mit Office 2013 eine ADAL-basierte Anmeldung (Active Directory Authentication Library) und bietet größere Sicherheit durch **mehrstufige Authentifizierung** und **zertifikatbasierte Authentifizierung**.


## <a name="configure-conditional-access-for-sharepoint-online"></a>Konfigurieren des bedingten Zugriffs für SharePoint Online

### <a name="step-1-configure-active-directory-security-groups"></a>Schritt 1: Konfigurieren von Active Directory-Sicherheitsgruppen
Bevor Sie beginnen, konfigurieren Sie Azure Active Directory-Sicherheitsgruppen für die bedingte Zugriffsrichtlinien. Sie können diese Gruppen im **Office 365 Admin Center** oder im **Intune-Kontenportal** konfigurieren. Sie verwenden diese Gruppen, um die Richtlinie auf Benutzer anzuwenden oder Benutzer von der Richtlinie auszunehmen. Bei Benutzern, für die eine Richtlinie gelten soll, muss jedes von ihnen verwendete Gerät die Richtlinie erfüllen, damit sie auf Ressourcen zugreifen können.

Sie können zwei Arten von Gruppentypen in einer SharePoint Online-Richtlinie angeben:

-   **Zielgruppen**: Gruppen von Benutzern, für die die Richtlinie gilt.

-   **Ausgenommene Gruppen**: Gruppen von Benutzern, die von der Richtlinie ausgenommen sind.

Benutzer, die in beiden Gruppen enthalten sind, werden von der Richtlinie ausgenommen.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Schritt 2: Konfigurieren und Bereitstellen einer Konformitätsrichtlinie
Falls noch nicht geschehen, erstellen Sie eine Kompatibilitätsrichtlinie und stellen Sie sie für die Benutzer bereit, auf die die SharePoint Online-Richtlinie angewendet werden soll.

> [!NOTE]
> Kompatibilitätsrichtlinien werden für Intune-Gruppen bereitgestellt, Richtlinien für bedingten Zugriff dagegen werden auf Azure Active Directory-Sicherheitsgruppen angewendet.

Ausführliche Informationen zum Konfigurieren der Kompatibilitätsrichtlinie finden Sie unter [Erstellen einer Kompatibilitätsrichtlinie](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT]
> Wenn Sie keine Kompatibilitätsrichtlinie bereitgestellt haben, werden die Geräte als kompatibel ausgewertet.

Fahren Sie anschließend mit **Schritt 3** fort.

### <a name="step-3-configure-the-sharepoint-online-policy"></a>Schritt 3: Konfigurieren der SharePoint Online-Richtlinie
Anschließend konfigurieren Sie die Richtlinie so, dass nur verwaltete und konforme Geräte auf SharePoint Online zugreifen dürfen. Diese Richtlinie wird in Azure Active Directory gespeichert.

#### <a name="bkmk_spopolicy"></a>

>[!NOTE]
> Sie können für Intune-Geräte in der Azure AD-Verwaltungskonsole auch eine Richtlinie für bedingten Zugriff erstellen (die Richtlinie wird in Azure AD als **Richtlinie für gerätebasierten bedingten Zugriff** bezeichnet). Darüber hinaus können Sie andere Richtlinien für bedingten Zugriff erstellen, z. B. mehrstufige Authentifizierung. Sie können auch Richtlinien für bedingten Zugriff für von Azure AD unterstützte Unternehmens-Apps von Drittanbietern festlegen, z. B. Salesforce und Box. Weitere Informationen finden Sie unter [Festlegen von gerätebasierten Azure Active Directory-Richtlinien für bedingten Zugriff zur Steuerung des Zugriffs auf über Azure Active Directory verbundene Anwendungen](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).


1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Richtlinie** > **Bedingter Zugriff** > **SharePoint Online-Richtlinie** aus.
   ![Screenshot der Seite mit der SharePoint Online-Richtlinie](../media/mdm-ca-spo-policy-configuration.png)

2. Wählen Sie **Richtlinie für bedingten Zugriff für SharePoint Online aktivieren** aus.

3. Unter **Anwendungszugriff** können Sie optional die Richtlinie für bedingten Zugriff auf Folgendes anwenden:

   - **Alle Plattformen**

     Dies setzt voraus, dass jedes Gerät, das für den Zugriff auf **SharePoint Online** verwendet wird, in Intune registriert und mit den Richtlinien kompatibel ist. Jede Clientanwendung, die die **moderne Authentifizierung** verwendet, unterliegt der Richtlinie für bedingten Zugriff. Wenn die Plattform zurzeit von Intune nicht unterstützt wird, ist der Zugriff auf **SharePoint** blockiert.

     Die Auswahl der Option **Alle Plattformen** bedeutet, dass Azure Active Directory diese Richtlinie auf alle Authentifizierungsanforderungen anwendet, unabhängig von der Plattform, die von der Clientanwendung gemeldet wird. Alle Plattformen müssen registriert und kompatibel sein, mit Ausnahme von:
     *   Windows-Geräten. Diese müssen registriert werden und kompatibel sein, mit der lokalen Active Directory-Domäne verknüpft sein oder beides.
     * nicht unterstützten Plattformen wie Mac. Allerdings werden Apps, die die moderne Authentifizierung von diesen Plattformen verwenden, weiterhin blockiert.

   - **Bestimmte Plattformen**

      Die Richtlinie für bedingten Zugriff wird auf jede Client-App angewendet, die die moderne Authentifizierung auf den von Ihnen festgelegten Plattformen verwendet.

     Bei Windows-PCs muss ein PC entweder in die Domäne eingebunden oder bei Intune registriert und konform sein. Sie können die folgenden Anforderungen festlegen:

     -   **Geräte müssen in eine Domäne eingebunden oder kompatibel sein.** Wählen Sie diese Option aus, wenn Sie festlegen möchten, dass die PCs entweder in die Domäne eingebunden oder mit den in Intune festgelegten Richtlinien konform sein müssen. Wenn ein PC keine der Anforderungen erfüllt, wird der Benutzer aufgefordert, das Gerät bei Intune zu registrieren.

     -   **Geräte müssen kompatibel sein.** Wählen Sie diese Option aus, wenn Sie festlegen möchten, dass PCs bei Intune registriert und kompatibel sein müssen. Wenn ein PC nicht registriert ist, wird eine Meldung mit Anweisungen zur Registrierung angezeigt.

4. Unter **Browserzugriff** auf SharePoint Online und OneDrive for Business können Sie auswählen, dass der Zugriff auf Exchange Online ausschließlich über unterstützte Browser gewährt werden soll: Safari (iOS) und Chrome (Android). Der Zugriff von anderen Browsern aus wird blockiert. Die gleichen Plattformeinschränkungen, die Sie für den Anwendungszugriff für OneDrive ausgewählt haben, gelten auch hier.

   Auf **Android**-Geräten müssen die Benutzer den Browserzugriff aktivieren. Zu diesem Zweck müssen Benutzer die Option **Browserzugriff aktivieren** auf dem registrierten Gerät wie folgt aktivieren:
   1.    Öffnen Sie die **Unternehmensportal**-App.
   2.    Wechseln Sie über die Schaltfläche mit den Auslassungspunkten (...) oder die Schaltfläche „Hardwaremenü“ zur Seite **Einstellungen**.
   3.    Klicken Sie auf die Schaltfläche **Browserzugriff aktivieren**.
   4.    Melden Sie sich im Chrome-Browser aus Office 365 ab, und starten Sie Chrome neu.

   Auf **iOS**- und **Android**-Plattformen stellt Azure Active Directory ein Transport Layer Security-Zertifikat (TLS) für das Gerät aus, das für den Zugriff auf den Dienst verwendet wird, damit es identifiziert werden kann. Das Gerät zeigt den Benutzern das Zertifikat zusammen mit einer Eingabeaufforderung zur Auswahl des Zertifikats an, wie in den folgenden Screenshots dargestellt. Der Benutzer muss dieses Zertifikat auswählen, bevor der Browser verwendet werden kann.

   **iOS**

   ![Screenshot der Zertifikataufforderung auf einem iPad](../media/mdm-browser-ca-ios-cert-prompt.png)

   **Android**

   ![Screenshot der Zertifikataufforderung auf einem Android-Gerät](../media/mdm-browser-ca-android-cert-prompt.png)
5. Klicken Sie unter **Zielgruppen** auf **Ändern**, um die Azure Active Directory-Sicherheitsgruppen auszuwählen, für die die Richtlinie gelten soll. Sie können dies für alle Benutzer oder nur für eine ausgewählte Benutzergruppe festlegen.

6. Wählen Sie unter **Exempted Groups** (Ausgenommene Gruppen) optional **Ändern**, um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die von dieser Richtlinie ausgenommen werden.

7. Wenn Sie fertig sind, wählen Sie **Speichern** aus.

Die Richtlinie für bedingten Zugriff wird sofort wirksam und muss nicht explizit bereitgestellt werden.

### <a name="step-4-monitor-the-compliance-and-conditional-access-policies"></a>Schritt 4: Überwachen der Richtlinien für Kompatibilität und bedingten Zugriff
Im Arbeitsbereich **Gruppen** können Sie den Status Ihrer Geräte anzeigen.

Wählen Sie eine beliebige Gruppe von Mobilgeräten aus. Wählen Sie dann auf der Registerkarte **Geräte** einen der folgenden **Filter** aus:

-   **Geräte, die nicht bei AAD registriert sind**. Diesen Geräten wird der Zugriff auf SharePoint Online verweigert.

-   **Geräte, die nicht kompatibel sind**. Diesen Geräten wird der Zugriff auf SharePoint Online verweigert.

-   **Geräte, die bei AAD registriert und kompatibel sind**. Diese Geräten können auf SharePoint Online zugreifen.

### <a name="see-also"></a>Siehe auch
[Protect access to email and O365 services with Microsoft Intune (Schützen des Zugriffs auf E-Mail- und Office 365-Dienste mit Microsoft Intune)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
