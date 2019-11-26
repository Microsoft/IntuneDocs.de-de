---
title: 'Hinzufügen von Einstellungsdatei-Einstellungen für macOS-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie eine XML-oder plist-Datei hinzu, die wichtige Informationen über Ihre APP enthält. Verwenden Sie ein Einstellungsdatei-Geräte Konfigurations Profil, um wichtige Informationen in der Eigenschaften Listen Datei zu ändern und Sie Ihren macOS-Geräten zuzuweisen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acad2e8539da7210c349ffb254af62f370af5f6
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391497"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Hinzufügen einer Eigenschaften Listen Datei zu macOS-Geräten mithilfe von Microsoft InTune

Mithilfe Microsoft InTune können Sie eine Eigenschaften Listen Datei (. plist) für MacOS-Geräte oder apps auf MacOS-Geräten hinzufügen.

Diese Funktion gilt für:

- macOS-Geräte mit 10,7 und höher

Eigenschaften Listen Dateien enthalten in der Regel Informationen zu macOS-Anwendungen. Weitere Informationen finden Sie unter [Informationen zu Eigenschaften Listen Dateien](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (Apple-Website) und [benutzerdefinierte Nutz Last Einstellungen](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

In diesem Artikel werden die verschiedenen Einstellungen der Eigenschaften Listen Datei aufgeführt und beschrieben, die Sie macOS-Geräten hinzufügen können. Verwenden Sie diese Einstellungen als Teil ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte), um die APP Bundle-ID (`com.company.application`) hinzuzufügen und die plist-Datei hinzuzufügen.

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren macOS-Geräten zugewiesen oder bereitgestellt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie das Profil.](device-profile-create.md)

## <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- Diese Einstellungen werden nicht überprüft. Stellen Sie sicher, dass Sie Ihre Änderungen testen, bevor Sie das Profil ihren Geräten zuweisen.
- Wenn Sie nicht sicher sind, wie Sie einen app-Schlüssel eingeben, ändern Sie die Einstellung in der app. Überprüfen Sie dann die Einstellungsdatei der App mithilfe von [Xcode](https://developer.apple.com/xcode/) , um zu sehen, wie die Einstellung konfiguriert ist. Apple empfiehlt, vor dem Importieren der Datei nicht verwaltbare Einstellungen mithilfe von Xcode zu entfernen.
- Nur einige apps funktionieren mit Managed Preferences und können möglicherweise nicht alle Einstellungen verwalten.
- Stellen Sie sicher, dass Sie die Eigenschaften Listen Dateien hochladen, die auf Geräte Kanaleinstellungen abzielen, nicht auf die Benutzer Kanaleinstellungen Eigenschaften Listen Dateien sind auf das gesamte Gerät ausgerichtet.

## <a name="preference-file"></a>Einstellungsdatei

- **Name**der Einstellungs Domäne: Eigenschaften Listen Dateien werden normalerweise für Webbrowser (Microsoft Edge), [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)und benutzerdefinierte Apps verwendet. Wenn Sie eine Einstellungs Domäne erstellen, wird auch eine Bündel-ID erstellt. Geben Sie die Bündel-ID ein, z. b. `com.company.application`. Geben Sie beispielsweise `com.Contoso.applicationName`, `com.Microsoft.Edge` oder `com.microsoft.wdav` ein.
- **Eigenschaften Listen Datei**: Wählen Sie die Datei mit der Eigenschaften Liste aus, die Ihrer APP zugeordnet ist. Stellen Sie sicher, dass es sich um eine `.plist` oder `.xml` Datei handelt. Laden Sie z. b. eine `YourApp-Manifest.plist` oder `YourApp-Manifest.xml` Datei hoch.
- **Dateiinhalt**: die Schlüsselinformationen in der Eigenschaften Listen Datei werden angezeigt. Wenn Sie die Schlüsselinformationen ändern müssen, öffnen Sie die Listen Datei in einem anderen Editor, und laden Sie die Datei dann in InTune erneut hoch.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).
