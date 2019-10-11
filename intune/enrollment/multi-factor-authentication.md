---
title: Anfordern der mehrstufigen Authentifizierung für die Intune-Geräteregistrierung
titleSuffix: Microsoft Intune
description: Anfordern der mehrstufigen Authentifizierung in Azure AD für die Intune-Geräteregistrierung.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea6af0fd71acb7aad22930c6173540e3aece4f98
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726374"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Erfordert mehrstufige Authentifizierung für Intune-Geräteregistrierungen

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune kann die mehrstufige Authentifizierung (MFA) von Azure AD für die Geräteregistrierung verwenden, damit Sie Ihre Unternehmensressourcen sichern können.

MFA funktioniert, da zwei oder mehr der folgenden Überprüfungsmethoden erforderlich sind:

- Etwas, das Sie kennen (normalerweise ein Kennwort oder eine PIN)
- Etwas, das Sie besitzen (ein vertrauenswürdiges Gerät, das nicht auf einfache Weise dupliziert werden kann, z.B. ein Telefon)
- Etwas Biometrisches (z.B. ein Fingerabdruck)

MFA wird für iOS-, Android-, Windows 8.1-Geräte oder höher und Windows Phone 8.1-Geräte oder mobile Windows 10-Geräte oder höher unterstützt.

Wenn Sie MFA aktivieren, müssen Benutzer zwei Formen von Anmeldeinformationen angeben, um ein Gerät zu registrieren.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Konfigurieren von Intune für das Anfordern der mehrstufigen Authentifizierung bei der Geräteregistrierung

Befolgen Sie die folgenden Schritte, um MFA anzufordern, wenn ein Gerät registriert wird:

>[!Important]
>Ihren Benutzern muss ein Azure Active Directory Premium P1-Abonnement oder höher zugewiesen sein, damit Sie diese Richtlinie implementieren können.

>[!Important]
>Konfigurieren Sie keine **gerätebasierten Zugriffsregeln** für die Microsoft Intune-Registrierung.

1. Melden Sie sich mit Ihren Anmeldeinformationen beim [Microsoft Azure-Portal](https://portal.azure.com) an.
2. Wechseln Sie im Portal zu **Intune**, und wählen Sie **Bedingter Zugriff** aus. Bei dem Knoten für bedingten Zugriff, auf den aus *Intune* zugegriffen wird, handelt es sich um denselben Knoten, auf den aus *Azure AD* zugegriffen wird.
4. Wählen Sie **Neue Richtlinie** aus.
5. Geben Sie unter **Neue Richtlinie** einen beschreibenden Namen für die Richtlinie ein.
6. Wählen Sie im Abschnitt **Zuweisungen** die Option **Benutzer und Gruppen** aus. 
7. Klicken Sie unter **Benutzer und Gruppen** auf **Select users or groups** (Benutzer oder Gruppen auswählen), und aktivieren Sie das Kontrollkästchen für **Benutzer und Gruppen**. Wählen Sie dann die Benutzer und/oder Gruppen aus, für die diese Richtlinie gelten soll, und klicken Sie anschließend auf **Fertig**.
8. Wählen Sie im Abschnitt **Zuweisungen** die Option **Cloud-Apps** aus.
9. Wählen Sie auf der Registerkarte **Einbeziehen** von **Cloud-Apps** die Option **Apps auswählen** aus, klicken Sie dann auf **Auswählen** > **Microsoft Intune-Registrierung**, und klicken Sie dann auf **Fertig**.
10. Sie müssen im Abschnitt **Zuweisungen** unter **Bedingungen** keine Einstellungen für die mehrstufige Authentifizierung konfigurieren.
11. Wählen Sie im Abschnitt **Zugriffssteuerung** die Option **Erteilen** aus.
12. Wählen Sie unter **Erteilen** die Option **Zugriff gewähren** aus, und wählen Sie dann **Mehrstufige Authentifizierung anfordern** aus. Wählen Sie nicht **Markieren des Geräts als kompatibel erforderlich** aus, da ein Gerät vor der Registrierung nicht auf Kompatibilität geprüft werden kann. Klicken Sie anschließend auf **Auswählen**.
13. Wählen Sie unter **Neue Richtlinie** die Optionen **Richtlinie aktivieren** > **An** aus, und klicken Sie dann auf **Erstellen**.



## <a name="next-steps"></a>Nächste Schritte

Wenn Benutzer ihre Geräte registrieren, müssen Sie sich jetzt mit einer zweiten Identifikationsart, z.B. mit einer PIN, einer Telefonnummer oder mit biometrischen Daten authentifizieren.
