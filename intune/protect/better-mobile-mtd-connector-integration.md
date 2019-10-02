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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ef94fff88c4318d6e3d387a58ca8359467fcc028
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721733"
---
# <a name="integrate-better-mobile-with-intune"></a>Integrieren von Better Mobile in Intune

Führen Sie die folgenden Schritte aus, um die Better Mobile Threat Defense-Lösung in Intune zu integrieren.

## <a name="before-you-begin"></a>Vorbereitung

> [!NOTE]
> Die folgenden Schritte müssen in der [Better Mobile-Verwaltungskonsole](https://aad.bmobi.net) ausgeführt werden.

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

- [Set up Better Client apps (Einrichten besserer Client-Apps)](mtd-apps-ios-app-configuration-policy-add-assign.md)
