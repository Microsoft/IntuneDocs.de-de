---
title: Einrichten der Intune-Registrierung für vollständig verwaltete Android-Geräte
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie vollständig verwaltete Android-Geräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 45c1d1f293454b32b97c8147f08809565714743a
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387204"
---
# <a name="set-up-intune-enrollment-of-android-fully-managed-devices-preview"></a>Einrichten der Intune-Registrierung von vollständig verwalteten Android-Geräten (Vorschauversion)

Vollständig verwaltete Android-Geräte sind unternehmenseigene Geräte, die einem einzelnen Benutzer zugeordnet sind und ausschließlich für die Arbeit verwendet werden und nicht für persönliche Zwecke. Administratoren können das gesamte Gerät verwalten und Richtlinienkontrollen durchsetzen, die für Arbeitsprofile nicht verfügbar sind, z. B.:
- Installieren von Apps nur über den Managed Google Play Store zulassen
- Deinstallieren von verwalteten Apps blockieren
- Zurücksetzen von Geräten auf Werkseinstellungen durch Benutzer verhindern usw.

Intune unterstützt Sie beim Bereitstellen von Apps und Einstellungen für Android Enterprise-Geräte, einschließlich vollständig verwaltete Android-Geräte. Ausführliche Informationen über Android Enterprise finden Sie in den [Voraussetzungen für Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Technische Anforderungen

Sie benötigen einen eigenständigen Intune-Mandanten, um vollständig verwaltete Android-Geräte zu verwalten. Die Verwaltung vollständig verwalteter Geräte ist weder im hybriden Modus (mit SCCM verknüpft) noch in der älteren Verwaltungskonsole von Silverlight verfügbar.

Geräte müssen folgende Anforderungen erfüllen, um als vollständig verwaltete Android-Geräte verwaltet zu werden:

- Mindestens Android-Betriebssystemversion 6.0.
- Geräte müssen ein Android-Build ausführen, das über GMS-Konnektivität (Google Mobile Services) verfügt. Geräte müssen über GMS verfügen und dazu in der Lage sein, eine Verbindung mit GMS herzustellen.

Wenn die obigen Anforderungen erfüllt sind, gibt es keine Einschränkungen bezüglich Gerätehersteller bzw. OEM.

## <a name="set-up-android-fully-managed-device-management"></a>Einrichten der Verwaltung vollständig verwalteter Android-Geräte

Führen Sie die folgenden Schritte aus, um die Verwaltung für vollständig verwaltete Android-Geräte einzurichten:

1. Sie müssen Sie [die MDM-Autorität (Mobile Device Management, mobile Geräteverwaltung) auf **Microsoft Intune** festlegen](mdm-authority-set.md), um die Verwaltung mobiler Geräte vorzubereiten. Sie legen dieses Element nur einmal fest, wenn Sie die Ersteinrichtung von Intune für die Verwaltung mobiler Geräte durchführen.
2. [Verknüpfen Sie Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto](connect-intune-android-enterprise.md).
3. [Zulassen unternehmenseigener Benutzergeräte](#enable-corporate-owned-user-devices)
4. [Registrieren der vollständig verwalteten Geräte](#enroll-the-fully-managed-devices)

### <a name="enable-corporate-owned-user-devices"></a>Zulassen unternehmenseigener Benutzergeräte

1. Rufen Sie das [Intune-Portal](https://portal.azure.com) auf, und klicken Sie auf **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Geräte (Vorschau)**.
2. Wählen Sie **Ja** unter **Benutzern die Registrierung unternehmenseigener Benutzergeräte ermöglichen** aus.

Wenn für diese Einstellung **Ja** ausgewählt ist, erhalten Sie ein Registrierungstoken (eine zufällige Zeichenfolge) und einen QR-Code für Ihren Intune-Mandanten. Dieses einzelne Registrierungstoken ist für all Ihre Benutzer gültig und läuft nicht ab. Je nach Android-Betriebssystem und Version des Geräts können Sie entweder das Token oder den QR-Code zum Registrieren des Kioskgeräts verwenden.

## <a name="enroll-the-fully-managed-devices"></a>Registrieren vollständig verwalteter Android-Geräte
Sie können jetzt [Ihre vollständig verwalteten Geräte registrieren](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Überlegungen zu diesem Vorschaufeature
Diese Public Preview enthält Kernfeatures für Lösungen für vollständig verwaltete Android-Geräte. Teilen Sie dem Team Ihre Erfahrungen mit dem Vorschaufeature über aktuelle Kommunikationskanäle mit (z. B. [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

Die folgenden Features werden in dieser Vorschau für vollständig verwaltete Android-Geräte unterstützt:
- Geräteregistrierung per NFC, Eingabe von Tokens, QR-Code und Zero-Touch
- Gerätekonfiguration für Benutzergruppen
- App-Verteilung und Konfiguration für Benutzergruppen


Beachten Sie bei der Verwendung dieses Vorschaufeatures Folgendes:
- Von in der Vorschau befindlichen Features wird bei unternehmenskritischen oder Produktionsbereitstellungen abgeraten. 
- Vorschaufeatures werden gemäß Produktionsstandards in Microsoft Intune implementiert. Allerdings stehen nicht alle Intune-Features für die Verwendung mit vollständig verwalteten Android-Benutzergeräten zur Verfügung. Vorschaufeatures sind in der Intune-Konsole deutlich mit „(Vorschau)“ gekennzeichnet. 
- Die Vorschaufeatures werden vollständig über die üblichen Intune-Supportkanäle unterstützt.
- Das Registrieren von vollständig verwalteten Android-Geräten mit Samsung Knox Mobile Enrollment wird in der Public Preview nicht unterstützt. 
- Die Verwendung der Intune-Unternehmensportal-App wird auf vollständig verwalteten Android-Geräten nicht unterstützt. 
- Intune-Features wie der bedingte Zugriff, App-Schutzrichtlinien und die Zertifikatbereitstellung werden in der Public Preview nicht unterstützt. 
- Gerätegruppenziele für Profile oder Apps werden in der Public Preview nicht unterstützt. Lediglich Benutzergruppenziele werden unterstützt. 
- Es gibt keine hochwertige Benutzeroberfläche zur Konfiguration von E-Mails, WLAN oder VPNs. Verwenden Sie App-Konfigurationsrichtlinien zum Konfigurieren unterstützter App-Konfigurationseinstellung.

## <a name="next-steps"></a>Nächste Schritte
- [Hinzufügen von Konfigurationsrichtlinien für vollständig verwaltete Android-Geräte](device-restrictions-android-for-work.md#device-owner-only)
- [Konfigurieren von App-Konfigurationsrichtlinien für vollständig verwaltete Android-Geräte](app-configuration-policies-use-android.md)

