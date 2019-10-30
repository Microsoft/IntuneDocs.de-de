---
title: Einrichten der Symantec-Integration in Microsoft Intune
titleSuffix: Microsoft Intune
description: 'Gewusst wie: Einrichten der Symantec Endpoint Protection Mobile-Lösung in Microsoft Intune, um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern.'
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6c28b222307ee20e3198033ef6aa4af3d756e7e
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681315"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>Einrichten der Symantec Endpoint Protection Mobile-Integration in Intune

Führen Sie die folgenden Schritte aus, um die Symantec Endpoint Protection Mobile-Lösung (SEP Mobile) in Intune zu integrieren. Sie müssen SEP Mobile-Apps in Azure AD für SSO-Funktionen hinzufügen.

> [!NOTE]
> Dieser Mobile Threat Defense-Anbieter wird für nicht registrierte Geräte nicht unterstützt.

## <a name="before-you-begin"></a>Vorbereitung

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Azure AD-Konto, mit dem Intune und SEP Mobile integriert werden

- Stellen Sie sicher, dass das Azure AD-Konto ordnungsgemäß in der [Symantec Endpoint Protection Mobile Management-Konsole](https://aad.skycure.com) konfiguriert ist, bevor Sie den grundlegenden SEP Mobile-Installationsvorgang starten.
- Das Azure AD-Konto muss ein globales Administratorkonto sein, um die Integration auszuführen.
### <a name="network-setup"></a>Netzwerkeinrichtung

Um sicherzustellen, dass das Netzwerk ordnungsgemäß für die Integration in das SEP Mobile-Setup konfiguriert ist, können Sie den Symantec-Artikel [Setting up your network configuration](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016) (Einrichten Ihrer Netzwerkkonfiguration) zu Rate ziehen.

### <a name="full-integration-vs-read-only"></a>Die vollständige Integration unterstützt im Vergleich zu Read-only

SEP Mobile unterstützt zwei Arten der Integration in Intune:

- **Schreibgeschützte Integration (Grundlegende Installation):** Inventarisiert nur Geräte aus Azure Active Directory und füllt sie in der Symantec Endpoint Protection Mobile Management-Konsole auf.
<br>
  - Wenn in der Symantec Endpoint Protection Mobile Management-Konsole **Report the health and risk of devices to Intune** (Integrität und Risiken der Geräte an Intune melden) und **Also report security incidents to Intune** (Auch Sicherheitsvorfälle an Intune melden) nicht aktiviert sind, ist die Integration schreibgeschützt, und ein Gerätestatus („kompatibel“ oder „nicht kompatibel“) wird in Intune nie geändert.
<br></br>
- **Vollständige Integration:** Ermöglicht SEP Mobile, Risiken und Details zu Sicherheitsvorfällen von Geräten an Intune zu melden, wodurch eine bidirektionale Kommunikation zwischen den beiden Clouddiensten entsteht.

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>Wie werden die SEP Mobile-Apps mit Azure AD und Intune verwendet?

- **iOS-App:** Ermöglicht Endbenutzern die Anmeldung bei Azure AD mithilfe einer iOS-App.

- **Android-App:** Ermöglicht Endbenutzern die Anmeldung bei Azure AD mithilfe einer Android-App.

- **Management-App:** Dies ist die SEP Mobile Azure AD-App für mehrere Mandanten, die dienstübergreifende Kommunikation mit Intune ermöglicht.

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>So richten Sie die schreibgeschützte Integration zwischen Intune und SEP Mobile ein

> [!IMPORTANT]
> Die SEP Mobile-Administratoranmeldeinformationen müssen aus einem E-Mail-Konto bestehen, das einem gültigen Benutzer in Azure Active Directory gehören muss, andernfalls schlägt die Anmeldung fehl. SEP Mobile verwendet Azure Active Directory zum Authentifizieren des Administrators mithilfe von einmaligem Anmelden (SSO).

1. Wechseln Sie zur [Symantec Endpoint Protection Mobile Management Console](https://aad.skycure.com).

2. Geben Sie Ihre **SEP Mobile-Administratoranmeldeinformationen** ein, und wählen Sie dann **Continue** (Fortfahren).

3. Wechseln Sie zu **Settings** (Einstellungen), und wählen Sie unter **Intune Integration** die Option **Basic Setup** (Grundlegende Installation) aus.

4. Wählen Sie neben **iOS App** die Option **Add to Active Directory** (Zu Active Directory hinzufügen) aus.

    ![Darstellung der Symantec Endpoint Protection Mobile Management-Konsole](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

5. Wenn die Anmeldeseite geöffnet wird, geben Sie Ihre Intune-Anmeldeinformationen ein, und klicken Sie dann auf **Accept** (Annehmen).

    ![Abbildung der Intune-Anmeldeaufforderung in der iOS-App](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

6. Nachdem die App in Azure AD hinzugefügt wurde, sehen Sie einen Hinweis darauf, dass die App erfolgreich hinzugefügt wurde.

    ![Abbildung des Bildschirms nach Abschluss des Vorgangs in der iOS-App](./media/skycure-mtd-connector-integration/symantec-portal-basic-added.png)

7. Wiederholen Sie diese Schritte für die **SEP Mobile Android**- und **Management**-App.

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>Hinzufügen einer Azure AD-Sicherheitsgruppe in SEP Mobile

Sie müssen eine Azure AD-Sicherheitsgruppe hinzufügen, die alle Geräte enthält, auf denen SEP Mobile ausgeführt wird.

- Geben Sie alle Sicherheitsgruppen von Geräten ein, auf denen SEP Mobile ausgeführt wird, wählen Sie diese aus, und speichern Sie die Änderungen.

    ![Darstellung der Benutzergruppen für SEP Mobile-Apps](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

SEP Mobile synchronisiert die Geräte und führt den Mobile Threat Defense-Dienst mit den Azure AD-Sicherheitsgruppen aus.

![Darstellung der Sicherheitsgruppenkonfiguration in der SEP Mobile Management-Konsole](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>So richten Sie die vollständige Integration zwischen Intune und SEP Mobile ein

### <a name="retrieve-the-directory-id-in-azure-ad"></a>Abrufen der Verzeichnis-ID in Azure AD

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Geben Sie „Active Directory“ in das Suchfeld ein, und wählen Sie dann **Azure Active Directory** aus.

3. Wählen Sie **Eigenschaften** aus.

4. Wählen Sie neben der **Verzeichnis-ID** das Kopiersymbol aus, und fügen Sie es an einem sicheren Speicherort ein. Sie benötigen diesen Bezeichner in einem späteren Schritt.

    ![Darstellung der Verzeichnis-ID im Azure-Portal](./media/skycure-mtd-connector-integration/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(Optional) Erstellen einer dedizierten Sicherheitsgruppe für Geräte, die die SEP Mobile-Apps ausführen müssen
1. Wählen Sie im [Azure-Portal](https://portal.azure.com) unter **Verwalten** **Benutzer und Gruppen** und dann **Alle Gruppen** aus.

2. Wählen Sie die Schaltfläche **Hinzufügen** aus. Geben Sie einen **Namen** für die Gruppe ein. Wählen Sie unter **Mitgliedschaftstyp** **Zugewiesen** aus.

3. Wählen Sie auf dem Blatt **Mitglieder** die Gruppenmitglieder und dann die Schaltfläche **Auswählen** aus.

4. Wählen Sie auf dem Blatt **Gruppe** die Option **Erstellen** aus.

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>Einrichten der Integration zwischen Symantec Endpoint Protection Mobile und Intune

1. Wechseln Sie zur [Symantec Endpoint Protection Mobile Management Console](https://aad.skycure.com).

2. Geben Sie Ihre **SEP Mobile-Administratoranmeldeinformationen** ein, und wählen Sie dann **Continue** (Fortfahren).

3. Wechseln Sie zum Abschnitt **Settings (Einstellungen)**  > **Integrations (Integrationen)**  > **Intune** > **EMM Integration Selection (EMM-Integrationsauswahl)** .

4. Fügen Sie im Feld **Directory ID** (Verzeichnis-ID) die Verzeichnis-ID ein, die Sie im vorherigen Abschnitt aus Azure Active Directory kopiert haben, und speichern Sie die Einstellungen.

    ![Darstellung der Verzeichnis-ID im SEP Mobile-Portal](./media/skycure-mtd-connector-integration/symantec-portal-directory-ID.png)

5. Wechseln Sie zum Abschnitt **Settings (Einstellungen)**  > **Integrations (Integrationen)**  > **Intune** > **Basic Setup (Grundlegende Installation)** .

6. Wählen Sie neben **iOS App** die Schaltfläche **Add to Active Directory** (Zu Active Directory hinzufügen) aus.

    ![Darstellung des Hinzufügens der iOS-App zu Active Directory](./media/skycure-mtd-connector-integration/symantec-portal-basic-add.png)

7. Melden Sie sich mit den Azure Active Directory-Anmeldeinformationen für das Office 365-Konto an, das das Verzeichnis verwaltet.

8. Wählen Sie die Schaltfläche **Accept** (Annehmen), um Azure Active Directory die SEP Mobile iOS-App hinzuzufügen.

    ![Darstellung der Schaltfläche „Accept“ (Annehmen)](./media/skycure-mtd-connector-integration/symantec-portal-basic-accept.png)

9. Wiederholen Sie den gleichen Vorgang für die **Android**- und **Management**-App.

10. Wählen Sie alle Benutzergruppen aus, die die SEP Mobile-Apps ausführen müssen, z.B. die Sicherheitsgruppe, die Sie zuvor erstellt haben.

    ![Darstellung der Benutzergruppen für SEP Mobile-Apps](./media/skycure-mtd-connector-integration/symantec-portal-basic-groups.png)

11. SEP Mobile synchronisiert die Geräte in den ausgewählten Gruppen und beginnt, Informationen an Intune zu senden. Sie können diese Daten im Abschnitt „Full Integration“ (Vollständige Integration) anzeigen. Wechseln Sie zum Abschnitt **Settings (Einstellungen)**  > **Integrations (Integrationen)**  > **Intune** > **Full Integration (Vollständige Integration)** .

     ![Abbildung, die anzeigt, dass die vollständige Integration von SEP Mobile abgeschlossen wurde.](./media/skycure-mtd-connector-integration/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>Nächste Schritte

[Hinzufügen und Zuweisen von Mobile Threat Defense-Apps (MTD) mit Intune](mtd-apps-ios-app-configuration-policy-add-assign.md)
