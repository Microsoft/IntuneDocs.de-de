---
title: Klassische Intune-Gruppen im Azure-Portal
titleSuffix: Microsoft Intune
description: Lernen Sie die Neuerungen bei Gruppen im Microsoft Intune-Azure-Portal kennen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
ms.custom: intune-azure
ms.openlocfilehash: b8f33d1cde7ab1b35f643f49af005fdbdb560a02
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-classic-groups-in-the-azure-portal"></a>Klassische Microsoft Intune-Gruppen im Azure-Portal

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Wir haben Ihr Feedback berücksichtigt und einige Änderungen für das Arbeiten mit Gruppen in Microsoft Intune vorgenommen.
Wenn Sie Intune über das Azure-Portal verwenden, wurden Ihre Intune-Gruppen zu Azure Active Directory-Sicherheitsgruppen migriert.

Der Vorteil für Sie ist, dass Sie jetzt in allen Ihren Enterprise Mobility + Security- und Azure AD-Apps dieselbe Gruppenumgebung verwenden. Darüber hinaus können Sie PowerShell und die Graph-API zum Erweitern und Anpassen dieser neuen Funktionalität nutzen.

Azure AD-Sicherheitsgruppen unterstützen alle Arten von Intune-Bereitstellungen für Benutzer und Geräte. Darüber hinaus können Sie dynamische Azure AD-Gruppen verwenden, die basierend auf den von Ihnen angegebenen Attributen automatisch aktualisiert werden. Sie können z.B. eine Gruppe von Geräten erstellen, auf denen iOS 9 ausgeführt wird. Wenn ein mit iOS 9 ausgeführtes Gerät angemeldet wird, wird das Gerät automatisch in der dynamischen Gruppe angezeigt.

## <a name="what-is-not-available"></a>Was ist nicht verfügbar?

Einige der Funktionen von Intune-Gruppen, die Sie eventuell zuvor verwendet haben, sind nicht in Azure AD verfügbar:

- Die Intune-Gruppen **Nicht gruppierte Benutzer** und **Nicht gruppierte Geräte** sind nicht mehr verfügbar.
- Die Option zum **Ausschließen bestimmter Mitglieder** aus einer Gruppe ist im Azure-Portal nicht vorhanden. Sie können jedoch eine Azure AD-Sicherheitsgruppe mit erweiterten Regeln verwenden, um dieses Verhalten zu replizieren. So könnten Sie beispielsweise eine erweiterte Regel erstellen, die alle Mitarbeiter der Vertriebsabteilung in einer Sicherheitsgruppe zusammenschließt, mit Ausnahme der Gruppen, deren Position das Wort Assistent aufweist. Sie könnten diese erweiterte Regel verwenden:

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Die Gruppe **Alle mit Exchange ActiveSync verwalteten Geräte** in der klassischen Intune-Konsole wurde nicht zu Azure AD migriert. Allerdings können Sie im Azure-Portal weiter auf Informationen zu mit EAS verwalteten Geräten zugreifen.

## <a name="how-to-get-started"></a>Erste Schritte

- Lesen Sie die folgenden Themen, um mehr über Azure AD-Sicherheitsgruppen und ihre Funktionsweise zu erfahren:
    -  [Verwalten des Zugriffs auf Ressourcen mit Azure Active Directory-Gruppen](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/)
    -  [Verwalten von Gruppen in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)
    -  [Verwenden von Attributen zum Erstellen erweiterter Regeln](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)
-  Stellen Sie sicher, dass Administratoren, die Gruppen erstellen müssen, der Azure AD-Rolle **Intune-Dienstadministrator** hinzugefügt werden. Beachten Sie, dass die Azure AD Dienstadministrator-Rolle nicht die Berechtigung **Gruppe verwalten** hat.
-  Wenn Ihre Intune-Gruppen die Option **Spezifische Mitglieder ausschließen** verwenden, entscheiden Sie, ob Sie diese Gruppen ohne Ausschlüsse umgestalten können, oder ob Sie erweiterte Regeln benötigen, um Geschäftsanforderungen zu erfüllen.


