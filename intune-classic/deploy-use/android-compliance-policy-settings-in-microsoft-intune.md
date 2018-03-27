---
title: Einstellungen für Kompatibilitätsrichtlinien für Android
description: In diesem Thema werden die Gerätekompatibilitätsrichtlinien für Android-Geräte beschrieben.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 63618f9af5f2bdb863a19c229c862e446dd4ea7a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="compliance-policy-settings-for-android-devices-in-microsoft-intune"></a>Einstellungen für Kompatibilitätsrichtlinien für Android-Geräte in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Die in diesem Thema beschriebenen Richtlinieneinstellungen gelten für Geräte mit Android 4.0 und höher oder Samsung KNOX 4.0 und höher.

Wenn Sie Informationen zu anderen Plattformen suchen, wählen Sie eine der folgenden Optionen:
> [!div class="op_single_selector"]
- [Einstellungen für Kompatibilitätsrichtlinien für iOS-Geräte](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Einstellungen für Kompatibilitätsrichtlinien für Windows-Geräte](windows-compliance-policy-settings-in-microsoft-intune.md)
- [Einstellungen für Konformitätsrichtlinien für Android for Work-Geräte](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit
### <a name="password"></a>Kennwort
- **Kennwort zum Entsperren mobiler Geräte erforderlich:** Legen Sie für diese Einstellung **Ja** fest, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.

-  **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.

- **Kennwortstärke:** Mit dieser Einstellung wird erkannt, ob die von Ihnen angegebenen Kennwortanforderungen auf dem Gerät eingerichtet wurden. Aktivieren Sie diese Einstellung, um festzulegen, dass Benutzer für Android-Geräte bestimmte Kennwortanforderungen erfüllen müssen. Es stehen die folgenden Optionen zur Auswahl:

  -   **Biometrie auf niedriger Sicherheitsstufe**
  -   **Erforderlich**
  -   **Mindestens numerisch**
  -   **Mindestens alphabetisch**
  -   **Mindestens alphanumerisch**
  -   **Alphanumerisch mit Symbolen**

- **Minuten Inaktivität vor erneuter Anforderung des Kennworts**: Gibt die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Benutzers abläuft und er ein neues erstellen muss.

- **Kennwortverlauf speichern:** Verwenden Sie diese Einstellung zusammen mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.

- **Wiederverwendung vorheriger Kennwörter verhindern:** Wenn **Kennwortverlauf speichern** aktiviert ist, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.

- **Kennworteingabe verlangen, wenn das Gerät aus dem Leerlaufbetrieb zurückkehrt:** Verwenden Sie diese Einstellung zusammen mit der Einstellung **Minuten der Inaktivität vor erneuter Anforderung des Kennworts**. Die Benutzer werden zur Eingabe eines Kennworts aufgefordert, um auf ein Gerät zugreifen zu können, das für die in der Einstellung **Minuten der Inaktivität vor erneuter Anforderung des Kennworts** angegebene Zeit inaktiv war.

### <a name="encryption"></a>Verschlüsselung
- **Verschlüsselung auf mobilen Geräten vorschreiben:** Legen Sie diese Einstellung auf **Ja** fest, damit Geräte verschlüsselt werden müssen, um eine Verbindung mit Ressourcen herzustellen. Wenn Sie die Einstellung **Kennwort zum Entsperren mobiler Geräte erforderlich** konfigurieren, werden Geräte verschlüsselt.

## <a name="device-health-and-security-settings"></a>Einstellungen für Geräteintegrität und Sicherheit

- **Gerät darf keinen Jailbreak oder Rootzugriff verwenden:** Wenn Sie diese Einstellung aktivieren, werden Geräte mit Jailbreak als nicht kompatibel eingestuft.
- **Installation von Apps aus unbekannten Quellen muss auf Geräten gesperrt sein (Android 4.0 und höher)**: Um Geräte zu blockieren, bei denen die Option **Sicherheit > Unbekannte Quellen** aktiviert ist, aktivieren Sie diese Einstellung, und legen Sie sie auf **Ja** fest.  

>[!IMPORTANT]
>Das Sideloading von Anwendungen erfordert, dass die Einstellung **Unbekannte Quellen** aktiviert ist. Erzwingen Sie diese Kompatibilitätsrichtlinie nur, wenn Sie kein Sideloading von Android-Apps auf Geräten durchführen.

- **USB-Debuggen muss deaktiviert sein (Android 4.2 und höher)**: Gibt an, ob ermittelt werden soll, ob die Option für USB-Debuggen auf dem Gerät aktiviert ist.
- **Aktivierung von "Gerät auf Sicherheitsbedrohungen überprüfen" auf Geräten erforderlich (Android 4.2–4.4)**: Gibt an, dass die Funktion **Apps überprüfen** auf dem Gerät aktiviert ist.
- **Niedrigste zulässige Android-Sicherheitspatchebene (Android 6.0 und höher)**: Geben Sie die niedrigste Android-Patchebene an.  Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht kompatibel. Das Datum muss im folgenden Format angegeben werden: JJJJ-MM-TT.
- **Schutz vor Gerätebedrohungen muss aktiviert sein**: Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lookout MTP-Lösung als Kompatibilitätsvoraussetzung zu fordern. Wählen Sie aus den folgenden Optionen die maximal zulässige Bedrohungsstufe aus:

  - **Keine (geschützt)**: Dies ist die sicherste Einstellung. Dies bedeutet, dass das Gerät keinerlei Bedrohungen unterliegen darf. Wenn auf dem Gerät Bedrohungen erkannt werden, wird es als nicht kompatibel bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen auf niedrigen Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel:** Das Gerät wird als kompatibel bewertet, wenn auf dem Gerät Bedrohungen auf niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen auf hoher Stufe erkannt werden, wird es als nicht kompatibel bewertet.
  - **Hoch**: Dies ist die unsicherste Einstellung. Mit dieser Einstellung werden grundsätzlich alle Bedrohungsstufen zugelassen. Sie ist daher üblicherweise nur für Berichtszwecke sinnvoll.

  Weitere Informationen finden Sie unter [Erstellen einer Lookout-Kompatibilitätsrichtlinie in Intune](create-lookout-device-compliance-policy.md).

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimal erforderliches Betriebssystem:** Wenn ein Gerät die Anforderungen für die minimal erforderliche Betriebssystemversion nicht erfüllt, wird es als nicht kompatibel gemeldet.
  Ein Link zum Durchführen von Upgrades wird angezeigt. Der Benutzer kann ein Upgrade des Geräts durchführen und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.
