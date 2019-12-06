---
title: 'Schnellstart: Einrichten der automatischen Registrierung in Intune'
description: 'Schnellstart: Einrichten der automatischen Registrierung für Windows 10-Geräte in Intune'
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9649a84650a555e964cd9200ed2295fee5efb9a
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562311"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Schnellstart: Einrichten der automatischen Registrierung für Windows 10-Geräte

In dieser Schnellstartanleitung richten Sie Microsoft Intune so ein, dass Geräte automatisch registriert werden, wenn sich bestimmte Benutzer auf Windows 10-Geräten anmelden.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen

- Microsoft Intune-Abonnement: [Registrieren Sie sich für eine kostenlose Testversion](../fundamentals/free-trial-sign-up.md).
- Um dieser Schnellstartanleitung zu folgen, müssen Sie zunächst [einen Benutzer](../fundamentals/quickstart-create-user.md) und [eine Gruppe erstellen](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) als globaler Administrator oder Intune-Dienstadministrator an. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="set-up-windows-10-automatic-enrollment"></a>Einrichten der automatischen Registrierung von Windows 10

In diesem Beispiel wird die MDM-Registrierung verwendet, damit sowohl unternehmenseigenen Geräte als auch BYO-Geräte automatisch registriert werden können. Sie können sich für ein kostenloses Azure Active Directory Premium-Abonnement registrieren.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Azure Active Directory** > **Mobilität (MDM und MAM)** aus.
2. Klicken Sie auf **Holen Sie sich die kostenlose Premium-Testversion, um dieses Feature zu verwenden**. Wenn Sie diese Option verwenden, können Sie eine automatische Registrierung über die kostenlose Premium-Testversion von Azure Active Directory durchführen. 

    ![Auswahl der Premium-Testversion für Azure Active Directory](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    Klicken Sie auf die Option **Enterprise Mobility + Security E5**, um eine kostenlose Testversion zu erhalten. Anschließend müssen Sie auf **Aktivieren** klicken, um die kostenlose Testversion zu aktivieren.

    ![Auswahl der Option „Enterprise Mobility + Security E5“ für die kostenlose Testversion](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. Wählen Sie **Microsoft Intune** aus. 

    ![Auswahl von Microsoft Intune aus der Liste](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Klicken Sie im **MDM-Benutzerbereich** auf **Some** (Einige), um die automatische MDM-Registrierung zum Verwalten von Unternehmensdaten auf den Windows-Geräten Ihrer Mitarbeiter zu verwenden. Die automatische MDM-Registrierung wird für mit Azure AD verknüpfte Geräte und BYOD-Szenarios konfiguriert.

    ![Auswahl von „Some“ (Einige) aus der Liste „Konfigurieren“](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Klicken Sie auf **Gruppen auswählen** > **Contoso Testers** > **Auswählen**, um die Gruppe zuzuweisen.

    ![Auswahl der zu registrierenden Gruppe](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Klicken Sie unter **MAM Users scope** (MAM-Benutzerbereich) auf **Some** (Einige), um Daten auf den Geräten Ihrer Mitarbeiter zu verwalten.
7. Klicken Sie auf **Gruppen auswählen** > **Contoso Testers** > **Auswählen**, um die Gruppe zuzuweisen. 
8. Sie können die Standardwerte als verbleibende Konfigurationswerte verwenden.
9. Wählen Sie **Speichern** aus.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Lesen Sie den Artikel [Registrierung von Windows-Geräten](windows-enroll.md), um die automatische Registrierung von Intune neu zu konfigurieren.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung haben Sie gelernt, wie die automatische Registrierung für Windows 10-Geräte eingerichtet wird. Weitere Informationen finden Sie unter [What is device enrollment? (Was ist eine Geräteregistrierung?)](device-enrollment.md)

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Registrieren Ihres Windows 10-Geräts](../quickstart-enroll-windows-device.md)
