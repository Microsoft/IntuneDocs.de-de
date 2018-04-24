---
title: Kompatibilitätseinstellungen für Android for Work
description: In diesem Thema werden die Gerätekompatibilitätsrichtlinien für Android-Geräte beschrieben, die mit Android for Work kompatibel sind.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 02/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 085cca57365da0df9dd739c3a1b2b0c6dd6fded6
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="compliance-policy-settings-for-android-for-work-devices-in-microsoft-intune"></a>Einstellungen für Kompatibilitätsrichtlinien für Android for Work-Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Die in diesem Thema beschriebenen Richtlinieneinstellungen gelten für Android for Work-Geräte.

Wenn Sie Informationen zu anderen Plattformen suchen, wählen Sie eine der folgenden Optionen:
> [!div class="op_single_selector"]
> - [Einstellungen für Kompatibilitätsrichtlinien für Android](android-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für iOS-Geräte](ios-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für Windows-Geräte](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit
### <a name="password"></a>Kennwort
- **Kennwort zum Entsperren mobiler Geräte erforderlich:** Legen Sie für diese Einstellung **Ja** fest, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.

-  **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.

- **Kennwortstärke:** Mit dieser Einstellung wird erkannt, ob die angegebenen Kennwortanforderungen auf dem Gerät konfiguriert wurden. Aktivieren Sie diese Einstellung, um festzulegen, dass Benutzer für Android-Geräte bestimmte Kennwortanforderungen konfigurieren müssen. Es stehen die folgenden Optionen zur Auswahl:
  -   **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  -   **Mindestens numerisch**
  -   **Mindestens alphabetisch**
  -   **Mindestens alphanumerisch**
  -   **Alphanumerisch mit Symbolen**

- **Minuten der Inaktivität, bevor ein Kennwort erforderlich ist:** Gibt die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen, bevor das Kennwort des Benutzers abläuft und er ein neues erstellen muss.

- **Kennwortverlauf speichern:** Verwenden Sie diese Einstellung in Verbindung mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.

- **Wiederverwendung vorheriger Kennwörter verhindern:** Wenn **Kennwortverlauf speichern** aktiviert ist, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.

- **Kennworteingabe verlangen, wenn das Gerät aus dem Leerlauf zurückkehrt:** Diese Einstellung sollte zusammen mit der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** verwendet werden. Die Endbenutzer werden zur Eingabe eines Kennworts aufgefordert, um auf ein Gerät zugreifen zu können, das für die in der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** angegebene Zeit inaktiv war.

### <a name="encryption"></a>Verschlüsselung
- **Verschlüsselung auf mobilen Geräten erforderlich:** Diese Einstellung muss nicht konfiguriert werden, da Android for Work-Geräte eine Verschlüsselung erzwingen.

## <a name="device-health-and-security-settings"></a>Einstellungen für Geräteintegrität und Sicherheit

- **Gerät darf nicht gehackt und kein Quellgerät sein:** Wenn Sie diese Einstellung aktivieren, werden gehackte Geräte als nicht kompatibel eingestuft.
- **Installation von Apps aus unbekannten Quellen muss auf Geräten gesperrt sein:** Diese Einstellung muss nicht konfiguriert werden, da Android for Work-Geräte die Installation von unbekannten Quellen immer einschränken. .  

- **USB-Debuggen muss deaktiviert sein**: Diese Einstellung muss nicht konfiguriert werden, da USB-Debuggen auf Android for Work-Geräten bereits deaktiviert ist.

- **Niedrigste zulässige Android-Sicherheitspatchebene**: Verwenden Sie diese Einstellung, um eine niedrigste zulässige Android-Patchebene festzulegen.  Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht kompatibel. Das Datum muss im folgenden Format angegeben werden: JJJJ-MM-TT.
- **Schutz vor Gerätebedrohungen muss aktiviert sein**: Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lösung „Schutz vor Gerätebedrohungen“ als Kompatibilitätsvoraussetzung zu fordern. Wählen Sie aus den folgenden Optionen die maximal zulässige Bedrohungsstufe aus:

  - **Keine (geschützt)**: Dies ist die sicherste Einstellung. Dies bedeutet, dass das Gerät keinerlei Bedrohungen unterliegen darf. Wenn auf dem Gerät Bedrohungen jeglicher Stufe erkannt werden, wird es als nicht kompatibel bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
  - **Hoch**: Dies ist die unsicherste Einstellung. Mit dieser Einstellung werden grundsätzlich alle Bedrohungsstufen zugelassen. Sie ist daher wahrscheinlich nur für Berichtszwecke sinnvoll.

  Weitere Informationen finden Sie unter [Erstellen einer Gerätekompatibilitätsrichtlinie](create-lookout-device-compliance-policy.md).

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften
- **Minimal erforderliches Betriebssystem**: Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht kompatibel gemeldet.
  Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Die Endbenutzer können ein Upgrade des Geräts durchführen und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.
