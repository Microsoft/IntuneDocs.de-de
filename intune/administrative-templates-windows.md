---
title: 'Verwendung von Vorlagen für Windows 10-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Verwenden Sie administrative Vorlagen in Microsoft Intune, um eine Vielzahl von Einstellungen für Windows 10-Geräte zu erstellen. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil, um Office-Programme zu konfigurieren, Funktionen in Internet Explorer zu sichern, den Zugriff auf OneDrive zu kontrollieren, Remotedesktopfunktionen zu verwenden, AutoPlay zu aktivieren, Energieverwaltungseinstellungen festzulegen, HTTP-Druck und unterschiedliche Anmeldeoptionen zu verwenden und die Größe des Ereignisprotokolls festzulegen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0426b63cb4601a73451ec9509ddea8e39271c29
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204972"
---
# <a name="windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Microsoft Intune

Wenn Sie Geräte in Ihrer Organisation verwalten, sollten Sie auch Einstellungen erstellen, die dann auf unterschiedliche Gerätegruppen angewendet werden. Nehmen Sie beispielsweise an, dass Sie über mehrere Gerätegruppen verfügen. Sie sollten Gruppe A mehrere bestimmte Einstellungen zuweisen. Gruppe B soll andere Einstellungen erhalten. Ihre Einstellungen sollen in einer einfachen, konfigurierbaren Ansicht angezeigt werden.

Sie können diese Aufgabe mithilfe der **administrativen Vorlagen** in Microsoft Intune erledigen. Die administrativen Vorlagen enthalten Hunderte Einstellungen, die Funktionen in Internet Explorer, Microsoft Office-Programmen und Remotedesktop anpassen sowie den Zugriff auf OneDrive und die Verwendung eines Bildkennworts oder einer PIN für die Anmeldung kontrollieren können. Diese Vorlagen ähneln den Gruppenrichtlinieneinstellungen (GPO) in Active Directory (AD) und sind [durch ADMX unterstützte Einstellungen](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies), die XML verwenden. Die Vorlagen in Intune sind jedoch vollständig cloudbasiert. Sie bieten eine einfachere und unkompliziertere Möglichkeit, die Einstellungen zu konfigurieren und die Einstellungen zu suchen, die Sie nutzen möchten.

**Administrative Vorlagen** sind in Intune integriert, einschließlich der Verwendung des OMA-URI, und erfordern keine weiteren Anpassungen. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Vorlageneinstellungen als Anlaufstelle, um Ihre Windows 10-Geräte zu verwalten.

In diesem Artikel sind die Schritte zum Erstellen einer Vorlage für Windows 10-Geräte aufgeführt. Zudem wird erläutert, wie alle verfügbaren Einstellungen in Microsoft Intune gefiltert werden können. Wenn Sie die Vorlage erstellen, wird ein Gerätekonfigurationsprofil erstellt. Sie können dieses Profil dann Windows 10-Geräten in Ihrer Organisation zuweisen oder für diese bereitstellen.

> [!NOTE]
> Administrative Vorlagen werden für eigenständige Geräte unterstützt. Sie werden derzeit jedoch nicht für gemeinsam verwaltete Geräte mit System Center Configuration Manager (SCCM) unterstützt.

## <a name="create-a-template"></a>Erstellen einer Vorlage

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen Namen für das Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
    - **Profiltyp**: Wählen Sie **Administrative Vorlagen (Vorschau)** aus.

4. Wählen Sie **Erstellen** aus. Klicken Sie im neuen Fenster auf **Einstellungen**. Jede Einstellung ist aufgeführt, und Sie können auf den Zurück- und Weiter-Pfeil klicken, um weitere Einstellungen anzuzeigen:

    ![Liste mit Beispieleinstellungen mit der Verwendung des Zurück- und Weiter-Pfeils](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. Wählen Sie eine beliebige Einstellung aus. Wählen Sie z. B. **Dateidownloads zulassen** aus. Es wird eine detaillierte Beschreibung der Einstellung angezeigt. Klicken Sie auf **Aktivieren** oder **Deaktivieren**, oder übernehmen Sie die Einstellung **Nicht konfiguriert** (Standard). In der detaillierten Beschreibung wird ebenso erläutert, was geschieht, wenn Sie **Aktivieren**, **Deaktivieren** oder **Nicht konfiguriert** auswählen.
6. Klicken Sie auf **OK**, um die Änderungen zu speichern.

Gehen Sie die Liste der Einstellungen durch, und konfigurieren Sie die gewünschten Einstellungen für Ihre Umgebung. Hier sind einige Beispiele:

- Verwenden Sie die Einstellung **Einstellungen für VBA-Makrobenachrichtigungen**, um VBA-Makros in verschiedenen Microsoft Office-Programmen zu verarbeiten, einschließlich in Word und Excel.
- Verwenden Sie die Einstellung **Dateidownloads zulassen**, um Downloads von Internet Explorer zuzulassen oder zu verhindern.
- Verwenden Sie die Einstellung **Kennwort anfordern, wenn ein Computer reaktiviert wird (Netzbetrieb)**, um Benutzer aufzufordern, ein Kennwort einzugeben, wenn das Gerät erneut aktiviert und der Energiesparmodus beendet wird.
- Verwenden Sie die Einstellung **Download von unsignierten ActiveX-Steuerelementen**, um das Herunterladen unsignierter ActiveX-Steuerelemente aus Internet Explorer für Benutzer zu blockieren.
- Verwenden Sie die Einstellung **Systemwiederherstellung deaktivieren**, um Benutzern zu erlauben oder sie daran zu hindern, eine Systemwiederherstellung auf dem Gerät auszuführen.
- Und vieles mehr!

## <a name="find-some-settings"></a>Suchen von Einstellungen

In diesem Vorlagen sind Hunderte von Einstellungen verfügbar. Nutzen Sie die integrierten Funktionen, um bestimmte Einstellungen einfacher zu finden:

- Wählen Sie in Ihrer Vorlage die Spalten **Settings** (Einstellungen), **State** (Status) oder **Path** (Pfad) aus, nach denen die Liste sortiert werden soll. Wenn Sie beispielsweise die Spalte **Path** auswählen, werden alle Einstellungen im `Microsoft Excel`-Pfad angezeigt:

  ![Klick auf „Path“ (Pfad), um die Liste alphabetisch zu sortieren](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Verwenden Sie das **Suchfeld** in Ihrer Vorlage, um nach bestimmten Einstellungen zu suchen. Suchen Sie beispielsweise nach `copy`. Es werden alle Einstellungen mit `copy` angezeigt:

  ![Klick auf „Path“ (Pfad), um die Liste alphabetisch zu sortieren](./media/administrative-templates-windows/search-copy-settings.png)

  Suchen Sie in einem anderen Beispiel nach `microsoft word`. Es werden alle Einstellungen angezeigt, die Sie für das Microsoft Word-Programm festlegen können. Suchen Sie nach `explorer`, um alle Internet Explorer-Einstellungen anzuzeigen, die Sie Ihrer Vorlage hinzufügen können.

## <a name="next-steps"></a>Nächste Schritte

Die Vorlage ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend die Vorlage (auch Profil genannt) zu](device-profile-assign.md), und [überwachen Sie deren Status](device-profile-monitor.md).
