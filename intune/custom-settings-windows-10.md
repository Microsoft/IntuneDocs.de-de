---
title: "Benutzerdefinierte Microsoft Intune-Einstellungen für Windows 10-Geräte"
titlesuffix: 
description: "Erfahren Sie etwas über die benutzerdefinierten Einstellungen, die Sie in einem benutzerdefinierten Windows 10-Profil konfigurieren können."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4bb86d0f80a4d337e0ab63ae7f90d6c3541462d9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>Benutzerdefinierte Microsoft Intune-Geräteeinstellungen für Windows 10-Geräte

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Stellen Sie mithilfe des **benutzerdefinierten** Profils von Microsoft Intune für Windows 10 und Windows 10 Mobile OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) bereit, um Features auf Geräten zu steuern. Windows 10 stellt viele CSP-Einstellungen zur Verfügung, z.B. den [Richtlinienkonfigurationsdienst-Anbieter (Policy Configuration Service Provider; Policy CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Wenn Sie nach einer bestimmten Einstellung suchen, beachten Sie, dass das [Geräteeinschränkungsprofil von Windows 10](device-restrictions-windows-10.md) viele Einstellungen enthält, die in Intune integriert sind und keine Angabe benutzerdefinierter Werte erfordern.

## <a name="configure-custom-settings"></a>Konfigurieren von benutzerdefinierten Einstellungen

1. Anweisungen zu den ersten Schritten finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen in Microsoft Intune](custom-settings-configure.md).
1. Klicken Sie im Bereich **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**, um einen neuen Wert hinzuzufügen. Sie können auch auf **Exportieren** klicken, um eine Liste aller konfigurierten Werte in einer durch Trennzeichen getrennten Wertedatei (CSV) anzuzeigen.
1. Geben Sie für jede OMA-URI-Einstellung, die Sie hinzufügen möchten, die folgenden Informationen ein. Verwenden Sie die Liste in diesem Artikel, um weitere Informationen zu den Einstellungen zu erhalten, die Sie verwenden können:
    - **Name**: Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen einfacher identifizieren können.
    - **Beschreibung**: Geben Sie optional eine Beschreibung für die Einstellung ein.
    - **OMA-URI (Groß-/Kleinschreibung beachten)**: Geben Sie den OMA-URI an, für den Sie eine Einstellung festlegen möchten.
    - **Datentyp** – Wählen Sie aus:
        - **Zeichenfolge**
        - **Zeichenfolge (XML)**
        - **Datum und Uhrzeit**
        - **Ganze Zahl**
        - **Gleitkomma**
        - **Boolesch**
        - **Base64**
    - **Wert**: Geben Sie den Wert oder die Datei an, der bzw. die mit der von Ihnen eingegebenen OMA-URI verknüpft werden soll.
1. Klicken Sie anschließend auf **OK**, navigieren Sie wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.
Das Profil wird erstellt und im Bereich „Profilliste“ angezeigt.

## <a name="example"></a>Beispiel
Im folgenden Screenshot ist die Einstellung **Connectivity/AllowVPNOverCellular** aktiviert. Dadurch kann ein Windows 10-Gerät eine VPN-Verbindung über ein Mobilfunknetz öffnen.

> ![Beispiel für eine benutzerdefinierte Richtlinie mit VPN-Einstellungen](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Suchen konfigurierbarer Richtlinien

Eine vollständige Liste aller Konfigurationsdienstanbieter (CSP), die von Windows 10 unterstützt werden, finden Sie in der [Konfigurationsdienstanbieter-Referenz](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) in der Windows-Dokumentationsbibliothek.

Nicht alle Einstellungen sind mit allen Windows 10-Versionen kompatibel. Die Tabelle im Windows-Artikel enthält entsprechende Informationen, welche Versionen für die einzelnen Konfigurationsdienstanbieter unterstützt werden.

Darüber hinaus unterstützt Intune nicht alle Einstellungen, die in diesem Artikel aufgeführt werden. Öffnen Sie den Artikel für die jeweilige Einstellung, um herauszufinden, ob die gewünschte Einstellung von Intune unterstützt wird. Jede Einstellungsseite zeigt ihren unterstützten Vorgang an. Damit die Einstellung mit Intune funktioniert, muss sie die Vorgänge **Hinzufügen** oder **Ersetzen** unterstützen.
