---
title: Erstellen einer Richtlinie für bedingten Zugriff auf Exchange
titleSuffix: Microsoft Intune
description: Konfigurieren Sie den bedingten Zugriff für Exchange lokal und für das ältere Exchange Online Dedicated in Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: stama
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c18da57282a190dec363e3dfbde5293f5228cb0b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504620"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Erstellen einer Richtlinie für bedingten Zugriff auf Exchange lokal und das ältere Exchange Online Dedicated

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel wird erläutert, wie Sie den bedingten Zugriff für Exchange lokal basierend auf der Gerätekonformität konfigurieren.

Wenn Sie über eine Exchange Online Dedicated-Umgebung verfügen und herausfinden müssen, ob es sich um die neue oder die ältere Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer. Um den E-Mail-Zugriff auf Exchange lokal oder Ihre ältere Exchange Online Dedicated-Umgebung zu steuern, konfigurieren Sie den bedingten Zugriff für Exchange lokal in Intune.

## <a name="before-you-begin"></a>Vorbereitung

Bevor Sie den bedingten Zugriff konfigurieren, überprüfen Sie, ob folgende Konfigurationen vorhanden sind:

- Bei Ihrer Exchange-Version handelt es sich um **Exchange 2010 SP1 oder höher**. Exchange Server-Clientzugriffsserver-Arrays werden unterstützt.

- Der [Exchange Active Sync-Connector für Exchange lokal](exchange-connector-install.md), der Intune mit Exchange lokal verbindet, ist installiert und wird verwendet.

    >[!IMPORTANT]  
    >Intune unterstützt mehrere lokale Exchange Connectors pro Abonnement.  Jeder Connector für Exchange lokal gilt spezifisch für einen bestimmten Intune-Mandanten und kann für keinen anderen Mandanten verwendet werden.  Wenn Sie über mehr als eine lokale Exchange-Organisation verfügen, können Sie einen separaten Connector für jede Exchange-Organisation einrichten.

- Der Connector für eine Organisation mir Exchange lokal kann auf jedem Computer installiert werden, solange dieser Computer mit dem Exchange-Server kommunizieren kann.

- Der Connector unterstützt die **Exchange-Clientzugriffsserver-Umgebung**. Intune unterstützt die direkte Installation des Connectors auf dem Exchange-CAS-Server. Aufgrund der zusätzlichen Last auf dem Server wird aber empfohlen, den Connector auf einem separaten Computer zu installieren. Sie müssen den Connector so konfigurieren, dass er mit einem der Exchange-Clientzugriffsserver kommuniziert.

- **Exchange ActiveSync** muss für die zertifikatbasierte Authentifizierung oder die Eingabe von Anmeldeinformationen durch Benutzer konfiguriert werden.

- Wenn Richtlinien für bedingten Zugriff konfiguriert und auf einen Benutzer angewendet wurden, muss das **Gerät**, das der Benutzer zum Abrufen von E-Mails verwendet, folgende Voraussetzungen erfüllen:
  - Es muss bei Intune **registriert** sein oder sich um einen in die Domäne eingebundenen PC handeln.
  - **Es muss in Azure Active Directory registriert sein**. Darüber hinaus muss die Exchange ActiveSync-ID des Clients in Azure Active Directory registriert sein.

- Der Azure AD Device Registration-Dienst wird automatisch für Intune und Office 365-Kunden aktiviert. Kunden, die den AD FS Device Registration Service bereitgestellt haben, sehen keine registrierten Geräte in ihrem lokalen Active Directory. **Dies gilt nicht für Windows-PCs und Windows Phone-Geräte.**

- Es besteht **Konformität** mit allen für das Gerät festgelegten Konformitätsrichtlinien.

- Wenn das Gerät die Einstellungen für den bedingten Zugriff nicht erfüllt, erhält der Benutzer bei der Anmeldung eine der folgenden Meldungen:
  - Wenn das Gerät nicht bei Intune oder in Azure Active Directory registriert ist, wird eine Meldung mit Anweisungen zum Installieren der Unternehmensportal-App, zum Registrieren des Geräts und zum Aktivieren des E-Mail-Zugriffs angezeigt. Dieser Prozess verknüpft auch die Exchange ActiveSync-ID mit dem Eintrag des Geräts in Azure Active Directory.
  - Wenn das Gerät nicht konform ist, wird eine Meldung angezeigt, die Benutzer zur Intune-Unternehmensportal-Website oder zur Unternehmensportal-App weiterleitet. Dort finden sie Informationen zum Problem und zu dessen Lösung.

### <a name="support-for-mobile-devices"></a>Unterstützung für mobile Geräte

- Windows Phone 8.1 und höher
- Systemeigene E-Mail-App unter iOS.
- EAS-E-Mail-Clients wie Gmail unter Android 4 oder höher.
- EAS-E-Mail-Clients für **Android-Arbeitsprofilgeräte:** Nur **Gmail** und **Nine Work for Android Enterprise** im **Arbeitsprofil** werden auf Android-Arbeitsprofilgeräten unterstützt. Damit der bedingte Zugriff mit Android-Arbeitsprofilen funktioniert, müssen Sie ein E-Mail-Profil für die Gmail- oder Nine Work for Android Enterprise-App erstellen und diese Apps als erforderliche Installation bereitstellen.

> [!NOTE]
> Microsoft Outlook für Android und iOS wird nicht über den lokalen Exchange-Connector unterstützt. Wenn Sie Richtlinien für den bedingten Azure Active Directory-Zugriff und Intune-App-Schutzrichtlinien mit Outlook für iOS und Android für Ihre lokale Postfächer nutzen möchten, lesen Sie [Verwendung der modernen Hybridauthentifizierung mit Outlook für iOS und Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). 

