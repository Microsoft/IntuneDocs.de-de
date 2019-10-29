---
title: Konformitätseinstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre iOS-Geräte in Microsoft Intune festzulegen. Sie können eine E-Mail anfordern, Geräte des Typs „mit Jailbreak“ oder „rooted“ überprüfen, das zulässige minimale und maximale Betriebssystem festlegen, Kennwortbeschränkungen einrichten, einschließlich Kennwortlänge und Geräteinaktivität, Apps einschränken und mehr.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b83b764af415349b287df2a09f9b4c355734c28
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810234"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>iOS-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für iOS-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) verwenden Sie diese Einstellungen, um Geräte des Typs „rooted“ (mit Jailbreak) als nicht konform zu markieren, eine zulässige Bedrohungsstufe festzulegen, den Ablauf von Kennwörtern einzurichten und vieles mehr.

Diese Funktion gilt für:

- iOS
- ipados

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie als **Plattform** die Option **iOS/iPadOS** aus.

## <a name="email"></a>E-Mail

- **Verwaltetes E-Mail-Profil für Mobilgeräte erforderlich:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erforderlich**: Geräte, die nicht über ein von Intune verwaltetes E-Mail-Profil verfügen, werden als nicht konform betrachtet. Ein Gerät verfügt möglicherweise nicht über ein verwaltetes E-Mail-Profil, wenn es nicht dem Ziel zugewiesen ist oder wenn der Benutzer das E-Mail-Konto auf dem Gerät manuell eingerichtet hat.

  Das Gerät wird in den folgenden Situationen als nicht kompatibel betrachtet:  
  - Das E-Mail-Profil ist einer anderen Benutzergruppe zugewiesen als der Benutzergruppe, die der Kompatibilitätsrichtlinie unterliegt.
  - Der Benutzer hat bereits ein E-Mail-Konto auf dem Gerät eingerichtet, das dem Intune-E-Mail-Profil entspricht, das auf dem Gerät bereitgestellt wurde. Intune kann das vom Benutzer konfigurierte Profil nicht überschreiben und es nicht verwalten. Zum Sicherstellen der Kompatibilität muss der Endbenutzer die vorhandenen E-Mail-Einstellungen entfernen. Anschließend kann Intune das verwaltete E-Mail-Profil installieren.  

Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren des Zugriffs auf Organisations-E-Mail mithilfe von E-Mail-Profilen in Microsoft Intune](../configuration/email-settings-configure.md).

## <a name="device-health"></a>Geräteintegrität

- **Geräte mit Jailbreak:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Blockieren**: Geräte mit Jailbreak oder entfernten Nutzungsbeschränkungen werden als nicht konform gekennzeichnet.  

- **Gerät darf höchstens die Gerätebedrohungsstufe aufweisen** *(iOS 8.0 und höher)* :  
  Verwenden Sie diese Einstellung, um die Risikobewertung als Konformitäts Bedingung zu verwenden. Wählen Sie die zulässige Bedrohungsstufe aus:  
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als konform bewertet, wenn nur Bedrohungen auf niedrigen Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als konform bewertet, wenn auf dem Gerät Bedrohungen auf niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

## <a name="device-properties"></a>Geräteeigenschaften

### <a name="operating-system-version"></a>Version des Betriebssystems  

- **Minimal Erforderliches Betriebssystem** *(IOS 8,0 und höher)* :  
  Wenn ein Gerät die Anforderung an die Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren. Danach kann er auf Organisationsressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion** *(IOS 8,0 und höher)* :  
  Wird auf einem Gerät eine neuere Betriebssystemversion als in der Regel verwendet, wird der Zugriff auf Organisationsressourcen gesperrt. Der Endbenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Mindestversion des Betriebssystem Builds** *(IOS 8,0 und höher)* :  
  Wenn Apple Sicherheitsupdates veröffentlicht, wird in der Regel die Nummer des Builds aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige minimale Buildnummer am Gerät einzugeben.

- **Maximale Version des Betriebs systembuilds** *(IOS 8,0 und höher)* :  
  Wenn Apple Sicherheitsupdates veröffentlicht, wird in der Regel die Nummer des Builds aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige maximale Buildnummer am Gerät einzugeben.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

> [!NOTE]
> Nachdem eine Konformitäts- oder Konfigurationsrichtlinie auf ein iOS-Gerät angewendet wurde, werden Benutzer alle 15 Minuten dazu aufgefordert, eine Kennung festzulegen. Benutzer erhalten kontinuierlich eine Aufforderung, bis sie eine Kennung festgelegt haben. Wenn eine Kennung für das IOS-Gerät festgelegt ist, wird der Verschlüsselungs Vorgang automatisch gestartet. Das Gerät bleibt verschlüsselt, bis die Kennung deaktiviert ist.

- **Anfordern eines Kennworts zum Entsperren mobiler Geräte:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.  
  - **Erforderlich**: Benutzer müssen ein Kennwort eingeben, bevor sie auf ihr Gerät zugreifen können. iOS-Geräte mit Kennwort sind verschlüsselt.

- **Einfache Kennwörter:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Benutzer können einfache Kenn Wörter wie **1234** oder **1111**erstellen.
  - **Blockieren**: Benutzer können kein einfaches Kennwort wie **1234** oder **1111** erstellen. 

- **Minimale Kennwortlänge:**  
  Geben Sie die Mindestanzahl an Ziffern oder Zeichen ein, die das Kennwort enthalten muss.  

- **Erforderlicher Kennworttyp:**  
  Wählen Sie aus, ob ein Kennwort nur aus **numerischen** Zeichen bestehen oder eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).

- **Anzahl nicht alphanumerischer Zeichen im Kennwort:**  
  Geben Sie die Mindestanzahl von Sonderzeichen (`&`, `#`, `%`, `!` usw.) ein, die im Kennwort enthalten sein müssen. 

  Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts** *(iOS 8.0 und höher)* :  
  Geben Sie an, wie schnell der Bildschirm gesperrt ist, bevor ein Benutzer ein Kennwort eingeben muss, um auf das Gerät zuzugreifen. Zu den Optionen gehören der Standardwert *nicht konfiguriert*, *sofort*und *1 Minute* bis *4 Stunden*.

- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:**  
  Geben Sie die Leerlaufzeit ein, bevor das Gerät seinen Bildschirm sperrt. Zu den Optionen gehören standardmäßig *nicht konfiguriert*, *sofort*und *1 Minute* bis *15 Minuten*.

- **Kennwortablauf (Tage):**  
  Wählen Sie die Anzahl der Tage aus, nach der das Kennwort abläuft und ein neues erstellt werden muss. 

- **Anzahl vorheriger Kennwörter, deren Wiederverwendung verhindert wird** *(iOS 8.0 und höher)* :   
  Geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden können.

### <a name="device-security"></a>Gerätesicherheit

- **Eingeschränkte Apps**:  
  Sie können Apps einschränken, indem Sie ihre Bündel-IDs der Richtlinie hinzufügen. Wenn die App auf einem Gerät installiert wird, wird das Gerät als nicht konform gekennzeichnet.

  - **App-Name**: Geben Sie einen benutzerfreundlichen Namen ein, damit Sie die Bündel-ID einfacher identifizieren können.
  - **App-Bündel-ID**: Geben Sie die eindeutige Bündel-ID ein, die vom App-Anbieter zugewiesen wurde. Informationen zum Ermitteln der Bündel-ID finden Sie unter [How to find the bundle ID for an iOS app (Ermitteln der Bündel-ID für eine iOS-App)](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (öffnet eine andere Microsoft-Website).  

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für macOS](compliance-policy-create-mac-os.md)-Geräte.
