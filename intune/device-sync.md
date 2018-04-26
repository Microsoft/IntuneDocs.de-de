---
title: Synchronisieren von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Synchronisieren von Geräten, die bei Microsoft Intune registriert sind und dort verwaltet werden, um die neuesten Richtlinien und Aktionen zu erhalten. In diesem Artikel werden die Schritte erläutert, die zur Synchronisierung mithilfe des Azure-Portals erfordelrich sind. Außerdem werden die wiederholbaren Fehlercodes aufgeführt.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb609f0d99378e2e30b3c3a4f769781448aea1b5
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Synchronisieren von Geräten mit Intune, um die neuesten Richtlinien und Aktionen zu erhalten


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Die Geräteaktion **Sync** (Synchronsieren) zwingt das ausgewählte Gerät dazu, sofort bei Intune einzuchecken. Checkt ein Gerät ein, empfängt es sofort alle ihm zugewiesenen ausstehenden Aktionen oder Richtlinien. Mit diesem Feature können Sie zugewiesene Richtlinien sofort überprüfen und Probleme beheben, ohne den nächsten geplanten Check-In abwarten zu müssen.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Gerät synchronisieren

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**. 
3. Klicken Sie in **Intune** auf **Geräte** > **Alle Geräte**.
4. Wählen Sie in der Liste der von Ihnen verwalteten Geräte ein Gerät aus, klicken Sie auf **Mehr** und dann auf **Synchronisieren**.
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

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Geräteaktionen**, um den Status der Synchronisierung anzuzeigen. 
