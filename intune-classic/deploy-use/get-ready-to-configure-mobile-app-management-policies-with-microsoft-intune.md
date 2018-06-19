---
title: Voraussetzungen für MAM-Richtlinien
description: Dieses Thema beschreibt die Voraussetzungen für das Einrichten von Benutzern vor dem Erstellen von Verwaltungsrichtlinien für mobile Apps.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 52cba4de7d19744e1a011071ac6c9bbb168ffb30
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024072"
---
# <a name="get-ready-to-configure-app-protection-policies-in-the-azure-portal"></a>Vorbereitungen zum Konfigurieren von App-Schutzrichtlinien im Azure-Portal

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

In diesem Thema werden die Voraussetzungen und die Schritte beschrieben, die Sie ausführen müssen, **bevor** Sie im Azure-Portal App-Schutzrichtlinien erstellen können.

Um zu verstehen, wie App-Schutzrichtlinien in Intune Ihre Unternehmensdaten schützen kann, gehen Sie unter [Schützen von Apps und Daten mit Microsoft Intune](protect-apps-and-data-with-microsoft-intune.md).

## <a name="what-is-the-azure-portal"></a>Was ist das Azure-Portal?

Das Azure-Portal stellt die neue Verwaltungskonsole zum Erstellen von App-Schutzrichtlinien dar. Es unterstützt die folgenden MAM-Szenarien:
- Geräte, die bei Intune registriert sind
- Geräte, die mithilfe einer anderen Lösung für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) verwaltet werden
- Geräte, die nicht durch eine MDM-Lösung verwaltet werden (BYOD)

Derzeit können Sie sowohl mit der **Intune-Verwaltungskonsole** als auch mit dem **Azure-Portal** App-Schutzrichtlinien konfigurieren.  Beachten Sie Folgendes:

* Die Richtlinien, die Sie im **Azure-Portal** erstellen, werden für alle oben aufgelisteten **MAM-Szenarien** unterstützt. Die **Intune-Verwaltungskonsole** unterstützt nur das Erstellen von Richtlinien für **Geräte, die durch Intune registriert und verwaltet sind**.

* Möglicherweise werden nicht alle Einstellungen der App-Schutzrichtlinie in der Intune-Verwaltungskonsole angezeigt, dar **neue Einstellungen** möglicherweise nur dem **Azure-Portal** hinzugefügt werden.

* Wenn Sie sowohl in der Intune-Verwaltungskonsole **als auch** im Azure-Portal App-Schutzrichtlinien erstellen, wird die im **Azure-Portal erstellte Richtlinie auf die Apps angewendet und für die Benutzer bereitgestellt**.
    * App-Schutzrichtlinien, die in der Intune-Verwaltungskonsole erstellt wurden, können nicht in das Azure-Portal importiert werden.  Die App-Schutzrichtlinien müssen im Azure-Portal neu erstellt werden.


* Andere **App-Verwaltungsfunktionen**, wie das Bereitstellen von Apps sowie Richtlinien für die App-Konfiguration, sind derzeit nur in der **Intune-Verwaltungskonsole** verfügbar.


Wenn Sie noch keine Erfahrungen mit dem Azure-Portal haben, sollten Sie sich unter [Azure portal for Microsoft Intune app protection policies (Azure-Portal für App-Schutzrichtlinien in Microsoft Intune)](azure-portal-for-microsoft-intune-mam-policies.md) einen kurzen Überblick über die Grundlagen zur Verwendung des Azure-Portals verschaffen.

Anweisungen zum Erstellen einer App-Schutzrichtlinie in der Intune-Verwaltungskonsole finden Sie unter [Configure and deploy app protection policies in the Microsoft Intune console (Konfigurieren und Bereitstellen von App-Schutzrichtlinien in der Microsoft Intune-Konsole)](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).


##  <a name="supported-platforms"></a>Unterstützte Plattformen
- iOS 8.1 oder höher
- Android 4 oder höher
- Windows 10

