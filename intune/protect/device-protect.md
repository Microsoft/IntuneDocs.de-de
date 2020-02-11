---
title: Schützen von Geräten mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr über die Methoden, mit denen Intune Ihnen helfen kann, Ihre Geräte vor nicht autorisiertem Zugriff und anderen Bedrohungen zu schützen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: conceptual
ms.subservice: protect
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c18b6bcc8ec6e8d78862c0368c920fd3d79ce2b5
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755577"
---
# <a name="protect-devices-with-microsoft-intune"></a>Schützen von Geräten mit Microsoft Intune

Mit Microsoft Intune können von Ihnen verwaltete Geräte und die Daten schützen, die auf diesen Geräten gespeichert sind.

## <a name="device-configuration"></a>Gerätekonfiguration
Die Intune-[Konfigurationsrichtlinien](../configuration/device-profiles.md) helfen Ihnen dabei, durch das Steuern zahlreicher Einstellungen und Funktionen Geräte zu schützen und zu konfigurieren. Beispiel:

- Sie können die Verwendung von Hardwarefeatures auf dem Gerät, z.B. die Kamera oder Bluetooth, einschränken.
- Sie können kompatible und nicht kompatible Apps konfigurieren. Sie werden benachrichtigt, wenn eine nicht kompatible App installiert wird. Einige Plattformen können die Installation blockieren.

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Zurücksetzen von Kennungen, wenn Geräte für ihre Benutzer gesperrt sind
Da der erste Schritt zum Schutz von Unternehmensdaten auf mobilen Geräten darin besteht, eine Kennung abzufragen, damit das Gerät verwendet werden kann, müssen Sie mitunter eine [Kennung zurücksetzen](../remote-actions/device-passcode-reset.md) oder einem Mitarbeiter hierbei helfen, entweder indem Sie die Kennung entfernen oder remote eine vorübergehende Kennung festlegen. Sie können verlorene oder gestohlene [Geräte auch remote sperren](../remote-actions/device-remote-lock.md).

## <a name="retire-devices-and-remove-data"></a>Außerkraftsetzen von Geräten und Entfernen von Daten
Wenn ein Gerät [aus der Intune-Verwaltung entfernt](../remote-actions/devices-wipe.md) werden soll (z. B. weil ein Benutzer die Organisation verlässt, oder das Gerät verloren bzw. gestohlen wurde), werden Sie wahrscheinlich Daten von diesem Gerät entfernen wollen. Intune bietet zahlreiche Methoden, um die Sicherheit Ihrer Unternehmensdaten zu gewährleisten.

## <a name="require-devices-to-be-compliant"></a>Verlangen, dass Geräte kompatibel sein müssen
Intune umfasst [Gerätekompatibilitätsrichtlinien](device-compliance-get-started.md), mit denen Sie Geräte auswerten (und in einigen Fällen auch Fehler beheben) können, die Ihren festgelegten Regeln nicht entsprechen. Sie können beispielsweise Berichte zu folgenden Themen erhalten:
- iOS-Geräte mit Jailbreak
- Verschlüsselte und nicht verschlüsselte Geräte
- Integrität von Windows 10-Geräten (gemäß Health Attestation)

## <a name="protect-apps-and-the-data-they-use"></a>Schützen von Apps und Daten, die verwendet werden
Intune bietet Ihnen eine Reihe von Funktionen an, die Sie zum Schützen Ihrer Apps und deren Daten verwenden können. Die Richtlinien der mobilen Anwendungsverwaltung (MAM) können
- Verhindern, dass Daten aus einer geschützten App gesichert werden
- Das Kopieren und Einfügen in andere Apps beschränken
- Festlegen, dass nur mit einer PIN auf eine App zugegriffen werden kann (weitere Informationen: [Schützen von Apps und Daten mit Microsoft Intune](../apps/app-protection-policy.md))

## <a name="add-an-additional-layer-of-protection-to-devices"></a>Hinzufügen einer zusätzlichen Schutzebene für Geräte
Die [mehrstufige Authentifizierung](../enrollment/multi-factor-authentication.md) (Multi-Factor Authentication, MFA) ist eine sicherere Methode der Authentifizierung der Benutzer von Geräten im Netzwerk.  Bei Verwendung von MFA müssen Benutzer ihre Identität zusätzlich zu Benutzername und Kennwort über einen Telefonanruf oder eine SMS bestätigen.

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Steuern der Einstellungen von Windows Hello for Business auf Windows-Geräten
Intune ermöglicht die Integration in [Windows Hello for Business](windows-hello.md). Dies ist eine alternative Anmeldemethode für Windows 10 und höher, die Active Directory oder ein Azure Active Directory-Konto verwendet, um ein Kennwort, eine Smartcard oder eine virtuelle Smartcard zu ersetzen.

## <a name="disable-activation-lock-on-ios-devices"></a>Deaktivieren der Aktivierungssperre auf iOS-Geräten
Die Aktivierungssperre ist eine Funktion, mit der Sie Ihre Geräte schützen können. Die Funktion erfordert die Eingabe der Apple-ID und des Kennworts, bevor das Gerät reaktiviert oder Daten vom Gerät gelöscht werden. Diese Funktion kann jedoch zu Problemen führen, z. B. wenn ein Benutzer das Unternehmen verlässt, ohne die Sperre aufzuheben. [Deaktivieren der Aktivierungssperre bei mit Intune überwachten iOS-Geräten](../remote-actions/device-activation-lock-disable.md) kann Ihnen helfen, die Sperre von überwachten iOS-Geräten zu entfernen, sodass sie neu zugewiesen oder gelöscht werden können.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [Mobile Threat Defense](mobile-threat-defense.md)
