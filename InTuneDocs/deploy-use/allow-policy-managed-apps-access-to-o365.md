---
title: App-basierter bedingter Zugriff auf O365 | Microsoft Intune
description: "Informationen dazu, wie Sie mit bedingtem Zugriff für die Verwaltung mobiler Anwendungen bestimmen können, welche Apps auf O365-Dienste zugreifen dürfen."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: c966d955365611781e83eea9f2aec743f0fc0321


---

# <a name="allow-only-mobile-apps-that-support-intune-mam-policies-to-access-office-365-services"></a>Zulassen des Zugriffs auf Office 365-Dienste ausschließlich für mobile Apps, die Intune-Richtlinien für die Verwaltung mobiler Anwendungen unterstützen
[Intune-Richtlinien für die Verwaltung mobiler Anwendungen (MAM)](protect-apps-and-data-with-microsoft-intune.md) unterstützen Sie beim Schutz Ihrer Unternehmensdaten auf Geräten, die für die Verwaltung in Intune registriert sind. Richtlinien für die Verwaltung mobiler Anwendungen können Sie auch auf **mitarbeitereigenen Geräten verwenden, die nicht für die Verwaltung in Intune registriert sind**.  Auch wenn Sie das Gerät nicht verwalten, müssen Sie in diesem Fall dennoch sicherstellen, dass Unternehmensdaten und -ressourcen geschützt sind. Mithilfe des bedingten Zugriffs für die Verwaltung mobiler Anwendungen (MAM CA) können Sie eine Richtlinie erstellen, mit der nur mobile Apps auf O365-Dienste wie Exchange Online zugreifen können, die Intune-Richtlinien für die Verwaltung mobiler Anwendungen unterstützen.

Wenn Sie beispielsweise zulassen, dass nur die **Microsoft Outlook-App** auf Exchange Online zugreifen kann, können Sie so **verhindern, dass die in iOS und Android integrierten Mail-Apps**, die nicht über den Datenschutz von Intune-Richtlinien für die Verwaltung mobiler Anwendungen verfügen, E-Mails von **Exchange Online** empfangen.

Das folgende Diagramm zeigt den Ablauf, mit dem Richtlinien für den bedingten Zugriff für die Verwaltung mobiler Anwendungen bestimmen, wann der Zugriff zugelassen oder blockiert wird: ![Diagramm, das die verschiedenen Kriterien anzeigt, mit denen bestimmt wird, wann der Zugriff zugelassen oder blockiert wird](../media/mam-ca-decision-flow_simple.png).

Beschreibung der Abkürzungen, die in den Diagrammen verwendet werden:
* **CP**: Unternehmensportal-App
* **AA**: Azure-Authentifikator-App
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Voraussetzungen
**Bevor** Sie MAM CA-Richtlinien konfigurieren können, müssen Sie über ein **Enterprise Mobility + Security- oder ein Azure Active Directory Premium-Abonnement** verfügen, und die Benutzer müssen für EMS oder Azure AD lizenziert sein. Weitere Informationen finden Sie in der [Preisübersicht für Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) oder der [Preisübersicht für Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


## <a name="supported-apps"></a>Unterstützte Apps
**Exchange Online**: **Microsoft Outlook** für Android und iOS.

Informationen zur Benutzererfahrung mit einer App, die über MAM CA-Richtlinien verfügt, finden Sie unter [What to expect when using an app with MAM CA](use-apps-with-mam-ca.md) (Was Sie bei Verwendung einer App mit MAM CA erwarten können).


## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer Exchange Online-Richtlinie für MAM-Apps](mam-ca-for-exchange-online.md)

[Blockieren von Apps, die über keine moderne Authentifizierung verfügen](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Weitere Informationen:

[Schützen von App-Daten mithilfe von Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

