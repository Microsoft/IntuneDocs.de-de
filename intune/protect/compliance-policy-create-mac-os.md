---
title: Konformitätseinstellungen für macOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre macOS-Geräte in Microsoft Intune festzulegen. Sie können den Systemintegritätsschutz von Apple in Anspruch nehmen, Kennwortbeschränkungen festlegen, eine Firewall anfordern, Gatekeeper zulassen und vieles mehr.
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
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813505"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>macOS-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für macOS-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) können Sie mit diesen Einstellungen eine minimale oder maximale Betriebssystemversion festlegen, ein Ablaufdatum für Kennwörter festlegen und vieles mehr.

Diese Funktion gilt für:

- macOS

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie als **Plattform** die Option **macOS** aus.

## <a name="device-health"></a>Geräteintegrität

- **System Integritätsschutz erforderlich**:  
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erfordert** , dass macOS-Geräte den [System Integritätsschutz](https://support.apple.com/HT204899) (öffnet die Apple-Website) aktiviert haben.  

## <a name="device-properties"></a>Geräteeigenschaften

- **Minimal erforderliche Betriebssystemversion:**  
  Wenn ein Gerät die Anforderung an die Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Gerätebenutzer kann sein Gerät aktualisieren. Danach kann er auf Organisationsressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion:**  
  Wird auf einem Gerät eine neuere Betriebssystemversion als in der Regel verwendet, wird der Zugriff auf Organisationsressourcen gesperrt. Der Gerätebenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Niedrigste Buildversion des Betriebssystems:**  
  Wenn Apple Sicherheitsupdates veröffentlicht, wird in der Regel die Nummer des Builds aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige minimale Buildnummer am Gerät einzugeben.

- **Höchste Buildversion des Betriebssystems:**  
  Wenn Apple Sicherheitsupdates veröffentlicht, wird in der Regel die Nummer des Builds aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige maximale Buildnummer am Gerät einzugeben.

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Anfordern eines Kennworts zum Entsperren mobiler Geräte:**  
  - **Nicht konfiguriert** (*Standardeinstellung*)
  - **Erforderlich**: Benutzer müssen ein Kennwort eingeben, bevor sie auf ihr Gerät zugreifen können.

- **Einfache Kennwörter:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Benutzer können Kenn Wörter erstellen, die einfach sind, z.b. **1234** oder **1111**.
  - **Blockieren**: Benutzer können kein einfaches Kennwort wie **1234** oder **1111** erstellen.

- **Minimale Kennwortlänge:**  
  Geben Sie die Mindestanzahl an Ziffern oder Zeichen ein, die das Kennwort enthalten muss.

- **Kennworttyp**: Wählen Sie diese Option, wenn ein Kennwort nur aus **numerischen** Zeichen bestehen soll, oder wenn eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).

- **Anzahl nicht alphanumerischer Zeichen im Kennwort:**  
  Geben Sie die Mindestanzahl von Sonderzeichen (`&`, `#`, `%`, `!` usw.) ein, die im Kennwort enthalten sein müssen.

  Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Minuten der Inaktivität vor Anforderung des Kennworts:**  
  Geben Sie die Leerlaufzeit ein, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):**  
  Wählen Sie die Anzahl der Tage aus, nach der das Kennwort abläuft und ein neues erstellt werden muss.

- **Anzahl vorheriger Kennwörter zum Verhindern der Wiederverwendung:**  
  Geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden können.
> [!IMPORTANT]
> Wenn die Kennwortanforderung auf einem macOS-Gerät geändert wird, werden die Änderungen erst wirksam, wenn der Benutzer sein Kennwort ändert. Wenn Sie beispielsweise die Längeneinschränkung des Kennworts auf acht Ziffern festlegen, und das macOS-Gerät derzeit ein Kennwort mit sechs Ziffern besitzt, bleibt das Gerät kompatibel, bis der Benutzer das nächste Mal das Kennwort auf dem Gerät ändert.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**:  
  - **Nicht konfiguriert** (*Standardeinstellung*)
  - **Erforderlich**: Verwenden Sie diese Einstellung, um die Datenspeicher auf Ihren Geräten zu verschlüsseln.

### <a name="device-security"></a>Gerätesicherheit

Die Firewall schützt Geräte vor nicht autorisierten Netzwerkzugriffen. Mit dieser können Sie Verbindungen für einzelne Anwendungen konfigurieren. 

- **Firewall:**  
  - **Nicht Konfiguriert** (*Standardeinstellung*): Bei dieser Einstellung bleibt die Firewall deaktiviert, und Netzwerkdatenverkehr wird zugelassen (also nicht blockiert).
  - **Aktivieren**: Verwenden Sie *Aktivieren*, um Geräte vor nicht autorisierten Zugriffen zu schützen. Wenn Sie dieses Feature aktivieren, können Sie eingehende Internetverbindungen verarbeiten und den geschützten Modus verwenden. 

- **Eingehende Verbindungen:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Eingehende Verbindungen und Freigabedienste werden zugelassen.
  - **Blockieren**: Blockieren Sie alle eingehenden Netzwerkverbindungen außer denjenigen, die für grundlegende Internetdienste erforderlich sind, z.B. DHCP, Bonjour und IPSec. Durch diese Einstellung werden auch alle Freigabedienste einschließlich der Bildschirmfreigabe, des Remotezugriffs und der Freigabe von Musik über iTunes gesperrt.  

- **Geschützter Modus:**  
  - **Nicht konfiguriert** (*Standard*): bei dieser Einstellung bleibt der Debugmodus deaktiviert.
  - **Aktivieren**: Aktivieren Sie dem geschützten Modus, damit das Gerät nicht auf Suchanforderungen von böswilligen Benutzern reagiert. Wenn diese Einstellung aktiviert ist, antwortet das Gerät weiterhin auf eingehende Anforderungen für autorisierte Apps.  

### <a name="gatekeeper"></a>Gatekeeper

Weitere Informationen finden Sie unter [Gatekeeper unter MacOS](https://support.apple.com/HT202491) (öffnet die Website von Apple).

**Apps aus den folgenden Downloadquellen zulassen:** ermöglicht die Installation unterstützter Anwendungen, die von anderen Downloadquellen stammen, auf Ihren Geräten. Die folgenden Optionen sind verfügbar:

- **Nicht konfiguriert** (*Standard*): die Gatekeeper-Option hat keine Auswirkung auf die Konformität oder Nichtkonformität.  
- **Mac App Store**: Nur Apps aus dem Mac App Store können installiert werden. Apps, die von Drittanbietern oder festgelegten Entwicklern stammen, können nicht installiert werden. Wenn ein Benutzer auswählt, dass Gatekeeper Apps installiert, die nicht aus dem Mac App Store stammen, erfüllt das Gerät nicht die Konformitätsvorgaben.
- **Mac App Store und festgelegte Entwickler:** installiert Apps aus dem Mac App Store und von festgelegten Entwicklern. macOS überprüft die Identität von Entwicklern und nimmt einige andere Überprüfungen vor, um die Integrität der App zu bestimmen. Wenn ein Benutzer auswählt, dass Gatekeeper Apps installiert, die nicht diesen Optionen entsprechen, erfüllt das Gerät nicht die Konformitätsvorgaben.
- **Beliebig**: Apps aus jeder beliebigen Quelle und von jedem beliebigen Entwickler können installiert werden. Dies ist die am wenigsten sichere Option.
 

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für iOS](compliance-policy-create-ios.md)-Geräte.