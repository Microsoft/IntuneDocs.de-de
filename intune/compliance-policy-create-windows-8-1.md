---
title: Windows 8.1-Education-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Eine Liste mit allen Einstellungen, mit denen Sie beim Festlegen von Kompatibilität mit Ihrer Windows 8.1 und Windows Phone 8.1-Geräte in Microsoft Intune angezeigt. Überprüfung der Kompatibilität auf des minimalen und maximalen Betriebssystems, legen und die Länge Aktivieren der Verschlüsselung auf die Speicherung von Daten und vieles mehr.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ed863378616f8001beab89177c642404287e7d3
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424941"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Einstellungen für Windows 8.1-Geräte als kompatibel oder nicht kompatibel mit Intune zu markieren

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dieser Artikel enthält und beschreibt die verschiedenen Einstellungen, die Sie auf Windows 8.1-Geräte in Intune konfigurieren können. Verwenden Sie diese Einstellungen als Teil Ihrer Lösung für mobile Geräte (MDM) einfache Kennwörter blockieren, legen Sie eine minimale und maximale Version des Betriebssystems und mehr.

Diese Funktion gilt für:

- Windows Phone 8.1
- Windows 8.1 und höher

Verwenden Sie als Intune-Administrator diesen Complianceeinstellungen zum Schutz der Ressourcen Ihrer Organisation ein. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Für **Plattform**Option **Windows Phone 8.1** oder **Windows 8.1 und höher**.

## <a name="device-properties"></a>Geräteeigenschaften

- **Minimal erforderliches Betriebssystem**: Geben Sie die zulässige Mindestversion. Wenn ein Gerät die Anforderung an die Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion**: Geben Sie die maximal zulässige Version. Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann nicht auf Ressourcen der Organisation zugreifen, bis Sie die Regel dahingehend ändern, dass die betreffende Betriebssystemversion zugelassen wird.

Windows 8.1-PCs geben die Version **3** zurück. Wenn die Regel für die Betriebssystemversion für Windows auf Windows 8.1 festgelegt ist, wird das betreffende Gerät als nicht kompatibel gemeldet, selbst wenn auf ihm Windows 8.1 installiert ist.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Einfache Kennwörter:** Legen Sie **Blockieren** fest, damit Benutzer kein einfaches Kennwort wie **1234** oder **1111** erstellen können. Wenn Sie diese Option auf **Nicht konfiguriert** setzen, können Benutzer Kennwörter wie **1234** oder **1111** erstellen.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Kennwort enthalten muss.

  Für Geräte, die unter Windows laufen und auf die mit einem Microsoft-Konto zugegriffen wird, wird die Konformitätsrichtlinie in diesem Fällen nicht korrekt ausgewertet:
  - Wenn die minimale Kennwortlänge mehr als acht Zeichen umfasst.
  - Oder, wenn die minimale Anzahl von Zeichensätzen mehr als zwei ist.

- **Kennworttyp**: Wählen Sie diese Option, wenn ein Kennwort nur aus **numerischen** Zeichen bestehen soll, oder wenn eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).
  
  - **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl von Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
    - Kleinbuchstaben
    - Großbuchstaben
    - Symbole
    - Zahlen

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen. Für Geräte, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Konformitätsrichtlinie in diesem Fall nicht korrekt ausgewertet:

    - Wenn die minimale Kennwortlänge mehr als acht Zeichen umfasst.
    - Oder wenn die minimale Anzahl von Zeichensätzen mehr als zwei ist.

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl der bereits verwendeten Kennwörtern an, die nicht erneut verwendet werden dürfen.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung auf mobilem Gerät anfordern**: Sie können **Erforderlich** festlegen, sodass das Gerät verschlüsselt sein muss, um eine Verbindung mit Datenspeicherressourcen herstellen zu können.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [bereichsmarkierungen Filter-Richtlinien verwenden](scope-tags.md).
- [Überwachen Sie Ihre Compliance-Richtlinien](compliance-policy-monitor.md).
- Finden Sie unter den [Einstellungen für Kompatibilitätsrichtlinien für Windows 10 und höher](compliance-policy-create-windows.md) Geräte.