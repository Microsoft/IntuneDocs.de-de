---
title: Einrichten der Skycure-Integration in Intune
description: Richten Sie die Skycure-Integration mit Microsoft Intune ein.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 93722f66-7641-4a3f-b1fb-3a0a58a36675
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 63713cd46da1d1222ec5766a55a7e7344a0a0d26
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-the-skycure-integration-with-intune"></a>Einrichten der Skycure-Integration in Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie müssen Skycure-Apps in Azure AD für SSO-Funktionen hinzufügen.

## <a name="before-you-begin"></a>Vorbereitung

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>Azure AD-Konto, mit dem Intune und Skycure integriert werden

-   Stellen Sie sicher, dass das Azure AD-Konto ordnungsgemäß in der [Skycure-Verwaltungskonsole](https://aad.skycure.com) konfiguriert ist, bevor Sie den grundlegenden Skycure-Installationsvorgang starten.

### <a name="full-integration-vs-read-only"></a>Die vollständige Integration unterstützt im Vergleich zu Read-only

Skycure unterstützt zwei Integrationsweisen mit Intune:

-   **Schreibgeschützte Integration (Grundlegende Installation):** Inventarisiert nur Geräte aus Azure Active Directory und füllt sie in der Skycure-Konsole auf.
<br>
    -   Wenn in der Skycure-Verwaltungskonsole **Report the health and risk of devices to Intune** (Integrität und Risiken der Geräte an Intune melden) und **Also report security incidents to Intune** (Auch Sicherheitsvorfälle an Intune melden) nicht aktiviert sind, ist die Integration schreibgeschützt, und ein Gerätestatus („kompatibel“ oder „nicht kompatibel“) wird in Intune nie geändert.
<br></br>
-   **Vollständige Integration:** Ermöglicht Skycure, Risiken und Details zu Sicherheitsvorfällen von Geräten an Intune zu melden, wodurch eine bidirektionale Kommunikation zwischen den beiden Cloud-Diensten entsteht.

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>Wie werden die Skycure-Apps mit Azure AD und Intune verwendet?

-   **iOS-App:** Ermöglicht Endbenutzern die Anmeldung bei Azure AD mithilfe einer iOS-App.

-   **Android-App:** Ermöglicht Endbenutzern die Anmeldung bei Azure AD mithilfe einer Android-App.

-   **Management-App:** Dies ist die Skycure Azure AD-App für mehrere Mandanten, die dienstübergreifende Kommunikation mit Intune ermöglicht.

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>So richten Sie die schreibgeschützte Integration zwischen Intune und Skycure ein

> [!IMPORTANT]
> Die Skycure-Administratoranmeldeinformationen sind eine E-Mail-Nachricht, die einem gültigen Benutzer in Azure Active Directory gehören muss, andernfalls schlägt die Anmeldung fehl. Skycure verwendet Azure Active Directory zum Authentifizieren des Administrators mithilfe von einmaligem Anmelden (SSO).

1.  Gehen Sie zur [Skycure-Verwaltungskonsole](https://aad.skycure.com).

2.  Geben Sie Ihre **Skycure-Administratoranmeldeinformationen** ein, und klicken Sie dann auf **Continue** (Weiter).

3.  Wechseln Sie zu **Einstellungen**, und wählen Sie unter **Intune-Integration** **Basic Setup** (Grundlegende Installation) aus.

4.  Klicken Sie auf dem Label **iOS-App** auf **Add to Active Directory** (Zu Active Directory hinzufügen).

    ![iOS-App auf der Skycure-Verwaltungskonsole](../media/mtp/skycure-setup-1.png)

5.  Die Anmeldeseite wird geöffnet, geben Sie Ihre Intune-Anmeldeinformationen ein, und klicken Sie dann auf **Accept** (Annehmen).

    ![iOS-App Intune-Anmeldeaufforderung](../media/mtp/skycure-setup-2.png)

6.  Sobald die App zu Azure AD hinzugefügt wurde, sehen Sie auf der Skycure-Verwaltungskonsole einen Hinweis darauf, dass die App erfolgreich zu Azure AD hinzugefügt wurde.

    ![iOS-App Abgeschlossen-Screenshot](../media/mtp/skycure-setup-3.png)

> [!NOTE]
> Wiederholen Sie den gleichen Vorgang für die **Skycure Android**- und **Verwaltungs**-Apps.

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Hinzufügen einer Azure AD-Sicherheitsgruppe in Skycure

Sie müssen eine Azure AD-Sicherheitsgruppe hinzufügen, die alle Geräte enthält, auf denen Skycure ausgeführt wird.

1.  Geben Sie alle Sicherheitsgruppen von Geräten ein, auf denen Skycure ausgeführt wird, wählen Sie diese aus, und klicken Sie auf **Apply changes** (Änderungen übernehmen).

    ![Konfigurieren der Sicherheitsgruppe Skycure-Verwaltungskonsole](../media/mtp/skycure-setup-4.png)

Skycure synchronisiert die Geräte und führt den Mobile Threat Defense-Dienst mit den Azure AD-Sicherheitsgruppen aus.

![Sicherheitsgruppenkonfiguration auf Skycure-Verwaltungskonsole abgeschlossen](../media/mtp/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Die vollständige Integration zwischen Intune und Skycure einrichten

1.  Gehen Sie zur [Skycure-Verwaltungskonsole](https://aad.skycure.com).

2.  Geben Sie Ihre **Skycure-Administratoranmeldeinformationen** ein, und klicken Sie dann auf **Continue** (Weiter).

3.  Wechseln Sie zu **Settings** (Einstellungen), und wählen Sie unter **Intune Integration** (Intune-Integration) **Full Integration** (Vollständige Integration) aus.

4.  Überprüfen Sie die folgenden Einstellungen:

    ein.  Report the health and risk of device to Intune (Integrität und Risiken des Geräts an Intune melden)

    b.  Also report security incidents to Intune (Auch Sicherheitsvorfälle an Intune melden)

5.  Klicken Sie auf **Apply changes** (Änderungen übernehmen).

    ![Vollständige Integration von Skycure abgeschlossen](../media/mtp/skycure-setup-6.png)

## <a name="next-steps"></a>Nächste Schritte

[Aktivieren von Skycure Mobile Threat Defense in Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)
