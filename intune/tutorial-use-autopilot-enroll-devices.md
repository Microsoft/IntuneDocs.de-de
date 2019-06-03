---
title: 'Tutorial: Registrieren von Geräten in Intune mithilfe von Autopilot'
titleSuffix: Microsoft Intune
description: In diesem Tutorial richten Sie Windows Autopilot ein, um Geräte in Intune zu registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ee353e5e6c39c3b402c0b4f039bb02efcfa4532
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044521"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Tutorial: Registrieren von Windows-Geräten in Intune mithilfe von Autopilot
Windows Autopilot vereinfacht das Registrieren von Geräten. Mit Microsoft Intune und Autopilot können Sie Ihren Endbenutzern neue Geräte geben, ohne die benutzerdefinierten Betriebssystemimages erstellen, verwalten und auf diese anwenden zu müssen. 

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> * Hinzufügen von Geräten zu Intune
> * Erstellen einer Autopilot-Gerätegruppe
> * Erstellen eines Autopilot-Bereitstellungsprofils
> * Zuweisen des Autopilot-Bereitstellungsprofils zur Gerätegruppe
> * Verteilen von Windows-Geräten an Benutzer

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

Eine Übersicht über die Vorteile, Szenarios und Voraussetzungen von Autopilot finden Sie unter [Übersicht über Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Voraussetzungen
- [Schnellstart: Einrichten der automatischen Registrierung für Windows 10-Geräte](quickstart-setup-auto-enrollment.md)
- [Azure Active Directory Premium-Abonnement](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Hinzufügen von Geräten

Der erste Schritt beim Einrichten von Windows Autopilot besteht darin, die Windows-Geräte zu Intune hinzuzufügen. Sie müssen lediglich eine CSV-Datei erstellen und in Intune importieren.

1. Erstellen Sie in einem beliebigen Text-Editor eine CSV-Datei (Comma-Separated Values), die die Windows-Geräte identifiziert. Verwenden Sie das folgende Format:
    
    *Seriennummer*, *Windows-Produkt-ID*, *Hardwarehash*, *Optionales Gruppentag*
    
    Die ersten drei Elemente sind erforderlich, das Gruppentag (früher „Auftrags-ID“) hingegen ist optional.

2. Speichern Sie die CSV-Datei.

3. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Geräte** > **Importieren** aus.

    ![Screenshot von Windows Autopilot-Geräten](media/enrollment-autopilot/autopilot-import-device.png)

4. Navigieren Sie unter **Windows Autopilot-Geräte hinzufügen** zu der CSV-Datei, die Sie gespeichert haben.

    ![Screenshot zum Hinzufügen von Windows Autopilot-Geräten](media/enrollment-autopilot/autopilot-import-device2.png)

5. Wählen Sie **Importieren** aus, um mit dem Importieren von Informationen zu den Geräten zu beginnen. Der Import kann mehrere Minuten dauern.

4. Nachdem der Importvorgang abgeschlossen ist, wählen Sie **Geräteregistrierung** > **Windows-Registrierung** > **Windows Autopilot** >  **Geräte** > **Synchronisieren** aus. Eine Meldung zeigt an, dass die Synchronisierung ausgeführt wird. Der Prozess kann ein paar Minuten in Anspruch nehmen, je nachdem, wie viele Geräte Sie synchronisieren.

5. Aktualisieren Sie die Ansicht, um neue Geräte anzuzeigen.

## <a name="create-an-autopilot-device-group"></a>Erstellen einer Autopilot-Gerätegruppe

Als Nächstes erstellen Sie eine Gerätegruppe und platzieren darin die Autopilot-Geräte, die Sie gerade geladen haben.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Option **Gruppen** > **Neue Gruppe** aus.
2. Auf dem Blatt **Gruppe**:
    1. Wählen Sie für **Gruppentyp** die Option **Sicherheit**.
    2. Geben Sie für **Gruppenname** *Autopilot-Gruppe* ein. Geben Sie für **Gruppenbeschreibung** *Testgruppe für Autopilot-Geräte* ein.
    3. Wählen Sie für **Mitgliedschaftstyp** **Zugewiesen** aus.
3. Wählen Sie auf dem Blatt **Gruppe** **Mitglieder** aus, und fügen Sie die Autopilot-Geräte der Gruppe hinzu. Autopilot-Geräte, die noch nicht registriert sind, sind Geräte, deren Name der Seriennummer des Geräts entspricht.
4. Wählen Sie **Erstellen** aus.  

## <a name="create-an-autopilot-deployment-profile"></a>Erstellen eines Autopilot-Bereitstellungsprofils

Nach dem Erstellen einer Gerätegruppe müssen Sie ein Bereitstellungsprofil erstellen, um die Autopilot-Geräte konfigurieren zu können.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofil** > **Profil erstellen** aus.
2. Geben Sie auf der Seite **Grundlagen** als **Name** *Autopilot-Profil* ein. Geben Sie für **Beschreibung** *Testprofil für Autopilot-Geräte* ein.
3. Legen Sie **Alle als Ziel angegebenen Geräte in Autopilot konvertieren** auf **Ja** fest. Durch diese Einstellung wird sichergestellt, dass alle Geräte in der Liste beim Autopilot-Bereitstellungsdienst registriert werden. Die Verarbeitung der Registrierung kann 48 Stunden dauern.
4. Wählen Sie **Weiter** aus.
5. Wählen Sie auf der Seite **Out-of-Box-Experience (OOBE)** als **Bereitstellungsmodus** **Benutzergesteuert** aus. Geräte mit diesem Profil werden dem Benutzer zugeordnet, der das Gerät registriert. Für die Registrierung des Geräts sind Benutzeranmeldeinformationen erforderlich.
6. Wählen Sie im Feld **Verknüpfen mit Azure AD als** die Option **In Azure AD eingebunden**.
7. Konfigurieren Sie die folgenden Optionen, und übernehmen Sie für die anderen die Standardwerte:
    - **Microsoft-Software-Lizenzbedingungen**: **Ausblenden**
    - **Datenschutzeinstellungen**: **Anzeigen**
    - **Art des Benutzerkontos**: **Standard**
8. Wählen Sie **Weiter** aus.
9. Wählen Sie auf der Seite **Zuweisungen** für **Zuweisen an** die Option **Ausgewählte Gruppen** aus.
10. Wählen Sie **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen** und dann **Autopilot-Gruppe** aus.
11. Wählen Sie **Weiter** aus.
12. Wählen Sie auf der Seite **Überprüfen + Erstellen** den Befehl **Erstellen** aus, um das Profil zu erstellen.

## <a name="distribute-devices-to-users"></a>Verteilen von Geräten an Benutzer

Sie können nun die Windows-Geräte an Ihre Benutzer verteilen. Wenn sie sich zum ersten Mal anmelden, registriert und konfiguriert das Autopilot-System automatisch die Geräte. 

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Wenn Sie die Autopilot-Geräte nicht mehr verwenden möchten, können Sie sie löschen.

1. Wenn Geräte bei Intune registriert sind, müssen Sie sie zunächst [aus Azure Active Directory-Portal löschen](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Windows-Registrierung** > **Geräte** aus.

3. Wählen Sie unter **Windows Autopilot-Geräte** die Geräte aus, die Sie löschen möchten, und wählen Sie dann **Löschen**.

4. Bestätigen Sie den Löschvorgang mit **Ja**. Der Löschvorgang kann einige Minuten dauern.

## <a name="next-steps"></a>Nächste Schritte

Informieren Sie sich auch über die anderen Optionen, die für Windows Autopilot verfügbar sind.

> [!div class="nextstepaction"]
> [Ausführlicher Artikel zur Autopilot-Registrierung](enrollment-autopilot.md)


