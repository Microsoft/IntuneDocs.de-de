---
title: Einrichten der Intune-Registrierung für vollständig verwaltete Android Enterprise-Geräte
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie vollständig verwaltete Android Enterprise-Geräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 755aefb955c2d30652434f2bd2e91981145fc56f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505593"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Einrichten der Intune-Registrierung von vollständig verwalteten Android Enterprise-Geräten 

Vollständig verwaltete Android Enterprise-Geräte sind unternehmenseigene Geräte, die einem einzelnen Benutzer zugeordnet sind und ausschließlich für die Arbeit verwendet werden und nicht für persönliche Zwecke. Administratoren können das gesamte Gerät verwalten und Richtlinienkontrollen durchsetzen, die für Arbeitsprofile nicht verfügbar sind, z. B.:
- Installieren von Apps nur über Managed Google Play zulassen
- Deinstallieren von verwalteten Apps blockieren
- Zurücksetzen von Geräten auf Werkseinstellungen durch Benutzer verhindern usw.

Intune unterstützt Sie beim Bereitstellen von Apps und Einstellungen für Android Enterprise-Geräte, einschließlich vollständig verwaltete Android Enterprise-Geräte. Ausführliche Informationen über Android Enterprise finden Sie in den [Voraussetzungen für Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Technische Anforderungen

Sie benötigen einen eigenständigen Intune-Mandanten, um vollständig verwaltete Android Enterprise-Geräte zu verwalten. Die Verwaltung vollständig verwalteter Geräte ist weder im hybriden Modus (mit SCCM verknüpft) noch in der älteren Verwaltungskonsole von Silverlight verfügbar.

Geräte müssen folgende Anforderungen erfüllen, um als vollständig verwaltete Android Enterprise-Geräte verwaltet zu werden:

- Mindestens Android-Betriebssystemversion 6.0.
- Geräte müssen ein Android-Build ausführen, das über GMS-Konnektivität (Google Mobile Services) verfügt. Geräte müssen über GMS verfügen und dazu in der Lage sein, eine Verbindung mit GMS herzustellen.

Wenn die obigen Anforderungen erfüllt sind, gibt es keine Einschränkungen bezüglich Gerätehersteller bzw. OEM.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Einrichten der Verwaltung vollständig verwalteter Android Enterprise-Geräte

Führen Sie die folgenden Schritte aus, um die Verwaltung für vollständig verwaltete Android Enterprise-Geräte einzurichten:

1. Sie müssen Sie [die MDM-Autorität (Mobile Device Management, mobile Geräteverwaltung) auf **Microsoft Intune** festlegen](../fundamentals/mdm-authority-set.md), um die Verwaltung mobiler Geräte vorzubereiten. Sie legen dieses Element nur einmal fest, wenn Sie die Ersteinrichtung von Intune für die Verwaltung mobiler Geräte durchführen.
2. [Verknüpfen Sie Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto](connect-intune-android-enterprise.md).
3. [Zulassen unternehmenseigener Benutzergeräte](#enable-corporate-owned-user-devices)
4. [Registrieren der vollständig verwalteten Geräte](#enroll-the-fully-managed-devices)

### <a name="enable-corporate-owned-user-devices"></a>Zulassen unternehmenseigener Benutzergeräte

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und wählen Sie **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Benutzergeräte** aus.
2. Wählen Sie **Ja** unter **Benutzern die Registrierung unternehmenseigener Benutzergeräte ermöglichen** aus.

> [!NOTE]
> Wenn Sie eine Richtlinie für den bedingten Zugriff mit Azure AD definiert haben, die das Steuerelement *Markieren des Geräts als kompatibel erforderlich* verwendet sowie für **Alle Cloud-Apps**, **Android** und **Browser** gilt, müssen Sie die **Microsoft Intune**-Cloud-App aus dieser Richtlinie ausschließen. Der Grund: Beim Android-Setupvorgang wird eine Chrome-Registerkarte zum Authentifizieren Ihrer Benutzer während der Registrierung verwendet. Weitere Informationen finden Sie in der [Dokumentation zum bedingten Zugriff mit Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/).

Wenn für diese Einstellung **Ja** ausgewählt ist, erhalten Sie ein Registrierungstoken (eine zufällige Zeichenfolge) und einen QR-Code für Ihren Intune-Mandanten. Dieses einzelne Registrierungstoken ist für all Ihre Benutzer gültig und läuft nicht ab. Abhängig vom Android-Betriebssystem und der Version des Geräts können Sie entweder das Token oder den QR-Code verwenden, um das Gerät zu registrieren.

## <a name="enroll-the-fully-managed-devices"></a>Registrieren vollständig verwalteter Android-Geräte
Sie können jetzt [Ihre vollständig verwalteten Geräte registrieren](android-dedicated-devices-fully-managed-enroll.md).

## <a name="next-steps"></a>Nächste Schritte
- [Add Android Enterprise fully managed device configuration policies (Hinzufügen von Konfigurationsrichtlinien für vollständig verwaltete Android Enterprise-Geräte)](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte](../apps/app-configuration-policies-use-android.md)

