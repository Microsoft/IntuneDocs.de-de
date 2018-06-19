---
title: Schützen von Skype for Business Online
description: Schützen und steuern Sie den Zugriff auf Skype for Business Online unter Verwendung von bedingtem Zugriff.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d9d912cc0a2d8f815e046d888fc8878a8703c514
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022712"
---
# <a name="protect-access-to-skype-for-business-online-with-microsoft-intune"></a>Schützen des Zugriffs auf Skype for Business Online mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können die Richtlinie für bedingten Zugriff für **Skype for Business Online** zum Steuern des Zugriffs auf Skype for Business Online verwenden.
Der bedingte Zugriff besteht aus zwei Komponenten:
- Einer Gerätekompatibilitätsrichtlinie, die das Gerät erfüllen muss, um als kompatibel bewertet zu werden
- Einer Richtlinie für bedingten Zugriff, in der Sie die Bedingungen festlegen, die das Gerät erfüllen muss, damit Sie auf den Dienst zugreifen können
Weitere Informationen zur Funktionsweise des bedingten Zugriffs finden Sie im Artikel [Protect access to email and O365 services (Schützen des Zugriffs auf E-Mail- und Office 365-Dienste)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Wenn ein Benutzer, für den der bedingte Zugriff gilt, versucht, Skype for Business Online auf seinem Gerät zu verwenden, erfolgt folgende Auswertung:

![Diagramm mit den Entscheidungspunkten, die bestimmen, ob der Zugriff eines Geräts auf Skype for Business Online zugelassen oder blockiert wird](../media/ConditionalAccess_SkypeforBusiness.png)

**Bevor** Sie eine bedingte Zugriffsrichtlinie für Skype for Business Online konfigurieren, müssen folgende Voraussetzungen erfüllt sein:
- Sie müssen über ein **Skype for Business Online-Abonnement** verfügen und Benutzern die Skype for Business Online-Lizenz zuweisen.
- Sie müssen über ein **Enterprise Mobility + Security- (EMS)** oder **Azure Active Directory (Azure AD) Premium-Abonnement** verfügen, und Benutzer müssen für EMS oder Azure AD lizenziert sein. Weitere Informationen finden Sie in der [Preisübersicht für Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) oder der [Preisübersicht für Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

-   [Aktivieren Sie die moderne Authentifizierung](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) für Skype for Business Online.
-  All Ihre Benutzer müssen **Skype for Business Online** verwenden. Wenn in Ihrer Bereitstellung sowohl Skype for Business Online als auch lokales Skype for Business verwendet werden, wird die Richtlinie für bedingten Zugriff nicht auf Benutzer angewendet.

Für das Gerät, dass Zugriff auf Skype for Business Online benötigt, müssen folgende Voraussetzungen erfüllt sein:

-   Es muss sich um ein **Android**- oder **iOS**-Gerät handeln.

-   Es muss bei Intune **registriert** sein.

-   Es muss mit allen bereitgestellten Konformitätsrichtlinien **konform** sein.


Der Gerätestatus wird in Azure Active Directory gespeichert, wo der Zugriff entsprechend den von Ihnen angegebenen Bedingungen gewährt oder blockiert wird.

Wenn eine Bedingung nicht erfüllt wird, erhält der Benutzer bei der Anmeldung die folgenden Meldungen:

-   Wenn das Gerät nicht bei Intune oder in Azure Active Directory registriert ist, wird eine Meldung mit Anweisungen zum Installieren der Unternehmensportal-App und zum Registrieren des Geräts angezeigt.

-   Wenn das Gerät nicht konform ist, wird eine Meldung angezeigt, die den Benutzer zur Intune-Unternehmensportalwebsite oder zur Unternehmensportal-App weiterleitet. Dort findet der Benutzer Informationen zum Problem und dessen Lösung.

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Konfigurieren des bedingten Zugriffs für Skype for Business Online

### <a name="step-1-configure-azure-active-directory-security-groups"></a>Schritt 1: Konfigurieren von Azure Active Directory-Sicherheitsgruppen
Bevor Sie beginnen, konfigurieren Sie Azure Active Directory-Sicherheitsgruppen für die bedingte Zugriffsrichtlinien. Sie können diese Gruppen im **Office 365 Admin Center** konfigurieren. Diese Gruppen werden verwendet, um die Richtlinie auf Benutzer anzuwenden oder Benutzer von der Richtlinie auszunehmen. Bei Benutzern, für die die Richtlinie gelten soll, muss jedes von ihnen verwendete Gerät die Richtlinie erfüllen, damit sie auf Ressourcen zugreifen können.

Sie können zwei Gruppen angeben, die für die Skype for Business-Richtlinie verwendet werden können:

-   **Zielgruppen**: Gruppen von Benutzern, für die die Richtlinie gilt.

-   **Ausgenommene Gruppen**: Gruppen von Benutzern, die von der Richtlinie ausgenommen sind.

Benutzer, die in beiden Gruppen enthalten sind, werden von der Richtlinie ausgenommen.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Schritt 2: Konfigurieren und Bereitstellen einer Konformitätsrichtlinie
Sie müssen eine Kompatibilitätsrichtlinie [erstellen](create-a-device-compliance-policy-in-microsoft-intune.md) und auf allen Geräten [bereitstellen](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md), die von der Richtlinie betroffen sind. Dies sind alle Geräte, die von den Benutzern in den **Zielgruppen** verwendet werden.

> [!NOTE]
> Kompatibilitätsrichtlinien werden für Intune-Gruppen bereitgestellt, Richtlinien für bedingten Zugriff dagegen werden auf Azure Active Directory-Sicherheitsgruppen angewendet.


> [!IMPORTANT]
> Wenn Sie keine Kompatibilitätsrichtlinie bereitgestellt haben, werden die Geräte als kompatibel ausgewertet.

Fahren Sie anschließend mit **Schritt 3** fort.

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Schritt 3: Konfigurieren der Skype for Business Online-Richtlinie
Jetzt konfigurieren Sie die Richtlinie so, dass nur verwaltete und kompatible Geräte auf Skype for Business Online zugreifen dürfen. Diese Richtlinie wird in Azure Active Directory gespeichert.

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Richtlinie** > **Bedingter Zugriff** > **Skype for Business Online-Richtlinie** aus.

   ![Screenshot der Seite mit der Skype for Business Online-Richtlinie für bedingten Zugriff](./media/conditional_access_SFBPolicy.png)

2. Wählen Sie **Richtlinie für bedingten Zugriff aktivieren** aus.

3. Unter **Anwendungszugriff** können Sie optional eine Richtlinie für bedingten Zugriff auf Folgendes anwenden:

   -   **iOS**

   -   **Android**

4. Wählen Sie unter **Zielgruppen** **Ändern** aus, um die Azure Active Directory-Sicherheitsgruppen auszuwählen, für die die Richtlinie gelten soll. Sie können dies für alle Benutzer oder nur für eine ausgewählte Benutzergruppe festlegen.

5. Wählen Sie unter **Exempted Groups** (Ausgenommene Gruppen) optional **Ändern**, um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die von dieser Richtlinie ausgenommen werden.

6. Wenn Sie fertig sind, wählen Sie **Speichern** aus.

Sie haben jetzt den bedingten Zugriff für Skype for Business Online konfiguriert. Die Richtlinie für bedingten Zugriff wird sofort wirksam und muss nicht explizit bereitgestellt werden.


## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Überwachen der Richtlinien für Konformität und bedingten Zugriff
Im Arbeitsbereich **Gruppen** können Sie den Status beim bedingten Zugriff Ihrer Geräte anzeigen.

Wählen Sie eine beliebige Gruppe von Mobilgeräten aus. Wählen Sie dann auf der Registerkarte **Geräte** einen der folgenden **Filter** aus:

* **Geräte, die nicht bei AAD registriert sind**: Diese Geräte werden für Skype for Business Online blockiert.

* **Geräte, die nicht kompatibel sind**: Diese Geräte werden für Skype for Business Online blockiert.

* **Geräte, die bei AAD registriert und kompatibel sind**: Diese Geräte können auf Skype for Business Online zugreifen.
