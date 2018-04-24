---
title: App-basierter bedingter Zugriff auf O365
description: Informationen dazu, wie Sie mit bedingtem Zugriff für die Verwaltung mobiler Anwendungen bestimmen können, welche Apps auf O365-Dienste zugreifen dürfen.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/05/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1f9446da0f553dca29bbfd96b99711c895cd8533
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>Zulassen des Zugriffs auf Office 365-Dienste ausschließlich für mobile Apps, die Intune-App-Richtlinien für die Verwaltung mobiler Anwendungen unterstützen

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

[Intune-App-Schutzrichtlinien](protect-apps-and-data-with-microsoft-intune.md) unterstützen Sie beim Schutz Ihrer Unternehmensdaten auf Geräten, die für die Verwaltung in Intune registriert sind. App-Schutzrichtlinien können Sie auch auf **mitarbeitereigenen Geräten verwenden, die nicht für die Verwaltung in Intune registriert sind**.  Auch wenn Sie das Gerät nicht verwalten, müssen Sie in diesem Fall dennoch sicherstellen, dass Unternehmensdaten und -ressourcen geschützt sind. Mithilfe des App-basierten bedingten Zugriffs mit MAM können Sie eine Richtlinie erstellen, die nur mobilen Apps mit Unterstützung für Intune-App-Schutzrichtlinien den Zugriff auf O365-Dienste wie Exchange Online gestattet.

Wenn Sie beispielsweise zulassen, dass nur die **Microsoft Outlook-App** auf Exchange Online zugreifen kann, können Sie so **verhindern, dass die in iOS und Android integrierten Mail-Apps**, die nicht über den Datenschutz von Intune-Richtlinien für die Verwaltung mobiler Anwendungen verfügen, E-Mails von **Exchange Online** empfangen. Sie können auch verhindern, dass mobile Apps, die nicht über MAM-Unterstützung verfügen, auf **SharePoint Online** zugreifen.

Das folgende Diagramm zeigt den Flow, anhand dessen Richtlinien für den App-basierten bedingten Zugriff festlegen, wann der Zugriff zugelassen oder blockiert wird: ![Diagramm, das die verschiedenen Kriterien anzeigt, die festlegen, wann der Zugriff zugelassen oder blockiert wird](../media/mam-ca-decision-flow_simple.png).

Beschreibung der Abkürzungen, die in den Diagrammen verwendet werden:
* **CP**: Unternehmensportal-App
* **AA**: Azure-Authentifikator-App
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Voraussetzungen
**Bevor** Sie Richtlinien für den App-basierten bedingten Zugriff konfigurieren können, müssen Sie über ein **Enterprise Mobility + Security- oder ein Azure Active Directory Premium-Abonnement** verfügen, und die Benutzer müssen für EMS oder Azure AD lizenziert sein. Weitere Informationen finden Sie in der [Preisübersicht für Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) oder der [Preisübersicht für Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).


## <a name="supported-apps"></a>Unterstützte Apps
**Exchange Online**:
* **Microsoft Outlook** für Android und iOS

**SharePoint Online**
* Microsoft Word für iOS und Android
* Microsoft Excel für iOS und Android
* Microsoft PowerPoint für iOS und Android
* Microsoft OneDrive for Business für iOS und Android
* Microsoft OneNote für iOS

>[!IMPORTANT]
>Bei Android-Geräten muss die anfängliche Geräteregistrierung durch Anmeldung bei der OneDrive-App oder bei der Outlook-App erfolgen. Die OneNote-App für Android unterstützt MAM ohne Registrierung noch nicht.

Informationen zur Benutzerumgebung mit einer App, die Richtlinien für den App-basierten bedingten Zugriff beinhaltet, finden Sie unter [Was ist bei der Verwendung einer App mit App-basierter Zertifizierungsstelle (CA) zu erwarten](use-apps-with-mam-ca.md).


## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer Exchange Online-Richtlinie für MAM-Apps](mam-ca-for-exchange-online.md)

[Erstellen einer SharePoint Online-Richtlinie für MAM-Apps](mam-ca-for-sharepoint-online.md)

[Blockieren von Apps, die über keine moderne Authentifizierung verfügen](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Siehe auch

[Protect app data with app protection policies (Schützen von App-Daten mithilfe von App-Schutzrichtlinien)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
