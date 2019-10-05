---
title: Exchange ohne Gerätemanagement
titleSuffix: Microsoft Intune
description: Verwenden Sie Microsoft Intune, wenn Sie Mitarbeitern Zugriff auf ihre Office 365 Exchange Online-E-Mails erteilen möchten. Sie müssen dafür kein Geräteverwaltungssystem einrichten.
keywords: Office 365 Exchange-E-Mail-Zugriff
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2017
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.topic: archived
ms.technology: ''
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66e1d2df3d6aa3e5346104d6548df7dcb210c0f0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732684"
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>Schützen von Office 365 Exchange Online ohne erforderliche Geräteverwaltung

Sie möchten Mitarbeitern Zugriff auf ihre geschäftlichen E-Mails geben, ohne mit viel Aufwand ein Geräteverwaltungssystem einzurichten? Kein Problem. Sie können über Intune Zugriff auf Office 365 Exchange Online gewähren. Um die notwendigen Schritte durchzuführen, vergewissern Sie sich, dass Sie über Lizenzen für Microsoft 365 oder Azure Active Directory (Premium) und Intune verfügen. Mitarbeiter müssen über ein [unterstütztes iOS- oder Android-Gerät](../fundamentals/supported-devices-browsers.md) verfügen. 

Wenn Sie sich dafür entscheiden, ein Geräteverwaltungssystem einzurichten, können Sie das tun. Diese Art von App-Schutz funktioniert unabhängig von der Geräteverwaltung. 

## <a name="action-plan"></a>Maßnahmenplan

1. [Weitere Informationen zum bedingten Zugriff](conditional-access.md). 
2. [Weitere Informationen zum App-basierten bedingten Zugriff](app-based-conditional-access-intune.md).
3. [Einrichten App-basierter Richtlinien für bedingten Zugriff für Exchange Online](app-based-conditional-access-intune-create.md).
4. [Blockieren von Apps, die nicht verwaltet werden können](app-modern-authentication-block.md), insbesondere Apps, die nicht die Authentifizierungsbibliothek von Azure Active Directory (ADAL) verwenden.
5. (Optional) [Einrichten App-basierter Richtlinien für bedingten Zugriff für SharePoint Online](app-based-conditional-access-intune-create.md). Diese Richtlinien blockieren den Zugriff auf Ihre Unternehmensdaten über Apps, die nicht verwaltet und geschützt werden können. Die Richtlinien beschränken auch den Zugriff über die mobile Version von SharePoint. 

## <a name="what-to-tell-employees-and-students"></a>Informationen für Mitarbeiter und Studenten

* Bitten Sie Ihre Mitarbeiter und Studenten, Microsoft Outlook oder Microsoft SharePoint für iOS aus dem Apple App Store oder für Android aus dem Google Play Store herunterzuladen. 
* Wenn Sie den Zugriff auf Apps blockieren, die keine moderne Authentifizierung verwenden, informieren Sie die Mitarbeiter und Studenten darüber. 

## <a name="next-steps"></a>Nächste Schritte

Sie haben den App-basierten bedingten Zugriff verwendet, um die Sicherheit der Unternehmensdaten zu erhöhen. Im Zuge der nächsten Schritte können Sie mehr über die anderen Möglichkeiten erfahren, den Schutz Ihrer Unternehmensdaten zu erhöhen. Dazu zählt Folgendes: 

* Einrichten des [bedingten Zugriffs basierend auf der Gerätekonformität, dem Geräterisiko, dem Speicherort und Benutzerattributen in Active Directory und Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)  
* Einrichten von App-Schutzrichtlinien zum Schutz Ihrer Unternehmensdaten vor versehentlichen und vorsätzlichen Datenverlusten 
* Verwenden von Azure Information Protection zum Schutz von Unternehmensdaten außerhalb Ihres Netzwerks 

Benötigen Sie Hilfe bei der Aktivierung dieses oder anderer EMS- oder Office 365-Szenarios? Wenn Sie über mindestens 150 Lizenzen für Microsoft 365, Enterprise Mobility + Security oder Azure Active Directory Premium verfügen, nutzen Sie Ihre [FastTrack-Vorteile](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 
