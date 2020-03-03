---
title: App-basierter bedingter Zugriff mit Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr über den App-basierten bedingten Zugriff mit Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9fe275be3f7eccee7f60dc27e5068e5b91ca93d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514148"
---
# <a name="app-based-conditional-access-with-intune"></a>App-basierter bedingter Zugriff mit Intune

[Intune-App-Schutzrichtlinien](../apps/app-protection-policy.md) unterstützen Sie beim Schutz Ihrer Unternehmensdaten auf Geräten, die bei Intune registriert sind. App-Schutzrichtlinien können Sie auch auf mitarbeitereigenen Geräten verwenden, die nicht für die Verwaltung in Intune registriert sind. Auch wenn Ihr Unternehmen das Gerät nicht verwaltet, müssen Sie in diesem Fall dennoch sicherstellen, dass Unternehmensdaten und -ressourcen geschützt sind.

Mit App-basiertem bedingten Zugriff und der Verwaltung von Client-Apps wird eine Sicherheitsstufe hinzugefügt, indem sichergestellt wird, dass nur Client-Apps, die Intune-App-Schutzrichtlinien unterstützen, auf Exchange Online und andere Office 365-Dienste zugreifen können.

> [!NOTE]
> Eine verwaltete App ist eine App, auf die App-Schutzrichtlinien angewendet wurden und die von Intune verwaltet werden kann.

Wenn Sie nur für die Microsoft Outlook-App den Zugriff auf Exchange Online zulassen, können Sie die integrierten E-Mail-Apps von iOS/iPadOS und Android blockieren. Darüber hinaus können Sie für Apps, auf die keine Intune-App-Schutzrichtlinien angewendet wurden, den Zugriff auf SharePoint Online blockieren.

## <a name="prerequisites"></a>Voraussetzungen

Damit Sie eine App-basierte Richtlinie für bedingten Zugriff erstellen können, benötigen Sie Folgendes:

- **Enterprise Mobility + Security (EMS)** oder ein **Azure Active Directory Premium-Abonnement**
- Benutzer müssen für EMS oder Azure AD lizenziert werden.

Weitere Informationen finden Sie unter [Enterprise Mobility: Preise](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) oder [Azure Active Directory: Preise](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Unterstützte Apps

Eine Liste von Apps, die den App-basierten bedingten Zugriff unterstützen, finden Sie in der [Referenz zu den Einstellungen für den bedingten Azure Active Directory-Zugriff](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

Der App-basierte bedingte Zugriff [unterstützt auch branchenspezifische Apps](app-modern-authentication-block.md), aber diese Apps müssen die [moderne Authentifizierung von Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) nutzen. 

## <a name="how-app-based-conditional-access-works"></a>Funktionsweise des App-basierten bedingten Zugriffs

In diesem Beispiel hat der Administrator App-Schutzrichtlinien auf die Outlook-App angewendet. Zudem gilt eine Regel für bedingten Zugriff, mit der die Outlook-App einer genehmigten Liste von Apps hinzugefügt wird, die verwendet werden kann, um auf Unternehmens-E-Mails zuzugreifen.

> [!NOTE]
> Das nachfolgende Flussdiagramm kann für andere verwaltete Apps verwendet werden.

![Veranschaulichung des Prozesses des App-basierten bedingten Zugriffs in einem Flussdiagramm](./media/app-based-conditional-access-intune/ca-intune-common-ways-3.png)

1. Der Benutzer versucht, sich über die Outlook-App bei Azure AD zu authentifizieren.

2. Der Benutzer wird an den App Store umgeleitet, um eine Broker-App zu installieren, wenn er zum ersten Mal versucht, sich zu authentifizieren. Die Broker-App kann der Microsoft Authenticator für iOS oder das Microsoft-Unternehmensportal für Android-Geräte sein.

   Wenn Benutzer versuchen, eine native E-Mail-App zu verwenden, werden sie an den App Store umgeleitet, um dann die Outlook-App zu installieren.

3. Die Broker-App wird auf dem Gerät installiert.

4. Die Broker-App startet die Azure AD-Registrierung, durch die ein Gerätedatensatz in Azure AD erstellt wird. Dies ist nicht mit der Registrierung für die Verwaltung mobiler Geräte (MDM) identisch, aber dieser Datensatz ist erforderlich, damit bedingte Zugriffsrichtlinien auf dem Gerät erzwungen werden können.

5. Die Broker-App überprüft die Identität der App. Es gibt eine Sicherheitsschicht, sodass die Broker-App überprüfen kann, ob die App für die Verwendung durch den Benutzer autorisiert ist.

6. Die Broker-App sendet die App-Client-ID während der Benutzerauthentifizierung an Azure AD, um zu überprüfen, ob sie in der durch die Richtlinie genehmigten Liste enthalten ist.

7. Azure AD ermöglicht dem Benutzer die Authentifizierung und die Verwendung der App basierend auf der durch die Richtlinie genehmigte Liste. Wenn die App nicht auf der Liste enthalten ist, verweigert Azure AD den Zugriff auf die App.

8. Die Outlook-App kommuniziert mit dem Outlook-Clouddienst, um die Kommunikation mit Exchange Online zu initiieren.

9. Der Outlook-Clouddienst kommuniziert mit Azure AD, um Exchange Online-Dienstzugriffstoken für den Benutzer abzurufen.

10. Die Outlook-App kommuniziert mit Exchange Online, um die Unternehmens-E-Mails des Benutzers abzurufen.

11. Unternehmens-E-Mails werden an das Postfach des Benutzers übermittelt.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer App-basierten Richtlinie für bedingten Zugriff](app-based-conditional-access-intune-create.md)

[Blockieren von Apps, die über keine moderne Authentifizierung verfügen](app-modern-authentication-block.md)
