---
title: Einrichten einer App-basierten Richtlinie für bedingten Zugriff mit Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie mit Intune eine App-basierte Richtlinie für bedingten Zugriff erstellen.
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
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712836"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Einrichten App-basierter Richtlinien für bedingten Zugriff mit Intune

Richten Sie die App-basierten Richtlinien für bedingten Zugriff für Apps ein, die in der Liste der genehmigten Apps aufgeführt sind. Die Liste der genehmigten Apps enthält Apps, die von Microsoft getestet wurden.

Bevor Sie App-basierte Richtlinien für den bedingten Zugriff verwenden, müssen Sie Ihren Apps [Intune-App-Schutzrichtlinien](../apps/app-protection-policies.md) zugewiesen haben.

> [!IMPORTANT]
> In diesem Artikel werden die einzelnen Schritte erläutert, die notwendig sind, um eine App-basierte Richtlinie für bedingten Zugriff hinzuzufügen. Sie können die gleichen Schritte auch beim Hinzufügen von Apps wie SharePoint Online, Microsoft Teams und Microsoft Exchange Online aus der Liste der genehmigten Apps verwenden.

## <a name="create-app-based-conditional-access-policies"></a>Erstellen App-basierter Richtlinien für bedingten Zugriff

Der bedingte Zugriff ist eine Technologie von Azure Active Directory (Azure AD). Bei dem Knoten für bedingten Zugriff, auf den Sie über *Intune* zugreifen, handelt es sich um denselben Knoten, auf den aus *Azure AD* zugegriffen wird. Da es derselbe Knoten ist, müssen Sie zum Konfigurieren von Richtlinien nicht zwischen Intune und Azure AD wechseln.

Bevor Sie Richtlinien für den bedingten Zugriff über das Microsoft Endpoint Manager Admin Center erstellen können, benötigen Sie eine Azure AD Premium-Lizenz.

### <a name="to-create-an-app-based-conditional-access-policy"></a>So erstellen Sie eine App-basierte bedingte Zugriffsrichtlinie

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Endpunktsicherheit** > **Bedingter Zugriff** > **Neue Richtlinie** aus.

3. Geben Sie einen **Namen** für die Richtlinie ein, und wählen Sie dann unter *Zuweisungen* die Option **Benutzer und Gruppen** aus. Fügen Sie mit den Optionen „Einschließen“ oder „Ausschließen“ Ihre Gruppen für die Richtlinie hinzu, und wählen Sie **Fertig** aus.

4. Wählen Sie **Cloud-Apps oder Aktionen** und die zu schützenden Apps aus. Wählen Sie z.B. **Apps auswählen** und **Office 365 SharePoint Online** sowie **Office 365 Exchange Online** aus.

   Wählen Sie **Fertig** aus, um die Änderungen zu speichern.

5. Wählen Sie **Bedingungen** > **Client-Apps** aus, um die Richtlinie auf Apps und Browser anzuwenden. Wählen Sie z.B. **Ja** aus, und aktivieren Sie dann **Browser** sowie **Mobile Apps und Desktopclients**.

   Wählen Sie **Fertig** aus, um die Änderungen zu speichern.

6. Wählen Sie unter *Zugriffssteuerung* die Option **Gewähren** aus, um den bedingten Zugriff basierend auf der Gerätekonformität anzuwenden. Wählen Sie z.B. **Zugriff gewähren** > **Markieren des Geräts als kompatibel erforderlich** aus.

   Wählen Sie **OK** aus, um die Änderungen zu speichern.

7. Wählen Sie für **Richtlinie aktivieren** die Option **Ein** und dann **Erstellen** aus, um Ihre Änderungen zu speichern.





## <a name="next-steps"></a>Nächste Schritte
[Blockieren von Apps, die keine moderne Authentifizierung verwenden](app-modern-authentication-block.md)

## <a name="see-also"></a>Siehe auch

[Erstellen und Zuweisen von App-Schutzrichtlinien](../apps/app-protection-policies.md)
[Bedingter Zugriff im klassischen Azure-Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
