---
title: Erstellen einer Konformitätsrichtlinie für macOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen oder konfigurieren Sie eine Microsoft Intune-Gerätekonformitätsrichtlinie für MacOS-Geräte, um Systemintegritätsschutz zu verwenden, legen Sie die minimale und maximale Betriebssystemversion fest, wählen Sie Ihre Kennwortanforderungen, und verschlüsseln Sie die Datenspeicherung.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 583a64b5dd91df2ef9e5acbaf129b447aca7f2d9
ms.sourcegitcommit: b93db06ba435555f5b126f97890931484372fcfb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52828993"
---
# <a name="add-a-device-compliance-policy-for-macos-devices-with-intune"></a>Hinzufügen einer Gerätekonformitätsrichtlinie für macOS-Geräte in Intune

Eine Intune-Konformitätsrichtlinie für macOS-Geräte gibt die Regeln und Einstellungen an, die macOS-Geräte erfüllen müssen, um konform zu sein. Wenn Sie Richtlinien für den bedingten Zugriff verwenden, können Sie den Zugriff auf Unternehmensressourcen zulassen oder blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen. Gerätekonformitätsrichtlinien können für sämtliche Plattformen im Intune Azure-Portal erstellt werden. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird:

---------------------------

| Richtlinieneinstellung | macOS 10.11 und höher |
| --- | --- |
| **PIN- oder Kennwortkonfiguration** | Wiederhergestellt |   
| **Geräteverschlüsselung** | Wiederhergestellt (durch Festlegen der PIN) |
| **E-Mail-Profil** | Isoliert |
|**Minimale Version des Betriebssystems** | Isoliert |
| **Maximale Version des Betriebssystems** | Isoliert |

---------------------------

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Das Gerät wird blockiert, wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt.
- Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Wählen Sie als **Plattform** die Option **macOS** aus. 
5. Wählen Sie **Einstellungen konfigurieren**, um die in diesem Artikel beschriebenen Einstellungen zu **Geräteintegrität**, **Geräteeigenschaften** und **Systemsicherheit** anzugeben. Wenn Sie fertig sind, wählen Sie **OK** und dann **Erstellen**.

## <a name="device-health"></a>Geräteintegrität

- **Ein Systemintegritätsschutz ist erforderlich**: Legen Sie dies auf **Erforderlich** fest, um zu überprüfen, ob Ihre macOS-Geräte den [Systemintegritätsschutz](https://support.apple.com/HT204899) aktiviert haben.

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
- **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die Mindestanzahl von Sonderzeichen (&, #, %, !, usw.) an, die im Kennwort enthalten sein müssen.

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen.

    > [!IMPORTANT]
    > Wenn die Kennwortanforderung auf einem macOS-Gerät geändert wird, werden die Änderungen erst wirksam, wenn der Benutzer sein Kennwort ändert. Wenn Sie beispielsweise die Längeneinschränkung des Kennworts auf acht Ziffern festlegen, und das macOS-Gerät derzeit ein Kennwort mit sechs Ziffern besitzt, bleibt das Gerät kompatibel, bis der Benutzer das nächste Mal das Kennwort auf dem Gerät ändert.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln.

### <a name="device-security"></a>Gerätesicherheit
Die Firewall schützt Geräte vor nicht autorisierten Netzwerkzugriffen. Mit dieser können Sie Verbindungen für einzelne Anwendungen konfigurieren. 

- **Firewall**: **Aktivieren** Sie diese, um Geräte vor nicht autorisierten Zugriffen zu schützen. Wenn Sie dieses Feature aktivieren, können Sie eingehende Internetverbindungen verarbeiten und den geschützten Modus verwenden. Durch die Standardeinstellung **Nicht konfiguriert** bleibt die Firewall deaktiviert, und Netzwerkdatenverkehr wird zugelassen (also nicht blockiert).
- **Eingehende Verbindungen**: Mit der Einstellung **Blockieren** werden eingehende Verbindungen für grundlegende Internetdienste wie DHCP, Bonjour und IPSec zugelassen. Alle anderen eingehenden Verbindungen werden gesperrt. Durch diese Einstellung werden auch alle Freigabedienste einschließlich der Bildschirmfreigabe, des Remotezugriffs und der Freigabe von Musik über iTunes gesperrt. Durch die Standardeinstellung **Nicht konfiguriert** werden eingehende Verbindungen und Freigabedienste zugelassen. 
- **Geschützter Modus**: **Aktivieren** Sie diesen, damit das Gerät nicht auf Suchanforderungen von böswilligen Benutzern reagiert. Wenn diese Einstellung aktiviert ist, antwortet das Gerät weiterhin auf eingehende Anforderungen für autorisierte Apps. Wenn die Standardeinstellung **Nicht konfiguriert** aktiviert ist, bleibt der geschützte Modus deaktiviert.

### <a name="gatekeeper"></a>Gatekeeper

**Apps aus den folgenden Downloadquellen zulassen:** ermöglicht die Installation unterstützter Anwendungen, die von anderen Downloadquellen stammen, auf Ihren Geräten. Die folgenden Optionen sind verfügbar:

- **Nicht konfiguriert:** Standard. Die Gatekeeper-Option hat keine Auswirkungen auf die Konformität. 
- **Mac App Store:** installiert nur Apps aus dem Mac App Store. Apps, die von Drittanbietern oder festgelegten Entwicklern stammen, können nicht installiert werden. Wenn ein Benutzer auswählt, dass Gatekeeper Apps installiert, die nicht aus dem Mac App Store stammen, erfüllt das Gerät nicht die Konformitätsvorgaben.
- **Mac App Store und festgelegte Entwickler:** installiert Apps aus dem Mac App Store und von festgelegten Entwicklern. macOS überprüft die Identität von Entwicklern und nimmt einige andere Überprüfungen vor, um die Integrität der App zu bestimmen. Wenn ein Benutzer auswählt, dass Gatekeeper Apps installiert, die nicht diesen Optionen entsprechen, erfüllt das Gerät nicht die Konformitätsvorgaben.
- **Anywhere** (Beliebig): Apps aus jeder beliebigen Quelle und von jedem beliebigen Entwickler können installiert werden. Dies ist die am wenigsten sichere Option.

Weitere Informationen finden Sie in der Apple-Dokumentation unter [Gatekeeper on macOS (Gatekeeper unter macOS)](https://support.apple.com/HT202491).

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

1. Wählen Sie eine Richtlinie, die Sie konfiguriert haben. Vorhandene Richtlinien befinden sich unter **Gerätekompatibilität** > **Richtlinien**.
2. Wählen Sie die Richtlinie und dann **Zuweisungen** aus. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und dann wählen Sie **Speichern**, um die Richtlinie für die Benutzer bereitzustellen.

> [!TIP]
> Standardmäßig wird die Konformität von den Geräten alle acht Stunden geprüft. Benutzer können diesen Prozess jedoch auch über die Intune-Unternehmensportal-App erzwingen.

Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="next-steps"></a>Nächste Schritte
[Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte](actions-for-noncompliance.md)  
[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)