## <a name="what-happened-to-intune-groups"></a>Was ist mit Intune-Gruppen geschehen?
Wenn Gruppen aus dem Azure-Portal zu Intune im Azure-Portal migriert werden, gelten die folgenden Regeln:

| Gruppen in Intune|Gruppen in Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Statische Benutzergruppe|Statische Azure AD-Sicherheitsgruppe|
|Dynamische Benutzergruppe|Statische Azure AD-Sicherheitsgruppen mit einer Hierarchie von Azure AD-Sicherheitsgruppen|
|Statische Gerätegruppe|Statische Azure AD-Sicherheitsgruppe|
|Dynamische Gerätegruppe|Dynamische Azure AD-Sicherheitsgruppe|
|Eine Gruppe mit einer Einschlussbedingung|Statische Azure AD-Sicherheitsgruppe mit statischen oder dynamischen Mitgliedern nach Verwenden der Bedingung „Einschließen“ in Intune|
|Eine Gruppe mit einer Ausschlussbedingung|Nicht migriert|
|Die integrierten Gruppen:<br>- **Alle Benutzer**<br>- **Nicht gruppierte Benutzer**<br>- **Alle Geräte**<br>- **Nicht gruppierte Geräte**<br>- **Alle Computer**<br>- **Alle mobilen Geräte**<br>- **Alle MDM-verwalteten Geräte**<br>- **Alle EAS-verwalteten Geräte**|Azure AD-Sicherheitsgruppen|

## <a name="group-hierarchy"></a>Gruppenhierarchie

In der Intune-Konsole verfügten alle Gruppen über eine übergeordnete Gruppe. Gruppen können nur Mitglieder aus ihrer übergeordneten Gruppe enthalten. In Azure AD können untergeordnete Gruppen Mitglieder enthalten, die die übergeordnete Gruppe nicht aufweist.

## <a name="group-attributes"></a>Gruppenattribute
Attribute sind Geräteeigenschaften, die bei der Definition von Gruppen verwendet werden können. In der folgenden Tabelle wird beschrieben, wie diese Kriterien zu Azure AD-Sicherheitsgruppen migriert werden.

| Attribut in Intune|Attribut in Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|OE-Attribut (Organisationseinheit) für Gerätegruppen|OE-Attribut für dynamische Gruppen.|
|Domänennamenattribut für Gerätegruppen|Domänennamenattribut für dynamische Gruppen.|
|Sicherheitsgruppe als Attribut für Benutzergruppen|In dynamischen Azure AD-Abfragen können Gruppen nicht als Attribute verwendet werden. Dynamische Gruppen dürfen nur benutzer- oder gerätespezifische Attribute enthalten.|
|Manager-Attribut für Benutzergruppen|Erweiterte Regel für das *Manager*-Attribut in dynamischen Gruppen|
|Alle Benutzer der übergeordneten Benutzergruppe|Statische Gruppe, die diese Gruppe als Mitglied enthält|
|Alle mobilen Geräte der übergeordneten Gerätegruppe|Statische Gruppe, die diese Gruppe als Mitglied enthält|
|Alle von Intune verwalteten mobilen Geräte|Verwaltungstypattribut mit dem Wert „MDM“ für dynamische Gruppen|
|Verschachtelte Gruppen in statischen Gruppen |Verschachtelte Gruppen in statischen Gruppen|
|Verschachtelte Gruppen in dynamischen Gruppen|Dynamische Gruppe mit einer Schachtelungsebene|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>Was geschieht mit Richtlinien und Apps, die Sie bereitgestellt haben?

Richtlinien und Apps werden Gruppen wie bisher weiter bereitgestellt. Allerdings verwalten Sie diese Gruppen jetzt im Azure-Portal statt in der Intune-Konsole.
