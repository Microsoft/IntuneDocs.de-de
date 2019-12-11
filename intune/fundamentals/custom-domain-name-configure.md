---
title: Konfigurieren eines benutzerdefinierten Domänennamens
titleSuffix: Microsoft Intune
description: Hinzufügen eines benutzerdefinierten Domänennamens für Ihr Microsoft Intune-Abonnement
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04708842373abf296b5350d9f77e02fa08ce48ed
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414620"
---
# <a name="configure-a-custom-domain-name"></a>Konfigurieren eines benutzerdefinierten Domänennamens

In diesem Thema erfahren Administratoren, wie Sie einen DNS CNAME erstellen können, um mithilfe von Microsoft Intune Ihre Anmeldung zu vereinfachen und anzupassen.

Wenn sich Ihre Organisation für einen cloudbasierten Microsoft-Dienst wie Intune registriert, erhalten Sie einen anfänglichen Domänenname, der in Azure Active Directory (AD) gehostet wird. Der Name sieht so aus: **IhreDomäne.onmicrosoft.com**. In diesem Beispiel steht **IhreDomäne** für den Domänennamen, den Sie bei der Registrierung ausgewählt haben. **onmicrosoft.com** ist das Suffix, das den Konten zugewiesen wird, die Sie Ihrem Abonnement hinzufügen. Sie können die benutzerdefinierte Domäne Ihrer Organisation so konfigurieren, dass auf Intune zugegriffen wird und nicht auf den bei der Einrichtung Ihres Abonnements angegebenen Domänennamen.

Bevor Sie Benutzerkonten erstellen oder Ihr lokales Active Directory-Verzeichnis synchronisieren, wird dringend empfohlen, dass Sie entscheiden, ob nur die .onmicrosoft.com-Domäne verwendet oder benutzerdefinierte Domänennamen hinzugefügt werden sollen. Richten Sie eine benutzerdefinierte Domäne ein, bevor Sie zur Vereinfachung der Benutzerverwaltung Benutzer hinzufügen. Durch Einrichten einer benutzerdefinierten Domäne können sich Benutzer mit den Anmeldeinformationen anmelden, die sie für den Zugriff auf andere Domänenressourcen verwenden.

Wenn Sie einen cloudbasierten Dienst von Microsoft abonnieren, wird Ihre Instanz dieses Diensts zu einem Microsoft [Azure AD-Mandanten](https://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant). Azure AD stellt Identitäts- und Verzeichnisdienste für Ihren cloudbasierten Dienst bereit. Die Aufgaben beim Konfigurieren von Intune zum Verwenden des benutzerdefinierten Domänennamens Ihres Unternehmens sind identisch mit denen bei anderen Azure AD-Mandanten. Daher können Sie sich an den Informationen und Verfahren unter [Hinzufügen Ihrer Domäne](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/) orientieren.

> [!TIP]
> Weitere Informationen zu benutzerdefinierten Domänen finden Sie unter [Konzeptionelle Übersicht über benutzerdefinierte Domänennamen in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Sie können den Namen der Anfangsdomäne „onmicrosoft.com“ nicht umbenennen oder entfernen. Sie können in Intune verwendete benutzerdefinierte Domänennamen hinzufügen, überprüfen oder entfernen, damit Ihre Geschäftsidentität eindeutig bleibt.

## <a name="to-add-and-verify-your-custom-domain"></a>So fügen Sie Ihre benutzerdefinierte Domäne hinzu und überprüfen sie

1. Wechseln Sie zum [Microsoft 365 Admin Center](https://admin.microsoft.com/), und melden Sie sich bei Ihrem Administratorkonto an.

2. Klicken Sie im Navigationsbereich auf **Einstellungen** &gt; **Domänen**.

3. Wählen Sie **Domäne hinzufügen** aus, und geben Sie Ihren benutzerdefinierten Domänennamen ein. Wählen Sie **Weiter** aus.
   ![Screenshot: Microsoft 365 Admin Center, bei dem „Einstellungen“ > „Domänen“ ausgewählt wurde und ein neuer Domänenname hinzugefügt wird](./media/custom-domain-name-configure/domain-custom-add.png)
4. Das Dialogfeld **Domäne überprüfen** öffnet sich und bietet Ihnen die Werte, um den TXT-Eintrag in Ihrem DNS-Hostinganbieter zu erstellen.
    - **GoDaddy-Benutzer**: Das Microsoft 365 Admin Center leitet Sie zur Anmeldeseite von GoDaddy um. Nachdem Sie Ihre Anmeldeinformationen eingegeben und die Vereinbarung über die Erlaubnis für das Ändern der Domäne akzeptiert haben, wird der TXT-Eintrag automatisch erstellt. Alternativ können Sie [den TXT-Eintrag erstellen](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Register.com-Benutzer**: Befolgen Sie die [ausführliche Anleitung](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify), um den TXT-Eintrag zu erstellen.
5. [Möglicherweise müssen Sie zusätzliche DNS-Einträge für Intune-Registrierungen erstellen](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium).

Die Schritte zum Hinzufügen und Überprüfen einer benutzerdefinierten Domäne können auch [in Azure Active Directory ausgeführt werden](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

[Weitere Informationen über Ihre erste onmicrosoft.com-Domäne in Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)

Weitere Informationen über das [Vereinfachen der Windows-Registrierung ohne Azure AD Premium](../enrollment/windows-enroll.md#simplify-windows-enrollment-without-azure-ad-premium) erhalten Sie, indem Sie einen DNS CNAME-Eintrag erstellen, der Registrierungen an Intune-Server weiterleitet.
