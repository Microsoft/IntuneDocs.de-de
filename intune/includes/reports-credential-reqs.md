---
ms.openlocfilehash: 6ec8f8a613d3b0a0b17f2615de634e70fa282fd7
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68229247"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Anforderungen an die Anmeldeinformationen für Azure AD und Intune

Authentifizierung und Autorisierung basieren auf Azure AD-Anmeldeinformationen und rollenbasierter Zugriffssteuerung über Intune (RBAC). Alle globalen Administratoren und Intune-Serviceadministratoren für Ihren Mandanten haben standardmäßig Zugriff auf das Data Warehouse. Verwenden Sie Intune-Rollen, um den Zugriff für mehr Benutzer bereitzustellen, indem Sie ihnen Zugriff auf die Ressource **Intune Data Warehouse** gewähren.

Anforderungen für den Zugriff auf das Intune Data Warehouse (einschließlich der API):

- Benutzer muss eine der folgenden Rollen innehaben:
  - Globaler Azure AD-Administrator
  - Intune-Dienstadministrator
  - Benutzer mit einem rollenbasierten Zugriff auf die **Intune Data Warehouse**-Ressource
  - Benutzerunabhängige Authentifizierung verwenden [Nur-Anwendung-Authentifizierung](../data-warehouse-app-only-auth.md) 
