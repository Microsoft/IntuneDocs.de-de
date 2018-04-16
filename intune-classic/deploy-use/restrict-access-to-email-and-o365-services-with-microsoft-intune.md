---
title: "Schützen von E-Mail und Office 365"
description: "In diesem Thema wird beschrieben, wie Sie bedingten Zugriff verwenden können, damit nur kompatible Geräte auf Unternehmens-E-Mail und -daten in SharePoint Online und anderen Diensten zugreifen können."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e121a3aaf4988bd92c36eb79131b2205263fb309
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="protect-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>Schützen des Zugriffs auf E-Mail, Office 365 und andere Dienste mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können den Zugriff auf Ihre geschäftlichen E-Mails, Office 365-Dienste wie **lokales Exchange**, **Exchange Online**, **Exchange Online Dedicated**, **SharePoint Online**, **Skype for Business Online** und andere Dienste mithilfe des bedingten EMS-Zugriffs (Enterprise Mobility + Security) schützen. Mithilfe dieser Funktion können Sie sicherstellen, dass der Zugriff auf die E-Mail- und Office 365-Dienste Ihres Unternehmens auf Geräte beschränkt ist, die den von Ihnen festgelegten Regeln für den bedingten Zugriff entsprechen. Diese werden entweder in der Intune-Verwaltungskonsole oder im klassischen Azure-Portal festgelegt.
## <a name="how-does-conditional-access-work"></a>Funktionsweise des bedingten Zugriffs
Mit den Kompatibilitätsrichtlinieneinstellungen können Sie die Kompatibilität eines Geräts bewerten. Eine Richtlinie für bedingten Zugriff verwendet diese Bewertung, um den Zugriff auf einen bestimmten Dienst zuzulassen oder zu beschränken. Wenn Sie eine Richtlinie für bedingten Zugriff in Kombination mit einer Gerätekompatibilitätsrichtlinie verwenden, erhalten nur kompatible Geräte Zugriff auf den Dienst. Die Richtlinien für Konformität und bedingten Zugriff werden dem Benutzer bereitgestellt. Jedes Gerät, das der Benutzer zum Zugriff auf die Dienste verwendet, wird auf die Einhaltung der Richtlinien überprüft.

> [!IMPORTANT]
> Bedenken Sie, dass für den Benutzer, der das Gerät verwendet, eine Kompatibilitätsrichtlinie bereitgestellt werden muss, damit das Gerät hinsichtlich der Kompatibilität bewertet werden kann.
> Wenn keine Kompatibilitätsrichtlinie für den Benutzer bereitgestellt wird, wird das Gerät als kompatibel behandelt, und es werden keine Zugriffsbeschränkungen angewendet.

Wenn Geräte die in den Richtlinien festgelegten Bedingungen nicht erfüllen, erhält der Benutzer Anweisungen zum Registrieren des Geräts und zum Beheben des Problems, das die Konformität des Geräts verhindert.

Ein typischer Ablauf des bedingten Zugriffs:

![Das Diagramm veranschaulicht die Entscheidungspunkte, mit denen ermittelt wird, ob ein Gerät Zugriff auf einen Dienst erhält oder blockiert wird](../media/ConditionalAccess4.png)

## <a name="setup-considerations"></a>Überlegungen zur Einrichtung

### <a name="licensing"></a>Lizenzierung

Microsoft Intune und Azure Active Directory Premium (Azure AD) arbeiten nahtlos zusammen, um mithilfe des bedingten EMS-Zugriffs mehrere Steuerungsebenen zu bieten. Wenn Sie Richtlinien für den bedingten Zugriff mithilfe von Intune bereitstellen möchten, benötigen Sie eine Lizenz für beide Produkte.

**Azure AD Premium-Lizenzen** können als eigenständiger Dienst oder im Rahmen von Enterprise Agreement (zusammen mit Intune) erworben werden. Wenn Sie bedingte Zugriffsrichtlinien mit Intune bereitgestellt haben, stellen Sie sicher, dass Sie die entsprechenden Azure AD Premium- oder **EMS Lizenzen** bezogen haben.

- Weitere Informationen finden Sie in der [Preisübersicht für Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) oder der [Preisübersicht für Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

Stellen Sie darüber sicher, dass den Benutzern, für die Richtlinien für bedingten Zugriff gelten sollen, [Azure AD Premium- oder EMS-Lizenzen](/intune/licenses-assign) zugewiesen wurden.

### <a name="device-compliance-settings"></a>Gerätekompatibilitätseinstellungen

Um den bedingten Zugriff einzurichten, konfigurieren Sie eine Richtlinie für die Gerätekompatibilität und eine Richtlinie für bedingten Zugriff. Die Kompatibilitätsrichtlinie enthält Einstellungen wie z. B. Kennung, Verschlüsselung und Informationen dazu, ob ein Gerät per Jailbreak manipuliert wurde. Das Gerät muss diesen Regeln entsprechen, um als kompatibel anerkannt zu werden.

- Erfahren Sie mehr über die [Richtlinie für die Gerätekompatibilität und ihre Funktionsweise](introduction-to-device-compliance-policies-in-microsoft-intune.md).

### <a name="conditional-access-policy"></a>Richtlinie für bedingten Zugriff

Sie können eine Richtlinie für bedingten Zugriff festlegen, um den Zugriff anhand folgender Aspekte zu schützen:
- Der Status der Gerätekonformität.
- Die auf dem Gerät ausgeführte Plattform.
- Die Art von Apps, die für den Zugriff auf die Dienste verwendet werden.

Im Gegensatz zu anderen Intune-Richtlinien stellen Sie Richtlinien für bedingten Zugriff nicht bereit. Stattdessen konfigurieren Sie die Richtlinie und wählen die Benutzer aus, für die die Richtlinie gelten soll. Dann wird die Richtlinie auf diese Benutzer angewendet. Bei Benutzern, für die eine Richtlinie gelten soll, muss jedes von ihnen verwendete Gerät die Richtlinie erfüllen, damit sie auf Ressourcen zugreifen können.


## <a name="next-steps"></a>Nächste Schritte


2. [Erstellen einer Gerätekompatibilitätsrichtlinie](create-a-device-compliance-policy-in-microsoft-intune.md)

3. Erstellen Sie eine Richtlinie für bedingten Zugriff für eines/n der folgenden Microsoft-Clouddienste bzw. -produkte:

   - [Bedingte Zugriffsrichtlinie für Exchange Online erstellen](restrict-access-to-exchange-online-with-microsoft-intune.md)
   - [Bedingte Zugriffsrichtlinie für Exchange Online lokal erstellen](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
   - [Bedingte Zugriffsrichtlinie für Exchange Online Dedicated (neu) erstellen](restrict-access-to-exchange-online-with-microsoft-intune.md)
   - [Bedingte Zugriffsrichtlinie für Exchange Online Dedicated (älter) erstellen](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
   - [Erstellen einer bedingten Zugriffsrichtlinie für SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
   - [Erstellen einer bedingten Zugriffsrichtlinie für Skype for Business](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
   - [Erstellen einer bedingten Zugriffsrichtlinie für Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
