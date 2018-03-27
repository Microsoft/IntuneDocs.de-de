---
title: Allgemeine Tipps für die Problembehandlung
description: Allgemeine Ressourcen zur Lösung von Problemen mit Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/08/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 944c5771e00d8e256944fe5767217f138797bde2
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>Allgemeine Tipps für die Problembehandlung für Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Nach der Bereitstellung von Microsoft Intune können möglicherweise Probleme bei der Konfiguration oder mit Clientgeräten auftreten. Die folgenden Ressourcen helfen Ihnen, die Ursache des Problems herauszufinden, sodass Sie es beheben können.

> [!NOTE]
> Um eine Supportanfrage zu erstellen oder eine vorhandene Anfrage anzuzeigen, [besuchen Sie das Office 365 Admin Center](https://portal.office.com/admin/default.aspx). Weitere Informationen zu Supportoptionen finden Sie unter [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="define-the-problem"></a>Definieren des Problems

-   Beschreiben Sie das Verhalten.

-   Bei wem und auf welchen Plattformen und Geräten ist dieses Verhalten aufgetreten?

-   Funktionierte das Gerät zuvor ordnungsgemäß?

-   Welche Änderungen haben Sie an der Intune- oder Gerätekonfiguration vorgenommen?

-   Wurden an der Umgebung, in der Sie arbeiten, andere Änderungen als Änderungen an der Konfiguration vorgenommen?

-   Wie häufig tritt dieses Problem auf, und tritt es sporadisch oder dauerhaft auf?

-   Könnte beim Benutzer ein Authentifizierungsproblem vorliegen? Wenn diese Möglichkeit besteht, überprüfen Sie, ob der Benutzer sich bei anderen Diensten, die Azure Active Directory verwenden, anmelden kann. Prüfen Sie auch, ob der Benutzer sich von einem anderen Gerät aus anmelden kann.

-   Haben Sie den Dienststatus überprüft? Sie können Intune-Dienststatus im [Verwaltungsportal von Office 365](https://portal.office.com/Admin/Default.aspx) überwachen. Wählen Sie im linken Bereich **Dienststatus** aus.

## <a name="collect-available-data"></a>Sammeln Sie verfügbare Daten

-   In den folgenden Ressourcen wird erläutert, wie Sie Geräteprotokolle erfassen:
  - [Senden von Android-Diagnosedatenprotokollen an Ihren IT-Administrator über ein USB-Kabel](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Senden von Android-Diagnosedatenprotokollen an Ihren IT-Administrator per E-Mail](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Senden von Android-Registrierungsfehlern an Ihren IT-Administrator](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)
  - [Senden von iOS-Registrierungsfehlern an Ihren IT-Administrator](/intune-user-help/send-errors-to-your-it-admin-ios)

-   Bei Verwaltungskonsolendaten (z. B. bei Problemen mit der Richtlinienimplementierung) überprüfen Sie die gewünschte Richtlinie und den Status dieser Richtlinie, wie in [Erstellen von Gruppen zum Verwalten von Benutzern und Geräten in Microsoft Intune](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune) beschrieben.

## <a name="research-the-solution"></a>Recherchieren der Lösung

-   Suchen Sie im Internet nach einer Lösung. Wenn Sie z. B. den Fehler 0x80073CF0 erhalten, suchen Sie im Internet nach **Technet Intune 0x80073cf0** und finden den Artikel [Behandlung von Problemen mit der App-Bereitstellung in Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md). Der Artikel enthält Vorschläge zur Behebung dieses Fehlers.

-   Suchen Sie im [Intune TechNet-Forum](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod) nach einer Antwort.  Wenn das Problem noch nicht behandelt wurde, stellen Sie Ihre Fragen im Forum, um zu schauen, welche Lösungsvorschläge von der Community kommen.

-   Öffnen Sie eine Supportanfrage. Das Intune-Supportteam kann Sie bei der Problembehandlung besser unterstützen, wenn Sie das Problem definiert und die verfügbaren Daten erfasst haben.

    Zum Erstellen einer Supportanfrage [besuchen Sie das Office 365 Admin Center](https://portal.office.com/admin/default.aspx). Weitere Informationen zu Supportoptionen finden Sie unter [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="find-community-resources"></a>Suchen von Communityressourcen
Weitere hilfreiche Informationen finden Sie in diesen Communityressourcen:

-   Der [Microsoft Intune Survival Guide](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) enthält Links zu vielen Ressourcen, die Sie beim Konfigurieren, Verwalten und beim Beheben von Problemen mit Intune unterstützen können.

-   [Intune-Blog](http://blogs.technet.com/b/windowsintune/)

-   [Folgen Sie Intune auf Twitter](https://twitter.com/MSIntune)

-   [Intune-Foren](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>Nächste Schritte
Die folgenden Themen enthalten Hilfe zur Behandlung bestimmter Probleme. Wenn diese Informationen für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) beschrieben an den Microsoft Support.

[Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Behandlung von Problemen mit dem Zugriff auf Unternehmensressourcen in Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Behandlung von Problemen mit der App-Bereitstellung in Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Behandlung von Problemen bei der Geräteregistrierung bei Intune](troubleshoot-device-enrollment-in-intune.md)

[Behandlung von Problemen mit Richtlinien in Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Behandlung von Problemen bei der Clienteinrichtung in Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Behandlung von Problemen bei Softwareupdates in Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)
