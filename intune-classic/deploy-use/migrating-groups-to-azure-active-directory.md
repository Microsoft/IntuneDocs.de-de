---
title: Migrieren zu Azure Active Directory-Gruppen
description: So werden Ihre Gruppen von Intune zu Azure AD migriert
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 12/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: ef0b540b6b70ca67a0da8b00997bb761722eb76a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="a-new-way-of-using-groups-in-intune"></a>Eine neue Art der Verwendung von Gruppen in Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Wir haben Ihr Feedback berücksichtigt und einige Änderungen für das Arbeiten mit Gruppen in Microsoft Intune vorgenommen.
Wir sind dabei, alle Intune-Gruppen unserer Kunden in Azure Active Directory-Sicherheitsgruppen zu migrieren.

Der Vorteil für Sie ist, dass Sie jetzt in allen Ihren Enterprise Mobility + Security- und Azure AD-Apps dieselbe Gruppenumgebung verwenden. Darüber hinaus werden können Sie PowerShell und die Graph-API zum Erweitern und Anpassen dieser neuen Funktionalität nutzen.

Azure AD-Sicherheitsgruppen unterstützen alle Arten von Intune-Bereitstellungen für Benutzer und Geräte. Darüber hinaus können Sie dynamische Azure AD-Gruppen verwenden, die basierend auf den von Ihnen angegebenen Attributen automatisch aktualisiert werden. Sie können z.B. eine Gruppe von Geräten erstellen, auf denen iOS 9 ausgeführt wird. Sobald ein neues Gerät mit iOS 9 registriert wird, wird es automatisch der dynamischen Gruppe hinzugefügt.

## <a name="when-is-this-happening"></a>Wann geschieht das?

Der Migrationsvorgang ist gerade im Gange. Sie werden benachrichtigt, bevor wir Ihre Daten migrieren.
Wenn die Migration Ihrer Daten bereits erfolgt ist, wird eine Meldung wie die folgende angezeigt, sobald Sie versuchen, in der klassischen Intune-Konsole auf Gruppen zuzugreifen:

![Meldung mit der Information, dass Gruppen migriert wurden.](http://i.imgur.com/72KRaXj.png)

## <a name="what-wont-be-available"></a>Was wird nicht verfügbar sein?

Einige bisherige Funktionen von Intune-Gruppen sind in Azure AD nicht verfügbar:

- Die Intune-Gruppen **Nicht gruppierte Benutzer** und **Nicht gruppierte Geräte** werden nicht migriert.
- Die derzeit in der Intune-Konsole vorhandene Option zum **Ausschließen bestimmter Mitglieder** aus einer Gruppe gibt es im Azure-Portal nicht. Sie können jedoch eine Azure Active Directory-Sicherheitsgruppe mit erweiterter Regeln verwenden, um dieses Verhalten zu replizieren. So könnten Sie beispielsweise die erweiterte Regel `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")` erstellen, die alle Mitarbeiter der Abteilung „Vertrieb“ in einer Sicherheitsgruppe enthält, mit Ausnahme der Personen, deren Position das Wort „Assistent“ aufweist.
- Die Gruppe **Alle mit Exchange ActiveSync verwalteten Geräte**, die in der Intune-Konsole integriert ist, wird nicht zu Azure AD migriert. Allerdings können Sie im Azure-Portal weiter auf Informationen zu mit Exchange ActiveSync verwalteten Geräten zugreifen.
- In der klassischen Intune-Verwaltungskonsole können Berichte nicht nach Gruppen gefiltert werden.
<!--- - Custom group targeting of notification rules will not be available. ROB I took this out as I couldn't replicate the behavior. --->

## <a name="how-to-get-ready"></a>Vorbereitungen

- Lesen Sie die folgenden Azure AD-Themen, um mehr über Azure AD-Sicherheitsgruppen und ihre Funktionsweise zu erfahren:
    -  [Verwalten des Zugriffs auf Ressourcen mit Azure Active Directory-Gruppen](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/)
    -  [Verwalten von Gruppen in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)
    -  [Verwenden von Attributen zum Erstellen erweiterter Regeln](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)
- Erwägen Sie vor der Migration das Entfernen von Intune-Gruppen, die Sie nicht mehr verwenden.
-  Stellen Sie sicher, dass Administratoren, die Gruppen erstellen müssen, der Azure AD-Rolle **Intune-Dienstadministrator** hinzugefügt werden. Beachten Sie, dass die Azure AD-Rolle „Dienstadministrator“ nicht die Berechtigung **Gruppe verwalten** hat.
-  Wenn Sie Gruppen mit der Option **Bestimmte Mitglieder ausschließen** verwenden, prüfen Sie, ob Sie diese Gruppe so ändern können, dass keine Ausschlüsse erforderlich sind, oder ob Sie in Ihrer Azure AD-Abfrage erweiterte Regeln nutzen können, um dasselbe Ergebnis zu erzielen.


## <a name="what-happens-to-intune-groups"></a>Was geschieht mit Intune-Gruppen?

| Gruppen in Intune|Gruppen in Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Statische Benutzergruppe|Statische Azure AD-Sicherheitsgruppe|
|Dynamische Benutzergruppe|Statische Azure AD-Sicherheitsgruppen mit einer Hierarchie von Azure AD-Sicherheitsgruppen|
|Statische Gerätegruppe|Statische Azure AD-Sicherheitsgruppe|
|Dynamische Gerätegruppe|Dynamische Azure AD-Sicherheitsgruppe|
|Eine Gruppe mit einer Einschlussbedingung|Statische Azure AD-Sicherheitsgruppe mit statischen oder dynamischen Mitgliedern nach Verwenden der Bedingung „Einschließen“ in Intune.|
|Eine Gruppe mit einer Ausschlussbedingung|Nicht migriert|
|Die integrierten Gruppen **Alle Benutzer**, **Nicht gruppierte Benutzer**, **Alle Geräte**, **Nicht gruppierte Geräte**, **Alle Computer**, **Alle mobilen Geräte**, **Alle mit MDM verwalteten Geräte** und **Alle mit EAS verwalteten Geräte**|Azure AD-Sicherheitsgruppen.|

In Intune müssen alle Gruppen eine übergeordnete Gruppe haben. Gruppen können nur Mitglieder aus der übergeordneten Gruppe enthalten. In Azure AD können untergeordnete Gruppen Mitglieder enthalten, die die übergeordnete Gruppe nicht aufweist.

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

## <a name="what-happens-to-policies-and-apps-youve-already-deployed"></a>Was geschieht mit Richtlinien und Apps, die Sie bereits bereitgestellt haben?

Richtlinien und Apps werden Gruppen wie bisher weiter bereitgestellt. Allerdings verwalten Sie diese Gruppen jetzt im Azure-Portal statt in der klassischen Intune-Konsole.
 
