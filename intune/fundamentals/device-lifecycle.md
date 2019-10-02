---
title: Übersicht über den MDM-Lebenszyklus von Microsoft Intune
description: Erfahren Sie, wie Ihnen Intune bei der Verwaltung von Geräten während ihres Lebenszyklus (von der Registrierung über die Konfiguration bis zur letztlichen Abkopplung) behilflich sein kann.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 414476389a36cdfafd9169d449ea11adf6e68efd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726296"
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>Übersicht über den MDM-Lebenszyklus von Microsoft Intune (MDM = Mobile Device Management; mobile Geräteverwaltung)

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Alle von Ihnen verwalteten Geräte verfügen über einen *Lebenszyklus*. Intune kann Ihnen bei der Verwaltung dieses Lebenszyklus helfen: von der Registrierung über die Konfiguration und den Schutz bis hin zur Abkopplung des Geräts, wenn es nicht mehr benötigt wird.

![Der Gerätelebenszyklus](./media/device-lifecycle/device-lifecycle.png "Der Intune-Lebenszyklus von Geräten")

## <a name="enroll"></a>Registrieren
Die heutigen Strategien zur Verwaltung mobiler Geräte (Mobile Device Management, MDM) befassen sich mit einer Vielzahl von Mobiltelefonen, Tablets und PCs (iOS, Android, Windows und Mac OS X). Wenn Sie das Gerät verwalten müssen, was bei unternehmenseigenen Geräten im Allgemeinen der Fall ist, besteht der erste Schritt darin, die [Geräteregistrierung einzurichten](../enrollment/device-enrollment.md). Durch das Registrieren bei Intune (MDM) oder durch [Installieren der Intune-Clientsoftware](../manage-windows-pcs-with-microsoft-intune.md) können Sie auch Windows-PCs verwalten.

## <a name="configure"></a>Konfigurieren
Das Registrieren Ihrer Geräte ist nur der erste Schritt. Um alle Intune-Angebote zu nutzen und um sicherzustellen, dass die Geräte sicher und mit Unternehmensstandards kompatibel sind, können Sie aus einer Vielzahl von Richtlinien auswählen. Mit diesen können Sie nahezu jeden Aspekt des Betriebs von verwalteten Geräten konfigurieren. Sollen Benutzer beispielsweise ein Kennwort für Geräte verwenden, die Unternehmensdaten enthalten? Sie können festlegen, dass ein Kennwort erforderlich ist. Haben Sie ein Unternehmens-WLAN? Sie können es automatisch konfigurieren. Hier sind die verfügbaren Typen von Konfigurationsoptionen aufgeführt:

- [**Gerätekonfiguration**](../configuration/device-profiles.md). Mit diesen Richtlinien können Sie die Features und Funktionen der von Ihnen verwalteten Geräten konfigurieren. Beispielsweise können Sie die Verwendung eines Kennworts auf Windows Phones verlangen oder die Verwendung der Kamera auf iPhones deaktivieren.
- [**Zugriff auf Unternehmensressourcen**](../configuration/device-profiles.md). Wenn Sie Ihren Benutzern den Zugriff auf ihre Arbeit über ihre persönlichen Geräte gestatten, stellt Sie dies vor gewisse Herausforderungen. Wie gewährleisten Sie beispielsweise, dass alle Geräte, die auf Unternehmens-E-Mail zugreifen müssen, ordnungsgemäß konfiguriert sind? Wie können Sie sicherstellen, dass Benutzer über eine VPN-Verbindung auf das Unternehmensnetzwerk zugreifen können, ohne die komplexen Einstellungen kennen zu müssen? Intune kann Sie entlasten, indem die von Ihnen verwalteten Geräte automatisch für den Zugriff auf allgemeine Unternehmensressourcen konfiguriert werden.
- [**Windows-PC-Verwaltungsrichtlinien (mit der Intune-Clientsoftware)** ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). Auch wenn Ihnen durch die Registrierung von Windows-PCs bei Intune die meisten Verwaltungsfunktionen für Geräte bereitgestellt werden, unterstützt Intune weiterhin das Verwalten von Windows-PCs über die Intune-Clientsoftware. Wenn Sie Informationen über einige Aufgaben benötigen, die Sie mit PCs ausführen können, beginnen Sie hier.

## <a name="protect"></a>Schützen
In der modernen IT-Welt ist der Schutz von Geräten vor unbefugtem Zugriff eine der wichtigsten Aufgaben, die Sie erfüllen müssen. Zusätzlich zu den Elementen im Schritt **Konfigurieren** des Gerätelebenszyklus stellt Intune diese Funktionen bereit, mit denen Sie von Ihnen verwaltete Geräte vor unbefugtem Zugriff oder böswilligen Angriffen schützen können:
- [**Mehrstufige Authentifizierung**](../enrollment/multi-factor-authentication.md). Durch das Hinzufügen einer zusätzlichen Authentifizierungsebene zu den Benutzeranmeldungen können Sie Geräte noch sicherer machen. Viele Geräte unterstützen die mehrstufige Authentifizierung, die eine zweite Authentifizierungsebene wie einen Telefonanruf oder eine SMS erfordert, bevor Benutzer Zugriff erhalten.
- [**Windows Hello for Business-Einstellungen**](../protect/windows-hello.md). Windows Hello for Business ist eine alternative Anmeldemethode, die Benutzern das Verwenden einer *Geste*, z. B. Fingerabdruck oder Windows Hello, ermöglicht, um sich ohne Kennwort anzumelden.
- [**Richtlinien zum Schutz von Windows-PCs (mit der Intune-Clientsoftware)** ](../policies-to-protect-windows-pcs-in-microsoft-intune.md). Wenn Sie Windows-PCs mit der Intune-Clientsoftware verwalten, stehen Richtlinien zur Verfügung, mit denen Sie die Einstellungen für Endpoint Protection, Softwareupdates und Windows-Firewall auf von Ihnen verwalteten PCs steuern können.

## <a name="retire"></a>Außerkraftsetzen
Wenn ein Gerät verloren geht, gestohlen wird oder ersetzt werden muss, oder wenn Benutzer in eine andere Position wechseln, ist es in der Regel an der Zeit, das Gerät [abzukoppeln oder zurückzusetzen](../remote-actions/device-management.md). Hierzu gibt es verschiedene Möglichkeiten, angefangen beim Zurücksetzen des Geräts über das Entfernen des Geräts aus der Verwaltung bis hin zum Löschen der darauf befindlichen Unternehmensdaten.

## <a name="next-steps"></a>Nächste Schritte

- Informationen zur [Geräteverwaltung in Microsoft Intune](../remote-actions/device-management.md)