### <a name="support-for-pcs"></a>Unterstützung für PCs

Die native **E-Mail**-Anwendung unter Windows 8.1 und höher (bei Registrierung bei MDM mit Intune)

## <a name="configure-exchange-on-premises-access"></a>Konfigurieren des Zugriffs auf Exchange lokal

Bevor Sie das folgende Verfahren zum Einrichten der Zugriffssteuerung für Exchange lokal ausführen können, müssen Sie mindestens einen [Intune-Connector für Exchange lokal](exchange-connector-install.md) einrichten.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

2. Wechseln Sie zu **Exchange-Zugriff**, und klicken Sie auf **Zugriff auf Exchange lokal**. 

3. Klicken Sie im Bereich **Zugriff auf Exchange lokal** auf die Option **Ja**, um *die Zugriffssteuerung von Exchange lokal zu aktivieren*.

4. Klicken Sie unter **Zuweisung** auf **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen**, und wählen Sie mindestens eine Gruppe aus, um den Zugriff zu konfigurieren. 

   Die Richtlinie für bedingten Zugriff für Exchange lokal wird auf die Mitglieder der von Ihnen ausgewählten Gruppen angewendet. Benutzer, die diese Richtlinie erhalten, müssen ihre Geräte bei Intune registrieren und die Anforderungen der Konformitätsprofile erfüllen, bevor sie auf Exchange lokal zugreifen können.

5. Um Gruppen auszuschließen, klicken Sie auf **Wählen Sie die Gruppen aus, die ausgeschlossen werden sollen**, und wählen Sie mindestens eine Gruppe aus, die für den Zugriff auf Exchange lokal von den Anforderungen zum Registrieren von Geräten und Einhalten der Konformitätsprofile ausgenommen werden sollen. 

6. Als Nächstes konfigurieren Sie Einstellungen für den Intune-Connector für Exchange lokal.  Klicken Sie im **Exchange-Zugriffsbereich** unter **Setup** auf **Lokaler Connector für Exchange ActiveSync**, und wählen Sie den Connector für die Exchange-Organisation aus, den Sie konfigurieren möchten.

7. Klicken Sie unter **Einstellungen** auf **Benutzerbenachrichtigungen**, um die Standard-E-Mail-Nachricht zu ändern, die an Benutzer gesendet wird, wenn diese auf Exchange lokal zugreifen möchten, ihre Geräte aber nicht konform sind. Die Nachrichtenvorlage verwendet Markupsprache.  Sie sehen während der Eingabe auch eine Vorschau der Nachricht.
   > [!TIP]
   > Weitere Informationen zur Markupsprache finden Sie in diesem Wikipedia-[Artikel](https://en.wikipedia.org/wiki/Markup_language).
 
   Klicken Sie auf **OK**, um Ihre Änderungen zu speichern und die Konfiguration des Zugriffs auf Exchange lokal abzuschließen.

8. Wählen Sie als Nächstes **Erweiterte Einstellungen für den Zugriff auf Exchange Active Sync** aus, um den Bereich *Erweiterte Einstellungen für den Zugriff auf Exchange Active Sync* zu öffnen, in dem Sie Regeln für den Gerätezugriff konfigurieren:  

   - Legen Sie unter **Zugriff nicht verwalteter Geräte** die globale Standardregel für den Zugriff von Geräten fest, für die die Regeln für bedingten Zugriff oder andere Regeln nicht gelten:

     - **Zugriff zulassen**: Alle Geräte können sofort auf Exchange lokal zugreifen. Geräte von Benutzern in Gruppen, die Sie im vorherigen Verfahren als „eingeschlossen“ konfiguriert haben, werden blockiert, wenn sie später als „nicht konform mit den Konformitätsrichtlinien“ oder „nicht in Intune registriert“ ausgewertet werden.

     - **Zugriff blockieren** und **Quarantäne**: Der Zugriff auf Exchange lokal wird sofort für alle Geräte blockiert. Geräte von Benutzern in Gruppen, die Sie im vorherigen Verfahren als „eingeschlossen“ konfiguriert haben, erhalten Zugriff, nachdem die Geräte in Intune registriert und als konform ausgewertet wurden. 

       Android-Geräte *ohne* Samsung-Knox-Standard unterstützen diese Einstellung nicht und werden immer blockiert.

   -  Klicken Sie bei **Geräteplattformausnahmen** auf **Hinzufügen**, und geben Sie die für Ihre Umgebung erforderlichen Plattforminformationen an. 
   
      Wenn die Einstellung **Zugriff nicht verwalteter Geräte** auf **blockiert** festgelegt ist, erhalten Geräte, die registriert und konform sind, auch dann Zugriff, wenn eine Plattformausnahme diesen blockieren würde.  
   
   Klicken Sie auf **OK**, um Ihre Änderungen zu speichern.

9. Klicken Sie auf **Speichern**, um die Richtlinie für bedingten Zugriff auf Exchange zu speichern.

Als Nächstes erstellen Sie eine Konformitätsrichtlinie und weisen diese den Benutzern in Intune zu, um ihre mobilen Geräte auszuwerten. Siehe [Erste Schritte mit der Gerätekonformität](device-compliance-get-started.md).

## <a name="see-also"></a>Siehe auch

[Problembehandlung für den Intune-Connector für Exchange lokal in Microsoft Intune](https://support.microsoft.com/help/4471887)
