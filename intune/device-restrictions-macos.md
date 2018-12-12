---
title: Einstellungen für Geräteeinschränkungen für Microsoft Intune unter macOS
titlesuffix: ''
description: In diesem Artikel erfahren Sie mehr über die Intune-Einstellungen zur Steuerung von Geräteeinstellungen und -funktionen auf macOS-Geräten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0a2a096bfb4b5fafd895425a775abc13afc643e2
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728535"
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Einstellungen für Geräteeinschränkungen für macOS-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel erfahren Sie mehr über Einstellungen für Microsoft Intune-Geräteeinschränkungen, die Sie für macOS-Geräte konfigurieren können.

## <a name="password"></a>Kennwort
- **Kennwort:** Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
  - **Erforderlicher Kennworttyp:** Geben Sie an, ob das Kennwort rein numerisch sein darf oder ob es alphanumerisch sein muss (also Buchstaben und Zahlen enthalten muss). Diese Einstellung wird lediglich unter Mac OS X 10.10.3 und höher unterstützt.
  - **Anzahl nicht alphanumerischer Zeichen im Kennwort:** Geben Sie die erforderliche Anzahl komplexer Zeichen im Kennwort an (**0** bis **4**).<br>Bei einem komplexen Zeichen handelt es sich um ein Symbol, z.B. **?**.
  - **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl von Zeichen an, die Benutzer für das Kennwort festlegen müssen (zwischen **4** und **16** Zeichen).
  - **Einfache Kennwörter:** Erlauben Sie die Verwendung einfacher Kennwörter wie **0000** oder **1234**.
  - **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts:** Geben Sie an, wie lange der Computer inaktiv sein muss, bevor er mithilfe eines Kennworts entsperrt werden muss.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Geben Sie die Zeitdauer an, die der Computer inaktiv sein muss, bevor der Bildschirms gesperrt wird.
  - **Kennwortablauf (Tage):** Geben Sie an, nach wie vielen Tagen der Benutzer das Kennwort ändern muss (**1** bis **255** Tage).
  - **Wiederverwendung vorheriger Kennwörter verhindern:** Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen (**1** bis **24**).

- **AutoAusfüllen für Kennwörter blockieren**: Wählen Sie **Blockieren**, um die Verwendung der Funktion zum automatischen Ausfüllen von Kennwörtern unter MacOS zu verhindern. Die Auswahl von **Blockieren** bewirkt auch Folgendes:

  - Benutzer werden nicht aufgefordert, in Safari oder beliebigen Apps gespeicherte Kennwörter zu verwenden.
  - Automatische sichere Kennwörter sind deaktiviert, und sichere Kennwörter werden Benutzern nicht empfohlen.

  **Nicht konfiguriert** lässt diese Funktionen zu.

- **Kennwortanforderungen durch Näherung blockieren**: Wählen Sie **Blockieren** aus, damit das Gerät eines Benutzers keine Kennwörter von in der Nähe befindlichen Geräten anfordert. **Nicht konfiguriert** lässt diese Kennwortanforderungen zu.

- **Kennwortfreigabe blockieren**: **Blockieren** verhindert die Freigabe von Kennwörtern zwischen Geräten mit AirDrop. **Nicht konfiguriert** ermöglicht die Freigabe von Kennwörtern.


## <a name="restricted-apps"></a>Eingeschränkte Apps

In der Liste der eingeschränkten Apps können Sie eine der folgenden Listen konfigurieren:

- **Unzulässige Apps:** Listet die (nicht von Intune verwalteten) Apps auf, die Benutzer nicht installieren und ausführen dürfen. Benutzer werden nicht daran gehindert, eine verbotene App zu installieren. Wenn sie dies jedoch tun, wird es Ihnen gemeldet.
- **Genehmigte Apps:** Listet die Apps auf, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine App zu installieren, die nicht auf der Genehmigungsliste aufgeführt ist. Wenn sie dies jedoch tun, wird es Ihnen gemeldet.

Klicken Sie zum Konfigurieren einer Liste auf **Hinzufügen**. Geben Sie dann einen Namen Ihrer Wahl sowie optional den Herausgeber der App und die Paket-ID der App an (z.B. *com.apple.calculator*).

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Nicht markierte E-Mail-Domänen

Fügen Sie im Feld **E-Mail-Domänen-URL** eine oder mehrere URLs der Liste hinzu. Wenn Benutzer eine E-Mail von einer Domäne erhalten, die Sie nicht konfiguriert haben, wird die E-Mail in der macOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

