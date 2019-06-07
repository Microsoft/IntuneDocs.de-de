---
title: 'Behandeln von Problemen mit E-Mail-Profilen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Häufig auftretende Probleme und Lösungen für E-Mail-Profile in Microsoft Intune, darunter doppelte E-Mail-Profile und Fehler auf Android-Geräten mit Samsung KNOX Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0fe37deb63457fef869df0f7263970a4e53cb29
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402706"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Häufig auftretende Probleme und Lösungen für E-Mail-Profile in Microsoft Intune

Erfahren Sie mehr zu einigen häufig auftretenden Problemen mit E-Mail-Profilen und den entsprechenden Lösungen.

## <a name="device-already-has-an-email-profile-installed"></a>Auf dem Gerät ist bereits ein E-Mail-Profil installiert

Wenn Benutzer vor der Registrierung in Intune ein E-Mail-Profil erstellen, funktioniert das Intune-E-Mail-Profil möglicherweise nicht wie erwartet:

- **iOS**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Das vom Benutzer erstellte E-Mail-Profil blockiert die Bereitstellung des von Intune erstellten Profils. Dieses Problem tritt häufig auf, da iOS-Benutzer in der Regel erst ein E-Mail-Profil erstellen und anschließend die Registrierung vornehmen. In der Unternehmensportal-App wird der Benutzer als nicht konform aufgeführt, und der Benutzer wird möglicherweise aufgefordert, das E-Mail-Profil zu entfernen.

  Der Benutzer muss sein E-Mail-Profil, damit das Intune-Profil bereitgestellt werden kann. Weisen Sie die Benutzer an, sich erst zu registrieren und anschließend Intune die Bereitstellung des Profils zu gestatten, um dieses Problem zu vermeiden. Anschließend können die Benutzer ihr E-Mail-Profil erstellen.

- **Windows**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Intune überschreibt das vorhandene vom Benutzer erstellte E-Mail-Profil.

- **Samsung KNOX Standard:** Intune identifiziert basierend auf der E-Mail-Adresse ein doppeltes E-Mail-Konto und überschreibt es mit dem Intune-Profil. Wenn der Benutzer dieses Konto konfiguriert, wird es erneut durch das Intune-Profil überschrieben. Dies kann für den Benutzer, dessen Kontokonfiguration überschrieben wird, verwirrend sein.

Samsung KNOX identifiziert das Profil nicht anhand des Hostnamens. Es wird empfohlen, nicht mehrere E-Mail-Profile zur Bereitstellung derselben E-Mail-Adresse auf unterschiedlichen Hosts zu erstellen, da diese sich gegenseitig überschreiben.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Fehler „0x87D1FDE8“ für KNOX Standard-Gerät

**Problem**: Nach dem Erstellen und Bereitstellen eines Exchange Active Sync-E-Mail-Profils für Samsung KNOX Standard für verschiedene Android-Geräte melden diese den Fehler **0x87D1FDE8**, oder es wird ein **Fehler bei der Wiederherstellung** auf der Registerkarte „Eigenschaften“ > „Richtlinie“ des Geräts angezeigt.

Überprüfen Sie die Konfiguration Ihres EAS-Profils für Samsung KNOX und die Quellrichtlinie. Die Samsung-Option zum Synchronisieren von Notizen wird nicht mehr unterstützt, und diese Option sollte in Ihrem Profil nicht ausgewählt werden. Achten Sie darauf, dass Geräte genug Zeit hatten, um die Richtlinie zu verarbeiten (bis zu 24 Stunden).

## <a name="unable-to-send-images-from--email-account"></a>Senden von Bildern über E-Mail-Konto nicht möglich

Gilt für: Intune im klassischen Azure-Portal

Benutzer, deren E-Mail-Konten automatisch konfiguriert wurden, können keine Bilder von ihren Geräten senden. Dies ist der Fall, wenn die Option **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** nicht aktiviert ist.

### <a name="intune-solution"></a>Intune-Lösung

1. Öffnen Sie die Microsoft Intune-Verwaltungskonsole, und wählen Sie die Workload **Richtlinie** aus, und klicken Sie auf **Konfigurationsrichtlinie**.

2. Wählen Sie das E-Mail-Profil aus, und klicken Sie auf **Bearbeiten**.

3. Wählen Sie **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** .

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integriert mit Windows Intune

1. Öffnen Sie die Configuration Manager-Konsole, und klicken Sie auf **Assets and Compliance** (Bestand und Kompatibilität).

2. Erweitern Sie **Übersicht** > **Konformitätseinstellungen** > **Zugriff auf Unternehmensressourcen**, und wählen Sie **E-Mail-Profile** aus.

3. Klicken Sie mit der rechten Maustaste auf das E-Mail-Profil, und öffnen Sie **Eigenschaften**.

4. Wählen Sie auf der Registerkarte **Synchronisierungseinstellungen** die Option **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** aus.

## <a name="next-steps"></a>Nächste Schritte

Fordern Sie [Hilfe beim Microsoft-Support](get-support.md) an, oder nutzen Sie die [Communityforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).