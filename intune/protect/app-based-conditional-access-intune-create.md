---
title: Einrichten einer App-basierten Richtlinie für bedingten Zugriff mit Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie mit Intune eine App-basierte Richtlinie für bedingten Zugriff erstellen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9cbe57d0cf69f036cd36d2c1b95c48b198645e7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723085"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Einrichten App-basierter Richtlinien für bedingten Zugriff mit Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Richten Sie die App-basierten bedingten Zugriffsrichtlinien für Apps ein, die in der Liste der genehmigten Apps aufgeführt sind. Die Liste der genehmigten Apps enthält Apps, die von Microsoft getestet wurden.

> [!IMPORTANT]
> In diesem Artikel werden die einzelnen Schritte erläutert, die notwendig sind, um eine App-basierte Richtlinie für bedingten Zugriff hinzuzufügen. Sie können die gleichen Schritte auch beim Hinzufügen von Apps wie SharePoint Online, Microsoft Teams und Microsoft Exchange Online aus der Liste der genehmigten Apps verwenden.

## <a name="create-app-based-conditional-access-policies"></a>Erstellen App-basierter Richtlinien für bedingten Zugriff
Der bedingte Zugriff ist eine Technologie von Azure Active Directory (Azure AD). Bei dem Knoten für bedingten Zugriff, auf den aus *Intune* zugegriffen wird, handelt es sich um denselben Knoten, auf den aus *Azure AD* zugegriffen wird. Dies bedeutet, dass Sie zum Konfigurieren von Richtlinien nicht zwischen Intune und Azure AD wechseln müssen.

> [!IMPORTANT]
> Sie benötigen eine Azure AD Premium-Lizenz, um im Intune-Portal Richtlinien für den bedingten Zugriff zu erstellen.

### <a name="to-create-an-app-based-conditional-access-policy"></a>So erstellen Sie eine App-basierte bedingte Zugriffsrichtlinie

> [!IMPORTANT]
> Bevor Sie App-basierte Richtlinien für den bedingten Zugriff verwenden, müssen Sie Ihren Apps [Intune-App-Schutzrichtlinien](../apps/app-protection-policies.md) zugewiesen haben.

1. Wählen Sie auf dem **Intune-Dashboard** die Option **Bedingter Zugriff** aus.

2. Wählen Sie in dem Bereich **Richtlinien** die Option **Neue Richtlinie** aus, um Ihre neue App-basierte Richtlinie für bedingten Zugriff zu erstellen.

4. Sobald Sie einen Richtliniennamen eingegeben haben und die verfügbaren Einstellungen im Abschnitt **Zuweisungen** konfiguriert haben, wählen Sie im Abschnitt **Zugriffskontrollen** **Gewähren** aus.

5. Wählen Sie **Genehmigte Client-App erforderlich**, **Auswählen** und anschließend **Erstellen** aus, um die neue Richtlinie zu speichern.

## <a name="next-steps"></a>Nächste Schritte
[Blockieren von Apps, die keine moderne Authentifizierung verwenden](app-modern-authentication-block.md)

## <a name="see-also"></a>Siehe auch

[Erstellen und Zuweisen von App-Schutzrichtlinien](../apps/app-protection-policies.md)
[Bedingter Zugriff im klassischen Azure-Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
