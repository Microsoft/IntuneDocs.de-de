---
title: Zuweisen von Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie das Azure-Portal, um Benutzern und Geräten Geräteprofile und Richtlinien zuzuweisen. Informationen zum Ausschließen von Gruppen aus einer Profilzuweisung in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fa1a1b1085d196411a03a6228eefa808399397ea
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune

Nachdem Sie ein Profil erstellt haben, können Sie das Profil Azure Active Directory-Gruppen (Azure AD) zuweisen.

## <a name="assign-a-device-profile"></a>Zuweisen eines Geräteprofils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, und suchen Sie nach **Microsoft Intune**.
2. Wählen Sie in **Microsoft Intune** die Option **Gerätekonfiguration** und anschließend **Profile** aus.
3. Wählen Sie in der Liste der Profile das Profil aus, das Sie zuweisen möchten, und anschließend **Zuweisungen**.
4. Wählen Sie aus, ob Sie Gruppen **einschließen** oder **ausschließen** möchten, und wählen Sie anschließend Gruppen aus.  

    ![Screenshot der Optionen zum Ein- oder Ausschließen von Gruppen aus einer Profilzuweisung](./media/group-include-exclude.png)

5. Wenn Sie Ihre Gruppen auswählen, wählen Sie eine Azure AD-Gruppe aus. Halten Sie die Taste **STRG** gedrückt, um mehrere Gruppen auszuwählen.
6. Klicken Sie abschließend auf **Speichern**.

## <a name="exclude-groups-from-a-profile-assignment"></a>Ausschließen von Gruppen aus einer Profilzuweisung

Mit Intune-Gerätekonfigurationsprofilen können Sie Gruppen aus der Richtlinienzuweisung ausschließen. So könnten Sie der Gruppe **Alle Unternehmensbenutzer** beispielsweise ein Geräteprofil zuweisen, aber gleichzeitig alle Mitglieder der Gruppe **Mitarbeiter des oberen Managements** ausschließen.

Wenn Sie Gruppen aus einer Zuweisung ausschließen, schließen Sie nur Benutzer oder Gerätegruppen aus (keine Mischung aus Gruppen).Intune berücksichtigt keine Benutzer-zu-Gerät-Beziehung. Das Einschließen von Benutzergruppen und das gleichzeitige Ausschließen von Gerätegruppen liefert möglicherweise nicht die von Ihnen gewünschten Ergebnisse. Bei einer Kombination aus verschiedenen Gruppen oder bei anderen Konflikten hat die Funktion „Einschließen“ Vorrang vor der Funktion „Ausschließen“.

Beispiel: Sie möchten allen Geräten in Ihrem Unternehmen, mit Ausnahme von Kioskgeräten, ein Geräteprofil zuweisen. Nun schließen Sie die Gruppe **Alle Benutzer** ein und gleichzeitig die Gruppe **Alle Geräte** aus. In diesem Fall erhalten alle Benutzer und ihre Geräte die Richtlinie, selbst wenn das Gerät des Benutzers der Gruppe **Alle Geräte** angehört.

Die Funktion „Ausschließen“ wertet nur direkte Mitglieder der Gruppen aus. Sie schließt keine Geräte ein, die einem Benutzer zugeordnet sind. Geräte, die über keinen Benutzer verfügen, erhalten die Richtlinie jedoch nicht. Grund hierfür ist, dass diese Geräte keine Beziehung zur Gruppe **Alle Benutzer** haben.

Wenn Sie **Alle Geräte** einschließen und gleichzeitig **Alle Benutzer** ausschließen, erhalten alle Geräte die Richtlinie. Damit sollten eigentlich alle Geräte mit einem zugeordneten Benutzer von der Richtlinie ausgeschlossen werden. Die Geräte werden jedoch nicht ausgeschlossen, da die Funktion „Ausschließen“ nur direkte Gruppenmitglieder miteinander vergleicht.

>[!TIP]
>Die Funktion „Ausschließen“ ist für Konformitätsrichtlinien oder App-Zuweisungen nicht verfügbar. Zum Ausschließen von Mitgliedern aus einer Zuweisung können Sie die Zuweisungen **Verfügbar** und **Nicht zutreffend** verwenden. Beispiel: Sie weisen der Gruppe **Alle Unternehmensbenutzer** eine App mit der Absicht **Verfügbar** zu und der Gruppe **Mitarbeiter des oberen Managements** die App mit der Absicht **Nicht zutreffend**. Die App wurde nun allen Benutzern *außer* den Benutzern der Gruppe **Mitarbeiter des oberen Managements** zugewiesen. Weisen Sie die App hingegen der Gruppe **Alle Unternehmensbenutzer** mit der Absicht **Erforderlich** zu, werden die Benutzer der Gruppe **Mitarbeiter des oberen Managements** nicht ausgeschlossen.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zum Überwachen der Zuweisungen von Geräteprofilen finden Sie unter [Überwachen von Geräteprofilen](device-profile-monitor.md).
