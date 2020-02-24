---
title: 'Registrieren von iOS-/iPadOS-Geräten: Benutzerregistrierung'
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr zum Einrichten der iOS-/iPadOS- und iPadOS-Benutzerregistrierung.
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
ms.openlocfilehash: d22d8d4772754fddbd366610402d64acc28ffc65
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415263"
---
# <a name="set-up-iosipados-and-ipados-user-enrollment-preview"></a>Einrichten der iOS-/iPadOS- und iPadOS-Benutzerregistrierung (Vorschau)

Sie können Intune so einrichten, dass iOS-/iPadOS- und iPadOS-Geräte im Rahmen des Apple-Benutzerregistrierungsprozesses registriert werden. Die Benutzerregistrierung bietet Administratoren im Vergleich zu anderen Registrierungsmethoden eine optimierte Teilmenge von Verwaltungsoptionen.

Weitere Informationen zu den mit der Benutzerregistrierung verfügbaren Optionen finden Sie unter [Von der Benutzerregistrierung unterstützte Aktionen, Kennwörter und andere Optionen](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> Die Unterstützung für die Apple-Benutzerregistrierung in Intune befindet sich derzeit in der Vorschauphase.

## <a name="prerequisites"></a>Voraussetzungen
- [Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM)](../fundamentals/mdm-authority-set.md)
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- [Verwaltete Apple IDs](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Erstellen eines Benutzerregistrierungsprofils in Intune

Ein Registrierungsprofil definiert die Einstellungen, die bei der Registrierung auf eine Gruppe von Geräten angewendet werden. 

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Registrierungstypen (Vorschau)**  > **Profil erstellen** > **iOS/iPadOS** aus. In diesem Profil geben Sie an, welche Registrierungserfahrung Ihre iOS-/iPadOS- und iPadOS-Endbenutzer auf Geräten haben, die nicht über eine Unternehmensmethode für Apple registriert werden. Wenn Sie Änderungen vornehmen möchten, können Sie dieses Profil nach der Erstellung bearbeiten.

    ![Erstellen eines Apple-Registrierungsprofils](./media/ios-user-enrollment/create-profile.png)

2. Geben Sie zu administrativen Zwecken auf der Seite **Grundlegende Einstellungen** einen **Namen** und eine **Beschreibung** für das Profil ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld **Name** zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über [dynamische Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Seite „Grundlagen“](./media/ios-user-enrollment/basics-page.png)


3. Wählen Sie **Weiter** aus.

4. Wählen Sie auf der Seite **Einstellungen** eine der folgenden Optionen für **Registrierungstyp** aus:

    ![Seite „Einstellungen“](./media/ios-user-enrollment/settings-page.png)

    - **Geräteregistrierung**: Alle Benutzer in diesem Profil verwenden die Geräteregistrierung.
    - **Benutzerregistrierung**: Alle Benutzer in diesem Profil verwenden die Benutzerregistrierung.
    - **Basierend auf Benutzerauswahl festlegen**: Alle Benutzer in dieser Gruppe können wählen, welchen Registrierungstyp sie verwenden möchten. Wenn Benutzer ihre Geräte registrieren, haben sie die Möglichkeit, zwischen **Ich besitze dieses Gerät** und **(Unternehmen) besitzt dieses Gerät** zu wählen. Bei Wahl der zweiten Option wird das Gerät über die Geräteregistrierung registriert. Wenn der Benutzer **Ich besitze dieses Gerät** wählt, erhält er eine weitere Option, um das gesamte Gerät oder nur sichere arbeitsbezogene Apps und Daten abzusichern. Die Wahl des Endbenutzers, ob er das Gerät besitzt, bestimmt, welcher Registrierungstyp auf seinem Gerät implementiert wird. Diese Benutzerauswahl wird in Intune auch im Attribut „Gerätebesitz“ berücksichtigt. Weitere Informationen zur Benutzererfahrung finden Sie unter [Einrichten des iOS-/iPadOS-Gerätezugriffs auf Unternehmensressourcen](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
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


