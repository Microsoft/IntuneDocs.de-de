---
title: Anfordern der mehrstufigen Authentifizierung für die Intune-Geräteregistrierung
titlesuffix: Microsoft Intune
description: Anfordern der mehrstufigen Authentifizierung in Azure AD für die Intune-Geräteregistrierung.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
ms.custom: intune-azure
ms.openlocfilehash: 5b2c2bb6e76bd6b2da7ee7c12282c0ff22d7d3e3
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
ms.locfileid: "31617208"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Erfordert mehrstufige Authentifizierung für Intune-Geräteregistrierungen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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
2. Wählen Sie im Portal **Azure Active Directory** aus.
2. Wählen Sie in **Azure Active Directory** **Verwalten** > **Unternehmensanwendungen** aus.
3. Wählen Sie unter **Unternehmensanwendungen** die Optionen **Verwalten** > **Alle Anwendungen** aus. Daraufhin sehen Sie eine Liste aller Azure-Apps, die Sie verwalten.
3. Wählen Sie aus dieser Liste **Microsoft Intune enrollment** (Microsoft Intune-Registrierung) aus.
4. Wählen Sie unter **Microsoft Intune-Registrierung** die Optionen **Sicherheit** > **Bedingter Zugriff** aus.
5. Wählen Sie **Neue Richtlinie** aus.
6. Geben Sie unter **Neue Richtlinie** einen beschreibenden Namen für die Richtlinie ein.
7. Wählen Sie im Abschnitt **Zuweisungen** die Option **Benutzer und Gruppen** aus.
8. Wählen Sie unter **Benutzer und Gruppen** die Benutzer oder Gruppen aus, die diese Richtlinie empfangen sollen, und klicken Sie dann auf **Fertig**.
9. Wählen Sie im Abschnitt **Zuweisungen** die Option **Cloud-Apps** aus.
10. Wählen Sie auf der Registerkarte **Einbeziehen** von **Cloud-Apps** die Option **Apps auswählen** aus, klicken Sie dann auf **Auswählen** > **Microsoft Intune-Registrierung**, und klicken Sie dann auf **Fertig**.
11. Wählen Sie im Abschnitt **Zuweisungen** die Option **Bedingungen** aus.
12. Sie müssen unter **Bedingungen** keine Einstellungen für MFA konfigurieren.
13. Wählen Sie im Abschnitt **Zugriffssteuerung** die Option **Erteilen** aus.
14. Wählen Sie unter **Erteilen** die Option **Zugriff gewähren** aus, und wählen Sie dann **Mehrstufige Authentifizierung anfordern** aus.
    Wählen Sie nicht **Markieren des Geräts als kompatibel erforderlich** aus, da ein Gerät vor der Registrierung nicht auf Kompatibilität geprüft werden kann.
15. Klicken Sie auf **Auswählen**.
16. Wählen Sie unter **Neue Richtlinie** die Optionen **Richtlinie aktivieren** > **An** aus, und klicken Sie dann auf **Erstellen**.



## <a name="next-steps"></a>Nächste Schritte

Wenn Benutzer ihre Geräte registrieren, müssen Sie sich jetzt mit einer zweiten Identifikationsart, z.B. mit einer PIN, einer Telefonnummer oder mit biometrischen Daten authentifizieren.
