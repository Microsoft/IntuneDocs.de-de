---
title: 'Registrieren von iOS-Geräten: Benutzerregistrierung'
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr zum Einrichten der iOS- und iPadOS-Benutzerregistrierung.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d77a275e3a48845f56b22ecc21b75f664ea619c5
ms.sourcegitcommit: f26039d674eb4d61ab68264dd1a10b2e5e1d842c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74691744"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>Einrichten der iOS- und iPadOS-Benutzerregistrierung (Vorschau)

Sie können Intune so einrichten, dass iOS- und iPadOS-Geräte im Rahmen des Apple-Benutzerregistrierungsprozesses registriert werden. Die Benutzerregistrierung bietet Administratoren im Vergleich zu anderen Registrierungsmethoden eine optimierte Teilmenge von Verwaltungsoptionen.

Weitere Informationen zu den mit der Benutzerregistrierung verfügbaren Optionen finden Sie unter [Von der Benutzerregistrierung unterstützte Aktionen, Kennwörter und andere Optionen](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> Die Unterstützung für die Apple-Benutzerregistrierung in Intune befindet sich derzeit in der Vorschauphase.

## <a name="prerequisites"></a>Voraussetzungen
- [Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM)](../fundamentals/mdm-authority-set.md)
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- [Verwaltete Apple IDs](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Erstellen eines Benutzerregistrierungsprofils in Intune

Ein Registrierungsprofil definiert die Einstellungen, die bei der Registrierung auf eine Gruppe von Geräten angewendet werden. 

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Registrierungstypen (Vorschau)**  > **Profil erstellen** > **iOS/iPadOS** aus. In diesem Profil geben Sie an, welche Registrierungserfahrung Ihre iOS- und iPadOS-Endbenutzer auf Geräten haben, die nicht über eine Unternehmensmethode für Apple registriert werden. Wenn Sie Änderungen vornehmen möchten, können Sie dieses Profil nach der Erstellung bearbeiten.

    ![Erstellen eines Apple-Registrierungsprofils](./media/ios-user-enrollment/create-profile.png)

2. Geben Sie zu administrativen Zwecken auf der Seite **Grundlegende Einstellungen** einen **Namen** und eine **Beschreibung** für das Profil ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld **Name** zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über [dynamische Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Seite „Grundlagen“](./media/ios-user-enrollment/basics-page.png)


3. Wählen Sie **Weiter** aus.

4. Auf der Seite **Einstellungen** können Sie Benutzern bei der Registrierung die Wahl lassen. Sie können auch eine Standardeinstellung festlegen.

    ![Seite „Einstellungen“](./media/ios-user-enrollment/settings-page.png)

    - Wenn Sie möchten, dass alle Benutzer in diesem Profil die Benutzerregistrierung verwenden, gehen Sie wie folgt vor:
        1. Legen Sie **Benutzer muss Gerätetyp auswählen** auf **Nicht konfiguriert** fest.
        2. Wählen Sie für **Standardregistrierungstyp**, die Option **Benutzerregistrierung** aus.
    - Wenn Sie möchten, dass alle Benutzer in diesem Profil die Geräteregistrierung verwenden, gehen Sie wie folgt vor:
        1. Legen Sie **Benutzer muss Gerätetyp auswählen** auf **Nicht konfiguriert** fest.
        2. Wählen Sie für **Standardregistrierungstyp**, die Option **Geräteregistrierung** aus.
    - Wenn Sie allen Benutzern in dieser Gruppe die Wahl des Registrierungstyps überlassen möchten, wählen Sie **Erforderlich** für **Benutzer muss Gerätetyp auswählen** aus. Wenn Benutzer ihre Geräte registrieren, haben sie die Möglichkeit, zwischen **Ich besitze dieses Gerät** und **(Unternehmen) besitzt dieses Gerät** zu wählen. Bei Wahl der ersten Option wird das Gerät über die Benutzerregistrierung registriert. Bei Wahl der zweiten Option wird das Gerät über die Geräteregistrierung registriert. Wenn der Benutzer **Ich besitze dieses Gerät** wählt, erhält er eine weitere Option, um das gesamte Gerät oder nur sichere arbeitsbezogene Apps und Daten abzusichern. Die Wahl des Endbenutzers, ob er das Gerät besitzt, bestimmt nur, welcher Registrierungstyp auf seinem Gerät implementiert wird. Diese Benutzerauswahl wird in Intune nicht im Attribut „Gerätebesitz“ berücksichtigt. Weitere Informationen zur Benutzererfahrung finden Sie unter [Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
    > [!NOTE]
    > Der folgende Hinweis ist ungenau und wird von der Benutzeroberfläche entfernt.
    > „Damit der bedingte Zugriff auf Geräten funktioniert, die für die Benutzerregistrierung vorgesehen sind, müssen Sie die App Azure Authenticator als erforderliche App per Push an diese Benutzergruppe übertragen, um einmaliges Anmelden und Workplace Join zu aktivieren.”
    > Als Administrator müssen Sie keine Maßnahmen ergreifen, um die Authenticator-App per Push an Ihre Benutzer zu verteilen. Ihre Benutzer werden im Unternehmensportal angewiesen, die Authenticator-App zu installieren, um die Benutzerregistrierung abzuschließen und sicherzustellen, dass diese Szenarien ordnungsgemäß funktionieren.

5. Wählen Sie **Weiter** aus.

6. Wählen Sie auf der Seite **Zuweisungen** die Benutzergruppen mit den Benutzern aus, denen Sie dieses Profil zuweisen möchten. Sie können das Profil allen Benutzern oder bestimmten Gruppen zuweisen. Alle Benutzer in den ausgewählten Gruppen verwenden den oben gewählten Registrierungstyp. Gerätegruppen werden für Szenarien zur Benutzerregistrierung nicht unterstützt, da die Funktion auf Benutzeridentitäten statt auf Geräten basiert. Sie können das Profil allen Benutzern oder bestimmten Gruppen zuweisen.

    ![Seite „Zuweisungen“](./media/ios-user-enrollment/assignments-page.png)

7. Wählen Sie **Weiter** aus.

8. Überprüfen Sie auf der Seite **Überprüfen und erstellen** Ihre Entscheidungen, und klicken Sie dann auf **Erstellen**, um das Profil den Benutzern zuzuweisen.

    ![Seite „Zuweisungen“](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Profilpriorität

Wenn Sie mehr als ein Registrierungstypprofil erstellt haben, können Sie die Prioritätsreihenfolge ändern, in der sie angewendet werden.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Registrierungstypen (Vorschau)** aus.
2. Ziehen Sie die Profile in die Liste, und legen Sie sie in der Reihenfolge ab, in der Sie sie anwenden möchten.

Bei Konflikten zwischen Profilen für einen beliebigen Benutzer wird das Profil mit höherer Priorität auf den Benutzer angewendet.


