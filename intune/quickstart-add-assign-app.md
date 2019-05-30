---
title: 'Schnellstart: Hinzufügen und Zuweisen einer Client-App'
titleSuffix: Microsoft Intune
description: In diesem Schnellstart verwenden Sie Microsoft Intune zum Hinzufügen und Zuweisen einer Client-App.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/25/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17db2227303fe3937156ad6afa610dce48bd1992
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041350"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Schnellstart: Hinzufügen und Zuweisen einer Client-App

In diesem Schnellstart verwenden Sie Intune, um Mitarbeitern Ihres Unternehmens eine Client-App hinzuzufügen und zuzuweisen. Eine der Prioritäten eines Administrators ist es, sicherzustellen, dass die Endbenutzer Zugriff auf die Apps haben, die sie für ihre Arbeit benötigen. 

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen

- Sie müssen für diesen Schnellstart [einen Benutzer erstellen](quickstart-create-user.md), [eine Gruppe erstellen](quickstart-create-group.md) und [ein Gerät registrieren](quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als [globaler Administrator oder Intune-Dienstadministrator](users-add.md#types-of-administrators). Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="add-the-client-app-to-intune"></a>Hinzufügen der Client-App zu Intune

Eine App kann eingefügt werden, damit Intune Aspekte der App verwalten kann. 

Führen Sie die folgenden Schritte aus, um eine App zu Intune hinzuzufügen:

1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Client-Apps** > **Apps** > **Hinzufügen**. 
2. Wählen Sie **Windows 10** im Abschnitt **Office 365 Suite** des Dropdownfelds **App-Typ** aus.
3. Klicken Sie auf **App-Suite konfigurieren**, um die Office-Apps auszuwählen, die dem Intune-Benutzer zugewiesen werden sollen.
4. Klicken Sie auf **OK**, um die standardmäßig ausgewählten Apps zu akzeptieren.
5. Klicken Sie auf **Informationen zur App-Suite**.
6. Geben Sie **Microsoft Office 365-App-Suite** als **Name der Suite** ein.
7. Geben Sie **Microsoft Office 365-App-Suite** als **Beschreibung der Suite** ein.
8. Klicken Sie neben **Diese App als ausgewählte App im Unternehmensportal anzeigen** auf **Ja**.
9. Klicken Sie auf **OK**.

    ![Screenshot vom Hinzufügen der App-Informationen](media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

8. Klicken Sie auf **Einstellungen der App-Suite**.
9. Wählen Sie **Monatlich** im Dropdownfeld **Updatekanal** aus.
10. Klicken Sie auf **OK** > **Hinzufügen**.

## <a name="assign-the-app-to-a-group"></a>Zuweisen der App zu einer Gruppe

Nachdem Sie eine App zu Microsoft Intune hinzugefügt haben, können Sie die App zu Benutzer- oder Gerätegruppen zuweisen.

> [!NOTE]
> Dieser Schnellstart setzt voraus, dass Sie die vorherigen Schnellstarts in dieser Serie abgeschlossen haben. Informationen dazu finden Sie in diesem Schnellstart unter [Voraussetzungen](quickstart-add-assign-app.md#prerequisites).

Führen Sie die folgenden Schritte aus, um eine App zu einer Gruppe zuzuweisen:
1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Client-Apps** > **Apps**. 
2. Wählen Sie die App aus, die einer Gruppe zugewiesen werden soll.   
3. Klicken Sie auf **Zuweisungen** > **Gruppe hinzufügen**, damit das Blatt **Gruppe hinzufügen** angezeigt wird.
4. Wählen Sie im Dropdownfeld **Zuweisungstyp** die Option **Für registrierte Geräte verfügbar** aus. 
5. Klicken Sie auf **Included Groups** > **Select groups to include** > **Contoso Testers** (Eingeschlossene Gruppen > Einzuschließende Gruppen auswählen > Contoso Testers).
6. Klicken Sie auf **Auswählen** > **OK** > **OK** > **Speichern**, um die Gruppe zuzuweisen.

Sie haben die App nun der Gruppe **Contoso Testers** zugewiesen.

## <a name="install-the-app-on-the-enrolled-device"></a>Installieren der App auf dem registrierten Gerät

Sie müssen die Unternehmensportal-App installieren, um die von Intune zur Verfügung gestellte **To-Do-App von Contoso** zu installieren. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die App dem Benutzer des registrierten Geräts zur Verfügung steht.

1. Melden Sie sich bei Ihrem registrierten Windows 10-Desktopgerät an.

    > [!IMPORTANT]
    > Das Gerät muss [bei Intune registriert](quickstart-enroll-windows-device.md) sein. Darüber hinaus müssen Sie sich mit einem Konto an dem Gerät anmelden, das der Gruppe angehört, der Sie die App zugewiesen haben.

2. Öffnen Sie den **Microsoft Store** über das **Startmenü**. Suchen Sie anschließend nach der **Unternehmensportal-App**, und installieren Sie sie.
3. Starten Sie die **Unternehmensportal-App**.
4. Klicken Sie auf die App, die Sie mit Intune hinzugefügt haben. In diesem Schnellstart haben Sie die **Microsoft Office 365-App-Suite**-App hinzugefügt.

    > [!NOTE]
    > Wenn Sie dem Intune-Benutzer keine Apps erfolgreich zugewiesen haben, wird die folgende Meldung angezeigt: *Ihr IT-Administrator hat keine Apps für Sie bereitgestellt.*

5. Klicken Sie auf **Installieren**.

Wenn Sie die Unternehmensportal-App jedoch aufgrund der Anforderungen Ihres Unternehmens Ihren Mitarbeitern zuweisen müssen, können Sie die Windows 10-Unternehmensportal-App direkt über Intune manuell zuweisen. Weitere Informationen finden Sie unter [Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](store-apps-company-portal-app.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie Apps zu Intune hinzugefügt, die Apps zu einer Gruppe zugewiesen und die Apps auf dem registrierten Windows 10-Desktopgerät installiert. Weitere Informationen zum Verwalten von Apps in Intune finden Sie unter [Was ist die Microsoft Intune App-Verwaltung?](app-management.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen und Zuweisen einer App-Schutzrichtlinie](quickstart-create-assign-app-policy.md)
