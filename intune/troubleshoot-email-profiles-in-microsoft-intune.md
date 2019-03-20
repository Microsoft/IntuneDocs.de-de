---
title: 'Behandeln von Problemen mit E-Mail-Profilen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Probleme mit E-Mail-Profilen sowie Informationen zu ihrer Problembehandlung und Lösung.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: troubleshooting
ms.prod: ''
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
ms.openlocfilehash: 02eac7eaa42f6f9c97426e0536e48a4bc399ed08
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461021"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Problembehandlung bei E-Mail-Profilen in Microsoft Intune

Erfahren Sie mehr zu einigen häufig auftretenden Problemen mit E-Mail-Profilen und den entsprechenden Lösungen.

Wenn Sie weitere Hilfe benötigen, können Sie auch [Support für Microsoft Intune](get-support.md) anfordern.

## <a name="unable-to-send-images-from--email-account"></a>Senden von Bildern über E-Mail-Konto nicht möglich
Gilt für: Intune im klassischen Azure-Portal

Benutzer, deren E-Mail-Konten automatisch konfiguriert wurden, können keine Bilder von ihren Geräten senden. Dies ist der Fall, wenn die Option **Allow e-mail to be sent from third-party applications** (E-Mail-Versand über Anwendungen von Drittanbietern zulassen) nicht aktiviert ist.

### <a name="intune-solution"></a>Intune-Lösung

1. Öffnen Sie die Microsoft Intune-Verwaltungskonsole, und wählen Sie die Workload **Richtlinie** aus, und klicken Sie auf **Konfigurationsrichtlinie**.

2. Wählen Sie das E-Mail-Profil aus, und klicken Sie auf **Bearbeiten**.

3. Wählen Sie **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** .

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integriert mit Windows Intune

1. Öffnen Sie die Configuration Manager-Konsole, und klicken Sie auf **Assets and Compliance** (Bestand und Kompatibilität).

2. Erweitern Sie **Übersicht** > **Konformitätseinstellungen** > **Zugriff auf Unternehmensressourcen**, und wählen Sie **E-Mail-Profile** aus.

3. Klicken Sie mit der rechten Maustaste auf das E-Mail-Profil, und öffnen Sie **Eigenschaften**.

4. Wählen Sie auf der Registerkarte **Synchronisierungseinstellungen** die Option **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** aus.

## <a name="device-already-has-an-email-profile-installed"></a>Auf dem Gerät ist bereits ein E-Mail-Profil installiert

Wenn der Benutzer ein E-Mail-Profil installiert hat, bevor ein Intune-Profil bereitgestellt wurde, hat die Bereitstellung des E-Mail-Profils für Intune je nach Geräteplattform folgende Auswirkungen:

- **iOS**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Das vom Benutzer erstellte doppelte E-Mail-Profil blockiert die Bereitstellung eines Profils, das vom Intune-Administrator erstellt wurde. Dieses Problem tritt häufig auf, da iOS-Benutzer in der Regel erst ein E-Mail-Profil erstellen und anschließend die Registrierung vornehmen. Das Unternehmensportal informiert den Benutzer darüber, dass aufgrund des manuell konfigurierten E-Mail-Profils ein Konformitätsverstoß vorliegt, und fordert ihn dazu auf, dieses Profil zu entfernen. Der Benutzer sollte sein E-Mail-Profil entfernen, damit das Intune-Profil bereitgestellt werden kann. Geben Sie den Benutzern die Anweisung, sich erst zu registrieren und anschließend Intune die Bereitstellung des Profils zu erlauben, um dieses Problem zu vermeiden. Installieren Sie anschließend das vom Benutzer erstellte E-Mail-Profil.

- **Windows**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Intune überschreibt das vorhandene vom Benutzer erstellte E-Mail-Profil.

- **Samsung KNOX Standard:** Intune identifiziert basierend auf der E-Mail-Adresse ein doppeltes E-Mail-Konto und überschreibt es mit dem Intune-Profil. Wenn der Benutzer dieses Konto konfiguriert, wird es erneut durch das Intune-Profil überschrieben. Dies kann für den Benutzer, dessen Kontokonfiguration überschrieben wird, verwirrend sein.

Samsung KNOX identifiziert das Profil nicht anhand des Hostnamens. Es wird empfohlen, dass Sie das Erstellen von mehreren E-Mail-Profilen für die Bereitstellung für dieselbe E-Mail-Adresse auf unterschiedlichen Hosts vermeiden, da diese sich gegenseitig überschreiben.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Fehler „0x87D1FDE8“ für KNOX Standard-Gerät
**Problem**: Nach dem Erstellen und Bereitstellen eines Exchange Active Sync-E-Mail-Profils für Samsung KNOX Standard für verschiedene Android-Geräte melden diese den Fehler **0x87D1FDE8** oder einen **Fehler bei der Wiederherstellung** auf der Registerkarte „Eigenschaften“ > „Richtlinie“ des Geräts.

Überprüfen Sie die Konfiguration Ihres EAS-Profils für Samsung KNOX und die Quellrichtlinie. Die Samsung-Option zum Synchronisieren von Notizen wird nicht mehr unterstützt, und diese Option sollte in Ihrem Profil nicht ausgewählt werden. Achten Sie darauf, dass Geräte genug Zeit hatten, um die Richtlinie zu verarbeiten (bis zu 24 Stunden).

## <a name="next-steps"></a>Nächste Schritte
Wenn Sie weitere Hilfe benötigen, können Sie auch [Support für Microsoft Intune](get-support.md) anfordern.
