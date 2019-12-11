---
ms.openlocfilehash: 8483ed3d4198e228bdaaf4723b2c9c0dca9cecfc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71830508"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Anforderungen an die Anmeldeinformationen für Azure AD und Intune

Authentifizierung und Autorisierung basieren auf Azure AD-Anmeldeinformationen und rollenbasierter Zugriffssteuerung über Intune (RBAC). Alle globalen Administratoren und Intune-Serviceadministratoren für Ihren Mandanten haben standardmäßig Zugriff auf das Data Warehouse. Verwenden Sie Intune-Rollen, um den Zugriff für mehr Benutzer bereitzustellen, indem Sie ihnen Zugriff auf die Ressource **Intune Data Warehouse** gewähren.

Anforderungen für den Zugriff auf das Intune Data Warehouse (einschließlich der API):

- Benutzer muss eine der folgenden Rollen innehaben:
  - Globaler Azure AD-Administrator
  - Intune-Dienstadministrator
  - Benutzer mit einem rollenbasierten Zugriff auf die **Intune Data Warehouse**-Ressource
  - Benutzerunabhängige Authentifizierung verwenden [Nur-Anwendung-Authentifizierung](../developer/data-warehouse-app-only-auth.md) 
