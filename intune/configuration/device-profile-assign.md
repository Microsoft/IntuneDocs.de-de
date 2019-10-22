---
title: Zuweisen von Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie das Azure-Portal, um Benutzern und Geräten Geräteprofile und Richtlinien zuzuweisen. Informationen zum Ausschließen von Gruppen von einer Profilzuweisung in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db1f0944a6725d1f361ea20c972d8ffa8f5d9035
ms.sourcegitcommit: a50a1ca123ecc2c5ac129f112f73838748f56476
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72237209"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Wenn Sie ein Profil erstellen, enthält es alle Einstellungen, die Sie vorgenommen haben. Als Nächstes stellen Sie das Profil für einen Azure AD-Benutzer (Azure Active Directory) oder eine -Gerätegruppe bereit. Dies wird auch als Zuweisen bezeichnet. Wenn Sie ein Profil zuweisen, erhalten Benutzer und Geräte das Profil, und die von Ihnen angegebenen Einstellungen werden angewendet.

In diesem Artikel wird erklärt, wie Sie ein Profil zuweisen können, und Sie erhalten Informationen zur Verwendung von Bereichsmarkierungen für Ihre Profile.

> [!NOTE]  
> Wenn eine Richtlinie entfernt oder nicht mehr einem Gerät zugewiesen wird, behält die Einstellung möglicherweise den vorhandenen Wert bei. Die Einstellung wird nicht auf einen Standardwert zurückgesetzt. Wenn Sie die Einstellung auf einen anderen Wert ändern möchten, erstellen Sie eine neue Richtlinie, und weisen Sie sie zu.

## <a name="assign-a-device-profile"></a>Zuweisen eines Geräteprofils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile**. Dort sind alle Profile aufgelistet.
3. Wählen Sie das Profil, das Sie zuweisen möchten, und klicken Sie dann auf **Assignments** (Zuweisungen).
4. Wählen Sie aus, ob Sie Gruppen **einschließen** oder **ausschließen** möchten, und wählen Sie Ihre Gruppen anschließend aus. Wenn Sie Ihre Gruppen auswählen, wählen Sie eine Azure AD-Gruppe aus. Halten Sie die **STRG**-Taste gedrückt, um mehrere Gruppen auszuwählen, und wählen Sie Ihre Gruppen anschließend aus.

    ![Screenshot der Optionen zum Ein- oder Ausschließen von Gruppen aus einer Profilzuweisung](./media/device-profile-assign/group-include-exclude.png)

5. **Speichern** Sie die Änderungen.

### <a name="evaluate-how-many-users-are-targeted"></a>Auswerten der Anzahl der betroffenen Benutzer

Wenn Sie das Profil zuweisen, können Sie auch **auswerten**, wie viele Benutzer betroffen sind. Durch diese Funktion wird eine Benutzeranzahl (jedoch keine Geräteanzahl) berechnet.

1. Klicken Sie in Intune auf **Device configuration** > **Profiles** (Gerätekonfiguration > Profile).
2. Wählen Sie ein Profil aus, und klicken Sie dann auf **Assignments** > **Evaluate** (Zuweisungen > Auswerten). Eine Meldung mit der Anzahl der von diesem Profil betroffenen Benutzer wird angezeigt.

Wenn die Schaltfläche **Evaluate** (Auswerten) ausgegraut ist, stellen Sie sicher, dass das Profil mindestens einer Gruppe zugewiesen wurde.

## <a name="use-scope-tags-or-applicability-rules"></a>Verwenden von Bereichstags oder Anwendbarkeitsregeln

Wenn Sie ein Profil erstellen oder aktualisieren, können Sie diesem auch Bereichstags und Anwendbarkeitsregeln hinzufügen.

**Bereichsmarkierungen** eignen sich zum Zuweisen und Filtern von Richtlinien für bestimmte Gruppen, z. B. Personalabteilung und Alle Mitarbeiter in North Carolina (USA). Unter [Use RBAC and scope tags for distributed IT (Verwenden der RBAC und von Bereichsmarkierungen für eine verteilte IT)](../fundamentals/scope-tags.md) finden Sie weitere Informationen.

Auf Windows 10-Geräten können Sie **Anwendbarkeitsregeln** hinzufügen, wodurch das Profil nur für eine bestimmte Betriebssystemversion oder eine bestimmte Windows-Version gilt. Unter [Anwendbarkeitsregeln](device-profile-create.md#applicability-rules) finden Sie weitere Informationen.

## <a name="exclude-groups-from-a-profile-assignment"></a>Ausschließen von Gruppen aus einer Profilzuweisung

Mit Intune-Gerätekonfigurationsprofilen können Sie Gruppen aus der Richtlinienzuweisung ausschließen.

Intune betrachtet keine Beziehungen zwischen Benutzer- und Gerätegruppen. Das Einschließen von Benutzergruppen und das gleichzeitige Ausschließen von Gerätegruppen liefert möglicherweise nicht die von Ihnen gewünschten Ergebnisse. In Szenarios von Benutzergruppe zu Benutzergruppe und Gerätegruppe zu Gerätegruppe hat ein Ausschluss Vorrang vor einem Einschluss.

Angenommen Sie weisen der Benutzergruppe **Alle Unternehmensbenutzer** ein Geräteprofil zu, schließen aber gleichzeitig Mitglieder der Benutzergruppe **Mitarbeiter der Führungsebene** aus. Da beide Gruppen Benutzergruppen sind, sind alle Mitglieder der Gruppe **Mitarbeiter der Geschäftsleitung** von der Richtlinie ausgeschlossen, obwohl sie Mitglieder der Gruppe **Alle Unternehmensbenutzer** sind.

In Szenarios mit gemischten Gruppen, wie etwa von Benutzergruppe zu Gerätegruppe oder von Gerätegruppe zu Benutzergruppe, hat ein Einschluss Vorrang vor einem Ausschluss.

Angenommen Sie möchten allen Benutzern in Ihrer Organisation, mit Ausnahme von Kioskgeräten, ein Geräteprofil zuweisen. Nun schließen Sie die Gruppe **Alle Benutzer** ein und gleichzeitig die Gruppe **Alle Geräte** aus. In diesem Fall erhalten alle Benutzer und ihre Geräte die Richtlinie, selbst wenn das Gerät des Benutzers der Gruppe **Alle Geräte** angehört.

Beim Ausschließen werden nur die direkten Mitglieder einer Gruppe berücksichtigt. Es werden keine Geräte berücksichtigt, die einem Benutzer zugeordnet sind. Geräte ohne Benutzer erhalten die Richtlinie jedoch nicht. Dies liegt daran, dass Geräte ohne Benutzer keine Beziehung zur Gruppe **Alle Benutzer** besitzen.

Wenn Sie **Alle Geräte** einschließen und gleichzeitig **Alle Benutzer** ausschließen, erhalten alle Geräte die Richtlinie. Damit sollten eigentlich alle Geräte mit einem zugeordneten Benutzer von der Richtlinie ausgeschlossen werden. Die Geräte werden jedoch nicht ausgeschlossen, da die Funktion „Ausschließen“ nur direkte Gruppenmitglieder miteinander vergleicht.

## <a name="next-steps"></a>Nächste Schritte

Unter [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md) finden Sie weitere Informationen zum Überwachen Ihrer Profile und der Geräte, auf denen Ihre Profile ausgeführt werden.
