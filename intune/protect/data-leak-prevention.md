---
title: Verhindern von Datenverlusten auf nicht verwalteten Geräten
titleSuffix: Microsoft Intune
description: Ermöglichen Sie den Zugriff auf Unternehmensdaten auf Geräten, und schützen Sie Daten vor Datenverlusten mithilfe von Microsoft Intune.
keywords: Datenschutz, Verluste verhindern, Gerät, O365, Office 365
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3affffdf69445ced667d718587303a5409423bf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502398"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>Verhindern von Datenverlusten auf nicht verwalteten Geräten mit Microsoft Intune

Wenn Sie Zugriff auf Unternehmensdaten gewähren, die von Office 365 gehostet werden, können Sie steuern, wie Benutzer Daten freigeben und speichern, ohne beabsichtigte oder versehentliche Datenverluste zu riskieren. Microsoft Intune stellt App-Schutzrichtlinien bereit, die Sie festlegen, um Ihre Unternehmensdaten auf benutzereigenen Geräten zu sichern. Die Geräte müssen nicht beim Intune-Dienst registriert werden. 

Mit Intune eingerichtete App-Schutzrichtlinien funktionieren auch auf Geräten, die mit einer Geräteverwaltungslösung verwaltet werden, die nicht von Microsoft stammt. Die personenbezogenen Daten auf den Geräten werden nicht angerührt. Nur die Unternehmensdaten werden von der IT-Abteilung verwaltet. 

Sie können App-Schutzrichtlinien für mobile Office-Apps auf Geräten festlegen, auf denen Windows, iOS oder Android ausgeführt wird, um Unternehmensdaten zu schützen. Mit diesen Richtlinien können Sie Richtlinien wie eine App-basierte PIN oder eine Verschlüsselung von Unternehmensdaten sowie erweiterte Einstellungen festlegen, um einzuschränken, wie die Funktionen „Ausschneiden“, „Kopieren“, „Einfügen“ und „Speichern unter“ von Benutzern zwischen verwalteten und nicht verwalteten Apps verwendet werden können. Sie können Unternehmensdaten auch remote zurücksetzen, ohne dass Benutzer Geräte registrieren müssen.

Die App-Schutzrichtlinien von Intune sind unabhängig von der Geräteverwaltung. Mit App-Schutzrichtlinien können Sie mobile Office-Apps sowohl auf nicht verwalteten als auch auf von Intune verwalteten Geräten und auf Geräten verwalten, die von MDM-Lösungen verwaltet werden, die nicht von Microsoft stammen.

## <a name="before-you-begin"></a>Vorbereitung

Der folgende Maßnahmenplan kann verwendet werden, wenn Sie die folgenden Anforderungen erfüllen:

* Ihr Unternehmen ist für den sicheren Übergang in die Cloud bereit.
* Ihr Unternehmen verwendet die Office 365 Exchange Online, SharePoint Online, OneDrive for Business oder Yammer.
* Ihr Unternehmen verfügt über Lizenzen für Microsoft-365, Enterprise Mobility + Security (EMS) oder Azure Information Protection.
* Ihr Unternehmen ermöglicht Benutzern den Zugriff auf Unternehmensdaten über unternehmens- oder benutzereigene Windows-, iOS- oder Android-Geräte.
* Ihr Unternehmen möchte nicht, dass die Registrierung von benutzereigenen Geräten in einem Geräteverwaltungsdienst erforderlich ist.

## <a name="action-plan"></a>Maßnahmenplan

Für iOS- und Android-Geräte:

1. Erfahren Sie, wie [App-Schutzrichtlinien](../apps/app-protection-policy.md) funktionieren.
2. Erfahren Sie, wie Sie [App-Schutzrichtlinien für mobile Office-Apps erstellen und bereitstellen](../apps/app-protection-policies.md).
3. [Überwachen Sie die App-Schutzrichtlinien](../apps/app-protection-policies-monitor.md), die Sie erstellen und bereitstellen.

Für Windows 10-Geräte:

1. Erfahren Sie, [wie Windows Information Protection (WIP) funktioniert](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip).
2. Machen Sie sich bereit für die Konfiguration von [App-Schutzrichtlinien für Windows 10](../apps/app-protection-policies-configure-windows-10.md).
3. [Erstellen Sie WIP-App-Schutzrichtlinien in Intune, und stellen Sie diese bereit](../apps/windows-information-protection-policy-create.md).

## <a name="what-to-tell-employees-and-students"></a>Informationen für Mitarbeiter und Studenten

Geben Sie nach Bedarf die folgenden Links frei, um zusätzliche Informationen bereitzustellen:

* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-ios.md)
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-android.md)

## <a name="next-steps"></a>Nächste Schritte

Benötigen Sie Hilfe bei der Aktivierung dieses oder anderer EMS- oder Office 365-Szenarios? Wenn Sie über mindestens 150 Lizenzen für Microsoft 365, Enterprise Mobility + Security oder Azure Active Directory Premium verfügen, nutzen Sie Ihre [FastTrack-Vorteile](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program).
