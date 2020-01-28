---
title: Erstellen von macOS-Kernelerweiterungsgeräteprofilen mit Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Hier erfahren Sie, wie Sie ein macOS-Geräteprofil hinzufügen oder erstellen und dann Kernelerweiterungen konfigurieren, um Überschreibungen und das Hinzufügen einer Bundle- und Team-ID in Microsoft Intune durch Benutzer zuzulassen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1075054f3812e8c40f38e705a440c46ba09fdd0e
ms.sourcegitcommit: 11cbd2a9d90dea20f6dc1f54f0a6acbeec3a71d6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146768"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Hinzufügen von macOS-Kernelerweiterungen in Intune

Auf macOS-Geräten können Sie Features auf Kernelebene hinzufügen. Diese Features greifen auf Teile des Betriebssystems zu, auf die reguläre Programme nicht zugreifen können. In Ihrer Organisation gibt es möglicherweise bestimmte Bedürfnisse oder Anforderungen, die von einer App oder einem Gerätefeature nicht erfüllt werden können. 

Fügen Sie Kernelerweiterungen (KEXT) in Microsoft Intune hinzu, und stellen Sie diese Erweiterungen dann für Ihre Geräte bereit, wenn Sie Kernelerweiterungen verwenden möchten, die immer Ladevorgänge auf Ihren Geräten ausführen dürfen.

Angenommen, Sie haben ein Virenerkennungsprogramm, das Ihr Gerät auf schädliche Inhalte überprüft. In diesem Fall können Sie die Kernelerweiterung dieses Virenerkennungsprogramms als zulässige Kernelerweiterung in Intune hinzufügen. Weisen Sie die Erweiterung anschließend Ihren macOS-Geräten zu.

Mithilfe dieses Features können Administratoren Benutzer dazu berechtigen, Kernelerweiterungen zu überschreiben sowie Team-IDs und bestimmte Kernelerweiterungen in Intune hinzuzufügen.

Diese Funktion gilt für:

- macOS 10.13.2 und höher

Wenn Sie dieses Feature verwenden möchten, muss Folgendes auf Ihre Geräte zutreffen:

- Ihre Geräte sind über das Programm zur Geräteregistrierung von Apple (DEP) bei Intune registriert. Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung oder Apple School Manager](../enrollment/device-enrollment-program-enroll-macos.md).

  ODER

- Ihre Geräte sind über sogenanntes „user approved enrollment“ (Registrierung mit Benutzereinwilligung; Apple-Begriff) bei Intune registriert. Weitere Informationen finden Sie auf der Apple-Website [Auf Änderungen an Kernel-Erweiterungen in macOS High Sierra vorbereiten](https://support.apple.com/en-us/HT208019).

Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Features in einem Profil hinzugefügt haben, können Sie das Profil auf macOS-Geräte in Ihrer Organisation übertragen oder für sie bereitstellen.

In diesem Artikel erfahren Sie, wie Sie ein Gerätekonfigurationsprofil mithilfe von Kernelerweiterungen in Intune erstellen.

> [!TIP]
> Weitere Informationen zu Kernelerweiterungen finden Sie auf der Apple-Website [Kernel Extension Overview (Übersicht über Kernelerweiterungen)](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html).

## <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- Nicht signierte Vorgängerversionen von Kernelerweiterungen können hinzugefügt werden.
- Es ist wichtig, dass Sie die richtige Team-ID und Bundle-ID der Kernelerweiterung eingeben. Intune überprüft die eingegebenen Werte nicht. Wenn Sie falsche Informationen eingeben, funktioniert die Erweiterung auf dem Gerät nicht. Eine Team-ID ist genau zehn alphanumerische Zeichen lang. 

> [!NOTE]
> Bei Apple stehen Informationen zum Signieren und zur Notarisierung sämtlicher Software zur Verfügung. Ab macOS 10.14.5 müssen Kernelerweiterungen, die über Intune bereitgestellt werden, nicht mehr der Notarisierungsrichtlinie von Apple entsprechen.
>
> Informationen zu dieser Notarisierungsrichtlinie sowie sämtliche Aktualisierungen oder Änderungen finden Sie auf den folgenden Apple-Websites:
>
> - [Notarizing your app before distribution (Notarisierung Ihrer App vor der Verteilung)](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) 
> - [Auf Änderungen an Kernel-Erweiterungen in macOS High Sierra vorbereiten](https://support.apple.com/en-us/HT208019)

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name:** Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **macOS** aus.
    - **Profiltyp:** Klicken Sie auf **Erweiterungen**.
    - **Einstellungen**: Geben Sie die Einstellungen ein, die Sie konfigurieren möchten. Eine Liste aller Einstellungen und ihrer Funktionen finden Sie unter:

        - [macOS](kernel-extensions-settings-macos.md)

4. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Liste angezeigt. Denken Sie daran, das [Profil zuzuweisen](../device-profile-assign.md) und [seinen Status zu überwachen](../device-profile-monitor.md).

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Profil erstellt wurde, kann es zugewiesen werden. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](../device-profile-monitor.md).
