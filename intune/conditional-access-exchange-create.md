---
title: Erstellen einer Richtlinie für bedingten Zugriff auf Exchange
titlesuffix: Microsoft Intune
description: Konfigurieren Sie den bedingten Zugriff für eine lokale Installation von Exchange und für das ältere Exchange Online Dedicated in Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0a539000153ad45b5256e4e63086fa72fee44947
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186096"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Erstellen einer Richtlinie für bedingten Zugriff auf eine lokale Installation von Exchange und auf das ältere Exchange Online Dedicated

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel wird dargestellt, wie Sie den bedingten Zugriff für eine lokale Installation von Exchange basierend auf der Gerätekonformität konfigurieren.

Wenn Sie über eine Exchange Online Dedicated-Umgebung verfügen und herausfinden müssen, ob es sich um die neue oder die ältere Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer. Um den E-Mail-Zugriff auf lokales Exchange oder Ihre ältere Exchange Online Dedicated-Umgebung zu steuern, konfigurieren Sie den bedingten Zugriff für lokales Exchange in Intune.

## <a name="before-you-begin"></a>Vorbereitung

Bevor Sie den bedingten Zugriff konfigurieren können, müssen Sie Folgendes überprüfen:

- Bei Ihrer Exchange-Version muss es sich um **Exchange 2010 SP1 oder höher** handeln. Exchange Server-Clientzugriffsserver-Arrays werden unterstützt.

- Sie müssen den [lokalen Exchange-Connector für Exchange Active Sync](exchange-connector-install.md) verwenden, der Intune mit Exchange lokal verbindet.

    >[!IMPORTANT]
    >Der lokale Exchange-Connector ist spezifisch für Ihren Intune-Mandanten und kann mit keinem anderen Mandanten verwendet werden. Intune unterstützt jetzt mehrere lokale Exchange Connectors pro Abonnement. Wenn Sie über mehr als eine lokale Exchange-Organisation verfügen, können Sie einen separaten Connector für jede Exchange-Organisation einrichten.

- Der Connector für eine lokale Exchange-Organisation kann auf jedem Computer installiert werden, solange dieser Computer mit dem Exchange-Server kommunizieren kann.

- Der Connector unterstützt die **Exchange-Clientzugriffsserver-Umgebung**. Technisch können Sie den Connector auch direkt auf dem Exchange-Clientzugriffsserver installieren, aber dies ist nicht zu empfehlen, da die Last auf dem Server dadurch erhöht wird. Sie müssen den Connector so konfigurieren, dass er mit einem der Exchange-Clientzugriffsserver kommuniziert.

- **Exchange ActiveSync** muss für die zertifikatbasierte Authentifizierung oder die Eingabe von Anmeldeinformationen durch Benutzer konfiguriert werden.

- Wenn Richtlinien für bedingten Zugriff konfiguriert und auf einen Benutzer angewendet wurden, muss das **Gerät**, das der Benutzer zum Abrufen von E-Mails verwendet, folgende Voraussetzungen erfüllen:
    - Es muss bei Intune **registriert** sein oder sich um einen in die Domäne eingebundenen PC handeln.
    - **Es muss in Azure Active Directory registriert sein**. Darüber hinaus muss die Exchange ActiveSync-ID des Clients in Azure Active Directory registriert sein.
<br></br>
- Der Azure AD Device Registration-Dienst wird automatisch für Intune und Office 365-Kunden aktiviert. Kunden, die bereits den AD FS Device Registration Service bereitgestellt haben, sehen keine registrierten Geräte in ihrem lokalen Active Directory. **Dies gilt nicht für Windows-PCs und Windows Phone-Geräte.**

- Es besteht **Konformität** mit allen für das Gerät festgelegten Konformitätsrichtlinien.

