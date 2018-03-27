---
title: Behandeln von Problemen mit E-Mail-Profilen
description: Probleme mit E-Mail-Profilen sowie Informationen zu ihrer Problembehandlung und Lösung.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 382d9240d751c69f3b415ef9ab205b3ef596463a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Problembehandlung bei E-Mail-Profilen in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Hier werden einige Probleme mit E-Mail-Profilen sowie Informationen zu ihrer Problembehandlung und Lösung angeführt.

Wenn sich das Problem mit diesen Informationen nicht beheben lässt, finden Sie unter [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Anfordern von Support für Microsoft Intune) weitere Möglichkeiten, Hilfe zu erhalten.


## <a name="unable-to-send-images-from--email-account"></a>Senden von Bildern über E-Mail-Konto nicht möglich
Benutzer, deren E-Mail-Konten automatisch konfiguriert wurden, können keine Bilder von ihren Geräten senden.
Dies ist der Fall, wenn die Option **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen**  nicht aktiviert ist.

### <a name="intune-solution"></a>Intune-Lösung

1.  Öffnen Sie die Microsoft Intune-Verwaltungskonsole, und wählen Sie **Richtlinie** Workload &gt;**Konfigurationsrichtlinie**.

2.  Wählen Sie das E-Mail-Profil aus, und klicken Sie auf **Bearbeiten**.

3.  Wählen Sie **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** .

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager integriert mit Windows Intune

1.  Öffnen Sie in der Configuration Manager-Konsole &gt; **Bestand und Kompatibilität**.

2.  Erweitern Sie **Übersicht** -&gt; **Kompatibilitätseinstellungen** -&gt; **Zugriff auf Unternehmensressourcen**, und wählen Sie **E-Mail-Profile** aus.

3.  Klicken Sie mit der rechten Maustaste auf das E-Mail-Profil, und öffnen Sie **Eigenschaften**.

4.  Wählen Sie auf der Registerkarte **Synchronisierungseinstellungen** die Option **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen** aus.


## <a name="device-already-has-an-email-profile-installed"></a>Auf dem Gerät ist bereits ein E-Mail-Profil installiert

Wenn der Benutzer ein E-Mail-Profil installiert hat, bevor ein Profil durch Intune bereitgestellt wurde, hat die Bereitstellung des Intune-E-Mail-Profils je nach Geräteplattform folgende Auswirkungen:

-**iOS**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Das vom Benutzer erstellte doppelte E-Mail-Profil blockiert die Bereitstellung eines Profils, das vom Intune-Administrator erstellt wurde. Das ist ein häufig auftretendes Problem, da iOS-Benutzer in der Regel ein E-Mail-Profil erstellen und anschließend die Registrierung vornehmen. Das Unternehmensportal informiert den Benutzer darüber, dass es aufgrund seines manuell konfigurierten E-Mail-Profils nicht kompatibel ist, und fordert ihn dazu auf, dieses Profil zu entfernen. Der Benutzer sollte sein E-Mail-Profil entfernen, damit das Intune-Profil bereitgestellt werden kann. Weisen Sie Ihre Benutzer an, sich vor der Installation eines E-Mail-Profils zu registrieren und die Bereitstellung des Profils durch Intune zuzulassen, um das Problem zu vermeiden.

-**Windows**: Intune erkennt basierend auf dem Hostnamen und der E-Mail-Adresse ein vorhandenes doppeltes E-Mail-Profil. Intune überschreibt das vorhandene, vom Benutzer erstellte E-Mail-Profil.

-**Samsung KNOX**: Intune identifiziert basierend auf der E-Mail-Adresse ein doppeltes E-Mail-Konto und überschreibt es mit dem Intune-Profil. Wenn der Benutzer dieses Konto konfiguriert, wird es erneut durch das Intune-Profil überschrieben. Dies kann für den Benutzer, dessen Kontokonfiguration überschrieben wird, verwirrend sein.

Da Samsung KNOX zum Identifizieren des Profils keinen Hostnamen verwendet, wird davon abgeraten, mehrere E-Mail-Profile für die Bereitstellung unter derselben E-Mail-Adresse auf unterschiedlichen Hosts zu erstellen, da sie sich gegenseitig überschreiben.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Fehler „0x87D1FDE8“ für KNOX Standard-Gerät
**Problem**: Nach dem Erstellen und Bereitstellen eines Exchange ActiveSync-E-Mail-Profils für Samsung KNOX Standard für verschiedene Android-Geräte melden diese den Fehler **0x87D1FDE8** oder **Fehler bei Wiederherstellung** auf der Registerkarte „Eigenschaften“ &gt; „Richtlinie“ des Geräts.

Überprüfen Sie die Konfiguration Ihres EAS-Profils für Samsung KNOX und die Quellrichtlinie. Die Samsung-Option zum Synchronisieren von Notizen wird nicht mehr unterstützt, und diese Option sollte in Ihrem Profil nicht ausgewählt werden. Achten Sie darauf, dass Geräte genug Zeit hatten, um die Richtlinie zu verarbeiten (bis zu 24 Stunden).

## <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) beschrieben an den Microsoft Support.
