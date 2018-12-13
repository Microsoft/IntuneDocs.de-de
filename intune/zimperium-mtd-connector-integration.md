---
title: Integrieren von Zimperium MTD in Microsoft Intune
titleSuffix: ''
description: Einrichten der Zimperium Mobile Threat Defense-Lösung (MTD) in Microsoft Intune, um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 3f2ffb3f99ce0dc925c52f733b25292cdbddae3e
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52860995"
---
# <a name="integrate-zimperium-with-intune"></a>Integrieren von Zimperium in Intune

Führen Sie die folgenden Schritte durch, um die Zimperium Mobile Threat Defense-Lösung in Intune zu integrieren.

## <a name="before-you-begin"></a>Vorbereitung

> [!NOTE]
> Die folgenden Schritte sollen in der  [Zimperium-MTD-Konsole](https://sso.zimperium.com/signon/aad/) ausgeführt werden.

Stellen Sie vor der Integration von Zimperium in Intune sicher, dass Sie über folgendes Abonnement und folgende Anmeldeinformationen verfügen:

-   Microsoft Intune-Abonnement

-   Anmeldeinformationen als globaler Azure Active Directory-Administrator zum Erteilen folgender Berechtigungen:

    -   Anmelden und Lesen des Benutzerprofils

    -   Zugriff auf das Verzeichnis als angemeldeter Benutzer

    -   Lesen der Verzeichnisdaten

    -   Senden von Geräteinformationen an Intune

-   Administratoranmeldeinformationen für den Zugriff auf die Zimperium MTD-Konsole

### <a name="zimperium-app-authorization"></a>Zimperium-App-Autorisierung

Der Prozess zur Autorisierung der App Zimperium umfasst Folgendes:

-   Erteilen Sie dem Zimperium-Dienst die Berechtigung zum Übertragen von Informationen zum Integritätszustand des Geräts an Intune. Um diese Berechtigungen zu gewähren, müssen Sie über Anmeldeinformationen als globaler Administrator verfügen. Die Berechtigungen können in einem Arbeitsschritt erteilt werden. Nach der Berechtigungserteilung sind keine Anmeldeinformationen als globaler Administrator für täglich ausgeführte Vorgänge erforderlich.

-   Zimperium wird mit der Azure Active Directory (AD) Enrollment Group-Mitgliedschaft synchronisiert, um die Datenbank des Geräts aufzufüllen.

-   Die Zimperium-Verwaltungskonsole darf Azure AD-SSO (Single Sign On) verwenden.

-   Die Zimperium-App darf für die Anmeldung Azure AD-SSO verwenden.

Weitere Informationen zu Einwilligung und Azure Active Directory-Anwendungen finden Sie unter [Anfordern der Berechtigungen von einem Verzeichnisadministrator](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) im Artikel *Berechtigungen und Einwilligung im Azure Active Directory v2.0-Endpunkt*.


## <a name="to-set-up-zimperium-integration"></a>Einrichten der Zimperium-Integration

1.  Wechseln Sie zur  [Zimperium-MTD-Konsole](https://sso.zimperium.com/signon/aad/) , und melden Sie sich mit Ihren Anmeldeinformationen an. Um die Zimperium-Integration einzurichten, müssen Sie sich als ein Azure Active Directory-Benutzer anmelden, dem die Rolle „Globaler Administrator“ zugewiesen ist. Bei dieser einmaligen Einrichtung werden Rechte als globaler Administrator benötigt, um den Zimperium-Apps die Berechtigung zur Kommunikation mit Intune in Ihrer Organisation zu gewähren. 

2.  Wählen Sie im linken Menü **Management** (Verwaltung) aus.

3.  Klicken Sie auf die Registerkarte **MDM settings** (MDM-Einstellungen).

4.  Wählen Sie **Add MDM** (MDM hinzufügen) aus, und wählen Sie dann **Microsoft Intune** in der Liste **MDM provider** (MDM-Anbieter) aus.

5.  Nachdem Sie Microsoft Intune als MDM-Dienst festgelegt haben, wird das Fenster  **Microsoft Intune Configuration**  (Microsoft Intune-Konfiguration) geöffnet. Wählen Sie in diesem Fenster für jede Option  **Add Azure Active Directory**  (Azure Active Directory hinzufügen) aus: **Zimperium zConsole**, **zIPS iOS and Android apps** (zIPS iOS und Android-Apps). Auf diese Weise wird Zimperium zur Kommunikation mit Intune und Azure AD über Azure AD-SSO (Single Sign-On, einmaliges Anmelden) autorisiert.

    > [!IMPORTANT]  
    > Sie müssen Zimperium zConsole, zIPS iOS und Android-Apps hinzufügen, um die Integration mit Intune abzuschließen.

6.  Klicken Sie auf  **Annehmen** , um die Zimperium-App für die Kommunikation mit Intune und Azure Active Directory zu autorisieren.

7.  Nachdem Sie **Zimperium zConsole** sowie **zIPS iOS und Android-Apps** zu Azure AD hinzugefügt haben, fügen Sie die Azure AD-Sicherheitsgruppen hinzu. Dadurch kann Zimperium die Azure AD-Sicherheitsgruppe mit seinem Dienst synchronisieren.

8.  Klicken Sie auf  **Fertig stellen**, um die Konfiguration zu speichern und die erste Azure AD-Sicherheitsgruppensynchronisierung zu starten.

9.  Melden Sie sich von der Zimperium MTD-Konsole ab.

## <a name="next-steps"></a>Nächste Schritte

-   [Einrichten von Zimperium-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