- Wenn das Gerät die Einstellungen für den bedingten Zugriff nicht erfüllt, erhält der Benutzer bei der Anmeldung eine der folgenden Meldungen:
    - Wenn das Gerät nicht bei Intune oder in Azure Active Directory registriert ist, wird eine Meldung mit Anweisungen zum Installieren der Unternehmensportal-App, zum Registrieren des Geräts und zum Aktivieren des E-Mail-Zugriffs angezeigt. Dieser Prozess verknüpft auch die Exchange ActiveSync-ID mit dem Eintrag des Geräts in Azure Active Directory.
    - Wenn das Gerät nicht konform ist, wird eine Meldung angezeigt, die Benutzer zum Intune-Unternehmensportal oder zur Unternehmensportal-App weiterleitet. Hier finden sie Informationen zum Problem und zu dessen Lösung.

### <a name="support-for-mobile-devices"></a>Unterstützung für mobile Geräte

- Windows Phone 8.1 und höher
- Systemeigene E-Mail-App unter iOS.
- EAS-E-Mail-Clients wie Gmail unter Android 4 oder höher.
- EAS-E-Mail-Clients für **Android-Arbeitsprofilgeräte:** Nur **Gmail** und **Nine Work for Android Enterprise** im **Arbeitsprofil** werden auf Android-Arbeitsprofilgeräten unterstützt. Damit der bedingte Zugriff mit Android-Arbeitsprofilen funktioniert, müssen Sie ein E-Mail-Profil für die Gmail- oder Nine Work for Android Enterprise-App sowie diese Apps als erforderliche Installation bereitstellen.

> [!NOTE]
> Microsoft Outlook für Android und iOS wird nicht über den lokalen Exchange-Connector unterstützt. Wenn Sie Richtlinien für den bedingten Azure Active Directory-Zugriff und Intune-App-Schutzrichtlinien mit Outlook für iOS und Android für Ihre lokale Postfächer nutzen möchten, lesen Sie [Verwendung der modernen Hybridauthentifizierung mit Outlook für iOS und Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). 

### <a name="support-for-pcs"></a>Unterstützung für PCs

Die systemeigene **E-Mail**-Anwendung unter Windows 8.1 und höher (bei Registrierung bei Intune)


## <a name="configure-exchange-on-premises-access"></a>Konfigurieren des Zugriffs auf Exchange lokal

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com/) mit Ihren Intune-Anmeldeinformationen an.

1. Sobald Sie erfolgreich angemeldet sind, wird das **Azure-Dashboard** angezeigt.

1. Klicken Sie im Menü links auf  **Alle Dienste** , und geben Sie in das Filtertextfeld  **Intune**  ein.

1. Wählen Sie  **Intune** aus. Das **Intune-Dashboard** wird angezeigt.

1. Klicken Sie auf **On-premises access** (Lokaler Zugriff). Der Bereich **On-premises access** (Lokaler Zugriff) enthält den Status der Richtlinie für bedingten Zugriff und die Geräte, die davon betroffen sind.

1. Wählen Sie unter **Verwalten** die Option **Zugriff auf Exchange lokal** aus.

1. Klicken Sie im Bereich **Exchange on-premises access** (Zugriff auf eine lokale Installation von Exchange) auf die Option **Ja**, um die Zugriffssteuerung für eine lokale Installation von Exchange zu aktivieren.

    > [!NOTE]
    > Wenn Sie keinen lokalen Connector für Exchange Active Sync konfiguriert haben, ist diese Option deaktiviert.  Sie müssen zunächst mindestens einen Connector installieren und konfigurieren, bevor Sie den bedingten Zugriff auf Exchange lokal aktivieren. Weitere Informationen finden Sie unter [Installieren des lokalen Exchange Connectors für Intune](exchange-connector-install.md).

1. Wählen Sie unter **Zuweisung** die Option **Eingeschlossene Gruppen** aus.  Verwenden Sie die Sicherheitsbenutzergruppe, auf die bedingter Zugriff angewendet werden soll. In diesem Fall müssen die Benutzer ihre Geräte selbst in Intune registrieren und die Konformität mit den Konformitätsprofilen sicherstellen.

