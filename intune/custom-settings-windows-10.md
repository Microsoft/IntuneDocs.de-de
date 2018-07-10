---
title: 'Benutzerdefinierte Einstellungen für Windows 10-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Konfigurieren von benutzerdefinierten OMA-URI-Einstellungen auf Geräten unter Windows 10 mithilfe eines benutzerdefinierten Profils in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232825"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>Benutzerdefinierte OMA-URI-Einstellungen für Windows 10-Geräte: Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Stellen Sie mithilfe des **benutzerdefinierten** Profils von Microsoft Intune für Windows 10 und Windows 10 Mobile OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) bereit. Diese Einstellungen werden zum Steuern von Features auf Geräten verwendet. Windows 10 stellt viele CSP-Einstellungen zur Verfügung, z.B. den [Richtlinienkonfigurationsdienst-Anbieter (Policy Configuration Service Provider, Policy CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Wenn Sie nach einer bestimmten Einstellung suchen, beachten Sie, dass das [Geräteeinschränkungsprofil von Windows 10](device-restrictions-windows-10.md) viele Einstellungen enthält, die in Intune integriert sind und keine benutzerdefinierte Werte erfordern.

## <a name="configure-custom-settings"></a>Konfigurieren von benutzerdefinierten Einstellungen

1. Erstellen Sie ein neues Konfigurationsprofil mithilfe des Profiltyps **Benutzerdefiniert**. Die Schritte werden unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen](custom-settings-configure.md) aufgeführt.
2. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**, um eine neue Einstellung zu erstellen. Sie können auch auf **Exportieren** klicken, um eine Liste aller konfigurierten Werte in einer durch Trennzeichen getrennten Wertedatei (CSV) anzuzeigen.
3. Geben Sie für jede OMA-URI-Einstellung, die Sie hinzufügen möchten, die folgenden Informationen ein:

- **Name:** Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen einfacher identifizieren können.
- **Beschreibung:** Geben Sie optional eine Beschreibung für die Einstellung ein.
- **OMA-URI (Groß-/Kleinschreibung beachten)**: Geben Sie den OMA-URI an, für den Sie eine Einstellung festlegen möchten.
- **Datentyp**: Wählen Sie aus dem Folgenden:
  - **Zeichenfolge**
  - **Zeichenfolge (XML)**
  - **Datum und Uhrzeit**
  - **Ganze Zahl**
  - **Gleitkomma**
  - **Boolesch**
  - **Base64**
- **Wert:** Geben Sie den Wert oder die Datei an, die dem von Ihnen eingegebenen OMA-URI zugeordnet werden soll.

4. Wenn Sie fertig sind, klicken Sie auf **OK**. Klicken Sie unter **Profil erstellen** auf **Erstellen**. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird die Einstellung **Konnektivität > VPN über Mobilfunknetz zulassen** aktiviert. Mit dieser Einstellung kann ein Windows 10-Gerät eine VPN-Verbindung über ein Mobilfunknetz herstellen.

![Beispiel für eine benutzerdefinierte Richtlinie mit VPN-Einstellungen](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Suchen konfigurierbarer Richtlinien

Eine vollständige Liste aller Konfigurationsdienstanbieter (CSP), die von Windows 10 unterstützt werden, finden Sie in der [Configuration service provider reference (Konfigurationsdienstanbieter-Referenz)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

Nicht alle Einstellungen sind mit allen Windows 10-Versionen kompatibel. Über die [Konfigurationsdienstanbieter-Referenz](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) erfahren Sie, welche Versionen für die einzelnen Konfigurationsdienstanbieter unterstützt werden.

Darüber hinaus unterstützt Intune nicht alle aufgeführten Einstellungen. Öffnen Sie den Artikel für die jeweilige Einstellung, um herauszufinden, ob die gewünschte Einstellung von Intune unterstützt wird. Jede Einstellungsseite zeigt ihren unterstützten Vorgang an. Damit die Einstellung mit Intune funktioniert, muss sie die Vorgänge **Hinzufügen** oder **Ersetzen** unterstützen.
