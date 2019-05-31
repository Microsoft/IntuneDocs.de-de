---
title: Hinzufügen von Unternehmensbezeichnern zu Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie in Microsoft Intune Unternehmensbezeichner (Registrierungsmethode, IMEI- und Seriennummern) hinzufügen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28ad1e492c4bdd7c87371611530cd3f8e2abc2e1
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567282"
---
# <a name="identify-devices-as-corporate-owned"></a>Identifizieren von Geräten als unternehmenseigen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie Geräte als unternehmenseigen identifizieren, um die Verwaltung und Identifizierung zu optimieren. Intune kann zusätzliche Verwaltungsaufgaben durchführen und zusätzliche Informationen sammeln, wie etwa die vollständige Telefonnummer und einen Bestand an Apps von unternehmenseigenen Geräten. Sie haben auch die Möglichkeit, Gerätebeschränkungen festzulegen, um die Registrierung von Geräten, die kein Unternehmenseigentum sind, zu blockieren.

Bei der Registrierung weist Intune automatisch den Geräten, die eine der folgenden Bedingungen erfüllen, den Status „Unternehmenseigen“ zu:

- Mit einem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md)-Konto registriert (alle Plattformen)
- Mit dem [Apple-Programm zur Geräteregistrierung](device-enrollment-program-enroll-ios.md), dem [Apple School Manager](apple-school-manager-set-up-ios.md) oder dem [Apple Configurator](apple-configurator-enroll-ios.md) registriert (iOS-Geräte).
- Mit einer IMEI-Nummer (alle Plattformen mit IMEI-Nummern) oder Seriennummer (iOS und Android) [vor der Registrierung als unternehmenseigen identifiziert](#identify-corporate-owned-devices-with-imei-or-serial-number)
- Als Windows 10 Enterprise-Gerät mit Azure Active Directory verknüpft
- In den [Geräteeigenschaften](#change-device-ownership) als „Unternehmen“ festgelegt

Nach der Registrierung können Sie in den [Besitzeinstellungen](#change-device-ownership) zwischen **Persönlich** und **Unternehmen** wechseln.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identifizieren von unternehmenseigenen Geräten mit IMEI- oder Seriennummer

Als Intune-Administrator können Sie eine durch Trennzeichen getrennte Datei (CSV-Datei) erstellen und importieren, die 14-stellige IMEI-Nummern oder Seriennummern auflistet. Intune verwendet diese Bezeichner, um den Gerätebesitz während der Registrierung als unternehmenseigen anzugeben. Sie können die IMEI-Nummern für alle unterstützten Plattformen deklarieren. Sie können die Seriennummer nur für iOS-, macOS- und Android-Geräte deklarieren. Jede IMEI-Nummer oder Seriennummer kann Details enthalten, die in der Liste zu administrativen Zwecken angegeben sind.

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Erfahren Sie, wie Sie die Seriennummer eines Apple-Geräts finden](https://support.apple.com/HT204308).<br>
[Erfahren Sie, wie Sie die Seriennummer Ihres Android-Geräts finden](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Hinzufügen von Unternehmensbezeichnern mithilfe einer CSV-Datei
Erstellen Sie dazu eine Liste mit zwei Spalten, die durch Trennzeichen getrennt ist (CSV) und keinen Header enthält. Fügen Sie die 14-stellige IMEI- oder Seriennummer in der linken Spalte und die Details in der rechten Spalte hinzu. Nur ein Typ von ID, IMEI- oder Seriennummer kann in eine CSV-Datei importiert werden. Details sind auf 128 Zeichen beschränkt und nur für administrative Zwecke bestimmt. Details werden nicht auf dem Gerät angezeigt. Die aktuelle Begrenzung beträgt 5.000 Zeilen pro CSV-Datei.

**Eine CSV-Datei mit Seriennummern hochladen**: Erstellen Sie eine durch Trennzeichen getrennte Liste (.csv) mit zwei Spalten ohne Header, und beschränken Sie die Liste auf 5.000 Geräte oder 5 MB pro CSV-Datei.

|||
|-|-|
|&lt;ID #1&gt;|&lt;Details zu Gerät 1&gt;|
|&lt;ID #2&gt;|&lt;Details zu Gerät 2&gt;|

Diese CSV-Datei wird bei der Anzeige in einem Text-Editor folgendermaßen angezeigt:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Einige Android- und iOS-Geräte verfügen über mehrere IMEI-Nummern. Intune liest nur eine IMEI-Nummer pro registriertem Gerät. Wenn Sie eine IMEI-Nummer importieren, es sich aber nicht um die IMEI-Nummer handelt, die von Intune inventarisiert wurde, wird das Gerät als ein persönliches Gerät und nicht als ein unternehmenseigenes Gerät eingestuft. Wenn Sie mehrere IMEI-Nummern für ein Gerät importieren, werden nicht inventarisierte Nummern als Anmeldungsstatus **Unbekannt** anzeigen.<br>
>Beachten Sie außerdem: Seriennummern sind die empfohlene Art der Kennzeichnung für iOS-Geräte.
>Android-Seriennummern sind nicht garantiert eindeutig oder vorhanden. Wenden Sie sich an Ihren Gerätehersteller, um herauszufinden, ob die Seriennummer eine zuverlässige Geräte-ID ist.
>Seriennummern, die vom Gerät an Intune übermittelt werden, stimmen möglicherweise nicht mit der angezeigten ID in den Menüs „Einstellungen für Android/Info“ auf dem Gerät überein. Überprüfen Sie den Typ der Seriennummer, die vom Gerätehersteller übermittelt wurde.
>Wenn Sie versuchen, meine Datei mit einer Seriennummer hochzuladen, die Punkte („.“) enthält, schlägt der Upload fehl. Seriennummern mit Punkten werden nicht unterstützt.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Hochladen einer CSV-Liste von Unternehmensbezeichnern

1. Wählen Sie [in Intune im Azure-Portal](https://portal.azure.com) die Optionen **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen** > **CSV-Datei hochladen** aus.

   ![Arbeitsbereich des Bezeichners von Unternehmensgeräten mit hervorgehobener Schaltfläche „Hinzufügen“](./media/add-corp-id.png)

2. Geben Sie auf dem Blatt **Bezeichner hinzufügen** den Bezeichnertyp ein: **IMEI** oder **Seriennummer**.

3. Klicken Sie auf das Ordnersymbol, und geben Sie den Pfad zu der Liste an, die Sie importieren möchten. Navigieren Sie zu der CSV-Datei, und wählen Sie **Hinzufügen** aus. 

4. Wenn die CSV-Datei Unternehmensbezeichner enthält, die sich bereits in Intune befinden, jedoch unterschiedliche Informationen aufweisen, wird das Popupfenster **Doppelte Bezeichner überprüfen** angezeigt. Wählen Sie die Bezeichner aus, die Sie in Intune überschreiben möchten, und klicken Sie dann auf **OK**, um die Bezeichner hinzuzufügen. Für jeden Bezeichner wird nur das erste Duplikat verglichen.

## <a name="manually-enter-corporate-identifiers"></a>Manuelles Eingeben von Unternehmensbezeichnern

1. Wählen Sie [in Intune im Azure-Portal](https://portal.azure.com) die Optionen **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen** > **Manuell eingeben** aus.

2. Geben Sie auf dem Blatt **Bezeichner hinzufügen** den Bezeichnertyp ein: **IMEI** oder **Seriennummer**.

3. Geben Sie den **Bezeichner** und die **Details** für jeden Bezeichner ein, den Sie hinzufügen möchten. Wenn Sie mit der Eingabe der Bezeichner fertig sind, klicken Sie auf **Hinzufügen**.

5. Wenn Sie die Unternehmensbezeichner eingegeben haben, die sich bereits in Intune befinden, jedoch unterschiedliche Informationen aufweisen, wird das Popupfenster **Doppelte Bezeichner überprüfen** angezeigt. Wählen Sie die Bezeichner aus, die Sie in Intune überschreiben möchten, und klicken Sie dann auf **OK**, um die Bezeichner hinzuzufügen. Für jeden Bezeichner wird nur das erste Duplikat verglichen.

Sie können auf **Aktualisieren** klicken, um neue Gerätebezeichner anzuzeigen.

Importierte Geräte sind nicht zwangsläufig registriert. Geräte können entweder **Registriert** oder **Nicht kontaktiert** sein. **Nicht kontaktiert** bedeutet, dass das Gerät noch nie mit dem Intune-Dienst kommuniziert hat.

## <a name="delete-corporate-identifiers"></a>Löschen von Unternehmensbezeichnern

1. Wählen Sie [in Intune im Azure-Portal](https://portal.azure.com) die Optionen **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** aus.
2. Wählen Sie die Gerätebezeichner aus, die Sie löschen möchten, und klicken Sie auf **Löschen**.
3. Bestätigen Sie den Löschvorgang.

Das Löschen eines Unternehmensbezeichners für ein registriertes Gerät hat keine Auswirkungen auf den Besitzstatus des Geräts. Wechseln Sie zum Ändern des Gerätebesitzes zu **Geräte**, wählen Sie das Gerät aus, klicken Sie auf **Eigenschaften**, und ändern Sie den **Gerätebesitz**.

## <a name="imei-specifications"></a>IMEI-Spezifikationen
Detaillierte Angaben über International Mobile Equipment Identifier finden Sie unter [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Ändern des Gerätebesitzes

Die Geräteeigenschaften zeigen den **Besitz** für jeden Gerätedatensatz in Intune an. Als Administrator können Sie Geräte als **Persönlich** oder **Unternehmen** festlegen.

**So ändern Sie den Gerätebesitz:**
1. Navigieren Sie in [Intune im Azure-Portal](https://portal.azure.com) zu **Geräte**, und wählen Sie das Gerät aus.
2. Wählen Sie **Eigenschaften** aus.
3. Geben Sie den **Gerätebesitz** als **Persönlich** oder **Unternehmen** an.

   ![Geräteeigenschaften, die die Optionen der Gerätekategorie und des Gerätebesitzes anzeigen.](./media/device-properties.png)
