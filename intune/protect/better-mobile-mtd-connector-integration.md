---
title: Einrichten der Better Mobile-Integration in Intune
titleSuffix: Intune on Azure
description: Better Mobile-Connectorintegration in Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0528ec962165f358b35afce98f58c8b9b4efe93c
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810325"
---
# <a name="integrate-better-mobile-with-intune"></a>Integrieren von Better Mobile in Intune

Führen Sie die folgenden Schritte aus, um die Better Mobile Threat Defense-Lösung in Intune zu integrieren.

## <a name="before-you-begin"></a>Vorbereitung

Die folgenden Schritte werden in der [Better Mobile-Administratorkonsole](https://aad.bmobi.net) ausgeführt und ermöglichen das Herstellen einer Verbindung mit dem Better Mobile-Dienst für in Intune registrierte Geräte (per Gerätekonformität) und für nicht registrierte Geräte (per App-Schutzrichtlinien).

Stellen Sie vor der Integration von Better Mobile in Intune sicher, dass Sie über Folgendes verfügen:

- Microsoft Intune-Abonnement

- Azure Active Directory-Administratoranmeldeinformationen zum Erteilen folgender Berechtigungen:

  - Anmelden und Lesen des Benutzerprofils

  - Zugriff auf das Verzeichnis als angemeldeter Benutzer

  - Lesen der Verzeichnisdaten

  - Senden von Geräteinformationen an Intune

- Administratoranmeldeinformationen für den Zugriff auf die Better Mobile-Verwaltungskonsole

### <a name="better-mobile-app-authorization"></a>Better Mobile-App-Autorisierung

Der Prozess zur Autorisierung der Better Mobile-App umfasst Folgendes:

- Erteilen Sie dem Better Mobile-Dienst die Berechtigung, Informationen zum Integritätszustand des Geräts an Intune zu übertragen.

- Better Mobile wird mit der Azure AD Enrollment Group-Mitgliedschaft synchronisiert, um die Datenbank des Geräts aufzufüllen.

- Erteilen Sie der Better Mobile-Verwaltungskonsole die Berechtigung, Azure AD-SSO (Single Sign On) zu verwenden.

- Erteilen Sie der Better Mobile-App die Berechtigung, die Azure AD-SSO-Anmeldung zu verwenden.

## <a name="to-set-up-better-mobile-integration"></a>So richten Sie die Better Mobile-Integration ein

1. Wechseln Sie zur [Better Mobile-Verwaltungskonsole](https://aad.bmobi.net), und melden Sie sich mit Ihren Anmeldeinformationen an.
2. Wählen Sie **Integration** > **EMM/MDM** > **KONTO HINZUFÜGEN** aus.

     ![Screenshot der Better Mobile-Verwaltungskonsole](./media/better-mobile-mtd-connector-integration/better_mobile_console.png)
 
3. Wählen Sie **Intune** aus.
4. Geben Sie neben **KONTONAME** einen Deskriptor ein. 
5. Geben Sie im Fenster **Microsoft-Anmeldung** Ihre Intune-Anmeldeinformationen ein.
6. Wählen Sie im Fenster **Angeforderte Berechtigungen** die Option **Annehmen** aus.
7. Suchen Sie nach den Azure AD-Sicherheitsgruppen, aus denen Better Mobile Geräte synchronisieren soll, und wählen Sie sie in der Liste aus. Wählen Sie dann **Weiter** aus.
8. Wählen Sie **Fertig** aus.
9. Die Seite **Konto hinzufügen** wird erneut angezeigt. Schließen Sie die Seite. 

## <a name="next-steps"></a>Nächste Schritte

- [Einrichten von Better Mobile-Apps für registrierte Geräte](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Einrichten von Better Mobile-Apps für nicht registrierte Geräte](~/protect/mtd-add-apps-unenrolled-devices.md)
