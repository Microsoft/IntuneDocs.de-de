---
title: 'Behandeln von Problemen mit E-Mail-Profilen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Häufig auftretende Probleme und Lösungen für E-Mail-Profile in Microsoft Intune, darunter doppelte E-Mail-Profile und Fehler auf Android-Geräten mit Samsung KNOX Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
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
ms.openlocfilehash: 38e8998d1720434b0fe866fc5cd41a0b733fc49b
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059840"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Häufig auftretende Probleme und Lösungen für E-Mail-Profile in Microsoft Intune

Erfahren Sie mehr zu einigen häufig auftretenden Problemen mit E-Mail-Profilen und den entsprechenden Lösungen.

## <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- E-Mail-Profile werden für den Benutzer bereitgestellt, der das Gerät registriert hat. Um das e-Mail-Profil zu konfigurieren, verwendet InTune die Azure Active Directory (AD)-Eigenschaften im e-Mail-Profil des Benutzers bei der Anmeldung. [E-Mail-Einstellungen zu Geräten hinzufügen](email-settings-configure.md) ist möglicherweise eine gute Ressource.
- Für Android Enterprise können Sie Gmail oder neun für Arbeiten mithilfe der verwalteten Google Play Store bereitstellen. [Verwaltete Google Play-apps hinzufügen](../apps/apps-add-android-for-work.md) listet die Schritte auf.
- Microsoft Outlook für IOS und Android unterstützt keine e-Mail-Profile. Stellen Sie stattdessen eine APP-Konfigurationsrichtlinie bereit. Weitere Informationen finden Sie unter [Outlook-Konfigurationseinstellung](../apps/app-configuration-policies-outlook.md).
- E-Mail-Profile, die auf Gerätegruppen (Nichtbenutzer Gruppen) abzielen, werden möglicherweise nicht an das Gerät übermittelt. Wenn das Gerät über einen primären Benutzer verfügt, sollte die Geräte Ausrichtung funktionieren. Wenn das e-Mail-Profil Benutzerzertifikate enthält, achten Sie darauf, dass Sie auf Benutzergruppen abzielen.
- Benutzer werden möglicherweise wiederholt aufgefordert, Ihr Kennwort für das e-Mail-Profil einzugeben. Überprüfen Sie in diesem Szenario alle Zertifikate, auf die im e-Mail-Profil verwiesen wird. Wenn eines der Zertifikate nicht für einen Benutzer bestimmt ist, wird von InTune erneut versucht, das e-Mail-Profil bereitzustellen.

## <a name="device-already-has-an-email-profile-installed"></a>Auf dem Gerät ist bereits ein E-Mail-Profil installiert

Wenn Benutzer ein e-Mail-Profil erstellen, bevor Sie sich bei InTune oder Office 365 MDM anmelden, funktioniert das von InTune bereitgestellte e-Mail-Profil möglicherweise nicht wie erwartet:

- **iOS**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Das vom Benutzer erstellte E-Mail-Profil blockiert die Bereitstellung des von Intune erstellten Profils. Dieses Problem tritt häufig auf, da iOS-Benutzer in der Regel erst ein E-Mail-Profil erstellen und anschließend die Registrierung vornehmen. In der Unternehmensportal-App wird der Benutzer als nicht konform aufgeführt, und der Benutzer wird möglicherweise aufgefordert, das E-Mail-Profil zu entfernen.

  Der Benutzer muss sein E-Mail-Profil, damit das Intune-Profil bereitgestellt werden kann. Weisen Sie die Benutzer an, sich erst zu registrieren und anschließend Intune die Bereitstellung des Profils zu gestatten, um dieses Problem zu vermeiden. Anschließend können die Benutzer ihr E-Mail-Profil erstellen.

- **Windows**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Intune überschreibt das vorhandene vom Benutzer erstellte E-Mail-Profil.

- **Samsung KNOX Standard:** Intune identifiziert basierend auf der E-Mail-Adresse ein doppeltes E-Mail-Konto und überschreibt es mit dem Intune-Profil. Wenn der Benutzer dieses Konto konfiguriert, wird es erneut durch das Intune-Profil überschrieben. Dies kann für den Benutzer, dessen Kontokonfiguration überschrieben wird, verwirrend sein.

Samsung KNOX identifiziert das Profil nicht anhand des Hostnamens. Es wird empfohlen, nicht mehrere E-Mail-Profile zur Bereitstellung derselben E-Mail-Adresse auf unterschiedlichen Hosts zu erstellen, da diese sich gegenseitig überschreiben.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Fehler „0x87D1FDE8“ für KNOX Standard-Gerät

**Problem**: Nach dem Erstellen und Bereitstellen eines Exchange Active Sync-E-Mail-Profils für Samsung KNOX Standard für verschiedene Android-Geräte melden diese den Fehler **0x87D1FDE8**, oder es wird ein **Fehler bei der Wiederherstellung** auf der Registerkarte „Eigenschaften“ > „Richtlinie“ des Geräts angezeigt.

Überprüfen Sie die Konfiguration Ihres EAS-Profils für Samsung KNOX und die Quellrichtlinie. Die Samsung-Option zum Synchronisieren von Notizen wird nicht mehr unterstützt, und diese Option sollte in Ihrem Profil nicht ausgewählt werden. Achten Sie darauf, dass Geräte genug Zeit hatten, um die Richtlinie zu verarbeiten (bis zu 24 Stunden).

## <a name="unable-to-send-images-from--email-account"></a>Senden von Bildern über E-Mail-Konto nicht möglich

Benutzer, deren E-Mail-Konten automatisch konfiguriert wurden, können keine Bilder von ihren Geräten senden. Dies ist der Fall, wenn die Option **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** nicht aktiviert ist.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** aus.
3. Wählen Sie Ihr e-Mail-Profil > **Eigenschaften** > **Einstellungen**aus.
4. Legen Sie die Einstellung **e-Mail-Versand von Anwendungen von Drittanbietern zulassen** auf **aktivieren**fest.

## <a name="next-steps"></a>Nächste Schritte

Fordern Sie [Hilfe beim Microsoft-Support](../fundamentals/get-support.md) an, oder nutzen Sie die [Communityforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
