---
ms.openlocfilehash: 6f5b0c8df86cf5bf1206c1cccb879e37c7944a21
ms.sourcegitcommit: 78f9750712c254d8b123ef15b74f30ca999aa128
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2019
ms.locfileid: "71912761"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Aktivieren der automatischen Registrierung von Windows 10

Durch die automatische Registrierung können Benutzer ihre Windows 10-Geräte in Intune registrieren. Benutzer müssen für die Registrierung ihr Geschäftskonto ihrem persönlichen Gerät hinzufügen oder firmeneigene Geräte mit Azure Active Directory verknüpfen. Im Hintergrund registriert sich das Gerät und tritt Azure Active Directory bei. Nach der Registrierung wird das Gerät mit Intune verwaltet.

**Voraussetzungen**

- Azure Active Directory Premium-Abonnement ([Testabonnement](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-Abonnement

### <a name="configure-automatic-mdm-enrollment"></a>Konfigurieren der automatischen MDM-Registrierung

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, und klicken Sie auf **Azure Active Directory**.

   ![Screenshot des Azure-Portals](../enrollment/media/windows-enroll/auto-enroll-azure-main.png)

2. Wählen Sie **Mobilität (MDM und MAM)** aus.

   ![Screenshot des Azure-Portals](../enrollment/media/windows-enroll/auto-enroll-mdm.png)

3. Wählen Sie **Microsoft Intune** aus.

   ![Screenshot des Azure-Portals](../enrollment/media/windows-enroll/auto-enroll-intune.png)

4. Konfigurieren Sie den **MDM-Benutzerbereich**. Geben Sie an, welche Geräte von Benutzern von Microsoft Intune verwaltet werden sollen. Diese Windows 10-Geräte können sich automatisch für die Verwaltung mit Microsoft Intune registrieren.

   - **Keine**: Automatische MDM-Registrierung ist deaktiviert.
   - **Einige**: Wählen Sie die **Gruppen** aus, die ihre Windows 10-Geräte automatisch registrieren können.
   - **Alle**: Alle Benutzer können ihre Windows 10-Geräte automatisch registrieren.

      > [!IMPORTANT]
      > Für BYOD-Geräte hat der MAM-Benutzerbereich Vorrang, wenn sowohl der MAM- als auch der MDM-Benutzerbereich (automatische MDM-Registrierung) für alle Benutzer aktiviert sind (oder für die gleichen Gruppen von Benutzern). Das Gerät verwendet dann WIP-Richtlinien (Windows Information Protection) (sofern Sie diese konfiguriert haben) und wird nicht für die mobile Geräteverwaltung registriert.
      >
      > Für unternehmenseigene Geräte hat der MDM-Benutzerbereich Vorrang, wenn beide Bereiche aktiviert sind. Die Geräte werden für die mobile Geräteverwaltung registriert.

   > [!NOTE]
   > Der MDM-Benutzerbereich muss auf eine Azure AD-Gruppe eingestellt sein, die Benutzerobjekte enthält.

   ![Screenshot des Azure-Portals](../enrollment/media/windows-enroll/auto-enroll-scope.png)

5. Verwenden Sie die Standardwerte für die folgenden URLs:
    - **URL für MDM-Nutzungsbedingungen**
    - **URL für MDM-Ermittlung**
    - **MDM Compliance-URL**

6. Wählen Sie **Speichern** aus.

Standardmäßig ist die zweistufige Authentifizierung für den Dienst nicht aktiviert. Die zweistufige Authentifizierung wird jedoch empfohlen, wenn Sie ein Gerät registrieren. Für die zweistufige Authentifizierung müssen Sie einen Anbieter für die zweistufige Authentifizierung in Azure AD konfigurieren. Außerdem müssen Sie Ihre Benutzerkonten für die mehrstufige Authentifizierung konfigurieren. Weitere Informationen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication-Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
