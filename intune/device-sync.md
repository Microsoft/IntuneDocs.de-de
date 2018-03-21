---
title: "Synchronisieren von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation"
description: "Synchronisieren Sie Geräte, die bei Microsoft Intune registriert sind und dort verwaltet werden, um die neuesten Richtlinien und Aktionen zu erhalten. Dieser Artikel erläutert die notwendigen Schritte zur Synchronisierung mithilfe des Azure-Portals und führt die Fehlercodes auf, die zurückgegeben werden können."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d2d13ce2ed06549a6cd09fd766a0072b15fcd067
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions---intune"></a>Synchronisieren von Geräten, um die neuesten Richtlinien und Aktionen zu erhalten – Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Die Geräteaktion **Sync** (Synchronsieren) zwingt das ausgewählte Gerät dazu, sofort bei Intune einzuchecken. Checkt ein Gerät ein, empfängt es sofort alle ihm zugewiesenen ausstehenden Aktionen oder Richtlinien. Mit diesem Feature können Sie zugewiesene Richtlinien sofort überprüfen und Probleme beheben, ohne den nächsten geplanten Check-In abwarten zu müssen.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Gerät synchronisieren

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie auf **Microsoft Intune**. 
3. Klicken Sie in **Intune** auf **Geräte**, und wählen Sie **Alle Geräte** aus.
4. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, klicken Sie auf **...Weitere**, und wählen Sie dann die Aktion **Synchronisieren** aus.
5. Klicken Sie zum Bestätigen auf **Ja**.


## <a name="retryable-error-codes"></a>Wiederholbare Fehlercodes

Wenn ein Administrator die Geräteaktion **Synchronisieren** ausführt, sind iOS- und Android-Apps, für die die Synchronisierung nicht ausgeführt werden konnte und die einen wiederholbaren Fehlercode ausgelöst haben, auf dem Gerät weiterhin verfügbar. Allerdings dauert es sieben Tage, bis Apps, die einen nicht wiederholbaren Fehlercode ausgelöst haben, auf dem Gerät wieder verfügbar sind.


| Fehlercode  | Vorgeschlagene Beschreibung | Wiederholbar |
|---|---|---|
| 2016330898 | Unbekannter Fehler aufgetreten. | Nein |
| 2016330897 | Ihre Verbindung zu Intune wurde aufgrund einer Zeitüberschreitung abgebrochen. Setzen Sie Ihre Verbindung zurück. | Ja  |
| 2016330896 | Ihre Internetverbindung wurde getrennt. Setzen Sie Ihre Verbindung zurück. | Ja  |
| 2016330895 | Ihre Internetverbindung wurde getrennt. Setzen Sie Ihre Verbindung zurück. | Ja  |
| 2016330894 | Ihre Internetverbindung wurde getrennt. Setzen Sie Ihre Verbindung zurück. | Ja  |
| 2016330893 | Ihre Internetverbindung wurde getrennt. Setzen Sie Ihre Verbindung zurück. | Ja |
| 2016330892 | Internationales Roaming ist deaktiviert. | Nein|
| 2016330891 | Während eines Anrufs kann für dieses Gerät nicht auf die Mobilfunkverbindung zugegriffen werden. Warten Sie, bis der Anruf beendet wird. | Ja |
| 2016330890 | Das Mobilfunknetz für dieses Gerät: Diese Geräte konnten zu diesem Zeitpunkt nicht verwendet werden. | Nein|
| 2016330889 | Fehler bei der sicheren Verbindung: Setzen Sie Ihre Verbindung zurück. | Ja |
| 2016330888 | Fehler bei der Auswertung der Serververtrauensstellung | Nein|

## <a name="next-step"></a>Nächster Schritt

Wählen Sie **Geräteaktionen** aus, um den Status der Synchronisierung anzuzeigen. 
