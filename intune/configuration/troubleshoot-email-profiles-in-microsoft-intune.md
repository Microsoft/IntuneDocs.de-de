---
title: 'Behandeln von Problemen mit E-Mail-Profilen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Häufig auftretende Probleme und Lösungen für E-Mail-Profile in Microsoft Intune, darunter doppelte E-Mail-Profile und Fehler auf Android-Geräten mit Samsung KNOX Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19830130f992a002b73402f5e13a8f062539917
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512669"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Häufig auftretende Probleme und Lösungen für E-Mail-Profile in Microsoft Intune

Erfahren Sie mehr zu einigen häufig auftretenden Problemen mit E-Mail-Profilen und den entsprechenden Lösungen.

## <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- E-Mail-Profile werden für den Benutzer bereitgestellt, der das Gerät registriert hat. Für die Konfiguration des E-Mail-Profils werden in Intune die Azure AD-Eigenschaften (Azure Active Directory) des E-Mail-Benutzerprofils bei der Anmeldung verwendet. Weitere Informationen hierzu finden Sie unter [Hinzufügen von E-Mail-Einstellungen für Geräte mit Intune](email-settings-configure.md).
- Stellen Sie für Android Enterprise über den verwalteten Google Play Store Gmail oder Nine for Work bereit. Eine Anleitung hierzu finden Sie unter [Hinzufügen verwalteter Google Play-Apps](../apps/apps-add-android-for-work.md).
- In Microsoft Outlook für iOS/iPadOS und Android werden E-Mail-Profile nicht unterstützt. Stellen Sie stattdessen eine Konfigurationsrichtlinie für Apps bereit. Weitere Informationen finden Sie unter [Microsoft Outlook-Konfigurationseinstellungen](../apps/app-configuration-policies-outlook.md).
- E-Mail-Profile, deren Ziel Gerätegruppen (und nicht Benutzergruppen) sind, werden möglicherweise nicht an das Gerät übermittelt. Verfügt das Gerät über einen primären Benutzer, sollte die Geräteausrichtung funktionieren. Enthält das E-Mail-Profil Benutzerzertifikate, vergewissern Sie sich, dass als Ziel Benutzergruppen festgelegt sind.
- Benutzer werden möglicherweise wiederholt zur Eingabe des Kennworts für das E-Mail-Profil aufgefordert. Überprüfen Sie in diesem Szenario alle Zertifikate, auf die im E-Mail-Profil verwiesen wird. Ist eines der Zertifikate nicht auf einen Benutzer ausgerichtet, versucht Intune, das E-Mail-Profil noch mal bereitzustellen.

## <a name="device-already-has-an-email-profile-installed"></a>Auf dem Gerät ist bereits ein E-Mail-Profil installiert

Wenn Benutzer vor der Registrierung bei Intune oder Office 365 MDM ein E-Mail-Profil erstellen, funktioniert das von Intune bereitgestellte E-Mail-Profil möglicherweise nicht wie erwartet:

- **iOS/iPadOS**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Das vom Benutzer erstellte E-Mail-Profil blockiert die Bereitstellung des von Intune erstellten Profils. Dieses Problem tritt häufig auf, da iOS-/iPadOS-Benutzer in der Regel zuerst ein E-Mail-Profil erstellen und dann die Registrierung vornehmen. In der Unternehmensportal-App wird der Benutzer als nicht konform aufgeführt, und der Benutzer wird möglicherweise aufgefordert, das E-Mail-Profil zu entfernen.

  Der Benutzer muss sein E-Mail-Profil, damit das Intune-Profil bereitgestellt werden kann. Weisen Sie die Benutzer an, sich erst zu registrieren und anschließend Intune die Bereitstellung des Profils zu gestatten, um dieses Problem zu vermeiden. Anschließend können die Benutzer ihr E-Mail-Profil erstellen.

- **Windows**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Intune überschreibt das vorhandene vom Benutzer erstellte E-Mail-Profil.

- **Samsung KNOX Standard**: Intune identifiziert basierend auf der E-Mail-Adresse ein doppeltes E-Mail-Konto und überschreibt es mit dem Intune-Profil. Wenn der Benutzer dieses Konto konfiguriert, wird es erneut durch das Intune-Profil überschrieben. Dies kann für den Benutzer, dessen Kontokonfiguration überschrieben wird, verwirrend sein.

Samsung KNOX identifiziert das Profil nicht anhand des Hostnamens. Es wird empfohlen, nicht mehrere E-Mail-Profile zur Bereitstellung derselben E-Mail-Adresse auf unterschiedlichen Hosts zu erstellen, da diese sich gegenseitig überschreiben.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Fehler „0x87D1FDE8“ für KNOX Standard-Gerät

**Problem:** Nach dem Erstellen und Bereitstellen eines Exchange Active Sync-E-Mail-Profils für Samsung KNOX Standard für verschiedene Android-Geräte werden der Fehler **0x87D1FDE8** oder ein **Fehler bei der Wiederherstellung** auf der Registerkarte „Eigenschaften“ > „Richtlinie“ des Geräts angezeigt.

Überprüfen Sie die Konfiguration Ihres EAS-Profils für Samsung KNOX und die Quellrichtlinie. Die Samsung-Option zum Synchronisieren von Notizen wird nicht mehr unterstützt, und diese Option sollte in Ihrem Profil nicht ausgewählt werden. Achten Sie darauf, dass Geräte genug Zeit hatten, um die Richtlinie zu verarbeiten (bis zu 24 Stunden).

## <a name="unable-to-send-images-from--email-account"></a>Senden von Bildern über E-Mail-Konto nicht möglich

Benutzer, deren E-Mail-Konten automatisch konfiguriert wurden, können keine Bilder von ihren Geräten senden. Dies ist der Fall, wenn die Option **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** nicht aktiviert ist.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** aus.
3. Klicken Sie auf Ihr E-Mail-Profil > **Eigenschaften** > **Einstellungen**.
4. Legen Sie die Einstellung **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** auf **Aktivieren** fest.

## <a name="next-steps"></a>Nächste Schritte

Fordern Sie [Hilfe beim Microsoft-Support](../fundamentals/get-support.md) an, oder nutzen Sie die [Communityforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
