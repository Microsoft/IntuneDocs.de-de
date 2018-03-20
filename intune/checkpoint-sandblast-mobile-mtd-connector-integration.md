---
title: Check Point SandBlast MTD in Microsoft Intune
titlesuffix: 
description: "Einrichten von CheckPoint SandBlast Mobile Threat Defense (MTD) in Intune, um den Zugriff von mobilen Geräten auf Ihre Unternehmensressourcen zu steuern."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b864d78fd7bfd7fb4e177b568b3587bc1e28b209
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>Integrieren von Check Point SandBlast Mobile in Intune

## <a name="before-you-begin"></a>Vorbereitung

> [!NOTE] 
> Folgende Schritte müssen in der [Check Point SandBlast Mobile MTD-Konsole](https://intune-4.eu1.locsec.net/) ausgeführt werden.

Stellen Sie vor der Integration von Check Point SandBlast Mobile in Intune sicher, dass Sie über Folgendes verfügen:

-   Microsoft Intune-Abonnement

-   Azure Active Directory-Administratoranmeldeinformationen zum Erteilen folgender Berechtigungen:

    -   Anmelden und Lesen des Benutzerprofils

    -   Zugriff auf das Verzeichnis als angemeldeter Benutzer

    -   Lesen der Verzeichnisdaten

    -   Senden von Geräteinformationen an Intune

-   Administratoranmeldeinformationen für den Zugriff auf die Check Point SandBlast Mobile MTD-Konsole.

### <a name="check-point-sandblast-app-authorization"></a>Autorisierung der Check Point SandBlast-App

Der Autorisierungsprozess der Check Point SandBlast-App umfasst Folgendes:

-   Der Check Point SandBlast Mobile-Dienst darf Informationen zum Integritätszustand des Geräts wieder an Intune übertragen.

-   Check Point SandBlast Mobile wird mit der Azure AD Enrollment Group-Mitgliedschaft synchronisiert, um die Datenbank des Geräts aufzufüllen.

-   Die Check Point SandBlast-Verwaltungskonsole darf Azure AD-SSO (Single Sign On, SSO) verwenden.

-   Die Check Point SandBlast Mobile-App darf sich über Azure AD-SSO anmelden.

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>So richten Sie die Check Point SandBlast Mobile-Integration ein

1.  Wechseln Sie zu [Check Point SandBlast Mobile MTD-Konsole](https://intune-4.eu1.locsec.net/), und melden Sie sich mit Ihren Anmeldeinformationen an.

2.  Klicken Sie auf die Registerkarte **Einstellungen**.

3.  Wählen Sie **Geräteverwaltung** aus, und klicken Sie anschließend auf **Einstellungen**.

4.  Wählen Sie **Microsoft Intune** aus der Dropdown-Liste **MDM-Dienst** aus.

5.  Nachdem Sie Microsoft Intune als MDM-Dienst festgelegt haben, wird das Fenster **Microsoft Intune-Konfiguration** geöffnet. Wählen Sie für jede Geräteplattform (iOS, Android und Windows) **Zu eigener Organisation hinzufügen** aus, um Check Point SandBlast Mobile für die Kommunikation mit Intune und Azure AD zu autorisieren.

    ![Abbildung der Check Point MTD-Konfiguration in Intune](./media/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > Sie müssen alle Geräteplattformen hinzufügen, um mit dem nächsten Schritt fortfahren zu können.

6.  Wählen Sie **Annehmen** aus, um die Check Point SandBlast Mobile-App für die Kommunikation mit Intune und Azure Active Directory zu autorisieren.

7.  Nachdem Sie alle Geräteplattformen aktiviert haben, müssen Sie die Azure AD-Sicherheitsgruppe eingeben.

8.  Wählen Sie **Überprüfen** aus. Wählen Sie **Speichern** aus, sobald die Azure AD-Sicherheitsgruppe erfolgreich überprüft wurde.

## <a name="next-steps"></a>Nächste Schritte

- [Einrichten von Check Point SandBlast Mobile-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)