1. Wenn Sie bestimmte Gruppen von Benutzern ausschließen möchten, können Sie dazu **Ausgeschlossene Gruppen** auswählen. Wählen Sie anschließend eine Benutzergruppe aus, die Sie von der erforderlichen Registrierung des Geräts und der Konformitätsprüfung ausschließen möchten.

1. Wählen Sie unter **Einstellungen** die Option **Benutzerbenachrichtigungen** aus, um die Standard-E-Mail-Nachricht zu ändern. Diese Meldung wird an Benutzer gesendet, wenn ihr Gerät nicht konform ist und sie auf Exchange lokal zugreifen möchten. Die Nachrichtenvorlage verwendet Markupsprache.  Sie sehen während der Eingabe auch eine Vorschau der Nachricht.
    > [!TIP]
    > Weitere Informationen zur Markupsprache finden Sie in diesem Wikipedia-[Artikel](https://en.wikipedia.org/wiki/Markup_language).

1. Legen Sie im Bereich **Advanced Exchange Active Sync access settings** (Erweiterte Zugriffseinstellungen für Exchange Active Sync) die globale Standardregel für den Zugriff von Geräten, die nicht von Intune verwaltet werden, sowie Regeln auf Plattformebene fest, wie in den nächsten beiden Schritten beschrieben.

1. Bei Geräten, die nicht durch den bedingten Zugriff oder andere Regeln abgedeckt werden, können Sie auswählen, ob der Zugriff auf Exchange zugelassen oder blockiert werden soll.

   - Wenn Sie den Zugriff zulassen, können alle Geräte sofort auf eine lokale Installation von Exchange zugreifen.  Geräte, die Benutzern in **Eingeschlossene Gruppen** gehören, werden blockiert, wenn sie später als nicht konform mit den Konformitätsrichtlinien ausgewertet werden oder nicht in Intune registriert sind.
   - Wenn Sie diese Option auf das Blockieren des Zugriffs festlegen, wird der Zugriff auf eine lokale Installation von Exchange sofort für alle Geräte blockiert.  Geräte, die Benutzern in **Eingeschlossenen Gruppen** gehören, erhalten Zugriff, sobald das Gerät in Intune registriert und als konform ausgewertet wurde. Android-Geräte ohne Samsung KNOX Standard werden immer blockiert, da sie diese Einstellung nicht unterstützen.

1. Wählen Sie unter **Geräteplattformausnahmen** die Option **Hinzufügen** aus, um die Plattformen anzugeben. Wenn die Einstellung **Zugriff nicht verwalteter Geräte** auf **blockiert** festgelegt ist, erhalten Geräte, die registriert und konform sind, auch dann Zugriff, wenn eine Plattformausnahme diesen blockieren würde. Wählen Sie **OK** aus, um die Einstellungen zu speichern.

1. Klicken Sie im Bereich **Lokal** auf **Speichern**, um die Richtlinie für bedingten Zugriff zu speichern.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Erstellen von Azure AD-Richtlinien für den bedingten Zugriff in Intune

Ab Intune Version 1704 können Administratoren im Intune Azure-Portal für Azure AD Richtlinien für den bedingten Zugriff erstellen, damit Sie nicht zwischen Azure- und Intune-Workloads wechseln müssen.

> [!IMPORTANT]
> Sie benötigen eine Azure AD Premium-Lizenz, um im Azure-Portal für Intune Azure AD-Richtlinien für den bedingten Zugriff zu erstellen.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Erstellen einer Azure AD-Richtlinie für den bedingten Zugriff

1. Wählen Sie auf dem **Intune-Dashboard** die Option **Bedingter Zugriff** aus.

2. Klicken Sie im Bereich **Richtlinien** auf **Neue Richtlinie**, um die neue Azure AD-Richtlinie für bedingten Zugriff zu erstellen.

## <a name="see-also"></a>Siehe auch

[Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
