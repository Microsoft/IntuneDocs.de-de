---
title: 'Verwendung von Vorlagen für Windows 10-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Verwenden Sie administrative Vorlagen in Microsoft Intune, um eine Vielzahl von Einstellungen für Windows 10-Geräte zu erstellen. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil, um Office-Programme und Microsoft Edge zu konfigurieren, Funktionen in Internet Explorer zu sichern, den Zugriff auf OneDrive zu kontrollieren, Remotedesktopfunktionen zu verwenden, AutoPlay zu aktivieren, Energieverwaltungseinstellungen festzulegen, HTTP-Druck und unterschiedliche Anmeldeoptionen zu verwenden und die Größe des Ereignisprotokolls festzulegen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50fc2d274531dce3d2466ba40a4738035b9b6811
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73756773"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Microsoft Intune

Wenn Sie Geräte in Ihrer Organisation verwalten, sollten Sie auch Einstellungen erstellen, die dann auf unterschiedliche Gerätegruppen angewendet werden. Nehmen Sie beispielsweise an, dass Sie über mehrere Gerätegruppen verfügen. Sie sollten Gruppe A mehrere bestimmte Einstellungen zuweisen. Gruppe B soll andere Einstellungen erhalten. Ihre Einstellungen sollen in einer einfachen, konfigurierbaren Ansicht angezeigt werden.

Sie können diese Aufgabe mithilfe der **administrativen Vorlagen** in Microsoft Intune erledigen. Die administrativen Vorlagen enthalten Hunderte Einstellungen, die Funktionen in Microsoft Edge Version 77 und höher, Internet Explorer, Microsoft Office-Programmen, Remotedesktop und OneDrive sowie die Verwendung von Kennwörtern und PINs u.v.m. kontrollieren können. Diese Einstellungen ermöglichen Gruppenadministratoren das Verwalten von Gruppenrichtlinien mithilfe der Cloud.

