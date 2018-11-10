---
title: Einrichten einer App-basierten Richtlinie für bedingten Zugriff mit Intune
description: Erfahren Sie, wie Sie mit Intune eine App-basierte Richtlinie für bedingten Zugriff erstellen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ba5035dfcbab4b938b1ed31786ad0f70dceb2d8c
ms.sourcegitcommit: b165a38b5d6de396f2edab6411742cb50a9b8816
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50253469"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Einrichten App-basierter Richtlinien für bedingten Zugriff mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Richten Sie die App-basierten bedingten Zugriffsrichtlinien für Apps ein, die in der Liste der genehmigten Apps aufgeführt sind. Die Liste der genehmigten Apps enthält Apps, die von Microsoft getestet wurden.

> [!IMPORTANT]
> In diesem Artikel werden die einzelnen Schritte erläutert, die notwendig sind, um eine App-basierte Richtlinie für bedingten Zugriff hinzuzufügen. Sie können die gleichen Schritte auch beim Hinzufügen von Apps wie SharePoint Online, Microsoft Teams und Microsoft Exchange Online aus der Liste der genehmigten Apps verwenden.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Erstellen von App-basierten Richtlinien für den bedingten Zugriff in der Azure AD-Workload

IT-Administratoren können App-basierte Richtlinien für den bedingten Zugriff über die Azure AD-Workload erstellen. Mit diesem Zugriff müssen Sie nicht zwischen den Azure- und Intune-Workloads wechseln.

> [!IMPORTANT]
> Sie benötigen eine Azure AD Premium-Lizenz, um im Azure-Portal für Intune Azure AD-Richtlinien für den bedingten Zugriff zu erstellen.

### <a name="to-create-an-app-based-conditional-access-policy"></a>So erstellen Sie eine App-basierte bedingte Zugriffsrichtlinie

> [!IMPORTANT]
> Bevor Sie App-basierte Richtlinien für den bedingten Zugriff verwenden, müssen Sie Ihren Apps [Intune-App-Schutzrichtlinien](app-protection-policies.md) zugewiesen haben.

1. Wählen Sie auf dem **Intune-Dashboard** die Option **Bedingter Zugriff** aus.

2. Wählen Sie im Bereich **Richtlinien** die Option **Neue Richtlinie** aus, um Ihre neue App-basierte Richtlinie für bedingten Zugriff zu erstellen.

4. Sobald Sie einen Richtliniennamen eingegeben haben und die verfügbaren Einstellungen im Abschnitt **Zuweisungen** konfiguriert haben, wählen Sie im Abschnitt **Zugriffskontrollen** **Gewähren** aus.

5. Wählen Sie **Genehmigte Client-App erforderlich**, **Auswählen** und anschließend **Erstellen** aus, um die neue Richtlinie zu speichern.

## <a name="next-steps"></a>Nächste Schritte
[Blockieren von Apps, die keine moderne Authentifizierung verwenden](app-modern-authentication-block.md)

### <a name="see-also"></a>Siehe auch

[Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md)
[Bedingter Zugriff im klassischen Azure-Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
