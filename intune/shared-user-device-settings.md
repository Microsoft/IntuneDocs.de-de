---
title: 'Einstellungen für gemeinsam genutzte oder von mehreren Benutzern verwendete Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Fügen Sie Windows 10- und Windows Holographic for Business-Geräte hinzu, die gemeinsam genutzt oder von mehreren Benutzern in Microsoft Intune verwendet werden. Hier finden Sie eine Liste mit allen Einstellungen und ihren Auswirkungen auf die Geräte (einschließlich Microsoft HoloLens). Verwalten Sie Gastkonten und sonstige Konten, löschen Sie inaktive Konten, aktivieren oder deaktivieren Sie das Speichern auf lokalen Speichermedien, legen Sie Energieoptionen und den Zeitpunkt für die Installation fest und verwenden Sie Geräte, die im Bildungsbereich eingesetzt werden, in einem Gerätekonfigurationsprofil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: cf35d2ab2a1e08591669ef21ed3c24a00076a1ae
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204946"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>Steuern von Zugriff, Konten und Energiefunktionen auf gemeinsam genutzten PCs oder von mehreren Benutzern verwendeten Geräten mit Intune

Geräte mit mehreren Benutzern werden als „gemeinsam genutzte Geräte“ bezeichnet und sind in den Lösungen für die mobile Geräteverwaltung (Mobile Device Management, MDM) enthalten. Mit Microsoft Intune können Sie gemeinsam genutzte Geräte anpassen, auf denen folgende Plattformen ausgeführt werden:

- Windows 10 Professional und höher
- Windows 10 Enterprise und höher
- Windows Holographic for Business (z.B. HoloLens)

Ein gutes Beispiel sind Schulen. Sie verfügen über Geräte, die in der Regel von vielen Schülern genutzt werden. Mithilfe dieser Einstellung kann der Intune-Administrator der Schule die Funktion für die gemeinsame PC-Nutzung aktivieren, um nur einen Benutzer gleichzeitig zuzulassen. Die Schüler können nicht zwischen verschiedenen Anmeldekonten auf dem Gerät wechseln. Außerdem kann festgelegt werden, dass nach der Abmeldung eines Schülers alle benutzerspezifischen Einstellungen gelöscht werden.

Endbenutzer können sich bei gemeinsam genutzten Geräten mit einem Gastkonto anmelden. Nach der Benutzeranmeldung werden die Anmeldeinformationen zwischengespeichert. Bei der Verwendung des Geräts erhalten diese Endbenutzer dann nur Zugriff auf von Ihnen ausgewählte Features. Sie wählen beispielsweise aus, wann das Gerät in den Energiesparmodus wechselt, ob Benutzer Dateien lokal anzeigen und speichern, Energieverwaltungseinstellungen aktivieren oder deaktivieren und andere Aktionen ausführen können. Darüber hinaus können Sie festlegen, ob das Gastkonto gelöscht wird, sobald sich der Benutzer abmeldet, oder inaktive Konten ab der Überschreitung eines bestimmten Schwellenwerts gelöscht werden.

Dieser Artikel zeigt, wie Sie ein Konfigurationsprofil erstellen, und bietet Links zu den verfügbaren Einstellungen mit entsprechenden Beschreibungen.

Wenn das Profil in Intune erstellt wird, stellen Sie das Profil für die Gerätegruppen in Ihrer Organisation bereit oder weisen es diesen zu. Sie können dieses Profil ebenfalls zu Gerätegruppen mit gemischten Gerätetypen und Betriebssystemversionen zuweisen.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
   - **Profiltyp**: Wählen Sie **Freigegebenes, von mehreren Benutzern verwendetes Gerät**  aus.

4. Konfigurieren Sie die Einstellungen für [Windows 10 und höher](shared-user-device-settings-windows.md) oder [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).

5. Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

Das Profil ist nun erstellt und in der Liste enthalten, führt aber noch keine Aktionen durch. Achten Sie darauf, dass Sie Gerätegruppen in Ihrer Organisation das [Profil zuweisen](device-profile-assign.md).

## <a name="next-steps"></a>Nächste Schritte

- Sehen sie sich die Übersicht über alle Einstellungen für [Windows 10 und höher](shared-user-device-settings-windows.md) oder [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) an.
- [Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)