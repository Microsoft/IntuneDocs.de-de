---
title: Konformitätseinstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre iOS-Geräte in Microsoft Intune festzulegen. Sie können eine E-Mail anfordern, Geräte des Typs „mit Jailbreak“ oder „rooted“ überprüfen, das zulässige minimale und maximale Betriebssystem festlegen, Kennwortbeschränkungen einrichten, einschließlich Kennwortlänge und Geräteinaktivität, Apps einschränken und mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ec071622a2e0d49068864f8bfb47954f54c8ba4
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423610"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>iOS-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für iOS-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) verwenden Sie diese Einstellungen, um Geräte des Typs „rooted“ (mit Jailbreak) als nicht konform zu markieren, eine zulässige Bedrohungsstufe festzulegen, den Ablauf von Kennwörtern einzurichten und vieles mehr.

Diese Funktion gilt für:

- iOS

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie als **Plattform** die Option **iOS** aus.

## <a name="email"></a>E-Mail

- **Verwaltetes E-Mail-Profil für Mobilgeräte erforderlich**: Bei Festlegen auf **Anfordern** werden Geräte, die nicht über ein von Intune verwaltetes E-Mail-Profil verfügen, als nicht konform betrachtet. Ein Gerät verfügt möglicherweise nicht über ein verwaltetes E-Mail-Profil, wenn es nicht dem Ziel zugewiesen ist oder wenn der Benutzer das E-Mail-Konto auf dem Gerät manuell eingerichtet hat. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Das Gerät wird in den folgenden Situationen als nicht kompatibel betrachtet:

  - Das E-Mail-Profil ist einer anderen Benutzergruppe zugewiesen als der Benutzergruppe, die der Kompatibilitätsrichtlinie unterliegt.
  - Der Benutzer hat bereits ein E-Mail-Konto auf dem Gerät eingerichtet, das dem Intune-E-Mail-Profil entspricht, das auf dem Gerät bereitgestellt wurde. Intune kann das vom Benutzer konfigurierte Profil nicht überschreiben und es nicht verwalten. Zum Sicherstellen der Kompatibilität muss der Endbenutzer die vorhandenen E-Mail-Einstellungen entfernen. Anschließend kann Intune das verwaltete E-Mail-Profil installieren.

- **Wählen Sie das E-Mail-Profil aus, das von Intune verwaltet werden muss:** Wenn die Einstellung **E-Mail-Konto muss von Intune verwaltet werden** aktiviert ist, wählen Sie **Auswählen** aus, um das Intune-E-Mail-Profil einzugeben. Das E-Mail-Profil muss auf dem Gerät vorhanden sein.

Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren des Zugriffs auf Organisations-E-Mail mithilfe von E-Mail-Profilen in Microsoft Intune](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Geräte mit Jailbreak**: Klicken Sie auf **Blockieren**, um Geräte des Typs „rooted“ (mit Jailbreak) als nicht konform zu kennzeichnen. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht** (iOS 8.0 und neuer): Verwenden Sie diese Einstellung, um die Risikobewertung als Konformitätsvoraussetzung zu fordern. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. Wählen Sie die zulässige Bedrohungsstufe aus, um diese Einstellung zu verwenden:
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

## <a name="device-properties"></a>Geräteeigenschaften

- **Minimal erforderliches Betriebssystem** (iOS 8.0 und neuer): Wenn ein Gerät die Anforderungen für die minimal erforderliche Betriebssystemversion nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren. Danach kann er auf Organisationsressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion** (iOS 8.0 und neuer): Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Organisationsressourcen gesperrt. Der Endbenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.
- **Mindestbuildversion des Betriebssystems** (iOS 8.0 und neuer): Wenn Apple Sicherheitsupdates veröffentlicht, wird die Nummer des Builds in der Regel aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige minimale Buildnummer am Gerät einzugeben.
- **Höchste Buildversion des Betriebssystems** (iOS 8.0 und neuer): Wenn Apple Sicherheitsupdates veröffentlicht, wird die Nummer des Builds in der Regel aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige maximale Buildnummer am Gerät einzugeben.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

> [!NOTE]
> Nachdem eine Konformitäts- oder Konfigurationsrichtlinie auf ein iOS-Gerät angewendet wurde, werden Benutzer alle 15 Minuten dazu aufgefordert, eine Kennung festzulegen. Benutzer erhalten kontinuierlich eine Aufforderung, bis sie eine Kennung festgelegt haben.

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können. iOS-Geräte mit Kennwort sind verschlüsselt.
- **Einfache Kennwörter:** Legen Sie **Blockieren** fest, damit Benutzer kein einfaches Kennwort wie **1234** oder **1111** erstellen können. Wenn Sie diese Option auf **Nicht konfiguriert** setzen, können Benutzer Kennwörter wie **1234** oder **1111** erstellen.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Kennwort enthalten muss.
- **Erforderlicher Kennworttyp**: Wählen Sie diese Option, wenn ein Kennwort nur aus **numerischen** Zeichen bestehen soll, oder wenn eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).
- **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die Mindestanzahl von Sonderzeichen (`&`, `#`, `%`, `!` usw.) an, die im Kennwort enthalten sein müssen.

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl der bereits verwendeten Kennwörtern an, die nicht erneut verwendet werden dürfen.

### <a name="device-security"></a>Gerätesicherheit

- **Eingeschränkte Apps**: Sie können Apps einschränken, indem Sie ihre Bündel-IDs der Richtlinie hinzufügen. Wenn die App auf einem Gerät installiert wird, wird das Gerät als nicht konform gekennzeichnet.

  - **App-Name:** Geben Sie einen benutzerfreundlichen Namen ein, damit Sie die Bündel-ID einfacher identifizieren können.
  - **App-Bündel-ID:** Geben Sie die eindeutige Bündel-ID ein, die vom App-Anbieter zugewiesen wurde. Informationen zum Ermitteln der Bündel-ID finden Sie unter [How to find the bundle ID for an iOS app (Ermitteln der Bündel-ID für eine iOS-App)](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (öffnet eine andere Microsoft-Website).  

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für macOS](compliance-policy-create-mac-os.md)-Geräte.
