---
title: Einrichten der Pradeo-Integration mit Intune
titleSuffix: Intune on Azure
description: Integration des Pradeo-Connectors in Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b76549ad4be80d510638e3f79111d700a80f73ca
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838528"
---
# <a name="integrate-pradeo-with-intune"></a>Integrieren von Pradeo in Intune

Führen Sie die folgenden Schritte durch, um die Pradeo Mobile Threat Defense-Lösung in Intune zu integrieren.

## <a name="before-you-begin"></a>Vorbereitung

> [!NOTE]
> Die folgenden Schritte werden in der [Pradeo Security-Konsole](https://www.apps-security.com) durchgeführt.

Stellen Sie vor der Integration von Pradeo in Intune sicher, dass Sie über Folgendes verfügen:

-   Microsoft Intune-Abonnement

-   Azure Active Directory-Administratoranmeldeinformationen zum Erteilen folgender Berechtigungen:

    -   Anmelden und Lesen des Benutzerprofils

    -   Zugriff auf das Verzeichnis als angemeldeter Benutzer

    -   Lesen der Verzeichnisdaten

    -   Senden von Geräteinformationen an Intune

-   Administratoranmeldeinformationen für den Zugriff auf die Pradeo Security-Konsole

### <a name="pradeo-app-authorization"></a>Pradeo-App-Autorisierung

Der Prozess zur Autorisierung der Pradeo-App umfasst Folgendes:

-   Erteilen Sie Pradeo die Berechtigung, Informationen zum Integritätszustand des Geräts an Intune zu übertragen.

-   Pradeo wird mit der Azure AD Enrollment Group-Mitgliedschaft synchronisiert, um die Datenbank des Geräts aufzufüllen.

-   Erteilen Sie der Pradeo-Verwaltungskonsole die Berechtigung, Azure AD-SSO (Single Sign On) zu verwenden.

-   Erteilen Sie der Pradeo-App die Berechtigung, die Azure AD-SSO-Anmeldung zu verwenden.

## <a name="to-set-up-pradeo-integration"></a>So richten Sie die Integration von Pradeo ein

1.  Wechseln Sie zur [Pradeo Security-Konsole](https://www.apps-security.com), und melden Sie sich mit Ihren Anmeldeinformationen an.

2.  Klicken Sie im Menü auf **Administration - Enterprise Mobility Management** (Verwaltung: Enterprise Mobility-Verwaltung).

3.  Klicken Sie auf das **Intune-Logo**.

4.  Klicken Sie im Fenster **EMM (Enterprise Mobility Management) - Intune** unter **Step 1** (Schritt 1) auf die Schaltfläche **Pradeo Connector**. 

    ![Screenshot des Intune-EMM-Fensters von Pradeo](./media/pradeo_setup.png)

5. Geben Sie Ihre Intune-Anmeldeinformationen im Microsoft Intune-Verbindungsfenster ein.

5.  Die Pradeo-Website wird erneut geöffnet. Klicken Sie unter **Step 2** (Schritt 2) auf die Schaltfläche **Pradeo Device Health** (Pradeo-Geräteintegrität).

7. Klicken Sie im Fenster „Pradeo-Intune Connector“ auf **Accept** (Akzeptieren). 

8. Klicken Sie im Fenster „Pradeo device API connector“ (Pradeo-Geräte-API-Connector) auf **Accept** (Akzeptieren).

9. Die Pradeo-Website wird erneut geöffnet. Klicken Sie unter **Step 3** auf die Schaltfläche **Connect to Microsoft** (Verbindung mit Microsoft herstellen). 

10. Geben Sie Ihre Intune-Anmeldeinformationen im Microsoft Intune-Authentifizierungsfenster ein.

11. Wenn die Nachricht **Successful Integration** (Die Integration wurde erfolgreich abgeschlossen) angezeigt wird, ist die Integration abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

-   [Einrichten von Pradeo-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