>[!NOTE]
>Ab Version 1703 können App-Schutzrichtlinien für Windows 10-Geräte in MAM ohne Registrierungsszenario definiert werden. Weitere Informationen finden Sie unter [Schutz von Unternehmensdaten mit Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

##  <a name="supported-apps"></a>Unterstützte Apps
* **Microsoft-Apps**: Bei diesen Apps ist das Intune App SDK integriert, und vor der Anwendung von App-Schutzrichtlinien sind keine weiteren Schritte nötig.
Die vollständige Liste der unterstützten Microsoft-Apps finden Sie in der [Microsoft Intune mobile application gallery](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) (Microsoft Intune-Katalog für mobile Anwendungen) auf der Seite für Microsoft Intune-Anwendungspartner. Klicken Sie auf eine App, um die unterstützten Szenarien und Plattformen anzuzeigen und zu erfahren, ob die App mehrere Identitäten unterstützt.

* **Branchenspezifische Apps Ihrer Organisation**: Diese Apps müssen vorbereitet werden. Bevor Sie App-Schutzrichtlinien auf sie anwenden können, müssen Sie das Intune App SDK in die Apps integrieren.

  * Für Geräte, die mit Intune verwaltet werden, lesen Sie die Informationen unter [Auswählen der Vorbereitung von Apps für MAM](/intune/apps-prepare-mobile-application-management).

  * Für nicht verwaltete Geräte, z. B. für Geräte im Besitz der Mitarbeiter, oder für Geräte, die über eine andere Lösung für mobile Geräte verwaltet werden, lesen Sie die Informationen unter [Schützen von branchenspezifischen Apps und Daten auf nicht in Intune registrierten Geräten](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

## <a name="prerequisites"></a>Voraussetzungen

- **Ein Microsoft Intune-Abonnement**. Benutzer benötigen Intune-Lizenzen, um Apps mit App-Schutzrichtlinien erhalten zu können.
  Sie verfügen bereits über ein Intune-Abonnement, wenn Sie Intune zurzeit zum Verwalten Ihrer Geräte verwenden. Sie sind ebenfalls im Besitz eines Intune-Abonnements, wenn Sie eine EMS-Lizenz (Enterprise Mobility Suite) erworben haben. Wenn Sie Intune testen, um die MAM-Fähigkeiten kennenzulernen, können Sie auf der Seite [Microsoft Intune](https://www.microsoft.com/server-cloud/products/microsoft-intune/) ein Testkonto erhalten.

  Um zu überprüfen, ob Sie über ein Intune-Abonnement verfügen, navigieren Sie im Office-Portal zur Seite **Abrechnung**.  Wenn Sie über ein Abonnement verfügen, sollte Intune in den Abonnements als **Aktiv** angezeigt werden.

- **Ein Office 365-Abonnement**, das für Folgendes erforderlich ist:

  - Anwenden von App-Schutzrichtlinien auf Apps, die mehrere Identitäten unterstützen.

  - Erstellen von SharePoint Online- und Exchange Online-Geschäftskonten. Lokale Exchange- und SharePoint-Bereitstellungen werden nicht unterstützt.

- **Einrichten von Skype for Business Online für die moderne Authentifizierung**. Weitere Informationen finden Sie unter [Aktivieren der modernen Authentifizierung](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) zum Erstellen von Benutzern. Azure AD authentifiziert Benutzer, wenn diese die App starten und ihre geschäftlichen Anmeldeinformationen eingeben.

    > [!NOTE]
    > Benutzergruppen müssen in Azure AD eingerichtet werden. Intune-Benutzergruppen können nicht zum Bereitstellen von App-Schutzrichtlinien im Azure-Portal verwendet werden.

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>Erstellen von Benutzern und Zuweisen von Microsoft Intune-Lizenzen

1.  Melden Sie sich mit Ihren Administratoranmeldeinformationen beim [Office-Portal](https://portal.office.com) an.

2.  Fügen Sie, wie im Abschnitt**Schritte zur Durchführung einer 30-tägigen Evaluierung von Intune** des [Intune-Evaluierungshandbuchs](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune) beschrieben, Benutzer hinzu, und weisen Sie anschließend Intune-Lizenzen zu. Um einem Benutzer Zugriff auf das Office-Portal, das Azure AD-Portal und das Azure-Portal zu gewähren, weisen Sie dem Benutzer die Rolle **Globaler Administrator** zu.

5.  App-Schutzrichtlinien werden für Benutzergruppen in Azure Active Directory bereitgestellt. Um Benutzergruppen für Ihre App-Schutzrichtlinien zu erstellen, erstellen Sie eine Benutzergruppe, wie im Abschnitt **Erstellen einer Benutzergruppe** von [Erstellen von Gruppen zum Organisieren der Benutzer und Gruppen des Testabonnements](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3) beschrieben.

### <a name="assign-roles-to-non-global-admin-users"></a>Zuweisen von Rollen zu nicht globalen Administratoren

Globale Administratoren haben Zugriff auf das [Azure-Portal](https://portal.azure.com).  Wenn Benutzer, die keine globalen Administratoren sind, in der Lage sein sollen, Richtlinien zu konfigurieren und andere Verwaltungsaufgaben für mobile Apps auszuführen, lesen Sie den Artikel [Verwenden von Rollenzuweisungen zum Verwalten Ihrer Azure-Abonnementressourcen](https://azure.microsoft.com/documentation/articles/role-based-access-control-configure/).

## <a name="next-steps"></a>Nächste Schritte
[Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
