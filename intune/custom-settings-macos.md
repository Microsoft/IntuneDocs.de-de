---
title: 'Hinzufügen von benutzerdefinierten Einstellungen für macOS-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Exportieren Sie macOS-Einstellungen aus Apple Configurator oder aus dem Apple-Profil-Manager, und importieren Sie diese Einstellungen in Microsoft Intune. Über diese Einstellungen können benutzerdefinierte Einstellungen und Features auf macOS-Geräten erstellt, verwendet und gesteuert werden. Dieses benutzerdefinierte Profil kann dann macOS-Geräten in Ihrer Organisation zugewiesen oder an diese verteilt werden, um eine Baseline oder einen Standard zu erstellen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0309c5aa73dc8c03cabd69878d55ac51aa6d4f3
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375136"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Verwenden benutzerdefinierter Einstellungen für macOS-Geräte in Microsoft Intune

Mit Microsoft Intune können Sie benutzerdefinierte Einstellungen für macOS-Geräte mit einem benutzerdefinierten Profil hinzufügen oder erstellen. Benutzerdefinierte Profile sind ein Feature in Intune. Sie sind dafür da, Geräteeinstellungen und -features hinzuzufügen, die nicht in Intune integriert sind.

Wenn Sie macOS-Geräte verwenden, gibt es zwei Möglichkeiten, benutzerdefinierte Einstellungen in Intune zu importieren:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple-Profil-Manager](https://support.apple.com/profile-manager)

Mit diesen beiden Tools können Sie Einstellungen in ein Konfigurationsprofil exportieren. Diese Datei importieren Sie dann in Intune und weisen das Profil Ihren macOS-Benutzern und -Geräten zu. Nach der Zuweisung werden die Einstellungen verteilt. Außerdem erstellen Sie eine Baseline oder einen Standard für macOS in Ihrer Organisation.

Dieser Artikel enthält eine Anleitung zur Verwendung von Apple Configurator und Apple Profile Manager und beschreibt die Eigenschaften, die Sie konfigurieren können.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie das Profil.](device-profile-create.md)

## <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- Wenn Sie mit **Apple Configurator** das Konfigurationsprofil erstellen, achten Sie darauf, dass die exportierten Einstellungen mit der macOS-Version auf den Geräten kompatibel sind. In der **Referenz zu Konfigurationsprofilen** und der **Referenz zum Protokoll für die Verwaltung mobiler Geräte** auf der [Apple Developer-Website](https://developer.apple.com/) finden Sie Informationen zum Beheben von Kompatibilitätsproblemen.

- Beachten Sie bei der Verwendung des **Apple-Profil-Managers** Folgendes:

  - Aktivieren Sie die [Verwaltung mobiler Geräte](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) im Profil-Manager.
  - Fügen Sie im Profil-Manager [macOS-Geräte](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) hinzu.
  - Nachdem Sie ein Gerät im Profil-Manager hinzugefügt haben, navigieren Sie zu **Bibliothek** > **Geräte**, wählen Sie Ihr Gerät aus, und klicken Sie auf **Einstellungen**. Legen Sie die allgemeinen, Sicherheits-, Datenschutz-, Verzeichnis- und Zertifikateinstellungen für das Gerät fest.

    Laden Sie diese Datei herunter, und speichern Sie sie. Diese Datei fügen Sie in das Intune-Profil ein. 

  - Achten Sie darauf, dass die Einstellungen, die Sie aus dem Apple-Profil-Manager exportieren, mit der macOS-Version auf den Geräten kompatibel sind. In der **Referenz zu Konfigurationsprofilen** und der **Referenz zum Protokoll für die Verwaltung mobiler Geräte** auf der [Apple Developer-Website](https://developer.apple.com/) finden Sie Informationen zum Beheben von Kompatibilitätsproblemen.

## <a name="custom-configuration-profile-settings"></a>Einstellungen für das benutzerdefinierte Konfigurationsprofil

- **Name des benutzerdefinierten Konfigurationsprofils:** Geben Sie einen Namen für die Richtlinie ein. Dieser Name wird auf dem Gerät und im Intune-Status angezeigt.
- **Konfigurationsprofildatei:** Navigieren Sie zum mit Apple Configurator oder dem Apple-Profil-Manager erstellten Konfigurationsprofil. Die importierte Datei wird im Bereich **Dateiinhalt** angezeigt.

  Sie können Ihren `.mobileconfig` Dateien auch Geräte Token hinzufügen. Geräte Token werden verwendet, um gerätespezifische Informationen hinzuzufügen. Geben Sie zum Beispiel zur Anzeige der Seriennummer `{{serialnumber}}` ein. Auf dem Gerät wird der Text ähnlich `123456789ABC`dem angezeigt, der für jedes Gerät eindeutig ist. Achten Sie darauf, bei der Eingabe von Variablen geschweifte Klammern `{{ }}` zu verwenden. [App-Konfigurationstoken](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) umfassen eine Reihe von Variablen, die Sie nutzen können. Zudem können Sie `deviceid` oder einen anderen gerätespezifischen Wert verwenden.

  > [!NOTE]
  > Variablen werden nicht in der Benutzeroberfläche überprüft und beachten die Groß-/Kleinschreibung. Daher gibt es möglicherweise Profile, die mit fehlerhaften Eingaben gespeichert wurden. Wenn Sie beispielsweise `{{DeviceID}}` anstelle von `{{deviceid}}` eingeben, wird die Zeichenfolge anstelle der eindeutigen Geräte-ID angezeigt. Stellen Sie sicher, dass Sie die richtigen Informationen eingeben.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](device-profile-assign.md).

Weitere Informationen finden Sie im [Artikel zum Erstellen eines Profils auf einem iOS-Gerät](custom-settings-ios.md).
