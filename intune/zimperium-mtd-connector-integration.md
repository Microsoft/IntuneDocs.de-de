---
title: Integrieren von Zimperium MTD in Microsoft Intune
titleSuffix: ''
description: Einrichten der Zimperium Mobile Threat Defense-Lösung (MTD) in Microsoft Intune, um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 68896a363cab37aabe9a597872da0fe75c44c473
ms.sourcegitcommit: 3903f20cb5686532ccd8c36aa43c5150cee7cca2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "52267236"
---
# <a name="integrate-zimperium-with-intune"></a>Integrieren von Zimperium in Intune

Führen Sie die folgenden Schritte durch, um die Zimperium Mobile Threat Defense-Lösung in Intune zu integrieren.

## <a name="before-you-begin"></a>Vorbereitung

> [!NOTE]
> Die folgenden Schritte sollen in der  [Zimperium-MTD-Konsole](https://sso.zimperium.com/signon/aad/) ausgeführt werden.

Stellen Sie vor der Integration von Zimperium in Intune sicher, dass Sie über folgendes Abonnement und folgende Anmeldeinformationen verfügen:

-   Microsoft Intune-Abonnement

-   Azure Active Directory-Administratoranmeldeinformationen zum Erteilen folgender Berechtigungen:

    -   Anmelden und Lesen des Benutzerprofils

    -   Zugriff auf das Verzeichnis als angemeldeter Benutzer

    -   Lesen der Verzeichnisdaten

    -   Senden von Geräteinformationen an Intune

-   Administratoranmeldeinformationen für den Zugriff auf die Zimperium MTD-Konsole

### <a name="zimperium-app-authorization"></a>Zimperium-App-Autorisierung

Der Prozess zur Autorisierung der App Zimperium umfasst Folgendes:

-   Der Zimperium-Dienst darf Informationen zum Integritätszustand des Geräts an Intune übertragen.

-   Zimperium wird mit der Azure Active Directory (AD) Enrollment Group-Mitgliedschaft synchronisiert, um die Datenbank des Geräts aufzufüllen.

-   Die Zimperium-Verwaltungskonsole darf Azure AD-SSO (Single Sign On) verwenden.

-   Die Zimperium-App darf für die Anmeldung Azure AD-SSO verwenden.

## <a name="to-set-up-zimperium-integration"></a>Einrichten der Zimperium Integration

1.  Wechseln Sie zur  [Zimperium-MTD-Konsole](https://sso.zimperium.com/signon/aad/) , und melden Sie sich mit Ihren Anmeldeinformationen an.

2.  Wählen Sie im linken Menü **Verwaltung** aus.

3.  Klicken Sie auf die Registerkarte **MDM settings** (MDM-Einstellungen).

4.  Wählen Sie **Add MDM** (MDM hinzufügen) aus, und wählen Sie dann **Microsoft Intune** aus der Liste der **MDM-Anbieter** aus.

5.  Nachdem Sie Microsoft Intune als MDM-Dienst festgelegt haben, öffnet sich das Fenster zur  **Microsoft Intune-Konfiguration** . Wählen Sie für jede Option  **Azure Active Directory hinzufügen**  aus: **Zimperium zConsole** und **zIPS-Apps für iOS- und Android** zur Autorisierung von Zimperium für die Kommunikation mit Intune und Azure AD über Azure AD-SSO.

    > [!IMPORTANT]
    > Sie müssen die iOS- und Android-Apps Zimperium zConsole und zIPS hinzufügen, um den Integrationsvorgang in Intune abzuschließen.

6.  Klicken Sie auf  **Annehmen** , um die Zimperium-App für die Kommunikation mit Intune und Azure Active Directory zu autorisieren.

7.  Nachdem Sie die **iOS- und Android-Apps Zimperium zConsole** und **zIPS** zu Azure AD hinzugefügt haben, fügen Sie die Azure AD-Sicherheitsgruppen hinzu. Dadurch kann Zimperium die Azure AD-Sicherheitsgruppe mit seinem Dienst synchronisieren.

8.  Klicken Sie auf  **Fertig stellen**, um die Konfiguration zu speichern und die erste Azure AD-Sicherheitsgruppensynchronisierung zu starten.

## <a name="next-steps"></a>Nächste Schritte

-   [Einrichten von Zimperium-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
