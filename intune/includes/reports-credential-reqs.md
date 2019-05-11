---
ms.openlocfilehash: 015e50d24149a6b6242eda86d5f3d62489e9955d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511328"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Anforderungen an die Anmeldeinformationen für Azure AD und Intune

Authentifizierung und Autorisierung basieren auf Azure AD-Anmeldeinformationen und rollenbasierter Zugriffssteuerung über Intune (RBAC). Alle globalen Administratoren und Intune-Serviceadministratoren für Ihren Mandanten haben standardmäßig Zugriff auf das Data Warehouse. Verwenden Sie Intune-Rollen, um den Zugriff für mehr Benutzer bereitzustellen, indem Sie ihnen Zugriff auf die Ressource **Intune Data Warehouse** gewähren.

Anforderungen für den Zugriff auf das Intune Data Warehouse (einschließlich der API):

  -  Benutzer muss eine der folgenden Rollen innehaben:
      -  Globaler Azure AD-Administrator
      -  Intune-Dienstadministrator
      -  Benutzer mit einem rollenbasierten Zugriff auf die **Intune Data Warehouse**-Ressource
      -  Benutzerunabhängige Authentifizierung verwenden [Nur-Anwendung-Authentifizierung](../data-warehouse-app-only-auth.md) 
