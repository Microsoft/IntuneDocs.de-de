---
title: Einstellungen für Konformitätsrichtlinien für iOS-Geräte
description: Dieses Thema beschreibt die Regeln und Einstellungen, die Sie in einer Konformitätsrichtlinie für iOS-Geräte festlegen können.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 58af24f4c3ed7a650323dab0072d4e5a85f5554c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="compliance-policy-settings-for-ios-devices-in-microsoft-intune"></a>Einstellungen für Kompatibilitätsrichtlinien für iOS-Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Die in diesem Thema beschriebenen Richtlinieneinstellungen gelten für Geräte mit iOS 8.0 und höher.

Wenn Sie Informationen zu anderen Plattformen suchen, wählen Sie eine der folgenden Optionen:
> [!div class="op_single_selector"]
> - [Einstellungen für Kompatibilitätsrichtlinien für Android-Geräte](android-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für Windows-Geräte](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit
### <a name="password"></a>Kennwort
- **Kennwort zum Entsperren mobiler Geräte erforderlich**: Legen Sie für diese Einstellung **Ja** fest, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können. iOS-Geräte mit Kennwort sind verschlüsselt.

- **Einfache Kennwörter zulassen**: Legen Sie für diese Einstellung **Ja** fest, damit Benutzer einfache Kennwörter wie **1234** oder **1111** erstellen können.

-  **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.

- **Erforderlicher Kennworttyp**: Geben Sie an, ob der Benutzer ein **alphanumerisches** oder ein **numerisches** Kennwort erstellen muss.

- **Minimale Anzahl von Zeichensätzen**: Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl von Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
  -   Kleinbuchstaben
  -   Großbuchstaben
  -   Symbole
  -   Zahlen

  Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

  Bei iOS-Geräten bezieht sich diese Einstellung auf die Anzahl von Sonderzeichen (z. B. **!**, **#**, **&amp;**), die im Kennwort enthalten sein müssen.

- **Minuten Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Benutzers abläuft und er ein neues erstellen muss.

- **Kennwortverlauf speichern**: Verwenden Sie diese Einstellung in Verbindung mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.

- **Wiederverwendung vorheriger Kennwörter verhindern:** Wenn Sie **Kennwortverlauf speichern** aktiviert haben, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.

- **Kennworteingabe verlangen, wenn das Gerät aus dem Leerlauf zurückkehrt**: Verwenden Sie diese Einstellung zusammen mit der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts**. Der Benutzer wird zur Eingabe eines Kennworts aufgefordert, um auf ein Gerät zugreifen zu können, das für die in der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** angegebene Zeit inaktiv war.

### <a name="email-profile"></a>E-Mail-Profil
- **E-Mail-Konto muss von Intune verwaltet werden**: Wenn diese Option auf **Ja** festgelegt ist, muss das Gerät das auf dem Gerät bereitgestellte E-Mail-Profil verwenden. Das Gerät wird in den folgenden Situationen als nicht kompatibel betrachtet:
  - Das E-Mail-Profil wird für eine andere Benutzergruppe bereitgestellt als die Benutzergruppe, auf die die Kompatibilitätsrichtlinie ausgerichtet ist.
  - Der Benutzer hat bereits ein E-Mail-Konto auf dem Gerät eingerichtet, das dem Intune-E-Mail-Profil entspricht, das auf dem Gerät bereitgestellt wurde. Intune kann das vom Benutzer bereitgestellte Profil nicht überschreiben und daher nicht verwalten. Zum Sicherstellen der Kompatibilität muss der Benutzer die vorhandenen E-Mail-Einstellungen entfernen. Anschließend kann Intune das verwaltete E-Mail-Profil installieren.

- **Wählen Sie das E-Mail-Profil aus, das von Intune verwaltet werden muss**: Wenn die Einstellung **E-Mail-Konto muss von Intune verwaltet werden** aktiviert ist, wählen Sie **Auswählen** aus, um das Intune-E-Mail-Profil anzugeben. Das E-Mail-Profil muss auf dem Gerät vorhanden sein.

     Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren des Zugriffs auf Unternehmens-E-Mail mithilfe von E-Mail-Profilen in Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="device-health-settings"></a>Einstellungen für die Geräteintegrität

- **Gerät darf keinen Jailbreak oder Rootzugriff verwenden**: Wenn Sie diese Einstellung aktivieren, sind Geräte mit Jailbreak nicht kompatibel.

##  <a name="device-properties"></a>Geräteeigenschaften
- **Minimal erforderliches Betriebssystem**: Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht kompatibel gemeldet.
Ein Link mit Informationen zum Upgradevorgang wird angezeigt. Der Benutzer kann sein Gerät aktualisieren. Danach kann er auf Unternehmensressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.
