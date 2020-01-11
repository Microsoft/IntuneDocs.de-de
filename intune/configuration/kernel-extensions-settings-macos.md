---
title: Einstellungen für die macOS-Kernel Erweiterung in Microsoft InTune-Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Hiermit können Sie auf macOS-Geräten Einstellungen hinzufügen, konfigurieren oder erstellen, um Kernel Erweiterungen zu verwenden. Außerdem können Sie zulassen, dass Benutzer genehmigte Erweiterungen außer Kraft setzen, alle Erweiterungen von Team Bezeichnern zulassen oder bestimmte Erweiterungen oder apps in Microsoft InTune zulassen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 89f54111258b5e628d9f83c381fde146bf996216
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206328"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>macOS-Geräteeinstellungen zum Konfigurieren und Verwenden von Kernel Erweiterungen in InTune



In diesem Artikel werden die verschiedenen Einstellungen für Kernelerweiterungen aufgeführt und beschrieben, die Sie auf macOS-Geräten steuern können. Verwenden Sie diese Einstellungen als Teil ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte), um Kernel Erweiterungen auf Ihren Geräten hinzuzufügen und zu verwalten.

Weitere Informationen zu Kernel Erweiterungen in InTune und Voraussetzungen finden Sie unter [Hinzufügen von macOS-Kernel Erweiterungen](../kernel-extensions-overview-macos.md).

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren macOS-Geräten zugewiesen oder bereitgestellt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Konfigurations Profil für Geräte-Kernel Erweiterungen](../kernel-extensions-overview-macos.md).

> [!NOTE]
> Diese Einstellungen gelten für verschiedene Registrierungs Typen. Weitere Informationen zu den verschiedenen Registrierungs Typen finden Sie unter [macOS](../macos-enroll.md)-Registrierung.

## <a name="kernel-extensions"></a>Kernel Erweiterungen

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>Einstellungen gelten für: vom Benutzer genehmigte, automatisierte Geräteregistrierung

- **Benutzer Überschreibungen zulassen**: **erlauben** Sie Benutzern das Genehmigen von Kernel Erweiterungen, die nicht im Konfigurations Profil enthalten sind. **Nicht konfiguriert** (Standardeinstellung) verhindert, dass Benutzer Erweiterungen zulassen, die nicht im Konfigurations Profil enthalten sind. Dies bedeutet, dass nur im Konfigurations Profil enthaltene Erweiterungen zulässig sind.

  Weitere Informationen zu dieser Funktion finden Sie unter [Laden von Benutzer genehmigten Kernel Erweiterungen](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) (öffnet die Website von Apple).

- **Zulässige Team**-IDs: Verwenden Sie diese Einstellung, um eine oder mehrere Team-IDs zuzulassen. Alle Kernel Erweiterungen, die mit den von Ihnen eingegebenen Team-IDs signiert wurden, sind zulässig und vertrauenswürdig. Mit anderen Worten: Verwenden Sie diese Option, um alle Kernel Erweiterungen innerhalb derselben Team-ID zuzulassen, bei der es sich möglicherweise um einen bestimmten Entwickler oder Partner handelt.

  **Fügen** Sie eine Team-ID gültiger und signierter Kernel Erweiterungen hinzu, die Sie laden möchten. Sie können mehrere Team-IDs hinzufügen. Der Team Bezeichner muss alphanumerisch (Buchstaben und Ziffern) und 10 Zeichen lang sein. Geben Sie beispielsweise `ABCDE12345` ein.

  Nachdem Sie eine Team-ID hinzugefügt haben, kann Sie auch gelöscht werden.

  [Suchen Sie nach Ihrer Team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öffnet die Website von Apple), die weitere Informationen enthält.

- **Zulässige Kernel Erweiterungen**: Verwenden Sie diese Einstellung, um bestimmte Kernel Erweiterungen zuzulassen. Nur die von Ihnen eingegebenen Kernel Erweiterungen sind zulässig oder vertrauenswürdig. 

  **Fügen** Sie die Bündel-ID und den Team Bezeichner einer Kernel Erweiterung hinzu, die Sie laden möchten. Verwenden Sie für nicht signierte Legacy-Kernel Erweiterungen eine leere Team Kennung. Sie können mehrere Kernel Erweiterungen hinzufügen. Der Team Bezeichner muss alphanumerisch (Buchstaben und Ziffern) und 10 Zeichen lang sein. Geben Sie z. b. `com.contoso.appname.macos` für die **Bündel-ID**und `ABCDE12345` für die **Team**-ID ein.

  > [!TIP]
  > Um die Bündel-ID einer Kernel Erweiterung (kext) auf einem macOS-Gerät zu erhalten, können Sie folgende Aktionen ausführen:
  >
  > 1. Führen Sie im Terminal `kextstat | grep -v com.apple`aus, und notieren Sie sich die Ausgabe. Installieren Sie die gewünschte Software bzw. die gewünschte kext-Datei. Führen Sie `kextstat | grep -v com.apple` erneut aus, und suchen Sie nach Änderungen.
  >
  >    Im Terminal werden `kextstat` alle Kernel Erweiterungen im Betriebssystem auflisten. 
  >
  > 2. Öffnen Sie auf dem Gerät die Informations Eigenschafts Listen Datei (Info. plist) für einen kext. Die Bündel-ID wird angezeigt. Jeder kext verfügt über eine in gespeicherte Info. plist-Datei. 

> [!NOTE]
> Sie müssen keine Team-IDs und Kernel Erweiterungen hinzufügen. Sie können eine oder die andere konfigurieren.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../device-profile-assign.md) und [Überwachen von Profilen](../device-profile-monitor.md)
