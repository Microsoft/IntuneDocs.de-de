---
title: Konformitätseinstellungen für macOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre macOS-Geräte in Microsoft Intune festzulegen. Sie können den Systemintegritätsschutz von Apple in Anspruch nehmen, Kennwortbeschränkungen festlegen, eine Firewall anfordern, Gatekeeper zulassen und vieles mehr.
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
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3224e7400ad56f971488aba53bb073a0d33bb9d
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423644"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>macOS-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für macOS-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) können Sie mit diesen Einstellungen eine minimale oder maximale Betriebssystemversion festlegen, ein Ablaufdatum für Kennwörter festlegen und vieles mehr.

Diese Funktion gilt für:

- macOS

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie als **Plattform** die Option **macOS** aus.

## <a name="device-health"></a>Geräteintegrität

- **Systemintegritätsschutz erforderlich**: Legen Sie dies auf **Anfordern** fest, um zu überprüfen, ob Ihre macOS-Geräte den [Systemintegritätsschutz](https://support.apple.com/HT204899) (öffnet die Website von Apple) aktiviert haben. In der Standardeinstellung **Nicht konfiguriert** wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

## <a name="device-properties"></a>Geräteeigenschaften

- **Minimale Betriebssystemversion:** Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link mit Informationen zum Upgradevorgang wird angezeigt. Der Endbenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximale Version des Betriebssystems:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.
- **Mindestbuildversion des Betriebssystems**: Wenn Apple Sicherheitsupdates veröffentlicht, wird die Nummer des Builds in der Regel aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige minimale Buildnummer am Gerät einzugeben.
- **Höchste Buildversion des Betriebssystems**: Wenn Apple Sicherheitsupdates veröffentlicht, wird die Nummer des Builds in der Regel aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige maximale Buildnummer am Gerät einzugeben.

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Einfache Kennwörter:** Legen Sie **Blockieren** fest, damit Benutzer kein einfaches Kennwort wie **1234** oder **1111** erstellen können. Wenn Sie diese Option auf **Nicht konfiguriert** setzen, können Benutzer Kennwörter wie **1234** oder **1111** erstellen.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Kennwort enthalten muss.
- **Kennworttyp**: Wählen Sie diese Option, wenn ein Kennwort nur aus **numerischen** Zeichen bestehen soll, oder wenn eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).
- **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die Mindestanzahl von Sonderzeichen (`&`, `#`, `%`, `!` usw.) an, die im Kennwort enthalten sein müssen.

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl der bereits verwendeten Kennwörtern an, die nicht erneut verwendet werden dürfen.

    > [!IMPORTANT]
    > Wenn die Kennwortanforderung auf einem macOS-Gerät geändert wird, werden die Änderungen erst wirksam, wenn der Benutzer sein Kennwort ändert. Wenn Sie beispielsweise die Längeneinschränkung des Kennworts auf acht Ziffern festlegen, und das macOS-Gerät derzeit ein Kennwort mit sechs Ziffern besitzt, bleibt das Gerät kompatibel, bis der Benutzer das nächste Mal das Kennwort auf dem Gerät ändert.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln.

### <a name="device-security"></a>Gerätesicherheit

Die Firewall schützt Geräte vor nicht autorisierten Netzwerkzugriffen. Mit dieser können Sie Verbindungen für einzelne Anwendungen konfigurieren. 

- **Firewall**: Legen Sie diese Einstellung auf **Aktivieren** fest, um Geräte vor nicht autorisierten Zugriffen zu schützen. Wenn Sie dieses Feature aktivieren, können Sie eingehende Internetverbindungen verarbeiten und den geschützten Modus verwenden. Durch die Standardeinstellung **Nicht konfiguriert** bleibt die Firewall deaktiviert, und Netzwerkdatenverkehr wird zugelassen (also nicht blockiert).
- **Eingehende Verbindungen:** **Blockieren** Sie alle eingehenden Netzwerkverbindungen außer denjenigen, die für grundlegende Internetdienste erforderlich sind, z.B. DHCP, Bonjour und IPSec. Durch diese Einstellung werden auch alle Freigabedienste einschließlich der Bildschirmfreigabe, des Remotezugriffs und der Freigabe von Musik über iTunes gesperrt. Durch die Standardeinstellung **Nicht konfiguriert** werden eingehende Verbindungen und Freigabedienste zugelassen.
- **Geschützter Modus**: **Aktivieren** Sie diese Einstellung, damit das Gerät nicht auf Suchanforderungen von böswilligen Benutzern reagiert. Wenn diese Einstellung aktiviert ist, antwortet das Gerät weiterhin auf eingehende Anforderungen für autorisierte Apps. Wenn die Standardeinstellung **Nicht konfiguriert** aktiviert ist, bleibt der geschützte Modus deaktiviert.

### <a name="gatekeeper"></a>Gatekeeper

Weitere Informationen finden Sie unter [Gatekeeper unter MacOS](https://support.apple.com/HT202491) (öffnet die Website von Apple).

**Apps aus den folgenden Downloadquellen zulassen:** ermöglicht die Installation unterstützter Anwendungen, die von anderen Downloadquellen stammen, auf Ihren Geräten. Die folgenden Optionen sind verfügbar:

- **Nicht konfiguriert:** Standard. Die Gatekeeper-Option hat keine Auswirkungen auf die Konformität. 
- **Mac App Store:** installiert nur Apps aus dem Mac App Store. Apps, die von Drittanbietern oder festgelegten Entwicklern stammen, können nicht installiert werden. Wenn ein Benutzer auswählt, dass Gatekeeper Apps installiert, die nicht aus dem Mac App Store stammen, erfüllt das Gerät nicht die Konformitätsvorgaben.
- **Mac App Store und festgelegte Entwickler:** installiert Apps aus dem Mac App Store und von festgelegten Entwicklern. macOS überprüft die Identität von Entwicklern und nimmt einige andere Überprüfungen vor, um die Integrität der App zu bestimmen. Wenn ein Benutzer auswählt, dass Gatekeeper Apps installiert, die nicht diesen Optionen entsprechen, erfüllt das Gerät nicht die Konformitätsvorgaben.
- **Anywhere** (Beliebig): Apps aus jeder beliebigen Quelle und von jedem beliebigen Entwickler können installiert werden. Dies ist die am wenigsten sichere Option.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für iOS](compliance-policy-create-ios.md)-Geräte.