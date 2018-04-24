---
title: Erstellen einer Gerätekonformitätsrichtlinie
description: Erstellen Sie eine Kompatibilitätsrichtlinie, um das Sichern mobiler Geräte und PCs zu unterstützen, die zum Zugriff auf Ihre Unternehmensdaten verwendet werden.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/12/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ed6f66747364debd89661d78bcf3b002b1c8a9b6
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-device-compliance-policy-in-microsoft-intune"></a>Erstellen einer Konformitätsrichtlinie für Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Dieses Thema beschreibt die Schritte, die zum Erstellen einer Kompatibilitätsrichtlinie für ein Gerät verwendet werden können, und der ein Gerät entsprechen muss, um als kompatibel angesehen zu werden.

##  <a name="step-1-add-a-new-policy"></a>Schritt 1: Hinzufügen einer neuen Richtlinie
  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Richtlinie** &gt; **Konformitätsrichtlinien** &gt; **Hinzufügen**.

  ![Screenshot der Konformitätsrichtlinienseite in der Intune-Verwaltungskonsole mit der Option „Hinzufügen“ im Menü oben auf der Seite](./media/intune-sa-3a-add-compliance-policy.png)

##  <a name="step-2--configure-settings"></a>Schritt 2: Konfigurieren von Einstellungen
Aktivieren Sie auf der Seite **Richtlinie erstellen** die folgenden Einstellungen nach Bedarf:
  -   Die Einstellungen für die Systemsicherheit, wie Kennwort und Verschlüsselung
  -   Einstellungen für die Geräteintegrität, etwa ob ein Gerät per Jailbreak manipuliert wurde oder vom Windows-Dienst für den Nachweis der Geräteintegrität als intakt gemeldet wird
  -   Einstellungen von Geräteeigenschaften, etwa die erforderliche minimale oder die zulässige maximale Betriebssystemversion
![Registerkarte „Allgemein“ auf der Seite „Richtlinie erstellen“](./media/intune-sa-3b-create-policy.png)


##  <a name="step-3-save-the-policy"></a>Schritt 3: Speichern der Richtlinie
Wählen Sie danach die Option **Richtlinie speichern**.

Sie haben die Möglichkeit, die Richtlinie direkt nach dem Speichern bereitzustellen, oder können sich für die spätere Bereitstellung entscheiden. Die neue Richtlinie wird im Knoten **Konformitätsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt.

##  <a name="step-4-set-the-compliance-status-validity-period"></a>Schritt 4: Festlegen des Gültigkeitszeitraums des Konformitätsstatus
Um den Zeitraum anzugeben, der dem Gerät zum Einchecken zur Verfügung steht, bevor es als nicht kompatibel eingestuft wird, wechseln Sie zu den Konformitätsrichtlinieneinstellungen, und aktualisieren Sie die Zeit. Der Standard ist auf 30 Tage festgelegt.

![Option „Einstellungen für Kompatibilitätsrichtlinie“ in der Richtlinienmenüleiste](../media/mdm-compliance-policy-settings.png)

![Dialogfeld „Kompatibilitätsrichtlinie“](../media/mdm-ca-compliance-status-validity-period.png)

## <a name="supported-policy-settings"></a>Unterstützte Richtlinieneinstellungen
In der folgenden Tabelle sind die Einstellungen für die Kompatibilitätsrichtlinie und die Plattformen aufgelistet, auf denen sie unterstützt werden.

-------------

|Einstellung|iOS|Android|Windows|
|-----|----|-----|-----|
|Anfordern eines Kennworts zum Entsperren mobiler Geräte|iOS 6 und höher|Android 4,0 und höher <br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8.1 und höher|
|Einfache Kennwörter zulassen|iOS 6 und höher|Nicht unterstützt|Windows Phone 8.1 und höher|
|Minimale Kennwortlänge|iOS 6 und höher| Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher| Windows Phone 8.1 und höher<br>Windows 8.1|
|Erforderlicher Kennworttyp|iOS 6 und höher|Nicht verfügbar|Windows Phone 8.1 und höher <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Minimale Anzahl von Zeichensätzen|iOS 6 und höher|Nicht verfügbar|Windows Phone 8.1 und höher <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Kennwortqualität|Nicht verfügbar|Android 4,0 und höher <br>Samsung KNOX Standard 4.0 und höher|Nicht verfügbar|
|Minuten Inaktivität vor erneuter Anforderung des Kennworts|iOS 6 und höher|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8.1 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Kennwortablauf (Tage)|iOS 6 und höher|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8.1 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Kennwortverlauf speichern|iOS 6 und höher|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8.1 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Wiederverwendung vorheriger Kennwörter verhindern|iOS 6 und höher|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8.1 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Kennwort anfordern, wenn das Gerät aus dem Leerlauf zurückkehrt| Nicht verfügbar| Nicht verfügbar|Windows 10 Mobile|
|Verschlüsselung auf mobilem Gerät anfordern|Nicht verfügbar|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8.1 und höher<br> Windows 8.1|
|Anforderung, dass Geräte als fehlerfrei gemeldet werden| Nicht verfügbar| Nicht verfügbar|Windows <br>Windows 10 Mobile|
|Gerät darf nicht per Jailbreak oder Rooting manipuliert worden sein|iOS 6 und höher|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher|Nicht verfügbar|
|E-Mail-Konto muss von Intune verwaltet werden|iOS 6 und höher|Nicht verfügbar| Nicht verfügbar|
|Wählen Sie das E-Mail-Profil aus, das von Intune verwaltet werden muss|iOS 6 und höher|Nicht verfügbar| Nicht verfügbar|
|Minimal erforderliches Betriebssystem|iOS 6 und höher|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher| Windows Phone 8.1 und höher<br>Windows 8.1|
|Maximal zulässige Betriebssystemversion|iOS 6 und höher|Android 4,0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8.1 und höher<br>Windows 8.1|

Weitere Informationen über die Kompatibilitätseinstellungen, die auf den einzelnen Plattformen unterstützt werden, finden Sie in den folgenden Themen:
> [!div class="op_single_selector"]
> - [Einstellungen für Kompatibilitätsrichtlinien für iOS-Geräte](ios-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für Android-Geräte](android-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für Windows- und Windows Phone-Geräte](windows-compliance-policy-settings-in-microsoft-intune.md)


## <a name="next-steps"></a>Nächste Schritte
[Bereitstellen und Überwachen einer Kompatibilitätsrichtlinie](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Siehe auch
[Einführung in Richtlinien zur Gerätekompatibilität](introduction-to-device-compliance-policies-in-microsoft-intune.md)
