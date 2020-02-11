---
title: Zurücksetzen von Gerätekennungen mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Mit der Aktion „Kennung entfernen“ können Sie die Kennung von Geräten entfernen oder zurücksetzen, die Sie mit Intune überwachen oder verwalten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2a5629e6a318836e23c6a2f7fceb59363a0ed72
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812495"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Zurücksetzen oder Entfernen einer Gerätekennung in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Dokument wird die Kennungsrückstellung auf Dienstebene sowie die Kennungsrückstellung des Arbeitsprofils auf Android Enterprise-Geräten (ehemals Android for Work bzw. AfW) erläutert. Diese Unterscheidung ist von Bedeutung, da die Anforderungen der einzelnen variieren können. Mit der Kennungsrückstellung auf Geräteebene wird die Kennung für das gesamte Gerät zurückgesetzt. Die Kennungsrückstellung eines Arbeitsprofils setzt die Kennung nur für das Arbeitsprofil des Benutzers auf Android Enterprise-Geräten zurück.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Unterstützte Plattformen für die Kennungsrückstellung auf Geräteebene

| Plattform | Unterstützt? |
| ---- | ---- |
| Geräte unter Android Version 6.x oder früher | Ja |
| Als Gerätebesitzer registrierte Android-Unternehmensgeräte | Ja |
| iOS-Geräte | Ja |
| Über die Benutzerregistrierung registrierte iOS-Geräte | Nein |
| Über ein Arbeitsprofil registrierte Android-Geräte | Nein |
| Geräte unter Android 7.0 und höher | Nein |
| macOS | Nein |
| Windows | Nein |

Für Android-Geräte bedeutet dies, dass die Kennungsrückstellung auf Geräteebene nur auf Geräten mit Version 6.x oder früher oder auf Android Enterprise-Geräten im Kioskmodus unterstützt wird. Der Grund dafür ist, dass Google die Unterstützung für das Zurücksetzen der Kennung bzw. des Kennworts von Android 7-Geräten über eine vom Geräteadministrator zugelassene App entfernt hat. Dies gilt nun für alle MDM-Anbieter.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Unterstützte Plattformen für die Kennungsrückstellung für Android Enterprise-Arbeitsprofile

| Plattform | Unterstützt? |
| ---- | ---- |
| Android Enterprise-Geräte, die mit einem Arbeitsprofil registriert sind und auf denen Version 8.0 und höher ausgeführt wird | Ja |
| Android Enterprise-Geräte, die mit einem Arbeitsprofil registriert sind und auf denen Version 7.x und früher ausgeführt wird | Nein |
| Android-Geräte mit Version 7.x. und früher | Nein |

Verwenden Sie die Aktion „Kennung zurücksetzen“, um eine neue Kennung für das Arbeitsprofil zu erstellen. Durch diese Aktion wird eine Kennungsrückstellung ausgelöst, und es wird ausschließlich für das Arbeitsprofil eine neue temporäre Kennung erstellt. 

## <a name="reset-a-passcode"></a>Zurücksetzen einer Kennung


1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) mit einer der folgenden Rollen an: Azure Active Directory Global Admin, Azure Active Directory Intune Service Admin, Helpdesk Operator oder Role Administrator (Globaler Administrator in Azure Active Directory, Intune-Dienstadministrator in Azure Active Directory, Support oder Administrator für Rollen).
2. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
3. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein Gerät aus, und klicken Sie auf **...Weitere**. Wählen Sie dann die Remotegeräteaktion **Kennung entfernen** aus.

## <a name="reset-android-work-profile-passcodes"></a>Zurücksetzen von Kennungen für Android-Arbeitsprofile

Unterstützte Android Enterprise-Geräte, die mit einem Arbeitsprofil registriert sind, erhalten ein neues Kennwort zum Entsperren des verwalteten Profils oder eine Abfrage eines verwalteten Profils für den Endbenutzer.

Für Android Enterprise-Geräte mit Version 8.x oder höher, die mit einem Arbeitsprofil registriert sind, werden Benutzer benachrichtigt, dass sie Ihre zurückgesetzte Kennung sofort nach dem Abschluss der Registrierung aktivieren müssen. Die Benachrichtigung wird angezeigt, wenn das Kennwort für ein Arbeitsprofil erforderlich ist und festgelegt wurde. Sobald die Kennung eingegeben wurde, wird die Benachrichtigung verworfen.


## <a name="remove-ios-passcodes"></a>Entfernen von iOS-Kennungen

Kennungen werden von iOS-Geräten entfernt und nicht zurückgesetzt. Wenn eine Konformitätsrichtlinie für Kennungen festgelegt wurde, fordert das Gerät den Benutzer dazu auf, in den Einstellungen eine neue Kennung festzulegen.

## <a name="next-steps"></a>Nächste Schritte

Um den Status der gerade ausgeführten Aktion anzuzeigen, wählen Sie im Bereich **Geräte** die Option **Geräteaktionen** aus.