Die Windows-Einstellungen ähneln den Einstellungen für Gruppenrichtlinienobjekte in Active Directory (AD). Diese Einstellungen sind in Windows integriert und sind [durch ADMX unterstützte Einstellungen](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies), die XML verwenden. Die Office- und Microsoft Edge-Einstellungen sind in ADMX erfasst und verwenden die ADMX-Einstellungen in [administrativen Office-Vorlagendateien](https://www.microsoft.com/download/details.aspx?id=49030) und [administrativen Microsoft Edge-Vorlagendateien](https://www.microsoftedgeinsider.com/enterprise). Die Intune-Vorlagen sind jedoch vollständig cloudbasiert. Sie bieten eine einfache und unkomplizierte Möglichkeit, die Einstellungen zu konfigurieren und die Einstellungen zu suchen, die Sie nutzen möchten.

**Administrative Vorlagen** sind in Intune integriert, einschließlich der Verwendung des OMA-URI, und erfordern keine weiteren Anpassungen. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Vorlageneinstellungen als Anlaufstelle, um Ihre Windows 10-Geräte zu verwalten.

In diesem Artikel sind die Schritte zum Erstellen einer Vorlage für Windows 10-Geräte aufgeführt. Zudem wird erläutert, wie alle verfügbaren Einstellungen in Intune gefiltert werden können. Wenn Sie die Vorlage erstellen, wird ein Gerätekonfigurationsprofil erstellt. Sie können dieses Profil dann Windows 10-Geräten in Ihrer Organisation zuweisen oder für diese bereitstellen.

## <a name="before-you-begin"></a>Vorbereitung

- Einige dieser Einstellungen sind ab Windows 10, Version 1703 (RS2), verfügbar. Einige Einstellungen sind nicht in allen Windows-Editionen enthalten. Um optimale Ergebnisse zu erzielen, wird empfohlen, Windows 10 Enterprise, Version 1903 (19h1) oder höher, zu verwenden.

- In den Windows-Einstellungen werden [Windows-Richtlinien-CSPs](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies) verwendet. Die CSPs funktionieren unter verschiedenen Windows-Editionen, z. B. Home, Professional, Enterprise. Wenn Sie herausfinden möchten, ob ein CSP unter einer bestimmten Edition funktioniert, klicken Sie auf [Windows-Richtlinien-CSPs](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies).

## <a name="create-a-template"></a>Erstellen einer Vorlage

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen Namen für das Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
    - **Profiltyp**: Wählen Sie **Administrative Vorlagen** aus.

4. Wählen Sie **Erstellen** aus. Klicken Sie im neuen Fenster auf **Einstellungen**. Jede Einstellung ist aufgeführt, und Sie können auf den Zurück- und Weiter-Pfeil klicken, um weitere Einstellungen anzuzeigen:

    ![Liste mit Beispieleinstellungen mit der Verwendung des Zurück- und Weiter-Pfeils](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Die Windows-Einstellungen in Intune korrelieren mit dem lokalen Gruppenrichtlinienpfad, der im Editor für lokale Gruppenrichtlinien (`gpedit`) angezeigt wird.

5. Klicken Sie in der Dropdownliste auf **Alle Produkte**. Sie können die Einstellungen in der Liste auch so filtern, dass nur **Windows**-Einstellungen, nur **Office**-Einstellungen oder nur Einstellungen von **Edge Version 77 oder höher** angezeigt werden:

    ![Filtern Sie die Liste, um in den administrativen Vorlagen in Intune alle Windows-Einstellungen oder alle Office-Einstellungen anzuzeigen.](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > Microsoft Edge-Einstellungen gelten für:
    >
    > - Microsoft Edge Version 77 und höher. Informationen zum Konfigurieren von Microsoft Edge Version 45 und früher finden Sie unter [Microsoft Edge Browser](device-restrictions-windows-10.md#microsoft-edge-browser).
    > - Windows 10 RS4 und höher mit installiertem [KB 4512509](https://support.microsoft.com/kb/4512509)
    > - Windows 10 RS5 und höher mit installiertem [KB 4512534](https://support.microsoft.com/kb/4512534)
    > - Windows 10 19H1 und höher mit installiertem [KB 4512941](https://support.microsoft.com/kb/4512941)

6. Wählen Sie eine beliebige Einstellung aus. Filtern Sie beispielsweise nach **Office**, und wählen Sie **Eingeschränktes Browsing aktivieren** aus. Es wird eine detaillierte Beschreibung der Einstellung angezeigt. Wählen Sie **Aktiviert** oder **Deaktiviert** aus, oder übernehmen Sie die Standardeinstellung **Nicht konfiguriert**. In der detaillierten Beschreibung wird erläutert, was geschieht, wenn Sie **Aktiviert**, **Deaktiviert** oder **Nicht konfiguriert** auswählen.
7. Klicken Sie auf **OK**, um die Änderungen zu speichern.

Gehen Sie die Liste der Einstellungen durch, und konfigurieren Sie die gewünschten Einstellungen für Ihre Umgebung. Hier sind einige Beispiele:

- Verwenden Sie die Einstellung **Einstellungen für VBA-Makrobenachrichtigungen**, um VBA-Makros in verschiedenen Microsoft Office-Programmen zu verarbeiten, einschließlich in Word und Excel.
- Verwenden Sie die Einstellung **Dateidownloads zulassen**, um Downloads von Internet Explorer zuzulassen oder zu verhindern.
- Verwenden Sie **Kennwort anfordern, wenn ein Computer reaktiviert wird (Netzbetrieb)** , um Benutzer aufzufordern, ein Kennwort einzugeben, sobald das Gerät wieder aktiviert und der Energiesparmodus beendet wird.
- Verwenden Sie die Einstellung **Download von unsignierten ActiveX-Steuerelementen**, um das Herunterladen unsignierter ActiveX-Steuerelemente aus Internet Explorer für Benutzer zu blockieren.
- Verwenden Sie die Einstellung **Systemwiederherstellung deaktivieren**, um Benutzern zu erlauben oder sie daran zu hindern, eine Systemwiederherstellung auf dem Gerät auszuführen.
- Verwenden Sie die Einstellung **Allow importing of favorites** (Importieren von Favoriten zulassen), um Benutzern das Importieren von Favoriten aus anderen Browsern in Microsoft Edge zu erlauben oder zu blockieren.
- Und vieles mehr!

## <a name="find-some-settings"></a>Suchen von Einstellungen

In diesem Vorlagen sind Hunderte von Einstellungen verfügbar. Nutzen Sie die integrierten Funktionen, um bestimmte Einstellungen einfacher zu finden:

- Wählen Sie in der Vorlage die Spalte **Einstellungen**, **Status**, **Einstellungstyp** oder **Pfad** aus, um die Liste entsprechend zu sortieren. Wenn Sie beispielsweise die Spalte **Path** auswählen, werden alle Einstellungen im `Microsoft Excel`-Pfad angezeigt:

  ![Klicken Sie auf „Pfad“, um alle Einstellungen anzuzeigen, die in den administrativen Vorlagen in Intune nach Gruppenrichtlinien- oder ADMX-Pfad gruppiert sind.](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Verwenden Sie das **Suchfeld** in Ihrer Vorlage, um nach bestimmten Einstellungen zu suchen. Sie können die Suche durch Festlegen des Titels oder Pfads durchführen. Suchen Sie beispielsweise nach `copy`. Es werden alle Einstellungen mit `copy` angezeigt:

  ![Suchen Sie nach „copy“, um in den administrativen Vorlagen in Intune alle Windows- und Office-Einstellungen anzuzeigen.](./media/administrative-templates-windows/search-copy-settings.png) 

  Suchen Sie in einem anderen Beispiel nach `microsoft word`. Es werden alle Einstellungen angezeigt, die Sie für das Microsoft Word-Programm festlegen können. Suchen Sie nach `explorer`, um alle Internet Explorer-Einstellungen anzuzeigen, die Sie Ihrer Vorlage hinzufügen können.

## <a name="next-steps"></a>Nächste Schritte

Die Vorlage ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend die Vorlage (auch Profil genannt) zu](device-profile-assign.md), und [überwachen Sie deren Status](device-profile-monitor.md).
