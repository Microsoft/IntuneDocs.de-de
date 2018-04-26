---
title: App-basierter bedingter Zugriff mit Intune
description: Erfahren Sie mehr über den App-basierten bedingten Zugriff mit Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a84e94c16e7c61d1fca83b7774a486f430c9407c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="app-based-conditional-access-with-intune"></a>App-basierter bedingter Zugriff mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[Intune-App-Schutzrichtlinien](app-protection-policy.md) unterstützen Sie beim Schutz Ihrer Unternehmensdaten auf Geräten, die bei Intune registriert sind. App-Schutzrichtlinien können Sie auch auf mitarbeitereigenen Geräten verwenden, die nicht für die Verwaltung in Intune registriert sind. Auch wenn Ihr Unternehmen das Gerät nicht verwaltet, müssen Sie in diesem Fall dennoch sicherstellen, dass Unternehmensdaten und -ressourcen geschützt sind.

Mit App-basiertem bedingten Zugriff und der Verwaltung von mobilen Apps wird eine Sicherheitsschicht hinzugefügt, indem sichergestellt wird, dass nur mobile Apps, die Intune-App-Schutzrichtlinien unterstützen, auf Exchange Online und andere Office 365-Dienste zugreifen können.

> [!NOTE]
> Eine verwaltete App ist eine App, auf die App-Schutzrichtlinien angewendet wurden und die von Intune verwaltet werden kann.

Wenn Sie nur für die Microsoft Outlook-App den Zugriff auf Exchange Online zulassen, können Sie die integrierten E-Mail-Apps von iOS und Android blockieren. Darüber hinaus können Sie für Apps, auf die keine Intune-App-Schutzrichtlinien angewendet wurden, den Zugriff auf SharePoint Online blockieren.

## <a name="prerequisites"></a>Voraussetzungen
Bevor Sie eine App-basierte bedingte Zugriffsrichtlinie erstellen, benötigen Sie Folgendes:

- **Enterprise Mobility + Security (EMS)** oder ein **Azure Active Directory Premium-Abonnement**
- Benutzer müssen für EMS oder Azure AD lizenziert werden.

Weitere Informationen finden Sie in der [Enterprise Mobility – Preise](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) oder der [Azure Active Directory – Preise](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Unterstützte Apps

Eine Liste von Apps, die den App-basierten bedingten Zugriff unterstützen, finden Sie in der [Dokumentation zur Technischen Referenz zum bedingen Zugriff von Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

Der App-basierte bedingte Zugriff [unterstützt auch branchenspezifische Apps](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication), aber diese Apps müssen die [moderne Authentifizierung von Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) nutzen.

## <a name="how-app-based-conditional-access-works"></a>Funktionsweise des App-basierten bedingten Zugriffs

In diesem Beispiel hat der Administrator App-Schutzrichtlinien auf die Outlook-App angewendet. Zudem gilt eine Regel für bedingten Zugriff, mit der die Outlook-App einer genehmigten Liste von Apps hinzugefügt wird, die beim Zugriff auf Unternehmens-E-Mails verwendet werden kann.

> [!NOTE]
> Die Struktur aus dem nachfolgenden Flussdiagramm kann für andere verwaltete Apps verwendet werden.

![Veranschaulichung des Prozesses des App-basierten bedingten Zugriffs in einem Flowchart](./media/ca-intune-common-ways-3.png)

1. Der Benutzer versucht, sich über die Outlook-App bei Azure AD zu authentifizieren.

2. Der Benutzer wird an den App Store umgeleitet, um eine Broker-App zu installieren, wenn er zum ersten Mal versucht, sich zu authentifizieren. Die Broker-App kann der Microsoft Authenticator für iOS oder das Microsoft-Unternehmensportal für Android-Geräte sein.

   Wenn Benutzer versuchen, eine native E-Mail-App zu verwenden, werden sie an den App Store umgeleitet, um dann die Outlook-App zu installieren.

3. Die Broker-App wird auf dem Gerät installiert.

4. Die Broker-App startet die Azure AD-Registrierung, durch die ein Gerätedatensatz in Azure AD erstellt wird. Dies ist nicht mit der Registrierung für die mobile Geräteverwaltung (MDM) identisch, aber dieser Datensatz ist erforderlich, damit bedingte Zugriffsrichtlinien auf dem Gerät erzwungen werden können.

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
