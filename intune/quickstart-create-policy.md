---
title: 'Schnellstart: Hinzufügen einer Gerätekonformitätsrichtlinie für ein Windows 10-Gerät'
description: Verwenden Sie diese Schnellstartanleitung, um Richtlinien zum Schützen von Unternehmensdaten und Verwalten von Geräten zu erstellen, die Endbenutzer verwenden, um auf Unternehmensressourcen zuzugreifen. Weisen Sie die Richtlinien anschließend Gruppen zu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d9169ab353da30e0f7b292cea4f5b9c93e316aa
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "49391551"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>Schnellstart: Hinzufügen einer Gerätekonformitätsrichtlinie für ein Windows 10-Gerät
Eine Intune-Konformitätsrichtlinie für Windows-Geräte gibt die Regeln und Einstellungen an, die Windows-Geräte erfüllen müssen, um als konform angesehen zu werden. Sie können diese Richtlinien mit [bedingtem Zugriff](https://docs.microsoft.com/intune/conditional-access) verwenden, um den Zugriff auf Unternehmensressourcen zuzulassen oder zu blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen.

In dieser Schnellstartanleitung erstellen Sie eine Gerätekonformitätsrichtlinie für ein Windows 10-Gerät und weisen dann der Richtlinie eine Gerätegruppe zu.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen
- Um dieser Schnellstartanleitung zu folgen, müssen Sie zunächst [einen Benutzer](quickstart-create-user.md) und [eine Gruppe erstellen](quickstart-create-group.md).


## <a name="sign-in-to-intune"></a>Anmelden bei Intune
Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator.

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie
1. Klicken Sie auf **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen**.
2. Geben Sie **Windows 10-Konformität** unter **Name** und **Beispielkonformitätsrichtlinie für Windows 10** in der **Beschreibung** ein.
3. Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.
4. Wählen Sie unter **Einstellungen** die Option **Systemsicherheit** aus, und legen Sie dann **Kennwort zum Entsperren mobiler Geräte erforderlich** auf **Erforderlich** fest. Wenn Sie Ihre Richtlinie eingerichtet haben, klicken Sie auf **OK**.
   ![Konformitätsrichtlinie](/intune/media/quickstart-create-policy/compliance-policy.png)
5. Schließen Sie den Bereich **Windows 10-Konformitätsrichtlinie**. 
6. Wählen Sie im Bereich **Richtlinie erstellen** die Option **Erstellen**. Dieser Schritt erstellt die Richtlinie und führt Sie unter **Gerätekonformität** > **Richtlinien** auf.
7. Wählen Sie die neue Richtlinie aus, und klicken Sie auf **Zuweisungen**. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
8. Klicken Sie auf **Ausgewählte Gruppen**, um Ihre vorhandenen Azure AD-Sicherheitsgruppen anzuzeigen. Klicken Sie auf **Contoso Tester** und dann auf **Speichern**, um die Richtlinie für Benutzer in der Gruppe bereitzustellen. Wenn Sie diese Gruppe unter [Gruppe erstellen](quickstart-create-group.md) nicht erstellt habe, können Sie die Gruppe Ihrer Wahl verwenden. 

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen
Löschen Sie die Richtlinie, wenn Sie sie nicht länger benötigen. Wählen Sie dazu die **Windows 10-Konformitätsrichtlinie** aus, und klicken Sie auf **Löschen**. 

## <a name="next-steps"></a>Nächste Schritte
In dieser Schnellstartanleitung haben Sie eine einfache Gerätekonformitätsrichtlinie erstellt und zugewiesen. Fahren Sie mit dem Schnellstart fort, um eine automatische Registrierung festzulegen, um ein Windows 10-Gerät zu registrieren, das die Richtlinie erhält. 
 
> [!div class="nextstepaction"]
> [Festlegen der Länge des Gerätekennworts](quickstart-set-password-length-android.md)